---
ms.openlocfilehash: d8cc506d60f3c24087ebde8ead345656fea0f484
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116346"
---
### <a name="types-in-microsoftvisualbasicapplicationservices-namespace-not-available"></a>Typy w przestrzeni nazw Microsoft. VisualBasic. ApplicationServices są niedostępne

Typy w przestrzeni nazw <xref:Microsoft.VisualBasic.ApplicationServices?displayProperty=fullName> są niedostępne.

#### <a name="version-introduced"></a>Wprowadzona wersja

.NET Core 3,0 (wersja zapoznawcza 8)

#### <a name="change-description"></a>Opis zmiany

Typy w przestrzeni nazw <xref:Microsoft.VisualBasic.ApplicationServices?displayProperty=fullName> były dostępne w niektórych wersjach programu .NET Core 3,0 Preview. Nie są już dostępne począwszy od programu .NET Core 3,0 w wersji zapoznawczej 9.

Typy zostały usunięte, aby uniknąć niepotrzebnych zależności zestawów lub istotne zmiany w kolejnych wersjach.

#### <a name="recommended-action"></a>Zalecane działanie

Jeśli kod zależy od użycia typów <xref:Microsoft.VisualBasic.ApplicationServices> i ich członków, można użyć odpowiedniego typu lub składowej w bibliotece klas .NET. Na przykład niektóre <xref:System.Environment?displayProperty=nameWithType> i <xref:System.Security.Principal.WindowsIdentity?displayProperty=nameWithType> Członkowie zapewniają równoważną funkcjonalność właściwości klasy <xref:Microsoft.VisualBasic.ApplicationServices.User?displayProperty=nameWithType>.

#### <a name="category"></a>Kategoria

Język Visual Basic

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:Microsoft.VisualBasic.ApplicationServices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.ApplicationServices`

-->
