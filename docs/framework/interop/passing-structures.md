---
title: Przekazywanie struktur
description: Dowiedz się, jak przekazywać struktury i klasy do funkcji niezarządzanych. Dowiedz się więcej o atrybucie StructLayoutAttribute, który służy do definiowania sformatowanych typów.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- platform invoke, calling unmanaged functions
ms.assetid: 9b92ac73-32b7-4e1b-862e-6d8d950cf169
ms.openlocfilehash: eae28d6746cd89d98b659b9eb957f158e1319190
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620823"
---
# <a name="passing-structures"></a><span data-ttu-id="eea74-104">Przekazywanie struktur</span><span class="sxs-lookup"><span data-stu-id="eea74-104">Passing Structures</span></span>
<span data-ttu-id="eea74-105">Wiele niezarządzanych funkcji oczekuje, że jako parametr funkcji, elementy członkowskie struktur (typy zdefiniowane przez użytkownika w Visual Basic) lub elementy członkowskie klas, które są zdefiniowane w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="eea74-105">Many unmanaged functions expect you to pass, as a parameter to the function, members of structures (user-defined types in Visual Basic) or members of classes that are defined in managed code.</span></span> <span data-ttu-id="eea74-106">Podczas przekazywania struktur lub klas do niezarządzanego kodu przy użyciu funkcji Invoke platformy należy podać dodatkowe informacje, aby zachować oryginalny układ i wyrównanie.</span><span class="sxs-lookup"><span data-stu-id="eea74-106">When passing structures or classes to unmanaged code using platform invoke, you must provide additional information to preserve the original layout and alignment.</span></span> <span data-ttu-id="eea74-107">W tym temacie wprowadzono <xref:System.Runtime.InteropServices.StructLayoutAttribute> atrybut, którego można użyć do zdefiniowania sformatowanych typów.</span><span class="sxs-lookup"><span data-stu-id="eea74-107">This topic introduces the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute, which you use to define formatted types.</span></span> <span data-ttu-id="eea74-108">Dla zarządzanych struktur i klas można wybrać spośród kilku przewidzianych zachowań układu **LayoutKind** .</span><span class="sxs-lookup"><span data-stu-id="eea74-108">For managed structures and classes, you can select from several predictable layout behaviors supplied by the **LayoutKind** enumeration.</span></span>  
  
 <span data-ttu-id="eea74-109">Centralne koncepcje przedstawione w tym temacie są istotną różnicą między strukturą i typami klas.</span><span class="sxs-lookup"><span data-stu-id="eea74-109">Central to the concepts presented in this topic is an important difference between structure and class types.</span></span> <span data-ttu-id="eea74-110">Struktury są typami wartości, a klasy są typami odwołań — klasy zawsze zapewniają co najmniej jeden poziom pośredni pamięci (wskaźnik do wartości).</span><span class="sxs-lookup"><span data-stu-id="eea74-110">Structures are value types and classes are reference types — classes always provide at least one level of memory indirection (a pointer to a value).</span></span> <span data-ttu-id="eea74-111">Różnica ta jest ważna, ponieważ funkcje niezarządzane często żądają pośrednika, jak pokazano w podpisach w pierwszej kolumnie tabeli poniżej.</span><span class="sxs-lookup"><span data-stu-id="eea74-111">This difference is important because unmanaged functions often demand indirection, as shown by the signatures in the first column of the following table.</span></span> <span data-ttu-id="eea74-112">Struktura zarządzana i deklaracje klas w pozostałych kolumnach przedstawiają stopień, w jakim można dostosować poziom pośredni w deklaracji. Deklaracje są dostępne dla Visual Basic i Visual C#.</span><span class="sxs-lookup"><span data-stu-id="eea74-112">The managed structure and class declarations in the remaining columns show the degree to which you can adjust the level of indirection in your declaration.Declarations are provided for both Visual Basic and Visual C#.</span></span>  
  
