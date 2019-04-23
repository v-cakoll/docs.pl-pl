---
ms.openlocfilehash: 734041f5921571cd11225a359e794526cbd8d0e1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774472"
---
### <a name="systemuriiswellformeduristring-method-returns-false-for-relative-uris-with-a-colon-char-in-first-segment"></a>Metoda System.Uri.IsWellFormedUriString zwraca wartość false dla względne identyfikatory URI przy użyciu znaku dwukropek w pierwszy segment

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.5 <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)> traktują względne identyfikatory URI z <code>:</code> w ich pierwszy segment, ponieważ niepoprawnie sformułowany. To różni się od <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=name> zachowania w programie .NET Framework 4.0 do RFC3986 została wprowadzona w celu.|
|Sugestia|Ta zmiana (na przykład wiele innych zmian URI) mają wpływ tylko na aplikacje zgodne z .NET Framework 4.5 (lub nowszy). Aby nadal używać starego zachowania, aplikacja jest przeznaczona dla .NET Framework 4.0. Alternatywnie skanowania identyfikatory URI przed wywołaniem <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=name> szukasz <code>:</code> znaki, które warto usunąć do celów sprawdzania poprawności, jeśli pożądane jest stare zachowanie.|
|Zakres|Mały|
|Wersja|4.5|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=nameWithType></li></ul>|
