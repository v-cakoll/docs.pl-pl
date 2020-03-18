---
title: Pobieranie informacji przechowywanych w atrybutach
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- retrieving attributes
- multiple attribute instances
- attributes [.NET Framework], retrieving
ms.assetid: 37dfe4e3-7da0-48b6-a3d9-398981524e1c
ms.openlocfilehash: 4f0f3555ae1ab7e662d5f88ac65739a7c791a964
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78158080"
---
# <a name="retrieving-information-stored-in-attributes"></a>Pobieranie informacji przechowywanych w atrybutach
Pobieranie atrybutu niestandardowego jest prostym procesem. Najpierw zadeklarować wystąpienie atrybutu, który chcesz pobrać. Następnie użyj <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType> metody, aby zainicjować nowy atrybut do wartości atrybutu, który chcesz pobrać. Po zainicjowaniu nowego atrybutu po prostu użyć jego właściwości, aby uzyskać wartości.  
  
> [!IMPORTANT]
> W tym temacie opisano sposób pobierania atrybutów kodu załadowanego do kontekstu wykonywania. Aby pobrać atrybuty dla kodu załadowanego do kontekstu <xref:System.Reflection.CustomAttributeData> tylko do odbicia, należy użyć klasy, jak pokazano w [jak: Załadować zestawy do kontekstu tylko do odbicia](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).  
  
 W tej sekcji opisano następujące sposoby pobierania atrybutów:  
  
