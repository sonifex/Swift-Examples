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
  
  
####  Apple Documentation
https://developer.apple.com/reference/foundation/urlsession
