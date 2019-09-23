---
ms.openlocfilehash: bb163d5a6eb3d926a44a83ea79572c3a497bbe8d
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181836"
---
### <a name="types-in-microsoftvisualbasicdevices-namespace-not-available"></a>Typy w przestrzeni nazw Microsoft. VisualBasic. Devices są niedostępne

Typy w <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> przestrzeni nazw są niedostępne.

#### <a name="version-introduced"></a>Wprowadzona wersja

.NET Core 3,0 (wersja zapoznawcza 8)

#### <a name="details"></a>Szczegóły

Typy w <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> przestrzeni nazw były dostępne w niektórych wersjach programu .NET Core 3,0 w wersji zapoznawczej. Nie są już dostępne począwszy od programu .NET Core 3,0 w wersji zapoznawczej 9.

Typy zostały usunięte, aby uniknąć niepotrzebnych zależności zestawów lub istotne zmiany w kolejnych wersjach.
 
#### <a name="recommended-action"></a>Zalecana akcja

Jeśli kod zależy od użycia <xref:Microsoft.VisualBasic.Devices> typów i ich członków, może być możliwe użycie odpowiedniego typu lub elementu członkowskiego w bibliotece klas .NET. Na przykład <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> równoważne funkcje klasy są dostarczane <xref:System.DateTime?displayProperty=nameWithType> przez typy i <xref:System.Environment?displayProperty=nameWithType> i równoważne funkcje <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> klasy są udostępniane przez typy w <xref:System.IO.Ports?displayProperty=nameWithType> przestrzeni nazw.

#### <a name="category"></a>Kategoria

Visual Basic

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.Devices`

-- >

