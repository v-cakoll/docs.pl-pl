---
ms.openlocfilehash: ad953a1562db407c04d7860c60eb5964fe6fe2ca
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620347"
---
### <a name="deserialization-of-mailmessage-objects-serialized-under-the-net-framework-45-may-fail"></a>Deserializacja serializowanych obiektów MailMessage w .NET Framework 4,5 może zakończyć się niepowodzeniem

#### <a name="details"></a>Szczegóły

Począwszy od .NET Framework 4,5, <xref:System.Web.Mail.MailMessage> obiekty mogą zawierać znaki inne niż ASCII. W .NET Framework 4 obsługiwane są tylko znaki ASCII. <xref:System.Web.Mail.MailMessage>obiekty, które zawierają znaki inne niż ASCII i które są serializowane w .NET Framework 4,5 lub nowszej, nie mogą być deserializowane w .NET Framework 4.

#### <a name="suggestion"></a>Sugestia

Upewnij się, że kod zapewnia obsługę wyjątków podczas deserializacji <xref:System.Web.Mail.MailMessage> obiektu.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Mały|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe

#### <a name="affected-apis"></a>Dotyczy interfejsów API

-<xref:System.Web.Mail.MailMessage?displayProperty=nameWithType></li></ul>|
