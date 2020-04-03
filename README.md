### Project Setup

#### 1. Download and install protoc compiler:
https://github.com/google/protobuf

*Make sure the compiler is in your path!*

#### 2. Install protoc plugin for Golang:
```
go get -u github.com/golang/protobuf/proto
go get -u github.com/golang/protobuf/protoc-gen-go
```

#### 3. Install Golang implementation of gRPC:
`go get google.golang.org/grpc`

***

### Running the Application

#### 1. Run this protoc compiler command from the root directory:
`protoc -I customer/ customer/customer.proto --go_out=plugins=grpc:customer`

##### This generates `customer/customer.pb.go`, a Protobuf file with source code that allows us to:
- Create the gRPC server
- Make client RPC calls

#### 2. Running gRPC Applications:

##### a. gRPC Server Application:
`go run main.go` from `/server` directory

##### b. gRPC Client Application:
`go run main.go` from `/client` directory

You should see output similar to this:

```2016/10/11 16:02:47 A new Customer has been added with id: 101

2016/10/11 16:02:47 A new Customer has been added with id: 102
 
2016/10/11 16:02:47 Customer: id:101 name:”Shiju Varghese” email:”shiju@xyz.com” 
   phone:”732–757–2923" addresses:<street:”1 Mission Street” city:”San Francisco” 
   state:”CA” zip:”94105" > addresses:<street:”Greenfield” city:”Kochi” state:”KL” 
   zip:”68356" isShippingAddress:true >
   
2016/10/11 16:02:47 Customer: id:102 name:”Irene Rose” email:”irene@xyz.com” 
   phone:”732–757–2924" addresses:<street:”1 Mission Street” city:”San Francisco” 
   state:”CA” zip:”94105" isShippingAddress:true >
```
   
This means that your gRPC server initialized, and received the correct RPC methods from the client application, which resulted in creating and displaying two customers.
 
 ***
 
 ### References
 
 ##### gRPC
 https://www.grpc.io/
 
 ##### Protocol Buffers (Protobuf) Language Guide:
 https://developers.google.com/protocol-buffers/docs/proto3
 
 ##### This project specifically:
 https://medium.com/@shijuvar/building-high-performance-apis-in-go-using-grpc-and-protocol-buffers-2eda5b80771b
 