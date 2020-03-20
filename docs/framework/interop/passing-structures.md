---
title: Przekazywanie struktur
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- platform invoke, calling unmanaged functions
ms.assetid: 9b92ac73-32b7-4e1b-862e-6d8d950cf169
ms.openlocfilehash: 11e329fa8f0c059b6c2f1c8ccb1d6bd0d0f0030a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181335"
---
# <a name="passing-structures"></a>Przekazywanie struktur
Wiele funkcji niezarządzanych oczekuje, że przejdziesz, jako parametr do funkcji, członków struktur (zdefiniowane przez użytkownika typy w języku Visual Basic) lub członków klas, które są zdefiniowane w kodzie zarządzanym. Podczas przekazywania struktur lub klas do kodu niezarządzanego przy użyciu platformy wywołać, należy podać dodatkowe informacje, aby zachować oryginalny układ i wyrównanie. W tym temacie <xref:System.Runtime.InteropServices.StructLayoutAttribute> przedstawiono atrybut, którego używasz do definiowania sformatowanych typów. Dla struktur zarządzanych i klas można wybrać z kilku przewidywalnych zachowań układu dostarczonych przez **LayoutKind** wyliczenia.  
  
 Centralnym elementem pojęć przedstawionych w tym temacie jest istotna różnica między strukturą a typami klas. Struktury są typy wartości i klasy są typy odwołań — klasy zawsze zapewniają co najmniej jeden poziom pośredniej pamięci (wskaźnik do wartości). Ta różnica jest ważna, ponieważ funkcje niezarządzane często wymagają pośredniego, jak pokazano w podpisach w pierwszej kolumnie poniższej tabeli. Struktura zarządzana i deklaracje klas w pozostałych kolumnach pokazują stopień, w jakim można dostosować poziom pośredni w deklaracji. Deklaracje są dostarczane dla języka Visual Basic i Visual C#.  
  
|Podpis niezarządzany|Deklaracja zarządzana: <br />bez pośrednictwa<br />`Structure MyType`<br />`struct MyType;`|Deklaracja zarządzana: <br />jeden poziom pośredni<br />`Class MyType`<br />`class MyType;`|  
|-------------------------|---------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|  
|`DoWork(MyType x);`<br /><br /> Wymaga zerowych poziomów pośrednictwu.|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> Dodaje zerowe poziomy pośrednictwu.|Nie jest to możliwe, ponieważ istnieje już jeden poziom pośredni.|  
|`DoWork(MyType* x);`<br /><br /> Wymaga jednego poziomu pośredniego.|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> Dodaje jeden poziom pośredni.|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> Dodaje zerowe poziomy pośrednictwu.|  
|`DoWork(MyType** x);`<br /><br /> Wymaga dwóch poziomów pośrednich.|Nie jest to możliwe, `ref` `ref` ponieważ **ByRef** **ByRef** lub nie można użyć.|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> Dodaje jeden poziom pośredni.|  
  
 W tabeli opisano następujące wskazówki dotyczące deklaracji wywoływania przez platformę:  
  
- Użyj struktury przekazywane przez wartość, gdy funkcja niezarządzana wymaga nie indirection.  
  
- Użyj struktury przekazywane przez odwołanie lub klasy przekazywane przez wartość, gdy funkcja niezarządzana wymaga jednego poziomu pośredniego.  
  
- Użyj klasy przekazywane przez odwołanie, gdy funkcja niezarządzana wymaga dwóch poziomów pośrednich.  
  
## <a name="declaring-and-passing-structures"></a>Deklarowanie i przekazywanie struktur  
 Poniższy przykład pokazuje, `Point` jak `Rect` zdefiniować i struktur w kodzie zarządzanym i przekazać typy jako parametr do **funkcji PtInRect** w pliku User32.dll. **PtInRect** ma następujący podpis niezarządzany:  
  
```cpp
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 Należy zauważyć, że należy przekazać Rect struktury przez odwołanie, ponieważ funkcja oczekuje wskaźnik do typu RECT.  
  
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
  
Friend Class NativeMethods
    Friend Declare Auto Function PtInRect Lib "user32.dll" (
        ByRef r As Rect, p As Point) As Boolean  
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
  
internal static class NativeMethods
{  
    [DllImport("User32.dll")]  
    internal static extern bool PtInRect(ref Rect r, Point p);  
}  
```  
  
## <a name="declaring-and-passing-classes"></a>Deklarowanie i przekazywanie klas  
 Można przekazać członków klasy do niezarządzanej funkcji DLL, tak długo, jak klasa ma układ stałego elementu członkowskiego. W poniższym przykładzie pokazano, `MySystemTime` jak przekazać członków klasy, które są zdefiniowane w kolejności sekwencyjnej, do **GetSystemTime** w pliku User32.dll. **GetSystemTime** ma następujący podpis niezarządzany:  
  
```cpp
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 W przeciwieństwie do typów wartości klasy zawsze mają co najmniej jeden poziom pośredni.  
  
```vb  
Imports System.Runtime.InteropServices  
  
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
  
Friend Class NativeMethods  
    Friend Declare Auto Sub GetSystemTime Lib "Kernel32.dll" (
        sysTime As MySystemTime)  
    Friend Declare Auto Function MessageBox Lib "User32.dll" (
        hWnd As IntPtr, lpText As String, lpCaption As String, uType As UInteger) As Integer  
End Class  
  
Public Class TestPlatformInvoke
    Public Shared Sub Main()  
        Dim sysTime As New MySystemTime()  
        NativeMethods.GetSystemTime(sysTime)  
  
        Dim dt As String  
        dt = "System time is:" & ControlChars.CrLf & _  
              "Year: " & sysTime.wYear & _  
              ControlChars.CrLf & "Month: " & sysTime.wMonth & _  
              ControlChars.CrLf & "DayOfWeek: " & sysTime.wDayOfWeek & _  
              ControlChars.CrLf & "Day: " & sysTime.wDay  
        NativeMethods.MessageBox(IntPtr.Zero, dt, "Platform Invoke Sample", 0)
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
internal static class NativeMethods
{  
    [DllImport("Kernel32.dll")]  
    internal static extern void GetSystemTime(MySystemTime st);  
  
    [DllImport("user32.dll", CharSet = CharSet.Auto)]  
    internal static extern int MessageBox(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);  
}  
  
public class TestPlatformInvoke  
{  
    public static void Main()  
    {  
        MySystemTime sysTime = new MySystemTime();  
        NativeMethods.GetSystemTime(sysTime);  
  
        string dt;  
        dt = "System time is: \n" +  
              "Year: " + sysTime.wYear + "\n" +  
              "Month: " + sysTime.wMonth + "\n" +  
              "DayOfWeek: " + sysTime.wDayOfWeek + "\n" +  
              "Day: " + sysTime.wDay;  
        NativeMethods.MessageBox(IntPtr.Zero, dt, "Platform Invoke Sample", 0);  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz też

- [Wywołanie funkcji DLL](calling-a-dll-function.md)
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- <xref:System.Runtime.InteropServices.FieldOffsetAttribute>
