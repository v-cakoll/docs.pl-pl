---
ms.openlocfilehash: ba543414d4f84362c9b9b876395815e837efbd3f
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181851"
---
### <a name="types-in-microsoftvisualbasicmyservices-namespace-not-available"></a>Typy w przestrzeni nazw Microsoft. VisualBasic. WebServices są niedostępne

Typy w <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> przestrzeni nazw są niedostępne.

#### <a name="version-introduced"></a>Wprowadzona wersja

.NET Core 3,0 (wersja zapoznawcza 8)

#### <a name="details"></a>Szczegóły

Typy w <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> przestrzeni nazw były dostępne w niektórych wersjach programu .NET Core 3,0 w wersji zapoznawczej. Nie są już dostępne począwszy od programu .NET Core 3,0 w wersji zapoznawczej 9.

Typy zostały usunięte, aby uniknąć niepotrzebnych zależności zestawów lub istotne zmiany w kolejnych wersjach.
 
#### <a name="recommended-action"></a>Zalecana akcja

Jeśli kod zależy od użycia typów **Microsoft. VisualBasic. WebServices** i ich członków, istnieją odpowiednie typy i elementy członkowskie w bibliotece klas .NET. Poniżej znajduje się mapowanie typów **Microsoft. VisualBasic. WebServices** na ich równoważne typy biblioteki klas .NET:

|Typ Microsoft. VisualBasic. WebServices|Typ biblioteki klas .NET|
|--|--|
|<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>|<xref:System.Windows.Clipboard?displayProperty=nameWithType>dla aplikacji <xref:System.Windows.Forms.Clipboard?displayProperty=nameWithType> WPF dla aplikacji Windows Forms| 
|<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy>|Typy w <xref:System.IO> przestrzeni nazw|
|<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>|Typy związane z rejestrem w <xref:Microsoft.Win32> przestrzeni nazw|
|<xref:Microsoft.VisualBasic.MyServices.SpecialDirectoriesProxy>|<xref:System.Environment.GetFolderPath%2A?displayProperty=nameWithType>|

#### <a name="category"></a>Kategoria

Visual Basic

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.MyServices`

-- >

