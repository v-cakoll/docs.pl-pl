---
title: OdbicieC#()
ms.date: 07/20/2015
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
ms.openlocfilehash: a56fb24b63e4d80dbb67b079466b67cd11672023
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711662"
---
# <a name="reflection-c"></a><span data-ttu-id="f176c-102">OdbicieC#()</span><span class="sxs-lookup"><span data-stu-id="f176c-102">Reflection (C#)</span></span>

<span data-ttu-id="f176c-103">Odbicie udostępnia obiekty (typu <xref:System.Type>) opisujące zestawy, moduły i typy.</span><span class="sxs-lookup"><span data-stu-id="f176c-103">Reflection provides objects (of type <xref:System.Type>) that describe assemblies, modules, and types.</span></span> <span data-ttu-id="f176c-104">Możesz użyć odbicia, aby dynamicznie utworzyć wystąpienie typu, powiązać typ z istniejącym obiektem lub uzyskać typ z istniejącego obiektu i wywołać jego metody lub uzyskać dostęp do jego pól i właściwości.</span><span class="sxs-lookup"><span data-stu-id="f176c-104">You can use reflection to dynamically create an instance of a type, bind the type to an existing object, or get the type from an existing object and invoke its methods or access its fields and properties.</span></span> <span data-ttu-id="f176c-105">Jeśli używasz atrybutów w kodzie, odbicie umożliwia uzyskanie dostępu do nich.</span><span class="sxs-lookup"><span data-stu-id="f176c-105">If you are using attributes in your code, reflection enables you to access them.</span></span> <span data-ttu-id="f176c-106">Aby uzyskać więcej informacji, zobacz [atrybuty](../../../standard/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="f176c-106">For more information, see [Attributes](../../../standard/attributes/index.md).</span></span>

<span data-ttu-id="f176c-107">Oto prosty przykład odbicia przy użyciu metody <xref:System.Object.GetType> dziedziczonej przez wszystkie typy z klasy podstawowej `Object` — Aby uzyskać typ zmiennej:</span><span class="sxs-lookup"><span data-stu-id="f176c-107">Here's a simple example of reflection using the <xref:System.Object.GetType> method - inherited by all types from the `Object` base class - to obtain the type of a variable:</span></span>

> [!NOTE]
> <span data-ttu-id="f176c-108">Upewnij się, że dodano `using System;` i `using System.Reflection;` w górnej części pliku *. cs* .</span><span class="sxs-lookup"><span data-stu-id="f176c-108">Make sure you add `using System;` and `using System.Reflection;` at the top of your *.cs* file.</span></span>

```csharp
// Using GetType to obtain type information:
int i = 42;
Type type = i.GetType();
Console.WriteLine(type);
```

<span data-ttu-id="f176c-109">Dane wyjściowe to: `System.Int32`.</span><span class="sxs-lookup"><span data-stu-id="f176c-109">The output is: `System.Int32`.</span></span>

<span data-ttu-id="f176c-110">Poniższy przykład używa odbicia w celu uzyskania pełnej nazwy załadowanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="f176c-110">The following example uses reflection to obtain the full name of the loaded assembly.</span></span>

```csharp
// Using Reflection to get information of an Assembly:
Assembly info = typeof(int).Assembly;
Console.WriteLine(info);
```

<span data-ttu-id="f176c-111">Dane wyjściowe to: `System.Private.CoreLib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=7cec85d7bea7798e`.</span><span class="sxs-lookup"><span data-stu-id="f176c-111">The output is: `System.Private.CoreLib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=7cec85d7bea7798e`.</span></span>

> [!NOTE]
> <span data-ttu-id="f176c-112">C# Słowa kluczowe `protected` i `internal` nie mają znaczenia w Il i nie są używane w interfejsach API odbicia.</span><span class="sxs-lookup"><span data-stu-id="f176c-112">The C# keywords `protected` and `internal` have no meaning in IL and are not used in the reflection APIs.</span></span> <span data-ttu-id="f176c-113">Odpowiednie warunki w IL są *rodziną* i *zestawem*.</span><span class="sxs-lookup"><span data-stu-id="f176c-113">The corresponding terms in IL are *Family* and *Assembly*.</span></span> <span data-ttu-id="f176c-114">Aby zidentyfikować metodę `internal` przy użyciu odbicia, należy użyć właściwości <xref:System.Reflection.MethodBase.IsAssembly%2A>.</span><span class="sxs-lookup"><span data-stu-id="f176c-114">To identify an `internal` method using reflection, use the <xref:System.Reflection.MethodBase.IsAssembly%2A> property.</span></span> <span data-ttu-id="f176c-115">Aby zidentyfikować metodę `protected internal`, użyj <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.</span><span class="sxs-lookup"><span data-stu-id="f176c-115">To identify a `protected internal` method, use the <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.</span></span>

## <a name="reflection-overview"></a><span data-ttu-id="f176c-116">Przegląd odbicia</span><span class="sxs-lookup"><span data-stu-id="f176c-116">Reflection overview</span></span>

<span data-ttu-id="f176c-117">Odbicie jest przydatne w następujących sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="f176c-117">Reflection is useful in the following situations:</span></span>

- <span data-ttu-id="f176c-118">Gdy musisz uzyskać dostęp do atrybutów w metadanych programu.</span><span class="sxs-lookup"><span data-stu-id="f176c-118">When you have to access attributes in your program's metadata.</span></span> <span data-ttu-id="f176c-119">Aby uzyskać więcej informacji, zobacz artykuł [pobieranie informacji przechowywanych w atrybutach](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="f176c-119">For more information, see [Retrieving Information Stored in Attributes](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span></span>
- <span data-ttu-id="f176c-120">Do badania i tworzenia wystąpień typów w zestawie.</span><span class="sxs-lookup"><span data-stu-id="f176c-120">For examining and instantiating types in an assembly.</span></span>
- <span data-ttu-id="f176c-121">Do kompilowania nowych typów w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="f176c-121">For building new types at runtime.</span></span> <span data-ttu-id="f176c-122">Użyj klas w <xref:System.Reflection.Emit>.</span><span class="sxs-lookup"><span data-stu-id="f176c-122">Use classes in <xref:System.Reflection.Emit>.</span></span>
- <span data-ttu-id="f176c-123">Do wykonywania późnego wiązania, uzyskiwanie dostępu do metod w typach utworzonych w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="f176c-123">For performing late binding, accessing methods on types created at run time.</span></span> <span data-ttu-id="f176c-124">Zobacz temat [dynamiczne ładowanie i używanie typów](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span><span class="sxs-lookup"><span data-stu-id="f176c-124">See the topic [Dynamically Loading and Using Types](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>

## <a name="related-sections"></a><span data-ttu-id="f176c-125">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="f176c-125">Related sections</span></span>

<span data-ttu-id="f176c-126">Informacje dodatkowe:</span><span class="sxs-lookup"><span data-stu-id="f176c-126">For more information:</span></span>

- [<span data-ttu-id="f176c-127">Odbicie</span><span class="sxs-lookup"><span data-stu-id="f176c-127">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)
- [<span data-ttu-id="f176c-128">Wyświetlanie informacji o typie</span><span class="sxs-lookup"><span data-stu-id="f176c-128">Viewing Type Information</span></span>](../../../framework/reflection-and-codedom/viewing-type-information.md)
- [<span data-ttu-id="f176c-129">Odbicie i typy ogólne</span><span class="sxs-lookup"><span data-stu-id="f176c-129">Reflection and Generic Types</span></span>](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)
- <xref:System.Reflection.Emit>
- [<span data-ttu-id="f176c-130">Pobieranie informacji przechowywanych w atrybutach</span><span class="sxs-lookup"><span data-stu-id="f176c-130">Retrieving Information Stored in Attributes</span></span>](../../../standard/attributes/retrieving-information-stored-in-attributes.md)

## <a name="see-also"></a><span data-ttu-id="f176c-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f176c-131">See also</span></span>

- [<span data-ttu-id="f176c-132">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="f176c-132">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="f176c-133">Zestawy w środowisku .NET</span><span class="sxs-lookup"><span data-stu-id="f176c-133">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
