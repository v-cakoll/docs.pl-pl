---
title: Określanie zestawu znaków
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- platform invoke, attribute fields
- attribute fields in platform invoke, CharSet
- CharSet field
ms.assetid: a8347eb1-295f-46b9-8a78-63331f9ecc50
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0146d3617f5a4aff2a76d2b2f4777b18a0e9c2ab
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2019
ms.locfileid: "58410822"
---
# <a name="specifying-a-character-set"></a>Określanie zestawu znaków
<xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> Pole kontroluje kierowanie ciągu i określa, jak wywołanie platformy znajduje nazwy funkcji w bibliotece DLL. W tym temacie opisano obie zachowania.  
  
 Niektóre interfejsy API wyeksportować dwie wersje funkcji, które przyjmują argumenty typu string: wąskiego (ANSI) i dwubajtowych (Unicode). Interfejs API Windows, na przykład zawiera następujące nazwy punktu wejścia dla **MessageBox** funkcji:  
  
-   **MessageBoxA**  
  
     Zawiera formatowanie ANSI 1-bajtowych wartości znakowych rozróżnianych na podstawie "A", po której dołączany do wybranej nazwy punktu wejścia. Wywołania **MessageBoxA** zawsze sformatować przeprowadzanie marshalingu ciągów ANSI, co jest często spotykane na platformach Windows 95 i Windows 98.  
  
-   **MessageBoxW**  
  
     Zawiera formatowanie 2-bajtowych wartości znakowych Unicode, rozróżnianych na podstawie "W" dołączany do wybranej nazwy punktu wejścia. Wywołania **MessageBoxW** zawsze przeprowadzanie marshalingu ciągów w formacie Unicode, co jest często spotykane na platformach Windows NT, Windows 2000 i Windows XP.  
  
## <a name="string-marshaling-and-name-matching"></a>Marshaling ciągów i dopasowywanie nazw  
 `CharSet` Pole akceptuje następujące wartości:  
  
 <xref:System.Runtime.InteropServices.CharSet.Ansi> (wartość domyślna)  
  
-   Ciąg marshalingu  
  
     Wywołanie platformy marshals ciągi z ich formatu zarządzanych (Unicode) na ANSI format.  
  
-   Dopasowywanie nazw  
  
     Gdy <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> pole jest `true`, ponieważ jest on domyślnie [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], wyszukuje tylko należy określić nazwę wywołania platformy. Na przykład, jeśli określisz **MessageBox**, wyszukuje wywołania platformy **MessageBox** i kończy się niepowodzeniem, gdy nie można odnaleźć dokładnej pisowni.  
  
     Gdy `ExactSpelling` pole jest `false`, ponieważ jest ona domyślnie w języku C++ i C#, pierwsze wywołanie platformy wyszukuje unmangled aliasu (**MessageBox**), następnie zniekształcone nazwy (**MessageBoxA**) Jeśli nie zostanie znaleziony unmangled aliasu. Należy zauważyć, że zachowanie Dopasowywanie nazw ANSI różni się od zachowania Dopasowywanie nazw Unicode.  
  
 <xref:System.Runtime.InteropServices.CharSet.Unicode>  
  
-   Ciąg marshalingu  
  
     Wywołanie platformy ciągi kopie z ich formatu zarządzanych (Unicode) do formatu Unicode.  
  
-   Dopasowywanie nazw  
  
     Gdy `ExactSpelling` pole jest `true`, ponieważ jest on domyślnie [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], wyszukuje tylko należy określić nazwę wywołania platformy. Na przykład, jeśli określisz **MessageBox**, wyszukuje wywołania platformy **MessageBox** i kończy się niepowodzeniem, jeśli nie może zlokalizować dokładnej pisowni.  
  
     Gdy `ExactSpelling` pole jest `false`, ponieważ jest ona domyślnie w języku C++ i C#, pierwsze wywołanie platformy wyszukuje zniekształcone nazwy (**MessageBoxW**), następnie unmangled aliasu (**MessageBox**) Jeśli nie znaleziono zniekształcone nazwy. Należy zauważyć, że zachowanie Dopasowywanie nazw Unicode różni się od zachowania Dopasowywanie nazw ANSI.  
  
 <xref:System.Runtime.InteropServices.CharSet.Auto>  
  
