---
title: Odbicie
ms.date: 07/20/2015
ms.assetid: d991bc0f-d16a-4ac5-9351-70e5c5b9891b
ms.openlocfilehash: 28f33c88f7aaaf51938a7d27fd2218a97b628acd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349279"
---
# <a name="reflection-visual-basic"></a><span data-ttu-id="7fa21-102">Odbicie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7fa21-102">Reflection (Visual Basic)</span></span>
<span data-ttu-id="7fa21-103">Odbicie udostępnia obiekty (typu <xref:System.Type>) opisujące zestawy, moduły i typy.</span><span class="sxs-lookup"><span data-stu-id="7fa21-103">Reflection provides objects (of type <xref:System.Type>) that describe assemblies, modules and types.</span></span> <span data-ttu-id="7fa21-104">Możesz użyć odbicia, aby dynamicznie utworzyć wystąpienie typu, powiązać typ z istniejącym obiektem lub uzyskać typ z istniejącego obiektu i wywołać jego metody lub uzyskać dostęp do jego pól i właściwości.</span><span class="sxs-lookup"><span data-stu-id="7fa21-104">You can use reflection to dynamically create an instance of a type, bind the type to an existing object, or get the type from an existing object and invoke its methods or access its fields and properties.</span></span> <span data-ttu-id="7fa21-105">Jeśli używasz atrybutów w kodzie, odbicie umożliwia uzyskanie dostępu do nich.</span><span class="sxs-lookup"><span data-stu-id="7fa21-105">If you are using attributes in your code, reflection enables you to access them.</span></span> <span data-ttu-id="7fa21-106">Aby uzyskać więcej informacji, zobacz [atrybuty](../../../standard/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="7fa21-106">For more information, see [Attributes](../../../standard/attributes/index.md).</span></span>  
  
 <span data-ttu-id="7fa21-107">Oto prosty przykład odbicia przy użyciu metody statycznej `GetType`-dziedziczona przez wszystkie typy z klasy podstawowej `Object` — Aby uzyskać typ zmiennej:</span><span class="sxs-lookup"><span data-stu-id="7fa21-107">Here's a simple example of reflection using the static method `GetType` - inherited by all types from the `Object` base class - to obtain the type of a variable:</span></span>  
  
```vb  
' Using GetType to obtain type information:  
Dim i As Integer = 42  
Dim type As System.Type = i.GetType()  
System.Console.WriteLine(type)  
```  
  
 <span data-ttu-id="7fa21-108">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="7fa21-108">The output is:</span></span>  
  
 `System.Int32`  
  
 <span data-ttu-id="7fa21-109">Poniższy przykład używa odbicia w celu uzyskania pełnej nazwy załadowanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="7fa21-109">The following example uses reflection to obtain the full name of the loaded assembly.</span></span>  
  
```vb  
' Using Reflection to get information from an Assembly:  
Dim info As System.Reflection.Assembly = GetType(System.Int32).Assembly  
System.Console.WriteLine(info)  
```  
  
 <span data-ttu-id="7fa21-110">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="7fa21-110">The output is:</span></span>  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
## <a name="reflection-overview"></a><span data-ttu-id="7fa21-111">Przegląd odbicia</span><span class="sxs-lookup"><span data-stu-id="7fa21-111">Reflection Overview</span></span>  
 <span data-ttu-id="7fa21-112">Odbicie jest przydatne w następujących sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="7fa21-112">Reflection is useful in the following situations:</span></span>  
  
- <span data-ttu-id="7fa21-113">Gdy musisz uzyskać dostęp do atrybutów w metadanych programu.</span><span class="sxs-lookup"><span data-stu-id="7fa21-113">When you have to access attributes in your program's metadata.</span></span> <span data-ttu-id="7fa21-114">Aby uzyskać więcej informacji, zobacz artykuł [pobieranie informacji przechowywanych w atrybutach](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="7fa21-114">For more information, see [Retrieving Information Stored in Attributes](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span></span>  
  
- <span data-ttu-id="7fa21-115">Do badania i tworzenia wystąpień typów w zestawie.</span><span class="sxs-lookup"><span data-stu-id="7fa21-115">For examining and instantiating types in an assembly.</span></span>  
  
- <span data-ttu-id="7fa21-116">Do kompilowania nowych typów w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="7fa21-116">For building new types at runtime.</span></span> <span data-ttu-id="7fa21-117">Użyj klas w <xref:System.Reflection.Emit>.</span><span class="sxs-lookup"><span data-stu-id="7fa21-117">Use classes in <xref:System.Reflection.Emit>.</span></span>  
  
- <span data-ttu-id="7fa21-118">Do wykonywania późnego wiązania, uzyskiwanie dostępu do metod w typach utworzonych w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="7fa21-118">For performing late binding, accessing methods on types created at run time.</span></span> <span data-ttu-id="7fa21-119">Zobacz temat [dynamiczne ładowanie i używanie typów](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span><span class="sxs-lookup"><span data-stu-id="7fa21-119">See the topic [Dynamically Loading and Using Types](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7fa21-120">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="7fa21-120">Related Sections</span></span>  
 <span data-ttu-id="7fa21-121">Informacje dodatkowe:</span><span class="sxs-lookup"><span data-stu-id="7fa21-121">For more information:</span></span>  
  
- [<span data-ttu-id="7fa21-122">Odbicie</span><span class="sxs-lookup"><span data-stu-id="7fa21-122">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)  
  
- [<span data-ttu-id="7fa21-123">Wyświetlanie informacji o typie</span><span class="sxs-lookup"><span data-stu-id="7fa21-123">Viewing Type Information</span></span>](../../../framework/reflection-and-codedom/viewing-type-information.md)  
  
- [<span data-ttu-id="7fa21-124">Odbicie i typy ogólne</span><span class="sxs-lookup"><span data-stu-id="7fa21-124">Reflection and Generic Types</span></span>](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
  
- <xref:System.Reflection.Emit>  
  
- [<span data-ttu-id="7fa21-125">Pobieranie informacji przechowywanych w atrybutach</span><span class="sxs-lookup"><span data-stu-id="7fa21-125">Retrieving Information Stored in Attributes</span></span>](../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
  
## <a name="see-also"></a><span data-ttu-id="7fa21-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7fa21-126">See also</span></span>

- [<span data-ttu-id="7fa21-127">Przewodnik programowania Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7fa21-127">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="7fa21-128">Zestawy w środowisku .NET</span><span class="sxs-lookup"><span data-stu-id="7fa21-128">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
