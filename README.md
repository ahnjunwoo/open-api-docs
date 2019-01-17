= Deflow Open Api

== 1. 목록

* (GET) /v1/order - 주문내역 조회
* (GET) /v1/trade - 거래내역 조회
* (DELETE) /v1/order - 주문 취소
* (GET) /v1/common/symbols - 마켓 조회
* (POST) /v1/order - 주문 생성
* (GET) /v1/records - 차트 데이터 조회
* (GET) /v1/ticker - 시세 조회
* (GET) /v1/trades - 최근 거래내역 조회
* (GET) /v1/market/dept - 호가 조회
* (GET) /v1/market - 최근 거래가 조회
* (GET) /v1/order/new - 미체결 주문내역 조회
* (GET) /v1/order/info - 주문 정보 조회
* (GET) /v1/user/accounts - 자산 조회


== 2. 기본규칙

=== 서명
파라미터를 알파벳순으로 정렬하여 keyvalue의 형식으로 알파벳String을 붙이고 마지막으로 sign=MD5(string+secretKey). +

IMPORTANT: 만약 파라미터중value가 NULL일 때, 즉 알파벳 스트링일시 서명알파벳 스티링에 기입되지 않음

.example (create_order)
----
A)파라미터가 아래와 같을경우：
{
    api_key = b819dce1cee32asx2255fdcbb1332aec;
    price = 200;
    side = BUY;
    symbol = ethusdt;
    time = 1536629834271;
    type = 1;
    volume = 10;
}

B)결합완료후：
string = api_keyb819dce1cee32asx2255fdcbb1332aecprice200sideBUYsymbolethusdttime1536629834271type1volume10

C)Hashing :
sign=MD5(string + secretKey)
----

=== Content Type

* content-type : application/x-www-formurlencoded

== 3.오류코드

[cols="3*^", options=header]
|===
|오류코드
|설명
|기타


|0
|성공
| -

|5
|주문 작성 실패
| -

|6
|수량이 최소값보다 작을때
| -

|7
|수량이 최대값보다 클때
| -

|8
|주문 취소 실패
| -

|9
|거래가 동결됨
| -

|13
|죄송합니다, 시스템 오류가 발생하였습니다. 시스템 관리자와 연락해주세요.
| -

|19
|사용할수 있는 금액 부족
| -

|22
|거래 수량 파라미터 부족
| -

|24
|거래 가격 파라미터 부족
| -

|100001
|시스템 이상
| -

|100002
|시스템 업그레이드
| -

|100004
|요구한 파라미터가 합법적이지 않습니다
| -

|100005
|파라미터 서명 오류
| -

|100007
|불법IP
| -

|110002
|알수없는 화폐번호
| -

|110003
|자금 비밀번호 오류
| -

|110004
|출금이 동결되었습니다.
| -

|110005
|사용가능 금액 부족
| -

|110020
|사용자ID가 존재 하지 않습니다.
| -

|110023
|이미 회원가입된 핸드폰 번호입니다.
| -

|110024
|이미 회원가입된 이메일 주소입니다.
| -

|110025
|관리자가 잠근 계정입니다.
| -

|110032
|사용권한이 없습니다.
| -

|110033
|충전 실패
| -

|110034
|출금 실패
| -

|===

== 4-1.(GET) /v1/order - 주문내역 조회

=== request

[cols=3*^,options="header"]
|===
h|필드
h|가입유형
h|설명

|symbol
|필수기입
|마켓 (btcusdt, ethusdt 등)

|pageSize
|선택기입
|화면 사이즈

|page
|선택기입
|페이지

|api_key
|필수기입
|api_key

|time
|필수기입
|타임스탬프

|sign
|필수기입
|서명
|===

=== response

[cols=3*^,options="header"]
|===
h|필드
h|실제예
h|설명

|code
|0
|오류코드

|msg
|"suc"
|메세지

|data
|
|샘플 참조
|===

.샘플 data
----

{
  "data": {
    "orderList": [
      {
        "created_at": 1527333467000,
        "deal_volume": "0.00100000",
        "volume": "0.001",
        "countCoin": "btc",
        "id": 112864,
        "type": 1,
        "remain_volume": "0.00000000",
        "price": "0.07979924",
        "tradeList": [
          {
            "fee": "0.00000000",
            "volume": "0.001",
            "ctime": 1527333467000,
            "id": 56341,
            "price": "0.07979924",
            "deal_price": "0.00007979",
            "feeCoin": "ETH",
            "type": "bid"
          }
        ],
        "baseCoin": "eth",
        "status": 2,
        "source_msg": "API",
        "total_price": "0.00007979",
        "side": "BUY",
        "source": 3,
        "status_msg": "success",
        "avg_price": "0.07979924",
        "side_msg": "bid"
      }
    ],
    "count": 112852
  },
  "code": "0",
  "msg": "suc"
}
----

