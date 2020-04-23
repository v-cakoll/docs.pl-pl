---
title: 'Porady: ładowanie zestawów do kontekstu Reflection-Only'
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
ms.openlocfilehash: cac6b3b3adf070ad6070e5c5941653f20dedd907
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130103"
---
# <a name="how-to-load-assemblies-into-the-reflection-only-context"></a><span data-ttu-id="3750d-102">Porady: ładowanie zestawów do kontekstu Reflection-Only</span><span class="sxs-lookup"><span data-stu-id="3750d-102">How to: Load Assemblies into the Reflection-Only Context</span></span>

<span data-ttu-id="3750d-103">Kontekst ładowania tylko odbicie umożliwia badanie zestawów skompilowanych dla innych platform lub dla innych wersji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3750d-103">The reflection-only load context allows you to examine assemblies compiled for other platforms or for other versions of the .NET Framework.</span></span> <span data-ttu-id="3750d-104">Kod załadowany do tego kontekstu może być badany tylko; nie można go wykonać.</span><span class="sxs-lookup"><span data-stu-id="3750d-104">Code loaded into this context can only be examined; it cannot be executed.</span></span> <span data-ttu-id="3750d-105">Oznacza to, że nie można tworzyć obiektów, ponieważ nie można wykonać konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="3750d-105">This means that objects cannot be created, because constructors cannot be executed.</span></span> <span data-ttu-id="3750d-106">Ponieważ kod nie może zostać wykonany, zależności nie są ładowane automatycznie.</span><span class="sxs-lookup"><span data-stu-id="3750d-106">Because the code cannot be executed, dependencies are not automatically loaded.</span></span> <span data-ttu-id="3750d-107">Jeśli musisz je przeanalizować, musisz załadować je samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="3750d-107">If you need to examine them, you must load them yourself.</span></span>

## <a name="to-load-an-assembly-into-the-reflection-only-load-context"></a><span data-ttu-id="3750d-108">Aby załadować zestaw do kontekstu ładowania tylko odbicie</span><span class="sxs-lookup"><span data-stu-id="3750d-108">To load an assembly into the reflection-only load context</span></span>

1. <span data-ttu-id="3750d-109">Użyj przeciążenia <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.String%29> metody, aby załadować zestaw przy użyciu jego nazwy wyświetlanej, lub <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> metodę ładowania zestawu przy użyciu jej ścieżki.</span><span class="sxs-lookup"><span data-stu-id="3750d-109">Use the <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.String%29> method overload to load the assembly given its display name, or the <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> method to load the assembly given its path.</span></span> <span data-ttu-id="3750d-110">Jeśli zestaw jest obrazem binarnym, Użyj przeciążenia <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.Byte%5B%5D%29> metody.</span><span class="sxs-lookup"><span data-stu-id="3750d-110">If the assembly is a binary image, use the <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.Byte%5B%5D%29> method overload.</span></span>

    > [!NOTE]
    > <span data-ttu-id="3750d-111">Nie można użyć kontekstu tylko odbicia do załadowania wersji biblioteki mscorlib. dll z wersji .NET Framework innej niż wersja w kontekście wykonania.</span><span class="sxs-lookup"><span data-stu-id="3750d-111">You cannot use the reflection-only context to load a version of mscorlib.dll from a version of the .NET Framework other than the version in the execution context.</span></span>

2. <span data-ttu-id="3750d-112">Jeśli zestaw ma zależności, <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> Metoda nie ładuje ich.</span><span class="sxs-lookup"><span data-stu-id="3750d-112">If the assembly has dependencies, the <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> method does not load them.</span></span> <span data-ttu-id="3750d-113">Jeśli musisz je przeanalizować, musisz załadować je samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="3750d-113">If you need to examine them, you must load them yourself.</span></span>

3. <span data-ttu-id="3750d-114">Ustal, czy zestaw jest ładowany do kontekstu tylko odbicie przy użyciu <xref:System.Reflection.Assembly.ReflectionOnly%2A> właściwości zestawu.</span><span class="sxs-lookup"><span data-stu-id="3750d-114">Determine whether an assembly is loaded into the reflection-only context by using the assembly's <xref:System.Reflection.Assembly.ReflectionOnly%2A> property.</span></span>

