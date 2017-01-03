# URLSesssion

### Simple way

I think, this is simplist way to make http request in swift using URLSession class. 
There is no custom configuration, just default settings.

```swift
let url = URL(string: "https://httpbin.org/get")
let task = URLSession.shared.dataTask(with: url!, completionHandler: { (data, response, error) in
    if error != nil {
        print("Error: \(error?.localizedDescription)")
    }
    
    if let response = response {
        print("Result : \(response)")
    }  
})
task.resume()
```  
  
### JSON Parsing (Ugly Way)

Json parsing in Swift is a bit hard. There is some library that making this process easy. But first I need to understand what lives under the hood

```swift

let url = URL(string: "https://httpbin.org/get")
let task = URLSession.shared.dataTask(with: url!) { (data, response, error) in

    if error != nil {
        print("Error: \(error?.localizedDescription)")
    }
    guard let data = data else {
        print("Error: Data is empty")
        return
    }
    let json = try? JSONSerialization.jsonObject(with: data, options: [])
    
    if let dictionary = json as? [String: Any] {
        
        for (key, value) in dictionary {
            //Returning all keys and values
        }
        if let headers = dictionary["headers"] as? [String: Any] {
            print("Host: \(headers["Host"]!)")
        }
        if let origin = dictionary["origin"] , let url = dictionary["url"] {
            print("Origin :\(origin)")
            print("Url :\(url)")
        }   
    }   
}
task.resume()

```


  
####  Apple Documentation
https://developer.apple.com/reference/foundation/urlsession
