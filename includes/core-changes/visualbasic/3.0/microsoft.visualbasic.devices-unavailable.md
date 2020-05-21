---
ms.openlocfilehash: a35de09b9a7bb9686433205359c3cc55954c29c3
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721318"
---
### <a name="types-in-microsoftvisualbasicdevices-namespace-not-available"></a>Typy w przestrzeni nazw Microsoft. VisualBasic. Devices są niedostępne

Typy w <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> przestrzeni nazw są niedostępne.

#### <a name="version-introduced"></a>Wprowadzona wersja

.NET Core 3,0 (wersja zapoznawcza 8)

#### <a name="change-description"></a>Zmień opis

Typy w <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> przestrzeni nazw były dostępne w niektórych wersjach programu .NET Core 3,0 w wersji zapoznawczej. Nie są już dostępne począwszy od programu .NET Core 3,0 w wersji zapoznawczej 9.

Typy zostały usunięte, aby uniknąć niepotrzebnych zależności zestawów lub istotne zmiany w kolejnych wersjach.

#### <a name="recommended-action"></a>Zalecana akcja

Jeśli kod zależy od użycia <xref:Microsoft.VisualBasic.Devices> typów i ich członków, może być możliwe użycie odpowiedniego typu lub elementu członkowskiego w bibliotece klas .NET. Na przykład równoważne funkcje <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> klasy są dostarczane przez <xref:System.DateTime?displayProperty=nameWithType> typy i i <xref:System.Environment?displayProperty=nameWithType> równoważne funkcje <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> klasy są udostępniane przez typy w <xref:System.IO.Ports?displayProperty=nameWithType> przestrzeni nazw.

#### <a name="category"></a>Kategoria

Visual Basic

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName>

<!--

#### Affected APIs

- `N:Microsoft.VisualBasic.Devices`

-->
