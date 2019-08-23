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
# <a name="viewing-type-information"></a>Wyświetlanie informacji o typie
<xref:System.Type?displayProperty=nameWithType> Klasa jest centralną odbiciem. Środowisko uruchomieniowe języka wspólnego tworzy **Typ** załadowanego typu podczas odbicia żądania. Możesz użyć metod, pól, właściwości i klas zagnieżdżonych obiektu **typu** , aby dowiedzieć się wszystkiego o tym typie.  
  
 Użyj <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> lub<xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType> , aby uzyskać obiekty **typu** z zestawów, które nie zostały załadowane, przekazując nazwę żądanego typu lub typów. Służy <xref:System.Type.GetType%2A?displayProperty=nameWithType> do pobierania obiektów **typu** z zestawu, który jest już załadowany. Użyj <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType> i <xref:System.Reflection.Module.GetTypes%2A?displayProperty=nameWithType> , aby uzyskać obiekty **typu** modułu.  
  
> [!NOTE]
> Jeśli chcesz sprawdzić typy ogólne i metody i manipulować nimi, zapoznaj się z dodatkowymi informacjami podanymi w obszarze odbicie [ [i typy ogólne](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md) oraz jak: Sprawdzanie i Tworzenie wystąpień typów ogólnych za](../../../docs/framework/reflection-and-codedom/how-to-examine-and-instantiate-generic-types-with-reflection.md)pomocą odbicia.  
  
 Poniższy przykład pokazuje składnię niezbędną do pobrania <xref:System.Reflection.Assembly> obiektu i modułu dla zestawu.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source5.cpp#6)]
 [!code-csharp[Conceptual.Types.ViewInfo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source5.cs#6)]
 [!code-vb[Conceptual.Types.ViewInfo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source5.vb#6)]  
  
 Poniższy przykład ilustruje pobieranie obiektów **typu** z załadowanego zestawu.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source5.cpp#7)]
 [!code-csharp[Conceptual.Types.ViewInfo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source5.cs#7)]
 [!code-vb[Conceptual.Types.ViewInfo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source5.vb#7)]  
  
 Po uzyskaniu **typu**istnieje wiele sposobów odnajdywania informacji o elementach członkowskich tego typu. Na przykład można dowiedzieć się więcej o wszystkich elementach członkowskich typu przez wywołanie <xref:System.Type.GetMembers%2A?displayProperty=nameWithType> metody, która uzyskuje <xref:System.Reflection.MemberInfo> tablicę obiektów opisującą każdy element członkowski bieżącego typu.  
  
 Można również użyć metod klasy **Type** , aby pobrać informacje o jednym lub wielu konstruktorach, metodach, zdarzeniach, polach lub właściwościach określonych przez nazwę. Na przykład <xref:System.Type.GetConstructor%2A?displayProperty=nameWithType> hermetyzuje określony Konstruktor bieżącej klasy.  
  
 Jeśli masz **Typ**, możesz użyć <xref:System.Type.Module%2A?displayProperty=nameWithType> właściwości, aby uzyskać obiekt, który hermetyzuje moduł zawierający ten typ. <xref:System.Reflection.Module.Assembly%2A?displayProperty=nameWithType> Użyj właściwości, aby zlokalizować obiekt, który hermetyzuje zestaw zawierający moduł. Zestaw, który hermetyzuje typ, można uzyskać bezpośrednio przy użyciu <xref:System.Type.Assembly%2A?displayProperty=nameWithType> właściwości.  
  
## <a name="systemtype-and-constructorinfo"></a>System. Type i ConstructorInfo  
 Poniższy przykład pokazuje, <xref:System.String> jak wyświetlić listę konstruktorów dla klasy, w tym przypadku klasy.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Types.ViewInfo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source1.cs#1)]
 [!code-vb[Conceptual.Types.ViewInfo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source1.vb#1)]  
  
## <a name="memberinfo-methodinfo-fieldinfo-and-propertyinfo"></a>MemberInfo, MethodInfo, FieldInfo i PropertyInfo  
 Uzyskaj informacje na temat metod, właściwości, zdarzeń i pól typu, przy użyciu <xref:System.Reflection.MemberInfo>obiektów <xref:System.Reflection.MethodInfo> <xref:System.Reflection.FieldInfo>,,, <xref:System.Reflection.PropertyInfo> lub.  
  
 Poniższy przykład używa **MemberInfo** , aby wyświetlić listę elementów członkowskich w klasie **System. IO. File** <xref:System.Type.IsPublic%2A> i używa właściwości, aby określić widoczność klasy.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Types.ViewInfo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source2.cs#2)]
 [!code-vb[Conceptual.Types.ViewInfo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source2.vb#2)]  
  
 Poniższy przykład sprawdza typ określonego elementu członkowskiego. Wykonuje odbicie na elemencie członkowskim klasy **MemberInfo** i wyświetla jego typ.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.Types.ViewInfo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source3.cs#3)]
 [!code-vb[Conceptual.Types.ViewInfo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source3.vb#3)]  
  
 W poniższym przykładzie są wykorzystywane wszystkie klasy  **\*informacyjne** odbicia <xref:System.Reflection.BindingFlags> wraz z, aby wyświetlić listę wszystkich elementów członkowskich (konstruktorów, pól, właściwości, zdarzeń i metod) określonej klasy, dzieląc elementy członkowskie na statyczne i wystąpienie Rodzaj.  
  
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
