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
ms.openlocfilehash: 31bb28b5bda51fb1579021e47b8d5ec49adb644e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33388836"
---
# <a name="specifying-an-entry-point"></a><span data-ttu-id="b2ef1-102">Określanie punktu wejścia</span><span class="sxs-lookup"><span data-stu-id="b2ef1-102">Specifying an Entry Point</span></span>
<span data-ttu-id="b2ef1-103">Punkt wejścia określa lokalizację funkcji w bibliotece DLL.</span><span class="sxs-lookup"><span data-stu-id="b2ef1-103">An entry point identifies the location of a function in a DLL.</span></span> <span data-ttu-id="b2ef1-104">W obrębie zarządzanego projektu, oryginalna nazwa lub porządkowy punkt wejścia docelowej funkcji określa tę funkcję wewnątrz międzyoperacyjnej granicy.</span><span class="sxs-lookup"><span data-stu-id="b2ef1-104">Within a managed project, the original name or ordinal entry point of a target function identifies that function across the interoperation boundary.</span></span> <span data-ttu-id="b2ef1-105">Co więcej, możesz zmapować punkt wejścia do innej nazwy, efektywnie zmieniając nazwę funkcji.</span><span class="sxs-lookup"><span data-stu-id="b2ef1-105">Further, you can map the entry point to a different name, effectively renaming the function.</span></span>  
  
 <span data-ttu-id="b2ef1-106">Poniższa lista zawiera możliwe powody zmiany nazwy funkcji DLL:</span><span class="sxs-lookup"><span data-stu-id="b2ef1-106">Following is a list of possible reasons to rename a DLL function:</span></span>  
  
-   <span data-ttu-id="b2ef1-107">Aby uniknąć używania nazw funkcji API wrażliwych na wielkość liter</span><span class="sxs-lookup"><span data-stu-id="b2ef1-107">To avoid using case-sensitive API function names</span></span>  
  
-   <span data-ttu-id="b2ef1-108">Aby postępować zgodnie z istniejącymi standardami nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="b2ef1-108">To comply with existing naming standards</span></span>  
  
-   <span data-ttu-id="b2ef1-109">Aby pomieścić funkcje, które przyjmują różne typy danych (poprzez deklarację wielu wersji tej samej funkcji DLL)</span><span class="sxs-lookup"><span data-stu-id="b2ef1-109">To accommodate functions that take different data types (by declaring multiple versions of the same DLL function)</span></span>  
  
-   <span data-ttu-id="b2ef1-110">Aby uprościć używanie API, które zawierają wersje ANSI i Unicode</span><span class="sxs-lookup"><span data-stu-id="b2ef1-110">To simplify using APIs that contain ANSI and Unicode versions</span></span>  
  
 <span data-ttu-id="b2ef1-111">Ten temat demonstruje, w jaki sposób zmienić nazwę funkcji DLL w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="b2ef1-111">This topic demonstrates how to rename a DLL function in managed code.</span></span>  
  
## <a name="renaming-a-function-in-visual-basic"></a><span data-ttu-id="b2ef1-112">Zmiana nazwy funkcji w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b2ef1-112">Renaming a Function in Visual Basic</span></span>  
 <span data-ttu-id="b2ef1-113">Używa języka Visual Basic **funkcja** — słowo kluczowe w **Declare** instrukcja <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> pola.</span><span class="sxs-lookup"><span data-stu-id="b2ef1-113">Visual Basic uses the **Function** keyword in the **Declare** statement to set the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> field.</span></span> <span data-ttu-id="b2ef1-114">Poniższy przykład pokazuje podstawową deklarację.</span><span class="sxs-lookup"><span data-stu-id="b2ef1-114">The following example shows a basic declaration.</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
  
Public Class Win32  
    Declare Auto Function MessageBox Lib "user32.dll" _  
       (ByVal hWnd As Integer, ByVal txt As String,_  
       ByVal caption As String, ByVal Typ As Integer) As Integer  