4. <span data-ttu-id="3750d-115">Jeśli atrybuty zostały zastosowane do zestawu lub do typów w zestawie, sprawdź te atrybuty przy użyciu <xref:System.Reflection.CustomAttributeData> klasy, aby upewnić się, że nie podjęto próby wykonania kodu w kontekście "tylko odbicie".</span><span class="sxs-lookup"><span data-stu-id="3750d-115">If attributes have been applied to the assembly or to types in the assembly, examine those attributes by using the <xref:System.Reflection.CustomAttributeData> class to ensure that no attempt is made to execute code in the reflection-only context.</span></span> <span data-ttu-id="3750d-116">Użyj odpowiedniego przeciążenia <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> metody w celu uzyskania <xref:System.Reflection.CustomAttributeData> obiektów reprezentujących atrybuty zastosowane do zestawu, elementu członkowskiego, modułu lub parametru.</span><span class="sxs-lookup"><span data-stu-id="3750d-116">Use the appropriate overload of the <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> method to obtain <xref:System.Reflection.CustomAttributeData> objects representing the attributes applied to an assembly, member, module, or parameter.</span></span>

    > [!NOTE]
    > <span data-ttu-id="3750d-117">Atrybuty zastosowane do zestawu lub jego zawartości mogą być zdefiniowane w zestawie lub mogą być zdefiniowane w innym zestawie załadowanym do kontekstu tylko odbicie.</span><span class="sxs-lookup"><span data-stu-id="3750d-117">Attributes applied to the assembly or to its contents might be defined in the assembly, or they might be defined in another assembly loaded into the reflection-only context.</span></span> <span data-ttu-id="3750d-118">Nie ma możliwości poinformowania z wyprzedzeniem o zdefiniowaniu atrybutów.</span><span class="sxs-lookup"><span data-stu-id="3750d-118">There is no way to tell in advance where the attributes are defined.</span></span>

## <a name="example"></a><span data-ttu-id="3750d-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="3750d-119">Example</span></span>

<span data-ttu-id="3750d-120">Poniższy przykład kodu pokazuje, jak sprawdzać atrybuty zastosowane do zestawu załadowanego do kontekstu tylko odbicie.</span><span class="sxs-lookup"><span data-stu-id="3750d-120">The following code example shows how to examine the attributes applied to an assembly loaded into the reflection-only context.</span></span>

<span data-ttu-id="3750d-121">Przykładowy kod definiuje atrybut niestandardowy z dwoma konstruktorami i jedną właściwością.</span><span class="sxs-lookup"><span data-stu-id="3750d-121">The code example defines a custom attribute with two constructors and one property.</span></span> <span data-ttu-id="3750d-122">Ten atrybut jest stosowany do zestawu, do typu zadeklarowanego w zestawie, do metody typu i do parametru metody.</span><span class="sxs-lookup"><span data-stu-id="3750d-122">The attribute is applied to the assembly, to a type declared in the assembly, to a method of the type, and to a parameter of the method.</span></span> <span data-ttu-id="3750d-123">Po wykonaniu zestaw ładuje się do kontekstu tylko odbicia i wyświetla informacje o niestandardowych atrybutach, które zostały zastosowane do niego, oraz do typów i składowych, które zawiera.</span><span class="sxs-lookup"><span data-stu-id="3750d-123">When executed, the assembly loads itself into the reflection-only context and displays information about the custom attributes that were applied to it and to the types and members it contains.</span></span>

> [!NOTE]
> <span data-ttu-id="3750d-124">Aby uprościć przykład kodu, zestaw ładuje i sprawdza siebie.</span><span class="sxs-lookup"><span data-stu-id="3750d-124">To simplify the code example, the assembly loads and examines itself.</span></span> <span data-ttu-id="3750d-125">Zwykle nie oczekuje się, że ten sam zestaw został załadowany do zarówno kontekstu wykonywania, jak i kontekstu tylko odbicie.</span><span class="sxs-lookup"><span data-stu-id="3750d-125">Normally, you would not expect to find the same assembly loaded into both the execution context and the reflection-only context.</span></span>

[!code-cpp[CustomAttributeData#1](../../../samples/snippets/cpp/VS_Snippets_CLR/CustomAttributeData/CPP/source.cpp#1)]
[!code-csharp[CustomAttributeData#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CustomAttributeData/CS/source.cs#1)]
[!code-vb[CustomAttributeData#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CustomAttributeData/VB/source.vb#1)]

## <a name="see-also"></a><span data-ttu-id="3750d-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3750d-126">See also</span></span>

- <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>
- <xref:System.Reflection.Assembly.ReflectionOnly%2A>
- <xref:System.Reflection.CustomAttributeData>