|<span data-ttu-id="eea74-113">Niezarządzany podpis</span><span class="sxs-lookup"><span data-stu-id="eea74-113">Unmanaged signature</span></span>|<span data-ttu-id="eea74-114">Deklaracja zarządzana:</span><span class="sxs-lookup"><span data-stu-id="eea74-114">Managed declaration:</span></span> <br /><span data-ttu-id="eea74-115">Brak pośrednich</span><span class="sxs-lookup"><span data-stu-id="eea74-115">no indirection</span></span><br />`Structure MyType`<br />`struct MyType;`|<span data-ttu-id="eea74-116">Deklaracja zarządzana:</span><span class="sxs-lookup"><span data-stu-id="eea74-116">Managed declaration:</span></span> <br /><span data-ttu-id="eea74-117">jeden poziom pośredni</span><span class="sxs-lookup"><span data-stu-id="eea74-117">one level of indirection</span></span><br />`Class MyType`<br />`class MyType;`|  
|-------------------------|---------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|  
|`DoWork(MyType x);`<br /><br /> <span data-ttu-id="eea74-118">Wymaga zerowych poziomów pośrednich.</span><span class="sxs-lookup"><span data-stu-id="eea74-118">Demands zero levels of indirection.</span></span>|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> <span data-ttu-id="eea74-119">Dodaje zero poziomów pośrednich.</span><span class="sxs-lookup"><span data-stu-id="eea74-119">Adds zero levels of indirection.</span></span>|<span data-ttu-id="eea74-120">Nie jest możliwe, ponieważ istnieje już jeden poziom pośredni.</span><span class="sxs-lookup"><span data-stu-id="eea74-120">Not possible because there is already one level of indirection.</span></span>|  
|`DoWork(MyType* x);`<br /><br /> <span data-ttu-id="eea74-121">Wymaga jednego poziomu pośredniego.</span><span class="sxs-lookup"><span data-stu-id="eea74-121">Demands one level of indirection.</span></span>|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> <span data-ttu-id="eea74-122">Dodaje jeden poziom pośredni.</span><span class="sxs-lookup"><span data-stu-id="eea74-122">Adds one level of indirection.</span></span>|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> <span data-ttu-id="eea74-123">Dodaje zero poziomów pośrednich.</span><span class="sxs-lookup"><span data-stu-id="eea74-123">Adds zero levels of indirection.</span></span>|  
|`DoWork(MyType** x);`<br /><br /> <span data-ttu-id="eea74-124">Wymaga dwóch poziomów pośrednich.</span><span class="sxs-lookup"><span data-stu-id="eea74-124">Demands two levels of indirection.</span></span>|<span data-ttu-id="eea74-125">Niemożliwa, ponieważ **ByRef** **ByRef** lub `ref` `ref` nie można użyć.</span><span class="sxs-lookup"><span data-stu-id="eea74-125">Not possible because **ByRef** **ByRef** or `ref` `ref` cannot be used.</span></span>|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> <span data-ttu-id="eea74-126">Dodaje jeden poziom pośredni.</span><span class="sxs-lookup"><span data-stu-id="eea74-126">Adds one level of indirection.</span></span>|  
  
 <span data-ttu-id="eea74-127">W tabeli opisano następujące wskazówki dotyczące deklaracji wywołania platformy:</span><span class="sxs-lookup"><span data-stu-id="eea74-127">The table describes the following guidelines for platform invoke declarations:</span></span>  
  
- <span data-ttu-id="eea74-128">Użyj struktury przeszacowanej przez wartość, gdy niezarządzana funkcja nie wymaga pośredniego.</span><span class="sxs-lookup"><span data-stu-id="eea74-128">Use a structure passed by value when the unmanaged function demands no indirection.</span></span>  
  
