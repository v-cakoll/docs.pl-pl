---
ms.openlocfilehash: 4c47b95e98aca727d9f0eda54a167a71fd53afb9
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567456"
---
### <a name="types-in-microsoftvisualbasicdevices-namespace-not-available"></a>Typy w przestrzeni nazw Microsoft. VisualBasic. Devices są niedostępne

Typy w przestrzeni nazw <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> są niedostępne.

#### <a name="version-introduced"></a>Wprowadzona wersja

.NET Core 3,0 (wersja zapoznawcza 8)

#### <a name="change-description"></a>Zmień opis

Typy w przestrzeni nazw <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> były dostępne w niektórych wersjach programu .NET Core 3,0 w wersji zapoznawczej. Nie są już dostępne począwszy od programu .NET Core 3,0 w wersji zapoznawczej 9.

Typy zostały usunięte, aby uniknąć niepotrzebnych zależności zestawów lub istotne zmiany w kolejnych wersjach.

#### <a name="recommended-action"></a>Zalecane działanie

Jeśli kod zależy od użycia typów <xref:Microsoft.VisualBasic.Devices> i ich członków, można użyć odpowiedniego typu lub składowej w bibliotece klas .NET. Na przykład równoważne funkcje klasy <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> są dostarczane przez typy <xref:System.DateTime?displayProperty=nameWithType> i <xref:System.Environment?displayProperty=nameWithType> i równoważne funkcje klasy <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> są udostępniane przez typy w przestrzeni nazw <xref:System.IO.Ports?displayProperty=nameWithType>.

#### <a name="category"></a>Kategoria

Język Visual Basic

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.Devices`

-- >

