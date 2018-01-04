---
title: Odczytywanie i zapisywanie schematy XML
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
ms.assetid: b5757c4a-ea59-467e-ac62-be2bfe24eb77
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 96f8cf924ffe510e1fea4d21fe86ca860fe8fab0
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="reading-and-writing-xml-schemas"></a>Odczytywanie i zapisywanie schematy XML
Schematu obiektu modelu (SOM) interfejsu API może służyć do odczytu i zapisu definicji schematu XML schematy języka (XSD) z plików lub innych źródeł i tworzenie XML schematów w pamięci przy użyciu klas w <xref:System.Xml.Schema?displayProperty=nameWithType> przestrzeni nazw, które są mapowane na struktury zdefiniowane w świecie Zalecenie szerokiej sieci Web konsorcjum W3C XML schematu.  
  
## <a name="reading-and-writing-xml-schemas"></a>Odczytywanie i zapisywanie schematy XML  
 <xref:System.Xml.Schema.XmlSchema> Klasa udostępnia <xref:System.Xml.Schema.XmlSchema.Read%2A> i <xref:System.Xml.Schema.XmlSchema.Write%2A> metody do odczytu i zapisu schematów XML. <xref:System.Xml.Schema.XmlSchema.Read%2A> Metoda zwraca <xref:System.Xml.Schema.XmlSchema> obiekt reprezentujący schematu XML i przyjmuje opcjonalny <xref:System.Xml.Schema.ValidationEventHandler> jako parametr do obsługi schemat sprawdzania poprawności ostrzeżeń i błędów napotkanych podczas odczytywania schematu XML.  
  
 <xref:System.Xml.Schema.XmlSchema.Write%2A> Metoda zapisuje schematów XML do <xref:System.IO.Stream>, <xref:System.IO.TextWriter> i <xref:System.Xml.XmlWriter> obiektów i może być opcjonalny <xref:System.Xml.XmlNamespaceManager> obiektu jako parametr. <xref:System.Xml.XmlNamespaceManager> Służy do obsługi przestrzeni nazw w schematu XML. Aby uzyskać więcej informacji na temat <xref:System.Xml.XmlNamespaceManager> , zobacz [Zarządzanie przestrzeni nazw w dokumencie XML](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md).  
  
 W poniższym przykładzie kodu przedstawiono odczytywanie i zapisywanie schematów XML z i do pliku. Przykładowy kod ma `example.xsd` pliku odczytuje go do <xref:System.Xml.Schema.XmlSchema> przy użyciu `static` <xref:System.Xml.Schema.XmlSchema.Read%2A> metody, a następnie zapisuje plik do konsoli i nowy `new.xsd` pliku. Udostępnia również przykładowy kod <xref:System.Xml.Schema.ValidationEventHandler> jako parametr `static` <xref:System.Xml.Schema.XmlSchema.Read%2A> można obsłużyć schemat sprawdzania poprawności ostrzeżeń i błędów napotkanych podczas odczytywania schematu XML. Jeśli <xref:System.Xml.Schema.ValidationEventHandler> nie określono (`null`), nie zostały zgłoszone nie ostrzeżenia i błędy.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Model SOM (XML Schema Object Model) ― omówienie](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)  
 [Tworzenie schematów XML](../../../../docs/standard/data/xml/building-xml-schemas.md)  
 [Przechodzenie schematów XML](../../../../docs/standard/data/xml/traversing-xml-schemas.md)  
 [Edytowanie schematów XML](../../../../docs/standard/data/xml/editing-xml-schemas.md)  
 [Uwzględnianie lub importowanie schematów XML](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)  
 [Klasa XmlSchemaSet na potrzeby kompilacji schematu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 [Zestaw informacji po kompilacji schematu](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)  
 [Zarządzanie przestrzeniami nazw w dokumencie XML](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md)
