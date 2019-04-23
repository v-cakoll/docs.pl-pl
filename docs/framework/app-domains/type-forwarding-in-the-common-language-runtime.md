---
title: Przekazywanie dalej typu w środowisku uruchomieniowym języka wspólnego
ms.date: 03/30/2017
dev_langs:
- csharp
- cpp
helpviewer_keywords:
- assemblies [.NET Framework], type forwarding
- type forwarding
ms.assetid: 51f8ffa3-c253-4201-a3d3-c4fad85ae097
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5e378eb36e633575d5afa886e886aed302cbdab9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59310988"
---
# <a name="type-forwarding-in-the-common-language-runtime"></a><span data-ttu-id="5fcc2-102">Przekazywanie dalej typu w środowisku uruchomieniowym języka wspólnego</span><span class="sxs-lookup"><span data-stu-id="5fcc2-102">Type Forwarding in the Common Language Runtime</span></span>
<span data-ttu-id="5fcc2-103">Przekazywanie dalej typu umożliwia przeniesienie typu do innego zestawu bez konieczności ponownego kompilowania aplikacji, które używają oryginalnego zestawu.</span><span class="sxs-lookup"><span data-stu-id="5fcc2-103">Type forwarding allows you to move a type to another assembly without having to recompile applications that use the original assembly.</span></span>  
  
 <span data-ttu-id="5fcc2-104">Załóżmy, że aplikacja używa `Example` klasy w zestawie o nazwie `Utility.dll`.</span><span class="sxs-lookup"><span data-stu-id="5fcc2-104">For example, suppose an application uses the `Example` class in an assembly named `Utility.dll`.</span></span> <span data-ttu-id="5fcc2-105">Deweloperzy `Utility.dll` może podjąć decyzję o Refaktoryzuj zestawu, a w procesie może przenieść `Example` klasy do innego zestawu.</span><span class="sxs-lookup"><span data-stu-id="5fcc2-105">The developers of `Utility.dll` might decide to refactor the assembly, and in the process they might move the `Example` class to another assembly.</span></span> <span data-ttu-id="5fcc2-106">Jeśli poprzednią wersję `Utility.dll` zostaje zastąpiona przez nową wersję `Utility.dll` i jej zestaw pomocnika, aplikacji używającej `Example` klasy nie powiedzie się, ponieważ nie można zlokalizować `Example` klasy w nowej wersji zestawu `Utility.dll`.</span><span class="sxs-lookup"><span data-stu-id="5fcc2-106">If the old version of `Utility.dll` is replaced by the new version of `Utility.dll` and its companion assembly, the application that uses the `Example` class fails because it cannot locate the `Example` class in the new version of `Utility.dll`.</span></span>  
  
 <span data-ttu-id="5fcc2-107">Deweloperzy `Utility.dll` można tego uniknąć, przekazuje żądania do `Example` klasy przy użyciu <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="5fcc2-107">The developers of `Utility.dll` can avoid this by forwarding requests for the `Example` class, using the <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> attribute.</span></span> <span data-ttu-id="5fcc2-108">Jeśli ten atrybut zostały doliczone do nowej wersji `Utility.dll`, żądań dla `Example` klasy są przekazywane do zestawu, który teraz zawiera klasę.</span><span class="sxs-lookup"><span data-stu-id="5fcc2-108">If the attribute has been applied to the new version of `Utility.dll`, requests for the `Example` class are forwarded to the assembly that now contains the class.</span></span> <span data-ttu-id="5fcc2-109">Istniejącej aplikacji działa normalnie, bez ponownej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="5fcc2-109">The existing application continues to function normally, without recompilation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5fcc2-110">.NET Framework w wersji 2.0 nie mogą przesyłać dalej typów w zestawach napisanych w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5fcc2-110">In the .NET Framework version 2.0, you cannot forward types from assemblies written in Visual Basic.</span></span> <span data-ttu-id="5fcc2-111">Jednak aplikacji napisanych w języku Visual Basic mogą wykorzystywać typy przekazane.</span><span class="sxs-lookup"><span data-stu-id="5fcc2-111">However, an application written in Visual Basic can consume forwarded types.</span></span> <span data-ttu-id="5fcc2-112">Oznacza to jeśli aplikacja używa zestawu kodowane w języku C# lub C++ i typu z tego zestawu jest przekazywany do innego zestawu, aplikacji Visual Basic można użyć typ przesłany.</span><span class="sxs-lookup"><span data-stu-id="5fcc2-112">That is, if the application uses an assembly coded in C# or C++, and a type from that assembly is forwarded to another assembly, the Visual Basic application can use the forwarded type.</span></span>  
  
