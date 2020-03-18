---
title: Odbicie (C#)
ms.date: 07/20/2015
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
ms.openlocfilehash: a56fb24b63e4d80dbb67b079466b67cd11672023
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74711662"
---
# <a name="reflection-c"></a><span data-ttu-id="b2149-102">Odbicie (C#)</span><span class="sxs-lookup"><span data-stu-id="b2149-102">Reflection (C#)</span></span>

<span data-ttu-id="b2149-103">Odbicie zapewnia obiekty <xref:System.Type>(typu), które opisują zespoły, moduły i typy.</span><span class="sxs-lookup"><span data-stu-id="b2149-103">Reflection provides objects (of type <xref:System.Type>) that describe assemblies, modules, and types.</span></span> <span data-ttu-id="b2149-104">Odbicie można użyć do dynamicznego utworzenia wystąpienia typu, powiązać typ z istniejącym obiektem lub uzyskać typ z istniejącego obiektu i wywołać jego metody lub uzyskać dostęp do jego pól i właściwości.</span><span class="sxs-lookup"><span data-stu-id="b2149-104">You can use reflection to dynamically create an instance of a type, bind the type to an existing object, or get the type from an existing object and invoke its methods or access its fields and properties.</span></span> <span data-ttu-id="b2149-105">Jeśli używasz atrybutów w kodzie, odbicie umożliwia dostęp do nich.</span><span class="sxs-lookup"><span data-stu-id="b2149-105">If you are using attributes in your code, reflection enables you to access them.</span></span> <span data-ttu-id="b2149-106">Aby uzyskać więcej informacji, zobacz [Atrybuty](../../../standard/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="b2149-106">For more information, see [Attributes](../../../standard/attributes/index.md).</span></span>

<span data-ttu-id="b2149-107">Oto prosty przykład odbicia przy <xref:System.Object.GetType> użyciu metody - dziedziczone `Object` przez wszystkie typy z klasy podstawowej - w celu uzyskania typu zmiennej:</span><span class="sxs-lookup"><span data-stu-id="b2149-107">Here's a simple example of reflection using the <xref:System.Object.GetType> method - inherited by all types from the `Object` base class - to obtain the type of a variable:</span></span>

> [!NOTE]
> <span data-ttu-id="b2149-108">Upewnij się, `using System;` `using System.Reflection;` że dodajesz i jesteś na górze pliku *.cs.*</span><span class="sxs-lookup"><span data-stu-id="b2149-108">Make sure you add `using System;` and `using System.Reflection;` at the top of your *.cs* file.</span></span>

```csharp
// Using GetType to obtain type information:
int i = 42;
Type type = i.GetType();
Console.WriteLine(type);
```

<span data-ttu-id="b2149-109">Wyjście to: `System.Int32`.</span><span class="sxs-lookup"><span data-stu-id="b2149-109">The output is: `System.Int32`.</span></span>

<span data-ttu-id="b2149-110">W poniższym przykładzie użyto odbicia w celu uzyskania pełnej nazwy załadowanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="b2149-110">The following example uses reflection to obtain the full name of the loaded assembly.</span></span>

```csharp
// Using Reflection to get information of an Assembly:
Assembly info = typeof(int).Assembly;
Console.WriteLine(info);
```

<span data-ttu-id="b2149-111">Wyjście to: `System.Private.CoreLib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=7cec85d7bea7798e`.</span><span class="sxs-lookup"><span data-stu-id="b2149-111">The output is: `System.Private.CoreLib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=7cec85d7bea7798e`.</span></span>

> [!NOTE]
> <span data-ttu-id="b2149-112">C# słowa `protected` kluczowe `internal` i nie mają znaczenia w IL i nie są używane w interfejsach API odbicia.</span><span class="sxs-lookup"><span data-stu-id="b2149-112">The C# keywords `protected` and `internal` have no meaning in IL and are not used in the reflection APIs.</span></span> <span data-ttu-id="b2149-113">Odpowiednie terminy w IL to *Rodzina* i *Montaż.*</span><span class="sxs-lookup"><span data-stu-id="b2149-113">The corresponding terms in IL are *Family* and *Assembly*.</span></span> <span data-ttu-id="b2149-114">Aby zidentyfikować `internal` metodę przy <xref:System.Reflection.MethodBase.IsAssembly%2A> użyciu odbicia, należy użyć właściwości.</span><span class="sxs-lookup"><span data-stu-id="b2149-114">To identify an `internal` method using reflection, use the <xref:System.Reflection.MethodBase.IsAssembly%2A> property.</span></span> <span data-ttu-id="b2149-115">Aby zidentyfikować `protected internal` metodę, <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>należy użyć pliku .</span><span class="sxs-lookup"><span data-stu-id="b2149-115">To identify a `protected internal` method, use the <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.</span></span>

## <a name="reflection-overview"></a><span data-ttu-id="b2149-116">Przegląd refleksji</span><span class="sxs-lookup"><span data-stu-id="b2149-116">Reflection overview</span></span>

<span data-ttu-id="b2149-117">Odbicie jest przydatne w następujących sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="b2149-117">Reflection is useful in the following situations:</span></span>

- <span data-ttu-id="b2149-118">Gdy trzeba uzyskać dostęp do atrybutów w metadanych programu.</span><span class="sxs-lookup"><span data-stu-id="b2149-118">When you have to access attributes in your program's metadata.</span></span> <span data-ttu-id="b2149-119">Aby uzyskać więcej informacji, zobacz [Pobieranie informacji przechowywanych w atrybutach](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="b2149-119">For more information, see [Retrieving Information Stored in Attributes](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span></span>
- <span data-ttu-id="b2149-120">Do badania i tworzenia wystąpień typów w zestawie.</span><span class="sxs-lookup"><span data-stu-id="b2149-120">For examining and instantiating types in an assembly.</span></span>
- <span data-ttu-id="b2149-121">Do tworzenia nowych typów w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="b2149-121">For building new types at runtime.</span></span> <span data-ttu-id="b2149-122">Użyj klas <xref:System.Reflection.Emit>w .</span><span class="sxs-lookup"><span data-stu-id="b2149-122">Use classes in <xref:System.Reflection.Emit>.</span></span>
- <span data-ttu-id="b2149-123">Do wykonywania późnego wiązania, uzyskiwanie dostępu do metod na typy utworzone w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="b2149-123">For performing late binding, accessing methods on types created at run time.</span></span> <span data-ttu-id="b2149-124">Zobacz temat [Dynamiczne ładowanie i używanie typów](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span><span class="sxs-lookup"><span data-stu-id="b2149-124">See the topic [Dynamically Loading and Using Types](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>

## <a name="related-sections"></a><span data-ttu-id="b2149-125">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="b2149-125">Related sections</span></span>

<span data-ttu-id="b2149-126">Więcej informacji:</span><span class="sxs-lookup"><span data-stu-id="b2149-126">For more information:</span></span>

- [<span data-ttu-id="b2149-127">Odbicie</span><span class="sxs-lookup"><span data-stu-id="b2149-127">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)
- [<span data-ttu-id="b2149-128">Wyświetlanie informacji o typie</span><span class="sxs-lookup"><span data-stu-id="b2149-128">Viewing Type Information</span></span>](../../../framework/reflection-and-codedom/viewing-type-information.md)
- [<span data-ttu-id="b2149-129">Odbicie i typy ogólne</span><span class="sxs-lookup"><span data-stu-id="b2149-129">Reflection and Generic Types</span></span>](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)
- <xref:System.Reflection.Emit>
- [<span data-ttu-id="b2149-130">Pobieranie informacji przechowywanych w atrybutach</span><span class="sxs-lookup"><span data-stu-id="b2149-130">Retrieving Information Stored in Attributes</span></span>](../../../standard/attributes/retrieving-information-stored-in-attributes.md)

## <a name="see-also"></a><span data-ttu-id="b2149-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b2149-131">See also</span></span>

- [<span data-ttu-id="b2149-132">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="b2149-132">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b2149-133">Zestawy w środowisku .NET</span><span class="sxs-lookup"><span data-stu-id="b2149-133">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
