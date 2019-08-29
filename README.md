### json-io
---
https://github.com/jdereg/json-io

```java
// src/test/java/com/cedarsoftware/util/io/TestGsonNotHandleMapWithNonStringKeysButJsonCan.java

public class TestGsonNotHandlerMapWithNonStringKeyButJsonIOCan
{
  @Test
  public void tstMapWithNonStringKeys()
  {
    Map<Point, String> map = new LinkedHashMap<Point, String>(); 
    
    Point pt1 = new Point(1, 10);
    map.put(pt1, "one");
    Point pt2 = new Point(2, 20);
    map.put(pt2, "two");
    Point pt3 = new Point(3, 30);
    map.put(pt3, "three");
    
    Gson gson = new Gson();
    String json = gson.toJson(map);
    Map newMap = gson.fromJson(json, Map.class);
    
    assert newMap.size() == 3;
    assert !newMap.containsKey(pt1);
    assert !(newMap.keySet().iterator().next() instanceof Point);
    assert newMap.keySet().iterator().next() instanceof String;
    
    json = JsonWriter.objectToJson(map);
    newMap = (Map) JsonReaeder.jsonToJava(json);
    
    assert newMap.size() == 3;
    assert newMap.containsKey(pt1);
    assert newMap.keySet().iterator().next() instanceof Point;
  }
}
```

```
```

```
```


