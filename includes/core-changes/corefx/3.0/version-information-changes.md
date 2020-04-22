---
ms.openlocfilehash: 1580c8c8b7bdad91656f494537230293dbaaf93b
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021574"
---
### <a name="apis-that-report-version-now-report-product-and-not-file-version"></a>Interfejsy API, które zgłaszają wersję raportu, teraz zgłaszają produkt, a nie wersję pliku

Wiele interfejsów API, które zwracają wersje w .NET Core teraz zwraca wersję produktu, a nie wersji pliku.

#### <a name="change-description"></a>Zmień opis

W .NET Core 2.2 i poprzednich <xref:System.Environment.Version?displayProperty=nameWithType> <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>wersjach metody takie jak , i okno dialogowe właściwości pliku dla zestawów .NET Core odzwierciedlają wersję pliku. Począwszy od .NET Core 3.0, odzwierciedlają one wersję produktu.

Na poniższym rysunku przedstawiono różnicę w informacjach o wersji dla zestawu *System.Runtime.dll* dla .NET Core 2.2 (po lewej) i .NET Core 3.0 (po prawej) wyświetlanych w oknie dialogowym Właściwości pliku **Eksploratora Windows.**

![Różnica w informacjach o wersji produktu](~/docs/images/core-changes/corefx/version-information-changes/file-details.png)

#### <a name="version-introduced"></a>Wprowadzono wersję

3.0

#### <a name="recommended-action"></a>Zalecana akcja

Brak. Ta zmiana powinna sprawić, że wykrywanie wersji będzie intuicyjne, a nie rozwarte.

#### <a name="category"></a>Kategoria

Podstawowe biblioteki .NET

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Environment.Version?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>

<!--

### Affected APIs

- `P:System.Environment.Version`
- `P:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription`

-->
