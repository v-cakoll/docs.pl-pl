---
title: Przekazywanie struktur
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: platform invoke, calling unmanaged functions
ms.assetid: 9b92ac73-32b7-4e1b-862e-6d8d950cf169
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a30905fdcf7063f6ecdae0346c9c5ee39b450be9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="passing-structures"></a>Przekazywanie struktur
Wiele funkcji niezarządzanej oczekiwać, że można przekazać jako parametru funkcji, członków struktur (Typy definiowane przez użytkownika w języku Visual Basic) lub klas zdefiniowanych w kodzie zarządzanym. Podczas wywołania przekazywanie struktury lub klasy do kodu niezarządzanego, przy użyciu platformy, należy podać dodatkowe informacje, aby zachować oryginalne układ i wyrównania. W tym temacie przedstawiono <xref:System.Runtime.InteropServices.StructLayoutAttribute> atrybut, który służy do definiowania typów sformatowany. Zarządzane, struktur i klas, możesz wybrać z zachowaniami przewidywalną układu dostarczanych przez **LayoutKind** wyliczenia.  
  
 Centralnej do koncepcji przedstawionych w tym temacie jest istotną różnicą między typami struktury i klasy. Typy wartości są struktur i klas typów referencyjnych — klas zawsze podawać co najmniej jeden poziom pośredni pamięci (wskaźnik do wartości). Ta różnica jest ważne, ponieważ funkcje niezarządzane często wymaga pośredni, pokazane podpisów w pierwszej kolumnie tabeli. Zarządzane struktury i klasy deklaracje w pozostałych kolumnach Pokaż stopień, do którego można dostosować poziom pośredni w Twojej deklaracji. Deklaracje są udostępniane dla języka Visual Basic i Visual C#.  
  
|Niezarządzanego podpisu|Deklaracja zarządzanego: <br />nie pośredni<br />`Structure MyType`<br />`struct MyType;`|Deklaracja zarządzanego: <br />jeden poziom pośredni<br />`Class MyType`<br />`class MyType;`|  
|-------------------------|---------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|  
|`DoWork(MyType x);`<br /><br /> Wymagania poziomach pośredników od zera.|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> Dodaje zero poziomach operatorów pośrednich.|Nie jest możliwa, ponieważ istnieje już jeden poziom pośredni.|  
|`DoWork(MyType* x);`<br /><br /> Wymaga pośredników o jeden poziom.|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> Dodaje pośredników o jeden poziom.|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> Dodaje zero poziomach operatorów pośrednich.|  
|`DoWork(MyType** x);`<br /><br /> Wymaga dwóch poziomach operatorów pośrednich.|Nie jest możliwe ponieważ **ByRef** **ByRef** lub `ref` `ref` nie można użyć.|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> Dodaje pośredników o jeden poziom.|  
  
 W tabeli opisano następujące wskazówki dla deklaracji wywołania platformy:  
  
-   Struktura przekazany przez wartość, gdy pośredni nie żąda niezarządzanej funkcji jest używana.  
  
-   Użyj struktury przekazywana przez odwołanie, lub klasy przekazany przez wartość, gdy jeden poziom pośredni żąda niezarządzanej funkcji.  
  
-   Używanie klasy przekazywany przez odwołanie, gdy dwa poziomy pośredni żąda niezarządzanej funkcji.  
  
## <a name="declaring-and-passing-structures"></a>Deklarowanie i przekazywanie struktur  
 Poniższy przykład przedstawia sposób definiowania `Point` i `Rect` struktury w kodzie zarządzanym i przekazywania typów jako parametr do **PtInRect** funkcji w pliku User32.dll. **PtInRect** ma następujące niezarządzanego podpisu:  
  
```  
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 Należy zauważyć, że trzeba przekazać struktura Rect przez odwołanie, ponieważ funkcja oczekuje wskaźnika do typu Rect.  
  
```vb  
Imports System.Runtime.InteropServices  
  
<StructLayout(LayoutKind.Sequential)> Public Structure Point  
    Public x As Integer  
    Public y As Integer  
End Structure  
  
Public Structure <StructLayout(LayoutKind.Explicit)> Rect  
    <FieldOffset(0)> Public left As Integer  
    <FieldOffset(4)> Public top As Integer  
    <FieldOffset(8)> Public right As Integer  
    <FieldOffset(12)> Public bottom As Integer  
End Structure  
  
