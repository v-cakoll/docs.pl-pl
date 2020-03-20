---
title: Określanie punktu wejścia
ms.date: 03/30/2017
helpviewer_keywords:
- EntryPoint field
- platform invoke, attribute fields
- attribute fields in platform invoke, EntryPoint
ms.assetid: d1247f08-0965-416a-b978-e0b50652dfe3
ms.openlocfilehash: c5f8f735dd3e8c359f88044a532c29303237acc8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181312"
---
# <a name="specifying-an-entry-point"></a><span data-ttu-id="86ca7-102">Określanie punktu wejścia</span><span class="sxs-lookup"><span data-stu-id="86ca7-102">Specifying an Entry Point</span></span>

<span data-ttu-id="86ca7-103">Punkt wejścia określa lokalizację funkcji w bibliotece DLL.</span><span class="sxs-lookup"><span data-stu-id="86ca7-103">An entry point identifies the location of a function in a DLL.</span></span> <span data-ttu-id="86ca7-104">W obrębie zarządzanego projektu, oryginalna nazwa lub porządkowy punkt wejścia docelowej funkcji określa tę funkcję wewnątrz międzyoperacyjnej granicy.</span><span class="sxs-lookup"><span data-stu-id="86ca7-104">Within a managed project, the original name or ordinal entry point of a target function identifies that function across the interoperation boundary.</span></span> <span data-ttu-id="86ca7-105">Co więcej, możesz zmapować punkt wejścia do innej nazwy, efektywnie zmieniając nazwę funkcji.</span><span class="sxs-lookup"><span data-stu-id="86ca7-105">Further, you can map the entry point to a different name, effectively renaming the function.</span></span>  
  
 <span data-ttu-id="86ca7-106">Poniżej znajduje się lista możliwych przyczyn zmiany nazwy funkcji DLL:</span><span class="sxs-lookup"><span data-stu-id="86ca7-106">The following is a list of possible reasons to rename a DLL function:</span></span>  
  
- <span data-ttu-id="86ca7-107">Aby uniknąć używania nazw funkcji API wrażliwych na wielkość liter</span><span class="sxs-lookup"><span data-stu-id="86ca7-107">To avoid using case-sensitive API function names</span></span>  
  
- <span data-ttu-id="86ca7-108">Aby postępować zgodnie z istniejącymi standardami nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="86ca7-108">To comply with existing naming standards</span></span>  
  
- <span data-ttu-id="86ca7-109">Aby pomieścić funkcje, które przyjmują różne typy danych (poprzez deklarację wielu wersji tej samej funkcji DLL)</span><span class="sxs-lookup"><span data-stu-id="86ca7-109">To accommodate functions that take different data types (by declaring multiple versions of the same DLL function)</span></span>  
  
- <span data-ttu-id="86ca7-110">Aby uprościć używanie API, które zawierają wersje ANSI i Unicode</span><span class="sxs-lookup"><span data-stu-id="86ca7-110">To simplify using APIs that contain ANSI and Unicode versions</span></span>  
  
 <span data-ttu-id="86ca7-111">Ten temat demonstruje, w jaki sposób zmienić nazwę funkcji DLL w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="86ca7-111">This topic demonstrates how to rename a DLL function in managed code.</span></span>  
  
## <a name="renaming-a-function-in-visual-basic"></a><span data-ttu-id="86ca7-112">Zmiana nazwy funkcji w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="86ca7-112">Renaming a Function in Visual Basic</span></span>  

