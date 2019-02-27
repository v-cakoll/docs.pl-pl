---
title: Walidacja schematu (XSD) XML przy użyciu klasy XmlSchemaSet
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 359b10eb-ec05-4cc6-ac96-c2b060afc4de
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7db1b0fe3d4b884bca2c2b00cc95c0872bfa7e7a
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2019
ms.locfileid: "56835580"
---
# <a name="xml-schema-xsd-validation-with-xmlschemaset"></a>Walidacja schematu (XSD) XML przy użyciu klasy XmlSchemaSet
Można zweryfikować względem schematu języka (XSD) definicji schematu XML w dokumentach XML <xref:System.Xml.Schema.XmlSchemaSet>.  
  
## <a name="validating-xml-documents"></a>Walidacja dokumentów XML  
 Dokumenty XML są weryfikowane przez <xref:System.Xml.XmlReader.Create%2A> metody <xref:System.Xml.XmlReader> klasy. Aby sprawdzić poprawność dokumentu XML, należy utworzyć <xref:System.Xml.XmlReaderSettings> obiekt, który zawiera schemat języka (XSD) definicji schematu XML za pomocą którego do walidacji dokumentu XML.  
  
> [!NOTE]
>  <xref:System.Xml.Schema> Przestrzeń nazw zawiera metody rozszerzenia, które ułatwiają sprawdzanie poprawności drzewa XML z pliku XSD, korzystając z [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) i [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md). Aby uzyskać więcej informacji na temat weryfikacji dokumentów XML za pomocą LINQ to XML, zobacz [jak: Weryfikowanie przy użyciu XSD (LINQ to XML) (C#)](../../../csharp/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md) i [jak: Weryfikowanie przy użyciu XSD (LINQ to XML) (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md).  
  
 Poszczególne schematu lub zestawu schematów (jako <xref:System.Xml.Schema.XmlSchemaSet>) mogą być dodawane do <xref:System.Xml.Schema.XmlSchemaSet> , przekazując jeden jako parametr do <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metody <xref:System.Xml.Schema.XmlSchemaSet>. Należy pamiętać, że podczas weryfikowania dokumentu docelowego obszaru nazw dokumentu musi odpowiadać docelowego obszaru nazw schematu w zestawie schematów.  
  
 Oto przykład dokumentu XML.  
  
 [!code-xml[XSDInference Examples#5](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xml#5)]  
  
 Poniżej znajduje się schemat, który sprawdza poprawność przykładowy dokument XML.  
  
 [!code-xml[XSDInference Examples#6](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xsd#6)]  
  
 W poniższym przykładzie kodu powyższego schematu jest dodawany do <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.XmlReaderSettings.Schemas%2A> właściwość <xref:System.Xml.XmlReaderSettings> obiektu. <xref:System.Xml.XmlReaderSettings> Obiekt jest przekazywany jako parametr do <xref:System.Xml.XmlReader.Create%2A> metody <xref:System.Xml.XmlReader> obiektu, który sprawdza poprawność dokumentu XML powyżej.  
  
 <xref:System.Xml.XmlReaderSettings.ValidationType%2A> Właściwość <xref:System.Xml.XmlReaderSettings> obiekt jest ustawiony na `Schema` do weryfikacji dokument XML za wymuszania <xref:System.Xml.XmlReader.Create%2A> metody <xref:System.Xml.XmlReader> obiektu. A <xref:System.Xml.Schema.ValidationEventHandler> jest dodawany do <xref:System.Xml.XmlReaderSettings> obiektu do obsługi dowolnej <xref:System.Xml.Schema.XmlSeverityType.Warning> lub <xref:System.Xml.Schema.XmlSeverityType.Error> zdarzeń wywołanych przez błędy znalezione w trakcie procesu walidacji dokumentu XML i schematu.  
  
 [!code-cpp[XmlSchemaSetOverall Example#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaSetOverall Example/CPP/xmlschemasetexample.cpp#1)]
 [!code-csharp[XmlSchemaSetOverall Example#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaSetOverall Example/CS/xmlschemasetexample.cs#1)]
 [!code-vb[XmlSchemaSetOverall Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaSetOverall Example/VB/xmlschemasetexample.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Klasa XmlSchemaSet na potrzeby kompilacji schematu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [Praca ze schematami XML](../../../../docs/standard/data/xml/working-with-xml-schemas.md)
