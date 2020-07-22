---
title: Wyświetlanie informacji o typie
description: Wyświetlanie informacji o typie przy użyciu typu System. Type, który stanowi centralne odbicie w programie .NET. Przejrzyj ConstructorInfo, MemberInfo, MethodInfo, FieldInfo i PropertyInfo.
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
ms.openlocfilehash: cd74021e1f1a79626e171db13def98e546cd51df
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865206"
---
# <a name="viewing-type-information"></a><span data-ttu-id="8156e-104">Wyświetlanie informacji o typie</span><span class="sxs-lookup"><span data-stu-id="8156e-104">Viewing Type Information</span></span>
<span data-ttu-id="8156e-105"><xref:System.Type?displayProperty=nameWithType>Klasa jest centralną odbiciem.</span><span class="sxs-lookup"><span data-stu-id="8156e-105">The <xref:System.Type?displayProperty=nameWithType> class is central to reflection.</span></span> <span data-ttu-id="8156e-106">Środowisko uruchomieniowe języka wspólnego tworzy **Typ** załadowanego typu podczas odbicia żądania.</span><span class="sxs-lookup"><span data-stu-id="8156e-106">The common language runtime creates the **Type** for a loaded type when reflection requests it.</span></span> <span data-ttu-id="8156e-107">Możesz użyć metod, pól, właściwości i klas zagnieżdżonych obiektu **typu** , aby dowiedzieć się wszystkiego o tym typie.</span><span class="sxs-lookup"><span data-stu-id="8156e-107">You can use a **Type** object's methods, fields, properties, and nested classes to find out everything about that type.</span></span>  
  
 <span data-ttu-id="8156e-108">Użyj <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> lub <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType> , aby uzyskać obiekty **typu** z zestawów, które nie zostały załadowane, przekazując nazwę żądanego typu lub typów.</span><span class="sxs-lookup"><span data-stu-id="8156e-108">Use <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType> to obtain **Type** objects from assemblies that have not been loaded, passing in the name of the type or types you want.</span></span> <span data-ttu-id="8156e-109">Służy <xref:System.Type.GetType%2A?displayProperty=nameWithType> do pobierania obiektów **typu** z zestawu, który jest już załadowany.</span><span class="sxs-lookup"><span data-stu-id="8156e-109">Use <xref:System.Type.GetType%2A?displayProperty=nameWithType> to get the **Type** objects from an assembly that is already loaded.</span></span> <span data-ttu-id="8156e-110">Użyj <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType> i, <xref:System.Reflection.Module.GetTypes%2A?displayProperty=nameWithType> Aby uzyskać obiekty **typu** modułu.</span><span class="sxs-lookup"><span data-stu-id="8156e-110">Use <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType> and <xref:System.Reflection.Module.GetTypes%2A?displayProperty=nameWithType> to obtain module **Type** objects.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8156e-111">Jeśli chcesz sprawdzić typy ogólne i metody i manipulować nimi, zapoznaj się z dodatkowymi informacjami podanymi w obszarze [odbicie i typy ogólne](reflection-and-generic-types.md) oraz [jak: sprawdzanie i Tworzenie wystąpień typów ogólnych za pomocą odbicia](how-to-examine-and-instantiate-generic-types-with-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="8156e-111">If you want to examine and manipulate generic types and methods, please see the additional information provided in [Reflection and Generic Types](reflection-and-generic-types.md) and [How to: Examine and Instantiate Generic Types with Reflection](how-to-examine-and-instantiate-generic-types-with-reflection.md).</span></span>  
  
 <span data-ttu-id="8156e-112">Poniższy przykład pokazuje składnię niezbędną do pobrania <xref:System.Reflection.Assembly> obiektu i modułu dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="8156e-112">The following example shows the syntax necessary to get the <xref:System.Reflection.Assembly> object and module for an assembly.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source5.cpp#6)]
 [!code-csharp[Conceptual.Types.ViewInfo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source5.cs#6)]
 [!code-vb[Conceptual.Types.ViewInfo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source5.vb#6)]  
  
 <span data-ttu-id="8156e-113">Poniższy przykład ilustruje pobieranie obiektów **typu** z załadowanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="8156e-113">The following example demonstrates getting **Type** objects from a loaded assembly.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source5.cpp#7)]
 [!code-csharp[Conceptual.Types.ViewInfo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source5.cs#7)]
 [!code-vb[Conceptual.Types.ViewInfo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source5.vb#7)]  
  
 <span data-ttu-id="8156e-114">Po uzyskaniu **typu**istnieje wiele sposobów odnajdywania informacji o elementach członkowskich tego typu.</span><span class="sxs-lookup"><span data-stu-id="8156e-114">Once you obtain a **Type**, there are many ways you can discover information about the members of that type.</span></span> <span data-ttu-id="8156e-115">Na przykład można dowiedzieć się więcej o wszystkich elementach członkowskich typu przez wywołanie <xref:System.Type.GetMembers%2A?displayProperty=nameWithType> metody, która uzyskuje tablicę <xref:System.Reflection.MemberInfo> obiektów opisującą każdy element członkowski bieżącego typu.</span><span class="sxs-lookup"><span data-stu-id="8156e-115">For example, you can find out about all the type's members by calling the <xref:System.Type.GetMembers%2A?displayProperty=nameWithType> method, which obtains an array of <xref:System.Reflection.MemberInfo> objects describing each of the members of the current type.</span></span>  
  
 <span data-ttu-id="8156e-116">Można również użyć metod klasy **Type** , aby pobrać informacje o jednym lub wielu konstruktorach, metodach, zdarzeniach, polach lub właściwościach określonych przez nazwę.</span><span class="sxs-lookup"><span data-stu-id="8156e-116">You can also use methods on the **Type** class to retrieve information about one or more constructors, methods, events, fields, or properties that you specify by name.</span></span> <span data-ttu-id="8156e-117">Na przykład <xref:System.Type.GetConstructor%2A?displayProperty=nameWithType> hermetyzuje określony Konstruktor bieżącej klasy.</span><span class="sxs-lookup"><span data-stu-id="8156e-117">For example, <xref:System.Type.GetConstructor%2A?displayProperty=nameWithType> encapsulates a specific constructor of the current class.</span></span>  
  
 <span data-ttu-id="8156e-118">Jeśli masz **Typ**, możesz użyć <xref:System.Type.Module%2A?displayProperty=nameWithType> właściwości, aby uzyskać obiekt, który hermetyzuje moduł zawierający ten typ.</span><span class="sxs-lookup"><span data-stu-id="8156e-118">If you have a **Type**, you can use the <xref:System.Type.Module%2A?displayProperty=nameWithType> property to obtain an object that encapsulates the module containing that type.</span></span> <span data-ttu-id="8156e-119">Użyj <xref:System.Reflection.Module.Assembly%2A?displayProperty=nameWithType> właściwości, aby zlokalizować obiekt, który hermetyzuje zestaw zawierający moduł.</span><span class="sxs-lookup"><span data-stu-id="8156e-119">Use the <xref:System.Reflection.Module.Assembly%2A?displayProperty=nameWithType> property to locate an object that encapsulates the assembly containing the module.</span></span> <span data-ttu-id="8156e-120">Zestaw, który hermetyzuje typ, można uzyskać bezpośrednio przy użyciu <xref:System.Type.Assembly%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="8156e-120">You can obtain the assembly that encapsulates the type directly by using the <xref:System.Type.Assembly%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="systemtype-and-constructorinfo"></a><span data-ttu-id="8156e-121">System. Type i ConstructorInfo</span><span class="sxs-lookup"><span data-stu-id="8156e-121">System.Type and ConstructorInfo</span></span>  
 <span data-ttu-id="8156e-122">Poniższy przykład pokazuje, jak wyświetlić listę konstruktorów dla klasy, w tym przypadku <xref:System.String> klasy.</span><span class="sxs-lookup"><span data-stu-id="8156e-122">The following example shows how to list the constructors for a class, in this case, the <xref:System.String> class.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Types.ViewInfo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source1.cs#1)]
 [!code-vb[Conceptual.Types.ViewInfo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source1.vb#1)]  
  
## <a name="memberinfo-methodinfo-fieldinfo-and-propertyinfo"></a><span data-ttu-id="8156e-123">MemberInfo, MethodInfo, FieldInfo i PropertyInfo</span><span class="sxs-lookup"><span data-stu-id="8156e-123">MemberInfo, MethodInfo, FieldInfo, and PropertyInfo</span></span>  
 <span data-ttu-id="8156e-124">Uzyskaj informacje na temat metod, właściwości, zdarzeń i pól typu, przy użyciu <xref:System.Reflection.MemberInfo> obiektów,, <xref:System.Reflection.MethodInfo> <xref:System.Reflection.FieldInfo> , lub <xref:System.Reflection.PropertyInfo> .</span><span class="sxs-lookup"><span data-stu-id="8156e-124">Obtain information about the type's methods, properties, events, and fields using <xref:System.Reflection.MemberInfo>, <xref:System.Reflection.MethodInfo>, <xref:System.Reflection.FieldInfo>, or <xref:System.Reflection.PropertyInfo> objects.</span></span>  
  
 <span data-ttu-id="8156e-125">Poniższy przykład używa **MemberInfo** , aby wyświetlić listę elementów członkowskich w klasie **System. IO. File** i używa <xref:System.Type.IsPublic%2A> właściwości, aby określić widoczność klasy.</span><span class="sxs-lookup"><span data-stu-id="8156e-125">The following example uses **MemberInfo** to list the number of members in the **System.IO.File** class and uses the <xref:System.Type.IsPublic%2A> property to determine the visibility of the class.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Types.ViewInfo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source2.cs#2)]
 [!code-vb[Conceptual.Types.ViewInfo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source2.vb#2)]  
  
 <span data-ttu-id="8156e-126">Poniższy przykład sprawdza typ określonego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="8156e-126">The following example investigates the type of the specified member.</span></span> <span data-ttu-id="8156e-127">Wykonuje odbicie na elemencie członkowskim klasy **MemberInfo** i wyświetla jego typ.</span><span class="sxs-lookup"><span data-stu-id="8156e-127">It performs reflection on a member of the **MemberInfo** class, and lists its type.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.Types.ViewInfo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source3.cs#3)]
 [!code-vb[Conceptual.Types.ViewInfo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source3.vb#3)]  
  
 <span data-ttu-id="8156e-128">W poniższym przykładzie są wykorzystywane wszystkie klasy \*\* \* informacji\*\* odbicia wraz z programem <xref:System.Reflection.BindingFlags> , aby wyświetlić listę wszystkich członków (konstruktorów, pól, właściwości, zdarzeń i metod) określonej klasy, dzieląc elementy członkowskie na kategorie statyczne i wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="8156e-128">The following example uses all the Reflection **\*Info** classes along with <xref:System.Reflection.BindingFlags> to list all the members (constructors, fields, properties, events, and methods) of the specified class, dividing the members into static and instance categories.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.Types.ViewInfo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source4.cs#4)]
 [!code-vb[Conceptual.Types.ViewInfo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source4.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="8156e-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8156e-129">See also</span></span>

- <xref:System.Reflection.BindingFlags>
- <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType>
- <xref:System.Type.GetType%2A?displayProperty=nameWithType>
- <xref:System.Type.GetMembers%2A?displayProperty=nameWithType>
- <xref:System.Type.GetFields%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Module.GetTypes%2A?displayProperty=nameWithType>
- <xref:System.Reflection.MemberInfo>
- <xref:System.Reflection.ConstructorInfo>
- <xref:System.Reflection.MethodInfo>
- <xref:System.Reflection.FieldInfo>
- <xref:System.Reflection.EventInfo>
- <xref:System.Reflection.ParameterInfo>
- [<span data-ttu-id="8156e-130">Odbicie i typy ogólne</span><span class="sxs-lookup"><span data-stu-id="8156e-130">Reflection and Generic Types</span></span>](reflection-and-generic-types.md)
