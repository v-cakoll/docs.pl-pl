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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7021a984f844660c45ae3e2d98569432ab64b657
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2018
ms.locfileid: "45668382"
---
# <a name="retrieving-information-stored-in-attributes"></a>Pobieranie informacji przechowywanych w atrybutach
Podczas pobierania atrybutów niestandardowych jest prostym procesem. Najpierw należy zadeklarować wystąpienia atrybutu, który ma zostać pobrane. Następnie należy użyć <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType> metodę, aby zainicjować nowy atrybut, aby wartość atrybutu, który ma zostać pobrane. Po zainicjowaniu nowy atrybut, po prostu użyć jego właściwości w celu uzyskania wartości.  
  
> [!IMPORTANT]
>  W tym temacie opisano, jak można pobrać atrybutów dla kodu ładowane do kontekstu wykonywania. Aby pobrać atrybutów dla kodu ładowane do kontekstu reflection-only, należy użyć <xref:System.Reflection.CustomAttributeData> klasy, jak pokazano w [porady: ładowanie zestawów do kontekstu Reflection-Only](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).  
  
 W tej sekcji opisano następujące sposoby pobierania atrybutów:  
  
-   [Trwa pobieranie jedno wystąpienie atrybutu](#cpconretrievingsingleinstanceofattribute)  
  
-   [Trwa pobieranie wielu wystąpień zastosowany do tego samego zakresu](#cpconretrievingmultipleinstancesofattributeappliedtosamescope)  
  
-   [Trwa pobieranie wielu wystąpień atrybutem zastosowanym do różnych zakresów](#cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes)  
  
<a name="cpconretrievingsingleinstanceofattribute"></a>   
## <a name="retrieving-a-single-instance-of-an-attribute"></a>Trwa pobieranie jedno wystąpienie atrybutu  
 W poniższym przykładzie `DeveloperAttribute` (opisanej w poprzedniej sekcji) jest stosowany do `MainApp` klasy na poziomie klasy. `GetAttribute` Metoda używa **metody GetCustomAttribute** można pobrać wartości przechowywane w `DeveloperAttribute` na poziomie klasy, przed wyświetleniem ich w konsoli.  
  
 [!code-cpp[Conceptual.Attributes.Usage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#18)]
 [!code-csharp[Conceptual.Attributes.Usage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#18)]
 [!code-vb[Conceptual.Attributes.Usage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#18)]  
  
 Ten program wyświetla następujący tekst podczas wykonywania.  
  
```  
The Name Attribute is: Joan Smith.  
The Level Attribute is: 42.  
The Reviewed Attribute is: True.  
```  
  
 Jeśli ten atrybut nie zostanie znaleziony, **metody GetCustomAttribute** inicjuje metodę `MyAttribute` ma wartość null. W tym przykładzie, sprawdza `MyAttribute` dla wystąpienia usługi i powiadamia użytkownika, jeśli atrybut nie zostanie znaleziony. Jeśli `DeveloperAttribute` nie znajduje się w zakresie klasy, zostanie wyświetlony następujący komunikat do konsoli.  
  
```  
The attribute was not found.   
```  
  
 W tym przykładzie przyjęto założenie, że definicja atrybutu znajduje się w bieżącej przestrzeni nazw. Pamiętaj, aby zaimportować obszar nazw, w której znajduje się definicja atrybutu, jeśli nie znajduje się w bieżącej przestrzeni nazw.  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtosamescope"></a>   
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-the-same-scope"></a>Trwa pobieranie wielu wystąpień zastosowany do tego samego zakresu  
 W poprzednim przykładzie klasę, aby sprawdzić i określonych atrybutów, można znaleźć są przekazywane do <xref:System.Attribute.GetCustomAttribute%2A>. Ten kod działa dobrze jeśli tylko jedno wystąpienie atrybutu jest stosowana na poziomie klasy. Jednakże, jeśli wiele wystąpień atrybutu są stosowane na tym samym poziomie klasy **metody GetCustomAttribute** metody nie uzyskać wszystkie informacje. W przypadkach, w której wiele wystąpień tego samego atrybutu są stosowane do tego samego zakresu, można użyć <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType> umieścić wszystkie wystąpienia atrybutu do tablicy. Na przykład, jeśli dwa wystąpienia `DeveloperAttribute` są stosowane na poziomie klasy w tej samej klasy `GetAttribute` metoda można modyfikować, aby wyświetlić informacje znajdujące się w obu atrybutów. Pamiętaj, aby zastosować wiele atrybutów na tym samym poziomie atrybutu muszą być zdefiniowane przy użyciu **AllowMultiple** właściwością **true** w <xref:System.AttributeUsageAttribute>.  
  
 Poniższy przykład kodu pokazuje sposób użycia **getcustomattributes —** metodę, aby utworzyć tablicę, która odwołuje się do wszystkich wystąpień `DeveloperAttribute` w dowolnej podanej klasy. Wartości wszystkich atrybutów są następnie wyświetlane w konsoli.  
  
 [!code-cpp[Conceptual.Attributes.Usage#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#19)]
 [!code-csharp[Conceptual.Attributes.Usage#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#19)]
 [!code-vb[Conceptual.Attributes.Usage#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#19)]  
  
 Jeśli nie zostaną znalezione żadne atrybuty, ten kod ostrzega o tym użytkownika. W przeciwnym razie informacje zawarte w obu przypadkach `DeveloperAttribute` jest wyświetlana.  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes"></a>   
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-different-scopes"></a>Trwa pobieranie wielu wystąpień atrybutem zastosowanym do różnych zakresów  
 <xref:System.Attribute.GetCustomAttributes%2A> i <xref:System.Attribute.GetCustomAttribute%2A> metody wyszukiwania całej klasy i nie zwraca wszystkich wystąpień atrybutu w tej klasie. Zamiast wyszukiwania tylko jeden określonej metody lub elementu członkowskiego w danym momencie. Jeśli posiadasz klasę za pomocą tego samego atrybutu, które są stosowane do każdego członka i chcesz pobrać wartości wszystkich atrybutów, które są stosowane do tych członków, należy podać co metoda lub elementu członkowskiego indywidualnie do **getcustomattributes —** i  **Metody GetCustomAttribute**.  
  
 Poniższy przykład kodu klasy jako parametr przyjmuje i wyszukuje `DeveloperAttribute` (zdefiniowanych wcześniej) na poziomie klasy, a na każdej poszczególne metody tej klasy.  
  
 [!code-cpp[Conceptual.Attributes.Usage#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#20)]
 [!code-csharp[Conceptual.Attributes.Usage#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#20)]
 [!code-vb[Conceptual.Attributes.Usage#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#20)]  
  
 Jeśli nie wystąpienia `DeveloperAttribute` znajdują się na poziomie metody lub klasy, `GetAttribute` metoda powiadamia użytkownika, który nie znaleziono żadnych atrybutów i wyświetla nazwę metody lub klasy, która nie zawiera atrybutu. Jeśli atrybut zostanie znaleziony, `Name`, `Level`, i `Reviewed` pola są wyświetlane w konsoli.  
  
 Można użyć elementów członkowskich <xref:System.Type> klasy można pobrać pojedynczych metod i składowych w klasie sukces. W tym przykładzie najpierw zapytania **typu** obiektu, aby uzyskać informacje o atrybutach na poziomie klasy. Następnie używa <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> umieszcza wystąpienia wszystkich metod na tablicę <xref:System.Reflection.MemberInfo?displayProperty=nameWithType> obiektów, aby pobrać informacje o atrybutach na poziomie metody. Można również użyć <xref:System.Type.GetProperties%2A?displayProperty=nameWithType> metodę sprawdzania, czy atrybuty na poziomie właściwości lub <xref:System.Type.GetConstructors%2A?displayProperty=nameWithType> pod kątem atrybuty na poziomie konstruktora.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Type?displayProperty=nameWithType>  
- <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType>  
- <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>  
- [Atrybuty](../../../docs/standard/attributes/index.md)