- [Pobieranie pojedynczego wystąpienia atrybutu](#cpconretrievingsingleinstanceofattribute)  
  
- [Pobieranie wielu wystąpień atrybutu zastosowanego do tego samego zakresu](#cpconretrievingmultipleinstancesofattributeappliedtosamescope)  
  
- [Pobieranie wielu wystąpień atrybutu zastosowanego do różnych zakresów](#cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes)  
  
<a name="cpconretrievingsingleinstanceofattribute"></a>
## <a name="retrieving-a-single-instance-of-an-attribute"></a>Pobieranie pojedynczego wystąpienia atrybutu  
 W poniższym `DeveloperAttribute` przykładzie (opisane w poprzedniej sekcji) `MainApp` jest stosowany do klasy na poziomie klasy. Metoda `GetAttribute` używa **GetCustomAttribute** do pobierania `DeveloperAttribute` wartości przechowywanych na poziomie klasy przed wyświetleniem ich do konsoli.  
  
 [!code-cpp[Conceptual.Attributes.Usage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#18)]
 [!code-csharp[Conceptual.Attributes.Usage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#18)]
 [!code-vb[Conceptual.Attributes.Usage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#18)]  
  
 Po wykonaniu tego programu wyświetlany jest następujący tekst.  
  
```console  
The Name Attribute is: Joan Smith.  
The Level Attribute is: 42.  
The Reviewed Attribute is: True.  
```  
  
 Jeśli atrybut nie zostanie znaleziony, **GetCustomAttribute** metoda `MyAttribute` inicjuje do wartości null. W tym `MyAttribute` przykładzie sprawdza takie wystąpienie i powiadamia użytkownika, jeśli nie znaleziono atrybutu. `DeveloperAttribute` Jeśli nie zostanie znaleziony w zakresie klasy, do konsoli zostanie wyświetlony następujący komunikat.  
  
```console  
The attribute was not found.
```  
  
 W tym przykładzie przyjęto założenie, że definicja atrybutu znajduje się w bieżącym obszarze nazw. Pamiętaj, aby zaimportować obszar nazw, w którym znajduje się definicja atrybutu, jeśli nie znajduje się w bieżącym obszarze nazw.  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtosamescope"></a>
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-the-same-scope"></a>Pobieranie wielu wystąpień atrybutu zastosowanego do tego samego zakresu  
 W poprzednim przykładzie klasa do sprawdzenia i określony atrybut <xref:System.Attribute.GetCustomAttribute%2A>do znalezienia są przekazywane do . Ten kod działa dobrze, jeśli tylko jedno wystąpienie atrybutu jest stosowany na poziomie klasy. Jednak jeśli wiele wystąpień atrybutu są stosowane na tym samym poziomie klasy, **GetCustomAttribute** Metoda nie pobiera wszystkie informacje. W przypadkach, gdy wiele wystąpień tego samego atrybutu są <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType> stosowane do tego samego zakresu, można użyć do umieszczenia wszystkich wystąpień atrybutu w tablicy. Na przykład jeśli dwa `DeveloperAttribute` wystąpienia są stosowane na poziomie klasy tej `GetAttribute` samej klasy, metoda może być modyfikowana w celu wyświetlenia informacji znalezionych w obu atrybutach. Należy pamiętać, aby zastosować wiele atrybutów na tym samym poziomie, atrybut **true** musi być <xref:System.AttributeUsageAttribute>zdefiniowany z **AllowMultiple** właściwość ustawiona na true w .  
  
 W poniższym przykładzie kodu pokazano, jak używać **GetCustomAttributes** metody `DeveloperAttribute` do tworzenia tablicy, która odwołuje się do wszystkich wystąpień w danej klasy. Wartości wszystkich atrybutów są następnie wyświetlane w konsoli.  
  
 [!code-cpp[Conceptual.Attributes.Usage#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#19)]
 [!code-csharp[Conceptual.Attributes.Usage#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#19)]
 [!code-vb[Conceptual.Attributes.Usage#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#19)]  
  
 Jeśli nie zostaną znalezione żadne atrybuty, ten kod ostrzega użytkownika. W przeciwnym razie wyświetlane `DeveloperAttribute` są informacje zawarte w obu przypadkach.  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes"></a>
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-different-scopes"></a>Pobieranie wielu wystąpień atrybutu zastosowanego do różnych zakresów  
 I <xref:System.Attribute.GetCustomAttributes%2A> <xref:System.Attribute.GetCustomAttribute%2A> metody nie wyszukiwania całej klasy i zwracawszystkie wystąpienia atrybutu w tej klasie. Zamiast tego wyszukują tylko jedną określoną metodę lub element członkowski w danej chwili. Jeśli masz klasę o tym samym przypisaniu zastosowaną do każdego członka i chcesz pobrać wartości we wszystkich atrybutach zastosowanych do tych elementów członkowskich, musisz podać każdą metodę lub element członkowski indywidualnie do **GetCustomAttributes** i **GetCustomAttribute**.  
  
 Poniższy przykład kodu przyjmuje klasę jako parametr `DeveloperAttribute` i wyszukuje (zdefiniowane wcześniej) na poziomie klasy i na każdej indywidualnej metody tej klasy.  
  
 [!code-cpp[Conceptual.Attributes.Usage#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#20)]
 [!code-csharp[Conceptual.Attributes.Usage#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#20)]
 [!code-vb[Conceptual.Attributes.Usage#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#20)]  
  
 Jeśli nie znaleziono `DeveloperAttribute` żadnych wystąpień na poziomie metody `GetAttribute` lub klasy, metoda powiadamia użytkownika, że nie znaleziono żadnych atrybutów i wyświetla nazwę metody lub klasy, która nie zawiera atrybutu. Jeśli zostanie znaleziony atrybut, `Level`pola `Reviewed` i pola zostaną wyświetlone w konsoli. `Name`  
  
 Można użyć członków klasy, <xref:System.Type> aby uzyskać poszczególne metody i elementy członkowskie w klasie przekazany. W tym przykładzie najpierw kwerendy **Type** obiektu, aby uzyskać informacje o atrybutach dla poziomu klasy. Następnie używa <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> się do umieszczania wystąpień wszystkich <xref:System.Reflection.MemberInfo?displayProperty=nameWithType> metod w tablicy obiektów do pobierania informacji o atrybutach dla poziomu metody. Można również użyć <xref:System.Type.GetProperties%2A?displayProperty=nameWithType> metody, aby sprawdzić atrybuty <xref:System.Type.GetConstructors%2A?displayProperty=nameWithType> na poziomie właściwości lub sprawdzić atrybuty na poziomie konstruktora.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>
- [Atrybuty](../../../docs/standard/attributes/index.md)
