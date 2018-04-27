---
title: Wpisywanie atrybutów niestandardowych
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 14
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b38aa643453d9ad853d0d17af0f1ddf2ba69d4a1
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="writing-custom-attributes"></a>Wpisywanie atrybutów niestandardowych
Projektowanie własnych niestandardowych atrybutów, nie trzeba wzorca wiele nowych pojęć. Jeśli znasz programowanie zorientowane obiektowo i dowiedzieć się, jak zaprojektować klasy, masz już większość wiedzy potrzebne. Atrybuty niestandardowe są zasadniczo tradycyjnych klas pochodzących od bezpośrednio lub pośrednio <xref:System.Attribute?displayProperty=nameWithType>. Podobnie jak tradycyjnych klasy atrybutów niestandardowych, które zawierają metod, które przechowują i pobierają dane.  
  
 Podstawowe kroki, aby poprawnie projektowania klas niestandardowych atrybutów są następujące:  
  
-   [Stosowanie AttributeUsageAttribute](#cpconapplyingattributeusageattribute)  
  
-   [Deklarowanie klasy atrybutów](#cpcondeclaringattributeclass)  
  
-   [Deklarowanie konstruktorów](#cpcondeclaringconstructors)  
  
-   [Deklarowanie właściwości](#cpcondeclaringproperties)  
  
 Ta sekcja zawiera opis każdego z tych kroków i nie zawiera z [przykład atrybutu niestandardowego](#cpconcustomattributeexample).  
  
<a name="cpconapplyingattributeusageattribute"></a>   
## <a name="applying-the-attributeusageattribute"></a>Stosowanie AttributeUsageAttribute  
 Rozpoczyna się od deklaracji atrybutu niestandardowego **AttributeUsageAttribute**, który definiuje niektóre właściwości klucza klasy atrybutu. Na przykład można określić, czy atrybut może być dziedziczone przez inne klasy lub Określ elementy, które można zastosować atrybut do. Poniższy fragment kodu przedstawiają sposób użycia **AttributeUsageAttribute**.  
  
 [!code-cpp[Conceptual.Attributes.Usage#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#5)]
 [!code-csharp[Conceptual.Attributes.Usage#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#5)]
 [!code-vb[Conceptual.Attributes.Usage#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#5)]  
  
 <xref:System.AttributeUsageAttribute?displayProperty=nameWithType> Ma trzy elementy członkowskie, które są ważne w przypadku tworzenia niestandardowych atrybutów: [attributetargets —](#cpconwritingcustomattributesanchor1), [dziedziczonych](#cpconwritingcustomattributesanchor2), i [AllowMultiple](#cpconwritingcustomattributesanchor3).  
  
<a name="cpconwritingcustomattributesanchor1"></a>   
### <a name="attributetargets-member"></a>Attributetargets — element członkowski  
 W poprzednim przykładzie **AttributeTargets.All** jest określony, wskazując, że ten atrybut można stosować do wszystkich elementów programu. Alternatywnie można określić **AttributeTargets.Class**, wskazującą, czy atrybut może odnosić się tylko do klasy, lub **AttributeTargets.Method**, wskazujący, że atrybut może być stosowana tylko do metody. Wszystkie elementy programu może być oznaczony opis przez atrybut niestandardowy w ten sposób.  
  
 Można również przekazać wiele wystąpień <xref:System.AttributeTargets>. Poniższy fragment kodu Określa, że atrybut niestandardowy może odnosić się do klasy lub metody.  
  
 [!code-cpp[Conceptual.Attributes.Usage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#6)]
 [!code-csharp[Conceptual.Attributes.Usage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#6)]
 [!code-vb[Conceptual.Attributes.Usage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#6)]  
  
<a name="cpconwritingcustomattributesanchor2"></a>   
### <a name="inherited-property"></a>Właściwość dziedziczona  
 <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> Właściwość wskazuje, czy atrybut może być dziedziczone przez klasy, które są pochodnymi klasy, do których zastosowano atrybut. Ta właściwość ma albo **true** (ustawienie domyślne) lub **false** flagi. Na przykład w poniższym przykładzie `MyAttribute` ma wartość domyślną <xref:System.AttributeUsageAttribute.Inherited%2A> wartość **true**, podczas gdy `YourAttribute` ma <xref:System.AttributeUsageAttribute.Inherited%2A> wartość **false**.  
  
 [!code-cpp[Conceptual.Attributes.Usage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Attributes.Usage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#7)]
 [!code-vb[Conceptual.Attributes.Usage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#7)]  
  
 Dwa atrybuty zostaną zastosowane do metody w klasie podstawowej `MyClass`.  
  
 [!code-cpp[Conceptual.Attributes.Usage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#9)]
 [!code-csharp[Conceptual.Attributes.Usage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#9)]
 [!code-vb[Conceptual.Attributes.Usage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#9)]  
  
 Ponadto klasa `YourClass` jest dziedziczona z klasy podstawowej `MyClass`. Metoda `MyMethod` pokazuje `MyAttribute`, ale nie `YourAttribute`.  
  
 [!code-cpp[Conceptual.Attributes.Usage#10](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#10)]
 [!code-csharp[Conceptual.Attributes.Usage#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#10)]
 [!code-vb[Conceptual.Attributes.Usage#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#10)]  
  
<a name="cpconwritingcustomattributesanchor3"></a>   
### <a name="allowmultiple-property"></a>AllowMultiple właściwość  
 <xref:System.AttributeUsageAttribute.AllowMultiple%2A?displayProperty=nameWithType> Właściwość wskazuje, czy w elemencie może istnieć wiele wystąpień atrybut. Jeśli ustawiono **true**, wiele wystąpień są dozwolone; Jeśli ustawioną **false** (ustawienie domyślne), jest dozwolone tylko jedno wystąpienie.  
  
 W poniższym przykładzie `MyAttribute` ma wartość domyślną <xref:System.AttributeUsageAttribute.AllowMultiple%2A> wartość **false**, podczas gdy `YourAttribute` ma wartość **true**.  
  
 [!code-cpp[Conceptual.Attributes.Usage#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#11)]
 [!code-csharp[Conceptual.Attributes.Usage#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#11)]
 [!code-vb[Conceptual.Attributes.Usage#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#11)]  
  
 Gdy zastosowano wiele wystąpień tych atrybutów, `MyAttribute` powoduje błąd kompilatora. W poniższym przykładzie pokazano sposób użycia prawidłową `YourAttribute` i nieprawidłowe użycie `MyAttribute`.  
  
 [!code-cpp[Conceptual.Attributes.Usage#13](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#13)]
 [!code-csharp[Conceptual.Attributes.Usage#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#13)]
 [!code-vb[Conceptual.Attributes.Usage#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#13)]  
  
 Jeśli oba <xref:System.AttributeUsageAttribute.AllowMultiple%2A> właściwości i <xref:System.AttributeUsageAttribute.Inherited%2A> ustawiono właściwość **true**, klasy, które są dziedziczone z innej klasy mogą dziedziczyć atrybutu i inne wystąpienie tego samego atrybutu stosowane w tej samej klasy podrzędnej. Jeśli <xref:System.AttributeUsageAttribute.AllowMultiple%2A> ustawiono **false**, wartości żadnych atrybutów w klasie nadrzędnej, zostaną zastąpione przez nowe wystąpienia tego samego atrybutu klasy podrzędnej.  
  
<a name="cpcondeclaringattributeclass"></a>   
## <a name="declaring-the-attribute-class"></a>Deklarowanie klasy atrybutów  
 Po zastosowaniu <xref:System.AttributeUsageAttribute>, możesz rozpocząć do definiowania specyfice atrybut. Deklaracja klasy atrybutu wygląda podobnie do deklaracji klasy tradycyjnych, jak pokazano w następującym kodem.  
  
 [!code-cpp[Conceptual.Attributes.Usage#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#14)]
 [!code-csharp[Conceptual.Attributes.Usage#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#14)]
 [!code-vb[Conceptual.Attributes.Usage#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#14)]  
  
 Ta definicja atrybutu przedstawiono następujące kwestie:  
  
-   Atrybut klasy musi być zadeklarowany jako publiczny klasy.  
  
-   Konwencja, nazwa klasy atrybutu kończy się wyrazem **atrybutu**. Podczas gdy nie jest to wymagane, tę Konwencję jest zalecane dla czytelności. Gdy jest stosowany atrybut włączenia programu word atrybutu jest opcjonalny.  
  
-   Wszystkie klasy atrybutu musi dziedziczyć pośrednio lub bezpośrednio z **System.Attribute**.  
  
-   Microsoft Visual Basic, wszystkie klasy atrybutu niestandardowego musi mieć **AttributeUsageAttribute** atrybutu.  
  
<a name="cpcondeclaringconstructors"></a>   
## <a name="declaring-constructors"></a>Deklarowanie konstruktorów  
 Atrybuty są inicjowane z konstruktorów w taki sam sposób jak tradycyjnych klasy. Poniższy fragment kodu przedstawiono typowe atrybut konstruktora. Ten konstruktor publiczny przyjmuje parametr i ustawia wartość równą zmiennej elementu członkowskiego.  
  
 [!code-cpp[Conceptual.Attributes.Usage#15](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#15)]
 [!code-csharp[Conceptual.Attributes.Usage#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#15)]
 [!code-vb[Conceptual.Attributes.Usage#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#15)]  
  
 Można przeciążać konstruktora, aby zmieścił się w różnych kombinacji wartości. Jeśli również definiować [właściwości](https://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52) dla klasy atrybutów niestandardowych, można użyć kombinacji parametrów nazwanych i pozycyjnych podczas inicjowania atrybutu. Zazwyczaj określa się wszystkie wymagane parametry jako parametry pozycyjne i wszystkie opcjonalne jako o nazwie. W takim przypadku atrybutu nie można zainicjować bez wymaganego parametru. Wszystkie inne parametry są opcjonalne. Należy pamiętać, że w języku Visual Basic konstruktory klasę atrybutów nie powinien używać ParamArray argument.  
  
 Poniższy przykładowy kod przedstawia jak atrybut, który używa poprzedniej Konstruktor może odnosić się przy użyciu parametrów opcjonalne i wymagane. Przyjęto założenie, że ten atrybut ma jedną wartość logiczną wymagane, a właściwość jeden opcjonalny ciąg.  
  
 [!code-cpp[Conceptual.Attributes.Usage#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#17)]
 [!code-csharp[Conceptual.Attributes.Usage#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#17)]
 [!code-vb[Conceptual.Attributes.Usage#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#17)]  
  
<a name="cpcondeclaringproperties"></a>   
## <a name="declaring-properties"></a>Deklarowanie właściwości  
 Jeśli chcesz zdefiniować nazwany parametr lub umożliwiają łatwe do zwrócenia wartości przechowywanych przez atrybut, Zadeklaruj [właściwości](https://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52). Właściwości atrybutów powinien być zadeklarowany jako publiczny jednostki z opisu typu danych, które zostaną zwrócone. Definiowanie zmiennej, która będzie przechowywać wartości z właściwości i skojarz ją z **uzyskać** i **ustawić** metody. Poniższy przykład kodu pokazuje, jak do zaimplementowania właściwości prostej w atrybut.  
  
 [!code-cpp[Conceptual.Attributes.Usage#16](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#16)]
 [!code-csharp[Conceptual.Attributes.Usage#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#16)]
 [!code-vb[Conceptual.Attributes.Usage#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#16)]  
  
<a name="cpconcustomattributeexample"></a>   
## <a name="custom-attribute-example"></a>Przykład atrybutu niestandardowego  
 Ta sekcja zawiera informacje o poprzednich i pokazano, jak zaprojektować proste atrybut, który dokumentów informacje o autorze sekcji kodu. Ten atrybut w tym przykładzie są przechowywane nazwy i poziom programisty, i określa, czy kod zostały sprawdzone. Używa trzech zmiennych prywatnych do przechowywania rzeczywiste wartości do zapisania. Pobiera i ustawia wartości właściwości publicznej odpowiada każdej zmiennej. Na koniec Konstruktor jest zdefiniowana z dwóch wymaganych parametrów.  
  
 [!code-cpp[Conceptual.Attributes.Usage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#4)]
 [!code-csharp[Conceptual.Attributes.Usage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#4)]
 [!code-vb[Conceptual.Attributes.Usage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#4)]  
  
 Można użyć tego atrybutu użycie pełnej nazwy `DeveloperAttribute`, lub za pomocą nazwy skróconej `Developer`, w jednym z następujących sposobów.  
  
 [!code-cpp[Conceptual.Attributes.Usage#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#12)]
 [!code-csharp[Conceptual.Attributes.Usage#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#12)]
 [!code-vb[Conceptual.Attributes.Usage#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#12)]  
  
 W pierwszym przykładzie atrybut zastosowany z tylko wymaganymi nazwanych parametrów, a w drugim przykładzie pokazano, atrybut zastosowany o wymaganych i opcjonalnych parametrów.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Attribute?displayProperty=nameWithType>  
 <xref:System.AttributeUsageAttribute>  
 [Atrybuty](../../../docs/standard/attributes/index.md)
