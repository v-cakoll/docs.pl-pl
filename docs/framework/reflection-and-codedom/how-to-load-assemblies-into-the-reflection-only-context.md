---
title: 'Porady: ładowanie zestawów do kontekstu Reflection-Only'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 8
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6ab0224dd0452003f1d43a314d03aaca0fe04fda
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-load-assemblies-into-the-reflection-only-context"></a><span data-ttu-id="1c41b-102">Porady: ładowanie zestawów do kontekstu Reflection-Only</span><span class="sxs-lookup"><span data-stu-id="1c41b-102">How to: Load Assemblies into the Reflection-Only Context</span></span>
<span data-ttu-id="1c41b-103">Kontekstu ładowania tylko odbicie można zbadać zestawy skompilowany dla innych platform lub innych wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1c41b-103">The reflection-only load context allows you to examine assemblies compiled for other platforms or for other versions of the .NET Framework.</span></span> <span data-ttu-id="1c41b-104">Tylko można zbadać kodu załadowanego w tym kontekście; Nie można wykonać.</span><span class="sxs-lookup"><span data-stu-id="1c41b-104">Code loaded into this context can only be examined; it cannot be executed.</span></span> <span data-ttu-id="1c41b-105">Oznacza to, że nie można utworzyć obiektów, ponieważ nie można wykonać konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="1c41b-105">This means that objects cannot be created, because constructors cannot be executed.</span></span> <span data-ttu-id="1c41b-106">Ponieważ nie można wykonać kod, zależności nie są ładowane automatycznie.</span><span class="sxs-lookup"><span data-stu-id="1c41b-106">Because the code cannot be executed, dependencies are not automatically loaded.</span></span> <span data-ttu-id="1c41b-107">Jeśli potrzebujesz zbadać je, należy załadować je samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="1c41b-107">If you need to examine them, you must load them yourself.</span></span>  
  
### <a name="to-load-an-assembly-into-the-reflection-only-load-context"></a><span data-ttu-id="1c41b-108">Aby załadować zestawu do kontekstu ładowania tylko odbicie</span><span class="sxs-lookup"><span data-stu-id="1c41b-108">To load an assembly into the reflection-only load context</span></span>  
  
1.  <span data-ttu-id="1c41b-109">Użyj <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.String%29> przeciążenie metody można załadować zestawu podanej nazwy wyświetlanej, lub <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> metody można załadować zestawu podanej ścieżki.</span><span class="sxs-lookup"><span data-stu-id="1c41b-109">Use the <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.String%29> method overload to load the assembly given its display name, or the <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> method to load the assembly given its path.</span></span> <span data-ttu-id="1c41b-110">Jeśli zestaw jest obraz binarny, użyj <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.Byte%5B%5D%29> przeciążenie metody.</span><span class="sxs-lookup"><span data-stu-id="1c41b-110">If the assembly is a binary image, use the <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.Byte%5B%5D%29> method overload.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1c41b-111">Za pomocą kontekstu reflection-only nie można załadować wersji biblioteki mscorlib.dll z wersji programu .NET Framework innej niż wersja w kontekstu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="1c41b-111">You cannot use the reflection-only context to load a version of mscorlib.dll from a version of the .NET Framework other than the version in the execution context.</span></span>  
  
2.  <span data-ttu-id="1c41b-112">Jeśli zestaw zawiera zależności, <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> — metoda nie załadować je.</span><span class="sxs-lookup"><span data-stu-id="1c41b-112">If the assembly has dependencies, the <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> method does not load them.</span></span> <span data-ttu-id="1c41b-113">Jeśli potrzebujesz zbadać je, należy załadować je samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="1c41b-113">If you need to examine them, you must load them yourself.</span></span>  
  
3.  <span data-ttu-id="1c41b-114">Określić, czy zestaw jest ładowany do kontekstu reflection-only przy użyciu zestawu <xref:System.Reflection.Assembly.ReflectionOnly%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="1c41b-114">Determine whether an assembly is loaded into the reflection-only context by using the assembly's <xref:System.Reflection.Assembly.ReflectionOnly%2A> property.</span></span>  
  