<span data-ttu-id="86ca7-113">Visual Basic używa **słowa kluczowego Function** w **Declare** instrukcji, aby ustawić <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> pole.</span><span class="sxs-lookup"><span data-stu-id="86ca7-113">Visual Basic uses the **Function** keyword in the **Declare** statement to set the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> field.</span></span> <span data-ttu-id="86ca7-114">Poniższy przykład pokazuje podstawową deklarację.</span><span class="sxs-lookup"><span data-stu-id="86ca7-114">The following example shows a basic declaration.</span></span>  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Function MessageBox Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
<span data-ttu-id="86ca7-115">Punkt wejścia **MessageBox** można zastąpić **msgbox,** dołączając słowo kluczowe **Alias** do definicji, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="86ca7-115">You can replace the **MessageBox** entry point with **MsgBox** by including the **Alias** keyword in your definition, as shown in the following example.</span></span> <span data-ttu-id="86ca7-116">W obu przykładach **auto** słowo kluczowe eliminuje konieczność określenia wersji zestawu znaków punktu wejścia.</span><span class="sxs-lookup"><span data-stu-id="86ca7-116">In both examples the **Auto** keyword eliminates the need to specify the character-set version of the entry point.</span></span> <span data-ttu-id="86ca7-117">Aby uzyskać więcej informacji na temat wybierania zestawu znaków, zobacz [Określanie zestawu znaków](specifying-a-character-set.md).</span><span class="sxs-lookup"><span data-stu-id="86ca7-117">For more information about selecting a character set, see [Specifying a Character Set](specifying-a-character-set.md).</span></span>  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Function MsgBox _
        Lib "user32.dll" Alias "MessageBox" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
## <a name="renaming-a-function-in-c-and-c"></a><span data-ttu-id="86ca7-118">Zmiana nazwy funkcji w języku C# i C++</span><span class="sxs-lookup"><span data-stu-id="86ca7-118">Renaming a Function in C# and C++</span></span>  
 <span data-ttu-id="86ca7-119">Można użyć pola <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType>, aby określić funkcję DLL po nazwie lub liczbie porządkowej.</span><span class="sxs-lookup"><span data-stu-id="86ca7-119">You can use the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> field to specify a DLL function by name or ordinal.</span></span> <span data-ttu-id="86ca7-120">Jeśli nazwa funkcji w definicji metody jest taka sama jak punkt wejścia w dll, nie trzeba jawnie zidentyfikować funkcję z **entrypoint** pola.</span><span class="sxs-lookup"><span data-stu-id="86ca7-120">If the name of the function in your method definition is the same as the entry point in the DLL, you do not have to explicitly identify the function with the **EntryPoint** field.</span></span> <span data-ttu-id="86ca7-121">W innym wypadku, użyj jednego z poniższych form atrybutów, aby wskazać nazwę lub liczbę porządkową:</span><span class="sxs-lookup"><span data-stu-id="86ca7-121">Otherwise, use one of the following attribute forms to indicate a name or ordinal:</span></span>  
  
```csharp
[DllImport("DllName", EntryPoint = "Functionname")]
[DllImport("DllName", EntryPoint = "#123")]
```
  
 <span data-ttu-id="86ca7-122">Należy zauważyć, że liczba porządkowa musi być poprzedzona znakiem kratki (#).</span><span class="sxs-lookup"><span data-stu-id="86ca7-122">Notice that you must prefix an ordinal with the pound sign (#).</span></span>  
  
 <span data-ttu-id="86ca7-123">W poniższym przykładzie pokazano, jak zastąpić **MessageBoxA** **msgbox** w kodzie przy użyciu **entrypoint** pola.</span><span class="sxs-lookup"><span data-stu-id="86ca7-123">The following example demonstrates how to replace **MessageBoxA** with **MsgBox** in your code by using the **EntryPoint** field.</span></span>  
  
```csharp
using System;
using System.Runtime.InteropServices;

internal static class NativeMethods
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
  
## <a name="see-also"></a><span data-ttu-id="86ca7-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="86ca7-124">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="86ca7-125">Tworzenie prototypów w kodzie zarządzanym</span><span class="sxs-lookup"><span data-stu-id="86ca7-125">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="86ca7-126">Przykłady wywołań platformy</span><span class="sxs-lookup"><span data-stu-id="86ca7-126">Platform Invoke Examples</span></span>](platform-invoke-examples.md)
- [<span data-ttu-id="86ca7-127">Organizowanie danych w wywołaniu platformy</span><span class="sxs-lookup"><span data-stu-id="86ca7-127">Marshaling Data with Platform Invoke</span></span>](marshaling-data-with-platform-invoke.md)
