---
title: Wnioskowanie schematów na podstawie dokumentów XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: f3d97d53-614d-4a04-a174-87965b7405f6
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9a27696b6511103e98d37fb72b33f801d23ad391
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "44042182"
---
# <a name="inferring-schemas-from-xml-documents"></a>Wnioskowanie schematów na podstawie dokumentów XML
W tym temacie opisano sposób użycia <xref:System.Xml.Schema.XmlSchemaInference> klasy zostać wywnioskowany schemat języka (XSD) definicji schematu XML struktury dokumentu XML.  
  
## <a name="the-schema-inference-process"></a>Procesu wnioskowania schematu  
 <xref:System.Xml.Schema.XmlSchemaInference> Klasy <xref:System.Xml.Schema?displayProperty=nameWithType> przestrzeń nazw jest używana do generowania co najmniej jednego schematu języka (XSD) definicji schematu XML ze struktury dokumentu XML. Wygenerowany schematów mogą służyć do zweryfikowania oryginalnego dokumentu XML.  
  
 Jako pliku XML dokumentu jest przetwarzany przez <xref:System.Xml.Schema.XmlSchemaInference> klasy <xref:System.Xml.Schema.XmlSchemaInference> klasy sprawia, że założenia dotyczące składników schematu, które opisują elementów i atrybutów w dokumencie XML. <xref:System.Xml.Schema.XmlSchemaInference> Klasy również wnioskuje składników schematu w sposób ograniczone przez wnioskowanie najbardziej restrykcyjny typ dla konkretnego elementu lub atrybutu. Jak dowiedzieć się więcej o dokumentu XML są zbierane, te ograniczenia są zmniejszyć przez wnioskowanie typów mniej restrykcyjne uprawnienia. Jest najmniej restrykcyjny typ, który można wywnioskować `xs:string`.  
  
 Weźmy na przykład, następujące części dokumentu XML.  
  
```xml  
<parent attribute1="6">  
    <child>One</child>  
    <child>Two</child>  
</parent>  
<parent attribute1="A">  
```  
  
 W przykładzie powyżej, kiedy `attribute1` napotkano atrybutu o wartości `6` przez <xref:System.Xml.Schema.XmlSchemaInference> procesu, zakłada się być typu `xs:unsignedByte`. Podczas drugiego `parent` napotkane elementu przez <xref:System.Xml.Schema.XmlSchemaInference> procesu ograniczenie się zmniejszyć, modyfikując typu, który ma `xs:string` ponieważ wartość `attribute1` atrybut jest teraz `A`. Podobnie `minOccurs` atrybutu dla wszystkich `child` wywnioskować w schemacie elementy są zmniejszyć do `minOccurs="0"` ponieważ drugi element nadrzędny nie ma elementów podrzędnych.  
  
