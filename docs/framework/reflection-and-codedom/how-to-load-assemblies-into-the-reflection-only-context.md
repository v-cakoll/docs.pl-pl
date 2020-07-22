---
title: 'Instrukcje: Ładowanie zestawów do kontekstu Reflection-Only'
description: Zapoznaj się z przykładem ładowania zestawów do kontekstu tylko odbicie w programie .NET. Należy zapoznać się z zestawami skompilowanymi dla innych platform lub wersji platformy .NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reflection, reflection-only loader context
- assemblies [.NET Framework], loading for reflection
- attributes [.NET Framework], retrieving
- assemblies [.NET Framework], reflection-only loader context
- reflection-only loader context
ms.assetid: 9818b660-52f5-423d-a9af-e75163aa7068
ms.openlocfilehash: 92f847f6c61ba39bf8621af6080baccfdabe514a
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865076"
---
# <a name="how-to-load-assemblies-into-the-reflection-only-context"></a><span data-ttu-id="14878-104">Instrukcje: Ładowanie zestawów do kontekstu Reflection-Only</span><span class="sxs-lookup"><span data-stu-id="14878-104">How to: Load Assemblies into the Reflection-Only Context</span></span>

<span data-ttu-id="14878-105">Kontekst ładowania tylko odbicie umożliwia badanie zestawów skompilowanych dla innych platform lub dla innych wersji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="14878-105">The reflection-only load context allows you to examine assemblies compiled for other platforms or for other versions of the .NET Framework.</span></span> <span data-ttu-id="14878-106">Kod załadowany do tego kontekstu może być badany tylko; nie można go wykonać.</span><span class="sxs-lookup"><span data-stu-id="14878-106">Code loaded into this context can only be examined; it cannot be executed.</span></span> <span data-ttu-id="14878-107">Oznacza to, że nie można tworzyć obiektów, ponieważ nie można wykonać konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="14878-107">This means that objects cannot be created, because constructors cannot be executed.</span></span> <span data-ttu-id="14878-108">Ponieważ kod nie może zostać wykonany, zależności nie są ładowane automatycznie.</span><span class="sxs-lookup"><span data-stu-id="14878-108">Because the code cannot be executed, dependencies are not automatically loaded.</span></span> <span data-ttu-id="14878-109">Jeśli musisz je przeanalizować, musisz załadować je samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="14878-109">If you need to examine them, you must load them yourself.</span></span>

## <a name="to-load-an-assembly-into-the-reflection-only-load-context"></a><span data-ttu-id="14878-110">Aby załadować zestaw do kontekstu ładowania tylko odbicie</span><span class="sxs-lookup"><span data-stu-id="14878-110">To load an assembly into the reflection-only load context</span></span>

1. <span data-ttu-id="14878-111">Użyj <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.String%29> przeciążenia metody, aby załadować zestaw przy użyciu jego nazwy wyświetlanej, lub <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> metodę ładowania zestawu przy użyciu jej ścieżki.</span><span class="sxs-lookup"><span data-stu-id="14878-111">Use the <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.String%29> method overload to load the assembly given its display name, or the <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> method to load the assembly given its path.</span></span> <span data-ttu-id="14878-112">Jeśli zestaw jest obrazem binarnym, użyj <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.Byte%5B%5D%29> przeciążenia metody.</span><span class="sxs-lookup"><span data-stu-id="14878-112">If the assembly is a binary image, use the <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.Byte%5B%5D%29> method overload.</span></span>

    > [!NOTE]
    > <span data-ttu-id="14878-113">Nie można użyć kontekstu tylko odbicia do załadowania wersji mscorlib.dll z wersji .NET Framework innej niż wersja w kontekście wykonania.</span><span class="sxs-lookup"><span data-stu-id="14878-113">You cannot use the reflection-only context to load a version of mscorlib.dll from a version of the .NET Framework other than the version in the execution context.</span></span>

2. <span data-ttu-id="14878-114">Jeśli zestaw ma zależności, metoda nie <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> ładuje ich.</span><span class="sxs-lookup"><span data-stu-id="14878-114">If the assembly has dependencies, the <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> method does not load them.</span></span> <span data-ttu-id="14878-115">Jeśli musisz je przeanalizować, musisz załadować je samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="14878-115">If you need to examine them, you must load them yourself.</span></span>

3. <span data-ttu-id="14878-116">Ustal, czy zestaw jest ładowany do kontekstu tylko odbicie przy użyciu <xref:System.Reflection.Assembly.ReflectionOnly%2A> Właściwości zestawu.</span><span class="sxs-lookup"><span data-stu-id="14878-116">Determine whether an assembly is loaded into the reflection-only context by using the assembly's <xref:System.Reflection.Assembly.ReflectionOnly%2A> property.</span></span>

