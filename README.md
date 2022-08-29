
## API NHẬN DIỆN KHÁCH HÀNG

#### BaseUrl

```http
  http://103.63.104.239/ClientDetectionApi
```

#### Đăng nhập

```http
  POST /api/authen
```
#### Input
| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `Username` | `string` | **Tên đăng nhập**|
| `Password` | `string` | **Mật khẩu**|

#### Output
```
{
    "Token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJVc2VyTmFtZSI6InZpbmgubnAiLCJleHAiOjE2NjE3NDMyMzIsImlzcyI6Ik1vYmlGb25lIDgiLCJhdWQiOiJNb2JpRm9uZSA4In0.W-QynIJoPElaO6QKknyHc7hmfWizlF_KgIaLZowDRY8",
    "UserName": "vinh.np"
}
```


#### Lưu ý: 

- Tại môi trường Dev: 
  - Sử dụng **Password** mặc định để đăng nhập: **mbf8@2022**

#### Lấy danh sách thuê bao

```http
  POST /api/Isdn/GetListISDN
```

#### Input
| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `Bearer Token (Header)`      | `string` | **Jwt**|
| `Identity`      | `string` | **Số CMND hoặc CCCD**|

#### Output
```
[
    {
        "HlrIsdn": "1286637133",
        "Name": "Nguyễn Thị Bích Thuỷ",
        "ContractDate": "",
        "Loaitb": "TBTT"
    },
    {
        "HlrIsdn": "1267325559",
        "Name": "Nguyễn Thị Bích Thủy",
        "ContractDate": "",
        "Loaitb": "TBTT"
    },
    {
        "HlrIsdn": "854916863",
        "Name": "Nguyễn Thị Bích Thủy",
        "ContractDate": "2019-04-02T00:00:00",
        "Loaitb": "TBTT"
    },
    ...
]
```

