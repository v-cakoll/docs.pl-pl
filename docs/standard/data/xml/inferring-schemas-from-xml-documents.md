---
title: Wnioskowanie schematów na podstawie dokumentów XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: f3d97d53-614d-4a04-a174-87965b7405f6
ms.openlocfilehash: 5c2d997d9006a3f1eb971eac20982b9dd5677ebf
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710755"
---
# <a name="inferring-schemas-from-xml-documents"></a>Wnioskowanie schematów na podstawie dokumentów XML
W tym temacie opisano sposób użycia <xref:System.Xml.Schema.XmlSchemaInference> klasy do wywnioskowania schematu języka definicji schematu XML (XSD) ze struktury dokumentu XML.  
  
## <a name="the-schema-inference-process"></a>Proces wnioskowania schematu  
 <xref:System.Xml.Schema.XmlSchemaInference> Klasa <xref:System.Xml.Schema?displayProperty=nameWithType> przestrzeni nazw służy do generowania co najmniej jednego schematu języka definicji schematu XML (XSD) ze struktury dokumentu XML. Wygenerowane schematy mogą służyć do sprawdzania poprawności oryginalnego dokumentu XML.  
  
 Ponieważ dokument XML jest przetwarzany przez <xref:System.Xml.Schema.XmlSchemaInference> klasę, <xref:System.Xml.Schema.XmlSchemaInference> Klasa tworzy założenia dotyczące składników schematu, które opisują elementy i atrybuty w dokumencie XML. <xref:System.Xml.Schema.XmlSchemaInference> Klasa również wnioskuje składniki schematu w ograniczony sposób, wprowadzając najbardziej restrykcyjny typ dla określonego elementu lub atrybutu. Po zebraniu większej ilości informacji o dokumencie XML te ograniczenia są zmniejszane przez wnioskowanie mniej restrykcyjnych typów. Najmniej restrykcyjny typ, który można wywnioskować, `xs:string`to.  
  
 Zrób na przykład poniższy fragment dokumentu XML.  
  
```xml  
<parent attribute1="6">  
    <child>One</child>  
    <child>Two</child>  
</parent>  
<parent attribute1="A">  
```  
  
 W powyższym przykładzie, gdy `attribute1` atrybut zostanie napotkany `6` przez wartość przez <xref:System.Xml.Schema.XmlSchemaInference> proces, przyjmuje się, że jest typu. `xs:unsignedByte` Gdy drugi `parent` element zostanie napotkany przez <xref:System.Xml.Schema.XmlSchemaInference> proces, ograniczenie jest ograniczane przez modyfikację typu do `xs:string` , ponieważ wartość `attribute1` atrybutu jest teraz. `A` Podobnie `minOccurs` atrybut dla wszystkich elementów, `child` które `minOccurs="0"` zostały wywnioskowane w schemacie, jest przyznany, ponieważ drugi element nadrzędny nie ma elementów podrzędnych.  
  