4. <span data-ttu-id="14878-117">Jeśli atrybuty zostały zastosowane do zestawu lub do typów w zestawie, sprawdź te atrybuty przy użyciu <xref:System.Reflection.CustomAttributeData> klasy, aby upewnić się, że nie podjęto próby wykonania kodu w kontekście "tylko odbicie".</span><span class="sxs-lookup"><span data-stu-id="14878-117">If attributes have been applied to the assembly or to types in the assembly, examine those attributes by using the <xref:System.Reflection.CustomAttributeData> class to ensure that no attempt is made to execute code in the reflection-only context.</span></span> <span data-ttu-id="14878-118">Użyj odpowiedniego przeciążenia <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> metody w celu uzyskania <xref:System.Reflection.CustomAttributeData> obiektów reprezentujących atrybuty zastosowane do zestawu, elementu członkowskiego, modułu lub parametru.</span><span class="sxs-lookup"><span data-stu-id="14878-118">Use the appropriate overload of the <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> method to obtain <xref:System.Reflection.CustomAttributeData> objects representing the attributes applied to an assembly, member, module, or parameter.</span></span>

    > [!NOTE]
    > <span data-ttu-id="14878-119">Atrybuty zastosowane do zestawu lub jego zawartości mogą być zdefiniowane w zestawie lub mogą być zdefiniowane w innym zestawie załadowanym do kontekstu tylko odbicie.</span><span class="sxs-lookup"><span data-stu-id="14878-119">Attributes applied to the assembly or to its contents might be defined in the assembly, or they might be defined in another assembly loaded into the reflection-only context.</span></span> <span data-ttu-id="14878-120">Nie ma możliwości poinformowania z wyprzedzeniem o zdefiniowaniu atrybutów.</span><span class="sxs-lookup"><span data-stu-id="14878-120">There is no way to tell in advance where the attributes are defined.</span></span>

## <a name="example"></a><span data-ttu-id="14878-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="14878-121">Example</span></span>

<span data-ttu-id="14878-122">Poniższy przykład kodu pokazuje, jak sprawdzać atrybuty zastosowane do zestawu załadowanego do kontekstu tylko odbicie.</span><span class="sxs-lookup"><span data-stu-id="14878-122">The following code example shows how to examine the attributes applied to an assembly loaded into the reflection-only context.</span></span>

<span data-ttu-id="14878-123">Przykładowy kod definiuje atrybut niestandardowy z dwoma konstruktorami i jedną właściwością.</span><span class="sxs-lookup"><span data-stu-id="14878-123">The code example defines a custom attribute with two constructors and one property.</span></span> <span data-ttu-id="14878-124">Ten atrybut jest stosowany do zestawu, do typu zadeklarowanego w zestawie, do metody typu i do parametru metody.</span><span class="sxs-lookup"><span data-stu-id="14878-124">The attribute is applied to the assembly, to a type declared in the assembly, to a method of the type, and to a parameter of the method.</span></span> <span data-ttu-id="14878-125">Po wykonaniu zestaw ładuje się do kontekstu tylko odbicia i wyświetla informacje o niestandardowych atrybutach, które zostały zastosowane do niego, oraz do typów i składowych, które zawiera.</span><span class="sxs-lookup"><span data-stu-id="14878-125">When executed, the assembly loads itself into the reflection-only context and displays information about the custom attributes that were applied to it and to the types and members it contains.</span></span>

> [!NOTE]
> <span data-ttu-id="14878-126">Aby uprościć przykład kodu, zestaw ładuje i sprawdza siebie.</span><span class="sxs-lookup"><span data-stu-id="14878-126">To simplify the code example, the assembly loads and examines itself.</span></span> <span data-ttu-id="14878-127">Zwykle nie oczekuje się, że ten sam zestaw został załadowany do zarówno kontekstu wykonywania, jak i kontekstu tylko odbicie.</span><span class="sxs-lookup"><span data-stu-id="14878-127">Normally, you would not expect to find the same assembly loaded into both the execution context and the reflection-only context.</span></span>

[!code-cpp[CustomAttributeData#1](../../../samples/snippets/cpp/VS_Snippets_CLR/CustomAttributeData/CPP/source.cpp#1)]
[!code-csharp[CustomAttributeData#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CustomAttributeData/CS/source.cs#1)]
[!code-vb[CustomAttributeData#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CustomAttributeData/VB/source.vb#1)]

## <a name="see-also"></a><span data-ttu-id="14878-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="14878-128">See also</span></span>

- <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>
- <xref:System.Reflection.Assembly.ReflectionOnly%2A>
- <xref:System.Reflection.CustomAttributeData>
