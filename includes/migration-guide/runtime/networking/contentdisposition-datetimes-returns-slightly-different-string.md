---
ms.openlocfilehash: c103dff320ae30d02c12ea5c585a47b589da8237
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621310"
---
### <a name="contentdisposition-datetimes-returns-slightly-different-string"></a>ContentDisposition DateTimes zwraca nieco inny ciąg

#### <a name="details"></a>Szczegóły

Reprezentacje ciągów dla <xref:System.Net.Mime.ContentDisposition?displayProperty=fullName> zostały zaktualizowane, począwszy od 4,6, do zawsze reprezentujące składnik godziny z <xref:System.DateTime?displayProperty=fullName> dwoma cyframi. Jest to zgodne z [RFC822](https://www.ietf.org/rfc/rfc0822.txt) i [RFC2822](https://www.ietf.org/rfc/rfc2822.txt). Powoduje to <xref:System.Net.Mime.ContentDisposition.ToString> zwrócenie nieco innego ciągu w 4,6 w scenariuszach, w których jeden z elementów czasu dyspozycji był wcześniejszy niż 10:00 am. Należy zauważyć, że ContentDispositions są czasami serializowane przez konwersję do ciągów, więc <xref:System.Net.Mime.ContentDisposition.ToString> należy przejrzeć wszystkie wywołania operacji, serializacji lub GetHashCode.

#### <a name="suggestion"></a>Sugestia

Nie należy oczekiwać, że reprezentacje ciągów ContentDispositions z różnych wersji .NET Framework będą prawidłowo porównywane ze sobą. Przed przeprowadzeniem porównania przekonwertuj ciągi z powrotem do ContentDispositions, jeśli jest to możliwe.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Mały|
|Wersja|4.6|
|Typ|Środowisko uruchomieniowe

#### <a name="affected-apis"></a>Dotyczy interfejsów API

-<xref:System.Net.Mime.ContentDisposition.ToString?displayProperty=nameWithType></li><li><xref:System.Net.Mime.ContentDisposition.GetHashCode?displayProperty=nameWithType></li></ul>|
