---
title: Przekazywanie dalej typu w środowisku uruchomieniowym języka wspólnego
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], type forwarding
- type forwarding
ms.assetid: 51f8ffa3-c253-4201-a3d3-c4fad85ae097
author: rpetrusha
ms.author: ronpet
dev_langs:
- csharp
- cpp
ms.openlocfilehash: 1b00eea3c28a160a5afc41d910144033d2339070
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524463"
---
# <a name="type-forwarding-in-the-common-language-runtime"></a><span data-ttu-id="e6649-102">Przekazywanie dalej typu w środowisku uruchomieniowym języka wspólnego</span><span class="sxs-lookup"><span data-stu-id="e6649-102">Type forwarding in the common language runtime</span></span>
<span data-ttu-id="e6649-103">Przekazywanie typu pozwala przenieść typ do innego zestawu bez konieczności ponownego kompilowania aplikacji, które używają oryginalnego zestawu.</span><span class="sxs-lookup"><span data-stu-id="e6649-103">Type forwarding allows you to move a type to another assembly without having to recompile applications that use the original assembly.</span></span>  
  
 <span data-ttu-id="e6649-104">Załóżmy na przykład, że aplikacja używa klasy `Example` w zestawie o nazwie *Utility. dll*.</span><span class="sxs-lookup"><span data-stu-id="e6649-104">For example, suppose an application uses the `Example` class in an assembly named *Utility.dll*.</span></span> <span data-ttu-id="e6649-105">Deweloperzy *Narzędzia Utility. dll* mogą zdecydować się na refaktoryzację zestawu, a w procesie może przenieść klasę `Example` do innego zestawu.</span><span class="sxs-lookup"><span data-stu-id="e6649-105">The developers of *Utility.dll* might decide to refactor the assembly, and in the process they might move the `Example` class to another assembly.</span></span> <span data-ttu-id="e6649-106">Jeśli stara wersja *Narzędzia Utility. dll* jest zastępowana przez nową wersję *pliku Utility. dll* i jego zestawu towarzyszącego, aplikacja, która używa klasy `Example`, kończy się niepowodzeniem, ponieważ nie może zlokalizować klasy `Example` w nowej wersji *Narzędzia. dll* .</span><span class="sxs-lookup"><span data-stu-id="e6649-106">If the old version of *Utility.dll* is replaced by the new version of *Utility.dll* and its companion assembly, the application that uses the `Example` class fails because it cannot locate the `Example` class in the new version of *Utility.dll*.</span></span>  
  
 <span data-ttu-id="e6649-107">Deweloperzy *narzędzi. dll* mogą uniknąć tego przez przekazywanie żądań dla klasy `Example` przy użyciu atrybutu <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>.</span><span class="sxs-lookup"><span data-stu-id="e6649-107">The developers of *Utility.dll* can avoid this by forwarding requests for the `Example` class, using the <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> attribute.</span></span> <span data-ttu-id="e6649-108">Jeśli atrybut został zastosowany do nowej wersji *pliku Utility. dll*, żądania dla klasy `Example` są przekazywane do zestawu, który zawiera teraz klasę.</span><span class="sxs-lookup"><span data-stu-id="e6649-108">If the attribute has been applied to the new version of *Utility.dll*, requests for the `Example` class are forwarded to the assembly that now contains the class.</span></span> <span data-ttu-id="e6649-109">Istniejąca aplikacja nadal działa normalnie, bez ponownej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e6649-109">The existing application continues to function normally, without recompilation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e6649-110">W .NET Framework w wersji 2,0 nie można przesłać dalej typów z zestawów utworzonych w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e6649-110">In the .NET Framework version 2.0, you cannot forward types from assemblies written in Visual Basic.</span></span> <span data-ttu-id="e6649-111">Jednak aplikacja zapisywana w Visual Basic może korzystać z przekazanych typów.</span><span class="sxs-lookup"><span data-stu-id="e6649-111">However, an application written in Visual Basic can consume forwarded types.</span></span> <span data-ttu-id="e6649-112">Oznacza to, że jeśli aplikacja używa zestawu zakodowanego w C# lub C++, a typ z tego zestawu jest przekazywany do innego zestawu, aplikacja Visual Basic może użyć przekazanego typu.</span><span class="sxs-lookup"><span data-stu-id="e6649-112">That is, if the application uses an assembly coded in C# or C++, and a type from that assembly is forwarded to another assembly, the Visual Basic application can use the forwarded type.</span></span>  
  
