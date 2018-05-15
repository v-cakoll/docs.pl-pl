---
title: Wyświetlanie informacji o typie
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- types, viewing type information
- Type object
- viewing type information
- reflection, viewing type information
ms.assetid: 7e7303a9-4064-4738-b4e7-b75974ed70d2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cc957b345c1e66059551508f73e37e0f6d69f6cd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="viewing-type-information"></a><span data-ttu-id="7ee82-102">Wyświetlanie informacji o typie</span><span class="sxs-lookup"><span data-stu-id="7ee82-102">Viewing Type Information</span></span>
<span data-ttu-id="7ee82-103"><xref:System.Type?displayProperty=nameWithType> Klasy jest podstawą odbicia.</span><span class="sxs-lookup"><span data-stu-id="7ee82-103">The <xref:System.Type?displayProperty=nameWithType> class is central to reflection.</span></span> <span data-ttu-id="7ee82-104">Tworzy środowisko uruchomieniowe języka wspólnego **typu** dla typu załadowanego podczas żądania odbicia.</span><span class="sxs-lookup"><span data-stu-id="7ee82-104">The common language runtime creates the **Type** for a loaded type when reflection requests it.</span></span> <span data-ttu-id="7ee82-105">Można użyć **typu** metod, pola, właściwości i zagnieżdżonych klas, aby dowiedzieć się wszystkiego o tego typu obiektu.</span><span class="sxs-lookup"><span data-stu-id="7ee82-105">You can use a **Type** object's methods, fields, properties, and nested classes to find out everything about that type.</span></span>  
  
 <span data-ttu-id="7ee82-106">Użyj <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> lub <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType> uzyskanie **typu** obiektów z zestawów, które nie zostały załadowane, przekazywanie nazwy typu lub typy mają.</span><span class="sxs-lookup"><span data-stu-id="7ee82-106">Use <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType> to obtain **Type** objects from assemblies that have not been loaded, passing in the name of the type or types you want.</span></span> <span data-ttu-id="7ee82-107">Użyj <xref:System.Type.GetType%2A?displayProperty=nameWithType> uzyskanie **typu** obiektów z zestawu, który został już załadowany.</span><span class="sxs-lookup"><span data-stu-id="7ee82-107">Use <xref:System.Type.GetType%2A?displayProperty=nameWithType> to get the **Type** objects from an assembly that is already loaded.</span></span> <span data-ttu-id="7ee82-108">Użyj <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType> i <xref:System.Reflection.Module.GetTypes%2A?displayProperty=nameWithType> uzyskać modułu **typu** obiektów.</span><span class="sxs-lookup"><span data-stu-id="7ee82-108">Use <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType> and <xref:System.Reflection.Module.GetTypes%2A?displayProperty=nameWithType> to obtain module **Type** objects.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7ee82-109">Do badania i manipulowania typy ogólne i metody, można znaleźć dodatkowe informacje zawarte w [odbicie i typy ogólne](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md) i [porady: zbadanie i rodzajowy wystąpień typów za pomocą odbicia](../../../docs/framework/reflection-and-codedom/how-to-examine-and-instantiate-generic-types-with-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="7ee82-109">If you want to examine and manipulate generic types and methods, please see the additional information provided in [Reflection and Generic Types](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md) and [How to: Examine and Instantiate Generic Types with Reflection](../../../docs/framework/reflection-and-codedom/how-to-examine-and-instantiate-generic-types-with-reflection.md).</span></span>  
  
 <span data-ttu-id="7ee82-110">W poniższym przykładzie przedstawiono składnię niezbędne, aby uzyskać <xref:System.Reflection.Assembly> obiektu i modułów zestawu.</span><span class="sxs-lookup"><span data-stu-id="7ee82-110">The following example shows the syntax necessary to get the <xref:System.Reflection.Assembly> object and module for an assembly.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source5.cpp#6)]
 [!code-csharp[Conceptual.Types.ViewInfo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source5.cs#6)]
 [!code-vb[Conceptual.Types.ViewInfo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source5.vb#6)]  
  
 <span data-ttu-id="7ee82-111">W poniższym przykładzie pokazano, uzyskiwanie **typu** obiektów z załadowanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="7ee82-111">The following example demonstrates getting **Type** objects from a loaded assembly.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source5.cpp#7)]
 [!code-csharp[Conceptual.Types.ViewInfo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source5.cs#7)]
 [!code-vb[Conceptual.Types.ViewInfo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source5.vb#7)]  
  
 <span data-ttu-id="7ee82-112">Po uzyskaniu **typu**, istnieje wiele sposobów, można znaleźć informacje o elementach członkowskich tego typu.</span><span class="sxs-lookup"><span data-stu-id="7ee82-112">Once you obtain a **Type**, there are many ways you can discover information about the members of that type.</span></span> <span data-ttu-id="7ee82-113">Na przykład można znaleźć o elementy członkowskie wszystkie typu przez wywołanie metody <xref:System.Type.GetMembers%2A?displayProperty=nameWithType> metodę, która pobiera tablicę <xref:System.Reflection.MemberInfo> opisujące wszystkich członków bieżącego typu obiektów.</span><span class="sxs-lookup"><span data-stu-id="7ee82-113">For example, you can find out about all the type's members by calling the <xref:System.Type.GetMembers%2A?displayProperty=nameWithType> method, which obtains an array of <xref:System.Reflection.MemberInfo> objects describing each of the members of the current type.</span></span>  
  
 <span data-ttu-id="7ee82-114">Możesz również użyć metod w **typu** klasy można pobrać informacji o co najmniej jeden konstruktorów, metod, zdarzenia, pola lub właściwości, które określają według nazwy.</span><span class="sxs-lookup"><span data-stu-id="7ee82-114">You can also use methods on the **Type** class to retrieve information about one or more constructors, methods, events, fields, or properties that you specify by name.</span></span> <span data-ttu-id="7ee82-115">Na przykład <xref:System.Type.GetConstructor%2A?displayProperty=nameWithType> hermetyzuje określonego konstruktora klasy.</span><span class="sxs-lookup"><span data-stu-id="7ee82-115">For example, <xref:System.Type.GetConstructor%2A?displayProperty=nameWithType> encapsulates a specific constructor of the current class.</span></span>  
  
 <span data-ttu-id="7ee82-116">Jeśli masz **typu**, można użyć <xref:System.Type.Module%2A?displayProperty=nameWithType> właściwości, aby uzyskać obiekt hermetyzujący zawierającego tego typu modułu.</span><span class="sxs-lookup"><span data-stu-id="7ee82-116">If you have a **Type**, you can use the <xref:System.Type.Module%2A?displayProperty=nameWithType> property to obtain an object that encapsulates the module containing that type.</span></span> <span data-ttu-id="7ee82-117">Użyj <xref:System.Reflection.Module.Assembly%2A?displayProperty=nameWithType> właściwości do zlokalizowania obiektu, który hermetyzuje zestawu zawierającego modułu.</span><span class="sxs-lookup"><span data-stu-id="7ee82-117">Use the <xref:System.Reflection.Module.Assembly%2A?displayProperty=nameWithType> property to locate an object that encapsulates the assembly containing the module.</span></span> <span data-ttu-id="7ee82-118">Można uzyskać zestawu, który hermetyzuje typ bezpośrednio za pomocą <xref:System.Type.Assembly%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="7ee82-118">You can obtain the assembly that encapsulates the type directly by using the <xref:System.Type.Assembly%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="systemtype-and-constructorinfo"></a><span data-ttu-id="7ee82-119">System.Type i ConstructorInfo</span><span class="sxs-lookup"><span data-stu-id="7ee82-119">System.Type and ConstructorInfo</span></span>  
 <span data-ttu-id="7ee82-120">Poniższy przykład przedstawia sposób listy konstruktorów dla klasy, w tym przypadku <xref:System.String> klasy.</span><span class="sxs-lookup"><span data-stu-id="7ee82-120">The following example shows how to list the constructors for a class, in this case, the <xref:System.String> class.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Types.ViewInfo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source1.cs#1)]
 [!code-vb[Conceptual.Types.ViewInfo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source1.vb#1)]  
  
## <a name="memberinfo-methodinfo-fieldinfo-and-propertyinfo"></a><span data-ttu-id="7ee82-121">Element MemberInfo, MethodInfo FieldInfo i PropertyInfo</span><span class="sxs-lookup"><span data-stu-id="7ee82-121">MemberInfo, MethodInfo, FieldInfo, and PropertyInfo</span></span>  
 <span data-ttu-id="7ee82-122">Uzyskaj informacje na temat metody, właściwości, zdarzeń i pola przy użyciu typu <xref:System.Reflection.MemberInfo>, <xref:System.Reflection.MethodInfo>, <xref:System.Reflection.FieldInfo>, lub <xref:System.Reflection.PropertyInfo> obiektów.</span><span class="sxs-lookup"><span data-stu-id="7ee82-122">Obtain information about the type's methods, properties, events, and fields using <xref:System.Reflection.MemberInfo>, <xref:System.Reflection.MethodInfo>, <xref:System.Reflection.FieldInfo>, or <xref:System.Reflection.PropertyInfo> objects.</span></span>  
  
 <span data-ttu-id="7ee82-123">W poniższym przykładzie użyto **MemberInfo** do wyświetlenia liczba elementów członkowskich w **System.IO.File** klasy i używa <xref:System.Type.IsPublic%2A> właściwości w celu określenia widoczność klasy.</span><span class="sxs-lookup"><span data-stu-id="7ee82-123">The following example uses **MemberInfo** to list the number of members in the **System.IO.File** class and uses the <xref:System.Type.IsPublic%2A> property to determine the visibility of the class.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Types.ViewInfo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source2.cs#2)]
 [!code-vb[Conceptual.Types.ViewInfo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source2.vb#2)]  
  
 <span data-ttu-id="7ee82-124">Poniższy przykład sprawdza typ określonego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="7ee82-124">The following example investigates the type of the specified member.</span></span> <span data-ttu-id="7ee82-125">Wykonuje odbicia w elemencie **MemberInfo** klasy, a jego typu.</span><span class="sxs-lookup"><span data-stu-id="7ee82-125">It performs reflection on a member of the **MemberInfo** class, and lists its type.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.Types.ViewInfo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source3.cs#3)]
 [!code-vb[Conceptual.Types.ViewInfo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source3.vb#3)]  
  
 <span data-ttu-id="7ee82-126">W poniższym przykładzie użyto wszystkich odbicia  **\*informacji** klasy wraz z programem <xref:System.Reflection.BindingFlags> Aby wyświetlić listę wszystkich członków (konstruktorów, pola, właściwości, zdarzeń i metody) z określonej klasy dzielenia elementów członkowskich w statycznej i wystąpienie kategorii.</span><span class="sxs-lookup"><span data-stu-id="7ee82-126">The following example uses all the Reflection **\*Info** classes along with <xref:System.Reflection.BindingFlags> to list all the members (constructors, fields, properties, events, and methods) of the specified class, dividing the members into static and instance categories.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.Types.ViewInfo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source4.cs#4)]
 [!code-vb[Conceptual.Types.ViewInfo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source4.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="7ee82-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7ee82-127">See Also</span></span>  
 <xref:System.Reflection.BindingFlags>  
 <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>  
 <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType>  
 <xref:System.Type.GetType%2A?displayProperty=nameWithType>  
 <xref:System.Type.GetMembers%2A?displayProperty=nameWithType>  
 <xref:System.Type.GetFields%2A?displayProperty=nameWithType>  
 <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>  
 <xref:System.Reflection.Module.GetTypes%2A?displayProperty=nameWithType>  
 <xref:System.Reflection.MemberInfo>  
 <xref:System.Reflection.ConstructorInfo>  
 <xref:System.Reflection.MethodInfo>  
 <xref:System.Reflection.FieldInfo>  
 <xref:System.Reflection.EventInfo>  
 <xref:System.Reflection.ParameterInfo>  
 [<span data-ttu-id="7ee82-128">Odbicie i typy ogólne</span><span class="sxs-lookup"><span data-stu-id="7ee82-128">Reflection and Generic Types</span></span>](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md)
