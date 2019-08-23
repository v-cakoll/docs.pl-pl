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
ms.openlocfilehash: b1b05a5548beb7e7c1f0ec8e96b6e02350318ef9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921420"
---
# <a name="type-forwarding-in-the-common-language-runtime"></a><span data-ttu-id="b448a-102">Przekazywanie dalej typu w środowisku uruchomieniowym języka wspólnego</span><span class="sxs-lookup"><span data-stu-id="b448a-102">Type Forwarding in the Common Language Runtime</span></span>
<span data-ttu-id="b448a-103">Przekazywanie typu pozwala przenieść typ do innego zestawu bez konieczności ponownego kompilowania aplikacji, które używają oryginalnego zestawu.</span><span class="sxs-lookup"><span data-stu-id="b448a-103">Type forwarding allows you to move a type to another assembly without having to recompile applications that use the original assembly.</span></span>  
  
 <span data-ttu-id="b448a-104">Załóżmy na przykład, że aplikacja używa `Example` klasy w zestawie o nazwie. `Utility.dll`</span><span class="sxs-lookup"><span data-stu-id="b448a-104">For example, suppose an application uses the `Example` class in an assembly named `Utility.dll`.</span></span> <span data-ttu-id="b448a-105">Deweloperzy `Utility.dll` mogą zdecydować się na refaktoryzację zestawu, a w procesie może `Example` przenieść klasę do innego zestawu.</span><span class="sxs-lookup"><span data-stu-id="b448a-105">The developers of `Utility.dll` might decide to refactor the assembly, and in the process they might move the `Example` class to another assembly.</span></span> <span data-ttu-id="b448a-106">Jeśli stara `Utility.dll` wersja programu jest zastępowana przez nową wersję programu `Utility.dll` i jego zestaw towarzyszący, aplikacja, która używa `Example` klasy, kończy się niepowodzeniem, ponieważ `Example` nie może zlokalizować klasy w nowej `Utility.dll`wersji programu.</span><span class="sxs-lookup"><span data-stu-id="b448a-106">If the old version of `Utility.dll` is replaced by the new version of `Utility.dll` and its companion assembly, the application that uses the `Example` class fails because it cannot locate the `Example` class in the new version of `Utility.dll`.</span></span>  
  
 <span data-ttu-id="b448a-107">Deweloperzy `Utility.dll` mogą uniknąć tego przez przekazywanie żądań `Example` dla klasy przy użyciu <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="b448a-107">The developers of `Utility.dll` can avoid this by forwarding requests for the `Example` class, using the <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> attribute.</span></span> <span data-ttu-id="b448a-108">Jeśli atrybut został zastosowany do nowej wersji programu `Utility.dll`, żądania `Example` dla klasy są przekazywane do zestawu, który teraz zawiera klasę.</span><span class="sxs-lookup"><span data-stu-id="b448a-108">If the attribute has been applied to the new version of `Utility.dll`, requests for the `Example` class are forwarded to the assembly that now contains the class.</span></span> <span data-ttu-id="b448a-109">Istniejąca aplikacja nadal działa normalnie, bez ponownej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="b448a-109">The existing application continues to function normally, without recompilation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b448a-110">W .NET Framework w wersji 2,0 nie można przesłać dalej typów z zestawów utworzonych w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b448a-110">In the .NET Framework version 2.0, you cannot forward types from assemblies written in Visual Basic.</span></span> <span data-ttu-id="b448a-111">Jednak aplikacja zapisywana w Visual Basic może korzystać z przekazanych typów.</span><span class="sxs-lookup"><span data-stu-id="b448a-111">However, an application written in Visual Basic can consume forwarded types.</span></span> <span data-ttu-id="b448a-112">Oznacza to, że jeśli aplikacja używa zestawu zakodowanego w C# lub C++, a typ z tego zestawu jest przekazywany do innego zestawu, aplikacja Visual Basic może użyć przekazanego typu.</span><span class="sxs-lookup"><span data-stu-id="b448a-112">That is, if the application uses an assembly coded in C# or C++, and a type from that assembly is forwarded to another assembly, the Visual Basic application can use the forwarded type.</span></span>  
  
