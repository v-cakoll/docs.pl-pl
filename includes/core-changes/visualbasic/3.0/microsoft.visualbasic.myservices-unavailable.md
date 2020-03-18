---
ms.openlocfilehash: d207a937917da78f6b902ad8ca4f02fa9a46c2e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76116371"
---
### <a name="types-in-microsoftvisualbasicmyservices-namespace-not-available"></a>Typy w obszarze nazw Microsoft.VisualBasic.MyServices niedostępne

Typy w <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> obszarze nazw nie są dostępne.

#### <a name="version-introduced"></a>Wprowadzona wersja

Podgląd .NET Core 3.0 8

#### <a name="change-description"></a>Zmień opis

Typy w <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> obszarze nazw były dostępne w niektórych wersjach podglądu programu .NET Core 3.0. Nie są już dostępne od wersji .NET Core 3.0 Preview 9.

Typy zostały usunięte, aby uniknąć niepotrzebnych zależności zestawu lub zerwania zmian w kolejnych wersjach.

#### <a name="recommended-action"></a>Zalecana akcja

Jeśli kod zależy od użycia **typów Microsoft.VisualBasic.MyServices** i ich członków, istnieją odpowiednie typy i elementy członkowskie w bibliotece klas .NET. Poniżej przedstawiono mapowanie typów **microsoft.VisualBasic.MyServices** na ich równoważne typy bibliotek klas .NET:

|Typ microsoft.VisualBasic.MyServices|Typ biblioteki klas .NET|
|--|--|
|<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>|<xref:System.Windows.Clipboard?displayProperty=nameWithType>dla aplikacji WPF, <xref:System.Windows.Forms.Clipboard?displayProperty=nameWithType> dla aplikacji Windows Forms|
|<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy>|Typy w <xref:System.IO> obszarze nazw|
|<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>|Typy związane z <xref:Microsoft.Win32> rejestrem w obszarze nazw|
|<xref:Microsoft.VisualBasic.MyServices.SpecialDirectoriesProxy>|<xref:System.Environment.GetFolderPath%2A?displayProperty=nameWithType>|

#### <a name="category"></a>Kategoria

Visual Basic

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.MyServices`

-->