4.  <span data-ttu-id="1c41b-115">Jeśli atrybuty zostały zastosowane do zestawu lub typów w zestawie, Sprawdź te atrybuty przy użyciu <xref:System.Reflection.CustomAttributeData> klasy, aby upewnić się, że nie są podejmowane próby wykonania kodu w kontekstu reflection-only.</span><span class="sxs-lookup"><span data-stu-id="1c41b-115">If attributes have been applied to the assembly or to types in the assembly, examine those attributes by using the <xref:System.Reflection.CustomAttributeData> class to ensure that no attempt is made to execute code in the reflection-only context.</span></span> <span data-ttu-id="1c41b-116">Użyj odpowiedniego przeciążenia <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> metodę, aby uzyskać <xref:System.Reflection.CustomAttributeData> obiektów reprezentujących atrybuty stosowane do zestawu, elementu członkowskiego, modułu lub parametr.</span><span class="sxs-lookup"><span data-stu-id="1c41b-116">Use the appropriate overload of the <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> method to obtain <xref:System.Reflection.CustomAttributeData> objects representing the attributes applied to an assembly, member, module, or parameter.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1c41b-117">Atrybuty stosowane do zestawu lub jego zawartość może być zdefiniowana w zestawie lub może być zdefiniowana w innym zestawie ładowane do kontekstu reflection-only.</span><span class="sxs-lookup"><span data-stu-id="1c41b-117">Attributes applied to the assembly or to its contents might be defined in the assembly, or they might be defined in another assembly loaded into the reflection-only context.</span></span> <span data-ttu-id="1c41b-118">Nie istnieje sposób mówić z wyprzedzeniem, gdzie są zdefiniowane atrybuty.</span><span class="sxs-lookup"><span data-stu-id="1c41b-118">There is no way to tell in advance where the attributes are defined.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c41b-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="1c41b-119">Example</span></span>  
 <span data-ttu-id="1c41b-120">Poniższy przykład kodu pokazuje, jak zbadać atrybutów zastosowany do zestawu ładowane do kontekstu reflection-only.</span><span class="sxs-lookup"><span data-stu-id="1c41b-120">The following code example shows how to examine the attributes applied to an assembly loaded into the reflection-only context.</span></span>  
  
 <span data-ttu-id="1c41b-121">Przykładowy kod definiuje atrybut niestandardowy dwa konstruktory i jedną właściwość.</span><span class="sxs-lookup"><span data-stu-id="1c41b-121">The code example defines a custom attribute with two constructors and one property.</span></span> <span data-ttu-id="1c41b-122">Atrybut jest stosowany do zestawu, na typ zadeklarowany w zestawie, metody typu i parametru metody.</span><span class="sxs-lookup"><span data-stu-id="1c41b-122">The attribute is applied to the assembly, to a type declared in the assembly, to a method of the type, and to a parameter of the method.</span></span> <span data-ttu-id="1c41b-123">Po wykonaniu zestaw ładuje się do kontekstu reflection-only i wyświetla informacje o niestandardowych atrybutów, które zostały zastosowane oraz typy i składniki, które zawiera.</span><span class="sxs-lookup"><span data-stu-id="1c41b-123">When executed, the assembly loads itself into the reflection-only context and displays information about the custom attributes that were applied to it and to the types and members it contains.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1c41b-124">Aby uprościć przykładów kodu, zestaw ładuje i sprawdza sama.</span><span class="sxs-lookup"><span data-stu-id="1c41b-124">To simplify the code example, the assembly loads and examines itself.</span></span> <span data-ttu-id="1c41b-125">Zwykle nie będzie Oczekiwano znalezienia tego samego zestawu ładowane do zarówno kontekstu wykonywania i kontekstu reflection-only.</span><span class="sxs-lookup"><span data-stu-id="1c41b-125">Normally, you would not expect to find the same assembly loaded into both the execution context and the reflection-only context.</span></span>  
  
 [!code-cpp[CustomAttributeData#1](../../../samples/snippets/cpp/VS_Snippets_CLR/CustomAttributeData/CPP/source.cpp#1)]
 [!code-csharp[CustomAttributeData#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CustomAttributeData/CS/source.cs#1)]
 [!code-vb[CustomAttributeData#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CustomAttributeData/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="1c41b-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1c41b-126">See Also</span></span>  
 <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>  
 <xref:System.Reflection.Assembly.ReflectionOnly%2A>  
 <xref:System.Reflection.CustomAttributeData>
