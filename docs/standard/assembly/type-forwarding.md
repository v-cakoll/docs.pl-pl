---
title: Przekazywanie dalej typu w środowisku uruchomieniowym języka wspólnego
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], type forwarding
- type forwarding
ms.assetid: 51f8ffa3-c253-4201-a3d3-c4fad85ae097
dev_langs:
- csharp
- cpp
ms.openlocfilehash: 215636a9617a2723d8ab69640c1d3e69491a7d87
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160368"
---
# <a name="type-forwarding-in-the-common-language-runtime"></a><span data-ttu-id="3744e-102">Przekazywanie dalej typu w środowisku uruchomieniowym języka wspólnego</span><span class="sxs-lookup"><span data-stu-id="3744e-102">Type forwarding in the common language runtime</span></span>
<span data-ttu-id="3744e-103">Przekazywanie tekstu umożliwia przeniesienie typu do innego zestawu bez konieczności ponownej kompilacji aplikacji korzystających z oryginalnego zestawu.</span><span class="sxs-lookup"><span data-stu-id="3744e-103">Type forwarding allows you to move a type to another assembly without having to recompile applications that use the original assembly.</span></span>  
  
 <span data-ttu-id="3744e-104">Załóżmy na przykład, `Example` że aplikacja używa klasy w zestawie o nazwie *Utility.dll*.</span><span class="sxs-lookup"><span data-stu-id="3744e-104">For example, suppose an application uses the `Example` class in an assembly named *Utility.dll*.</span></span> <span data-ttu-id="3744e-105">Deweloperzy *Utility.dll* może zdecydować się na refaktoryzacji zestawu, `Example` a w procesie mogą przenieść klasy do innego zestawu.</span><span class="sxs-lookup"><span data-stu-id="3744e-105">The developers of *Utility.dll* might decide to refactor the assembly, and in the process they might move the `Example` class to another assembly.</span></span> <span data-ttu-id="3744e-106">Jeśli stara wersja *pliku Utility.dll* zostanie zastąpiona nową wersją *pliku Utility.dll* i jej zestawu towarzyszącego, aplikacja korzystająca z `Example` tej klasy nie powiedzie się, ponieważ nie może zlokalizować `Example` klasy w nowej wersji pliku *Utility.dll*.</span><span class="sxs-lookup"><span data-stu-id="3744e-106">If the old version of *Utility.dll* is replaced by the new version of *Utility.dll* and its companion assembly, the application that uses the `Example` class fails because it cannot locate the `Example` class in the new version of *Utility.dll*.</span></span>  
  
 <span data-ttu-id="3744e-107">Deweloperzy *Utility.dll* można tego uniknąć, przesyłając dalej żądania dla `Example` klasy, przy użyciu atrybutu. <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute></span><span class="sxs-lookup"><span data-stu-id="3744e-107">The developers of *Utility.dll* can avoid this by forwarding requests for the `Example` class, using the <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> attribute.</span></span> <span data-ttu-id="3744e-108">Jeśli atrybut został zastosowany do nowej wersji *Utility.dll,* żądania dla `Example` klasy są przekazywane do zestawu, który teraz zawiera klasę.</span><span class="sxs-lookup"><span data-stu-id="3744e-108">If the attribute has been applied to the new version of *Utility.dll*, requests for the `Example` class are forwarded to the assembly that now contains the class.</span></span> <span data-ttu-id="3744e-109">Istniejąca aplikacja nadal działa normalnie, bez ponownej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="3744e-109">The existing application continues to function normally, without recompilation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3744e-110">W wersji .NET Framework w wersji 2.0 nie można przesyłać dalej typów z zestawów napisanych w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="3744e-110">In the .NET Framework version 2.0, you cannot forward types from assemblies written in Visual Basic.</span></span> <span data-ttu-id="3744e-111">Jednak aplikacja napisana w języku Visual Basic może korzystać z typów przesyłanych dalej.</span><span class="sxs-lookup"><span data-stu-id="3744e-111">However, an application written in Visual Basic can consume forwarded types.</span></span> <span data-ttu-id="3744e-112">Oznacza to, że jeśli aplikacja używa zestawu zakodowanego w języku C# lub C++, a typ z tego zestawu jest przekazywany do innego zestawu, aplikacja Visual Basic może używać typu przekazywanego dalej.</span><span class="sxs-lookup"><span data-stu-id="3744e-112">That is, if the application uses an assembly coded in C# or C++, and a type from that assembly is forwarded to another assembly, the Visual Basic application can use the forwarded type.</span></span>  
  
