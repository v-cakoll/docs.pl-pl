---
ms.openlocfilehash: efa0efaf40e2e432d477f1659d7bde3abc98241d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67857527"
---
### <a name="unicode-standard-version-80-categories-now-supported"></a>Obsługiwane są teraz standardowe kategorie Unicode w wersji 8.0

|   |   |
|---|---|
|Szczegóły|W .NET Framework 4.6.2 dane Unicode zostały uaktualnione z standardu Unicode w wersji 6.3 do wersji 8.0.  Żądając kategorii znaków Unicode w .NET Framework 4.6.2, niektóre wyniki mogą nie odpowiadać wynikom w poprzednich wersjach programu .NET Framework.  Ta zmiana dotyczy głównie sylaby Cherokee i nowych samogłosek Tai Lue znaków i znaków tonu.|
|Sugestia|Przejrzyj kod i usuń/zmień logikę, która zależy od zakodowanych na stałe kategorii znaków Unicode.|
|Zakres|Mały|
|Wersja|4.6.2|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Char.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.String,System.Int32)?displayProperty=nameWithType></li></ul>|