- <span data-ttu-id="eea74-129">Użyj struktury przeszacowanej przez odwołanie lub klasy przekazaną przez wartość, gdy niezarządzana funkcja wymaga jednego poziomu pośredniego.</span><span class="sxs-lookup"><span data-stu-id="eea74-129">Use either a structure passed by reference or a class passed by value when the unmanaged function demands one level of indirection.</span></span>  
  
- <span data-ttu-id="eea74-130">Użyj klasy przekazaną przez odwołanie, gdy niezarządzana funkcja wymaga dwóch poziomów pośrednika.</span><span class="sxs-lookup"><span data-stu-id="eea74-130">Use a class passed by reference when the unmanaged function demands two levels of indirection.</span></span>  
  
## <a name="declaring-and-passing-structures"></a><span data-ttu-id="eea74-131">Deklarowanie i przekazywanie struktur</span><span class="sxs-lookup"><span data-stu-id="eea74-131">Declaring and Passing Structures</span></span>  
 <span data-ttu-id="eea74-132">Poniższy przykład pokazuje, jak zdefiniować `Point` `Rect` struktury i w kodzie zarządzanym i przekazać typy jako parametr do funkcji **PtInRect** w pliku User32.dll.</span><span class="sxs-lookup"><span data-stu-id="eea74-132">The following example shows how to define the `Point` and `Rect` structures in managed code, and pass the types as parameter to the **PtInRect** function in the User32.dll file.</span></span> <span data-ttu-id="eea74-133">**PtInRect** ma następujący niezarządzany podpis:</span><span class="sxs-lookup"><span data-stu-id="eea74-133">**PtInRect** has the following unmanaged signature:</span></span>  
  
```cpp
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 <span data-ttu-id="eea74-134">Należy zwrócić uwagę, że należy przekazać strukturę Rect przez odwołanie, ponieważ funkcja oczekuje wskaźnika do typu RECT.</span><span class="sxs-lookup"><span data-stu-id="eea74-134">Notice that you must pass the Rect structure by reference, since the function expects a pointer to a RECT type.</span></span>  
  
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
  
## <a name="declaring-and-passing-classes"></a><span data-ttu-id="eea74-135">Deklarowanie i przekazywanie klas</span><span class="sxs-lookup"><span data-stu-id="eea74-135">Declaring and Passing Classes</span></span>  
 <span data-ttu-id="eea74-136">Elementy członkowskie klasy można przekazać do niezarządzanej funkcji DLL, o ile Klasa ma stały układ elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="eea74-136">You can pass members of a class to an unmanaged DLL function, as long as the class has a fixed member layout.</span></span> <span data-ttu-id="eea74-137">Poniższy przykład ilustruje sposób przekazywania elementów członkowskich `MySystemTime` klasy, które są zdefiniowane w kolejności sekwencyjnej, do **GetSystemTime** w pliku User32.dll.</span><span class="sxs-lookup"><span data-stu-id="eea74-137">The following example demonstrates how to pass members of the `MySystemTime` class, which are defined in sequential order, to the **GetSystemTime** in the User32.dll file.</span></span> <span data-ttu-id="eea74-138">**GetSystemTime** ma następujący niezarządzany podpis:</span><span class="sxs-lookup"><span data-stu-id="eea74-138">**GetSystemTime** has the following unmanaged signature:</span></span>  
  
```cpp
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 <span data-ttu-id="eea74-139">W przeciwieństwie do typów wartości, klasy zawsze mają co najmniej jeden poziom pośredni.</span><span class="sxs-lookup"><span data-stu-id="eea74-139">Unlike value types, classes always have at least one level of indirection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="eea74-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eea74-140">See also</span></span>

- [<span data-ttu-id="eea74-141">Wywołanie funkcji DLL</span><span class="sxs-lookup"><span data-stu-id="eea74-141">Calling a DLL Function</span></span>](calling-a-dll-function.md)
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- <xref:System.Runtime.InteropServices.FieldOffsetAttribute>