Class Win32API      
    Declare Auto Function PtInRect Lib "user32.dll" _  
    (ByRef r As Rect, p As Point) As Boolean  
End Class  
```  
  
```csharp  
using System.Runtime.InteropServices;  
  
[StructLayout(LayoutKind.Sequential)]  
public struct Point {  
    public int x;  
    public int y;  
}     
  
[StructLayout(LayoutKind.Explicit)]  
public struct Rect {  
    [FieldOffset(0)] public int left;  
    [FieldOffset(4)] public int top;  
    [FieldOffset(8)] public int right;  
    [FieldOffset(12)] public int bottom;  
}     
  
class Win32API {  
    [DllImport("User32.dll")]  
    public static extern bool PtInRect(ref Rect r, Point p);  
}  
```  
  
## <a name="declaring-and-passing-classes"></a>Deklarowanie i przekazywanie klas  
 Elementy członkowskie klasy można przekazać do funkcji niezarządzanej DLL, tak długo, jak klasa ma układ stałego elementu członkowskiego. W poniższym przykładzie pokazano sposób przekazywania członkami `MySystemTime` klasy, które są zdefiniowane w kolejności sekwencyjnej, do **GetSystemTime** w pliku User32.dll. **GetSystemTime** ma następujące niezarządzanego podpisu:  
  
```  
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 W przeciwieństwie do typów wartości klasy zawsze mają co najmniej jeden poziom pośredni.  
  
```vb  
Imports System  
Imports System.Runtime.InteropServices  
Imports Microsoft.VisualBasic  
  
<StructLayout(LayoutKind.Sequential)> Public Class MySystemTime  
    Public wYear As Short  
    Public wMonth As Short  
    Public wDayOfWeek As Short   
    Public wDay As Short  
    Public wHour As Short  
    Public wMinute As Short  
    Public wSecond As Short  
    Public wMiliseconds As Short  
End Class  
  
Public Class Win32  
    Declare Auto Sub GetSystemTime Lib "Kernel32.dll"(sysTime _  
        As MySystemTime)  
    Declare Auto Function MessageBox Lib "User32.dll"(hWnd As IntPtr, _  
        txt As String, caption As String, Typ As Integer) As Integer  
End Class  
  
Public Class TestPlatformInvoke      
    Public Shared Sub Main()  
        Dim sysTime As New MySystemTime()  
        Win32.GetSystemTime(sysTime)  
  
        Dim dt As String  
        dt = "System time is:" & ControlChars.CrLf & _  
              "Year: " & sysTime.wYear & _  
              ControlChars.CrLf & "Month: " & sysTime.wMonth & _  
              ControlChars.CrLf & "DayOfWeek: " & sysTime.wDayOfWeek & _  
              ControlChars.CrLf & "Day: " & sysTime.wDay  
        Win32.MessageBox(IntPtr.Zero, dt, "Platform Invoke Sample", 0)        
    End Sub  
End Class  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential)]  
public class MySystemTime {  
    public ushort wYear;   
    public ushort wMonth;  
    public ushort wDayOfWeek;   
    public ushort wDay;   
    public ushort wHour;   
    public ushort wMinute;   
    public ushort wSecond;   
    public ushort wMilliseconds;   
}  
class Win32API {  
    [DllImport("Kernel32.dll")]  
    public static extern void GetSystemTime(MySystemTime st);  
  
    [DllImport("user32.dll", CharSet=CharSet.Auto)]  
     public static extern int MessageBox(IntPtr hWnd,  
         string text, string caption, int options);  
}  
  
public class TestPlatformInvoke  
{  
    public static void Main()  
    {  
        MySystemTime sysTime = new MySystemTime();  
        Win32API.GetSystemTime(sysTime);  
  
        string dt;  
        dt = "System time is: \n" +  
              "Year: " + sysTime.wYear + "\n" +  
              "Month: " + sysTime.wMonth + "\n" +  
              "DayOfWeek: " + sysTime.wDayOfWeek + "\n" +  
              "Day: " + sysTime.wDay;  
        Win32API.MessageBox(IntPtr.Zero, dt, "Platform Invoke Sample", 0);  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Wywołanie funkcji DLL](../../../docs/framework/interop/calling-a-dll-function.md)  
 <xref:System.Runtime.InteropServices.StructLayoutAttribute>  
 <xref:System.Runtime.InteropServices.StructLayoutAttribute>  
 <xref:System.Runtime.InteropServices.FieldOffsetAttribute>
