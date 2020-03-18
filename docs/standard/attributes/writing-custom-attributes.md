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
ms.openlocfilehash: 6570c6994c0f2e6571361c3eadc73b02a55f1584
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73140584"
---
# <a name="writing-custom-attributes"></a>Wpisywanie atrybutów niestandardowych
Aby zaprojektować własne atrybuty niestandardowe, nie trzeba opanować wiele nowych koncepcji. Jeśli znasz programowanie obiektowe i wiesz, jak projektować klasy, masz już większość potrzebnej wiedzy. Atrybuty niestandardowe są zasadniczo tradycyjnych klas, które <xref:System.Attribute?displayProperty=nameWithType>pochodzą bezpośrednio lub pośrednio z . Podobnie jak tradycyjne klasy, atrybuty niestandardowe zawierają metody, które przechowują i pobierają dane.  
  
 Podstawowe kroki, aby poprawnie zaprojektować niestandardowe klasy atrybutów są następujące:  
  
- [Stosowanie atrybutu AttributeUsageAttribute](#applying-the-attributeusageattribute)  
  
- [Deklarowanie klasy atrybutu](#declaring-the-attribute-class)  
  
- [Deklarowanie konstruktorów](#declaring-constructors)  
  
- [Deklarowanie właściwości](#declaring-properties)  
  
 W tej sekcji opisano każdy z tych kroków i kończy się [przykładem atrybutu niestandardowego](#custom-attribute-example).  
  
## <a name="applying-the-attributeusageattribute"></a>Stosowanie atrybutu AttributeUsageAttribute  
 Deklaracja atrybutu niestandardowego <xref:System.AttributeUsageAttribute?displayProperty=nameWithType>rozpoczyna się od , który definiuje niektóre kluczowe cechy klasy atrybutu. Na przykład można określić, czy atrybut może być dziedziczony przez inne klasy lub określić, do których elementów można zastosować atrybut. Poniższy fragment kodu pokazuje, jak <xref:System.AttributeUsageAttribute>używać pliku .  
  
 [!code-cpp[Conceptual.Attributes.Usage#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#5)]
 [!code-csharp[Conceptual.Attributes.Usage#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#5)]
 [!code-vb[Conceptual.Attributes.Usage#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#5)]  
  
 Ma <xref:System.AttributeUsageAttribute> trzy elementy członkowskie, które są ważne dla tworzenia atrybutów niestandardowych: [AttributeTargets](#attributetargets-member), [Dziedziczone](#inherited-property)i [AllowMultiple](#allowmultiple-property).  
  
### <a name="attributetargets-member"></a>AttributeTargets Członek  
 W poprzednim przykładzie <xref:System.AttributeTargets.All?displayProperty=nameWithType> określono, wskazując, że ten atrybut może być stosowany do wszystkich elementów programu. Alternatywnie można określić <xref:System.AttributeTargets.Class?displayProperty=nameWithType>, wskazując, że atrybut może być stosowany <xref:System.AttributeTargets.Method?displayProperty=nameWithType>tylko do klasy, lub , wskazując, że atrybut może być stosowany tylko do metody. Wszystkie elementy programu mogą być oznaczone do opisu przez atrybut niestandardowy w ten sposób.  
  
 Można również przekazać wiele <xref:System.AttributeTargets> wartości. Poniższy fragment kodu określa, że atrybut niestandardowy można zastosować do dowolnej klasy lub metody.  
  
 [!code-cpp[Conceptual.Attributes.Usage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#6)]
 [!code-csharp[Conceptual.Attributes.Usage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#6)]
 [!code-vb[Conceptual.Attributes.Usage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#6)]  
  
### <a name="inherited-property"></a>Dziedziczona właściwość  
 Właściwość <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> wskazuje, czy atrybut może być dziedziczony przez klasy, które są uzyskiwane z klas, do których atrybut jest stosowany. Ta właściwość przyjmuje `true` (domyślną) `false` lub flagę. W poniższym `MyAttribute` przykładzie ma <xref:System.AttributeUsageAttribute.Inherited%2A> wartość `true`domyślną <xref:System.AttributeUsageAttribute.Inherited%2A> , `false`podczas gdy `YourAttribute` ma wartość .  
  
 [!code-cpp[Conceptual.Attributes.Usage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Attributes.Usage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#7)]
 [!code-vb[Conceptual.Attributes.Usage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#7)]  
  
 Dwa atrybuty są następnie stosowane do metody `MyClass`w klasie podstawowej .  
  
 [!code-cpp[Conceptual.Attributes.Usage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#9)]
 [!code-csharp[Conceptual.Attributes.Usage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#9)]
 [!code-vb[Conceptual.Attributes.Usage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#9)]  
  
 Na koniec `YourClass` klasa jest dziedziczona z klasy `MyClass`podstawowej . Metoda `MyMethod` pokazuje `MyAttribute`, `YourAttribute`ale nie .  
  
 [!code-cpp[Conceptual.Attributes.Usage#10](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#10)]
 [!code-csharp[Conceptual.Attributes.Usage#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#10)]
 [!code-vb[Conceptual.Attributes.Usage#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#10)]  
  
### <a name="allowmultiple-property"></a>Właściwość AllowMultiple  
 Właściwość <xref:System.AttributeUsageAttribute.AllowMultiple%2A?displayProperty=nameWithType> wskazuje, czy wiele wystąpień atrybutu może istnieć na element. Jeśli jest `true`ustawiona na , wiele wystąpień są dozwolone; jeśli ustawiono `false` (domyślnie), dozwolone jest tylko jedno wystąpienie.  
  
 W poniższym `MyAttribute` przykładzie ma <xref:System.AttributeUsageAttribute.AllowMultiple%2A> wartość `false`domyślną , podczas gdy `YourAttribute` ma wartość `true`.  
  
 [!code-cpp[Conceptual.Attributes.Usage#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#11)]
 [!code-csharp[Conceptual.Attributes.Usage#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#11)]
 [!code-vb[Conceptual.Attributes.Usage#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#11)]  
  
 Gdy wiele wystąpień tych atrybutów `MyAttribute` są stosowane, tworzy błąd kompilatora. Poniższy przykład kodu pokazuje prawidłowe `YourAttribute` użycie i nieprawidłowe `MyAttribute`użycie .  
  
 [!code-cpp[Conceptual.Attributes.Usage#13](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#13)]
 [!code-csharp[Conceptual.Attributes.Usage#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#13)]
 [!code-vb[Conceptual.Attributes.Usage#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#13)]  
  
 Jeśli zarówno <xref:System.AttributeUsageAttribute.AllowMultiple%2A> właściwość, <xref:System.AttributeUsageAttribute.Inherited%2A> jak i `true`właściwość są ustawione na , klasa, która jest dziedziczona z innej klasy może dziedziczyć atrybut i mieć inne wystąpienie tego samego atrybutu stosowane w tej samej klasie podrzędnej. Jeśli <xref:System.AttributeUsageAttribute.AllowMultiple%2A> jest `false`ustawiona na , wartości wszystkich atrybutów w klasie nadrzędnej zostaną zastąpione przez nowe wystąpienia tego samego atrybutu w klasie podrzędnej.  
  
## <a name="declaring-the-attribute-class"></a>Deklarowanie klasy atrybutu  
 Po zastosowaniu <xref:System.AttributeUsageAttribute>, można rozpocząć definiowanie specyfiki atrybutu. Deklaracja klasy atrybut wygląda podobnie do deklaracji klasy tradycyjnej, jak pokazano w poniższym kodzie.  
  
 [!code-cpp[Conceptual.Attributes.Usage#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#14)]
 [!code-csharp[Conceptual.Attributes.Usage#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#14)]
 [!code-vb[Conceptual.Attributes.Usage#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#14)]  
  
 Ta definicja atrybutu pokazuje następujące punkty:  
  
- Klasy atrybutów muszą być zadeklarowane jako klasy publiczne.  
  
- Zgodnie z konwencją nazwa klasy atrybutu kończy się słowem **Atrybut**. Chociaż nie jest to wymagane, ta konwencja jest zalecana dla czytelności. Po zastosowaniu atrybutu dołączenie słowa Atrybut jest opcjonalne.  
  
- Wszystkie klasy atrybutów muszą dziedziczyć bezpośrednio lub pośrednio z <xref:System.Attribute?displayProperty=nameWithType>.  
  
- W programie Microsoft Visual Basic wszystkie <xref:System.AttributeUsageAttribute?displayProperty=nameWithType> klasy atrybutów niestandardowych musi mieć atrybut.  
  
## <a name="declaring-constructors"></a>Deklarowanie konstruktorów  
 Atrybuty są inicjowane z konstruktorów w taki sam sposób jak tradycyjne klasy. Poniższy fragment kodu ilustruje typowy konstruktor atrybutów. Ten konstruktor publiczny przyjmuje parametr i ustawia zmienną składową równą jego wartości.  
  
 [!code-cpp[Conceptual.Attributes.Usage#15](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#15)]
 [!code-csharp[Conceptual.Attributes.Usage#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#15)]
 [!code-vb[Conceptual.Attributes.Usage#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#15)]  
  
 Konstruktor można przeciążać, aby pomieścić różne kombinacje wartości. Jeśli zdefiniujesz również [właściwość](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)) dla niestandardowej klasy atrybutów, można użyć kombinacji parametrów nazwanych i pozycyjnych podczas inicjowania atrybutu. Zazwyczaj wszystkie wymagane parametry są definiowane jako pozycyjne i wszystkie parametry opcjonalne jako nazwane. W takim przypadku atrybut nie może zostać zainicjowany bez wymaganego parametru. Wszystkie inne parametry są opcjonalne. Należy zauważyć, że w języku Visual Basic konstruktory dla klasy atrybutów nie należy używać ParamArray argument.  
  
 W poniższym przykładzie kodu pokazano, jak można zastosować atrybut, który używa poprzedniego konstruktora przy użyciu parametrów opcjonalnych i wymaganych. Zakłada się, że atrybut ma jedną wymaganą wartość logiczną i jedną opcjonalną właściwość ciągu.  
  
 [!code-cpp[Conceptual.Attributes.Usage#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#17)]
 [!code-csharp[Conceptual.Attributes.Usage#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#17)]
 [!code-vb[Conceptual.Attributes.Usage#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#17)]  
  
## <a name="declaring-properties"></a>Deklarowanie właściwości  
 Jeśli chcesz zdefiniować nazwany parametr lub zapewnić łatwy sposób zwracania wartości przechowywanych przez atrybut, należy zadeklarować [właściwość](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)). Właściwości atrybutu powinny być zadeklarowane jako jednostki publiczne z opisem typu danych, który zostanie zwrócony. Zdefiniuj zmienną, która będzie przechowywać wartość właściwości i skojarzyć ją z **metodami get** i **set.** W poniższym przykładzie kodu przedstawiono sposób implementowania właściwości simple w atrybucie.  
  
 [!code-cpp[Conceptual.Attributes.Usage#16](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#16)]
 [!code-csharp[Conceptual.Attributes.Usage#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#16)]
 [!code-vb[Conceptual.Attributes.Usage#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#16)]  
  
## <a name="custom-attribute-example"></a>Przykład atrybutu niestandardowego  
 W tej sekcji znajdują się poprzednie informacje i pokazano, jak zaprojektować prosty atrybut, który dokumentuje informacje o autorze sekcji kodu. Atrybut w tym przykładzie przechowuje nazwę i poziom programisty oraz to, czy kod został przejrzany. Używa trzech zmiennych prywatnych do przechowywania rzeczywistych wartości do zapisania. Każda zmienna jest reprezentowana przez właściwość publiczną, która pobiera i ustawia wartości. Na koniec konstruktor jest zdefiniowany z dwoma wymaganymi parametrami.  
  
 [!code-cpp[Conceptual.Attributes.Usage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#4)]
 [!code-csharp[Conceptual.Attributes.Usage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#4)]
 [!code-vb[Conceptual.Attributes.Usage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#4)]  
  
 Ten atrybut można zastosować przy `DeveloperAttribute`użyciu pełnej nazwy lub przy `Developer`użyciu skróconej nazwy, w jeden z następujących sposobów.  
  
 [!code-cpp[Conceptual.Attributes.Usage#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#12)]
 [!code-csharp[Conceptual.Attributes.Usage#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#12)]
 [!code-vb[Conceptual.Attributes.Usage#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#12)]  
  
 Pierwszy przykład pokazuje atrybut zastosowany tylko z wymaganymi nazwanymi parametrami, podczas gdy drugi przykład pokazuje atrybut zastosowany z parametrami wymaganymi i opcjonalnymi.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Attribute?displayProperty=nameWithType>
- <xref:System.AttributeUsageAttribute?displayProperty=nameWithType>
- [Atrybuty](../../../docs/standard/attributes/index.md)
