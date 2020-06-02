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
ms.openlocfilehash: fc8dcb38471d80d01d1f87993783af3d24868506
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84276138"
---
# <a name="retrieving-information-stored-in-attributes"></a>Pobieranie informacji przechowywanych w atrybutach
Pobieranie atrybutu niestandardowego jest procesem prostym. Najpierw Zadeklaruj wystąpienie atrybutu, który ma zostać pobrany. Następnie użyj metody, <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType> Aby zainicjować nowy atrybut do wartości atrybutu, który ma zostać pobrany. Po zainicjowaniu nowego atrybutu wystarczy użyć jego właściwości w celu uzyskania wartości.  
  
> [!IMPORTANT]
> W tym temacie opisano sposób pobierania atrybutów dla kodu załadowanego do kontekstu wykonywania. Aby pobrać atrybuty dla kodu załadowanego do kontekstu tylko odbicie, należy użyć <xref:System.Reflection.CustomAttributeData> klasy, jak pokazano w [instrukcje: ładowanie zestawów do kontekstu tylko odbicie](../../framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).  
  
 W tej sekcji opisano następujące metody pobierania atrybutów:  
  
- [Pobieranie pojedynczego wystąpienia atrybutu](#cpconretrievingsingleinstanceofattribute)  
  
- [Pobieranie wielu wystąpień atrybutu zastosowanych do tego samego zakresu](#cpconretrievingmultipleinstancesofattributeappliedtosamescope)  
  
- [Pobieranie wielu wystąpień atrybutu zastosowanych do różnych zakresów](#cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes)  
  
<a name="cpconretrievingsingleinstanceofattribute"></a>
## <a name="retrieving-a-single-instance-of-an-attribute"></a>Pobieranie pojedynczego wystąpienia atrybutu  
 W poniższym przykładzie `DeveloperAttribute` (opisany w poprzedniej sekcji) jest stosowany do `MainApp` klasy na poziomie klasy. `GetAttribute`Metoda używa metody **GetCustomAttribute** do pobierania wartości przechowywanych `DeveloperAttribute` na poziomie klasy przed wyświetleniem ich w konsoli programu.  
  
 [!code-cpp[Conceptual.Attributes.Usage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#18)]
 [!code-csharp[Conceptual.Attributes.Usage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#18)]
 [!code-vb[Conceptual.Attributes.Usage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#18)]  
  
 Ten program wyświetla następujący tekst po wykonaniu.  
  
```console  
The Name Attribute is: Joan Smith.  
The Level Attribute is: 42.  
The Reviewed Attribute is: True.  
```  
  
 Jeśli atrybut nie zostanie znaleziony, Metoda **GetCustomAttribute** inicjuje `MyAttribute` wartość null. Ten przykład sprawdza `MyAttribute` dla takiego wystąpienia i powiadamia użytkownika, jeśli nie zostanie znaleziony żaden atrybut. Jeśli `DeveloperAttribute` nie zostanie znaleziony w zakresie klasy, w konsoli zostanie wyświetlony następujący komunikat.  
  
```console  
The attribute was not found.
```  
  
 W tym przykładzie przyjęto założenie, że definicja atrybutu znajduje się w bieżącej przestrzeni nazw. Pamiętaj, aby zaimportować przestrzeń nazw, w której znajduje się Definicja atrybutu, jeśli nie znajduje się w bieżącej przestrzeni nazw.  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtosamescope"></a>
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-the-same-scope"></a>Pobieranie wielu wystąpień atrybutu zastosowanych do tego samego zakresu  
 W poprzednim przykładzie Klasa do sprawdzenia i określony atrybut do znalezienia są przenoszone do <xref:System.Attribute.GetCustomAttribute%2A> . Ten kod działa prawidłowo, gdy tylko jedno wystąpienie atrybutu jest stosowane na poziomie klasy. Jeśli jednak na tym samym poziomie klasy zastosowano wiele wystąpień atrybutu, Metoda **GetCustomAttribute** nie pobiera wszystkich informacji. W przypadkach, gdy wiele wystąpień tego samego atrybutu jest stosowanych do tego samego zakresu, można użyć, <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType> Aby umieścić wszystkie wystąpienia atrybutu w tablicy. Na przykład jeśli dwa wystąpienia `DeveloperAttribute` są stosowane na poziomie klasy tej samej klasy, `GetAttribute` można zmodyfikować metodę w celu wyświetlenia informacji znalezionych w obu atrybutach. Pamiętaj, aby zastosować wiele atrybutów na tym samym poziomie, atrybut musi być zdefiniowany za pomocą właściwości **AllowMultiple** ustawionej na **wartość true** w elemencie <xref:System.AttributeUsageAttribute> .  
  
 Poniższy przykład kodu pokazuje, jak za pomocą metody **GetCustomAttributes —** utworzyć tablicę, która odwołuje się do wszystkich wystąpień `DeveloperAttribute` w danej klasie. Wartości wszystkich atrybutów są następnie wyświetlane w konsoli programu.  
  
 [!code-cpp[Conceptual.Attributes.Usage#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#19)]
 [!code-csharp[Conceptual.Attributes.Usage#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#19)]
 [!code-vb[Conceptual.Attributes.Usage#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#19)]  
  
 Jeśli nie zostaną znalezione żadne atrybuty, ten kod zgłosi użytkownika. W przeciwnym razie wyświetlane są informacje zawarte w obu wystąpieniach elementu `DeveloperAttribute` .  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes"></a>
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-different-scopes"></a>Pobieranie wielu wystąpień atrybutu zastosowanych do różnych zakresów  
 <xref:System.Attribute.GetCustomAttributes%2A>Metody i <xref:System.Attribute.GetCustomAttribute%2A> nie przeszukują całej klasy i zwracają wszystkie wystąpienia atrybutu w tej klasie. Zamiast tego przeszukują tylko jedną określoną metodę lub element członkowski jednocześnie. Jeśli masz klasę z tym samym atrybutem, który jest stosowany do każdego elementu członkowskiego i chcesz pobrać wartości we wszystkich atrybutach zastosowanych do tych elementów członkowskich, musisz dostarczyć każdą metodę lub element członkowski oddzielnie do **GetCustomAttributes —** i **GetCustomAttribute**.  
  
 Poniższy przykład kodu przyjmuje klasę jako parametr i wyszukuje `DeveloperAttribute` (zdefiniowane wcześniej) na poziomie klasy i dla każdej indywidualnej metody tej klasy.  
  
 [!code-cpp[Conceptual.Attributes.Usage#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#20)]
 [!code-csharp[Conceptual.Attributes.Usage#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#20)]
 [!code-vb[Conceptual.Attributes.Usage#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#20)]  
  
 Jeśli żadne wystąpienia programu nie `DeveloperAttribute` zostaną znalezione na poziomie metody lub poziomie klasy, `GetAttribute` Metoda powiadamia użytkownika, że nie znaleziono żadnych atrybutów i wyświetla nazwę metody lub klasy, która nie zawiera atrybutu. Jeśli zostanie znaleziony atrybut, `Name` `Level` pola, i `Reviewed` są wyświetlane w konsoli programu.  
  
 Można użyć elementów członkowskich <xref:System.Type> klasy, aby uzyskać poszczególne metody i składowe w pomyślnej klasie. Ten przykład najpierw wysyła zapytanie do obiektu **typu** w celu pobrania informacji o atrybucie dla poziomu klasy. Następnie używa <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> do umieszczania wystąpień wszystkich metod w tablicy <xref:System.Reflection.MemberInfo?displayProperty=nameWithType> obiektów w celu pobrania informacji o atrybucie dla poziomu metody. Można również użyć metody, <xref:System.Type.GetProperties%2A?displayProperty=nameWithType> Aby sprawdzić atrybuty na poziomie właściwości lub <xref:System.Type.GetConstructors%2A?displayProperty=nameWithType> sprawdzić atrybuty na poziomie konstruktora.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>
- [Atrybuty](index.md)
