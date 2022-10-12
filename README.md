# API NHẬN DIỆN KHÁCH HÀNG

## Nội dung

- [BaseUrl](#BaseUrl)
- [Xác thực](#đăng-nhập)
  - [Đăng nhập](#đăng-nhập)
  - [Kiểm tra Access Token](#kiểm-tra-access-token)
  - [RefreshToken](#refreshtoken)
- [Lấy danh sách thuê bao](#lấy-danh-sách-thuê-bao)
- [Thông tin thuê bao](#lấy-thông-tin-thuê-bao-từ-qlkh)
  - [Từ phân hệ QLKH](#lấy-thông-tin-thuê-bao-từ-qlkh)
  - [Từ phân hệ CRM](#lấy-thông-tin-thuê-bao-từ-crm)
  - [Số dư](#số-dư)
  - [Các gói cước đang sử dụng](#các-gói-cước-đang-sử-dụng)
  - [Tư vấn gói cước](#tư-vấn-gói-cước)
  - [Khuyến nghị số thuê bao](#khuyến-nghị-số-thuê-bao)
- [Lịch sử](#lịch-sử-nạp-tiền)
  - [Nạp tiền](#lịch-sử-nạp-tiền)
  - [Sử dụng gói cước](#sử-dụng-gói-cước)
  - [Khiếu Nại](#lịch-sử-khiếu-nại)
  - [MNP - chuyển mạng](#lịch-sử-mnp)
  - [Quà tặng](#lịch-sử-quà-tặng)
  - [Tương tác 3 tháng gần nhất](#lịch-sử-tương-tác)
- [Doanh thu](#doanh-thu-tháng)
  - [Theo Tháng](#doanh-thu-tháng)
- [Platform](#app-platform)
  - [App](#app-platform)
- [Khách hàng](#hành-vi-khách-hàng)
  - [Hành vi khách hàng](#hành-vi-khách-hàng)
- [Tiện ích](#tiện-ích)
  - [Gửi tin nhắn cho khách hàng VIP](#tiện-ích)

## BaseUrl

```http
  http://103.63.104.239/ClientDetectionApi
```

## Đăng nhập

#### Giao thức: POST

```http
  /api/account/authen
```

#### Input (JSON)

| Parameter  | Type     | Description       |
| :--------- | :------- | :---------------- |
| `Username` | `string` | **Tên đăng nhập** |
| `Password` | `string` | **Mật khẩu**      |

#### Output

<details>
  <summary>Hiển thị</summary>
  
```
{
    "Token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJVc2VyTmFtZSI6InZpbmgubnAiLCJleHAiOjE2NjI2NTY1OTIsImlzcyI6Ik1vYmlGb25lIDgiLCJhdWQiOiJNb2JpRm9uZSA4In0.zOMUTD8cry0H6yHu-zjQx0anI6KkQKSHIyK6yYPOFRs",
    "RefreshToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJVc2VyTmFtZSI6InZpbmgubnAiLCJleHAiOjE2NjMyNTc3OTIsImlzcyI6Ik1vYmlGb25lIDgiLCJhdWQiOiJNb2JpRm9uZSA4In0.Jdvhij2cu46SPD7NV1htMGH7HAfoFsafvcFfaaLFirA",
    "UserName": "vinh.np"
}
```
  
</details>

#### Lưu ý:

- Tại môi trường Dev:
  - Sử dụng **Password** mặc định để đăng nhập: **Được cung cấp bởi MobiFone**

## Kiểm tra Access Token

#### Giao thức: POST

```http
  /api/account/check-access-token
```

####

#### Input (JSON)

| Parameter     | Type     | Description                                     |
| :------------ | :------- | :---------------------------------------------- |
| `AccessToken` | `string` | **Access Token lấy được từ Login API trước đó** |

#### Output

<details>
  <summary>Hiển thị</summary>
  
```
{
    "Status": "Ok",
    "UserName": "vinh.np"
}
```
  
</details>

## RefreshToken

#### Giao thức: POST

```http
  /api/account/refresh-token
```

####

#### Input (JSON)

| Parameter      | Type     | Description                                      |
| :------------- | :------- | :----------------------------------------------- |
| `RefreshToken` | `string` | **Refresh Token lấy được từ Login API trước đó** |

#### Output

<details>
  <summary>Hiển thị</summary>
  
```
{
    "Token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJVc2VyTmFtZSI6InZpbmgubnAiLCJleHAiOjE2NjI2NTgyMTUsImlzcyI6Ik1vYmlGb25lIDgiLCJhdWQiOiJNb2JpRm9uZSA4In0.1DdacDaVHdWQZd-uDAs0njRRzqHY06MXCCf7CPXut2s",
    "RefreshToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJVc2VyTmFtZSI6InZpbmgubnAiLCJleHAiOjE2NjMyNTk0MTUsImlzcyI6Ik1vYmlGb25lIDgiLCJhdWQiOiJNb2JpRm9uZSA4In0.EPh5B7fFWo2HqV4O8V4GT4ss321XW0ceLONJtmTkLyU",
    "UserName": "vinh.np"
}
```
  
</details>

## Lấy danh sách thuê bao

#### Giao thức: POST

```http
  /api/Isdn/GetListISDN
```

#### Input (JSON)

| Parameter               | Type     | Description           |
| :---------------------- | :------- | :-------------------- |
| `Bearer Token (Header)` | `string` | **Jwt**               |
| `Identity`              | `string` | **Số CMND hoặc CCCD** |

#### Output

<details>
  <summary>Hiển thị</summary>
  
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
  
</details>

## Lấy thông tin thuê bao từ QLKH

#### Giao thức: POST

```http
  /api/information/qlkh
```

#### Input (JSON)

| Parameter               | Type     | Description                                              |
| :---------------------- | :------- | :------------------------------------------------------- |
| `Bearer Token (Header)` | `string` | **Jwt**                                                  |
| `PhoneNumber`           | `string` | **Số điện thoại (không bao gồm số "0"), độ dài 9 ký tự** |

#### Output

<details>
  <summary>Hiển thị</summary>
  
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
  
</details>

## Lấy thông tin thuê bao từ CRM

#### Giao thức: POST

```http
  /api/information/crm
```

#### Input (JSON)

| Parameter               | Type     | Description                                              |
| :---------------------- | :------- | :------------------------------------------------------- |
| `Bearer Token (Header)` | `string` | **Jwt**                                                  |
| `PhoneNumber`           | `string` | **Số điện thoại (không bao gồm số "0"), độ dài 9 ký tự** |

#### Output

<details>
  <summary>Hiển thị</summary>
  
```
{
    "IssueId": 3603563,
    "Phone": "907158999",
    "ContactName": "Đinh Thị Minh Nguyệt",
    "GroupId": 32059,
    "ProvinceId": 31762,
    "DistrictId": 32059,
    "Email": "",
    "Custom000557": "C",
    "Custom000558": "",
    "Custom000559": "E",
    "Custom000560": "Y",
    "Custom000561": "Y",
    "Custom000562": "Ca Nhan",
    "Custom000563": "Tra Truoc",
    "Custom000564": "Hang Dong",
    "Custom000565": "Dang Hoat Dong",
    "Custom000566": "Binh Thuong",
    "Custom000567": "0",
    "Custom000568": "700",
    "Custom000569": "0",
    "Custom000570": "0",
    "Custom000571": "0",
    "Custom000572": "700",
    "Custom000573": "452",
    "Custom000574": "17986",
    "Custom000575": "34523",
    "Custom000576": "930",
    "Custom000577": "2100",
    "Custom000578": "350",
    "Custom000579": "225",
    "Custom000580": "0",
    "Custom000581": "0",
    "Custom000582": "12000",
    "Custom000583": "12350",
    "Custom000584": "12350",
    "Custom000585": "90000",
    "Custom000586": "90000",
    "Custom000587": "90000",
    "Custom000588": "103607",
    "Custom000589": "122436",
    "Custom000590": "137223",
    "Custom000593": "",
    "Custom000594": "0",
    "Custom000595": "1",
    "Custom000596": "0",
    "Custom000597": "1",
    "Custom000598": "0",
    "Custom000599": "200000",
    "Custom000600": "0",
    "Custom000601": "200000",
    "Custom000602": "156771",
    "Custom000603": "157471",
    "Custom000604": "",
    "Custom000605": "",
    "Custom000610": "",
    "Custom000611": "COMBO",
    "Custom000612": "T      ",
    "Custom000613": "0",
    "Custom000614": "0",
    "Custom000615": "KHONG",
    "Custom000616": "CO",
    "Custom000617": "350",
    "Custom000618": "0",
    "Custom000619": "1",
    "Custom000620": "0",
    "Custom000621": "01/08/1984",
    "Custom000630": "CLIP,TTDT,GPRS,RESETSGSN,CH",
    "Custom000631": "0",
    "Custom000632": "0",
    "Custom000633": "1",
    "Custom000634": "",
    "Custom000635": "96",
    "Custom000636": "52",
    "Custom000637": "89",
    "Custom000638": "",
    "Custom000639": "3",
    "Custom000640": "6",
    "Custom000641": "1",
    "Custom000642": "2",
    "Custom000643": "47",
    "Custom000644": "",
    "Custom000645": "",
    "Custom000646": "",
    "Custom000647": "1",
    "Custom000648": "6",
    "Custom000649": "1",
    "Custom000650": "255",
    "Custom000651": "518",
    "Custom000652": "",
    "Custom000653": "",
    "Custom000658": "31762:84,31792:3,31816:4",
    "Custom000659": "",
    "Custom000660": "",
    "Custom000661": "",
    "Custom000662": "",
    "Custom000663": "",
    "Custom000664": "",
    "Custom000665": "",
    "Custom000666": "N",
    "Custom000667": "",
    "Custom000668": "38",
    "Custom000669": "271662316",
    "Custom000670": "NVVP",
    "Custom000671": "7",
    "Custom000672": "16",
    "Custom000673": "21",
    "Custom000674": "28",
    "Custom000675": "Active",
    "Custom000676": "GALAXY A70 (SM-A705F,DS)",
    "Custom000677": "SAMSUNG",
    "Custom000678": "Smart Phone",
    "Custom000679": "Deny",
    "Custom000680": "C90N",
    "Custom000681": "",
    "Custom000682": "",
    "Custom000683": "",
    "Custom000684": "",
    "Custom000689": "NU",
    "Custom000690": "",
    "Custom000691": "DNI",
    "Custom000692": "BHO",
    "Custom000693": "Y",
    "Custom000694": "4G",
    "Custom000695": "Android",
    "IssueDatetime": "2022-09-08T21:42:24",
    "Custom000696": "DNI_BHO",
    "Custom000697": "MC",
    "Custom000698": "VIE",
    "Custom000699": "2006-09-19T00:00:00",
    "Custom000700": "8E,8P,CK30,CK50,CK70,ED100,ED50,K90",
    "Custom000705": "52961",
    "Custom000706": "3380",
    "Custom000707": "225",
    "Custom000708": "36700",
    "Custom000709": "270000",
    "Custom000710": "363266",
    "Custom000711": "Y",
    "Custom000712": "N",
    "Custom000763": "SIM 4G",
    "Custom000766": "N",
    "Custom000767": "",
    "Custom000768": "",
    "Custom000771": "",
    "Custom000772": "",
    "Custom000773": "",
    "Custom000782": "",
    "Custom000783": "",
    "Custom000784": "",
    "Custom000785": "",
    "Custom000776": "Y",
    "Custom000777": "2022-05-04T00:00:00",
    "Custom000786": "DNBH68",
    "Custom000787": "4CTH00541",
    "Custom000788": "",
    "Custom000789": 288332,
    "Custom000790": 231743,
    "Custom000791": "8",
    "Custom000803": 4,
    "Custom000804": 4,
    "Custom000805": 4,
    "Custom000806": 0,
    "Custom000807": 0,
    "Custom000808": "Tỉnh Đồng Nai",
    "Custom000809": "Thành phố Biên Hòa",
    "Custom000810": 0,
    "Custom000811": "C90N",
    "Custom000812": "2022-09-09T00:00:00",
    "Custom000813": 0,
    "Custom000814": 0,
    "Custom000815": 0,
    "Custom000816": 0,
    "Custom000817": 0,
    "Custom000818": "0",
    "Custom000819": 293061,
    "Custom000820": 755515,
    "Custom000821": "D90",
    "Custom000822": "",
    "SubId": 14450260,
    "Custom000854": "",
    "Custom000855": "",
    "Custom000868": "DNBH68M4BC"
}
```
  
</details>

## Số dư

#### Giao thức: POST

```http
  /api/information/balance
```

#### Input (JSON)

| Parameter               | Type     | Description                                              |
| :---------------------- | :------- | :------------------------------------------------------- |
| `Bearer Token (Header)` | `string` | **Jwt**                                                  |
| `PhoneNumber`           | `string` | **Số điện thoại (không bao gồm số "0"), độ dài 9 ký tự** |

#### Lưu ý:

- Số thuê bao tại CRM có thể có dữ liệu hoặc không:
  - Nếu có dữ liệu sẽ lấy được **số dư**
  - Nếu không sẽ trả về số dư là **0**

#### Output

<details>
  <summary>Hiển thị</summary>
  
```
{
    "Balance": "0"
}
```
  
</details>

## Các gói cước đang sử dụng

#### Giao thức: POST

```http
  /api/information/using-package
```

#### Input (JSON)

| Parameter               | Type     | Description                                              |
| :---------------------- | :------- | :------------------------------------------------------- |
| `Bearer Token (Header)` | `string` | **Jwt**                                                  |
| `PhoneNumber`           | `string` | **Số điện thoại (không bao gồm số "0"), độ dài 9 ký tự** |

#### Lưu ý:

- Số thuê bao tại CRM có thể có dữ liệu hoặc không:
  - Nếu có dữ liệu sẽ lấy được **các gói cước**
  - Nếu không sẽ trả về empty

#### Output

<details>
  <summary>Hiển thị</summary>
  
```
{
    "Packages": "D15"
}
```
  
</details>

## Tư vấn gói cước

#### Giao thức: POST

```http
  /api/information/recommend-package
```

#### Input (JSON)

| Parameter               | Type     | Description                                              |
| :---------------------- | :------- | :------------------------------------------------------- |
| `Bearer Token (Header)` | `string` | **Jwt**                                                  |
| `PhoneNumber`           | `string` | **Số điện thoại (không bao gồm số "0"), độ dài 9 ký tự** |

#### Lưu ý:

- Số thuê bao tại CRM có thể có dữ liệu hoặc không:
  - Nếu có dữ liệu sẽ lấy được **các gói cước có thể tư vấn**
  - Nếu không sẽ trả về empty

#### Output

<details>
  <summary>Hiển thị</summary>
  
```
{
    "Packages": "8E,8P,CK30,CK50,CK70,ED100,ED50"
}
```
  
</details>

## Khuyến nghị số thuê bao

#### Giao thức: POST

```http
  /api/information/suggest-phone-number
```

#### Input (JSON)

| Parameter               | Type     | Description                                              |
| :---------------------- | :------- | :------------------------------------------------------- |
| `Bearer Token (Header)` | `string` | **Jwt**                                                  |
| `PhoneNumber`           | `string` | **Số điện thoại (không bao gồm số "0"), độ dài 9 ký tự** |

#### Output

<details>
  <summary>Hiển thị</summary>
  
```
{
    "Message": "Số thuê bao khuyến nghị sử dụng",
    "PhoneNumbers": [
        {
            "TelNumber": "786030483"
        },
        {
            "TelNumber": "785946488"
        },
        {
            "TelNumber": "797946488"
        },
        {
            "TelNumber": "786046488"
        },
        {
            "TelNumber": "786346488"
        },
        {
            "TelNumber": "798546488"
        }
    ]
}
```
  
</details>

## Lịch sử nạp tiền

#### Giao thức: POST

- Lịch sử nạp tiền 3 tháng gần nhất
- Với n (tháng hiện tại), n-1 (tháng trước đó), ...

```http
/api/history/nap-tien
```

#### Input (JSON)

| Parameter               | Type     | Description                                              |
| :---------------------- | :------- | :------------------------------------------------------- |
| `Bearer Token (Header)` | `string` | **Jwt**                                                  |
| `PhoneNumber`           | `string` | **Số điện thoại (không bao gồm số "0"), độ dài 9 ký tự** |

#### Lưu ý

- Vì dữ liệu được lấy từ CRM nên một vài số thuê bao có thể sẽ không có dữ liệu
  - Nếu không có dữ liệu sẽ trả về danh sách rỗng **[]**

#### Output

<details>
  <summary>Hiển thị</summary>
  
```
[
    {
        "Title": "Tháng 10",
        "Charge": "0",
        "Code": "n"
    },
    {
        "Title": "Tháng 9",
        "Charge": "0",
        "Code": "n-1"
    },
    {
        "Title": "Tháng 8",
        "Charge": "0",
        "Code": "n-2"
    },
    {
        "Title": "Tháng 7",
        "Charge": "0",
        "Code": "n-3"
    }
]
```
  
</details>

## Sử dụng gói cước

#### Giao thức: POST

```http
/api/history/su-dung-goi
```

#### Input (JSON)

| Parameter               | Type     | Description                                              |
| :---------------------- | :------- | :------------------------------------------------------- |
| `Bearer Token (Header)` | `string` | **Jwt**                                                  |
| `PhoneNumber`           | `string` | **Số điện thoại (không bao gồm số "0"), độ dài 9 ký tự** |

#### Output

<details>
  <summary>Hiển thị</summary>
  
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
  
</details>

## Lịch sử khiếu nại

#### Giao thức: POST

```http
/api/history/khieu-nai
```

#### Input (JSON)

| Parameter               | Type     | Description                                              |
| :---------------------- | :------- | :------------------------------------------------------- |
| `Bearer Token (Header)` | `string` | **Jwt**                                                  |
| `PhoneNumber`           | `string` | **Số điện thoại (không bao gồm số "0"), độ dài 9 ký tự** |

#### Output

<details>
  <summary>Hiển thị</summary>
  
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
  
</details>

## Lịch sử MNP

#### Giao thức: POST

```http
/api/history/mnp
```

#### Input (JSON)

| Parameter               | Type     | Description                                              |
| :---------------------- | :------- | :------------------------------------------------------- |
| `Bearer Token (Header)` | `string` | **Jwt**                                                  |
| `PhoneNumber`           | `string` | **Số điện thoại (không bao gồm số "0"), độ dài 9 ký tự** |

#### Output

<details>
  <summary>Hiển thị</summary>
  
```
[
    {
        "MnpRegistrationId": 5341317,
        "RegInfDate": "2022-09-09T15:14:47",
        "TimerDescription": "Thời gian hết hạn timer: 12/09/2022 14:14:47",
        "TrangThaiChuyenMang": "Hoàn tất chuyển",
        "NhaMang": "Vinaphone",
        "LoaiChuyenMang": "Chuyển mạng đi",
        "TrangThaiChuyenMangCu": "Mở/Cắt trên tổng đài",
        "TrangThaiThanhcong": "Thành công"
    },
    {
        "MnpRegistrationId": 5268712,
        "RegInfDate": "2022-07-22T09:43:54",
        "TimerDescription": "Thời gian hết hạn timer: 25/07/2022 08:43:54",
        "TrangThaiChuyenMang": "Hủy không đủ điều kiện",
        "NhaMang": "Vinaphone",
        "LoaiChuyenMang": "Chuyển mạng đi",
        "TrangThaiChuyenMangCu": "Không đủ điều kiện",
        "TrangThaiThanhcong": "Chưa thành công"
    },
    {
        "MnpRegistrationId": 5334970,
        "RegInfDate": "2022-09-06T09:27:21",
        "TimerDescription": "",
        "TrangThaiChuyenMang": "Hủy không đủ điều kiện",
        "NhaMang": "Vinaphone",
        "LoaiChuyenMang": "Chuyển mạng đi",
        "TrangThaiChuyenMangCu": "Không đủ điều kiện",
        "TrangThaiThanhcong": "Chưa thành công"
    },
    {
        "MnpRegistrationId": 5277514,
        "RegInfDate": "2022-07-27T18:08:20",
        "TimerDescription": "Thời gian hết hạn timer: 28/07/2022 16:00:20",
        "TrangThaiChuyenMang": "Hủy không đủ điều kiện",
        "NhaMang": "Vinaphone",
        "LoaiChuyenMang": "Chuyển mạng đi",
        "TrangThaiChuyenMangCu": "Không đủ điều kiện",
        "TrangThaiThanhcong": "Chưa thành công"
    },
    {
        "MnpRegistrationId": 5273928,
        "RegInfDate": "2022-07-26T10:39:09",
        "TimerDescription": "Thời gian hết hạn timer: 27/07/2022 09:39:09",
        "TrangThaiChuyenMang": "Hủy không đủ điều kiện",
        "NhaMang": "Vinaphone",
        "LoaiChuyenMang": "Chuyển mạng đi",
        "TrangThaiChuyenMangCu": "Không đủ điều kiện",
        "TrangThaiThanhcong": "Chưa thành công"
    },
    {
        "MnpRegistrationId": 5271563,
        "RegInfDate": "2022-07-25T11:03:08",
        "TimerDescription": "Thời gian hết hạn timer: 26/07/2022 10:03:08",
        "TrangThaiChuyenMang": "Hủy không đủ điều kiện",
        "NhaMang": "Vinaphone",
        "LoaiChuyenMang": "Chuyển mạng đi",
        "TrangThaiChuyenMangCu": "Không đủ điều kiện",
        "TrangThaiThanhcong": "Chưa thành công"
    }
]
```
  
</details>

## Lịch sử quà tặng

#### Giao thức: POST

```http
/api/history/qua-tang
```

#### Input (JSON)

| Parameter               | Type     | Description                                              |
| :---------------------- | :------- | :------------------------------------------------------- |
| `Bearer Token (Header)` | `string` | **Jwt**                                                  |
| `PhoneNumber`           | `string` | **Số điện thoại (không bao gồm số "0"), độ dài 9 ký tự** |

#### Output

<details>
  <summary>Hiển thị</summary>
  
```
[
    {
        "Year": 2022,
        "ChuongTrinh": "Quà Sinh nhật KNDL",
        "HanChonQua": "2022-07-14T00:00:00",
        "QuaDaChon": "Đèn LED để bàn thông minh Baseus",
        "TrangThai": "Đã nhận"
    },
    {
        "Year": 2021,
        "ChuongTrinh": "Quà Sinh nhật KNDL",
        "HanChonQua": "2021-07-14T00:00:00",
        "QuaDaChon": "Bộ đồ ăn Minh Long",
        "TrangThai": "Đã nhận"
    },
    {
        "Year": 2020,
        "ChuongTrinh": "Quà Sinh nhật KNDL",
        "HanChonQua": "2020-07-15T00:00:00",
        "QuaDaChon": "",
        "TrangThai": "Chưa nhận"
    },
    {
        "Year": 2019,
        "ChuongTrinh": "Quà Sinh nhật KNDL",
        "HanChonQua": "2019-07-14T00:00:00",
        "QuaDaChon": "Máy xay sinh tố Philip",
        "TrangThai": "Đã nhận"
    },
    {
        "Year": 2018,
        "ChuongTrinh": "Quà Sinh nhật KNDL",
        "HanChonQua": "2018-07-14T00:00:00",
        "QuaDaChon": "",
        "TrangThai": "Chưa nhận"
    }
]
```
  
</details>

## Lịch sử tương tác

#### Giao thức: POST

```http
/api/history/three-months-trace
```

#### Input (JSON)

| Parameter               | Type     | Description                                              |
| :---------------------- | :------- | :------------------------------------------------------- |
| `Bearer Token (Header)` | `string` | **Jwt**                                                  |
| `PhoneNumber`           | `string` | **Số điện thoại (không bao gồm số "0"), độ dài 9 ký tự** |

#### Output

<details>
  <summary>Hiển thị</summary>
  
```
[
    {
        "IssueDatetime": "2022-09-12T14:56:18",
        "Description": "Huy thue bao 788289363 mstrHLRIN = 11 va huy SIM 452019960930253, giữ lại AUC"
    }
]
```
  
</details>

## Doanh thu Tháng

#### Giao thức: POST

```http
/api/revenue/monthly
```

#### Input (JSON)

| Parameter               | Type     | Description                                              |
| :---------------------- | :------- | :------------------------------------------------------- |
| `Bearer Token (Header)` | `string` | **Jwt**                                                  |
| `PhoneNumber`           | `string` | **Số điện thoại (không bao gồm số "0"), độ dài 9 ký tự** |

#### Output

<details>
  <summary>Hiển thị</summary>
  
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
  
</details>

## App Platform

#### Giao thức: POST

```http
/api/platform/app
```

#### Input (JSON)

| Parameter               | Type     | Description                                              |
| :---------------------- | :------- | :------------------------------------------------------- |
| `Bearer Token (Header)` | `string` | **Jwt**                                                  |
| `PhoneNumber`           | `string` | **Số điện thoại (không bao gồm số "0"), độ dài 9 ký tự** |

#### Output

<details>
  <summary>Hiển thị</summary>
  
```
[
    {
        "SubsId": 908168644,
        "Dichvu": "Platform_Amnhac",
        "SoNgayActive": 43
    }
    ...
]
```
  
</details>

## Hành vi khách hàng

#### Giao thức: POST

```http
/api/customer/behaviors
```

#### Input (JSON)

| Parameter               | Type     | Description                                              |
| :---------------------- | :------- | :------------------------------------------------------- |
| `Bearer Token (Header)` | `string` | **Jwt**                                                  |
| `PhoneNumber`           | `string` | **Số điện thoại (không bao gồm số "0"), độ dài 9 ký tự** |

#### Output

<details>
  <summary>Hiển thị</summary>
  
```
{
    "Behaviors": "zalo,truyen"
}
```
#### Lưu ý: Nếu không có dữ liệu sẽ trả về "Behaviors":""
  
</details>

## Tiện ích

#### Giao thức: POST

```http
/api/customer/send-sms-vip
```

#### Input (JSON)

| Parameter               | Type     | Description                                              |
| :---------------------- | :------- | :------------------------------------------------------- |
| `Bearer Token (Header)` | `string` | **Jwt**                                                  |
| `PhoneNumber`           | `string` | **Số điện thoại (không bao gồm số "0"), độ dài 9 ký tự** |
| `CustomerName`          | `string` | **Họ và tên của khách hàng VIP**                         |
| `CustomerPhoneNumber`   | `string` | **Số điện thoại của khách hàng VIP (bao gồm cả số "0")** |

#### Lưu ý

- **PhoneNumber** là số điện thoại cần được nhận tin nhắn

#### Output

<details>
  <summary>Hiển thị</summary>
  
```
{
    "Message": "Gửi tin nhắn thành công"
}
```
  
</details>
