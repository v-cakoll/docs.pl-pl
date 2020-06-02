---
title: Odczytywanie i zapisywanie schematów XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: b5757c4a-ea59-467e-ac62-be2bfe24eb77
ms.openlocfilehash: bf1078d52f5e9056da6b28acc8dd2fc257eb3636
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291256"
---
# <a name="reading-and-writing-xml-schemas"></a>Odczytywanie i zapisywanie schematów XML
Za pomocą interfejsu API modelu Object Model (SOM) można odczytywać i zapisywać schematy języka definicji schematu XML (XSD) z plików lub innych źródeł oraz tworzyć schematy XML w pamięci przy użyciu klas w <xref:System.Xml.Schema?displayProperty=nameWithType> przestrzeni nazw, które są mapowane na struktury zdefiniowane w zaleceniu schematu xml organizacja World Wide Web Consortium (W3C).  
  
## <a name="reading-and-writing-xml-schemas"></a>Odczytywanie i zapisywanie schematów XML  
 <xref:System.Xml.Schema.XmlSchema>Klasa zawiera <xref:System.Xml.Schema.XmlSchema.Read%2A> <xref:System.Xml.Schema.XmlSchema.Write%2A> metody i do odczytywania i zapisywania schematów XML. <xref:System.Xml.Schema.XmlSchema.Read%2A>Metoda zwraca <xref:System.Xml.Schema.XmlSchema> obiekt reprezentujący schemat XML i przyjmuje opcjonalnie <xref:System.Xml.Schema.ValidationEventHandler> jako parametr obsługujący ostrzeżenia i błędy walidacji schematu podczas odczytywania schematu XML.  
  
 <xref:System.Xml.Schema.XmlSchema.Write%2A>Metoda zapisuje schematy XML do <xref:System.IO.Stream> <xref:System.IO.TextWriter> i <xref:System.Xml.XmlWriter> obiektów i może przyjmować opcjonalny <xref:System.Xml.XmlNamespaceManager> obiekt jako parametr. Służy <xref:System.Xml.XmlNamespaceManager> do obsługi przestrzeni nazw napotkanych w schemacie XML. Aby uzyskać więcej informacji na temat <xref:System.Xml.XmlNamespaceManager> klasy, zobacz [Zarządzanie przestrzeniami nazw w dokumencie XML](managing-namespaces-in-an-xml-document.md).  
  
 Poniższy przykład kodu ilustruje odczytywanie i zapisywanie schematów XML z i do pliku. Przykładowy kod pobiera `example.xsd` plik, odczytuje go do <xref:System.Xml.Schema.XmlSchema> obiektu za pomocą `static` <xref:System.Xml.Schema.XmlSchema.Read%2A> metody, a następnie zapisuje plik do konsoli programu i nowego `new.xsd` pliku. Przykład kodu dostarcza także <xref:System.Xml.Schema.ValidationEventHandler> jako parametr do `static` <xref:System.Xml.Schema.XmlSchema.Read%2A> metody do obsługi wszelkich ostrzeżeń lub błędów walidacji schematu podczas odczytywania schematu XML. Jeśli <xref:System.Xml.Schema.ValidationEventHandler> nie określono ( `null` ), nie są zgłaszane żadne ostrzeżenia ani błędy.  
  
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

- [Model SOM (XML Schema Object Model) ― omówienie](xml-schema-object-model-overview.md)
- [Tworzenie schematów XML](building-xml-schemas.md)
- [Przechodzenie schematów XML](traversing-xml-schemas.md)
- [Edytowanie schematów XML](editing-xml-schemas.md)
- [Uwzględnianie lub importowanie schematów XML](including-or-importing-xml-schemas.md)
- [Klasa XmlSchemaSet na potrzeby kompilacji schematu](xmlschemaset-for-schema-compilation.md)
- [Zestaw informacji po kompilacji schematu](post-schema-compilation-infoset.md)
- [Zarządzanie przestrzeniami nazw w dokumencie XML](managing-namespaces-in-an-xml-document.md)