End Class  
```  
  
 <span data-ttu-id="b2ef1-115">Można zastąpić **MessageBox** punkt wejścia z **MsgBox** przez dołączenie **Alias** — słowo kluczowe w definicji, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b2ef1-115">You can replace the **MessageBox** entry point with **MsgBox** by including the **Alias** keyword in your definition, as shown in the following example.</span></span> <span data-ttu-id="b2ef1-116">W obu przykładach **automatycznie** — słowo kluczowe eliminuje potrzebę Określ wersję zestawu znaków punktu wejścia.</span><span class="sxs-lookup"><span data-stu-id="b2ef1-116">In both examples the **Auto** keyword eliminates the need to specify the character-set version of the entry point.</span></span> <span data-ttu-id="b2ef1-117">Aby uzyskać więcej informacji o wybieraniu znak, zobacz [określający zestaw znaków](../../../docs/framework/interop/specifying-a-character-set.md).</span><span class="sxs-lookup"><span data-stu-id="b2ef1-117">For more information about selecting a character set, see [Specifying a Character Set](../../../docs/framework/interop/specifying-a-character-set.md).</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
  
Public Class Win32  
    Declare Auto Function MsgBox Lib "user32.dll" _  
       Alias "MessageBox" (ByVal hWnd As Integer, ByVal txt As String,_  
       ByVal caption As String, ByVal Typ As Integer) As Integer  
End Class  
```  
  
## <a name="renaming-a-function-in-c-and-c"></a><span data-ttu-id="b2ef1-118">Zmiana nazwy funkcji w języku C# i C++</span><span class="sxs-lookup"><span data-stu-id="b2ef1-118">Renaming a Function in C# and C++</span></span>  
 <span data-ttu-id="b2ef1-119">Można użyć pola <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType>, aby określić funkcję DLL po nazwie lub liczbie porządkowej.</span><span class="sxs-lookup"><span data-stu-id="b2ef1-119">You can use the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> field to specify a DLL function by name or ordinal.</span></span> <span data-ttu-id="b2ef1-120">Jeśli nazwa funkcji w definicji metody jest taka sama jak punkt wejścia w bibliotece DLL, nie trzeba jawnie zidentyfikowanie funkcji z **punktu wejścia** pola.</span><span class="sxs-lookup"><span data-stu-id="b2ef1-120">If the name of the function in your method definition is the same as the entry point in the DLL, you do not have to explicitly identify the function with the **EntryPoint** field.</span></span> <span data-ttu-id="b2ef1-121">W innym wypadku, użyj jednego z poniższych form atrybutów, aby wskazać nazwę lub liczbę porządkową:</span><span class="sxs-lookup"><span data-stu-id="b2ef1-121">Otherwise, use one of the following attribute forms to indicate a name or ordinal:</span></span>  
  
```  
[DllImport("dllname", EntryPoint="Functionname")]  
[DllImport("dllname", EntryPoint="#123")]  
```  
  
 <span data-ttu-id="b2ef1-122">Należy zauważyć, że liczba porządkowa musi być poprzedzona znakiem kratki (#).</span><span class="sxs-lookup"><span data-stu-id="b2ef1-122">Notice that you must prefix an ordinal with the pound sign (#).</span></span>  
  
 <span data-ttu-id="b2ef1-123">W poniższym przykładzie pokazano, jak zastąpić **MessageBoxA** z **MsgBox** w kodzie za pomocą **punktu wejścia** pola.</span><span class="sxs-lookup"><span data-stu-id="b2ef1-123">The following example demonstrates how to replace **MessageBoxA** with **MsgBox** in your code by using the **EntryPoint** field.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b2ef1-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b2ef1-124">See Also</span></span>  
 <xref:System.Runtime.InteropServices.DllImportAttribute>  
 [<span data-ttu-id="b2ef1-125">Tworzenie prototypów w kodzie zarządzanym</span><span class="sxs-lookup"><span data-stu-id="b2ef1-125">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)  
 [<span data-ttu-id="b2ef1-126">Przykłady wywołań platformy</span><span class="sxs-lookup"><span data-stu-id="b2ef1-126">Platform Invoke Examples</span></span>](../../../docs/framework/interop/platform-invoke-examples.md)  
 [<span data-ttu-id="b2ef1-127">Marshaling danych w wywołaniu platformy</span><span class="sxs-lookup"><span data-stu-id="b2ef1-127">Marshaling Data with Platform Invoke</span></span>](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)
