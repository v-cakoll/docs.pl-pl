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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032759"
---
# <a name="specifying-an-entry-point"></a><span data-ttu-id="4fa9c-102">Określanie punktu wejścia</span><span class="sxs-lookup"><span data-stu-id="4fa9c-102">Specifying an Entry Point</span></span>
<span data-ttu-id="4fa9c-103">Punkt wejścia określa lokalizację funkcji w bibliotece DLL.</span><span class="sxs-lookup"><span data-stu-id="4fa9c-103">An entry point identifies the location of a function in a DLL.</span></span> <span data-ttu-id="4fa9c-104">W obrębie zarządzanego projektu, oryginalna nazwa lub porządkowy punkt wejścia docelowej funkcji określa tę funkcję wewnątrz międzyoperacyjnej granicy.</span><span class="sxs-lookup"><span data-stu-id="4fa9c-104">Within a managed project, the original name or ordinal entry point of a target function identifies that function across the interoperation boundary.</span></span> <span data-ttu-id="4fa9c-105">Co więcej, możesz zmapować punkt wejścia do innej nazwy, efektywnie zmieniając nazwę funkcji.</span><span class="sxs-lookup"><span data-stu-id="4fa9c-105">Further, you can map the entry point to a different name, effectively renaming the function.</span></span>  
  
 <span data-ttu-id="4fa9c-106">Poniższa lista zawiera możliwe powody zmiany nazwy funkcji DLL:</span><span class="sxs-lookup"><span data-stu-id="4fa9c-106">Following is a list of possible reasons to rename a DLL function:</span></span>  
  
- <span data-ttu-id="4fa9c-107">Aby uniknąć używania nazw funkcji API wrażliwych na wielkość liter</span><span class="sxs-lookup"><span data-stu-id="4fa9c-107">To avoid using case-sensitive API function names</span></span>  
  
- <span data-ttu-id="4fa9c-108">Aby postępować zgodnie z istniejącymi standardami nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="4fa9c-108">To comply with existing naming standards</span></span>  
  
- <span data-ttu-id="4fa9c-109">Aby pomieścić funkcje, które przyjmują różne typy danych (poprzez deklarację wielu wersji tej samej funkcji DLL)</span><span class="sxs-lookup"><span data-stu-id="4fa9c-109">To accommodate functions that take different data types (by declaring multiple versions of the same DLL function)</span></span>  
  
- <span data-ttu-id="4fa9c-110">Aby uprościć używanie API, które zawierają wersje ANSI i Unicode</span><span class="sxs-lookup"><span data-stu-id="4fa9c-110">To simplify using APIs that contain ANSI and Unicode versions</span></span>  
  
 <span data-ttu-id="4fa9c-111">Ten temat demonstruje, w jaki sposób zmienić nazwę funkcji DLL w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="4fa9c-111">This topic demonstrates how to rename a DLL function in managed code.</span></span>  
  
## <a name="renaming-a-function-in-visual-basic"></a><span data-ttu-id="4fa9c-112">Zmiana nazwy funkcji w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4fa9c-112">Renaming a Function in Visual Basic</span></span>  
 <span data-ttu-id="4fa9c-113">Visual Basic stosuje **funkcja** — słowo kluczowe w **Declare** instrukcję, aby ustawić <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> pola.</span><span class="sxs-lookup"><span data-stu-id="4fa9c-113">Visual Basic uses the **Function** keyword in the **Declare** statement to set the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> field.</span></span> <span data-ttu-id="4fa9c-114">Poniższy przykład pokazuje podstawową deklarację.</span><span class="sxs-lookup"><span data-stu-id="4fa9c-114">The following example shows a basic declaration.</span></span>  
  
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
  
 <span data-ttu-id="4fa9c-115">Możesz zastąpić **MessageBox** punktu wejścia przy użyciu **MsgBox** umieszczając **Alias** — słowo kluczowe w definicji, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="4fa9c-115">You can replace the **MessageBox** entry point with **MsgBox** by including the **Alias** keyword in your definition, as shown in the following example.</span></span> <span data-ttu-id="4fa9c-116">W obu przykładach **automatycznie** — słowo kluczowe eliminuje potrzebę określenia wersji zestawu znaków punktu wejścia.</span><span class="sxs-lookup"><span data-stu-id="4fa9c-116">In both examples the **Auto** keyword eliminates the need to specify the character-set version of the entry point.</span></span> <span data-ttu-id="4fa9c-117">Aby uzyskać więcej informacji o wybieraniu znak zestawu, zobacz [Określanie zestawu znaków](../../../docs/framework/interop/specifying-a-character-set.md).</span><span class="sxs-lookup"><span data-stu-id="4fa9c-117">For more information about selecting a character set, see [Specifying a Character Set](../../../docs/framework/interop/specifying-a-character-set.md).</span></span>  
  
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
  
## <a name="renaming-a-function-in-c-and-c"></a><span data-ttu-id="4fa9c-118">Zmiana nazwy funkcji w języku C# i C++</span><span class="sxs-lookup"><span data-stu-id="4fa9c-118">Renaming a Function in C# and C++</span></span>  
 <span data-ttu-id="4fa9c-119">Można użyć pola <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType>, aby określić funkcję DLL po nazwie lub liczbie porządkowej.</span><span class="sxs-lookup"><span data-stu-id="4fa9c-119">You can use the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> field to specify a DLL function by name or ordinal.</span></span> <span data-ttu-id="4fa9c-120">Jeśli nazwa funkcji w definicji metody jest taka sama jak punkt wejścia w DLL, nie trzeba jawnie identyfikować funkcji przy użyciu **punktu wejścia** pola.</span><span class="sxs-lookup"><span data-stu-id="4fa9c-120">If the name of the function in your method definition is the same as the entry point in the DLL, you do not have to explicitly identify the function with the **EntryPoint** field.</span></span> <span data-ttu-id="4fa9c-121">W innym wypadku, użyj jednego z poniższych form atrybutów, aby wskazać nazwę lub liczbę porządkową:</span><span class="sxs-lookup"><span data-stu-id="4fa9c-121">Otherwise, use one of the following attribute forms to indicate a name or ordinal:</span></span>  
  
```csharp
[DllImport("DllName", EntryPoint = "Functionname")]
[DllImport("DllName", EntryPoint = "#123")]
```
  
 <span data-ttu-id="4fa9c-122">Należy zauważyć, że liczba porządkowa musi być poprzedzona znakiem kratki (#).</span><span class="sxs-lookup"><span data-stu-id="4fa9c-122">Notice that you must prefix an ordinal with the pound sign (#).</span></span>  
  
 <span data-ttu-id="4fa9c-123">Poniższy przykład demonstruje sposób zamiany **MessageBoxA** z **MsgBox** w kodzie za pomocą **punktu wejścia** pola.</span><span class="sxs-lookup"><span data-stu-id="4fa9c-123">The following example demonstrates how to replace **MessageBoxA** with **MsgBox** in your code by using the **EntryPoint** field.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4fa9c-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4fa9c-124">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="4fa9c-125">Tworzenie prototypów w kodzie zarządzanym</span><span class="sxs-lookup"><span data-stu-id="4fa9c-125">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="4fa9c-126">Przykłady wywołań platformy</span><span class="sxs-lookup"><span data-stu-id="4fa9c-126">Platform Invoke Examples</span></span>](../../../docs/framework/interop/platform-invoke-examples.md)
- [<span data-ttu-id="4fa9c-127">Marshaling danych w wywołaniu platformy</span><span class="sxs-lookup"><span data-stu-id="4fa9c-127">Marshaling Data with Platform Invoke</span></span>](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)