## <a name="forward-types"></a><span data-ttu-id="e6649-113">Typy do przodu</span><span class="sxs-lookup"><span data-stu-id="e6649-113">Forward types</span></span>  
 <span data-ttu-id="e6649-114">Aby przesłać dalej typ, należy wykonać cztery kroki:</span><span class="sxs-lookup"><span data-stu-id="e6649-114">There are four steps to forwarding a type:</span></span>  
  
1. <span data-ttu-id="e6649-115">Przenieś kod źródłowy dla typu z oryginalnego zestawu do zestawu docelowego.</span><span class="sxs-lookup"><span data-stu-id="e6649-115">Move the source code for the type from the original assembly to the destination assembly.</span></span>  
   
2. <span data-ttu-id="e6649-116">W zestawie, w którym używany jest typ, Dodaj <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> dla typu, który został przeniesiony.</span><span class="sxs-lookup"><span data-stu-id="e6649-116">In the assembly where the type used to be located, add a <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> for the type that was moved.</span></span> <span data-ttu-id="e6649-117">Poniższy kod przedstawia atrybut dla typu o nazwie `Example`, który został przeniesiony.</span><span class="sxs-lookup"><span data-stu-id="e6649-117">The following code shows the attribute for a type named `Example` that was moved.</span></span>  
   
   ```cpp  
    [assembly:TypeForwardedToAttribute(Example::typeid)]  
   ```
   
   ```csharp  
    [assembly:TypeForwardedToAttribute(typeof(Example))]  
   ```  
   
3. <span data-ttu-id="e6649-118">Kompiluj zestaw, który zawiera teraz typ.</span><span class="sxs-lookup"><span data-stu-id="e6649-118">Compile the assembly that now contains the type.</span></span>  
   
4. <span data-ttu-id="e6649-119">Ponownie skompiluj zestaw, w którym znajduje się typ, z odwołaniem do zestawu, który zawiera teraz typ.</span><span class="sxs-lookup"><span data-stu-id="e6649-119">Recompile the assembly where the type used to be located, with a reference to the assembly that now contains the type.</span></span> <span data-ttu-id="e6649-120">Na przykład, Jeśli kompilujesz C# plik z wiersza polecenia, użyj opcji [-Reference (C# opcje kompilatora)](../../csharp/language-reference/compiler-options/reference-compiler-option.md) , aby określić zestaw, który zawiera typ.</span><span class="sxs-lookup"><span data-stu-id="e6649-120">For example, if you are compiling a C# file from the command line, use the [-reference (C# compiler options)](../../csharp/language-reference/compiler-options/reference-compiler-option.md) option to specify the assembly that contains the type.</span></span> <span data-ttu-id="e6649-121">W C++programie użyj dyrektywy [#using](/cpp/preprocessor/hash-using-directive-cpp) w pliku źródłowym, aby określić zestaw, który zawiera typ.</span><span class="sxs-lookup"><span data-stu-id="e6649-121">In C++, use the [#using](/cpp/preprocessor/hash-using-directive-cpp) directive in the source file to specify the assembly that contains the type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6649-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e6649-122">See also</span></span>

- <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>
- [<span data-ttu-id="e6649-123">Przekazywanie typu (C++/CLI)</span><span class="sxs-lookup"><span data-stu-id="e6649-123">Type forwarding (C++/CLI)</span></span>](/cpp/windows/type-forwarding-cpp-cli)
- [<span data-ttu-id="e6649-124">#using — dyrektywa</span><span class="sxs-lookup"><span data-stu-id="e6649-124">#using directive</span></span>](/cpp/preprocessor/hash-using-directive-cpp)
