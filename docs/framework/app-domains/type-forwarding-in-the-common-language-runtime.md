---
title: "Przekazywanie dalej typu w środowisku uruchomieniowym języka wspólnego"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- cpp
helpviewer_keywords:
- assemblies [.NET Framework], type forwarding
- type forwarding
ms.assetid: 51f8ffa3-c253-4201-a3d3-c4fad85ae097
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 32dad99e8d5caa7d88fa302a1bea8b83847bfde3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="type-forwarding-in-the-common-language-runtime"></a><span data-ttu-id="71ec5-102">Przekazywanie dalej typu w środowisku uruchomieniowym języka wspólnego</span><span class="sxs-lookup"><span data-stu-id="71ec5-102">Type Forwarding in the Common Language Runtime</span></span>
<span data-ttu-id="71ec5-103">Przekazywanie dalej typu umożliwia przeniesienie typu do innego zestawu bez konieczności ponownego kompilowania aplikacji, które używają oryginalnego zestawu.</span><span class="sxs-lookup"><span data-stu-id="71ec5-103">Type forwarding allows you to move a type to another assembly without having to recompile applications that use the original assembly.</span></span>  
  
 <span data-ttu-id="71ec5-104">Na przykład, załóżmy, że aplikacja używa `Example` klasa w zestawie o nazwie `Utility.dll`.</span><span class="sxs-lookup"><span data-stu-id="71ec5-104">For example, suppose an application uses the `Example` class in an assembly named `Utility.dll`.</span></span> <span data-ttu-id="71ec5-105">Deweloperzy `Utility.dll` zdecydować o Refaktoryzuj zestawu, a w procesie może przenieść `Example` klasy do innego zestawu.</span><span class="sxs-lookup"><span data-stu-id="71ec5-105">The developers of `Utility.dll` might decide to refactor the assembly, and in the process they might move the `Example` class to another assembly.</span></span> <span data-ttu-id="71ec5-106">Jeśli stara wersja `Utility.dll` zostało zastąpione przez nową wersję `Utility.dll` i jego zestawu uzupełniających, aplikacji używającej `Example` klasy nie powiedzie się, ponieważ nie można zlokalizować `Example` klasy w nowej wersji `Utility.dll`.</span><span class="sxs-lookup"><span data-stu-id="71ec5-106">If the old version of `Utility.dll` is replaced by the new version of `Utility.dll` and its companion assembly, the application that uses the `Example` class fails because it cannot locate the `Example` class in the new version of `Utility.dll`.</span></span>  
  
 <span data-ttu-id="71ec5-107">Deweloperzy `Utility.dll` można tego uniknąć przekazywania żądań `Example` przy użyciu <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="71ec5-107">The developers of `Utility.dll` can avoid this by forwarding requests for the `Example` class, using the <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> attribute.</span></span> <span data-ttu-id="71ec5-108">Jeśli zastosowano atrybut do nowej wersji `Utility.dll`, żądania dotyczące `Example` klasy są przekazywane do zestawu, który zawiera teraz klasy.</span><span class="sxs-lookup"><span data-stu-id="71ec5-108">If the attribute has been applied to the new version of `Utility.dll`, requests for the `Example` class are forwarded to the assembly that now contains the class.</span></span> <span data-ttu-id="71ec5-109">Istniejącej aplikacji działa normalnie, bez ponownej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="71ec5-109">The existing application continues to function normally, without recompilation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="71ec5-110">W programie .NET Framework w wersji 2.0 nie można przesłać dalej typy z zestawów napisane w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="71ec5-110">In the .NET Framework version 2.0, you cannot forward types from assemblies written in Visual Basic.</span></span> <span data-ttu-id="71ec5-111">Jednak aplikacja napisana w języku Visual Basic, jaką może wykorzystać typów przekazywane.</span><span class="sxs-lookup"><span data-stu-id="71ec5-111">However, an application written in Visual Basic can consume forwarded types.</span></span> <span data-ttu-id="71ec5-112">Oznacza to jeśli aplikacja używa zestawu kodowane w języku C# lub języka C++, a typ z tego zestawu jest przekazywany do innego zestawu, aplikacji Visual Basic można użyć typu przekazany dalej.</span><span class="sxs-lookup"><span data-stu-id="71ec5-112">That is, if the application uses an assembly coded in C# or C++, and a type from that assembly is forwarded to another assembly, the Visual Basic application can use the forwarded type.</span></span>  
  
