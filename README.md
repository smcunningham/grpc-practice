Download and install protoc compiler:
https://github.com/google/protobuf

Install protoc plugin for Golang:
`go get -u github.com/golang/protobuf/proto`
`go get -u github.com/golang/protobuf/protoc-gen-go`

Install Golang implementation of gRPC:
`go get google.golang.org/grpc`

Protocol Buffers Language Guide:
https://developers.google.com/protocol-buffers/docs/proto3

Run this protoc compiler command from the root directory to generate source code
essential to creating the server and to make client calls through RPC:
`protoc -I customer/ customer/customer.proto --go_out=plugins=grpc:customer`

Run gRPC server with this command from server directory:
`go run main.go`

To test the RPC methods by calling from the client application,
run from the client directory:
`go run main.go`

You should see similar output:
`2016/10/11 16:02:47 A new Customer has been added with id: 101
 2016/10/11 16:02:47 A new Customer has been added with id: 102
 2016/10/11 16:02:47 Customer: id:101 name:”Shiju Varghese” email:”shiju@xyz.com” 
   phone:”732–757–2923" addresses:<street:”1 Mission Street” city:”San Francisco” 
   state:”CA” zip:”94105" > addresses:<street:”Greenfield” city:”Kochi” state:”KL” 
   zip:”68356" isShippingAddress:true >
 2016/10/11 16:02:47 Customer: id:102 name:”Irene Rose” email:”irene@xyz.com” 
   phone:”732–757–2924" addresses:<street:”1 Mission Street” city:”San Francisco” 
   state:”CA” zip:”94105" isShippingAddress:true >
   `
 This means that your gRPC server was correctly started, and it received the
 correct RPC methods from the client application, which resulted in creating
 and displaying two customers.
 
 For further reading, see:
 https://medium.com/@shijuvar/building-high-performance-apis-in-go-using-grpc-and-protocol-buffers-2eda5b80771b