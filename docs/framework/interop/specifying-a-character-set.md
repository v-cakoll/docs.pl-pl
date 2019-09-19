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
ms.openlocfilehash: 9ee68d0da3b7f23d4de0192da076ef6f71d6d222
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71051633"
---
# <a name="specifying-a-character-set"></a>Określanie zestawu znaków
<xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> Pole steruje kierowaniem ciągów i określa, w jaki sposób metoda Invoke odnajduje nazwy funkcji w bibliotece DLL. W tym temacie opisano oba zachowania.  
  
 Niektóre interfejsy API eksportują dwie wersje funkcji przyjmujących argumenty ciągów: wąski (ANSI) i szeroki (Unicode). Interfejs API systemu Windows, na przykład, zawiera następujące nazwy punktów wejścia dla funkcji **MessageBox** :  
  
- **MessageBoxA**  
  
     Zawiera 1-bajtowe znaki formatowania ANSI, rozróżniane przez "A" do nazwy punktu wejścia. Wywołania klasy **MessageBox** są zawsze organizowane w formacie ANSI.  
  
- **MessageBoxW**  
  
     Zawiera 2-bajtowe znaki formatowania Unicode, rozróżniane "W" dołączone do nazwy punktu wejścia. Wywołania **MessageBoxW** zawsze marshalą ciągi w formacie Unicode.  
  
## <a name="string-marshaling-and-name-matching"></a>Kierowanie ciągów i dopasowywanie nazw  
 `CharSet` Pole akceptuje następujące wartości:  
  
 <xref:System.Runtime.InteropServices.CharSet.Ansi>(wartość domyślna)  
  
- Kierowanie ciągów  
  
     Wywołanie platformy umożliwia kierowanie ciągów z formatu zarządzanego (Unicode) do formatu ANSI.  
  
- Dopasowanie nazw  
  
     Gdy pole ma `true`wartość domyślną w Visual Basic, platforma wywoła wyszukiwanie tylko dla określonej nazwy. <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> Na przykład jeśli określisz element **MessageBox**, funkcja Invoke wywoła wyszukiwanie dla **MessageBox** i zakończy się niepowodzeniem, gdy nie będzie można zlokalizować dokładnej pisowni.  
  
     `false` C++ C#Gdy pole jest, ponieważ jest domyślnie w i, wywołanie platformy wyszuka alias niezniekształconej najpierw (MessageBox), a następnie nazwę zniekształcona (MessageBox), jeśli alias niezniekształconej nie zostanie znaleziony. `ExactSpelling` Należy zauważyć, że zachowanie dopasowania nazw ANSI różni się od zachowania dopasowywania nazw Unicode.  
  
 <xref:System.Runtime.InteropServices.CharSet.Unicode>  
  
- Kierowanie ciągów  
  
     Wywołanie platformy kopiuje ciągi z formatu zarządzanego (Unicode) do formatu Unicode.  
  
- Dopasowanie nazw  
  
     Gdy pole ma `true`wartość domyślną w Visual Basic, platforma wywoła wyszukiwanie tylko dla określonej nazwy. `ExactSpelling` Na przykład jeśli określisz element **MessageBox**, funkcja Invoke wywoła wyszukiwanie dla **MessageBox** i zakończy się niepowodzeniem, jeśli nie można zlokalizować dokładnej pisowni.  
  
     `false` C++ C#Gdy pole jest, ponieważ jest domyślnie w i, wywołanie platformy wyszukuje najpierw nazwę zniekształcona (MessageBoxW), a następnie alias niezniekształconej (MessageBox), jeśli nazwa zniekształcona nie zostanie znaleziona. `ExactSpelling` Zauważ, że zachowanie dopasowywania nazw Unicode różni się od zachowania dopasowania nazw ANSI.  
  
 <xref:System.Runtime.InteropServices.CharSet.Auto>  
  
- Wywołanie platformy wybiera między formatami ANSI i Unicode w czasie wykonywania, na podstawie platformy docelowej.  
  
## <a name="specifying-a-character-set-in-visual-basic"></a>Określanie zestawu znaków w Visual Basic  
 Poniższy przykład deklaruje funkcję **MessageBox** trzykrotnie, za każdym razem z innym zachowaniem zestawu znaków. Możesz określić zachowanie zestawu znaków w Visual Basic, dodając słowo kluczowe **ANSI**, **Unicode**lub słowa kluczowego do instrukcji deklaracji.  
  
 W przypadku pominięcia słowa kluczowego zestawu znaków, jak zostało to zrobione w pierwszej instrukcji deklaracji <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> , pole jest domyślnie ustawione na zestaw znaków ANSI. Drugie i trzecie instrukcje w przykładzie jawnie określają zestaw znaków za pomocą słowa kluczowego.  
  
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
  
## <a name="specifying-a-character-set-in-c-and-c"></a>Określanie zestawu znaków w C# iC++  
 <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> Pole Identyfikuje podstawowy zestaw znaków jako ANSI lub Unicode. Zestaw znaków kontroluje sposób organizowania argumentów ciągów dla metody. Aby wskazać zestaw znaków, użyj jednej z następujących form:  
  
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
  
 W poniższym przykładzie przedstawiono trzy zarządzane definicje funkcji **MessageBox** przypisanej do określenia zestawu znaków. W pierwszej definicji, z pominięciem, pole domyślnie `CharSet` jest zestaw znaków ANSI.  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [Tworzenie prototypów w kodzie zarządzanym](creating-prototypes-in-managed-code.md)
- [Przykłady wywołań platformy](platform-invoke-examples.md)
- [Marshaling danych w wywołaniu platformy](marshaling-data-with-platform-invoke.md)
