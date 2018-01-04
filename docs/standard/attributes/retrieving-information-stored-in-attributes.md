---
title: Pobieranie informacji przechowywanych w atrybutach
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- retrieving attributes
- multiple attribute instances
- attributes [.NET Framework], retrieving
ms.assetid: 37dfe4e3-7da0-48b6-a3d9-398981524e1c
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 146572fb060d1bd37d6eee5b5dce3c255b28f8b2
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="retrieving-information-stored-in-attributes"></a>Pobieranie informacji przechowywanych w atrybutach
Podczas pobierania atrybutów niestandardowych jest prosty proces. Po pierwsze Zadeklaruj wystąpienie atrybutu, który ma zostać pobrane. Następnie należy użyć <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType> metodę, aby zainicjować nowy atrybut na wartość atrybutu do pobrania. Po zainicjowaniu nowy atrybut po prostu użyć jego właściwości w celu uzyskania wartości.  
  
> [!IMPORTANT]
>  W tym temacie opisano, jak pobrać atrybutów dla kodu ładowane do kontekstu wykonywania. Aby pobrać atrybutów dla kodu ładowane do kontekstu reflection-only, należy użyć <xref:System.Reflection.CustomAttributeData> klasy, jak pokazano w [porady: zestawy obciążenia w kontekście Reflection-Only](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).  
  
 W tej sekcji opisano sposoby można pobrać atrybutów:  
  