## <a name="forward-types"></a><span data-ttu-id="3744e-113">Typy do przodu</span><span class="sxs-lookup"><span data-stu-id="3744e-113">Forward types</span></span>  
 <span data-ttu-id="3744e-114">Istnieją cztery kroki przekazywania typu:</span><span class="sxs-lookup"><span data-stu-id="3744e-114">There are four steps to forwarding a type:</span></span>  
  
1. <span data-ttu-id="3744e-115">Przenieś kod źródłowy typu z oryginalnego złożenia do zestawu docelowego.</span><span class="sxs-lookup"><span data-stu-id="3744e-115">Move the source code for the type from the original assembly to the destination assembly.</span></span>  

2. <span data-ttu-id="3744e-116">W zestawie, w którym typ był <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> używany, dodaj a dla typu, który został przeniesiony.</span><span class="sxs-lookup"><span data-stu-id="3744e-116">In the assembly where the type used to be located, add a <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> for the type that was moved.</span></span> <span data-ttu-id="3744e-117">Poniższy kod przedstawia atrybut dla `Example` typu o nazwie, który został przeniesiony.</span><span class="sxs-lookup"><span data-stu-id="3744e-117">The following code shows the attribute for a type named `Example` that was moved.</span></span>  

   ```cpp  
    [assembly:TypeForwardedToAttribute(Example::typeid)]  
   ```

   ```csharp  
    [assembly:TypeForwardedToAttribute(typeof(Example))]  
   ```  

3. <span data-ttu-id="3744e-118">Skompiluj zestaw, który teraz zawiera typ.</span><span class="sxs-lookup"><span data-stu-id="3744e-118">Compile the assembly that now contains the type.</span></span>  

4. <span data-ttu-id="3744e-119">Ponownie skompilować zestaw, w którym typ był używany, z odwołaniem do zestawu, który teraz zawiera typ.</span><span class="sxs-lookup"><span data-stu-id="3744e-119">Recompile the assembly where the type used to be located, with a reference to the assembly that now contains the type.</span></span> <span data-ttu-id="3744e-120">Na przykład jeśli kompilowanie pliku C# z wiersza polecenia, użyj [-reference (Opcje kompilatora C#),](../../csharp/language-reference/compiler-options/reference-compiler-option.md) aby określić zestaw, który zawiera typ.</span><span class="sxs-lookup"><span data-stu-id="3744e-120">For example, if you are compiling a C# file from the command line, use the [-reference (C# compiler options)](../../csharp/language-reference/compiler-options/reference-compiler-option.md) option to specify the assembly that contains the type.</span></span> <span data-ttu-id="3744e-121">W języku C++ użyj dyrektywy [#using](/cpp/preprocessor/hash-using-directive-cpp) w pliku źródłowym, aby określić zestaw, który zawiera typ.</span><span class="sxs-lookup"><span data-stu-id="3744e-121">In C++, use the [#using](/cpp/preprocessor/hash-using-directive-cpp) directive in the source file to specify the assembly that contains the type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3744e-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3744e-122">See also</span></span>

- <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>
- [<span data-ttu-id="3744e-123">Przekazywanie tekstu (C++/CLI)</span><span class="sxs-lookup"><span data-stu-id="3744e-123">Type forwarding (C++/CLI)</span></span>](/cpp/windows/type-forwarding-cpp-cli)
- [<span data-ttu-id="3744e-124">dyrektywa #using</span><span class="sxs-lookup"><span data-stu-id="3744e-124">#using directive</span></span>](/cpp/preprocessor/hash-using-directive-cpp)
