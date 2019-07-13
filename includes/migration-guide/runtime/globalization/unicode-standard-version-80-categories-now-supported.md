---
ms.openlocfilehash: 480cbdecd681408a7e1d6fa366e3f1a4b131ab42
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67857527"
---
### <a name="unicode-standard-version-80-categories-now-supported"></a>Teraz obsługiwane kategorie standardowej wersji 8.0 Unicode

|   |   |
|---|---|
|Szczegóły|W programie .NET Framework 4.6.2 danych Unicode został uaktualniony ze standardu Unicode wersji 6.3 do wersji 8.0.  Podczas żądania kategorii znaków Unicode w programie .NET Framework 4.6.2, niektóre wyniki mogą być niezgodne wyniki w poprzednich wersjach systemu .NET Framework.  Ta zmiana przede wszystkim ma wpływ sylab Czirokeski i nowe Tai artość samogłosek znaki i znaki tonowe.|
|Sugestia|Przegląd kodu i Usuń/Zmień logikę, która jest zależna od ustalonych kategorii znaków Unicode.|
|Scope|Mały|
|Wersja|4.6.2|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Char.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.String,System.Int32)?displayProperty=nameWithType></li></ul>|

