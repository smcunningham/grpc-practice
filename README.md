## gRPC Customer Application

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

#### 1. Run protoc compiler from the root directory:
`protoc -I customer/ customer/customer.proto --go_out=plugins=grpc:customer`

##### This generates `customer/customer.pb.go`, a Protobuf file with source code that allows us to:
- Create the gRPC server
- Make client RPC calls

#### 2. Run gRPC Applications:

##### a. gRPC Server:
`go run main.go` from `/server` directory or

`go run server/main.go` from project root directory.

##### b. gRPC Client:
`go run main.go` from `/client` directory or

`go run client/main.go` from project root directory.

You should see output similar to this in the client console:

```
2016/10/11 16:02:47 A new Customer has been added with id: 101

2016/10/11 16:02:47 A new Customer has been added with id: 102
 
2020/04/03 17:11:21 Customer: id:101 name:"Stevan Cunningham" email:"stevanc@xyz.com" 
  phone:"480-432-0248" addresses:<street:"2836 E Presidio St" city:"Mesa" state:"AZ" zip:"85213" > 
  addresses:<street:"2400 Renwick Ave" city:"Oklahoma City" state:"OK" zip:"73128" 
  isShippingAddress:true > 

2020/04/03 17:11:21 Customer: id:102 name:"Andrea Anne" email:"andreaannecunningham@xyz.com" 
  phone:"732-757-2924" addresses:<street:"1 Mission Street" city:"Lakewood" state:"CO" zip:"94105" 
  isShippingAddress:true > 
```
   
This means that your gRPC server initialized, and received the correct RPC calls from the client app, which resulted in creating and displaying two new customers.
 
 ***
 
 ### References
 
 ##### gRPC
 https://www.grpc.io/
 
 ##### Protocol Buffers (Protobuf) Language Guide:
 https://developers.google.com/protocol-buffers/docs/proto3
 
 ##### This project specifically:
 https://medium.com/@shijuvar/building-high-performance-apis-in-go-using-grpc-and-protocol-buffers-2eda5b80771b
 