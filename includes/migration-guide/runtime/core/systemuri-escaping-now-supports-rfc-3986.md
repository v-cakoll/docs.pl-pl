---
ms.openlocfilehash: 1d7dc808d5b514acc582675d6ccdbd5778314624
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620267"
---
### <a name="systemuri-escaping-now-supports-rfc-3986"></a>Ucieczka system. URI obsługuje teraz RFC 3986

#### <a name="details"></a>Szczegóły

Ucieczka identyfikatorów URI została zmieniona w .NET Framework 4,5 w celu obsługi [specyfikacji RFC 3986](https://tools.ietf.org/html/rfc3986). Określone zmiany obejmują:<ul><li><xref:System.Uri.EscapeDataString(System.String)?displayProperty=fullName>wyprowadza znaki zastrzeżone na podstawie RFC 3986.</li><li><xref:System.Uri.EscapeUriString(System.String)?displayProperty=fullName>nie ma znaków zarezerwowanych.</li><li><xref:System.Uri.UnescapeDataString(System.String)?displayProperty=fullName>nie zgłasza wyjątku, jeśli napotka nieprawidłową sekwencję ucieczki.</li><li>Niezastrzeżone znaki ucieczki przestają być znakami ucieczki.</li></ul>

#### <a name="suggestion"></a>Sugestia

<ul><li>Zaktualizuj aplikacje, aby nie polegać na zgłaszaniu <xref:System.Uri.UnescapeDataString(System.String)?displayProperty=fullName> w przypadku nieprawidłowej sekwencji ucieczki. Takie sekwencje muszą być wykrywane bezpośrednio.</li><li>Podobnie, należy oczekiwać, że identyfikatory URI i niezmienionych ciągów i danych mogą się różnić od .NET Framework 4,0 i .NET Framework 4,5 i nie powinny być porównywane bezpośrednio między wersjami programu .NET. Zamiast tego należy je analizować i znormalizować w jednej wersji platformy .NET przed dokonaniem jakichkolwiek porównań.</li></ul>

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Mały|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe

#### <a name="affected-apis"></a>Dotyczy interfejsów API

-<xref:System.Uri.EscapeDataString(System.String)?displayProperty=nameWithType></li><li><xref:System.Uri.EscapeUriString(System.String)?displayProperty=nameWithType></li><li><xref:System.Uri.UnescapeDataString(System.String)?displayProperty=nameWithType></li></ul>|
