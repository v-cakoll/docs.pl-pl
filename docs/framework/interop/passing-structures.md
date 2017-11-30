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
ms.openlocfilehash: ab9002d6e86b91f0ed21dae41f82af31f04291c5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="passing-structures"></a><span data-ttu-id="9d932-102">Przekazywanie struktur</span><span class="sxs-lookup"><span data-stu-id="9d932-102">Passing Structures</span></span>
<span data-ttu-id="9d932-103">Wiele funkcji niezarządzanej oczekiwać, że można przekazać jako parametru funkcji, członków struktur (Typy definiowane przez użytkownika w języku Visual Basic) lub klas zdefiniowanych w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="9d932-103">Many unmanaged functions expect you to pass, as a parameter to the function, members of structures (user-defined types in Visual Basic) or members of classes that are defined in managed code.</span></span> <span data-ttu-id="9d932-104">Podczas wywołania przekazywanie struktury lub klasy do kodu niezarządzanego, przy użyciu platformy, należy podać dodatkowe informacje, aby zachować oryginalne układ i wyrównania.</span><span class="sxs-lookup"><span data-stu-id="9d932-104">When passing structures or classes to unmanaged code using platform invoke, you must provide additional information to preserve the original layout and alignment.</span></span> <span data-ttu-id="9d932-105">W tym temacie przedstawiono <xref:System.Runtime.InteropServices.StructLayoutAttribute> atrybut, który służy do definiowania typów sformatowany.</span><span class="sxs-lookup"><span data-stu-id="9d932-105">This topic introduces the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute, which you use to define formatted types.</span></span> <span data-ttu-id="9d932-106">Zarządzane, struktur i klas, możesz wybrać z zachowaniami przewidywalną układu dostarczanych przez **LayoutKind** wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="9d932-106">For managed structures and classes, you can select from several predictable layout behaviors supplied by the **LayoutKind** enumeration.</span></span>  
  
 <span data-ttu-id="9d932-107">Centralnej do koncepcji przedstawionych w tym temacie jest istotną różnicą między typami struktury i klasy.</span><span class="sxs-lookup"><span data-stu-id="9d932-107">Central to the concepts presented in this topic is an important difference between structure and class types.</span></span> <span data-ttu-id="9d932-108">Typy wartości są struktur i klas typów referencyjnych — klas zawsze podawać co najmniej jeden poziom pośredni pamięci (wskaźnik do wartości).</span><span class="sxs-lookup"><span data-stu-id="9d932-108">Structures are value types and classes are reference types — classes always provide at least one level of memory indirection (a pointer to a value).</span></span> <span data-ttu-id="9d932-109">Ta różnica jest ważne, ponieważ funkcje niezarządzane często wymaga pośredni, pokazane podpisów w pierwszej kolumnie tabeli.</span><span class="sxs-lookup"><span data-stu-id="9d932-109">This difference is important because unmanaged functions often demand indirection, as shown by the signatures in the first column of the following table.</span></span> <span data-ttu-id="9d932-110">Zarządzane struktury i klasy deklaracje w pozostałych kolumnach Pokaż stopień, do którego można dostosować poziom pośredni w Twojej deklaracji. Deklaracje są udostępniane dla języka Visual Basic i Visual C#.</span><span class="sxs-lookup"><span data-stu-id="9d932-110">The managed structure and class declarations in the remaining columns show the degree to which you can adjust the level of indirection in your declaration.Declarations are provided for both Visual Basic and Visual C#.</span></span>  
  
|<span data-ttu-id="9d932-111">Niezarządzanego podpisu</span><span class="sxs-lookup"><span data-stu-id="9d932-111">Unmanaged signature</span></span>|<span data-ttu-id="9d932-112">Deklaracja zarządzanego:</span><span class="sxs-lookup"><span data-stu-id="9d932-112">Managed declaration:</span></span> <br /><span data-ttu-id="9d932-113">nie pośredni</span><span class="sxs-lookup"><span data-stu-id="9d932-113">no indirection</span></span><br />`Structure MyType`<br />`struct MyType;`|<span data-ttu-id="9d932-114">Deklaracja zarządzanego:</span><span class="sxs-lookup"><span data-stu-id="9d932-114">Managed declaration:</span></span> <br /><span data-ttu-id="9d932-115">jeden poziom pośredni</span><span class="sxs-lookup"><span data-stu-id="9d932-115">one level of indirection</span></span><br />`Class MyType`<br />`class MyType;`|  
|-------------------------|---------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|  
|`DoWork(MyType x);`<br /><br /> <span data-ttu-id="9d932-116">Wymagania poziomach pośredników od zera.</span><span class="sxs-lookup"><span data-stu-id="9d932-116">Demands zero levels of indirection.</span></span>|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> <span data-ttu-id="9d932-117">Dodaje zero poziomach operatorów pośrednich.</span><span class="sxs-lookup"><span data-stu-id="9d932-117">Adds zero levels of indirection.</span></span>|<span data-ttu-id="9d932-118">Nie jest możliwa, ponieważ istnieje już jeden poziom pośredni.</span><span class="sxs-lookup"><span data-stu-id="9d932-118">Not possible because there is already one level of indirection.</span></span>|  
|`DoWork(MyType* x);`<br /><br /> <span data-ttu-id="9d932-119">Wymaga pośredników o jeden poziom.</span><span class="sxs-lookup"><span data-stu-id="9d932-119">Demands one level of indirection.</span></span>|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> <span data-ttu-id="9d932-120">Dodaje pośredników o jeden poziom.</span><span class="sxs-lookup"><span data-stu-id="9d932-120">Adds one level of indirection.</span></span>|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> <span data-ttu-id="9d932-121">Dodaje zero poziomach operatorów pośrednich.</span><span class="sxs-lookup"><span data-stu-id="9d932-121">Adds zero levels of indirection.</span></span>|  
|`DoWork(MyType** x);`<br /><br /> <span data-ttu-id="9d932-122">Wymaga dwóch poziomach operatorów pośrednich.</span><span class="sxs-lookup"><span data-stu-id="9d932-122">Demands two levels of indirection.</span></span>|<span data-ttu-id="9d932-123">Nie jest możliwe ponieważ **ByRef** **ByRef** lub `ref` `ref` nie można użyć.</span><span class="sxs-lookup"><span data-stu-id="9d932-123">Not possible because **ByRef** **ByRef** or `ref` `ref` cannot be used.</span></span>|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> <span data-ttu-id="9d932-124">Dodaje pośredników o jeden poziom.</span><span class="sxs-lookup"><span data-stu-id="9d932-124">Adds one level of indirection.</span></span>|  
  
 <span data-ttu-id="9d932-125">W tabeli opisano następujące wskazówki dla deklaracji wywołania platformy:</span><span class="sxs-lookup"><span data-stu-id="9d932-125">The table describes the following guidelines for platform invoke declarations:</span></span>  
  
