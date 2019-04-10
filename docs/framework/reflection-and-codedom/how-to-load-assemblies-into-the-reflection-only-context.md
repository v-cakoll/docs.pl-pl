---
title: 'Instrukcje: Ładowanie zestawów do kontekstu Reflection-Only'
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8dc05d27b0316c82c5314a766fcad929dc5f3698
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59331055"
---
# <a name="how-to-load-assemblies-into-the-reflection-only-context"></a><span data-ttu-id="a6dff-102">Instrukcje: Ładowanie zestawów do kontekstu Reflection-Only</span><span class="sxs-lookup"><span data-stu-id="a6dff-102">How to: Load Assemblies into the Reflection-Only Context</span></span>
<span data-ttu-id="a6dff-103">Kontekst ładowania tylko odbicie umożliwia analizowanie zestawy skompilowane dla innych platform lub w przypadku innych wersji systemu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a6dff-103">The reflection-only load context allows you to examine assemblies compiled for other platforms or for other versions of the .NET Framework.</span></span> <span data-ttu-id="a6dff-104">Tylko można zbadać kodu załadowanego w tym kontekście; Nie można wykonać.</span><span class="sxs-lookup"><span data-stu-id="a6dff-104">Code loaded into this context can only be examined; it cannot be executed.</span></span> <span data-ttu-id="a6dff-105">Oznacza to, że nie można utworzyć obiektów, ponieważ nie można wykonać konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="a6dff-105">This means that objects cannot be created, because constructors cannot be executed.</span></span> <span data-ttu-id="a6dff-106">Ponieważ nie można wykonać kod, zależności nie są ładowane automatycznie.</span><span class="sxs-lookup"><span data-stu-id="a6dff-106">Because the code cannot be executed, dependencies are not automatically loaded.</span></span> <span data-ttu-id="a6dff-107">Jeśli musisz zbadać je, należy załadować je samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="a6dff-107">If you need to examine them, you must load them yourself.</span></span>  
  
### <a name="to-load-an-assembly-into-the-reflection-only-load-context"></a><span data-ttu-id="a6dff-108">Ładowanie zestawów do kontekstu ładowania tylko odbicie</span><span class="sxs-lookup"><span data-stu-id="a6dff-108">To load an assembly into the reflection-only load context</span></span>  
  
1. <span data-ttu-id="a6dff-109">Użyj <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.String%29> przeciążenia metody, aby załadować zestawu, biorąc pod uwagę jego nazwę wyświetlaną lub <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> metodę, aby załadować zestaw podanej ścieżce.</span><span class="sxs-lookup"><span data-stu-id="a6dff-109">Use the <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.String%29> method overload to load the assembly given its display name, or the <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> method to load the assembly given its path.</span></span> <span data-ttu-id="a6dff-110">Jeśli zestaw jest obrazem binarnym, użyj <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.Byte%5B%5D%29> przeciążenie metody.</span><span class="sxs-lookup"><span data-stu-id="a6dff-110">If the assembly is a binary image, use the <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.Byte%5B%5D%29> method overload.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a6dff-111">Za pomocą kontekstu reflection-only nie można załadować wersji biblioteki mscorlib.dll z wersji programu .NET Framework niż wersja w kontekście wykonywania.</span><span class="sxs-lookup"><span data-stu-id="a6dff-111">You cannot use the reflection-only context to load a version of mscorlib.dll from a version of the .NET Framework other than the version in the execution context.</span></span>  
  
2. <span data-ttu-id="a6dff-112">Jeśli zestaw ma zależności, <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> metoda nie ładuje je.</span><span class="sxs-lookup"><span data-stu-id="a6dff-112">If the assembly has dependencies, the <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> method does not load them.</span></span> <span data-ttu-id="a6dff-113">Jeśli musisz zbadać je, należy załadować je samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="a6dff-113">If you need to examine them, you must load them yourself.</span></span>  
  
3. <span data-ttu-id="a6dff-114">Ustal, czy zestaw jest ładowany do kontekstu reflection-only przy użyciu zestawu <xref:System.Reflection.Assembly.ReflectionOnly%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="a6dff-114">Determine whether an assembly is loaded into the reflection-only context by using the assembly's <xref:System.Reflection.Assembly.ReflectionOnly%2A> property.</span></span>  
  
