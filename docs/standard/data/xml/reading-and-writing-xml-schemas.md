---
title: Odczytywanie i zapisywanie schematów XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: b5757c4a-ea59-467e-ac62-be2bfe24eb77
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 241ff40448c3dca2846f9e420dc7df41427dc79d
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44266894"
---
# <a name="reading-and-writing-xml-schemas"></a>Odczytywanie i zapisywanie schematów XML
Schematu Object Model (model SOM) interfejsu API może służyć do odczytu i zapisu schematów języka (XSD) definicji schematu XML z plików lub innych źródeł i tworzenie XML schematów w pamięci przy użyciu klas w <xref:System.Xml.Schema?displayProperty=nameWithType> przestrzeni nazw, które są mapowane do struktur, zdefiniowanych na całym świecie Wide Web Consortium (W3C) XML schematu zalecenia.  
  
## <a name="reading-and-writing-xml-schemas"></a>Odczytywanie i zapisywanie schematów XML  
 <xref:System.Xml.Schema.XmlSchema> Klasa udostępnia <xref:System.Xml.Schema.XmlSchema.Read%2A> i <xref:System.Xml.Schema.XmlSchema.Write%2A> metody na odczytywanie i zapisywanie schematów XML. <xref:System.Xml.Schema.XmlSchema.Read%2A> Metoda zwraca <xref:System.Xml.Schema.XmlSchema> obiekt reprezentujący schemat XML i przyjmuje opcjonalny <xref:System.Xml.Schema.ValidationEventHandler> jako parametr do obsługi schematu Walidacja ostrzeżeń i błędów napotkanych podczas odczytywania schematu XML.  
  
 <xref:System.Xml.Schema.XmlSchema.Write%2A> Metoda zapisuje schematów XML do <xref:System.IO.Stream>, <xref:System.IO.TextWriter> i <xref:System.Xml.XmlWriter> obiektów i może opcjonalnie <xref:System.Xml.XmlNamespaceManager> obiektu jako parametr. <xref:System.Xml.XmlNamespaceManager> Jest używana do obsługi przestrzeni nazw w schematu XML. Aby uzyskać więcej informacji na temat <xref:System.Xml.XmlNamespaceManager> klasy, zobacz [Zarządzanie przestrzeni nazw w dokumencie XML](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md).  
  
 Poniższy przykład kodu ilustruje odczytywanie i zapisywanie schematów XML z i do pliku. Przykładowy kod pobiera `example.xsd` pliku odczytuje go do <xref:System.Xml.Schema.XmlSchema> przy użyciu `static` <xref:System.Xml.Schema.XmlSchema.Read%2A> metody, a następnie zapisuje plik do konsoli jak i nową `new.xsd` pliku. Udostępnia również przykładowy kod <xref:System.Xml.Schema.ValidationEventHandler> jako parametr do `static` <xref:System.Xml.Schema.XmlSchema.Read%2A> metody, aby obsłużyć schematu sprawdzania poprawności ostrzeżeń i błędów napotkanych podczas odczytywania schematu XML. Jeśli <xref:System.Xml.Schema.ValidationEventHandler> nie jest określony (`null`), żadne ostrzeżenia ani błędy są zgłaszane.  
  
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
