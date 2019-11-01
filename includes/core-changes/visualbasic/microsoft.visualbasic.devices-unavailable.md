---
ms.openlocfilehash: 4c47b95e98aca727d9f0eda54a167a71fd53afb9
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198517"
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

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.Devices`

-- >

