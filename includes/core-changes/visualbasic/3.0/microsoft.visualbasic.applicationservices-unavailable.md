---
ms.openlocfilehash: d8cc506d60f3c24087ebde8ead345656fea0f484
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76116346"
---
### <a name="types-in-microsoftvisualbasicapplicationservices-namespace-not-available"></a>Typy w obszarze nazw Microsoft.VisualBasic.ApplicationServices niedostępne

Typy w <xref:Microsoft.VisualBasic.ApplicationServices?displayProperty=fullName> obszarze nazw nie są dostępne.

#### <a name="version-introduced"></a>Wprowadzona wersja

Podgląd .NET Core 3.0 8

#### <a name="change-description"></a>Zmień opis

Typy w <xref:Microsoft.VisualBasic.ApplicationServices?displayProperty=fullName> obszarze nazw były dostępne w niektórych wersjach podglądu programu .NET Core 3.0. Nie są już dostępne od wersji .NET Core 3.0 Preview 9.

Typy zostały usunięte, aby uniknąć niepotrzebnych zależności zestawu lub zerwania zmian w kolejnych wersjach.

#### <a name="recommended-action"></a>Zalecana akcja

Jeśli kod zależy od <xref:Microsoft.VisualBasic.ApplicationServices> użycia typów i ich elementów członkowskich, można użyć odpowiedniego typu lub elementu członkowskiego w bibliotece klas .NET. Na przykład <xref:System.Environment?displayProperty=nameWithType> niektóre <xref:System.Security.Principal.WindowsIdentity?displayProperty=nameWithType> i elementy członkowskie zapewniają równoważne <xref:Microsoft.VisualBasic.ApplicationServices.User?displayProperty=nameWithType> funkcje do właściwości klasy.

#### <a name="category"></a>Kategoria

Visual Basic

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:Microsoft.VisualBasic.ApplicationServices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.ApplicationServices`

-->
