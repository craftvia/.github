<p align="center">
  <a href="https://craftvia.org">
    <img src="./assets/craftvia-wordmark.svg" alt="CraftVia" width="360">
  </a>
</p>

<p align="center">
  <strong>試作から製品までをつなぐ、オープンな組み込み開発基盤。</strong>
</p>

<p align="center">
  <a href="https://craftvia.org/ja/">Webサイト</a> ·
  <a href="https://github.com/craftvia/craftvia-web">Webサイトのソース</a> ·
  <a href="./README.md">English</a>
</p>

---

## CraftViaとは

CraftViaは、**製品指向のマイコンCore**と、開発・計測を担う共通の**Station**を組み合わせたオープンな組み込み開発基盤です。初期の実験から実機への搭載、さらに必要に応じたMCU直載せ設計までを、一続きの開発経路にすることを目指します。

```text
開発・計測する             実機へ持ち出す           必要に応じて卒業する

┌──────────────────┐       ┌──────────────────┐       ┌──────────────────┐
│ Station          │       │ Carrier          │       │ 専用PCB          │
│  ├─ 配線         │       │  ├─ 用途固有回路 │       │                  │
│  ├─ 書き込み     │ ────▶ │  ├─ 外部接続     │ ────▶ │ MCU直載せ設計    │
│  ├─ 電源・計測   │       │  └─ Core         │       │                  │
│  └─ Core         │       └──────────────────┘       └──────────────────┘
└──────────────────┘
```

### Core、Station、Carrier

| 要素 | 役割 | 製品への搭載 |
| --- | --- | --- |
| **Core** | MCUと、その安定動作に必要な回路 | 想定する |
| **Station** | 配線、書き込み、デバッグ、電源操作、計測 | 原則として想定しない |
| **Carrier** | センサー、通信、駆動回路、電源、コネクタなどの用途固有機能 | 想定する |

## 一般的なMCU開発ボードとの違い

一般的なMCU開発ボードは、MCUに加えてデバッガ、USBインターフェース、電源、スイッチ、LEDなどの開発機能を一枚にまとめます。CraftViaは、これらの役割を分離します。

- 繰り返し使用する開発機能を**Station**へ集約する
- **Core**にはMCUと、その安定動作に必要十分な回路だけを搭載する
- 開発済みのCoreをStationからCarrierや実機へそのまま移動できる
- 複数種類のMCUへ同じ設計思想とインターフェースを適用し、共通Station上で開発できる

Coreを永久に使用することが目的ではありません。規模、コスト、面積、使用環境などの要求に応じて、公開された設計資産を利用し、MCU直載せ設計へ移行できることを重視します。

## 開発状況

CraftViaは初期ハードウェア開発段階です。明示がない限り、現在のハードウェアは**未検証**であり、量産利用可能な状態を意味しません。

| ハードウェア | 役割 | 状況 |
| --- | --- | --- |
| **Core-S G031** | Core | Rev0基板発注済み・到着待ち — 未実装・未検証 |
| **Station-S** | Station | Rev0基板発注済み・到着待ち — 未実装・未検証 |
| **MakerCard-S** | MakerCard | Rev0基板発注済み・到着待ち — 未実装・未検証 |
| **Core-S ESP32-C3** | 次期Core | 仕様検討中 |
| **Core-S RP2040** | 次期Core | 仕様検討中 |

## 設計原則

1. **Develop, measure, move, graduate** — Stationで開発・計測し、Coreを実機へ移し、必要になればMCU直載せへ卒業する。
2. **開発機能と動作機能を分離する** — 人が使用する開発機能はStationへ、MCUの動作に必要な機能はCoreへ配置する。
3. **測定可能性を最初から設計する** — 書き込み、ログ、電圧、電流、テストアクセスを後付けにしない。
4. **判断根拠を公開する** — 編集可能な設計ソースや製造データとともに、制約、失敗、測定条件、設計判断を記録する。
5. **実案件で検証して育てる** — 机上の汎用性ではなく、実際の試作、治具、装置開発から得た知見を反映する。

## リポジトリ

| リポジトリ | 役割 |
| --- | --- |
| [`craftvia-web`](https://github.com/craftvia/craftvia-web) | CraftViaプロジェクトサイトのソース |
| [`craftvia-docs`](https://github.com/craftvia/craftvia-docs) | 共通仕様、互換性、設計指針、Getting Started |
| [`craftvia-core-s-g031`](https://github.com/craftvia/craftvia-core-s-g031) | Core-S G031の編集可能な設計ソースと製造データ |
| [`craftvia-station-s`](https://github.com/craftvia/craftvia-station-s) | Station-Sの編集可能な設計ソースと製造データ |
| [`craftvia-makercard-s`](https://github.com/craftvia/craftvia-makercard-s) | MakerCard-Sの編集可能な設計ソースと製造データ |

技術仕様は`craftvia-docs`または各ハードウェアrepoで管理します。このプロフィールは概要と入口を提供するものであり、仕様の重複管理は行いません。

最初に[CraftVia Rev0 Getting Started](https://github.com/craftvia/craftvia-docs/blob/main/guides/getting-started.ja.md)を確認し、使用するハードウェアのREADME、Revision仕様書、検証計画、Release Notesを続けて確認してください。

## ドキュメント、ライセンス、Contribution

個別の表示がない限り、CraftViaのハードウェアにはCERN-OHL-P-2.0、ソフトウェアにはApache-2.0、文書にはCC BY 4.0を適用します。CraftViaの名称・ロゴはKohei Ikedaが所有し、[CraftVia Trademark Policy（英語正本）](../LICENSES/TRADEMARK_POLICY.md)および[参考訳](../LICENSES/TRADEMARK_POLICY.ja.md)で別途定めます。各ハードウェアReleaseには、検証状態、既知の問題、設計Revision、収録する製造データを明記します。

製品固有の問題報告や変更提案は、該当する製品repoのIssueを使用してください。共通仕様、文書修正、互換性に関する質問、プロジェクト全体への問い合わせは、[`craftvia-docs`のIssue](https://github.com/craftvia/craftvia-docs/issues)で受け付けます。ハードウェア動作を報告する場合は、製品Version、PCB Revision、構成、確認できた証拠を記載してください。

> ハードウェア設計とブランド資産は別々の条件で提供します。オープンハードウェア設計を利用・改変できることは、改変品や第三者製造品をCraftVia公式品として表示できることを意味しません。

---

<p align="center"><strong>試し、測り、持ち出し、製品へつなぐ。</strong></p>