== 4-2. (GET) /v1/trade - 거래내역 조회

=== request

[cols=3*^,options="header"]
|===
h|필드
h|가입유형
h|설명

|symbol
|필수기입
|마켓 (btcusdt, ethusdt 등)

|pageSize
|선택기입
|화면 사이즈

|page
|선택기입
|페이지

|api_key
|필수기입
|api_key

|time
|필수기입
|타임스탬프

|sign
|필수기입
|서명
|===

=== response

[cols=3*^,options="header"]
|===
h|필드
h|실제예
h|설명

|code
|0
|오류코드

|msg
|"suc"
|메세지

|data
|
|샘플 참조
|===

.샘플 data
----

{
  "code": "0",
  "msg": "suc",
  "data": {
    "count": 2,
    "resultList": [
      {
        "volume": "0.186",
        "side": "SELL",
        "feeCoin": "BTC",
        "price": "0.04400000",
        "fee": "0.00000820",
        "ctime": 1535968300000,
        "deal_price": "0.00820028",
        "id": 140,
        "type": "卖出",
        "bid_id": 282,
        "ask_id": 281
      },
      {
        "volume": "0.186",
        "side": "BUY",
        "feeCoin": "ETH",
        "price": "0.04400000",
        "fee": "0.00018637",
        "ctime": 1535968300000,
        "deal_price": "0.00820028",
        "id": 140,
        "type": "买入",
        "bid_id": 282,
        "ask_id": 281
      }
    ]
  }
}
----

== 4-3. (DELETE) /v1/order - 주문 취소

=== request

[cols=3*^,options="header"]
|===
h|필드
h|가입유형
h|설명

|order_id
|필수기입
|주문 ID

|symbol
|필수기입
|마켓 (btcusdt, ethusdt 등)

|api_key
|필수기입
|api_key

|time
|필수기입
|타임스탬프

|sign
|필수기입
|서명
|===

=== response

[cols=3*^,options="header"]
|===
h|필드
h|실제예
h|설명

|code
|0
|오류코드

|msg
|"suc"
|메세지
|===

== 4-4. (GET) /v1/common/symbols - 마켓 조회
* 서명검증 불필요

=== request

[cols=3*^,options="header"]
|===
h|필드
h|가입유형
h|설명

|없음
|
|

|===

=== response

[cols=3*^,options="header"]
|===
h|필드
h|실제예
h|설명

|code
|0
|오류코드

|msg
|"suc"
|메세지

|data
|
|샘플 참조
|===

.샘플 data
----
{
  "code": "0",
  "msg": "suc",
  "data": [
    {
      "symbol": "btcusdt",
      "count_coin": "usdt",
      "amount_precision": 6,
      "base_coin": "btc",
      "price_precision": 2
    },
    {
      "symbol": "bytusdt",
      "count_coin": "usdt",
      "amount_precision": 3,
      "base_coin": "byt",
      "price_precision": 4
    }
  ]
}
----

== 4-5. (POST) /v1/order - 주문 생성

=== request

[cols=3*^,options="header"]
|===
h|필드
h|가입유형
h|설명

|side
|필수기입
|BUY or SELL

|type
|필수기입
|주문 유형. 1 : 지정가주문, 2 : 시장가주문

|volume
|필수기입
|구매수량（다중，복수필드）

|price
|선택기입
|주문단가 (type=1일 경우)

|symbol
|필수기입
|마켓 (btcusdt, ethusdt 등)

|api_key
|필수기입
|api_key

|time
|필수기입
|타임스탬프

|sign
|필수기입
|서명
|===

=== response

[cols=3*^,options="header"]
|===
h|필드
h|실제예
h|설명

|code
|0
|오류코드

|msg
|"suc"
|메세지
|===

== 4-6. (GET) /v1/records - 차트 데이터 조회
* 서명 검증 불필요

=== request

[cols=3*^,options="header"]
|===
h|필드
h|가입유형
h|설명

|symbol
|필수기입
|마켓 (btcusdt, ethusdt 등)

|period
|필수기입
|기간 (분), 하루는 1440
|===

=== response

[cols=3*^,options="header"]
|===
h|필드
h|실제예
h|설명

