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
ms.openlocfilehash: 1016a0c63a85919764271e01771ff8192341725c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33398238"
---
# <a name="specifying-a-character-set"></a>Określanie zestawu znaków
<xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> Pola określa ciąg organizowanie i określa, jak wywołanie nazwy funkcji znalezione w bibliotece DLL platformy. W tym temacie opisano zarówno zachowania.  
  
 Niektóre funkcje interfejsu API wyeksportować dwie wersje funkcji, które przyjmują argumenty typu string: wąskie (ANSI) i sieci (Unicode). Interfejs API Win32, na przykład obejmuje następujące nazwy punktu wejścia dla **MessageBox** funkcji:  
  
-   **MessageBoxA**  
  
     Udostępnia 1-bajtowych wartości znakowych formatowania ANSI, rozróżnianych na podstawie "A" dodanym na końcu nazwy punktu wejścia. Wywołuje się **MessageBoxA** zawsze sformatować kierowanie ciągów ANSI, jak często na platformach Windows 95 i Windows 98.  
  
-   **MessageBoxW**  
  
     Udostępnia 2-bajtowych wartości znakowych Unicode formatowania, rozróżnianych na podstawie "W" dodanym na końcu nazwy punktu wejścia. Wywołuje się **MessageBoxW** zawsze kierować ciągi w formacie Unicode, jak często na platformach Windows NT, Windows 2000 i Windows XP.  
  
## <a name="string-marshaling-and-name-matching"></a>Organizowanie ciągów i dopasowywanie nazw  
 **CharSet** pole przyjmuje następujące wartości:  
  
 **CharSet.Ansi** (wartość domyślna)  
  
-   Ciąg organizowanie  
  
     Wywołanie platformy ciągów marshals z ich format zarządzanych (Unicode) do formatu ANSI.  
  
-   Dopasowywanie nazw  
  
     Gdy <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> pole jest **true**, ponieważ jest domyślnie w [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], wyszukuje tylko nazwa nadana wywołanie platformy. Na przykład jeśli określisz **MessageBox**, wywołanie platformy wyszukuje **MessageBox** i kończy się niepowodzeniem, gdy nie można odnaleźć dokładnej pisowni.  
  
     Gdy **opcję ExactSpelling** pole jest **false**, ponieważ jest domyślnie w C++ i C#, wywołanie platformy wyszukuje unmangled alias najpierw (**MessageBox**), następnie (nazwa zniekształcona **MessageBoxA**) Jeśli nie zostanie znaleziony unmangled alias. Zwróć uwagę, że zachowanie Dopasowywanie nazw ANSI różni się od zachowania Dopasowywanie nazw Unicode.  
  
 **Wartość CharSet.Unicode**  
  
-   Ciąg organizowanie  
  
     Wywołanie platformy ciągów kopie z ich format zarządzanych (Unicode) na Unicode format.  
  
-   Dopasowywanie nazw  
  
     Gdy **opcję ExactSpelling** pole jest **true**, ponieważ jest domyślnie w [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], wyszukuje tylko nazwa nadana wywołanie platformy. Na przykład jeśli określisz **MessageBox**, wywołanie platformy wyszukuje **MessageBox** i kończy się niepowodzeniem, jeśli nie można zlokalizować dokładnej pisowni.  
  
     Gdy **opcję ExactSpelling** pole jest **false**, ponieważ jest domyślnie w C++ i C#, wywołanie platformy wyszukuje nazwa zniekształcona najpierw (**MessageBoxW**), następnie unmangled aliasu (**MessageBox**) Jeśli nie zostanie znaleziona taka nazwa zniekształcona. Zwróć uwagę, że zachowanie Dopasowywanie nazw Unicode różni się od zachowania Dopasowywanie nazw ANSI.  
  
 **CharSet.Auto**  
  
-   Wywołanie platformy wybierze między ANSI i Unicode formaty w czasie wykonywania, oparte na platformie docelowej.  
  
