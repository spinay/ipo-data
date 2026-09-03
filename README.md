# ipo-data

공모주(IPO) 일정 데이터. 앱이 읽어가는 **배포 전용** 저장소다.

```
https://raw.githubusercontent.com/spinay/ipo-data/main/ipos.json
```

## 이 저장소는 손으로 고치지 않는다

`spinay/and`의 GitHub Actions가 매일 09:00 KST에 자동으로 덮어쓴다.
여기에 직접 커밋하면 다음 실행 때 사라진다.
파이프라인 코드와 수정은 `spinay/and/data-pipeline`에서 한다.

## 데이터 출처

- **금융감독원 OpenDART** — 청약일·환불일(납입기일)·확정공모가·주관사·상장일
- 구글 시트 — 자동 수집이 놓친 값 보정 (override)

## 형식

```json
{
  "version": "2026-09-03T06:12:00.000Z",
  "count": 19,
  "ipos": [
    {
      "canonical_key": "2026-08-26_스카이랩스",
      "company_name": "스카이랩스",
      "sector": "IPO",
      "subscription_start": "2026-08-26",
      "subscription_end": "2026-08-27",
      "refund_date": "2026-08-31",
      "listing_date": "2026-09-04",
      "confirmed_price": 13000,
      "min_subscription_qty": 10,
      "deposit_ratio": 0.5,
      "underwriters": ["한국투자증권"],
      "status": "waitingListing",
      "dart_corp_code": "01586923"
    }
  ]
}
```

`canonical_key`는 `청약시작일_회사명`이며 앱의 청약 기록과 영구 연결되는
키다. 데이터가 재배포돼도 안정적으로 유지된다.

`listing_date`가 `null`인 종목은 아직 청약 전이라 상장일이 정해지지 않은
것이다(거래소가 납입 완료 후 확정). 오류가 아니다.

## 고지

투자 판단과 책임은 이용자 본인에게 있다. 데이터의 정확성을 보증하지 않는다.
원본은 [DART 전자공시시스템](https://dart.fss.or.kr)에서 확인할 것.
