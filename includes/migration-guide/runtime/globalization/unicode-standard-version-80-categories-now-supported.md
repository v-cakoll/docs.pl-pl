---
ms.openlocfilehash: 480cbdecd681408a7e1d6fa366e3f1a4b131ab42
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760672"
---
### <a name="unicode-standard-version-80-categories-now-supported"></a>Teraz obsługiwane kategorie standardowej wersji 8.0 Unicode

|   |   |
|---|---|
|Szczegóły|W programie .NET Framework 4.6.2 danych Unicode został uaktualniony ze standardu Unicode wersji 6.3 do wersji 8.0.  Podczas żądania kategorii znaków Unicode w programie .NET Framework 4.6.2, niektóre wyniki mogą być niezgodne wyniki w poprzednich wersjach systemu .NET Framework.  Ta zmiana przede wszystkim ma wpływ sylab Czirokeski i nowe Tai artość samogłosek znaki i znaki tonowe.|
|Sugestia|Przegląd kodu i Usuń/Zmień logikę, która jest zależna od ustalonych kategorii znaków Unicode.|
|Zakres|Mały|
|Wersja|4.6.2|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Char.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.String,System.Int32)?displayProperty=nameWithType></li></ul>|

