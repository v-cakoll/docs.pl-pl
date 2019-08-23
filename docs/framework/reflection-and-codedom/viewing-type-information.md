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
ms.openlocfilehash: e658b2c86eecdbc45a9adde8d28cfb890dd591b9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956661"
---
# <a name="viewing-type-information"></a><span data-ttu-id="53816-102">Wyświetlanie informacji o typie</span><span class="sxs-lookup"><span data-stu-id="53816-102">Viewing Type Information</span></span>
<span data-ttu-id="53816-103"><xref:System.Type?displayProperty=nameWithType> Klasa jest centralną odbiciem.</span><span class="sxs-lookup"><span data-stu-id="53816-103">The <xref:System.Type?displayProperty=nameWithType> class is central to reflection.</span></span> <span data-ttu-id="53816-104">Środowisko uruchomieniowe języka wspólnego tworzy **Typ** załadowanego typu podczas odbicia żądania.</span><span class="sxs-lookup"><span data-stu-id="53816-104">The common language runtime creates the **Type** for a loaded type when reflection requests it.</span></span> <span data-ttu-id="53816-105">Możesz użyć metod, pól, właściwości i klas zagnieżdżonych obiektu **typu** , aby dowiedzieć się wszystkiego o tym typie.</span><span class="sxs-lookup"><span data-stu-id="53816-105">You can use a **Type** object's methods, fields, properties, and nested classes to find out everything about that type.</span></span>  
  
 <span data-ttu-id="53816-106">Użyj <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> lub<xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType> , aby uzyskać obiekty **typu** z zestawów, które nie zostały załadowane, przekazując nazwę żądanego typu lub typów.</span><span class="sxs-lookup"><span data-stu-id="53816-106">Use <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType> to obtain **Type** objects from assemblies that have not been loaded, passing in the name of the type or types you want.</span></span> <span data-ttu-id="53816-107">Służy <xref:System.Type.GetType%2A?displayProperty=nameWithType> do pobierania obiektów **typu** z zestawu, który jest już załadowany.</span><span class="sxs-lookup"><span data-stu-id="53816-107">Use <xref:System.Type.GetType%2A?displayProperty=nameWithType> to get the **Type** objects from an assembly that is already loaded.</span></span> <span data-ttu-id="53816-108">Użyj <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType> i <xref:System.Reflection.Module.GetTypes%2A?displayProperty=nameWithType> , aby uzyskać obiekty **typu** modułu.</span><span class="sxs-lookup"><span data-stu-id="53816-108">Use <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType> and <xref:System.Reflection.Module.GetTypes%2A?displayProperty=nameWithType> to obtain module **Type** objects.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="53816-109">Jeśli chcesz sprawdzić typy ogólne i metody i manipulować nimi, zapoznaj się z dodatkowymi informacjami podanymi w obszarze odbicie [ [i typy ogólne](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md) oraz jak: Sprawdzanie i Tworzenie wystąpień typów ogólnych za](../../../docs/framework/reflection-and-codedom/how-to-examine-and-instantiate-generic-types-with-reflection.md)pomocą odbicia.</span><span class="sxs-lookup"><span data-stu-id="53816-109">If you want to examine and manipulate generic types and methods, please see the additional information provided in [Reflection and Generic Types](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md) and [How to: Examine and Instantiate Generic Types with Reflection](../../../docs/framework/reflection-and-codedom/how-to-examine-and-instantiate-generic-types-with-reflection.md).</span></span>  
  
 <span data-ttu-id="53816-110">Poniższy przykład pokazuje składnię niezbędną do pobrania <xref:System.Reflection.Assembly> obiektu i modułu dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="53816-110">The following example shows the syntax necessary to get the <xref:System.Reflection.Assembly> object and module for an assembly.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source5.cpp#6)]
 [!code-csharp[Conceptual.Types.ViewInfo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source5.cs#6)]
 [!code-vb[Conceptual.Types.ViewInfo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source5.vb#6)]  
  
 <span data-ttu-id="53816-111">Poniższy przykład ilustruje pobieranie obiektów **typu** z załadowanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="53816-111">The following example demonstrates getting **Type** objects from a loaded assembly.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source5.cpp#7)]
 [!code-csharp[Conceptual.Types.ViewInfo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source5.cs#7)]
 [!code-vb[Conceptual.Types.ViewInfo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source5.vb#7)]  
  
 <span data-ttu-id="53816-112">Po uzyskaniu **typu**istnieje wiele sposobów odnajdywania informacji o elementach członkowskich tego typu.</span><span class="sxs-lookup"><span data-stu-id="53816-112">Once you obtain a **Type**, there are many ways you can discover information about the members of that type.</span></span> <span data-ttu-id="53816-113">Na przykład można dowiedzieć się więcej o wszystkich elementach członkowskich typu przez wywołanie <xref:System.Type.GetMembers%2A?displayProperty=nameWithType> metody, która uzyskuje <xref:System.Reflection.MemberInfo> tablicę obiektów opisującą każdy element członkowski bieżącego typu.</span><span class="sxs-lookup"><span data-stu-id="53816-113">For example, you can find out about all the type's members by calling the <xref:System.Type.GetMembers%2A?displayProperty=nameWithType> method, which obtains an array of <xref:System.Reflection.MemberInfo> objects describing each of the members of the current type.</span></span>  
  
 <span data-ttu-id="53816-114">Można również użyć metod klasy **Type** , aby pobrać informacje o jednym lub wielu konstruktorach, metodach, zdarzeniach, polach lub właściwościach określonych przez nazwę.</span><span class="sxs-lookup"><span data-stu-id="53816-114">You can also use methods on the **Type** class to retrieve information about one or more constructors, methods, events, fields, or properties that you specify by name.</span></span> <span data-ttu-id="53816-115">Na przykład <xref:System.Type.GetConstructor%2A?displayProperty=nameWithType> hermetyzuje określony Konstruktor bieżącej klasy.</span><span class="sxs-lookup"><span data-stu-id="53816-115">For example, <xref:System.Type.GetConstructor%2A?displayProperty=nameWithType> encapsulates a specific constructor of the current class.</span></span>  
  
 <span data-ttu-id="53816-116">Jeśli masz **Typ**, możesz użyć <xref:System.Type.Module%2A?displayProperty=nameWithType> właściwości, aby uzyskać obiekt, który hermetyzuje moduł zawierający ten typ.</span><span class="sxs-lookup"><span data-stu-id="53816-116">If you have a **Type**, you can use the <xref:System.Type.Module%2A?displayProperty=nameWithType> property to obtain an object that encapsulates the module containing that type.</span></span> <span data-ttu-id="53816-117"><xref:System.Reflection.Module.Assembly%2A?displayProperty=nameWithType> Użyj właściwości, aby zlokalizować obiekt, który hermetyzuje zestaw zawierający moduł.</span><span class="sxs-lookup"><span data-stu-id="53816-117">Use the <xref:System.Reflection.Module.Assembly%2A?displayProperty=nameWithType> property to locate an object that encapsulates the assembly containing the module.</span></span> <span data-ttu-id="53816-118">Zestaw, który hermetyzuje typ, można uzyskać bezpośrednio przy użyciu <xref:System.Type.Assembly%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="53816-118">You can obtain the assembly that encapsulates the type directly by using the <xref:System.Type.Assembly%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="systemtype-and-constructorinfo"></a><span data-ttu-id="53816-119">System. Type i ConstructorInfo</span><span class="sxs-lookup"><span data-stu-id="53816-119">System.Type and ConstructorInfo</span></span>  
 <span data-ttu-id="53816-120">Poniższy przykład pokazuje, <xref:System.String> jak wyświetlić listę konstruktorów dla klasy, w tym przypadku klasy.</span><span class="sxs-lookup"><span data-stu-id="53816-120">The following example shows how to list the constructors for a class, in this case, the <xref:System.String> class.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Types.ViewInfo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source1.cs#1)]
 [!code-vb[Conceptual.Types.ViewInfo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source1.vb#1)]  
  
## <a name="memberinfo-methodinfo-fieldinfo-and-propertyinfo"></a><span data-ttu-id="53816-121">MemberInfo, MethodInfo, FieldInfo i PropertyInfo</span><span class="sxs-lookup"><span data-stu-id="53816-121">MemberInfo, MethodInfo, FieldInfo, and PropertyInfo</span></span>  
 <span data-ttu-id="53816-122">Uzyskaj informacje na temat metod, właściwości, zdarzeń i pól typu, przy użyciu <xref:System.Reflection.MemberInfo>obiektów <xref:System.Reflection.MethodInfo> <xref:System.Reflection.FieldInfo>,,, <xref:System.Reflection.PropertyInfo> lub.</span><span class="sxs-lookup"><span data-stu-id="53816-122">Obtain information about the type's methods, properties, events, and fields using <xref:System.Reflection.MemberInfo>, <xref:System.Reflection.MethodInfo>, <xref:System.Reflection.FieldInfo>, or <xref:System.Reflection.PropertyInfo> objects.</span></span>  
  
 <span data-ttu-id="53816-123">Poniższy przykład używa **MemberInfo** , aby wyświetlić listę elementów członkowskich w klasie **System. IO. File** <xref:System.Type.IsPublic%2A> i używa właściwości, aby określić widoczność klasy.</span><span class="sxs-lookup"><span data-stu-id="53816-123">The following example uses **MemberInfo** to list the number of members in the **System.IO.File** class and uses the <xref:System.Type.IsPublic%2A> property to determine the visibility of the class.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Types.ViewInfo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source2.cs#2)]
 [!code-vb[Conceptual.Types.ViewInfo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source2.vb#2)]  
  
 <span data-ttu-id="53816-124">Poniższy przykład sprawdza typ określonego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="53816-124">The following example investigates the type of the specified member.</span></span> <span data-ttu-id="53816-125">Wykonuje odbicie na elemencie członkowskim klasy **MemberInfo** i wyświetla jego typ.</span><span class="sxs-lookup"><span data-stu-id="53816-125">It performs reflection on a member of the **MemberInfo** class, and lists its type.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.Types.ViewInfo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source3.cs#3)]
 [!code-vb[Conceptual.Types.ViewInfo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source3.vb#3)]  
  
 <span data-ttu-id="53816-126">W poniższym przykładzie są wykorzystywane wszystkie klasy  **\*informacyjne** odbicia <xref:System.Reflection.BindingFlags> wraz z, aby wyświetlić listę wszystkich elementów członkowskich (konstruktorów, pól, właściwości, zdarzeń i metod) określonej klasy, dzieląc elementy członkowskie na statyczne i wystąpienie Rodzaj.</span><span class="sxs-lookup"><span data-stu-id="53816-126">The following example uses all the Reflection **\*Info** classes along with <xref:System.Reflection.BindingFlags> to list all the members (constructors, fields, properties, events, and methods) of the specified class, dividing the members into static and instance categories.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.Types.ViewInfo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source4.cs#4)]
 [!code-vb[Conceptual.Types.ViewInfo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source4.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="53816-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="53816-127">See also</span></span>

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
- [<span data-ttu-id="53816-128">Odbicie i typy ogólne</span><span class="sxs-lookup"><span data-stu-id="53816-128">Reflection and Generic Types</span></span>](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md)
