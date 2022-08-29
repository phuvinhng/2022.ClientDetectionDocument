
# API NHẬN DIỆN KHÁCH HÀNG

## Nội dung
* [BaseUrl](#BaseUrl)
* [Đăng nhập](#đăng-nhập)
* [Lấy danh sách thuê bao](#lấy-danh-sách-thuê-bao)
* [Thông tin thuê bao](#lấy-thông-tin-thuê-bao-từ-qlkh)
  - [Từ phân hệ QLKH](#lấy-thông-tin-thuê-bao-từ-qlkh)
  - Từ phân hệ CRM
* [Lịch sử](#lịch-sử-nạp-tiền)
  - [Nạp tiền](#lịch-sử-nạp-tiền)
  - [Khiếu Nại](#lịch-sử-khiếu-nại)
* [Doanh thu](#doanh-thu-tháng)
  * [Theo Tháng](#doanh-thu-tháng)


## BaseUrl

```http
  http://103.63.104.239/ClientDetectionApi
```

## Đăng nhập
#### Giao thức: POST
```http
  /api/authen
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

## Lấy danh sách thuê bao
#### Giao thức: POST
```http
  /api/Isdn/GetListISDN
```

#### Input
| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
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

## Lấy thông tin thuê bao từ QLKH
#### Giao thức: POST
```http
  /api/information/qlkh
```
#### Input
| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `PhoneNumber`      | `string` | **Số điện thoại (không bao gồm số "0"), độ dài 9 ký tự**|

#### Output
```
{
    "Name": "Đinh Thị Minh Nguyệt",
    "BirthDate": "1984-08-01T00:00:00",
    "Sex": "1",
    "ActiveDatetime": "2006-09-19T00:00:00",
    "LoaiTb": "TBTT",
    "Address": "Xã An Viễn H.Trảng Bom Đồng Nai",
    "IdNo": "271662316",
    "IdIssueDate": "2011-03-15T00:00:00",
    "IdIssuePlace": "DNI"
}
```

## Lịch sử nạp tiền
#### Giao thức: POST
```http
/api/history/nap-tien
```
#### Input
| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `PhoneNumber`      | `string` | **Số điện thoại (không bao gồm số "0"), độ dài 9 ký tự**|

#### Output
```
[
    {
        "Isdn": "907158999",
        "MobType": "MC",
        "Code": "C90N",
        "ChargePrice": 90000
    },
    {
        "Isdn": "907158999",
        "MobType": "MC",
        "Code": "C90N",
        "ChargePrice": 90000
    },
    {
        "Isdn": "907158999",
        "MobType": "MC",
        "Code": "C90N",
        "ChargePrice": 90000
    }
    ...
]
```

## Lịch sử khiếu nại
#### Giao thức: POST
```http
/api/history/khieu-nai
```
#### Input
| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `PhoneNumber`      | `string` | **Số điện thoại (không bao gồm số "0"), độ dài 9 ký tự**|

#### Output
```
[
    {
        "Customernumber": "907158999",
        "Startdate": "2022-05-04T08:04:07",
        "Dialednumber": "90908",
        "CompContent": "",
        "CoFeedback": "",
        "ProvincePsc": "Tỉnh Đồng Nai",
        "DistrictPsc": "Thành phố Biên Hòa"
    },
    ...
]
```

## Doanh thu Tháng
#### Giao thức: POST
```http
/api/revenue/monthly
```
#### Input
| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `PhoneNumber`      | `string` | **Số điện thoại (không bao gồm số "0"), độ dài 9 ký tự**|

#### Output
```
[
    {
        "Month": "2022-05-01T00:00:00",
        "ChargeVat": 209030,
        "Charge": 209030
    },
    {
        "Month": "2022-06-01T00:00:00",
        "ChargeVat": 136873,
        "Charge": 136873
    },
    ...
]
```