-   <span data-ttu-id="9d932-126">Struktura przekazany przez wartość, gdy pośredni nie żąda niezarządzanej funkcji jest używana.</span><span class="sxs-lookup"><span data-stu-id="9d932-126">Use a structure passed by value when the unmanaged function demands no indirection.</span></span>  
  
-   <span data-ttu-id="9d932-127">Użyj struktury przekazywana przez odwołanie, lub klasy przekazany przez wartość, gdy jeden poziom pośredni żąda niezarządzanej funkcji.</span><span class="sxs-lookup"><span data-stu-id="9d932-127">Use either a structure passed by reference or a class passed by value when the unmanaged function demands one level of indirection.</span></span>  
  
-   <span data-ttu-id="9d932-128">Używanie klasy przekazywany przez odwołanie, gdy dwa poziomy pośredni żąda niezarządzanej funkcji.</span><span class="sxs-lookup"><span data-stu-id="9d932-128">Use a class passed by reference when the unmanaged function demands two levels of indirection.</span></span>  
  
## <a name="declaring-and-passing-structures"></a><span data-ttu-id="9d932-129">Deklarowanie i przekazywanie struktur</span><span class="sxs-lookup"><span data-stu-id="9d932-129">Declaring and Passing Structures</span></span>  
 <span data-ttu-id="9d932-130">Poniższy przykład przedstawia sposób definiowania `Point` i `Rect` struktury w kodzie zarządzanym i przekazywania typów jako parametr do **PtInRect** funkcji w pliku User32.dll.</span><span class="sxs-lookup"><span data-stu-id="9d932-130">The following example shows how to define the `Point` and `Rect` structures in managed code, and pass the types as parameter to the **PtInRect** function in the User32.dll file.</span></span> <span data-ttu-id="9d932-131">**PtInRect** ma następujące niezarządzanego podpisu:</span><span class="sxs-lookup"><span data-stu-id="9d932-131">**PtInRect** has the following unmanaged signature:</span></span>  
  
```  
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 <span data-ttu-id="9d932-132">Należy zauważyć, że trzeba przekazać struktura Rect przez odwołanie, ponieważ funkcja oczekuje wskaźnika do typu Rect.</span><span class="sxs-lookup"><span data-stu-id="9d932-132">Notice that you must pass the Rect structure by reference, since the function expects a pointer to a RECT type.</span></span>  
  
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
  
## <a name="declaring-and-passing-classes"></a><span data-ttu-id="9d932-133">Deklarowanie i przekazywanie klas</span><span class="sxs-lookup"><span data-stu-id="9d932-133">Declaring and Passing Classes</span></span>  
 <span data-ttu-id="9d932-134">Elementy członkowskie klasy można przekazać do funkcji niezarządzanej DLL, tak długo, jak klasa ma układ stałego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="9d932-134">You can pass members of a class to an unmanaged DLL function, as long as the class has a fixed member layout.</span></span> <span data-ttu-id="9d932-135">W poniższym przykładzie pokazano sposób przekazywania członkami `MySystemTime` klasy, które są zdefiniowane w kolejności sekwencyjnej, do **GetSystemTime** w pliku User32.dll.</span><span class="sxs-lookup"><span data-stu-id="9d932-135">The following example demonstrates how to pass members of the `MySystemTime` class, which are defined in sequential order, to the **GetSystemTime** in the User32.dll file.</span></span> <span data-ttu-id="9d932-136">**GetSystemTime** ma następujące niezarządzanego podpisu:</span><span class="sxs-lookup"><span data-stu-id="9d932-136">**GetSystemTime** has the following unmanaged signature:</span></span>  
  
```  
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 <span data-ttu-id="9d932-137">W przeciwieństwie do typów wartości klasy zawsze mają co najmniej jeden poziom pośredni.</span><span class="sxs-lookup"><span data-stu-id="9d932-137">Unlike value types, classes always have at least one level of indirection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9d932-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9d932-138">See Also</span></span>  
 [<span data-ttu-id="9d932-139">Wywoływanie funkcji DLL</span><span class="sxs-lookup"><span data-stu-id="9d932-139">Calling a DLL Function</span></span>](../../../docs/framework/interop/calling-a-dll-function.md)  
 <xref:System.Runtime.InteropServices.StructLayoutAttribute>  
 <xref:System.Runtime.InteropServices.StructLayoutAttribute>  
 <xref:System.Runtime.InteropServices.FieldOffsetAttribute>
