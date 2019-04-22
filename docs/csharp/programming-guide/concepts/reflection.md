---
title: Odbicie (C#)
ms.date: 07/20/2015
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
ms.openlocfilehash: 4dfd9391407fec4bd20ac4ae05162763e909d665
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58841319"
---
# <a name="reflection-c"></a><span data-ttu-id="30a6b-102">Odbicie (C#)</span><span class="sxs-lookup"><span data-stu-id="30a6b-102">Reflection (C#)</span></span>
<span data-ttu-id="30a6b-103">Odbicie udostępnia obiekty (typu <xref:System.Type>) opisują zestawów, modułów i typów.</span><span class="sxs-lookup"><span data-stu-id="30a6b-103">Reflection provides objects (of type <xref:System.Type>) that describe assemblies, modules and types.</span></span> <span data-ttu-id="30a6b-104">Można używać odbicia do dynamicznego utworzenia wystąpienia typu, powiązania typu z istniejącym obiektem lub uzyskania typu z istniejącego obiektu i wywoływania jego metody lub dostępu do jego pola i właściwości.</span><span class="sxs-lookup"><span data-stu-id="30a6b-104">You can use reflection to dynamically create an instance of a type, bind the type to an existing object, or get the type from an existing object and invoke its methods or access its fields and properties.</span></span> <span data-ttu-id="30a6b-105">Jeśli używasz atrybutów w kodzie, odbicie umożliwia dostęp do nich.</span><span class="sxs-lookup"><span data-stu-id="30a6b-105">If you are using attributes in your code, reflection enables you to access them.</span></span> <span data-ttu-id="30a6b-106">Aby uzyskać więcej informacji, zobacz [atrybuty](../../../../docs/standard/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="30a6b-106">For more information, see [Attributes](../../../../docs/standard/attributes/index.md).</span></span>  
  
 <span data-ttu-id="30a6b-107">Poniżej przedstawiono prosty przykład odbicia przy użyciu metody statycznej `GetType` — dziedziczone przez wszystkie typy z `Object` podstawowej klasy — w celu uzyskania typu zmiennej:</span><span class="sxs-lookup"><span data-stu-id="30a6b-107">Here's a simple example of reflection using the static method `GetType` - inherited by all types from the `Object` base class - to obtain the type of a variable:</span></span>  
  
```csharp  
// Using GetType to obtain type information:  
int i = 42;  
System.Type type = i.GetType();  
System.Console.WriteLine(type);  
```  
  
 <span data-ttu-id="30a6b-108">Dane wyjściowe to:</span><span class="sxs-lookup"><span data-stu-id="30a6b-108">The output is:</span></span>  
  
 `System.Int32`  
  
 <span data-ttu-id="30a6b-109">W poniższym przykładzie użyto odbicia, aby uzyskać pełną nazwę załadowany zestaw.</span><span class="sxs-lookup"><span data-stu-id="30a6b-109">The following example uses reflection to obtain the full name of the loaded assembly.</span></span>  
  
```csharp  
// Using Reflection to get information of an Assembly:  
System.Reflection.Assembly info = typeof(System.Int32).Assembly;  
System.Console.WriteLine(info);  
```  
  
 <span data-ttu-id="30a6b-110">Dane wyjściowe to:</span><span class="sxs-lookup"><span data-stu-id="30a6b-110">The output is:</span></span>  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
> [!NOTE]
>  <span data-ttu-id="30a6b-111">Słowa kluczowe języka C# `protected` i `internal` nie mają znaczenia IL i nie są używane w odbiciu interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="30a6b-111">The C# keywords `protected` and `internal` have no meaning in IL and are not used in the reflection APIs.</span></span> <span data-ttu-id="30a6b-112">Odpowiednie postanowienia IL są *rodziny* i *zestawu*.</span><span class="sxs-lookup"><span data-stu-id="30a6b-112">The corresponding terms in IL are *Family* and *Assembly*.</span></span> <span data-ttu-id="30a6b-113">Aby zidentyfikować `internal` przy użyciu odbicia, użyj metody <xref:System.Reflection.MethodBase.IsAssembly%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="30a6b-113">To identify an `internal` method using reflection, use the <xref:System.Reflection.MethodBase.IsAssembly%2A> property.</span></span> <span data-ttu-id="30a6b-114">Aby zidentyfikować `protected internal` metody, użyj <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.</span><span class="sxs-lookup"><span data-stu-id="30a6b-114">To identify a `protected internal` method, use the <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.</span></span>  
  
## <a name="reflection-overview"></a><span data-ttu-id="30a6b-115">Omówienie odbicia</span><span class="sxs-lookup"><span data-stu-id="30a6b-115">Reflection Overview</span></span>  
 <span data-ttu-id="30a6b-116">Odbicie jest przydatne w następujących sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="30a6b-116">Reflection is useful in the following situations:</span></span>  
  
-   <span data-ttu-id="30a6b-117">Jeśli masz dostęp do atrybutów w metadanych programu.</span><span class="sxs-lookup"><span data-stu-id="30a6b-117">When you have to access attributes in your program's metadata.</span></span> <span data-ttu-id="30a6b-118">Aby uzyskać więcej informacji, zobacz [pobieranie informacji przechowywanych w atrybutach](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="30a6b-118">For more information, see [Retrieving Information Stored in Attributes](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span></span>  
  
-   <span data-ttu-id="30a6b-119">Badanie i tworzenie wystąpień typów w zestawie.</span><span class="sxs-lookup"><span data-stu-id="30a6b-119">For examining and instantiating types in an assembly.</span></span>  
  
-   <span data-ttu-id="30a6b-120">Do tworzenia nowych typów w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="30a6b-120">For building new types at runtime.</span></span> <span data-ttu-id="30a6b-121">Używanie klas w <xref:System.Reflection.Emit>.</span><span class="sxs-lookup"><span data-stu-id="30a6b-121">Use classes in <xref:System.Reflection.Emit>.</span></span>  
  
-   <span data-ttu-id="30a6b-122">Do wykonywania późne powiązania, uzyskiwanie dostępu do metody na typach tworzony w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="30a6b-122">For performing late binding, accessing methods on types created at run time.</span></span> <span data-ttu-id="30a6b-123">Zobacz temat [dynamiczne ładowanie i przy użyciu typów](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span><span class="sxs-lookup"><span data-stu-id="30a6b-123">See the topic [Dynamically Loading and Using Types](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="30a6b-124">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="30a6b-124">Related Sections</span></span>  
 <span data-ttu-id="30a6b-125">Informacje dodatkowe:</span><span class="sxs-lookup"><span data-stu-id="30a6b-125">For more information:</span></span>  
  
-   [<span data-ttu-id="30a6b-126">Odbicie</span><span class="sxs-lookup"><span data-stu-id="30a6b-126">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)  
  
-   [<span data-ttu-id="30a6b-127">Wyświetlanie informacji o typie</span><span class="sxs-lookup"><span data-stu-id="30a6b-127">Viewing Type Information</span></span>](../../../framework/reflection-and-codedom/viewing-type-information.md)  
  
-   [<span data-ttu-id="30a6b-128">Odbicie i typy ogólne</span><span class="sxs-lookup"><span data-stu-id="30a6b-128">Reflection and Generic Types</span></span>](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
  
-   <xref:System.Reflection.Emit>  
  
-   [<span data-ttu-id="30a6b-129">Pobieranie informacji przechowywanych w atrybutach</span><span class="sxs-lookup"><span data-stu-id="30a6b-129">Retrieving Information Stored in Attributes</span></span>](../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
  
## <a name="see-also"></a><span data-ttu-id="30a6b-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="30a6b-130">See also</span></span>

- [<span data-ttu-id="30a6b-131">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="30a6b-131">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="30a6b-132">Zestawy w środowisku uruchomieniowym CLR</span><span class="sxs-lookup"><span data-stu-id="30a6b-132">Assemblies in the Common Language Runtime</span></span>](../../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