-   Wywołanie platformy wybiera między ANSI i Unicode formaty w czasie wykonywania, oparte na platformie docelowej.  
  
## <a name="specifying-a-character-set-in-visual-basic"></a>Określanie zestawu znaków w języku Visual Basic  
 Poniższy przykład deklaruje **MessageBox** funkcja trzy razy, każdorazowo przy użyciu różnych zachowanie zestawu znaków. Można określić zachowanie zestawu znaków w języku Visual Basic, dodając **Ansi**, **Unicode**, lub **automatycznie** — słowo kluczowe do instrukcji deklaracji.  
  
 Jeżeli pominięto słowa kluczowego zestaw znaków, jak odbywa się w pierwszej instrukcji deklaracji <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> pola wartość domyślna to zestawu znaków ANSI. Drugi i trzeci instrukcji w przykładzie jawnie określić znak, który został ustawiony za pomocą słowa kluczowego.  
  
```vb
Imports System

Friend Class WindowsAPI
    Friend Shared Declare Function MessageBoxA Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer

    Friend Shared Declare Unicode Function MessageBoxW Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer

    Friend Shared Declare Auto Function MessageBox Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
## <a name="specifying-a-character-set-in-c-and-c"></a>Określanie zestawu znaków w C# i C++  
 <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> Pole identyfikuje podstawowy zestaw znaków jako ANSI lub Unicode. Formanty, jak powinny być wprowadzane argumenty typu string do metody zestawu znaków. Aby wskazać zestaw znaków, użyj jednej z następujących form:  
  
```csharp
[DllImport("DllName", CharSet = CharSet.Ansi)]
[DllImport("DllName", CharSet = CharSet.Unicode)]
[DllImport("DllName", CharSet = CharSet.Auto)]
```
  
```cpp
[DllImport("DllName", CharSet = CharSet::Ansi)]
[DllImport("DllName", CharSet = CharSet::Unicode)]
[DllImport("DllName", CharSet = CharSet::Auto)]
```
  
 W poniższym przykładzie przedstawiono trzy definicje zarządzanych **MessageBox** opartego na atrybutach funkcji do określenia zestawu znaków. W pierwszym definicji przez jej pominięcia `CharSet` pola wartość domyślna to zestawu znaków ANSI.  
  
```csharp  
using System;
using System.Runtime.InteropServices;

internal static class WindowsAPI
{
    [DllImport("user32.dll")]
    internal static extern int MessageBoxA(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);

    [DllImport("user32.dll", CharSet = CharSet.Unicode)]
    internal static extern int MessageBoxW(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);

    [DllImport("user32.dll", CharSet = CharSet.Auto)]
    internal static extern int MessageBox(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);
}
```  
  
```cpp
typedef void* HWND;

// Can use MessageBox or MessageBoxA.
[DllImport("user32")]
extern "C" int MessageBox(
    HWND hWnd, String* lpText, String* lpCaption, unsigned int uType);

// Can use MessageBox or MessageBoxW.
[DllImport("user32", CharSet = CharSet::Unicode)]
extern "C" int MessageBoxW(
    HWND hWnd, String* lpText, String* lpCaption, unsigned int uType);

// Must use MessageBox.
[DllImport("user32", CharSet = CharSet::Auto)]
extern "C" int MessageBox(
    HWND hWnd, String* lpText, String* lpCaption, unsigned int uType);
```
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [Tworzenie prototypów w kodzie zarządzanym](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)
- [Przykłady wywołań platformy](../../../docs/framework/interop/platform-invoke-examples.md)
- [Marshaling danych w wywołaniu platformy](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)
