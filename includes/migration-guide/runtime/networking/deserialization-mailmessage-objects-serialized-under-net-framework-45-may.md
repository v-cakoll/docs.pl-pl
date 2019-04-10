---
ms.openlocfilehash: a6f93bbdf39a1b525e2daeb12afc3a6392a66e30
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235751"
---
### <a name="deserialization-of-mailmessage-objects-serialized-under-the-net-framework-45-may-fail"></a>Deserializacja obiektów MailMessage serializowane w .NET Framework 4.5 może zakończyć się niepowodzeniem

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.5 <xref:System.Web.Mail.MailMessage> obiektów może zawierać znaki spoza zestawu ASCII. W programie .NET Framework 4 obsługiwane są tylko znaki ASCII. <xref:System.Web.Mail.MailMessage> obiekty, które zawierają znaki spoza zestawu ASCII i które są serializowane w ramach programu .NET Framework 4.5 lub nowszej nie mogą być deserializowane w .NET Framework 4.|
|Sugestia|Upewnij się, że kod zapewnia obsługę wyjątków podczas deserializacji <xref:System.Web.Mail.MailMessage> obiektu.|
|Zakres|Mały|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Web.Mail.MailMessage?displayProperty=nameWithType></li></ul>|
