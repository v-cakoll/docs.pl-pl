---
title: OdbicieC#()
ms.date: 07/20/2015
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
ms.openlocfilehash: 7906ca6f02a369e6f4d51f11f96616b6a89f48c5
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70971661"
---
# <a name="reflection-c"></a><span data-ttu-id="c3e7f-102">OdbicieC#()</span><span class="sxs-lookup"><span data-stu-id="c3e7f-102">Reflection (C#)</span></span>
<span data-ttu-id="c3e7f-103">Odbicie zawiera obiekty (typu <xref:System.Type>) opisujące zestawy, moduły i typy.</span><span class="sxs-lookup"><span data-stu-id="c3e7f-103">Reflection provides objects (of type <xref:System.Type>) that describe assemblies, modules and types.</span></span> <span data-ttu-id="c3e7f-104">Możesz użyć odbicia, aby dynamicznie utworzyć wystąpienie typu, powiązać typ z istniejącym obiektem lub uzyskać typ z istniejącego obiektu i wywołać jego metody lub uzyskać dostęp do jego pól i właściwości.</span><span class="sxs-lookup"><span data-stu-id="c3e7f-104">You can use reflection to dynamically create an instance of a type, bind the type to an existing object, or get the type from an existing object and invoke its methods or access its fields and properties.</span></span> <span data-ttu-id="c3e7f-105">Jeśli używasz atrybutów w kodzie, odbicie umożliwia uzyskanie dostępu do nich.</span><span class="sxs-lookup"><span data-stu-id="c3e7f-105">If you are using attributes in your code, reflection enables you to access them.</span></span> <span data-ttu-id="c3e7f-106">Aby uzyskać więcej informacji, zobacz [atrybuty](../../../standard/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="c3e7f-106">For more information, see [Attributes](../../../standard/attributes/index.md).</span></span>  
  
 <span data-ttu-id="c3e7f-107">Oto prosty przykład odbicia przy użyciu metody `GetType` statycznej dziedziczonej przez wszystkie typy `Object` z klasy podstawowej — w celu uzyskania typu zmiennej:</span><span class="sxs-lookup"><span data-stu-id="c3e7f-107">Here's a simple example of reflection using the static method `GetType` - inherited by all types from the `Object` base class - to obtain the type of a variable:</span></span>  
  
```csharp  
// Using GetType to obtain type information:  
int i = 42;  
System.Type type = i.GetType();  
System.Console.WriteLine(type);  
```  
  
 <span data-ttu-id="c3e7f-108">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="c3e7f-108">The output is:</span></span>  
  
 `System.Int32`  
  
 <span data-ttu-id="c3e7f-109">Poniższy przykład używa odbicia w celu uzyskania pełnej nazwy załadowanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="c3e7f-109">The following example uses reflection to obtain the full name of the loaded assembly.</span></span>  
  
```csharp  
// Using Reflection to get information of an Assembly:  
System.Reflection.Assembly info = typeof(System.Int32).Assembly;  
System.Console.WriteLine(info);  
```  
  
 <span data-ttu-id="c3e7f-110">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="c3e7f-110">The output is:</span></span>  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
> [!NOTE]
> <span data-ttu-id="c3e7f-111">C# Słowa kluczowe `protected` i`internal` nie mają znaczenia w Il i nie są używane w interfejsach API odbicia.</span><span class="sxs-lookup"><span data-stu-id="c3e7f-111">The C# keywords `protected` and `internal` have no meaning in IL and are not used in the reflection APIs.</span></span> <span data-ttu-id="c3e7f-112">Odpowiednie warunki w IL są *rodziną* i *zestawem*.</span><span class="sxs-lookup"><span data-stu-id="c3e7f-112">The corresponding terms in IL are *Family* and *Assembly*.</span></span> <span data-ttu-id="c3e7f-113">Aby zidentyfikować `internal` metodę przy użyciu odbicia, <xref:System.Reflection.MethodBase.IsAssembly%2A> należy użyć właściwości.</span><span class="sxs-lookup"><span data-stu-id="c3e7f-113">To identify an `internal` method using reflection, use the <xref:System.Reflection.MethodBase.IsAssembly%2A> property.</span></span> <span data-ttu-id="c3e7f-114">Aby zidentyfikować `protected internal` metodę, <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>Użyj.</span><span class="sxs-lookup"><span data-stu-id="c3e7f-114">To identify a `protected internal` method, use the <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.</span></span>  
  
## <a name="reflection-overview"></a><span data-ttu-id="c3e7f-115">Przegląd odbicia</span><span class="sxs-lookup"><span data-stu-id="c3e7f-115">Reflection Overview</span></span>  
 <span data-ttu-id="c3e7f-116">Odbicie jest przydatne w następujących sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="c3e7f-116">Reflection is useful in the following situations:</span></span>  
  
- <span data-ttu-id="c3e7f-117">Gdy musisz uzyskać dostęp do atrybutów w metadanych programu.</span><span class="sxs-lookup"><span data-stu-id="c3e7f-117">When you have to access attributes in your program's metadata.</span></span> <span data-ttu-id="c3e7f-118">Aby uzyskać więcej informacji, zobacz artykuł [pobieranie informacji przechowywanych w atrybutach](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="c3e7f-118">For more information, see [Retrieving Information Stored in Attributes](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span></span>  
  
- <span data-ttu-id="c3e7f-119">Do badania i tworzenia wystąpień typów w zestawie.</span><span class="sxs-lookup"><span data-stu-id="c3e7f-119">For examining and instantiating types in an assembly.</span></span>  
  
- <span data-ttu-id="c3e7f-120">Do kompilowania nowych typów w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c3e7f-120">For building new types at runtime.</span></span> <span data-ttu-id="c3e7f-121">Użyj klas w <xref:System.Reflection.Emit>.</span><span class="sxs-lookup"><span data-stu-id="c3e7f-121">Use classes in <xref:System.Reflection.Emit>.</span></span>  
  
- <span data-ttu-id="c3e7f-122">Do wykonywania późnego wiązania, uzyskiwanie dostępu do metod w typach utworzonych w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c3e7f-122">For performing late binding, accessing methods on types created at run time.</span></span> <span data-ttu-id="c3e7f-123">Zobacz temat [dynamiczne ładowanie i używanie typów](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span><span class="sxs-lookup"><span data-stu-id="c3e7f-123">See the topic [Dynamically Loading and Using Types](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c3e7f-124">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="c3e7f-124">Related Sections</span></span>  
 <span data-ttu-id="c3e7f-125">Informacje dodatkowe:</span><span class="sxs-lookup"><span data-stu-id="c3e7f-125">For more information:</span></span>  
  
- [<span data-ttu-id="c3e7f-126">Odbicie</span><span class="sxs-lookup"><span data-stu-id="c3e7f-126">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)  
  
- [<span data-ttu-id="c3e7f-127">Wyświetlanie informacji o typie</span><span class="sxs-lookup"><span data-stu-id="c3e7f-127">Viewing Type Information</span></span>](../../../framework/reflection-and-codedom/viewing-type-information.md)  
  
- [<span data-ttu-id="c3e7f-128">Odbicie i typy ogólne</span><span class="sxs-lookup"><span data-stu-id="c3e7f-128">Reflection and Generic Types</span></span>](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
  
- <xref:System.Reflection.Emit>  
  
- [<span data-ttu-id="c3e7f-129">Pobieranie informacji przechowywanych w atrybutach</span><span class="sxs-lookup"><span data-stu-id="c3e7f-129">Retrieving Information Stored in Attributes</span></span>](../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
  
## <a name="see-also"></a><span data-ttu-id="c3e7f-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c3e7f-130">See also</span></span>

- [<span data-ttu-id="c3e7f-131">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c3e7f-131">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="c3e7f-132">Zestawy w środowisku .NET</span><span class="sxs-lookup"><span data-stu-id="c3e7f-132">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
