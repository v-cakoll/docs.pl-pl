---
ms.openlocfilehash: d8cc506d60f3c24087ebde8ead345656fea0f484
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76116346"
---
### <a name="types-in-microsoftvisualbasicapplicationservices-namespace-not-available"></a>Typy w przestrzeni nazw Microsoft. VisualBasic. ApplicationServices są niedostępne

Typy w <xref:Microsoft.VisualBasic.ApplicationServices?displayProperty=fullName> przestrzeni nazw są niedostępne.

#### <a name="version-introduced"></a>Wprowadzona wersja

.NET Core 3,0 (wersja zapoznawcza 8)

#### <a name="change-description"></a>Zmień opis

Typy w <xref:Microsoft.VisualBasic.ApplicationServices?displayProperty=fullName> przestrzeni nazw były dostępne w niektórych wersjach programu .net Core 3,0 Preview. Nie są już dostępne począwszy od programu .NET Core 3,0 w wersji zapoznawczej 9.

Typy zostały usunięte, aby uniknąć niepotrzebnych zależności zestawów lub istotne zmiany w kolejnych wersjach.

#### <a name="recommended-action"></a>Zalecana akcja

Jeśli kod zależy od użycia <xref:Microsoft.VisualBasic.ApplicationServices> typów i ich członków, może być możliwe użycie odpowiedniego typu lub elementu członkowskiego w bibliotece klas .NET. Na przykład niektórzy <xref:System.Environment?displayProperty=nameWithType> i <xref:System.Security.Principal.WindowsIdentity?displayProperty=nameWithType> Członkowie zapewniają równoważną funkcjonalność właściwości <xref:Microsoft.VisualBasic.ApplicationServices.User?displayProperty=nameWithType> klasy.

#### <a name="category"></a>Kategoria

Visual Basic

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:Microsoft.VisualBasic.ApplicationServices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.ApplicationServices`

-->
