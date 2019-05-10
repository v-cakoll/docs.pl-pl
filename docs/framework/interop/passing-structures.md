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
ms.openlocfilehash: e932481496aef7fd0533054316deb32f65e95deb
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063183"
---
# <a name="passing-structures"></a>Przekazywanie struktur
Wiele funkcji niezarządzanych oczekuje przekazania jako parametr do funkcji elementów członkowskich struktury (typy zdefiniowane przez użytkownika w języku Visual Basic) lub elementów członkowskich klas, które są zdefiniowane w kodzie zarządzanym. Podczas wywołania przekazywanie struktury lub klasy do kodu niezarządzanego za pomocą platformy, należy podać dodatkowe informacje, aby zachować oryginalny układ i wyrównania. W tym temacie przedstawiono <xref:System.Runtime.InteropServices.StructLayoutAttribute> atrybut, który służy do definiowania typów sformatowany. Zarządzane struktur i klas, możesz wybrać z zachowaniami przewidywalne układu dostarczanych przez **LayoutKind** wyliczenia.  
  
 Centralny do koncepcji przedstawionych w tym temacie jest jedną istotną różnicą między typami struktury i klasy. Struktury są typami wartości i klasy są typami odwołań — klasy zawsze zapewniają co najmniej jeden poziom pośredni pamięci (wskaźnik do wartości). Różnica ta jest ważne, ponieważ niezarządzane funkcje często wymagają pośredniego, przedstawiony przez sygnatury w pierwszej kolumnie tabeli. Struktury zarządzanej i deklaracje klas w pozostałych kolumnach pokazano stopnia, do którego można dostosować poziom pośrednictwa w swojej deklaracji. Deklaracje znajdują się zarówno dla języka Visual Basic i Visual C#.  
  
|Niezarządzane podpisu|Deklaracja zarządzanego: <br />nie operatora pośredniego<br />`Structure MyType`<br />`struct MyType;`|Deklaracja zarządzanego: <br />jeden poziom pośredni<br />`Class MyType`<br />`class MyType;`|  
|-------------------------|---------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|  
|`DoWork(MyType x);`<br /><br /> Żądania poziomach pośredników od zera.|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> Dodaje zero poziomach operatorów pośrednich.|Nie jest możliwe, ponieważ istnieje już jeden poziom pośredni.|  
|`DoWork(MyType* x);`<br /><br /> Wymaga jednego poziomu pośredniego.|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> Dodaje jeden poziom pośrednictwa.|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> Dodaje zero poziomach operatorów pośrednich.|  
|`DoWork(MyType** x);`<br /><br /> Zapotrzebowania na dwóch poziomach operatorów pośrednich.|Nie jest możliwe ponieważ **ByRef** **ByRef** lub `ref` `ref` nie mogą być używane.|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> Dodaje jeden poziom pośrednictwa.|  
  
 W tabeli opisano następujące wytyczne dla deklaracji wywołania platformy:  
  
- Struktura przekazywany przez wartość, gdy niezarządzanej funkcji zapotrzebowania na pośrednie nie jest używana.  
  
- Użyj przekazywany przez odwołanie struktury lub klasy przekazywany przez wartość, gdy zapotrzebowania na jeden poziom pośredni w funkcji niezarządzanej.  
  
- Używanie klasy przekazywany przez odwołanie, gdy niezarządzanej funkcji zapotrzebowania na dwóch poziomach operatorów pośrednich.  
  
## <a name="declaring-and-passing-structures"></a>Deklarowanie i przekazywanie struktur  
 Poniższy przykład pokazuje jak zdefiniować `Point` i `Rect` struktury w kodzie zarządzanym i przekazywania typów jako parametr do **PtInRect** funkcji w pliku User32.dll. **PtInRect** ma następujący podpis niezarządzanych:  
  
```  
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 Należy zauważyć, że należy przekazać struktura Rect przez odwołanie, ponieważ funkcja oczekuje wskaźnika do typu Rect.  
  
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
 Elementy członkowskie klasy można przekazać do niezarządzanych funkcji DLL, tak długo, jak klasa ma układ członek stałej. W poniższym przykładzie pokazano sposób przekazywania członkowie `MySystemTime` klasy, które są zdefiniowane w porządku sekwencyjnym do **GetSystemTime** w pliku User32.dll. **GetSystemTime** ma następujący podpis niezarządzanych:  
  
```  
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 Inaczej niż w przypadku typów wartości klasy mają zawsze co najmniej jeden poziom pośrednictwa.  
  
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
