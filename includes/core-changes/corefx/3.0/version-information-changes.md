---
ms.openlocfilehash: bb264e406c6604c3606e564d99018eda0f9e8d89
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721702"
---
### <a name="apis-that-report-version-now-report-product-and-not-file-version"></a>Interfejsy API służące do raportowania wersji teraz produktu i nie wersji

Wiele interfejsów API, które zwracają wersje w oprogramowaniu .NET Core, teraz zwracają wersję produktu, a nie wersję pliku.

#### <a name="change-description"></a>Zmień opis

W programie .NET Core 2,2 i poprzednich wersjach metody, takie jak <xref:System.Environment.Version?displayProperty=nameWithType> , <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> i okno dialogowe właściwości pliku dla zestawów .NET Core odzwierciedlają wersję pliku. Począwszy od platformy .NET Core 3,0, odzwierciedlają one wersję produktu.

Na poniższej ilustracji przedstawiono różnice w informacjach o wersji zestawu *System. Runtime. dll* dla programu .net Core 2,2 (po lewej stronie) i .net Core 3,0 (po prawej), jak pokazano w oknie dialogowym właściwości pliku **Eksploratora Windows** .

![Różnica w informacjach o wersji produktu](~/docs/images/core-changes/corefx/version-information-changes/file-details.png)

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="recommended-action"></a>Zalecana akcja

Brak. Ta zmiana powinna sprawiać, że wykrywanie wersji jest intuicyjne, a nie obtuse.

#### <a name="category"></a>Kategoria

Podstawowe biblioteki platformy .NET

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Environment.Version?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.Environment.Version`
- `P:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription`

-->
