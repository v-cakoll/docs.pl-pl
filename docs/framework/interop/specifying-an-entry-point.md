---
title: "Określanie punktu wejścia"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- EntryPoint field
- platform invoke, attribute fields
- attribute fields in platform invoke, EntryPoint
ms.assetid: d1247f08-0965-416a-b978-e0b50652dfe3
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7486820d78d767b8eb79397d6179ac81efc27968
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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
 Używa języka Visual Basic **funkcja** — słowo kluczowe w **Declare** instrukcja <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> pola. Poniższy przykład pokazuje podstawową deklarację.  
  
```vb  
Imports System.Runtime.InteropServices  
  
Public Class Win32  
    Declare Auto Function MessageBox Lib "user32.dll" _  
       (ByVal hWnd As Integer, ByVal txt As String,_  
       ByVal caption As String, ByVal Typ As Integer) As Integer  
End Class  
```  
  
 Można zastąpić **MessageBox** punkt wejścia z **MsgBox** przez dołączenie **Alias** — słowo kluczowe w definicji, jak pokazano w poniższym przykładzie. W obu przykładach **automatycznie** — słowo kluczowe eliminuje potrzebę Określ wersję zestawu znaków punktu wejścia. Aby uzyskać więcej informacji o wybieraniu znak, zobacz [określający zestaw znaków](../../../docs/framework/interop/specifying-a-character-set.md).  
  
```vb  
Imports System.Runtime.InteropServices  
  
Public Class Win32  
    Declare Auto Function MsgBox Lib "user32.dll" _  
       Alias "MessageBox" (ByVal hWnd As Integer, ByVal txt As String,_  
       ByVal caption As String, ByVal Typ As Integer) As Integer  
End Class  
```  
  
## <a name="renaming-a-function-in-c-and-c"></a>Zmiana nazwy funkcji w języku C# i C++  
 Można użyć pola <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType>, aby określić funkcję DLL po nazwie lub liczbie porządkowej. Jeśli nazwa funkcji w definicji metody jest taka sama jak punkt wejścia w bibliotece DLL, nie trzeba jawnie zidentyfikowanie funkcji z **punktu wejścia** pola. W innym wypadku, użyj jednego z poniższych form atrybutów, aby wskazać nazwę lub liczbę porządkową:  
  
```  
[DllImport("dllname", EntryPoint="Functionname")]  
[DllImport("dllname", EntryPoint="#123")]  
```  
  
 Należy zauważyć, że liczba porządkowa musi być poprzedzona znakiem kratki (#).  
  
 W poniższym przykładzie pokazano, jak zastąpić **MessageBoxA** z **MsgBox** w kodzie za pomocą **punktu wejścia** pola.  
  
```csharp  
using System.Runtime.InteropServices;  
  
public class Win32 {  
    [DllImport("user32.dll", EntryPoint="MessageBoxA")]  
    public static extern int MsgBox(int hWnd, String text, String caption,  
                                    uint type);  
}  
```  
  
```cpp  
using namespace System::Runtime::InteropServices;  
  
typedef void* HWND;  
[DllImport("user32", EntryPoint="MessageBoxA")]  
extern "C" int MsgBox(HWND hWnd,  
                      String*  pText,  
                      String*  pCaption,  
                      unsigned int uType);  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.InteropServices.DllImportAttribute>  
 [Tworzenie prototypów w kodzie zarządzanym](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)  
 [Przykłady wywołań platformy](../../../docs/framework/interop/platform-invoke-examples.md)  
 [Marshaling danych w wywołaniu platformy](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)
