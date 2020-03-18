---
ms.openlocfilehash: 5612ebce67946e22aaeeba861115ce4f8967e1f5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75344456"
---
### <a name="apis-that-report-version-now-report-product-and-not-file-version"></a>Interfejsy API, które zgłaszają wersję raportu teraz zgłosić produkt, a nie wersji pliku

Wiele interfejsów API, które zwracają wersje w .NET Core teraz zwrócić wersję produktu, a nie wersji pliku.

#### <a name="change-description"></a>Zmień opis

W .NET Core 2.2 i poprzednich <xref:System.Environment.Version?displayProperty=nameWithType> <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>wersjach metody, takie jak , , i okno dialogowe właściwości pliku dla zestawów .NET Core odzwierciedlają wersję pliku. Począwszy od .NET Core 3.0, odzwierciedlają one wersję produktu.

Na poniższej ilustracji przedstawiono różnicę w informacjach o wersji dla zestawu *System.Runtime.dll* dla .NET Core 2.2 (po lewej) i .NET Core 3.0 (po prawej) wyświetlanych w oknie dialogowym właściwości pliku **Eksploratora Windows.**

![Różnica w informacjach o wersji produktu](~/docs/images/core-changes/corefx/version-information-changes/file-details.png)

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="recommended-action"></a>Zalecana akcja

Brak. Ta zmiana powinna sprawić, że wykrywanie wersji będzie intuicyjne, a nie rozwrzęce.

#### <a name="category"></a>Kategoria

CoreFx

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Environment.Version?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>

<!--

### Affected APIs

- `P:System.Environment.Version`
- `P:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription`

-->