## <a name="forwarding-types"></a><span data-ttu-id="b448a-113">Typy przekazywania</span><span class="sxs-lookup"><span data-stu-id="b448a-113">Forwarding Types</span></span>  
 <span data-ttu-id="b448a-114">Aby przesłać dalej typ, należy wykonać cztery kroki:</span><span class="sxs-lookup"><span data-stu-id="b448a-114">There are four steps to forwarding a type:</span></span>  
  
1. <span data-ttu-id="b448a-115">Przenieś kod źródłowy dla typu z oryginalnego zestawu do zestawu docelowego.</span><span class="sxs-lookup"><span data-stu-id="b448a-115">Move the source code for the type from the original assembly to the destination assembly.</span></span>  
  
2. <span data-ttu-id="b448a-116">W zestawie, w którym używany jest typ, Dodaj <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> dla typu, który został przeniesiony.</span><span class="sxs-lookup"><span data-stu-id="b448a-116">In the assembly where the type used to be located, add a <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> for the type that was moved.</span></span> <span data-ttu-id="b448a-117">Poniższy kod przedstawia atrybut dla typu o nazwie `Example` , który został przeniesiony.</span><span class="sxs-lookup"><span data-stu-id="b448a-117">The following code shows the attribute for a type named `Example` that was moved.</span></span>  
  
    ```csharp  
    [assembly:TypeForwardedToAttribute(typeof(Example))]  
    ```  
  
    ```cpp  
    [assembly:TypeForwardedToAttribute(Example::typeid)]  
    ```  
  
3. <span data-ttu-id="b448a-118">Kompiluj zestaw, który zawiera teraz typ.</span><span class="sxs-lookup"><span data-stu-id="b448a-118">Compile the assembly that now contains the type.</span></span>  
  
4. <span data-ttu-id="b448a-119">Ponownie skompiluj zestaw, w którym znajduje się typ, z odwołaniem do zestawu, który zawiera teraz typ.</span><span class="sxs-lookup"><span data-stu-id="b448a-119">Recompile the assembly where the type used to be located, with a reference to the assembly that now contains the type.</span></span> <span data-ttu-id="b448a-120">Na przykład, Jeśli kompilujesz C# plik z wiersza polecenia, użyj opcji [/Reference (C# opcje kompilatora)](../../csharp/language-reference/compiler-options/reference-compiler-option.md) , aby określić zestaw, który zawiera typ.</span><span class="sxs-lookup"><span data-stu-id="b448a-120">For example, if you are compiling a C# file from the command line, use the [/reference (C# Compiler Options)](../../csharp/language-reference/compiler-options/reference-compiler-option.md) option to specify the assembly that contains the type.</span></span> <span data-ttu-id="b448a-121">W C++programie użyj dyrektywy [#using](/cpp/preprocessor/hash-using-directive-cpp) w pliku źródłowym, aby określić zestaw, który zawiera typ.</span><span class="sxs-lookup"><span data-stu-id="b448a-121">In C++, use the [#using](/cpp/preprocessor/hash-using-directive-cpp) directive in the source file to specify the assembly that contains the type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b448a-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b448a-122">See also</span></span>

- <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>
- [<span data-ttu-id="b448a-123">Przekazywanie dalej typu (C++/CLI)</span><span class="sxs-lookup"><span data-stu-id="b448a-123">Type Forwarding (C++/CLI)</span></span>](/cpp/windows/type-forwarding-cpp-cli)
- [<span data-ttu-id="b448a-124">#using — dyrektywa</span><span class="sxs-lookup"><span data-stu-id="b448a-124">#using Directive</span></span>](/cpp/preprocessor/hash-using-directive-cpp)
