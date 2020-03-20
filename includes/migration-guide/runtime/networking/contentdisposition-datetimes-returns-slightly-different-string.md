---
ms.openlocfilehash: 705bbd0e0bf80e0726d41898685a5e166e039f99
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858448"
---
### <a name="contentdisposition-datetimes-returns-slightly-different-string"></a>DateTimes z funkcją rozróżniania treści zwraca nieco inny ciąg

|   |   |
|---|---|
|Szczegóły|Reprezentacje ciągów <xref:System.Net.Mime.ContentDisposition?displayProperty=name>'s zostały zaktualizowane, począwszy od 4.6, <xref:System.DateTime?displayProperty=name> aby zawsze reprezentować składnik godziny a z dwiema cyframi. Jest to zgodne z [RFC822](https://www.ietf.org/rfc/rfc0822.txt) i [RFC2822](https://www.ietf.org/rfc/rfc2822.txt). Powoduje <xref:System.Net.Mime.ContentDisposition.ToString> to, że zwraca nieco inny ciąg w 4.6 w scenariuszach, w których jeden z elementów czasu dyspozycji był przed 10:00 AM. Należy zauważyć, że ContentDispositions są czasami serializowane za <xref:System.Net.Mime.ContentDisposition.ToString> pośrednictwem konwertowania ich na ciągi, więc wszelkie operacje, serializacji lub Wywołania GetHashCode powinny być przeglądane.|
|Sugestia|Nie oczekuj, że reprezentacje ciągów ContentDispositions z różnych wersji programu .NET Framework zostaną poprawnie porównane ze sobą. Przekonwertować ciągi z powrotem do ContentDispositions, jeśli to możliwe, przed przeprowadzeniem porównania.|
|Zakres|Mały|
|Wersja|4.6|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Net.Mime.ContentDisposition.ToString?displayProperty=nameWithType></li><li><xref:System.Net.Mime.ContentDisposition.GetHashCode?displayProperty=nameWithType></li></ul>|
