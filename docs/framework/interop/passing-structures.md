---
title: Przekazywanie struktur
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- platform invoke, calling unmanaged functions
ms.assetid: 9b92ac73-32b7-4e1b-862e-6d8d950cf169
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9e1eff9d1ef9f36c80f71e738fdd4dc56a9b6ec6
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894142"
---
# <a name="passing-structures"></a>Przekazywanie struktur
Wiele niezarządzanych funkcji oczekuje, że jako parametr funkcji, elementy członkowskie struktur (typy zdefiniowane przez użytkownika w Visual Basic) lub elementy członkowskie klas, które są zdefiniowane w kodzie zarządzanym. Podczas przekazywania struktur lub klas do niezarządzanego kodu przy użyciu funkcji Invoke platformy należy podać dodatkowe informacje, aby zachować oryginalny układ i wyrównanie. W tym temacie wprowadzono <xref:System.Runtime.InteropServices.StructLayoutAttribute> atrybut, którego można użyć do zdefiniowania sformatowanych typów. Dla zarządzanych struktur i klas można wybrać spośród kilku przewidzianych zachowań układu **LayoutKind** .  
  
 Centralne koncepcje przedstawione w tym temacie są istotną różnicą między strukturą i typami klas. Struktury są typami wartości, a klasy są typami odwołań — klasy zawsze zapewniają co najmniej jeden poziom pośredni pamięci (wskaźnik do wartości). Różnica ta jest ważna, ponieważ funkcje niezarządzane często żądają pośrednika, jak pokazano w podpisach w pierwszej kolumnie tabeli poniżej. Struktura zarządzana i deklaracje klas w pozostałych kolumnach przedstawiają stopień, w jakim można dostosować poziom pośredni w deklaracji. Deklaracje są udostępniane zarówno dla Visual Basic, C#jak i dla wizualizacji.  
  
|Niezarządzany podpis|Deklaracja zarządzana: <br />Brak pośrednich<br />`Structure MyType`<br />`struct MyType;`|Deklaracja zarządzana: <br />jeden poziom pośredni<br />`Class MyType`<br />`class MyType;`|  
|-------------------------|---------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|  
|`DoWork(MyType x);`<br /><br /> Wymaga zerowych poziomów pośrednich.|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> Dodaje zero poziomów pośrednich.|Nie jest możliwe, ponieważ istnieje już jeden poziom pośredni.|  
|`DoWork(MyType* x);`<br /><br /> Wymaga jednego poziomu pośredniego.|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> Dodaje jeden poziom pośredni.|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> Dodaje zero poziomów pośrednich.|  
|`DoWork(MyType** x);`<br /><br /> Wymaga dwóch poziomów pośrednich.|Niemożliwa, ponieważ **ByRef** **ByRef** lub `ref` `ref` nie można użyć.|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> Dodaje jeden poziom pośredni.|  
  
 W tabeli opisano następujące wskazówki dotyczące deklaracji wywołania platformy:  
  
- Użyj struktury przeszacowanej przez wartość, gdy niezarządzana funkcja nie wymaga pośredniego.  
  
- Użyj struktury przeszacowanej przez odwołanie lub klasy przekazaną przez wartość, gdy niezarządzana funkcja wymaga jednego poziomu pośredniego.  
  
- Użyj klasy przekazaną przez odwołanie, gdy niezarządzana funkcja wymaga dwóch poziomów pośrednika.  
  
## <a name="declaring-and-passing-structures"></a>Deklarowanie i przekazywanie struktur  
 Poniższy przykład pokazuje, `Point` jak zdefiniować struktury i `Rect` w kodzie zarządzanym i przekazać typy jako parametr do funkcji **PtInRect** w pliku User32. dll. **PtInRect** ma następujący niezarządzany podpis:  
  
```cpp
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 Należy zwrócić uwagę, że należy przekazać strukturę Rect przez odwołanie, ponieważ funkcja oczekuje wskaźnika do typu RECT.  
  
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
 Elementy członkowskie klasy można przekazać do niezarządzanej funkcji DLL, o ile Klasa ma stały układ elementu członkowskiego. Poniższy przykład ilustruje sposób przekazywania elementów członkowskich `MySystemTime` klasy, które są zdefiniowane w kolejności sekwencyjnej, do **GetSystemTime** w pliku User32. dll. **GetSystemTime** ma następujący niezarządzany podpis:  
  
```cpp
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 W przeciwieństwie do typów wartości, klasy zawsze mają co najmniej jeden poziom pośredni.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Wywołanie funkcji DLL](../../../docs/framework/interop/calling-a-dll-function.md)
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- <xref:System.Runtime.InteropServices.FieldOffsetAttribute>
