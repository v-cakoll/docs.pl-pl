---
title: Wnioskowanie schematów z dokumentów XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: f3d97d53-614d-4a04-a174-87965b7405f6
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f8640a951acab512cbe2397df831a74700b5ad6c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="inferring-schemas-from-xml-documents"></a>Wnioskowanie schematów z dokumentów XML
W tym temacie opisano sposób użycia <xref:System.Xml.Schema.XmlSchemaInference> klasy na potrzeby wnioskowania dotyczącego schematu schematu XML definition language (XSD) ze struktury dokumentu XML.  
  
## <a name="the-schema-inference-process"></a>Proces wnioskowania schematu  
 <xref:System.Xml.Schema.XmlSchemaInference> Klasy <xref:System.Xml.Schema?displayProperty=nameWithType> przestrzeni nazw jest używany do generowania schematów języka (XSD) definicja schematu XML co najmniej jednego ze struktury dokumentu XML. Wygenerowany schematów może służyć do zweryfikowania oryginalnego dokumentu XML.  
  
 Jako XML dokumentu jest przetwarzany przez <xref:System.Xml.Schema.XmlSchemaInference> klasy <xref:System.Xml.Schema.XmlSchemaInference> klasy sprawia, że założenia dotyczące składników schematu, które opisują elementów i atrybutów w dokumencie XML. <xref:System.Xml.Schema.XmlSchemaInference> Klasy również wnioskuje składników schematu w sposób ograniczone przez wnioskowanie najbardziej restrykcyjne typu dla określonego elementu lub atrybutu. Jak zbierane więcej informacji na temat dokumentu XML przez wnioskowanie typów mniej restrykcyjnych są zmniejszyć te ograniczenia. Jest najmniej restrykcyjny typ, który można wywnioskować `xs:string`.  
  
 Podjąć, na przykład następujące części dokumentu XML.  
  
```xml  
<parent attribute1="6">  
    <child>One</child>  
    <child>Two</child>  
</parent>  
<parent attribute1="A">  
```  
  
 W przykładzie przedstawionym powyżej, gdy `attribute1` napotkano atrybut o wartości `6` przez <xref:System.Xml.Schema.XmlSchemaInference> procesu, zakłada się, być typu `xs:unsignedByte`. Gdy drugi `parent` napotkano element przez <xref:System.Xml.Schema.XmlSchemaInference> procesów, ograniczenie jest zmniejszyć zmieniając typ do `xs:string` ponieważ wartość `attribute1` atrybut jest teraz `A`. Podobnie `minOccurs` atrybutu dla wszystkich `child` elementy wywnioskować w schemacie są zmniejszyć do `minOccurs="0"` ponieważ drugi element nadrzędny nie ma elementów podrzędnych.  
  