4. <span data-ttu-id="a6dff-115">Jeśli atrybuty zostały zastosowane do zestawu lub typów w zestawie, należy zbadać te atrybuty, używając <xref:System.Reflection.CustomAttributeData> klasy, aby upewnić się, że nie są podejmowane próby wykonania kodu w kontekstu reflection-only.</span><span class="sxs-lookup"><span data-stu-id="a6dff-115">If attributes have been applied to the assembly or to types in the assembly, examine those attributes by using the <xref:System.Reflection.CustomAttributeData> class to ensure that no attempt is made to execute code in the reflection-only context.</span></span> <span data-ttu-id="a6dff-116">Użyj odpowiedniego przeciążenia <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> metodę, aby uzyskać <xref:System.Reflection.CustomAttributeData> obiektów reprezentujących atrybuty stosowane do zestawu, elementu członkowskiego, modułu lub parametr.</span><span class="sxs-lookup"><span data-stu-id="a6dff-116">Use the appropriate overload of the <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> method to obtain <xref:System.Reflection.CustomAttributeData> objects representing the attributes applied to an assembly, member, module, or parameter.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a6dff-117">Atrybuty stosowane do zestawu lub jego zawartość może być zdefiniowane w zestawie lub może być zdefiniowana w innym zestawie ładowane do kontekstu reflection-only.</span><span class="sxs-lookup"><span data-stu-id="a6dff-117">Attributes applied to the assembly or to its contents might be defined in the assembly, or they might be defined in another assembly loaded into the reflection-only context.</span></span> <span data-ttu-id="a6dff-118">Nie ma możliwości z wyprzedzeniem sprawdzić, gdzie są zdefiniowane atrybuty.</span><span class="sxs-lookup"><span data-stu-id="a6dff-118">There is no way to tell in advance where the attributes are defined.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6dff-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="a6dff-119">Example</span></span>  
 <span data-ttu-id="a6dff-120">Poniższy przykład kodu pokazuje jak zbadać atrybuty stosowane do zestawu ładowane do kontekstu reflection-only.</span><span class="sxs-lookup"><span data-stu-id="a6dff-120">The following code example shows how to examine the attributes applied to an assembly loaded into the reflection-only context.</span></span>  
  
 <span data-ttu-id="a6dff-121">Przykładowy kod definiuje dwa konstruktory i jedną właściwość atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="a6dff-121">The code example defines a custom attribute with two constructors and one property.</span></span> <span data-ttu-id="a6dff-122">Ten atrybut jest stosowany do zestawu, do typu zadeklarowany w zestawie, do metody typu i parametru metody.</span><span class="sxs-lookup"><span data-stu-id="a6dff-122">The attribute is applied to the assembly, to a type declared in the assembly, to a method of the type, and to a parameter of the method.</span></span> <span data-ttu-id="a6dff-123">Po wykonaniu zestawu ładuje się do kontekstu reflection-only i wyświetla informacje na temat atrybutów niestandardowych, które zostały zastosowane do niego i typy i elementy członkowskie, które zawiera.</span><span class="sxs-lookup"><span data-stu-id="a6dff-123">When executed, the assembly loads itself into the reflection-only context and displays information about the custom attributes that were applied to it and to the types and members it contains.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a6dff-124">Aby uprościć przykład kodu, zestaw ładuje i sprawdza się.</span><span class="sxs-lookup"><span data-stu-id="a6dff-124">To simplify the code example, the assembly loads and examines itself.</span></span> <span data-ttu-id="a6dff-125">Zwykle będzie spodziewa się znaleźć tego samego zestawu, które są ładowane do kontekstu wykonywania i kontekstu reflection-only.</span><span class="sxs-lookup"><span data-stu-id="a6dff-125">Normally, you would not expect to find the same assembly loaded into both the execution context and the reflection-only context.</span></span>  
  
 [!code-cpp[CustomAttributeData#1](../../../samples/snippets/cpp/VS_Snippets_CLR/CustomAttributeData/CPP/source.cpp#1)]
 [!code-csharp[CustomAttributeData#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CustomAttributeData/CS/source.cs#1)]
 [!code-vb[CustomAttributeData#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CustomAttributeData/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="a6dff-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a6dff-126">See also</span></span>

- <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>
- <xref:System.Reflection.Assembly.ReflectionOnly%2A>
- <xref:System.Reflection.CustomAttributeData>
