---
title: Odbicie (Visual Basic)
ms.date: 07/20/2015
ms.assetid: d991bc0f-d16a-4ac5-9351-70e5c5b9891b
ms.openlocfilehash: d2ad8957d308aa98935c862ec1864b6682be904b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834884"
---
# <a name="reflection-visual-basic"></a><span data-ttu-id="5cbfd-102">Odbicie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5cbfd-102">Reflection (Visual Basic)</span></span>
<span data-ttu-id="5cbfd-103">Odbicie udostępnia obiekty (typu <xref:System.Type>) opisują zestawów, modułów i typów.</span><span class="sxs-lookup"><span data-stu-id="5cbfd-103">Reflection provides objects (of type <xref:System.Type>) that describe assemblies, modules and types.</span></span> <span data-ttu-id="5cbfd-104">Można używać odbicia do dynamicznego utworzenia wystąpienia typu, powiązania typu z istniejącym obiektem lub uzyskania typu z istniejącego obiektu i wywoływania jego metody lub dostępu do jego pola i właściwości.</span><span class="sxs-lookup"><span data-stu-id="5cbfd-104">You can use reflection to dynamically create an instance of a type, bind the type to an existing object, or get the type from an existing object and invoke its methods or access its fields and properties.</span></span> <span data-ttu-id="5cbfd-105">Jeśli używasz atrybutów w kodzie, odbicie umożliwia dostęp do nich.</span><span class="sxs-lookup"><span data-stu-id="5cbfd-105">If you are using attributes in your code, reflection enables you to access them.</span></span> <span data-ttu-id="5cbfd-106">Aby uzyskać więcej informacji, zobacz [atrybuty](../../../standard/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="5cbfd-106">For more information, see [Attributes](../../../standard/attributes/index.md).</span></span>  
  
 <span data-ttu-id="5cbfd-107">Poniżej przedstawiono prosty przykład odbicia przy użyciu metody statycznej `GetType` — dziedziczone przez wszystkie typy z `Object` podstawowej klasy — w celu uzyskania typu zmiennej:</span><span class="sxs-lookup"><span data-stu-id="5cbfd-107">Here's a simple example of reflection using the static method `GetType` - inherited by all types from the `Object` base class - to obtain the type of a variable:</span></span>  
  
```vb  
' Using GetType to obtain type information:  
Dim i As Integer = 42  
Dim type As System.Type = i.GetType()  
System.Console.WriteLine(type)  
```  
  
 <span data-ttu-id="5cbfd-108">Dane wyjściowe to:</span><span class="sxs-lookup"><span data-stu-id="5cbfd-108">The output is:</span></span>  
  
 `System.Int32`  
  
 <span data-ttu-id="5cbfd-109">W poniższym przykładzie użyto odbicia, aby uzyskać pełną nazwę załadowany zestaw.</span><span class="sxs-lookup"><span data-stu-id="5cbfd-109">The following example uses reflection to obtain the full name of the loaded assembly.</span></span>  
  
```vb  
' Using Reflection to get information from an Assembly:  
Dim info As System.Reflection.Assembly = GetType(System.Int32).Assembly  
System.Console.WriteLine(info)  
```  
  
 <span data-ttu-id="5cbfd-110">Dane wyjściowe to:</span><span class="sxs-lookup"><span data-stu-id="5cbfd-110">The output is:</span></span>  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
## <a name="reflection-overview"></a><span data-ttu-id="5cbfd-111">Omówienie odbicia</span><span class="sxs-lookup"><span data-stu-id="5cbfd-111">Reflection Overview</span></span>  
 <span data-ttu-id="5cbfd-112">Odbicie jest przydatne w następujących sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="5cbfd-112">Reflection is useful in the following situations:</span></span>  
  
-   <span data-ttu-id="5cbfd-113">Jeśli masz dostęp do atrybutów w metadanych programu.</span><span class="sxs-lookup"><span data-stu-id="5cbfd-113">When you have to access attributes in your program's metadata.</span></span> <span data-ttu-id="5cbfd-114">Aby uzyskać więcej informacji, zobacz [pobieranie informacji przechowywanych w atrybutach](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="5cbfd-114">For more information, see [Retrieving Information Stored in Attributes](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span></span>  
  
-   <span data-ttu-id="5cbfd-115">Badanie i tworzenie wystąpień typów w zestawie.</span><span class="sxs-lookup"><span data-stu-id="5cbfd-115">For examining and instantiating types in an assembly.</span></span>  
  
-   <span data-ttu-id="5cbfd-116">Do tworzenia nowych typów w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="5cbfd-116">For building new types at runtime.</span></span> <span data-ttu-id="5cbfd-117">Używanie klas w <xref:System.Reflection.Emit>.</span><span class="sxs-lookup"><span data-stu-id="5cbfd-117">Use classes in <xref:System.Reflection.Emit>.</span></span>  
  
-   <span data-ttu-id="5cbfd-118">Do wykonywania późne powiązania, uzyskiwanie dostępu do metody na typach tworzony w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="5cbfd-118">For performing late binding, accessing methods on types created at run time.</span></span> <span data-ttu-id="5cbfd-119">Zobacz temat [dynamiczne ładowanie i przy użyciu typów](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span><span class="sxs-lookup"><span data-stu-id="5cbfd-119">See the topic [Dynamically Loading and Using Types](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5cbfd-120">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="5cbfd-120">Related Sections</span></span>  
 <span data-ttu-id="5cbfd-121">Informacje dodatkowe:</span><span class="sxs-lookup"><span data-stu-id="5cbfd-121">For more information:</span></span>  
  
-   [<span data-ttu-id="5cbfd-122">Odbicie</span><span class="sxs-lookup"><span data-stu-id="5cbfd-122">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)  
  
-   [<span data-ttu-id="5cbfd-123">Wyświetlanie informacji o typie</span><span class="sxs-lookup"><span data-stu-id="5cbfd-123">Viewing Type Information</span></span>](../../../framework/reflection-and-codedom/viewing-type-information.md)  
  
-   [<span data-ttu-id="5cbfd-124">Odbicie i typy ogólne</span><span class="sxs-lookup"><span data-stu-id="5cbfd-124">Reflection and Generic Types</span></span>](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
  
-   <xref:System.Reflection.Emit>  
  
-   [<span data-ttu-id="5cbfd-125">Pobieranie informacji przechowywanych w atrybutach</span><span class="sxs-lookup"><span data-stu-id="5cbfd-125">Retrieving Information Stored in Attributes</span></span>](../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
  
## <a name="see-also"></a><span data-ttu-id="5cbfd-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5cbfd-126">See also</span></span>

- [<span data-ttu-id="5cbfd-127">Przewodnik programowania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5cbfd-127">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="5cbfd-128">Zestawy w środowisku uruchomieniowym CLR</span><span class="sxs-lookup"><span data-stu-id="5cbfd-128">Assemblies in the Common Language Runtime</span></span>](../../../framework/app-domains/assemblies-in-the-common-language-runtime.md)
