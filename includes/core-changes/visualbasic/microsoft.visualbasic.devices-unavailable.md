---
ms.openlocfilehash: dae4afa92b8833f326b4eacd00b36bb3e1199cc1
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237425"
---
### <a name="types-in-microsoftvisualbasicdevices-namespace-not-available"></a>Typy w przestrzeni nazw Microsoft. VisualBasic. Devices są niedostępne

Typy w przestrzeni nazw <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> są niedostępne.

#### <a name="version-introduced"></a>Wprowadzona wersja

.NET Core 3,0 (wersja zapoznawcza 8)

#### <a name="change-description"></a>Zmień opis

Typy w przestrzeni nazw <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> były dostępne w niektórych wersjach programu .NET Core 3,0 w wersji zapoznawczej. Nie są już dostępne począwszy od programu .NET Core 3,0 w wersji zapoznawczej 9.

Typy zostały usunięte, aby uniknąć niepotrzebnych zależności zestawów lub istotne zmiany w kolejnych wersjach.
 
#### <a name="recommended-action"></a>Zalecana akcja

Jeśli kod zależy od użycia typów <xref:Microsoft.VisualBasic.Devices> i ich elementów członkowskich, można użyć odpowiedniego typu lub elementu członkowskiego w bibliotece klas .NET. Na przykład równoważne funkcje klasy <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> są dostarczane przez typy <xref:System.DateTime?displayProperty=nameWithType> i <xref:System.Environment?displayProperty=nameWithType>, a równoważne funkcje klasy <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> są udostępniane przez typy w przestrzeni nazw <xref:System.IO.Ports?displayProperty=nameWithType>.

#### <a name="category"></a>Kategoria

Visual Basic

#### <a name="affected-apis"></a>Narażone interfejsy API

- <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.Devices`

-- >