## <a name="inferring-schemas-from-xml-documents"></a>Wnioskowanie schematów na podstawie dokumentów XML  
 <xref:System.Xml.Schema.XmlSchemaInference> Klasa używa dwóch przeciążone <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> metod, które można pobrać schematu z dokumentu XML.  
  
 Pierwszy <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> metoda służy do tworzenia schemat, na podstawie dokumentu XML. Drugi <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> metoda jest używana do wnioskowania dotyczącego schematu, który opisuje wiele dokumentów XML. Na przykład można dostarczyć wiele dokumentów XML, aby <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> metodą w czasie, aby wygenerować schemat opisujący cały zestaw dokumentów XML.  
  
 Pierwszy <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> metoda wnioskuje schemat z dokumentu XML zawartych w <xref:System.Xml.XmlReader> obiektu i zwraca <xref:System.Xml.Schema.XmlSchemaSet> obiektu zawierającego schemat wykrywany. Drugi <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> metoda wyszukuje <xref:System.Xml.Schema.XmlSchemaSet> obiekt do schematu z tej samej docelowego obszaru nazw w dokumencie XML znajdujący się w <xref:System.Xml.XmlReader> usprawniają istniejącego schematu obiektu i zwraca <xref:System.Xml.Schema.XmlSchemaSet> obiekt zawierający wywnioskowane schemat.  
  
 Zmiany wprowadzone w schemacie dostosowany opierają się na nowej struktury w dokumencie XML. Na przykład zgodnie z dokumentu XML, o ile, założenia składają się o znaleziono typów danych i schemat jest tworzony na podstawie tych założeń. Jednakże jeśli dane na drugi wnioskowania — dostęp próbny, różni się od oryginalnego założeń, schemat jest dostosowany. Poniższy przykład przedstawia proces uściślenia.  
  
 [!code-cpp[XmlSchemaInferenceExamples#4](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaInferenceExamples/CPP/XmlSchemaInferenceExamples.cpp#4)]
 [!code-csharp[XmlSchemaInferenceExamples#4](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaInferenceExamples/CS/XmlSchemaInferenceExamples.cs#4)]
 [!code-vb[XmlSchemaInferenceExamples#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaInferenceExamples/VB/XmlSchemaInferenceExamples.vb#4)]  
  
 Przykład przyjmuje następującego pliku `item1.xml`, jako pierwszy danych wejściowych.  
  
 [!code-xml[XmlSchemaInferenceExamples#13](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/item1.xml#13)]  
  
 Przykład następnie przyjmuje `item2.xml` pliku jako dane wejściowe drugiego:  
  
 [!code-xml[XmlSchemaInferenceExamples#14](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/item2.xml#14)]  
  
 Gdy `productID` napotkano atrybutu w dokumencie XML z pierwszej wartości `123456789` zakłada się, że `xs:unsignedInt` typu. Kiedy drugi dokument XML jest jednak odczytu i wartość `A53-246` zostanie znaleziony, `xs:unsignedInt` typu nie będzie można również założyć. Schemat jest dostosowany i typu `productID` jest zmieniana na `xs:string`. Ponadto `minOccurs` atrybutu dla `supplierID` element jest ustawiony na `0`, ponieważ drugi dokument XML nie zawiera żadnych `supplierID` elementu.  
  
 Poniżej znajduje się schemat wnioskowany z pierwszego dokumentu XML.  
  
 [!code-xml[XmlSchemaInferenceExamples#15](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/InferSchema1.xml#15)]  
  
 Poniżej znajduje się schemat wnioskowany z pierwszego dokumentu XML, przez drugi dokument XML.  
  
 [!code-xml[XmlSchemaInferenceExamples#16](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/InferSchema2.xml#16)]  
  
## <a name="inline-schemas"></a>Wbudowane schematy  
 Jeśli wbudowanego schematu języka (XSD) definicji schematu XML jest napotkał podczas <xref:System.Xml.Schema.XmlSchemaInference> procesu <xref:System.Xml.Schema.XmlSchemaInferenceException> zgłaszany. Na przykład generuje następujące wbudowanego schematu <xref:System.Xml.Schema.XmlSchemaInferenceException>.  
  
```xml  
<root xmlns:ex="http://www.contoso.com" xmlns="http://www.tempuri.org">  
    <xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" targetNamespace="http://www.contoso.com">  
        <xs:element name="Contoso" type="xs:normalizedString" />  
    </xs:schema>  
    <ex:Contoso>Test</ex:Contoso>  
</root>  
```  
  
## <a name="schemas-that-cannot-be-refined"></a>Schematy, które nie może być Refined  
 Brak schematu XML W3C konstrukcji, która schematu języka (XSD) definicji schematu XML <xref:System.Xml.Schema.XmlSchemaInference> procesu nie może obsłużyć, jeśli określony typ, aby dostosować i powodować zgłoszenie wyjątku. Takie jak typ złożony którego compositor najwyższego poziomu jest inna niż sekwencji. W modelu obiektów schematu (SOM) odpowiada <xref:System.Xml.Schema.XmlSchemaComplexType> którego <xref:System.Xml.Schema.XmlSchemaComplexType.Particle%2A> właściwość nie jest wystąpieniem <xref:System.Xml.Schema.XmlSchemaSequence>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Schema.XmlSchemaInference>  
- [Model SOM (XML Schema Object Model)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)  
- [Wnioskowanie schematu XML](../../../../docs/standard/data/xml/inferring-an-xml-schema.md)  
- [Zasady wnioskowania typów węzłów schematu i struktury](../../../../docs/standard/data/xml/rules-for-inferring-schema-node-types-and-structure.md)  
- [Zasady wnioskowania typów prostych](../../../../docs/standard/data/xml/rules-for-inferring-simple-types.md)
