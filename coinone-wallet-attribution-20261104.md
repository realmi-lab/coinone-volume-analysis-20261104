# 온체인 분석의 지갑은 코인원 것인가 — 귀속 확인 (2026-11-05 16:33 KST 재확인)

[온체인 조사](coinone-onchain-20261104.md)에서 본 USDC·USDT·BTC 지갑이 실제로 코인원 것인지, 공개 API로 직접 다시 확인한 결과입니다.

## 결론

USDC(솔라나)와 USDT(트론) 지갑은 코인원 것으로 **확인됨**, BTC(비트코인) 지갑은 코인원 것으로 **추정(중간~높음)** 입니다.

| 자산 (네트워크) | 지갑 | 판정 | 근거 |
|---|---|---|---|
| USDC (솔라나) | 핫월렛 `8TWNcXvh9BXKdgNdRKGAfKzGUYsoVDMKUuAdbMYxCJEA` | 확인됨 | 솔라나 탐색기 Solscan의 공개 이름 'Coinone Hot Wallet'. 공개 노드로 조회하면 USDC 토큰계정 `J1jb7LadTZGYJxy694b8HZfsBeYwpy4ma2V5L5FmTu28`의 주인이 이 지갑이고, 발행 주소가 Circle의 정식 USDC(`EPjFWdd5AufqSSqeM2qN1xzybapC8G4wEGGkZwyTDt1v`)이며, 잔고는 2,220,121.71 USDC입니다(재확인 시각 기준). |
| USDT (트론) | 입출금 허브 `TDoyjmPJHzRFmYfCRLRsPhKjLETwd9fKr9` | 확인됨 | 트론 탐색기 Tronscan의 공식 태그 'Coinone'과 코인원 로고. 2019-03-13에 만들어진 주소입니다. |
| BTC (비트코인) | 운영 허브 `3DGxAYYUA61WrrdbBac8Ra9eA9peAQwTJF` | 추정 (중간~높음) | 직접 붙은 라벨은 없습니다. 거래 추적 서비스 Whale Alert가 코인원으로 표시한 서로 다른 입금 주소 3개와 같은 입금 묶음에 속하고, 여러 입금을 이 주소로 모으는 패턴이 반복됩니다. |
| (참고) RLUSD (XRPL) | `rp2diYfVtpbgEMyaoWnuaWgFCAkqCAEg28`, `rhuCPEoLFYbpbwyhXioSumPKrnfCi3AXJZ` | 확인됨 | XRPScan 공개 이름 'Coinone', 도메인 coinone.co.kr |

- 어느 코인을 어느 네트워크로 주고받는지는 코인원 공식 안내 표로 확인했습니다. USDC = 솔라나(SPL), USDT = 트론(TRC20), BTC = 비트코인, RLUSD = XRPL입니다. [코인원 지원 네트워크](https://support.coinone.co.kr/support/solutions/articles/31000163237)
- 솔라나에서 입금을 모아 핫월렛으로 보내는 주소 `99JuxP6CnGZTR8v9bkUpMfPmBgubQ5SZxAXVVV2sQN7g`와 그 수수료를 내는 주소 `57wqAB7uqGcML918tBy3d63wW9zHJeDdjNCrNBEGrxDF`도 코인원 것으로 추정됩니다(중간). 공식 소유 증빙은 없습니다.

## 주의할 점

1. 라벨은 블록체인 탐색기(Solscan, Tronscan, XRPScan)와 Whale Alert가 붙인 것이며, 코인원이 직접 주소를 공개한 것은 아닙니다.
2. 조사한 것은 코인원의 주요 핫월렛입니다. 콜드월렛과 고객별 입금 주소는 다 담기지 않았으므로, 온체인 표의 금액은 이 지갑들에서 관측한 흐름이지 코인원 전체 입출금이 아닙니다.
3. 이 지갑의 돈은 고객 자산이 함께 들어 있는 거래소 지갑입니다. 보이는 흐름은 고객의 입출금을 코인원이 처리한 것이지, 코인원이 직접 매매한 자금이 아닙니다.

## 재확인 방법 (로그인·키 불필요)

- 트론 태그: `https://apilist.tronscanapi.com/api/account?address=TDoyjmPJHzRFmYfCRLRsPhKjLETwd9fKr9` → `addressTag`
- XRPL 이름: `https://api.xrpscan.com/api/v1/account/<주소>` → `accountName`
- 솔라나 토큰계정 주인·발행 주소·잔고: 공개 RPC `https://api.mainnet-beta.solana.com`에 `getAccountInfo`(`J1jb7LadTZGYJxy694b8HZfsBeYwpy4ma2V5L5FmTu28`, `jsonParsed`) → `owner`, `mint`, `tokenAmount`
- 솔라나 핫월렛 이름: Solscan 계정 페이지 `https://solscan.io/account/8TWNcXvh9BXKdgNdRKGAfKzGUYsoVDMKUuAdbMYxCJEA`
