---
title: Odbicie (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: d991bc0f-d16a-4ac5-9351-70e5c5b9891b
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ca22705a0eee6749ff7121d63d9b505b153e45d9
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="reflection-visual-basic"></a><span data-ttu-id="529ba-102">Odbicie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="529ba-102">Reflection (Visual Basic)</span></span>
<span data-ttu-id="529ba-103">Odbicie udostępnia obiekty (typu <xref:System.Type>) opisują zestawy, moduły i typy.</span><span class="sxs-lookup"><span data-stu-id="529ba-103">Reflection provides objects (of type <xref:System.Type>) that describe assemblies, modules and types.</span></span> <span data-ttu-id="529ba-104">Odbicie umożliwia dynamicznie utworzyć wystąpienia typu, powiązać danego typu do istniejącego obiektu, lub pobranie typu z istniejącego obiektu i wywołanie metody lub dostępu do swoich pól i właściwości.</span><span class="sxs-lookup"><span data-stu-id="529ba-104">You can use reflection to dynamically create an instance of a type, bind the type to an existing object, or get the type from an existing object and invoke its methods or access its fields and properties.</span></span> <span data-ttu-id="529ba-105">Jeśli używane są atrybuty w kodzie, odbicia umożliwia dostęp do nich.</span><span class="sxs-lookup"><span data-stu-id="529ba-105">If you are using attributes in your code, reflection enables you to access them.</span></span> <span data-ttu-id="529ba-106">Aby uzyskać więcej informacji, zobacz [atrybutów](../../../standard/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="529ba-106">For more information, see [Attributes](../../../standard/attributes/index.md).</span></span>  
  
 <span data-ttu-id="529ba-107">Poniżej przedstawiono prosty przykład odbicia przy użyciu metody statycznej `GetType` — dziedziczone przez wszystkie typy z `Object` podstawowa klasa — można uzyskać typu zmienną:</span><span class="sxs-lookup"><span data-stu-id="529ba-107">Here's a simple example of reflection using the static method `GetType` - inherited by all types from the `Object` base class - to obtain the type of a variable:</span></span>  
  
```vb  
' Using GetType to obtain type information:  
Dim i As Integer = 42  
Dim type As System.Type = i.GetType()  
System.Console.WriteLine(type)  
```  
  
 <span data-ttu-id="529ba-108">Wynik jest:</span><span class="sxs-lookup"><span data-stu-id="529ba-108">The output is:</span></span>  
  
 `System.Int32`  
  
 <span data-ttu-id="529ba-109">W poniższym przykładzie użyto odbicia, aby uzyskać pełną nazwę załadowanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="529ba-109">The following example uses reflection to obtain the full name of the loaded assembly.</span></span>  
  
```vb  
' Using Reflection to get information from an Assembly:  
Dim info As System.Reflection.Assembly = GetType(System.Int32).Assembly  
System.Console.WriteLine(info)  
```  
  
 <span data-ttu-id="529ba-110">Wynik jest:</span><span class="sxs-lookup"><span data-stu-id="529ba-110">The output is:</span></span>  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
## <a name="reflection-overview"></a><span data-ttu-id="529ba-111">Odbicie — omówienie</span><span class="sxs-lookup"><span data-stu-id="529ba-111">Reflection Overview</span></span>  
 <span data-ttu-id="529ba-112">Odbicie jest przydatne w następujących sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="529ba-112">Reflection is useful in the following situations:</span></span>  
  
-   <span data-ttu-id="529ba-113">Jeśli użytkownik ma dostęp do atrybutów w metadanych programu.</span><span class="sxs-lookup"><span data-stu-id="529ba-113">When you have to access attributes in your program's metadata.</span></span> <span data-ttu-id="529ba-114">Aby uzyskać więcej informacji, zobacz [pobierania informacji przechowywanych w atrybutach](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="529ba-114">For more information, see [Retrieving Information Stored in Attributes](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span></span>  
  
-   <span data-ttu-id="529ba-115">Badanie i tworzenie wystąpień typów w zestawie.</span><span class="sxs-lookup"><span data-stu-id="529ba-115">For examining and instantiating types in an assembly.</span></span>  
  
-   <span data-ttu-id="529ba-116">Do tworzenia nowych typów w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="529ba-116">For building new types at runtime.</span></span> <span data-ttu-id="529ba-117">Korzystanie z klas w <xref:System.Reflection.Emit>.</span><span class="sxs-lookup"><span data-stu-id="529ba-117">Use classes in <xref:System.Reflection.Emit>.</span></span>  
  
-   <span data-ttu-id="529ba-118">Do wykonania późne wiązanie podczas uzyskiwania dostępu do metody na typach utworzone w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="529ba-118">For performing late binding, accessing methods on types created at run time.</span></span> <span data-ttu-id="529ba-119">Zobacz temat [dynamiczne ładowanie i przy użyciu typów](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span><span class="sxs-lookup"><span data-stu-id="529ba-119">See the topic [Dynamically Loading and Using Types](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="529ba-120">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="529ba-120">Related Sections</span></span>  
 <span data-ttu-id="529ba-121">Informacje dodatkowe:</span><span class="sxs-lookup"><span data-stu-id="529ba-121">For more information:</span></span>  
  
-   [<span data-ttu-id="529ba-122">Odbicie</span><span class="sxs-lookup"><span data-stu-id="529ba-122">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)  
  
-   [<span data-ttu-id="529ba-123">Wyświetlanie informacji o typie</span><span class="sxs-lookup"><span data-stu-id="529ba-123">Viewing Type Information</span></span>](../../../framework/reflection-and-codedom/viewing-type-information.md)  
  
-   [<span data-ttu-id="529ba-124">Odbicie i typy ogólne</span><span class="sxs-lookup"><span data-stu-id="529ba-124">Reflection and Generic Types</span></span>](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
  
-   <xref:System.Reflection.Emit>  
  
-   [<span data-ttu-id="529ba-125">Pobieranie informacji przechowywanych w atrybutach</span><span class="sxs-lookup"><span data-stu-id="529ba-125">Retrieving Information Stored in Attributes</span></span>](../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
  
## <a name="see-also"></a><span data-ttu-id="529ba-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="529ba-126">See Also</span></span>  
 [<span data-ttu-id="529ba-127">Przewodnik programowania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="529ba-127">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)  
 [<span data-ttu-id="529ba-128">Zestawy w środowisku uruchomieniowym CLR</span><span class="sxs-lookup"><span data-stu-id="529ba-128">Assemblies in the Common Language Runtime</span></span>](../../../framework/app-domains/assemblies-in-the-common-language-runtime.md)
