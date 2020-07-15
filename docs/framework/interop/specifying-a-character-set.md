---
title: Określanie zestawu znaków
description: Dowiedz się, jak określić zestaw znaków, który używa kodowania z wąskim (ANSI) lub szerokim (Unicode). Możesz również określić wybór automatyczny środowiska uruchomieniowego.
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
ms.openlocfilehash: 789753742d8714e481f038e323407cbab0499f6c
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309797"
---
# <a name="specify-a-character-set"></a>Określanie zestawu znaków

<xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType>Pole steruje kierowaniem ciągów i określa, w jaki sposób metoda Invoke odnajduje nazwy funkcji w bibliotece DLL. W tym temacie opisano oba zachowania.  
  
 Niektóre interfejsy API eksportują dwie wersje funkcji przyjmujących argumenty ciągów: wąski (ANSI) i szeroki (Unicode). Interfejs API systemu Windows, na przykład, zawiera następujące nazwy punktów wejścia dla funkcji **MessageBox** :  
  
- **MessageBoxA**  
  
     Zawiera 1-bajtowe znaki formatowania ANSI, rozróżniane przez "A" do nazwy punktu wejścia. Wywołania klasy **MessageBox** są zawsze organizowane w formacie ANSI.  
  
- **MessageBoxW**  
  
     Zawiera 2-bajtowe znaki formatowania Unicode, rozróżniane "W" dołączone do nazwy punktu wejścia. Wywołania **MessageBoxW** zawsze marshalą ciągi w formacie Unicode.  
  
## <a name="string-marshaling-and-name-matching"></a>Kierowanie ciągów i dopasowywanie nazw  
 `CharSet`Pole akceptuje następujące wartości:  
  
 <xref:System.Runtime.InteropServices.CharSet.Ansi>(wartość domyślna)  
  
- Kierowanie ciągów  
  
     Wywołanie platformy umożliwia kierowanie ciągów z formatu zarządzanego (Unicode) do formatu ANSI.  
  
- Dopasowanie nazw  
  
     Gdy <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> pole ma `true` wartość domyślną w Visual Basic, platforma wywoła wyszukiwanie tylko dla określonej nazwy. Na przykład jeśli określisz element **MessageBox**, funkcja Invoke wywoła wyszukiwanie dla **MessageBox** i zakończy się niepowodzeniem, gdy nie będzie można zlokalizować dokładnej pisowni.  
  
     Gdy `ExactSpelling` pole jest `false` , ponieważ jest domyślnie w języku C++ i C#, wywołanie platformy wyszuka alias niezniekształconej najpierw (**MessageBox**), a następnie nazwę zniekształcona (**MessageBox**), jeśli alias niezniekształconej nie zostanie znaleziony. Należy zauważyć, że zachowanie dopasowania nazw ANSI różni się od zachowania dopasowywania nazw Unicode.  
  
 <xref:System.Runtime.InteropServices.CharSet.Unicode>  
  
- Kierowanie ciągów  
  
     Wywołanie platformy kopiuje ciągi z formatu zarządzanego (Unicode) do formatu Unicode.  
  
- Dopasowanie nazw  
  
     Gdy `ExactSpelling` pole ma `true` wartość domyślną w Visual Basic, platforma wywoła wyszukiwanie tylko dla określonej nazwy. Na przykład jeśli określisz element **MessageBox**, funkcja Invoke wywoła wyszukiwanie dla **MessageBox** i zakończy się niepowodzeniem, jeśli nie można zlokalizować dokładnej pisowni.  
  
     Gdy `ExactSpelling` pole jest `false` Domyślnie w języku C++ i C#, wywołanie platformy wyszukuje najpierw nazwę zniekształcona (**MessageBoxW**), a następnie alias niezniekształconej (**MessageBox**), jeśli nie odnaleziono nazwy zniekształcona. Zauważ, że zachowanie dopasowywania nazw Unicode różni się od zachowania dopasowania nazw ANSI.  
  
 <xref:System.Runtime.InteropServices.CharSet.Auto>  
  
- Wywołanie platformy wybiera między formatami ANSI i Unicode w czasie wykonywania, na podstawie platformy docelowej.  
  
## <a name="specify-a-character-set-in-visual-basic"></a>Określ zestaw znaków w Visual Basic

Możesz określić zachowanie zestawu znaków w Visual Basic, dodając `Ansi` `Unicode` słowo kluczowe,, lub `Auto` do instrukcji deklaracji. W przypadku pominięcia słowa kluczowego zestawu znaków <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> wartością domyślną pola jest zestaw znaków ANSI.

Poniższy przykład deklaruje funkcję **MessageBox** trzykrotnie, za każdym razem z innym zachowaniem zestawu znaków. Pierwsza instrukcja pomija słowo kluczowe zestawu znaków, dlatego zestaw znaków jest domyślnie ANSI. Drugie i trzecie instrukcje jawnie określają zestaw znaków za pomocą słowa kluczowego.

```vb
Friend Class NativeMethods
    Friend Declare Function MessageBoxA Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer

    Friend Declare Unicode Function MessageBoxW Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer

    Friend Declare Auto Function MessageBox Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
## <a name="specify-a-character-set-in-c-and-c"></a>Określanie zestawu znaków w językach C# i C++

<xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType>Pole Identyfikuje podstawowy zestaw znaków jako ANSI lub Unicode. Zestaw znaków kontroluje sposób organizowania argumentów ciągów dla metody. Aby wskazać zestaw znaków, użyj jednej z następujących form:  
  
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
  
 W poniższym przykładzie przedstawiono trzy zarządzane definicje funkcji **MessageBox** przypisanej do określenia zestawu znaków. W pierwszej definicji, z pominięciem, `CharSet` pole domyślnie jest zestaw znaków ANSI.  
  
```csharp  
using System;
using System.Runtime.InteropServices;

internal static class NativeMethods
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
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [Tworzenie prototypów w kodzie zarządzanym](creating-prototypes-in-managed-code.md)
- [Przykłady wywołań platformy](platform-invoke-examples.md)
- [Organizowanie danych w wywołaniu platformy](marshaling-data-with-platform-invoke.md)
