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
ms.openlocfilehash: bf119ff547df59cd369d688fd81ab058893614f2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130016"
---
# <a name="viewing-type-information"></a><span data-ttu-id="9cb38-102">Wyświetlanie informacji o typie</span><span class="sxs-lookup"><span data-stu-id="9cb38-102">Viewing Type Information</span></span>
<span data-ttu-id="9cb38-103">Klasa <xref:System.Type?displayProperty=nameWithType> jest środkowa do odbicia.</span><span class="sxs-lookup"><span data-stu-id="9cb38-103">The <xref:System.Type?displayProperty=nameWithType> class is central to reflection.</span></span> <span data-ttu-id="9cb38-104">Środowisko uruchomieniowe języka wspólnego tworzy **Typ** załadowanego typu podczas odbicia żądania.</span><span class="sxs-lookup"><span data-stu-id="9cb38-104">The common language runtime creates the **Type** for a loaded type when reflection requests it.</span></span> <span data-ttu-id="9cb38-105">Możesz użyć metod, pól, właściwości i klas zagnieżdżonych obiektu **typu** , aby dowiedzieć się wszystkiego o tym typie.</span><span class="sxs-lookup"><span data-stu-id="9cb38-105">You can use a **Type** object's methods, fields, properties, and nested classes to find out everything about that type.</span></span>  
  
 <span data-ttu-id="9cb38-106">Użyj <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> lub <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType>, aby uzyskać obiekty **typu** z zestawów, które nie zostały załadowane, przekazując nazwę żądanego typu lub typów.</span><span class="sxs-lookup"><span data-stu-id="9cb38-106">Use <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType> to obtain **Type** objects from assemblies that have not been loaded, passing in the name of the type or types you want.</span></span> <span data-ttu-id="9cb38-107">Użyj <xref:System.Type.GetType%2A?displayProperty=nameWithType>, aby uzyskać obiekty **typu** z zestawu, który jest już załadowany.</span><span class="sxs-lookup"><span data-stu-id="9cb38-107">Use <xref:System.Type.GetType%2A?displayProperty=nameWithType> to get the **Type** objects from an assembly that is already loaded.</span></span> <span data-ttu-id="9cb38-108">Użyj <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType> i <xref:System.Reflection.Module.GetTypes%2A?displayProperty=nameWithType>, aby uzyskać obiekty **typu** modułu.</span><span class="sxs-lookup"><span data-stu-id="9cb38-108">Use <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType> and <xref:System.Reflection.Module.GetTypes%2A?displayProperty=nameWithType> to obtain module **Type** objects.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9cb38-109">Jeśli chcesz sprawdzić typy ogólne i metody i manipulować nimi, zapoznaj się z dodatkowymi informacjami podanymi w obszarze [odbicie i typy ogólne](reflection-and-generic-types.md) oraz [jak: sprawdzanie i Tworzenie wystąpień typów ogólnych za pomocą odbicia](how-to-examine-and-instantiate-generic-types-with-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="9cb38-109">If you want to examine and manipulate generic types and methods, please see the additional information provided in [Reflection and Generic Types](reflection-and-generic-types.md) and [How to: Examine and Instantiate Generic Types with Reflection](how-to-examine-and-instantiate-generic-types-with-reflection.md).</span></span>  
  
 <span data-ttu-id="9cb38-110">Poniższy przykład pokazuje składnię niezbędną do uzyskania <xref:System.Reflection.Assembly> obiektu i modułu dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="9cb38-110">The following example shows the syntax necessary to get the <xref:System.Reflection.Assembly> object and module for an assembly.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source5.cpp#6)]
 [!code-csharp[Conceptual.Types.ViewInfo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source5.cs#6)]
 [!code-vb[Conceptual.Types.ViewInfo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source5.vb#6)]  
  
 <span data-ttu-id="9cb38-111">Poniższy przykład ilustruje pobieranie obiektów **typu** z załadowanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="9cb38-111">The following example demonstrates getting **Type** objects from a loaded assembly.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source5.cpp#7)]
 [!code-csharp[Conceptual.Types.ViewInfo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source5.cs#7)]
 [!code-vb[Conceptual.Types.ViewInfo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source5.vb#7)]  
  
 <span data-ttu-id="9cb38-112">Po uzyskaniu **typu**istnieje wiele sposobów odnajdywania informacji o elementach członkowskich tego typu.</span><span class="sxs-lookup"><span data-stu-id="9cb38-112">Once you obtain a **Type**, there are many ways you can discover information about the members of that type.</span></span> <span data-ttu-id="9cb38-113">Na przykład można dowiedzieć się więcej o wszystkich elementach członkowskich typu, wywołując metodę <xref:System.Type.GetMembers%2A?displayProperty=nameWithType>, która uzyskuje tablicę obiektów <xref:System.Reflection.MemberInfo> opisujących każdy element członkowski bieżącego typu.</span><span class="sxs-lookup"><span data-stu-id="9cb38-113">For example, you can find out about all the type's members by calling the <xref:System.Type.GetMembers%2A?displayProperty=nameWithType> method, which obtains an array of <xref:System.Reflection.MemberInfo> objects describing each of the members of the current type.</span></span>  
  
 <span data-ttu-id="9cb38-114">Można również użyć metod klasy **Type** , aby pobrać informacje o jednym lub wielu konstruktorach, metodach, zdarzeniach, polach lub właściwościach określonych przez nazwę.</span><span class="sxs-lookup"><span data-stu-id="9cb38-114">You can also use methods on the **Type** class to retrieve information about one or more constructors, methods, events, fields, or properties that you specify by name.</span></span> <span data-ttu-id="9cb38-115">Na przykład <xref:System.Type.GetConstructor%2A?displayProperty=nameWithType> hermetyzuje określony Konstruktor bieżącej klasy.</span><span class="sxs-lookup"><span data-stu-id="9cb38-115">For example, <xref:System.Type.GetConstructor%2A?displayProperty=nameWithType> encapsulates a specific constructor of the current class.</span></span>  
  
 <span data-ttu-id="9cb38-116">Jeśli masz **Typ**, możesz użyć właściwości <xref:System.Type.Module%2A?displayProperty=nameWithType>, aby uzyskać obiekt, który hermetyzuje moduł zawierający ten typ.</span><span class="sxs-lookup"><span data-stu-id="9cb38-116">If you have a **Type**, you can use the <xref:System.Type.Module%2A?displayProperty=nameWithType> property to obtain an object that encapsulates the module containing that type.</span></span> <span data-ttu-id="9cb38-117">Użyj właściwości <xref:System.Reflection.Module.Assembly%2A?displayProperty=nameWithType>, aby zlokalizować obiekt, który hermetyzuje zestaw zawierający moduł.</span><span class="sxs-lookup"><span data-stu-id="9cb38-117">Use the <xref:System.Reflection.Module.Assembly%2A?displayProperty=nameWithType> property to locate an object that encapsulates the assembly containing the module.</span></span> <span data-ttu-id="9cb38-118">Możesz uzyskać zestaw, który hermetyzuje typ bezpośrednio przy użyciu właściwości <xref:System.Type.Assembly%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9cb38-118">You can obtain the assembly that encapsulates the type directly by using the <xref:System.Type.Assembly%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="systemtype-and-constructorinfo"></a><span data-ttu-id="9cb38-119">System. Type i ConstructorInfo</span><span class="sxs-lookup"><span data-stu-id="9cb38-119">System.Type and ConstructorInfo</span></span>  
 <span data-ttu-id="9cb38-120">Poniższy przykład pokazuje, jak wyświetlić listę konstruktorów dla klasy, w tym przypadku klasy <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="9cb38-120">The following example shows how to list the constructors for a class, in this case, the <xref:System.String> class.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Types.ViewInfo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source1.cs#1)]
 [!code-vb[Conceptual.Types.ViewInfo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source1.vb#1)]  
  
## <a name="memberinfo-methodinfo-fieldinfo-and-propertyinfo"></a><span data-ttu-id="9cb38-121">MemberInfo, MethodInfo, FieldInfo i PropertyInfo</span><span class="sxs-lookup"><span data-stu-id="9cb38-121">MemberInfo, MethodInfo, FieldInfo, and PropertyInfo</span></span>  
 <span data-ttu-id="9cb38-122">Uzyskaj informacje na temat metod, właściwości, zdarzeń i pól typu, przy użyciu <xref:System.Reflection.MemberInfo>, <xref:System.Reflection.MethodInfo>, <xref:System.Reflection.FieldInfo>lub <xref:System.Reflection.PropertyInfo> obiektów.</span><span class="sxs-lookup"><span data-stu-id="9cb38-122">Obtain information about the type's methods, properties, events, and fields using <xref:System.Reflection.MemberInfo>, <xref:System.Reflection.MethodInfo>, <xref:System.Reflection.FieldInfo>, or <xref:System.Reflection.PropertyInfo> objects.</span></span>  
  
 <span data-ttu-id="9cb38-123">Poniższy przykład używa **MemberInfo** , aby wyświetlić liczbę elementów członkowskich w klasie **System. IO. File** i używa właściwości <xref:System.Type.IsPublic%2A>, aby określić widoczność klasy.</span><span class="sxs-lookup"><span data-stu-id="9cb38-123">The following example uses **MemberInfo** to list the number of members in the **System.IO.File** class and uses the <xref:System.Type.IsPublic%2A> property to determine the visibility of the class.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Types.ViewInfo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source2.cs#2)]
 [!code-vb[Conceptual.Types.ViewInfo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source2.vb#2)]  
  
 <span data-ttu-id="9cb38-124">Poniższy przykład sprawdza typ określonego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="9cb38-124">The following example investigates the type of the specified member.</span></span> <span data-ttu-id="9cb38-125">Wykonuje odbicie na elemencie członkowskim klasy **MemberInfo** i wyświetla jego typ.</span><span class="sxs-lookup"><span data-stu-id="9cb38-125">It performs reflection on a member of the **MemberInfo** class, and lists its type.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.Types.ViewInfo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source3.cs#3)]
 [!code-vb[Conceptual.Types.ViewInfo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source3.vb#3)]  
  
 <span data-ttu-id="9cb38-126">W poniższym przykładzie zastosowano wszystkie klasy **\*informacji** o odbiciu wraz z <xref:System.Reflection.BindingFlags>, aby wyświetlić listę wszystkich członków (konstruktorów, pól, właściwości, zdarzeń i metod) określonej klasy, dzieląc elementy członkowskie na kategorie statyczne i wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="9cb38-126">The following example uses all the Reflection **\*Info** classes along with <xref:System.Reflection.BindingFlags> to list all the members (constructors, fields, properties, events, and methods) of the specified class, dividing the members into static and instance categories.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.Types.ViewInfo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source4.cs#4)]
 [!code-vb[Conceptual.Types.ViewInfo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source4.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="9cb38-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9cb38-127">See also</span></span>

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
- [<span data-ttu-id="9cb38-128">Odbicie i typy ogólne</span><span class="sxs-lookup"><span data-stu-id="9cb38-128">Reflection and Generic Types</span></span>](reflection-and-generic-types.md)
