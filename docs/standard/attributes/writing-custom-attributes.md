---
title: Wpisywanie atrybutów niestandardowych
ms.date: 07/17/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- multiple attribute instances
- AttributeTargets enumeration
- attributes [.NET Framework], custom
- AllowMultiple property
- custom attributes
- AttributeUsageAttribute class, custom attributes
- Inherited property
- attribute classes, declaring
ms.assetid: 97216f69-bde8-49fd-ac40-f18c500ef5dc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 67a5ffe2075618020f3ab9f801852a1a97fc74d2
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44087394"
---
# <a name="writing-custom-attributes"></a>Wpisywanie atrybutów niestandardowych
Aby zaprojektować atrybutów niestandardowych, nie trzeba opanować wiele nowych pojęć. Jeśli znasz programowanie zorientowane obiektowo i wiedzieć, jak klasy należy projektować, masz już większość wiedzę potrzebną. Atrybuty niestandardowe są zasadniczo tradycyjnych klas, które pochodzą bezpośrednio lub pośrednio z <xref:System.Attribute?displayProperty=nameWithType>. Podobnie jak tradycyjnych klasy atrybutów niestandardowych, które zawierają metody, które przechowywać i pobierać dane.  
  
 Podstawowe kroki, aby prawidłowo projektowania klas atrybutów niestandardowych, są następujące:  
  
