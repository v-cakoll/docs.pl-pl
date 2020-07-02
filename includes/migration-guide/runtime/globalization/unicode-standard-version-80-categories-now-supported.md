---
ms.openlocfilehash: a20fad5f9c95e59c14ffd91f4921cf8bfab443cd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621190"
---
### <a name="unicode-standard-version-80-categories-now-supported"></a>Kategorie Unicode w wersji Standard 8,0 są teraz obsługiwane

#### <a name="details"></a>Szczegóły

W .NET Framework 4.6.2 dane Unicode zostały uaktualnione z wersji standard Unicode 6,3 do wersji 8,0.  Podczas żądania kategorii znaków Unicode w .NET Framework 4.6.2 niektóre wyniki mogą być niezgodne z wynikami w poprzednich .NET Framework wersjach.  Ta zmiana głównie ma wpływ na sylaby czirokeski i nowe znaki samogłosek artość oraz znaki tonu.

#### <a name="suggestion"></a>Sugestia

Przejrzyj kod i Usuń lub Zmień logikę, która zależy od zakodowanych kategorii znaków Unicode.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Mały|
|Wersja|4.6.2|
|Typ|Środowisko uruchomieniowe

#### <a name="affected-apis"></a>Dotyczy interfejsów API

-<xref:System.Char.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.String,System.Int32)?displayProperty=nameWithType></li></ul>|