-   [Trwa pobieranie jedno wystąpienie atrybutu](#cpconretrievingsingleinstanceofattribute)  
  
-   [Pobieranie wielu wystąpień atrybut zastosowany do tego samego zakresu](#cpconretrievingmultipleinstancesofattributeappliedtosamescope)  
  
-   [Pobieranie wielu wystąpień atrybutem stosowanym do różnych zakresów](#cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes)  
  
<a name="cpconretrievingsingleinstanceofattribute"></a>   
## <a name="retrieving-a-single-instance-of-an-attribute"></a>Trwa pobieranie jedno wystąpienie atrybutu  
 W poniższym przykładzie `DeveloperAttribute` (opisane w poprzedniej sekcji) jest stosowana do `MainApp` klasy na poziomie klasy. `GetAttribute` Używa metody **metody GetCustomAttribute** można pobrać wartości przechowywane w `DeveloperAttribute` na poziomie klasy przed ich wyświetlania w konsoli.  
  
 [!code-cpp[Conceptual.Attributes.Usage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#18)]
 [!code-csharp[Conceptual.Attributes.Usage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#18)]
 [!code-vb[Conceptual.Attributes.Usage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#18)]  
  
 Ten program wyświetla następujący tekst podczas wykonywania.  
  
```  
The Name Attribute is: Joan Smith.  
The Level Attribute is: 42.  
The Reviewed Attribute is: True.  
```  
  
 Jeśli ten atrybut nie zostanie znaleziony, **metody GetCustomAttribute** inicjuje metody `MyAttribute` ma wartość null. W tym przykładzie sprawdza `MyAttribute` dla wystąpienia obiektu i powiadamia użytkownika, jeśli nie jest odnaleźć atrybutu. Jeśli `DeveloperAttribute` nie została odnaleziona w zakresie klasy następujący komunikat wyświetlany w konsoli.  
  
```  
The attribute was not found.   
```  
  
 W przykładzie założono, że definicja atrybutu znajduje się w bieżącej przestrzeni nazw. Pamiętaj, aby zaimportować przestrzeni nazw, w której znajduje się definicja atrybutu, jeśli nie znajduje się w bieżącej przestrzeni nazw.  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtosamescope"></a>   
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-the-same-scope"></a>Pobieranie wielu wystąpień atrybut zastosowany do tego samego zakresu  
 W poprzednim przykładzie klasa do zbadania i określony atrybut można znaleźć są przekazywane do <xref:System.Attribute.GetCustomAttribute%2A>. Ten kod działa także jeśli tylko jedno wystąpienie atrybutu jest stosowana na poziomie klasy. Jednak jeśli wiele wystąpień atrybutu są stosowane na tym samym poziomie klasy **metody GetCustomAttribute** — metoda nie pobiera wszystkie informacje. W przypadkach, gdy wiele wystąpień tego samego atrybutu są stosowane do tego samego zakresu, można użyć <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType> można umieścić wszystkie wystąpienia atrybutu do tablicy. Na przykład, jeśli dwa wystąpienia `DeveloperAttribute` są stosowane na poziomie klasy w tej samej klasy `GetAttribute` metody można zmodyfikować, aby wyświetlić informacje znajdujące się w obu atrybutów. Pamiętaj, aby zastosować wielu atrybutów na tym samym poziomie atrybutu musi być zdefiniowana z **AllowMultiple** ustawioną właściwość **true** w <xref:System.AttributeUsageAttribute>.  
  
 Poniższy przykładowy kod przedstawia sposób użycia **GetCustomAttributes** metodę w celu utworzenia tablicę, która odwołuje się do wszystkich wystąpień `DeveloperAttribute` w dowolnej podanej klasy. Wartości wszystkich atrybutów są następnie wyświetlane w konsoli.  
  
 [!code-cpp[Conceptual.Attributes.Usage#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#19)]
 [!code-csharp[Conceptual.Attributes.Usage#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#19)]
 [!code-vb[Conceptual.Attributes.Usage#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#19)]  
  
 Jeśli nie zostaną znalezione żadne atrybuty, ten kod ostrzega o tym użytkownika. W przeciwnym razie informacje zawarte w obu wystąpień `DeveloperAttribute` jest wyświetlany.  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes"></a>   
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-different-scopes"></a>Pobieranie wielu wystąpień atrybutem stosowanym do różnych zakresów  
 <xref:System.Attribute.GetCustomAttributes%2A> i <xref:System.Attribute.GetCustomAttribute%2A> metody wyszukiwania całej klasy i nie zwraca wszystkie wystąpienia atrybutów w tej klasy. Zamiast wyszukiwania tylko jeden określonej metody lub członka naraz. Jeśli masz klasy z tego samego atrybutu zastosowane do każdego elementu członkowskiego i chcesz pobrać wartości na wszystkie atrybuty, które są stosowane do tych członków, należy podać co metody lub członka indywidualnie do **GetCustomAttributes** i  **Metody GetCustomAttribute**.  
  
 Poniższy przykład kodu klasy jako parametr przyjmuje i wyszukuje `DeveloperAttribute` (zdefiniowanych wcześniej) na poziomie klasy i co poszczególne metody tej klasy.  
  
 [!code-cpp[Conceptual.Attributes.Usage#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#20)]
 [!code-csharp[Conceptual.Attributes.Usage#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#20)]
 [!code-vb[Conceptual.Attributes.Usage#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#20)]  
  
 Jeśli nie wystąpienia `DeveloperAttribute` znajdują się na poziomie metody lub klasa, `GetAttribute` metoda powiadamia użytkownika, którego nie znaleziono żadnych atrybutów i wyświetla nazwę metody lub klasa, która nie zawiera atrybutu. Jeśli atrybut zostanie znaleziony, `Name`, `Level`, i `Reviewed` pola są wyświetlane w konsoli.  
  
 Korzystając z członkami <xref:System.Type> klasy można pobrać poszczególnych metod i elementów członkowskich w klasie przekazany. W tym przykładzie najpierw wysyła zapytanie **typu** obiektu, aby uzyskać informacje o atrybutach dotyczące poziomie klasy. Następnie używa <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> umieścić wystąpień wszystkich metod do tablicy <xref:System.Reflection.MemberInfo?displayProperty=nameWithType> obiektów można pobrać informacji o atrybut na poziomie metody. Można również użyć <xref:System.Type.GetProperties%2A?displayProperty=nameWithType> metodę sprawdzania, czy atrybuty na poziomie właściwości lub <xref:System.Type.GetConstructors%2A?displayProperty=nameWithType> do sprawdzenia atrybuty na poziomie konstruktora.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Type?displayProperty=nameWithType>  
 <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType>  
 <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>  
 [Atrybuty](../../../docs/standard/attributes/index.md)
