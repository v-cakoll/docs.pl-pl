---
title: Odczytywanie i zapisywanie schematów XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: b5757c4a-ea59-467e-ac62-be2bfe24eb77
ms.openlocfilehash: 889c5f85a2ea3fc08dadefda5509de0fcfab76ec
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710417"
---
# <a name="reading-and-writing-xml-schemas"></a>Odczytywanie i zapisywanie schematów XML
Za pomocą interfejsu API modelu obiektów schematu (SOM) można odczytywać i zapisywać schematy języka definicji schematu XML (XSD) z plików lub innych źródeł oraz tworzyć schematy XML w pamięci przy użyciu klas w przestrzeni nazw <xref:System.Xml.Schema?displayProperty=nameWithType>, które są mapowane na struktury zdefiniowane w zaleceniu schematu XML organizacja World Wide Web Consortium (W3C).  
  
## <a name="reading-and-writing-xml-schemas"></a>Odczytywanie i zapisywanie schematów XML  
 Klasa <xref:System.Xml.Schema.XmlSchema> udostępnia metody <xref:System.Xml.Schema.XmlSchema.Read%2A> i <xref:System.Xml.Schema.XmlSchema.Write%2A> do odczytywania i zapisywania schematów XML. Metoda <xref:System.Xml.Schema.XmlSchema.Read%2A> zwraca obiekt <xref:System.Xml.Schema.XmlSchema> reprezentujący schemat XML i przyjmuje opcjonalny <xref:System.Xml.Schema.ValidationEventHandler> jako parametr obsługujący ostrzeżenia i błędy walidacji schematu podczas odczytywania schematu XML.  
  
 Metoda <xref:System.Xml.Schema.XmlSchema.Write%2A> zapisuje schematy XML do <xref:System.IO.Stream>, <xref:System.IO.TextWriter> i <xref:System.Xml.XmlWriter> obiektów i może przyjmować opcjonalny obiekt <xref:System.Xml.XmlNamespaceManager> jako parametr. <xref:System.Xml.XmlNamespaceManager> jest używany do obsługi przestrzeni nazw napotkanych w schemacie XML. Aby uzyskać więcej informacji na temat klasy <xref:System.Xml.XmlNamespaceManager>, zobacz [Zarządzanie przestrzeniami nazw w dokumencie XML](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md).  
  
 Poniższy przykład kodu ilustruje odczytywanie i zapisywanie schematów XML z i do pliku. Przykładowy kod pobiera `example.xsd` plik, odczytuje go do obiektu <xref:System.Xml.Schema.XmlSchema> przy użyciu metody `static`<xref:System.Xml.Schema.XmlSchema.Read%2A>, a następnie zapisuje plik w konsoli programu i w nowym pliku `new.xsd`. Przykład kodu udostępnia również <xref:System.Xml.Schema.ValidationEventHandler> jako parametr metody `static`<xref:System.Xml.Schema.XmlSchema.Read%2A> do obsługi wszelkich ostrzeżeń lub błędów walidacji schematu podczas odczytywania schematu XML. Jeśli nie określono <xref:System.Xml.Schema.ValidationEventHandler> (`null`), nie są zgłaszane żadne ostrzeżenia ani błędy.  
  
 [!code-cpp[XmlSchemaReadWriteExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaReadWriteExample/CPP/XmlSchemaReadWriteExample.cpp#1)]
 [!code-csharp[XmlSchemaReadWriteExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaReadWriteExample/CS/XmlSchemaReadWriteExample.cs#1)]
 [!code-vb[XmlSchemaReadWriteExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaReadWriteExample/VB/XmlSchemaReadWriteExample.vb#1)]  
  
 Przykład przyjmuje `example.xsd` jako dane wejściowe.  
  
```xml  
<?xml version="1.0"?>  
<xs:schema id="play" targetNamespace="http://tempuri.org/play.xsd" elementFormDefault="qualified" xmlns="http://tempuri.org/play.xsd" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:element name='myShoeSize'>  
        <xs:complexType>  
            <xs:simpleContent>  
                <xs:extension base='xs:decimal'>  
                    <xs:attribute name='sizing' type='xs:string' />  
                </xs:extension>  
            </xs:simpleContent>  
        </xs:complexType>  
    </xs:element>  
</xs:schema>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Model SOM (XML Schema Object Model) ― omówienie](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)
- [Tworzenie schematów XML](../../../../docs/standard/data/xml/building-xml-schemas.md)
- [Przechodzenie schematów XML](../../../../docs/standard/data/xml/traversing-xml-schemas.md)
- [Edytowanie schematów XML](../../../../docs/standard/data/xml/editing-xml-schemas.md)
- [Uwzględnianie lub importowanie schematów XML](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)
- [Klasa XmlSchemaSet na potrzeby kompilacji schematu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [Zestaw informacji po kompilacji schematu](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
- [Zarządzanie przestrzeniami nazw w dokumencie XML](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md)