## <a name="forwarding-types"></a><span data-ttu-id="5fcc2-113">Typy przekazywania</span><span class="sxs-lookup"><span data-stu-id="5fcc2-113">Forwarding Types</span></span>  
 <span data-ttu-id="5fcc2-114">Istnieją cztery kroki przekazywania typu:</span><span class="sxs-lookup"><span data-stu-id="5fcc2-114">There are four steps to forwarding a type:</span></span>  
  
1. <span data-ttu-id="5fcc2-115">Przenieść kod źródłowy dla typu z oryginalnego zestawu do zestawu docelowego.</span><span class="sxs-lookup"><span data-stu-id="5fcc2-115">Move the source code for the type from the original assembly to the destination assembly.</span></span>  
  
2. <span data-ttu-id="5fcc2-116">W zestawie, w którym typ używany do można znaleźć, Dodaj <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> dla typu, który został przeniesiony.</span><span class="sxs-lookup"><span data-stu-id="5fcc2-116">In the assembly where the type used to be located, add a <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> for the type that was moved.</span></span> <span data-ttu-id="5fcc2-117">Poniższy kod przedstawia atrybut typu o nazwie `Example` , została przeniesiona.</span><span class="sxs-lookup"><span data-stu-id="5fcc2-117">The following code shows the attribute for a type named `Example` that was moved.</span></span>  
  
    ```csharp  
    [assembly:TypeForwardedToAttribute(typeof(Example))]  
    ```  
  
    ```cpp  
    [assembly:TypeForwardedToAttribute(Example::typeid)]  
    ```  
  
3. <span data-ttu-id="5fcc2-118">Skompiluj zestaw, który zawiera teraz typu.</span><span class="sxs-lookup"><span data-stu-id="5fcc2-118">Compile the assembly that now contains the type.</span></span>  
  
4. <span data-ttu-id="5fcc2-119">Zestaw, gdzie typ używany w zlokalizowanym z odwołania do zestawu, który teraz zawiera typ należy ponownie skompilować.</span><span class="sxs-lookup"><span data-stu-id="5fcc2-119">Recompile the assembly where the type used to be located, with a reference to the assembly that now contains the type.</span></span> <span data-ttu-id="5fcc2-120">Na przykład, jeśli kompilujesz z pliku C# z wiersza polecenia, użyj [/Reference (opcje kompilatora C#)](~/docs/csharp/language-reference/compiler-options/reference-compiler-option.md) opcję, aby określić zestaw, który zawiera typu.</span><span class="sxs-lookup"><span data-stu-id="5fcc2-120">For example, if you are compiling a C# file from the command line, use the [/reference (C# Compiler Options)](~/docs/csharp/language-reference/compiler-options/reference-compiler-option.md) option to specify the assembly that contains the type.</span></span> <span data-ttu-id="5fcc2-121">W języku C++, użyj [#using](/cpp/preprocessor/hash-using-directive-cpp) dyrektywy w pliku źródłowym, aby określić zestaw, który zawiera typu.</span><span class="sxs-lookup"><span data-stu-id="5fcc2-121">In C++, use the [#using](/cpp/preprocessor/hash-using-directive-cpp) directive in the source file to specify the assembly that contains the type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fcc2-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5fcc2-122">See also</span></span>

- <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>
- [<span data-ttu-id="5fcc2-123">Przekazywanie dalej typu (C++/CLI)</span><span class="sxs-lookup"><span data-stu-id="5fcc2-123">Type Forwarding (C++/CLI)</span></span>](/cpp/windows/type-forwarding-cpp-cli)
- [<span data-ttu-id="5fcc2-124">#using — dyrektywa</span><span class="sxs-lookup"><span data-stu-id="5fcc2-124">#using Directive</span></span>](/cpp/preprocessor/hash-using-directive-cpp)