|code
|0
|오류코드

|msg
|"suc"
|메세지

|data
|
|샘플 참조
|===

.샘플 data
----
{
  "code": "0",
  "msg": "suc",
  "data": [
    [
      1536001200,    // timestamp
      271.93,             // open
      271.93,             // high
      271.93,             // low
      271.93,             // close
      0                       // trade
    ],
    [
      1536001260,
      271.93,
      271.93,
      271.93,
      271.93,
      0
    ]
  ]
}
----

== 4-7. (GET) /v1/ticker - 시세 조회
* 서명 검증 불필요

=== request

[cols=3*^,options="header"]
|===
h|필드
h|가입유형
h|설명


|symbol
|필수기입
|마켓 (btcusdt, ethusdt 등)
all : 전체 symbol 조회

|===

=== response

[cols=3*^,options="header"]
|===
h|필드
h|실제예
h|설명

|code
|0
|오류코드

|msg
|"suc"
|메세지

|data
|
|샘플 참조
|===

.샘플 data
----
{
  "code": "0",
  "msg": "suc",
  "data": {
    "ethusdt": {
      "high": 1100,
      "vol": 45,
      "last": 790,
      "low": 11,
      "buy": "800.00",
      "sell": "900.00",
      "time": 1531217396533
    }
  }
}
----

== 4-8. (GET) /v1/trades - 최근 거래내역 조회
* 서명 검증 불필요

=== request

[cols=3*^,options="header"]
|===
h|필드
h|가입유형
h|설명

|symbol
|필수기입
|마켓 (btcusdt, ethusdt 등)

|===

=== response

[cols=3*^,options="header"]
|===
h|필드
h|실제예
h|설명

|code
|0
|오류코드

|msg
|"suc"
|메세지

|data
|
|샘플 참조
|===

.샘플 data
----
{
  "code": "0",
  "msg": "suc",
  "data": [
    {
      "amount": 0.01957,
      "price": 790,
      "id": 1665,
      "type": "buy"
    },
    {
      "amount": 0.11336,
      "price": 790,
      "id": 1664,
      "type": "sell"
    }
  ]
}
----

== 4-9. (GET) /v1/market/dept - 호가 조회
* 서명 검증 불필요

=== request

[cols=3*^,options="header"]
|===
h|필드
h|가입유형
h|설명

|symbol
|필수기입
|마켓 (btcusdt, ethusdt 등)

|type
|필수기입
|호가유형，step0, step1, step2（합병호가0-2）；step0时, 정밀도높음

|===

=== response

[cols=3*^,options="header"]
|===
h|필드
h|실제예
h|설명

|code
|0
|오류코드

|msg
|"suc"
|메세지

|data
|
|샘플 참조
|===

.샘플 data
----
{
  "code": "0",
  "msg": "suc",
  "data": {
    "tick": {
      "asks": [
        [ "900", 0.02781 ],            // price, volume
        [ "1000", 0.33263 ]
      ],
      "bids": [
        [ "800", 0.0995 ]
      ],
      "time": 1531217396533
    }
  }
}
----

== 4-10. (GET) /v1/market - 최근 거래가 조회
=== request

[cols=3*^,options="header"]
|===
h|필드
h|가입유형
h|설명

|api_key
|필수기입
|api_key

|time
|필수기입
|타임스탬프

|sign
|필수기입
|서명

|===

=== response

[cols=3*^,options="header"]
|===
h|필드
h|실제예
h|설명

|code
|0
|오류코드

|msg
|"suc"
|메세지

|data
|
|샘플 참조
|===

.샘플 data
----
{
  "code": "0",
  "msg": "suc",
  "data": {
    "qtumbtc": 0.000641,
    "btcusdt": 6439.04,
    "ethbtc": 0.044,
    "bchbtc": 0.08094,
    "bchusdt": 516.89,
    "qtumusdt": 4.041,
    "ethusdt": 790
  }
}
----

== 4-11. (GET) /v1/order/new - 미체결 주문내역 조회

=== request

[cols=3*^,options="header"]
|===
h|필드
h|가입유형
h|설명

|symbol
|필수기입
|마켓 (btcusdt, ethusdt 등)

|pageSize
|선택기입
|화면 사이즈

|page
|선택기입
|페이지

|api_key
|필수기입
|api_key

|time
|필수기입
|타임스탬프

|sign
|필수기입
|서명

|===

=== response

[cols=3*^,options="header"]
|===
h|필드
h|실제예
h|설명

|code
|0
|오류코드

|msg
|"suc"
|메세지

