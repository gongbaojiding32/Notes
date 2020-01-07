## HTML5本体储存五种方案

**1. LocalStorage**
**LocalStorage就是Key-Value的简单键值对存储结构，Web Storage除了localStorage的持久性存储外有针对性本次回话的sessionStorage方式, 一般情况下localStorage较常用 示例如下**

``` js
function save(dataModel) {

    var value = dataModel.serialize();

    window.localStorage['DataModel'] = value;

    window.localStorage['DataCount'] = dataModel.size();

    console.log(dataModel.size() + ' datas are saved');

    return value;

}

function restore(dataModel) {

    var value = window.localStorage['DataModel'];

    if (value) {

        dataModel.deserialize(value);

        console.log(window.localStorage['DataCount'] + ' datas are restored');

        return value;

    }

    return '';

}

function clear() {

    if (window.localStorage['DataModel']) {

        console.log(window.localStorage['DataCount'] + ' datas are cleared');

        delete window.localStorage['DataModel'];

        delete window.localStorage['DataCount'];

    }

}
```

**2. Cookie c存储内容有限，只适合简单信息存储，**

``` js
function getCookieValue(name) {

    if (document.cookie.length > 0) {

        var start = document.cookie.indexOf(name + "=");

        if (start !== -1) {

            start = start + name.length + 1;

            var end = document.cookie.indexOf(";", start);

            if (end === -1) {

                end = document.cookie.length;

            }

            return unescape(document.cookie.substring(start, end));

        }

    }

    return '';

}

function save(dataModel) {

    var value = dataModel.serialize();

    document.cookie = 'DataModel=' + escape(value);

    document.cookie = 'DataCount=' + dataModel.size();

    console.log(dataModel.size() + ' datas are saved');

    return value;

}
```

**3. Indexed Database API**
**IndexedDB 可以存储结构对象，可构建key和index的索引方式查找，目前各浏览器的已经逐渐支持IndexedDB的存储方式，其使用代码如下，需注意IndexedDB的很多操作接口类似NodeJS的异步回调方式，特别是查询时连cursor的continue都是异步再次回调onsuccess函数的操作方式，因此和NodeJS一样使用上不如同步的代码容易。**

``` js
function save(dataModel) {

    var tx = db.transaction("meters", "readwrite");

    var store = tx.objectStore("meters");

    dataModel.each(function(data) {

        store.put({

            id: data.getId(),

            tag: data.getTag(),

            name: data.getName(),

            meterValue: data.a('meter.value'),

            meterAngle: data.a('meter.angle'),

            p3: data.p3(),

            r3: data.r3(),

            s3: data.s3()

        });

    });

    tx.oncomplete = function() {

        console.log(dataModel.size() + ' datas are saved');

    };

    return dataModel.serialize();

}
```

**4. FileSystem API**
**FileSystem API 相当于操作本地文件的存储方式，目前支持浏览器不多，其接口标准业发展制定变化中，因此也可以动态生成图片到本地文件，然后通过filesystem:http:... 的URL方式直接赋值给img的html元素的src访问**

``` js
function save(dataModel) {

    var value = dataModel.serialize();

    fs.root.getFile('meters.txt', {
        create: true
    }, function(fileEntry) {

        console.log(fileEntry.toURL());

        fileEntry.createWriter(function(fileWriter) {

            fileWriter.onwriteend = function() {

                console.log(dataModel.size() + ' datas are saved');

            };

            var blob = new Blob([value], {
                type: 'text/plain'
            });

            fileWriter.write(blob);

        });

    });

    return value;

}
```

**5. Application Cache**
**window.applicationCache对象是对浏览器的应用缓存的编程访问方式，其status属性可用于查看缓存的当前状态**

```js
var appCache = window.applicationCache;
 
switch (appCache.status) {
 
case appCache.UNCACHED: // UNCACHED == 0
 
return 'UNCACHED';
 
break;
 
case appCache.IDLE: // IDLE == 1
 
return 'IDLE';
 
break;
 
case appCache.CHECKING: // CHECKING == 2
 
return 'CHECKING';
 
break;
 
case appCache.DOWNLOADING: // DOWNLOADING == 3
 
return 'DOWNLOADING';
 
break;
 
case appCache.UPDATEREADY: // UPDATEREADY == 4
 
return 'UPDATEREADY';
 
break;
 
case appCache.OBSOLETE: // OBSOLETE == 5
 
return 'OBSOLETE';
 
break;
 
default:
 
return 'UKNOWN CACHE STATUS';
 
break;
 
};
```


