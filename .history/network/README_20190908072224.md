## Xây dựng mô hình mạng dành cho dự án xác thực văn bằng
### Mô hình mạng này dựa trên mô hình mạng byfn (build your first network)

1. Tài nguyên cần có trước khi bắt đầu:

2. Các bước tiến hành:
```bash
# launch network; create channel and join peer to channel
cd ./first-network
echo y | ./byfn.sh down 
# Stop all docker container relate with byfn
echo y | ./byfn.sh up -a -n -s couchdb

#  -a - launch certificate authorities (no certificate authorities are launched by default)
#  -n - do not deploy chaincode (abstore chaincode is deployed by default)
#  -s couchdb use coucdb as database for world state
```

Sau khi khởi khởi chạy lệnh trên, một network theo đúng mô hình của byfn sẽ được khởi tạo, sau này nếu có tùy chỉnh trong mô hình network thì sẽ sửa đổi trong file `./byfn` mà thôi.

Theo mặc định, tên channel sẽ được khởi tạo là `mychannel`, giá trị này có thể thay đổi.

Tùy thuộc vào vị trí lưu trữ chaincode ở trên máy tính mà thay đổi giá trị này cho phù hợp
```yaml
  volumes:
        - /var/run/:/host/var/run/
        - ./../chaincode/:/opt/gopath/src/github.com/chaincode
        - ./crypto-config:/opt/gopath/src/github.com/hyperledger/fabric/peer/crypto/
        - ./scripts:/opt/gopath/src/github.com/hyperledger/fabric/peer/scripts/
        - ./channel-artifacts:/opt/gopath/src/github.com/hyperledger/fabric/peer/channel-artifacts
```


