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
ms.locfileid: "33399746"
---
# <a name="viewing-type-information"></a>Wyświetlanie informacji o typie
<xref:System.Type?displayProperty=nameWithType> Klasy jest podstawą odbicia. Tworzy środowisko uruchomieniowe języka wspólnego **typu** dla typu załadowanego podczas żądania odbicia. Można użyć **typu** metod, pola, właściwości i zagnieżdżonych klas, aby dowiedzieć się wszystkiego o tego typu obiektu.  
  
 Użyj <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> lub <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType> uzyskanie **typu** obiektów z zestawów, które nie zostały załadowane, przekazywanie nazwy typu lub typy mają. Użyj <xref:System.Type.GetType%2A?displayProperty=nameWithType> uzyskanie **typu** obiektów z zestawu, który został już załadowany. Użyj <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType> i <xref:System.Reflection.Module.GetTypes%2A?displayProperty=nameWithType> uzyskać modułu **typu** obiektów.  
  
> [!NOTE]
>  Do badania i manipulowania typy ogólne i metody, można znaleźć dodatkowe informacje zawarte w [odbicie i typy ogólne](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md) i [porady: zbadanie i rodzajowy wystąpień typów za pomocą odbicia](../../../docs/framework/reflection-and-codedom/how-to-examine-and-instantiate-generic-types-with-reflection.md).  
  
 W poniższym przykładzie przedstawiono składnię niezbędne, aby uzyskać <xref:System.Reflection.Assembly> obiektu i modułów zestawu.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source5.cpp#6)]
 [!code-csharp[Conceptual.Types.ViewInfo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source5.cs#6)]
 [!code-vb[Conceptual.Types.ViewInfo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source5.vb#6)]  
  
 W poniższym przykładzie pokazano, uzyskiwanie **typu** obiektów z załadowanego zestawu.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source5.cpp#7)]
 [!code-csharp[Conceptual.Types.ViewInfo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source5.cs#7)]
 [!code-vb[Conceptual.Types.ViewInfo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source5.vb#7)]  
  
 Po uzyskaniu **typu**, istnieje wiele sposobów, można znaleźć informacje o elementach członkowskich tego typu. Na przykład można znaleźć o elementy członkowskie wszystkie typu przez wywołanie metody <xref:System.Type.GetMembers%2A?displayProperty=nameWithType> metodę, która pobiera tablicę <xref:System.Reflection.MemberInfo> opisujące wszystkich członków bieżącego typu obiektów.  
  
 Możesz również użyć metod w **typu** klasy można pobrać informacji o co najmniej jeden konstruktorów, metod, zdarzenia, pola lub właściwości, które określają według nazwy. Na przykład <xref:System.Type.GetConstructor%2A?displayProperty=nameWithType> hermetyzuje określonego konstruktora klasy.  
  
 Jeśli masz **typu**, można użyć <xref:System.Type.Module%2A?displayProperty=nameWithType> właściwości, aby uzyskać obiekt hermetyzujący zawierającego tego typu modułu. Użyj <xref:System.Reflection.Module.Assembly%2A?displayProperty=nameWithType> właściwości do zlokalizowania obiektu, który hermetyzuje zestawu zawierającego modułu. Można uzyskać zestawu, który hermetyzuje typ bezpośrednio za pomocą <xref:System.Type.Assembly%2A?displayProperty=nameWithType> właściwości.  
  
## <a name="systemtype-and-constructorinfo"></a>System.Type i ConstructorInfo  
 Poniższy przykład przedstawia sposób listy konstruktorów dla klasy, w tym przypadku <xref:System.String> klasy.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Types.ViewInfo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source1.cs#1)]
 [!code-vb[Conceptual.Types.ViewInfo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source1.vb#1)]  
  
## <a name="memberinfo-methodinfo-fieldinfo-and-propertyinfo"></a>Element MemberInfo, MethodInfo FieldInfo i PropertyInfo  
 Uzyskaj informacje na temat metody, właściwości, zdarzeń i pola przy użyciu typu <xref:System.Reflection.MemberInfo>, <xref:System.Reflection.MethodInfo>, <xref:System.Reflection.FieldInfo>, lub <xref:System.Reflection.PropertyInfo> obiektów.  
  
 W poniższym przykładzie użyto **MemberInfo** do wyświetlenia liczba elementów członkowskich w **System.IO.File** klasy i używa <xref:System.Type.IsPublic%2A> właściwości w celu określenia widoczność klasy.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Types.ViewInfo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source2.cs#2)]
 [!code-vb[Conceptual.Types.ViewInfo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source2.vb#2)]  
  
 Poniższy przykład sprawdza typ określonego elementu członkowskiego. Wykonuje odbicia w elemencie **MemberInfo** klasy, a jego typu.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.Types.ViewInfo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source3.cs#3)]
 [!code-vb[Conceptual.Types.ViewInfo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source3.vb#3)]  
  
 W poniższym przykładzie użyto wszystkich odbicia  **\*informacji** klasy wraz z programem <xref:System.Reflection.BindingFlags> Aby wyświetlić listę wszystkich członków (konstruktorów, pola, właściwości, zdarzeń i metody) z określonej klasy dzielenia elementów członkowskich w statycznej i wystąpienie kategorii.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.Types.ViewInfo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source4.cs#4)]
 [!code-vb[Conceptual.Types.ViewInfo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source4.vb#4)]  
  
## <a name="see-also"></a>Zobacz też  
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
 [Odbicie i typy ogólne](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md)