## <a name="forwarding-types"></a><span data-ttu-id="71ec5-113">Przekazywanie typów</span><span class="sxs-lookup"><span data-stu-id="71ec5-113">Forwarding Types</span></span>  
 <span data-ttu-id="71ec5-114">Istnieją cztery kroki do przesyłania dalej typu:</span><span class="sxs-lookup"><span data-stu-id="71ec5-114">There are four steps to forwarding a type:</span></span>  
  
1.  <span data-ttu-id="71ec5-115">Przenoszenie kodu źródłowego dla typu z oryginalnego zestawu do zestawu docelowego.</span><span class="sxs-lookup"><span data-stu-id="71ec5-115">Move the source code for the type from the original assembly to the destination assembly.</span></span>  
  
2.  <span data-ttu-id="71ec5-116">W zestawie, gdzie typ używany do można znaleźć, Dodaj <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> dla typu, która została przeniesiona.</span><span class="sxs-lookup"><span data-stu-id="71ec5-116">In the assembly where the type used to be located, add a <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> for the type that was moved.</span></span> <span data-ttu-id="71ec5-117">Poniższy kod przedstawia atrybut typu o nazwie `Example` który został przeniesiony.</span><span class="sxs-lookup"><span data-stu-id="71ec5-117">The following code shows the attribute for a type named `Example` that was moved.</span></span>  
  
    ```csharp  
    [assembly:TypeForwardedToAttribute(typeof(Example))]  
    ```  
  
    ```cpp  
    [assembly:TypeForwardedToAttribute(Example::typeid)]  
    ```  
  
3.  <span data-ttu-id="71ec5-118">Kompilowanie zestawu, który zawiera teraz typu.</span><span class="sxs-lookup"><span data-stu-id="71ec5-118">Compile the assembly that now contains the type.</span></span>  
  
4.  <span data-ttu-id="71ec5-119">Skompiluj ponownie zestawu, gdzie typ używany do znajdować się odwołanie do zestawu, który zawiera teraz typ.</span><span class="sxs-lookup"><span data-stu-id="71ec5-119">Recompile the assembly where the type used to be located, with a reference to the assembly that now contains the type.</span></span> <span data-ttu-id="71ec5-120">Na przykład, jeśli kompilacja pliku C# z wiersza polecenia, użyj [/Reference (opcje kompilatora C#)](~/docs/csharp/language-reference/compiler-options/reference-compiler-option.md) opcję, aby określić zestaw zawierający typ.</span><span class="sxs-lookup"><span data-stu-id="71ec5-120">For example, if you are compiling a C# file from the command line, use the [/reference (C# Compiler Options)](~/docs/csharp/language-reference/compiler-options/reference-compiler-option.md) option to specify the assembly that contains the type.</span></span> <span data-ttu-id="71ec5-121">W języku C++ użyj [#using](http://msdn.microsoft.com/library/870b15e5-f361-40a8-ba1c-c57d75c8809a) dyrektywy w pliku źródłowym, aby określić zestaw zawierający typ.</span><span class="sxs-lookup"><span data-stu-id="71ec5-121">In C++, use the [#using](http://msdn.microsoft.com/library/870b15e5-f361-40a8-ba1c-c57d75c8809a) directive in the source file to specify the assembly that contains the type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71ec5-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="71ec5-122">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>  
 [<span data-ttu-id="71ec5-123">Przekazywanie dalej typu (C++/CLI)</span><span class="sxs-lookup"><span data-stu-id="71ec5-123">Type Forwarding (C++/CLI)</span></span>](/cpp/windows/type-forwarding-cpp-cli)  
 [<span data-ttu-id="71ec5-124">#using — dyrektywa</span><span class="sxs-lookup"><span data-stu-id="71ec5-124">#using Directive</span></span>](http://msdn.microsoft.com/library/870b15e5-f361-40a8-ba1c-c57d75c8809a)
