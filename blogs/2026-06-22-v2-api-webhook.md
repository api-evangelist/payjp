---
title: "v2 API の Webhook イベントに含まれるキー名変更に関するお知らせ"
url: "https://pay.jp/info/2026-06-22-110000"
date: "2026-06-22"
feed_url: "https://pay.jp/info/feed.xml"
---
平素より PAY.JP をご利用いただき、誠にありがとうございます。 このたび、v2 API の Webhook イベントの payload に含まれるキーを、API レスポンスのキーと統一する仕様変更を実施いたします。従来、一部のキーが API レスポンスと異なっておりましたが、本変更により両者のキーが一致し、より一貫性のある形式となります。 変更内容 変更前（Webhook） 変更後（API レスポンスと統一） created_date created_at updated_date updated_at meta_data metadata 移行スケジュール 現在〜2026年9月30日（移行期間）: 後方互換のため、変更前・変更後の両方のキーを送信します。 2026年10月1日以降: 変更後（API レスポンスと統一された）のキーのみを送信し、変更前のキーは含まれなくなります。 加盟店様への影響とご対応 移行期間中に、Webhook を受信するシステムが新しいキー（ created_at / updated_at / metadata ）を参照するようご対応をお願いいたします。2026年10月1日以降も旧キー（ created_date / updated_date / meta_data ）を参照したままの場合、値が取得できなくなりますのでご注意ください。 ※ 本変更は、v