## <a name="inferring-schemas-from-xml-documents"></a>Wnioskowanie schematów z dokumentów XML  
 <xref:System.Xml.Schema.XmlSchemaInference> Klasa korzysta z dwóch przeciążony <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> metod można pobrać schematu z dokumentu XML.  
  
 Pierwszy <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> metoda służy do tworzenia schematu na podstawie dokumentu XML. Drugi <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> metody jest używany na potrzeby wnioskowania dotyczącego schematu, które opisują wiele dokumentów XML. Na przykład może dostarczyć wiele dokumentów XML do <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> metodą w czasie, aby wygenerować schematu, który opisuje cały zestaw dokumentów XML.  
  
 Pierwszy <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> metody wnioskuje schemat z dokumentu XML zawartych w <xref:System.Xml.XmlReader> obiektu i zwraca <xref:System.Xml.Schema.XmlSchemaSet> obiekt zawierający wywnioskowany schemat. Drugi <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> wyszukiwania — metoda <xref:System.Xml.Schema.XmlSchemaSet> obiekt do schematu z tego samego obszaru nazw docelowych zawartymi w dokumencie XML <xref:System.Xml.XmlReader> obiektu udoskonalanie istniejącego schematu i zwraca <xref:System.Xml.Schema.XmlSchemaSet> obiekt zawierający wywnioskowane schemat.  
  
 Zmiany wprowadzone w schemacie precyzyjnych są oparte na nowej struktury odnaleziono w dokumencie XML. Na przykład jako dokument XML jest przesunięta, zostają założeń dotyczących typów danych znaleziono i schemat jest tworzony na podstawie tych założeń. Jednak jeśli dane na drugi wnioskowania przebiegu różni się od oryginalnej założeń, schemat jest precyzyjnych. Poniższy przykład przedstawia proces uściślenia.  
  
 [!code-cpp[XmlSchemaInferenceExamples#4](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaInferenceExamples/CPP/XmlSchemaInferenceExamples.cpp#4)]
 [!code-csharp[XmlSchemaInferenceExamples#4](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaInferenceExamples/CS/XmlSchemaInferenceExamples.cs#4)]
 [!code-vb[XmlSchemaInferenceExamples#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaInferenceExamples/VB/XmlSchemaInferenceExamples.vb#4)]  
  
 Przykład przyjmuje następującego pliku `item1.xml`, jako jego pierwszej danej wejściowej.  
  
 [!code-xml[XmlSchemaInferenceExamples#13](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/item1.xml#13)]  
  
 Przykład bierze `item2.xml` pliku jako dane wejściowe drugiego:  
  
 [!code-xml[XmlSchemaInferenceExamples#14](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/item2.xml#14)]  
  
 Gdy `productID` napotkano w pierwszy dokument XML, wartość atrybutu `123456789` zakłada się, że `xs:unsignedInt` typu. Podczas drugiego dokumentu XML jest jednak odczytu i wartość `A53-246` zostanie znaleziony, `xs:unsignedInt` nie można przyjąć typu. Schemat jest precyzyjnych i typ `productID` jest zmieniana na `xs:string`. Ponadto `minOccurs` atrybutu dla `supplierID` element jest ustawiony na wartość `0`, ponieważ jest drugi dokument XML nie `supplierID` elementu.  
  
 Oto schemat wywnioskować na podstawie pierwszego dokumentu XML.  
  
 [!code-xml[XmlSchemaInferenceExamples#15](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/InferSchema1.xml#15)]  
  
 Oto schemat wywnioskować na podstawie pierwszy dokument XML, przez drugiego dokumentu XML.  
  
 [!code-xml[XmlSchemaInferenceExamples#16](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/InferSchema2.xml#16)]  
  
## <a name="inline-schemas"></a>Wbudowane schematy  
 Jeśli schemat wbudowany schemat XML definition language (XSD) napotkano podczas <xref:System.Xml.Schema.XmlSchemaInference> procesu <xref:System.Xml.Schema.XmlSchemaInferenceException> jest generowany. Na przykład następujące wbudowanego schematu zgłasza <xref:System.Xml.Schema.XmlSchemaInferenceException>.  
  
```xml  
<root xmlns:ex="http://www.contoso.com" xmlns="http://www.tempuri.org">  
    <xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" targetNamespace="http://www.contoso.com">  
        <xs:element name="Contoso" type="xs:normalizedString" />  
    </xs:schema>  
    <ex:Contoso>Test</ex:Contoso>  
</root>  
```  
  
## <a name="schemas-that-cannot-be-refined"></a>Schematów, które nie mogą być Refined  
 Brak konstrukcje schematu W3C XML, który schematu (XSD) języka definicji schematu XML <xref:System.Xml.Schema.XmlSchemaInference> procesu nie może obsłużyć, jeśli określony typ, aby doprecyzować i spowodować wyjątków. Takie jak typ złożony którego compositor najwyższego poziomu jest inna niż sekwencji. W modelu obiektu schematu (SOM) odpowiada <xref:System.Xml.Schema.XmlSchemaComplexType> których <xref:System.Xml.Schema.XmlSchemaComplexType.Particle%2A> właściwość nie jest wystąpieniem <xref:System.Xml.Schema.XmlSchemaSequence>.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.Schema.XmlSchemaInference>  
 [Model SOM (XML Schema Object Model)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)  
 [Wnioskowanie schematu XML](../../../../docs/standard/data/xml/inferring-an-xml-schema.md)  
 [Zasady wnioskowania typów węzłów schematu i struktury](../../../../docs/standard/data/xml/rules-for-inferring-schema-node-types-and-structure.md)  
 [Zasady wnioskowania typów prostych](../../../../docs/standard/data/xml/rules-for-inferring-simple-types.md)
