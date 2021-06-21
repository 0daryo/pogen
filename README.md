# pogen
Generator of function to get http path pattern in proto option from http.Request.URL.Path

If you have this kind of grpc-gateway like proto file, 
http.Request.URL.Path can be ```/users/1```.

With generated codes, You can get ```users/{userId}``` for analysis or metrics.
```
service UserService {
  rpc GetStatus(UserRequest) returns (UserResponse) {
    option (google.api.http) = {
      get: "/users/{userId}"
      body: "*"
    };
  }
}
```

# Usage
``` go run main.go -p example -o example/example.go -d example/proto```

# Options
```
  -d string
        proto directory name (default "proto/service")
  -o string
        output file (default "output.go")
  -p string
        package name (default "main")
```

# Problem
Getting pattern from http.Request.URL.Path is not efficient. order is o(n).