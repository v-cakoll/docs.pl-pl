---
ms.openlocfilehash: 58e65bae1593f23945a971b896a1db4a929b4587
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198519"
---
### <a name="types-in-microsoftvisualbasicmyservices-namespace-not-available"></a>Typy w przestrzeni nazw Microsoft. VisualBasic. WebServices są niedostępne

Typy w przestrzeni nazw <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> są niedostępne.

#### <a name="version-introduced"></a>Wprowadzona wersja

.NET Core 3,0 (wersja zapoznawcza 8)

#### <a name="change-description"></a>Zmień opis

Typy w przestrzeni nazw <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> były dostępne w niektórych wersjach programu .NET Core 3,0 Preview. Nie są już dostępne począwszy od programu .NET Core 3,0 w wersji zapoznawczej 9.

Typy zostały usunięte, aby uniknąć niepotrzebnych zależności zestawów lub istotne zmiany w kolejnych wersjach.

#### <a name="recommended-action"></a>Zalecana akcja

Jeśli kod zależy od użycia typów **Microsoft. VisualBasic. WebServices** i ich członków, istnieją odpowiednie typy i elementy członkowskie w bibliotece klas .NET. Poniżej znajduje się mapowanie typów **Microsoft. VisualBasic. WebServices** na ich równoważne typy biblioteki klas .NET:

|Typ Microsoft. VisualBasic. WebServices|Typ biblioteki klas .NET|
|--|--|
|<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>|<xref:System.Windows.Clipboard?displayProperty=nameWithType> dla aplikacji WPF <xref:System.Windows.Forms.Clipboard?displayProperty=nameWithType> dla aplikacji Windows Forms|
|<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy>|Typy w przestrzeni nazw <xref:System.IO>|
|<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>|Typy związane z rejestrem w przestrzeni nazw <xref:Microsoft.Win32>|
|<xref:Microsoft.VisualBasic.MyServices.SpecialDirectoriesProxy>|<xref:System.Environment.GetFolderPath%2A?displayProperty=nameWithType>|

#### <a name="category"></a>Kategoria

Visual Basic

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.MyServices`

-- >

