---
ms.openlocfilehash: 7f528510e4158dad71280a7b1f269a231b8c60f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76116343"
---
### <a name="types-in-microsoftvisualbasicdevices-namespace-not-available"></a>Typy w obszarze nazw Microsoft.VisualBasic.Devices niedostępne

Typy w <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> obszarze nazw nie są dostępne.

#### <a name="version-introduced"></a>Wprowadzona wersja

Podgląd .NET Core 3.0 8

#### <a name="change-description"></a>Zmień opis

Typy w <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> obszarze nazw były dostępne w niektórych wersjach podglądu programu .NET Core 3.0. Nie są już dostępne od wersji .NET Core 3.0 Preview 9.

Typy zostały usunięte, aby uniknąć niepotrzebnych zależności zestawu lub zerwania zmian w kolejnych wersjach.

#### <a name="recommended-action"></a>Zalecana akcja

Jeśli kod zależy od <xref:Microsoft.VisualBasic.Devices> użycia typów i ich elementów członkowskich, można użyć odpowiedniego typu lub elementu członkowskiego w bibliotece klas .NET. Na przykład równoważne funkcje <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> do klasy <xref:System.DateTime?displayProperty=nameWithType> jest <xref:System.Environment?displayProperty=nameWithType> dostarczany przez i typów <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> i równoważne funkcje <xref:System.IO.Ports?displayProperty=nameWithType> do klasy jest dostarczany przez typy w przestrzeni nazw.

#### <a name="category"></a>Kategoria

Visual Basic

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.Devices`

-->