## <a name="inferring-schemas-from-xml-documents"></a>Wnioskowanie schematów na podstawie dokumentów XML  
 <xref:System.Xml.Schema.XmlSchemaInference> Klasa używa dwóch przeciążonych <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> metod do wywnioskowania schematu z dokumentu XML.  
  
 Pierwsza <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> Metoda jest używana do tworzenia schematu na podstawie dokumentu XML. Druga <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> Metoda służy do wnioskowania schematu opisującego wiele dokumentów XML. Na przykład można utworzyć strumieniowo wiele dokumentów XML do <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> metody po jednej naraz w celu utworzenia schematu opisującego cały zestaw dokumentów XML.  
  
 Pierwsza <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> Metoda wnioskuje schemat z dokumentu XML zawartego w <xref:System.Xml.XmlReader> obiekcie i zwraca <xref:System.Xml.Schema.XmlSchemaSet> obiekt zawierający wywnioskowany schemat. Druga <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> Metoda <xref:System.Xml.Schema.XmlSchemaSet> przeszukuje obiekt dla schematu z tą samą docelową przestrzenią nazw, co dokument XML zawarty <xref:System.Xml.XmlReader> w obiekcie, uściślije istniejący schemat i zwraca <xref:System.Xml.Schema.XmlSchemaSet> obiekt zawierający wywnioskowany schemat.  
  
 Zmiany wprowadzone w rafinowanym schemacie są oparte na nowej strukturze, która znajduje się w dokumencie XML. Na przykład w przypadku przechodzenia dokumentu XML założono założenia dotyczące znalezionych typów danych, a schemat jest tworzony na podstawie tych założeń. Jednakże w przypadku wystąpienia danych w drugim przebiegu wnioskowania, który różni się od oryginalnego założeń, schemat zostanie rafinowany. Poniższy przykład ilustruje proces uściślania.  
  
 [!code-cpp[XmlSchemaInferenceExamples#4](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaInferenceExamples/CPP/XmlSchemaInferenceExamples.cpp#4)]
 [!code-csharp[XmlSchemaInferenceExamples#4](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaInferenceExamples/CS/XmlSchemaInferenceExamples.cs#4)]
 [!code-vb[XmlSchemaInferenceExamples#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaInferenceExamples/VB/XmlSchemaInferenceExamples.vb#4)]  
  
 Przykład pobiera następujący plik, `item1.xml`, jako pierwsze dane wejściowe.  
  
 [!code-xml[XmlSchemaInferenceExamples#13](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/item1.xml#13)]  
  
 Przykład pobiera `item2.xml` plik jako drugi dane wejściowe:  
  
 [!code-xml[XmlSchemaInferenceExamples#14](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/item2.xml#14)]  
  
 Gdy `productID` atrybut zostanie napotkany w pierwszym dokumencie XML, przyjmuje się, że `123456789` wartość jest `xs:unsignedInt` typu. Jednak po odczytaniu drugiego dokumentu XML i znalezieniu wartości `A53-246` , `xs:unsignedInt` typ nie może być już przyjęty. Schemat jest rafinowany i typ `productID` zostanie zmieniony na. `xs:string` Ponadto `minOccurs` atrybut dla `supplierID` elementu jest ustawiony na `0`, ponieważ drugi dokument XML nie `supplierID` zawiera elementu.  
  
 Poniżej znajduje się schemat wnioskowany na podstawie pierwszego dokumentu XML.  
  
 [!code-xml[XmlSchemaInferenceExamples#15](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/InferSchema1.xml#15)]  
  
 Poniżej znajduje się schemat wnioskowany na podstawie pierwszego dokumentu XML, rafinowany przez drugi dokument XML.  
  
 [!code-xml[XmlSchemaInferenceExamples#16](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/InferSchema2.xml#16)]  
  
## <a name="inline-schemas"></a>Schematy wbudowane  
 Jeśli podczas <xref:System.Xml.Schema.XmlSchemaInference> procesu napotkany jest schemat języka definicji wbudowanego schematu XML (XSD), <xref:System.Xml.Schema.XmlSchemaInferenceException> zostanie zgłoszony. Na przykład poniższy schemat wbudowany zgłasza <xref:System.Xml.Schema.XmlSchemaInferenceException>.  
  
```xml  
<root xmlns:ex="http://www.contoso.com" xmlns="http://www.tempuri.org">  
    <xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" targetNamespace="http://www.contoso.com">  
        <xs:element name="Contoso" type="xs:normalizedString" />  
    </xs:schema>  
    <ex:Contoso>Test</ex:Contoso>  
</root>  
```  
  
## <a name="schemas-that-cannot-be-refined"></a>Schematy, które nie mogą zostać ulepszone  
 Istnieją konstrukcje schematu W3C XML, które nie mogą obsłużyć procesu schematu <xref:System.Xml.Schema.XmlSchemaInference> języka definicji schematu XML (XSD), jeśli podano typ do uściślenia i spowoduje zgłoszenie wyjątku. Takie jak typ złożony, którego compositor najwyższego poziomu jest coś innego niż sekwencja. W modelu Object Model (SOM) odnosi się do obiektu <xref:System.Xml.Schema.XmlSchemaComplexType> , którego <xref:System.Xml.Schema.XmlSchemaComplexType.Particle%2A> właściwość nie jest wystąpieniem. <xref:System.Xml.Schema.XmlSchemaSequence>  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Xml.Schema.XmlSchemaInference>
- [Model SOM (XML Schema Object Model)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)
- [Wnioskowanie schematu XML](../../../../docs/standard/data/xml/inferring-an-xml-schema.md)
- [Zasady wnioskowania typów węzłów schematu i struktury](../../../../docs/standard/data/xml/rules-for-inferring-schema-node-types-and-structure.md)
- [Zasady wnioskowania typów prostych](../../../../docs/standard/data/xml/rules-for-inferring-simple-types.md)