## <a name="specifying-a-character-set-in-visual-basic"></a>Określanie zestawu znaków w języku Visual Basic  
 Poniższy przykład deklaruje **MessageBox** funkcja trzy razy, zawsze z inaczej zestawu znaków. Można określić zachowanie zestawu znaków w języku Visual Basic, dodając **Ansi**, **Unicode**, lub **automatycznie** — słowo kluczowe do instrukcji deklaracji.  
  
 W przypadku pominięcia kluczowego zestawu znaków, co jest wykonywane w pierwszej instrukcji deklaracji <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> pola wartość domyślna to zestaw znaków ANSI. Drugi i trzeci instrukcje w tym przykładzie jawnie określić zestaw ze słowem kluczowym znaków.  
  
```vb  
Imports System.Runtime.InteropServices  
  
Public Class Win32  
   Declare Function MessageBoxA Lib "user32.dll"(ByVal hWnd As Integer, _  
       ByVal txt As String, ByVal caption As String, _  
       ByVal Typ As Integer) As Integer  
  
   Declare Unicode Function MessageBoxW Lib "user32.dll" _  
       (ByVal hWnd As Integer, ByVal txt As String, _  
        ByVal caption As String, ByVal Typ As Integer) As Integer  
  
   Declare Auto Function MessageBox Lib "user32.dll" _  
       (ByVal hWnd As Integer, ByVal txt As String, _  
        ByVal caption As String, ByVal Typ As Integer) As Integer  
End Class  
```  
  
## <a name="specifying-a-character-set-in-c-and-c"></a>Określanie zestawu znaków w języku C# i C++  
 <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> Pole określa podstawowy zestaw znaków jako ANSI lub Unicode. Formanty, jak można zorganizować argumenty typu string do metody zestawu znaków. Do wskazania zestawu znaków, należy użyć jednej z następujących formatów:  
  
```csharp  
[DllImport("dllname", CharSet=CharSet.Ansi)]  
[DllImport("dllname", CharSet=CharSet.Unicode)]  
[DllImport("dllname", CharSet=CharSet.Auto)]  
```  
  
```cpp  
[DllImport("dllname", CharSet=CharSet::Ansi)]  
[DllImport("dllname", CharSet=CharSet::Unicode)]  
[DllImport("dllname", CharSet=CharSet::Auto)]  
```  
  
 W poniższym przykładzie przedstawiono trzy zarządzanych definicje **MessageBox** funkcji przypisanych do określenia zestawu znaków. W pierwszym definicji, przez jej pominięcia **CharSet** pola wartość domyślna to zestaw znaków ANSI.  
  
```csharp  
[DllImport("user32.dll")]  
    public static extern int MessageBoxA(int hWnd, String text,   
        String caption, uint type);  
[DllImport("user32.dll", CharSet=CharSet.Unicode)]  
    public static extern int MessageBoxW(int hWnd, String text,   
        String caption, uint type);  
[DllImport("user32.dll", CharSet=CharSet.Auto)]  
    public static extern int MessageBox(int hWnd, String text,   
        String caption, uint type);  
```  
  
```cpp  
typedef void* HWND;  
  
//Can use MessageBox or MessageBoxA.  
[DllImport("user32")]  
extern "C" int MessageBox(HWND hWnd,  
                          String* pText,  
                          String* pCaption,  
                          unsigned int uType);  
  
//Can use MessageBox or MessageBoxW.  
[DllImport("user32", CharSet=CharSet::Unicode)]  
extern "C" int MessageBoxW(HWND hWnd,  
                          String* pText,  
                          String* pCaption,  
                          unsigned int uType);  
  
//Must use MessageBox.  
[DllImport("user32", CharSet=CharSet::Auto)]  
extern "C" int MessageBox(HWND hWnd,  
                          String* pText,  
                          String* pCaption,  
                          unsigned int uType);  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.InteropServices.DllImportAttribute>  
 [Tworzenie prototypów w kodzie zarządzanym](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)  
 [Przykłady wywołań platformy](../../../docs/framework/interop/platform-invoke-examples.md)  
 [Marshaling danych w wywołaniu platformy](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)
