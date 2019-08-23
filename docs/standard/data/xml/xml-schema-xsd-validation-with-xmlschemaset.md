---
title: Sprawdzanie poprawności schematu XML (XSD) przy użyciu klasy XmlSchemaSet
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 359b10eb-ec05-4cc6-ac96-c2b060afc4de
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9bdcfe785d6f5f81d721acd45eebb580b08b2d14
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916075"
---
# <a name="xml-schema-xsd-validation-with-xmlschemaset"></a>Sprawdzanie poprawności schematu XML (XSD) przy użyciu klasy XmlSchemaSet
Dokumenty XML można sprawdzić pod kątem schematu języka definicji schematu XML (XSD) w <xref:System.Xml.Schema.XmlSchemaSet>.  
  
## <a name="validating-xml-documents"></a>Sprawdzanie poprawności dokumentów XML  
 Dokumenty XML są sprawdzane za <xref:System.Xml.XmlReader.Create%2A> pomocą metody <xref:System.Xml.XmlReader> klasy. Aby sprawdzić poprawność dokumentu XML, <xref:System.Xml.XmlReaderSettings> Utwórz obiekt, który zawiera schemat języka definicji schematu XML (XSD), za pomocą którego można sprawdzić poprawność dokumentu XML.  
  
> [!NOTE]
> Przestrzeń nazw zawiera metody rozszerzające, które ułatwiają Weryfikowanie drzewa XML względem pliku XSD przy użyciu [LINQ to XMLC#()](../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) i [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md). <xref:System.Xml.Schema> Aby uzyskać więcej informacji na temat sprawdzania poprawności dokumentów XML za [pomocą LINQ to XML, zobacz How to: Weryfikuj przy użyciu XSD (LINQ to XML)C#(](../../../csharp/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md) ) [i instrukcje: Sprawdź poprawność przy użyciu XSD (LINQ to XML](../../../visual-basic/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md)) (Visual Basic).  
  
 Pojedynczy schemat lub zestaw <xref:System.Xml.Schema.XmlSchemaSet>schematów (jako) można dodać do obiektu <xref:System.Xml.Schema.XmlSchemaSet> , przekazując jeden <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> jako <xref:System.Xml.Schema.XmlSchemaSet>parametr do metody. Należy pamiętać, że podczas walidacji dokumentu docelowa przestrzeń nazw dokumentu musi być zgodna z docelową przestrzenią nazw schematu w zestawie schematów.  
  
 Poniżej znajduje się przykładowy dokument XML.  
  
 [!code-xml[XSDInference Examples#5](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xml#5)]  
  
 Poniżej znajduje się schemat, który sprawdza poprawność przykładowego dokumentu XML.  
  
 [!code-xml[XSDInference Examples#6](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xsd#6)]  
  
 W poniższym przykładzie kodu schemat został dodany do <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.XmlReaderSettings.Schemas%2A> właściwości <xref:System.Xml.XmlReaderSettings> obiektu. Obiekt jest przekazaniem jako parametr <xref:System.Xml.XmlReader.Create%2A> do metody <xref:System.Xml.XmlReader> obiektu, który sprawdza powyższy dokument XML. <xref:System.Xml.XmlReaderSettings>  
  
 `Schema` <xref:System.Xml.XmlReader.Create%2A> Właściwość obiektu jest ustawiona na tak, aby wymuszać walidację dokumentu XML przez metodę <xref:System.Xml.XmlReader> obiektu. <xref:System.Xml.XmlReaderSettings> <xref:System.Xml.XmlReaderSettings.ValidationType%2A> Element <xref:System.Xml.Schema.ValidationEventHandler> jest dodawany <xref:System.Xml.XmlReaderSettings> do obiektu, aby obsłużyć <xref:System.Xml.Schema.XmlSeverityType.Error> dowolne <xref:System.Xml.Schema.XmlSeverityType.Warning> lub zdarzenia zgłoszone przez błędy znalezione podczas procesu weryfikacji zarówno dokumentu XML, jak i schematu.  
  
 [!code-cpp[XmlSchemaSetOverall Example#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaSetOverall Example/CPP/xmlschemasetexample.cpp#1)]
 [!code-csharp[XmlSchemaSetOverall Example#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaSetOverall Example/CS/xmlschemasetexample.cs#1)]
 [!code-vb[XmlSchemaSetOverall Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaSetOverall Example/VB/xmlschemasetexample.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Klasa XmlSchemaSet na potrzeby kompilacji schematu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [Praca ze schematami XML](../../../../docs/standard/data/xml/working-with-xml-schemas.md)
