---
title: Określanie punktu wejścia
ms.date: 03/30/2017
helpviewer_keywords:
- EntryPoint field
- platform invoke, attribute fields
- attribute fields in platform invoke, EntryPoint
ms.assetid: d1247f08-0965-416a-b978-e0b50652dfe3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 15a441ea7b0b16c83c590289d04cf0c10623fb85
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59086068"
---
# <a name="specifying-an-entry-point"></a>Określanie punktu wejścia
Punkt wejścia określa lokalizację funkcji w bibliotece DLL. W obrębie zarządzanego projektu, oryginalna nazwa lub porządkowy punkt wejścia docelowej funkcji określa tę funkcję wewnątrz międzyoperacyjnej granicy. Co więcej, możesz zmapować punkt wejścia do innej nazwy, efektywnie zmieniając nazwę funkcji.  
  
 Poniższa lista zawiera możliwe powody zmiany nazwy funkcji DLL:  
  
-   Aby uniknąć używania nazw funkcji API wrażliwych na wielkość liter  
  
-   Aby postępować zgodnie z istniejącymi standardami nazewnictwa  
  
-   Aby pomieścić funkcje, które przyjmują różne typy danych (poprzez deklarację wielu wersji tej samej funkcji DLL)  
  
-   Aby uprościć używanie API, które zawierają wersje ANSI i Unicode  
  
 Ten temat demonstruje, w jaki sposób zmienić nazwę funkcji DLL w kodzie zarządzanym.  
  
## <a name="renaming-a-function-in-visual-basic"></a>Zmiana nazwy funkcji w języku Visual Basic  
 Visual Basic stosuje **funkcja** — słowo kluczowe w **Declare** instrukcję, aby ustawić <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> pola. Poniższy przykład pokazuje podstawową deklarację.  
  
```vb
Imports System

Friend Class WindowsAPI
    Friend Shared Declare Auto Function MessageBox Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
 Możesz zastąpić **MessageBox** punktu wejścia przy użyciu **MsgBox** umieszczając **Alias** — słowo kluczowe w definicji, jak pokazano w poniższym przykładzie. W obu przykładach **automatycznie** — słowo kluczowe eliminuje potrzebę określenia wersji zestawu znaków punktu wejścia. Aby uzyskać więcej informacji o wybieraniu znak zestawu, zobacz [Określanie zestawu znaków](../../../docs/framework/interop/specifying-a-character-set.md).  
  
```vb
Imports System

Friend Class WindowsAPI
    Friend Shared Declare Auto Function MsgBox _
        Lib "user32.dll" Alias "MessageBox" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
## <a name="renaming-a-function-in-c-and-c"></a>Zmiana nazwy funkcji w języku C# i C++  
 Można użyć pola <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType>, aby określić funkcję DLL po nazwie lub liczbie porządkowej. Jeśli nazwa funkcji w definicji metody jest taka sama jak punkt wejścia w DLL, nie trzeba jawnie identyfikować funkcji przy użyciu **punktu wejścia** pola. W innym wypadku, użyj jednego z poniższych form atrybutów, aby wskazać nazwę lub liczbę porządkową:  
  
```csharp
[DllImport("DllName", EntryPoint = "Functionname")]
[DllImport("DllName", EntryPoint = "#123")]
```
  
 Należy zauważyć, że liczba porządkowa musi być poprzedzona znakiem kratki (#).  
  
 Poniższy przykład demonstruje sposób zamiany **MessageBoxA** z **MsgBox** w kodzie za pomocą **punktu wejścia** pola.  
  
```csharp
using System;
using System.Runtime.InteropServices;

internal static class WindowsAPI
{
    [DllImport("user32.dll", EntryPoint = "MessageBoxA")]
    internal static extern int MessageBox(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);
}
```
  
```cpp
using namespace System;
using namespace System::Runtime::InteropServices;

typedef void* HWND;
[DllImport("user32", EntryPoint = "MessageBoxA")]
extern "C" int MsgBox(
    HWND hWnd, String* lpText, String* lpCaption, unsigned int uType);
```
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [Tworzenie prototypów w kodzie zarządzanym](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)
- [Przykłady wywołań platformy](../../../docs/framework/interop/platform-invoke-examples.md)
- [Marshaling danych w wywołaniu platformy](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)