|data
|
|샘플 참조
|===

.샘플 data
----
{
  "code": "0",
  "msg": "suc",
  "data": {
    "count": 2,
    "resultList": [
      {
        "side": "SELL",
        "total_price": "6976.02",
        "created_at": 1536118132923,
        "avg_price": "0.00000000",
        "countCoin": "usdt",
        "source": 1,
        "type": 1,
        "side_msg": "卖出",
        "volume": "0.99657500",
        "price": "7000.00",
        "source_msg": "WEB",
        "status_msg": "未成交",
        "deal_volume": "0.00000000",
        "id": 263,
        "remain_volume": "0.99657500",
        "baseCoin": "btc",
        "tradeList": [],
        "status": 1
      },
      {
        "side": "BUY",
        "total_price": "24.44",
        "created_at": 1536118089957,
        "avg_price": "0.00000000",
        "countCoin": "usdt",
        "source": 1,
        "type": 1,
        "side_msg": "买入",
        "volume": "0.00379800",
        "price": "6436.00",
        "source_msg": "WEB",
        "status_msg": "未成交",
        "deal_volume": "0.00000000",
        "id": 262,
        "remain_volume": "0.00379800",
        "baseCoin": "btc",
        "tradeList": [],
        "status": 1
      }
    ]
  }
}
----

== 4-12. (GET) /v1/order/info - 주문 정보 조회

=== request

[cols=3*^,options="header"]
|===
h|필드
h|가입유형
h|설명

|order_id
|필수기입
|주문 ID

|symbol
|필수기입
|마켓 (btcusdt, ethusdt 등)

|api_key
|필수기입
|api_key

|time
|필수기입
|타임스탬프

|sign
|필수기입
|서명

|===

=== response

[cols=3*^,options="header"]
|===
h|필드
h|실제예
h|설명

|code
|0
|오류코드

|msg
|"suc"
|메세지

|data
|
|샘플 참조
|===

.샘플 data
----
{
  "code": "0",
  "msg": "suc",
  "data": {
    "trade_list": [
      {
        "volume": "0.00900000",
        "feeCoin": "USDT",
        "price": "6431.63",
        "fee": "0.05",
        "ctime": 1534991068000,
        "deal_price": "57.88",
        "id": 55,
        "type": "卖出"
      },
      {
        "volume": "0.00100000",
        "feeCoin": "USDT",
        "price": "6431.63",
        "fee": "0.00",
        "ctime": 1534991089000,
        "deal_price": "6.43",
        "id": 56,
        "type": "卖出"
      }
    ],
    "order_info": {
      "side": "SELL",
      "total_price": "64.31",
      "created_at": 1534991067588,
      "avg_price": "6431.63",
      "countCoin": "usdt",
      "source": 3,
      "type": 1,
      "side_msg": "卖出",
      "volume": "0.01000000",
      "price": "6431.63",
      "source_msg": "API",
      "status_msg": "完全成交",
      "deal_volume": "0.01000000",
      "id": 100,
      "remain_volume": "0.00000000",
      "baseCoin": "btc",
      "tradeList": [
        {
          "volume": "0.00900000",
          "feeCoin": "USDT",
          "price": "6431.63",
          "fee": "0.05",
          "ctime": 1534991068000,
          "deal_price": "57.88",
          "id": 55,
          "type": "卖出"
        },
        {
          "volume": "0.00100000",
          "feeCoin": "USDT",
          "price": "6431.63",
          "fee": "0.00",
          "ctime": 1534991089000,
          "deal_price": "6.43",
          "id": 56,
          "type": "卖出"
        }
      ],
      "status": 2
    }
  }
}
----

== 4-13. (GET) /v1/user/accounts - 자산 조회

=== request

[cols=3*^,options="header"]
|===
h|필드
h|가입유형
h|설명

|api_key
|필수기입
|api_key

|time
|필수기입
|타임스탬프

|sign
|필수기입
|서명
|===

=== response

[cols=3*^,options="header"]
|===
h|필드
h|실제예
h|설명

|code
|0
|오류코드

|msg
|"suc"
|메세지

|data
|
|샘플 참조
|===

.샘플 data
----

{
  "code": "0",
  "msg": "suc",
  "data": {
    "total_asset": "20052.32902812",
    "coin_list": [
      {
        "normal": "8.77629030",
        "locked": "1.85091253",
        "coin": "btc"
      },
      {
        "normal": "331032.69901617",
        "locked": "69751.96400000",
        "coin": "byt"
      }
    ]
  }
}
----
