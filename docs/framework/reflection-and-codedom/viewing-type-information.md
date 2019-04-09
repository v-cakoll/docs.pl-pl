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
ms.openlocfilehash: 2028bc8d9f160daef8afcdf881e1dfd514b4c94f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59190406"
---
# <a name="viewing-type-information"></a>Wyświetlanie informacji o typie
<xref:System.Type?displayProperty=nameWithType> Klasy stanowi podstawę do odbicia. Środowisko uruchomieniowe języka wspólnego tworzy **typu** załadować typu, gdy odbicie żąda ona. Możesz użyć **typu** metody, pola, właściwości i klasy zagnieżdżone, aby dowiedzieć się wszystkiego o usłudze typu obiektu.  
  
 Użyj <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> lub <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType> uzyskać **typu** obiektów z zestawów, które nie zostały załadowane, przekazując nazwę typu lub typów, które chcesz. Użyj <xref:System.Type.GetType%2A?displayProperty=nameWithType> można pobrać **typu** obiektów z zestawu, który jest już załadowany. Użyj <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType> i <xref:System.Reflection.Module.GetTypes%2A?displayProperty=nameWithType> uzyskać moduł **typu** obiektów.  
  
> [!NOTE]
>  Do badania i manipulowania typy ogólne i metody, można znaleźć dodatkowe informacje zawarte w [odbicie i typy ogólne](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md) i [jak: Badanie i tworzenie wystąpień typów ogólnych za pomocą odbicia](../../../docs/framework/reflection-and-codedom/how-to-examine-and-instantiate-generic-types-with-reflection.md).  
  
 Poniższy przykład pokazuje składnię niezbędne do doprowadzenia <xref:System.Reflection.Assembly> obiektu i modułów dla zestawu.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source5.cpp#6)]
 [!code-csharp[Conceptual.Types.ViewInfo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source5.cs#6)]
 [!code-vb[Conceptual.Types.ViewInfo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source5.vb#6)]  
  
 W poniższym przykładzie pokazano uzyskiwanie **typu** obiektów z załadowany zestaw.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source5.cpp#7)]
 [!code-csharp[Conceptual.Types.ViewInfo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source5.cs#7)]
 [!code-vb[Conceptual.Types.ViewInfo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source5.vb#7)]  
  
 Po uzyskaniu **typu**, istnieje wiele sposobów można znaleźć informacje o elementach członkowskich tego typu. Na przykład, znajdziesz o wszystkich typów członków, wywołując <xref:System.Type.GetMembers%2A?displayProperty=nameWithType> metody, która pobiera tablicę <xref:System.Reflection.MemberInfo> opisującej każdy z elementów członkowskich bieżącego typu obiektów.  
  
 Można również użyć metod na **typu** klasy do pobrania informacji o jeden lub więcej konstruktorów, metod, zdarzeń, pola lub właściwości, które określają według nazwy. Na przykład <xref:System.Type.GetConstructor%2A?displayProperty=nameWithType> hermetyzuje określonego konstruktora klasy.  
  
 Jeśli masz **typu**, możesz użyć <xref:System.Type.Module%2A?displayProperty=nameWithType> właściwość, aby uzyskać obiekt, który hermetyzuje moduł zawierający tego typu. Użyj <xref:System.Reflection.Module.Assembly%2A?displayProperty=nameWithType> właściwości do zlokalizowania obiektu, który hermetyzuje zestaw zawierający modułu. Można uzyskać zestawu, który hermetyzuje typ bezpośrednio przy użyciu <xref:System.Type.Assembly%2A?displayProperty=nameWithType> właściwości.  
  
## <a name="systemtype-and-constructorinfo"></a>System.Type i ConstructorInfo —  
 Poniższy przykład ilustruje sposób wyświetlenia listy konstruktory dla klas, w tym przypadku <xref:System.String> klasy.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Types.ViewInfo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source1.cs#1)]
 [!code-vb[Conceptual.Types.ViewInfo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source1.vb#1)]  
  
## <a name="memberinfo-methodinfo-fieldinfo-and-propertyinfo"></a>Element MemberInfo, MethodInfo, FieldInfo i PropertyInfo  
 Uzyskać informacje na temat metody, właściwości, zdarzeń i pola za pomocą typu <xref:System.Reflection.MemberInfo>, <xref:System.Reflection.MethodInfo>, <xref:System.Reflection.FieldInfo>, lub <xref:System.Reflection.PropertyInfo> obiektów.  
  
 W poniższym przykładzie użyto **MemberInfo** Aby wyświetlić listę liczba elementów członkowskich w **System.IO.File** klasy i używa <xref:System.Type.IsPublic%2A> właściwości, aby ustalić widoczność klasy.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Types.ViewInfo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source2.cs#2)]
 [!code-vb[Conceptual.Types.ViewInfo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source2.vb#2)]  
  
 Poniższy przykład sprawdza typ określonego elementu członkowskiego. Wykonuje odbicie w elemencie **MemberInfo** klasy i wyświetla typ dysku.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.Types.ViewInfo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source3.cs#3)]
 [!code-vb[Conceptual.Types.ViewInfo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source3.vb#3)]  
  
 W poniższym przykładzie użyto wszystkich odbicia  **\*informacje** klasy wraz z <xref:System.Reflection.BindingFlags> Aby wyświetlić listę wszystkich członków (konstruktory, pola, właściwości, zdarzenia i metody) określonej klasy dzielenia elementów członkowskich w statycznej i wystąpienie kategorii.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.Types.ViewInfo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source4.cs#4)]
 [!code-vb[Conceptual.Types.ViewInfo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source4.vb#4)]  
  
## <a name="see-also"></a>Zobacz także

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
- [Odbicie i typy ogólne](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md)
