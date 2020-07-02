---
ms.openlocfilehash: f7dcf9c4c3dc7ea536ddc847769a1a30f1298bb2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617281"
---
### <a name="systemuriiswellformeduristring-method-returns-false-for-relative-uris-with-a-colon-char-in-first-segment"></a>Metoda System. URI. IsWellFormedUriString zwraca wartość false dla względnych identyfikatorów URI z dwukropkiem w pierwszym segmencie

#### <a name="details"></a>Szczegóły

Począwszy od .NET Framework 4,5, <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)> traktuje względne identyfikatory URI z `:` w pierwszym segmencie jako niewłaściwie sformułowane. Jest to zmiana z <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=fullName> zachowania w .NET Framework 4,0, która była zgodna z RFC3986.

#### <a name="suggestion"></a>Sugestia

Ta zmiana (taka jak wiele innych zmian identyfikatorów URI) będzie mieć wpływ tylko na aplikacje ukierunkowane na .NET Framework 4,5 (lub nowsze). Aby nadal korzystać z starego zachowania, wybierz aplikację jako docelową do .NET Framework 4,0. Alternatywnie możesz skanować identyfikator URI przed wywołaniem <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=fullName> wyszukiwania `:` znaków, które można usunąć w celu weryfikacji, jeśli jest to wymagane.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Mały       |
| Wersja | 4.5         |
| Typ    | Przekierowanie |

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=nameWithType>