- [Stosowanie AttributeUsageAttribute](#applying-the-attributeusageattribute)  
  
- [Deklarowanie klasy atrybutów](#declaring-the-attribute-class)  
  
- [Deklarowanie konstruktorów](#declaring-constructors)  
  
- [Deklarowanie właściwości](#declaring-properties)  
  
 W tej sekcji opisano każdy z tych kroków i nie zawiera z [przykład atrybutu niestandardowego](#custom-attribute-example).  
  
## <a name="applying-the-attributeusageattribute"></a>Stosowanie AttributeUsageAttribute  
 Deklaracji atrybutu niestandardowego, który rozpoczyna się od <xref:System.AttributeUsageAttribute?displayProperty=nameWithType>, definiujący niektóre z kluczowych charakterystyk klasy atrybutu. Na przykład można określić, czy atrybut może być dziedziczona przez inne klasy lub Określ elementy, które można zastosować atrybut do. Poniższy fragment kodu pokazuje sposób użycia <xref:System.AttributeUsageAttribute>.  
  
 [!code-cpp[Conceptual.Attributes.Usage#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#5)]
 [!code-csharp[Conceptual.Attributes.Usage#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#5)]
 [!code-vb[Conceptual.Attributes.Usage#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#5)]  
  
 <xref:System.AttributeUsageAttribute> Ma trzy elementy członkowskie, które są ważne w przypadku tworzenia niestandardowych atrybutów: [attributetargets —](#attributetargets-member), [dziedziczone](#inherited-property), i [AllowMultiple](#allowmultiple-property).  
  
### <a name="attributetargets-member"></a>Attributetargets — element członkowski  
 W poprzednim przykładzie <xref:System.AttributeTargets.All?displayProperty=nameWithType> jest określony, wskazujący, że ten atrybut można stosować do wszystkich elementów programu. Alternatywnie, można określić <xref:System.AttributeTargets.Class?displayProperty=nameWithType>, wskazujący, że Twoje atrybut można stosować tylko do klasy, lub <xref:System.AttributeTargets.Method?displayProperty=nameWithType>, wskazujący, że Twoje atrybut można stosować tylko do metody. Wszystkie elementy program może być oznaczony jako opis przez atrybut niestandardowy w ten sposób.  
  
 Można również przekazać wiele <xref:System.AttributeTargets> wartości. Poniższy fragment kodu Określa, czy niestandardowy atrybut można stosować do dowolnej klasy lub metody.  
  
 [!code-cpp[Conceptual.Attributes.Usage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#6)]
 [!code-csharp[Conceptual.Attributes.Usage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#6)]
 [!code-vb[Conceptual.Attributes.Usage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#6)]  
  
### <a name="inherited-property"></a>Właściwość dziedziczona  
 <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> Właściwość wskazuje, czy atrybut może być dziedziczona przez klasy, które są pochodnymi klasy, do których zastosowano atrybut. Ta właściwość ma albo `true` (ustawienie domyślne) lub `false` flagi. W poniższym przykładzie `MyAttribute` ma wartość domyślną <xref:System.AttributeUsageAttribute.Inherited%2A> wartość `true`, podczas gdy `YourAttribute` ma <xref:System.AttributeUsageAttribute.Inherited%2A> wartość `false`.  
  
 [!code-cpp[Conceptual.Attributes.Usage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Attributes.Usage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#7)]
 [!code-vb[Conceptual.Attributes.Usage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#7)]  
  
 Dwa atrybuty są następnie stosowane do metody w klasie bazowej `MyClass`.  
  
 [!code-cpp[Conceptual.Attributes.Usage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#9)]
 [!code-csharp[Conceptual.Attributes.Usage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#9)]
 [!code-vb[Conceptual.Attributes.Usage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#9)]  
  
 Na koniec klasę `YourClass` jest dziedziczona z klasy bazowej `MyClass`. Metoda `MyMethod` pokazuje `MyAttribute`, ale nie `YourAttribute`.  
  
 [!code-cpp[Conceptual.Attributes.Usage#10](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#10)]
 [!code-csharp[Conceptual.Attributes.Usage#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#10)]
 [!code-vb[Conceptual.Attributes.Usage#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#10)]  
  
### <a name="allowmultiple-property"></a>AllowMultiple właściwość  
 <xref:System.AttributeUsageAttribute.AllowMultiple%2A?displayProperty=nameWithType> Właściwość wskazuje, czy na element może istnieć wiele wystąpień usługi atrybutu. Jeśli ustawiono `true`, wielu wystąpień są dozwolone; Jeśli równa `false` (ustawienie domyślne), jest dozwolone tylko jedno wystąpienie.  
  
 W poniższym przykładzie `MyAttribute` ma wartość domyślną <xref:System.AttributeUsageAttribute.AllowMultiple%2A> wartość `false`, podczas gdy `YourAttribute` ma wartość `true`.  
  
 [!code-cpp[Conceptual.Attributes.Usage#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#11)]
 [!code-csharp[Conceptual.Attributes.Usage#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#11)]
 [!code-vb[Conceptual.Attributes.Usage#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#11)]  
  
 Po zastosowaniu wielu wystąpień tych atrybutów, `MyAttribute` powoduje błąd kompilatora. Poniższy przykład kodu pokazuje prawidłowe użycie `YourAttribute` i nieprawidłowe użycie `MyAttribute`.  
  
 [!code-cpp[Conceptual.Attributes.Usage#13](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#13)]
 [!code-csharp[Conceptual.Attributes.Usage#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#13)]
 [!code-vb[Conceptual.Attributes.Usage#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#13)]  
  
 Jeśli oba <xref:System.AttributeUsageAttribute.AllowMultiple%2A> właściwości i <xref:System.AttributeUsageAttribute.Inherited%2A> ustawioną na `true`, klasę, która jest dziedziczony z innej klasy mogą dziedziczyć atrybutu i inne wystąpienie tego samego atrybutu stosowane w tej samej klasy podrzędnej. Jeśli <xref:System.AttributeUsageAttribute.AllowMultiple%2A> ustawiono `false`, wartości atrybutów w klasie nadrzędnej, zostaną zastąpione przez nowe wystąpienia tego samego atrybutu klasy podrzędnej.  
  
## <a name="declaring-the-attribute-class"></a>Deklarowanie klasy atrybutów  
 Po zastosowaniu <xref:System.AttributeUsageAttribute>, możesz rozpocząć definiowanie szczegółowych informacji z atrybutu. Deklaracja klasy atrybutu wygląda podobnie do deklaracji klasy tradycyjnych, jak pokazano w następującym kodem.  
  
 [!code-cpp[Conceptual.Attributes.Usage#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#14)]
 [!code-csharp[Conceptual.Attributes.Usage#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#14)]
 [!code-vb[Conceptual.Attributes.Usage#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#14)]  
  
 Ta definicja atrybutu pokazuje następujące kwestie:  
  
- Klasy atrybutów musi być zadeklarowany jako publiczne klasy.  
  
- Zgodnie z Konwencją Nazwa klasy atrybutu kończy się wyrazem **atrybutu**. Chociaż nie jest to wymagane, ta Konwencja jest zalecana dla czytelności. Jeśli ten atrybut jest stosowany, włączenie word atrybut jest opcjonalny.  
  
- Wszystkie klasy atrybutu musi dziedziczyć pośrednio lub bezpośrednio <xref:System.Attribute?displayProperty=nameWithType>.  
  
- Microsoft Visual Basic, wszystkie klasy atrybutu niestandardowego musi mieć <xref:System.AttributeUsageAttribute?displayProperty=nameWithType> atrybutu.  
  
## <a name="declaring-constructors"></a>Deklarowanie konstruktorów  
 Atrybuty są inicjowane z konstruktorów w taki sam sposób jak tradycyjnych klasy. Poniższy fragment kodu przedstawia typowe atrybut konstruktora. Ten publiczny konstruktor przyjmuje parametr i ustawia zmienną członkowską równa jego wartości.  
  
 [!code-cpp[Conceptual.Attributes.Usage#15](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#15)]
 [!code-csharp[Conceptual.Attributes.Usage#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#15)]
 [!code-vb[Conceptual.Attributes.Usage#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#15)]  
  
 Możesz doprowadzić do przeciążenia konstruktora, aby obsłużyć różne kombinacje wartości. Jeśli należy także zdefiniować [właściwość](https://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52) dla swojej klasy atrybutów niestandardowych, można użyć kombinacji parametrów nazwanych i pozycyjnych podczas inicjowania atrybutu. Zazwyczaj można zdefiniować wszystkie wymagane parametry jako parametry pozycyjne i wszystkie opcjonalne jako o nazwie. W tym przypadku atrybut nie można zainicjować bez wymaganego parametru. Wszystkie inne parametry są opcjonalne. Należy pamiętać, że w języku Visual Basic konstruktory klasy atrybutów nie należy używać argumentu ParamArray.  
  
 W poniższym przykładzie kodu przedstawiono sposób atrybut, który korzysta z poprzednich Konstruktor może odnosić się przy użyciu parametrów opcjonalnych i wymaganych. Przyjęto założenie, że ten atrybut ma jedną wartość logiczną wymagane i właściwość jeden opcjonalny ciąg.  
  
 [!code-cpp[Conceptual.Attributes.Usage#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#17)]
 [!code-csharp[Conceptual.Attributes.Usage#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#17)]
 [!code-vb[Conceptual.Attributes.Usage#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#17)]  
  
## <a name="declaring-properties"></a>Deklarowanie właściwości  
 Jeśli chcesz zdefiniować nazwany parametr lub prosty sposób zwracania wartości przechowywane przez atrybut, Zadeklaruj [właściwość](https://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52). Właściwości atrybutów powinien być zadeklarowany jako publiczny jednostki opis typu danych, który zostanie zwrócony. Zdefiniuj zmienną, która będzie przechowywać wartości właściwości i powiąż ją z **uzyskać** i **ustaw** metody. Poniższy przykład kodu demonstruje sposób implementacji właściwości prostej usługi atrybutu.  
  
 [!code-cpp[Conceptual.Attributes.Usage#16](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#16)]
 [!code-csharp[Conceptual.Attributes.Usage#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#16)]
 [!code-vb[Conceptual.Attributes.Usage#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#16)]  
  
## <a name="custom-attribute-example"></a>Przykład atrybutu niestandardowego  
 Ta sekcja zawiera wcześniejszych informacji i pokazuje, jak projektować proste atrybut, który dokumenty, informacje o autorze sekcji kodu. Ten atrybut, w tym przykładzie przechowuje nazwę i poziom programisty, i czy zostało poddane przeglądowi kodu. Używa trzech zmiennych prywatnych do przechowywania wartości faktycznych można zapisać. Każda zmienna jest reprezentowany przez właściwość publiczną, która pobiera i ustawia wartości. Na koniec Konstruktor jest zdefiniowana za pomocą dwóch wymaganych parametrów.  
  
 [!code-cpp[Conceptual.Attributes.Usage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#4)]
 [!code-csharp[Conceptual.Attributes.Usage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#4)]
 [!code-vb[Conceptual.Attributes.Usage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#4)]  
  
 Można zastosować ten atrybut przy użyciu pełnej nazwy `DeveloperAttribute`, lub za pomocą nazwy skróconej, `Developer`, w jednym z następujących sposobów.  
  
 [!code-cpp[Conceptual.Attributes.Usage#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#12)]
 [!code-csharp[Conceptual.Attributes.Usage#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#12)]
 [!code-vb[Conceptual.Attributes.Usage#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#12)]  
  
 Pierwszy przykład pokazuje zastosowany tylko wymagane nazwanych parametrów, podczas gdy drugi przykład przedstawia zastosowany przy użyciu wymaganych i opcjonalnych parametrów.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Attribute?displayProperty=nameWithType>  
- <xref:System.AttributeUsageAttribute?displayProperty=nameWithType>  
- [Atrybuty](../../../docs/standard/attributes/index.md)
