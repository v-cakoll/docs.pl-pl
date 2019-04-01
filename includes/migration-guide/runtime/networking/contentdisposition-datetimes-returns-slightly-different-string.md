---
ms.openlocfilehash: 529d1b83c0637f705b725a64aa82e2c053bbfd19
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58467084"
---
### <a name="contentdisposition-datetimes-returns-slightly-different-string"></a>Zwraca ciąg nieco inny, ContentDisposition Data/Godzina

|   |   |
|---|---|
|Szczegóły|Reprezentacji ciągów obiektu <xref:System.Net.Mime.ContentDisposition?displayProperty=name>firmy zostały zaktualizowane, począwszy od 4.6, aby zawsze reprezentuje składnik godziny z <xref:System.DateTime?displayProperty=name> z dwoma cyframi. Pozwala to wykonania [RFC822](https://www.ietf.org/rfc/rfc0822.txt) i [RFC2822](https://www.ietf.org/rfc/rfc2822.txt). Powoduje to, że <xref:System.Net.Mime.ContentDisposition.ToString> zwraca ciąg nieco inne w wersji 4.6 w scenariuszach, w których jeden z elementów czasu dyspozycji zakończyła się przed 10:00:00. Należy pamiętać, że ContentDispositions czasami są serializowane przez konwertowanie ich na ciągi znaków, więc wszelkie <xref:System.Net.Mime.ContentDisposition.ToString> operacji, serializacji lub wywołania metody GetHashCode powinny być zweryfikowane pod.|
|Sugestia|Nie oczekuje, że ciągów reprezentujących ContentDispositions z różnych wersji programu .NET Framework poprawnie zostanie porównany ze sobą. Konwertowanie ciągów do ContentDispositions, jeśli to możliwe, przed przeprowadzeniem porównanie.|
|Zakres|Mały|
|Wersja|4.6|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Net.Mime.ContentDisposition.ToString?displayProperty=nameWithType></li><li><xref:System.Net.Mime.ContentDisposition.GetHashCode?displayProperty=nameWithType></li></ul>|

