---
title: Sprawdzanie poprawności schematu XML (XSD) przy użyciu klasy XmlSchemaSet
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 359b10eb-ec05-4cc6-ac96-c2b060afc4de
ms.openlocfilehash: 6bd7525b77d4154193b57f8e6589cb865ace5fd6
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709884"
---
# <a name="xml-schema-xsd-validation-with-xmlschemaset"></a>Sprawdzanie poprawności schematu XML (XSD) przy użyciu klasy XmlSchemaSet
Dokumenty XML można sprawdzić w oparciu o schemat języka definicji schematu XML (XSD) w <xref:System.Xml.Schema.XmlSchemaSet>.  
  
## <a name="validating-xml-documents"></a>Sprawdzanie poprawności dokumentów XML  
 Dokumenty XML są weryfikowane przez metodę <xref:System.Xml.XmlReader.Create%2A> klasy <xref:System.Xml.XmlReader>. Aby sprawdzić poprawność dokumentu XML, Utwórz obiekt <xref:System.Xml.XmlReaderSettings>, który zawiera schemat języka definicji schematu XML (XSD), za pomocą którego ma zostać zweryfikowany dokument XML.  
  
> [!NOTE]
> Przestrzeń nazw <xref:System.Xml.Schema> zawiera metody rozszerzające, które ułatwiają Weryfikowanie drzewa XML względem pliku XSD przy użyciu [LINQ to XMLC#()](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) i [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md). Aby uzyskać więcej informacji na temat sprawdzania poprawności dokumentów XML za pomocą LINQ to XML, zobacz [How to Validate using XSDC#(LINQ to XML) ()](../../../csharp/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md) i [How to: Validate using XSD (LINQ to XML) (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md).
  
 Pojedynczy schemat lub zestaw schematów (jako <xref:System.Xml.Schema.XmlSchemaSet>) można dodać do <xref:System.Xml.Schema.XmlSchemaSet>, przekazując jeden jako parametr do metody <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> <xref:System.Xml.Schema.XmlSchemaSet>. Należy pamiętać, że podczas walidacji dokumentu docelowa przestrzeń nazw dokumentu musi być zgodna z docelową przestrzenią nazw schematu w zestawie schematów.  
  
 Poniżej znajduje się przykładowy dokument XML.  
  
 [!code-xml[XSDInference Examples#5](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xml#5)]  
  
 Poniżej znajduje się schemat, który sprawdza poprawność przykładowego dokumentu XML.  
  
 [!code-xml[XSDInference Examples#6](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xsd#6)]  
  
 W poniższym przykładzie kodu schemat został dodany do właściwości <xref:System.Xml.Schema.XmlSchemaSet><xref:System.Xml.XmlReaderSettings.Schemas%2A> obiektu <xref:System.Xml.XmlReaderSettings>. Obiekt <xref:System.Xml.XmlReaderSettings> jest przenoszona jako parametr do metody <xref:System.Xml.XmlReader.Create%2A> obiektu <xref:System.Xml.XmlReader>, który sprawdza powyższy dokument XML.  
  
 Właściwość <xref:System.Xml.XmlReaderSettings.ValidationType%2A> obiektu <xref:System.Xml.XmlReaderSettings> jest ustawiona na `Schema` w celu wymuszenia walidacji dokumentu XML przez metodę <xref:System.Xml.XmlReader.Create%2A> obiektu <xref:System.Xml.XmlReader>. <xref:System.Xml.Schema.ValidationEventHandler> jest dodawany do obiektu <xref:System.Xml.XmlReaderSettings>, aby obsłużyć wszystkie zdarzenia <xref:System.Xml.Schema.XmlSeverityType.Warning> lub <xref:System.Xml.Schema.XmlSeverityType.Error> zgłoszone przez błędy znalezione podczas procesu weryfikacji zarówno dokumentu XML, jak i schematu.  
  
 [!code-cpp[XmlSchemaSetOverall Example#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaSetOverall Example/CPP/xmlschemasetexample.cpp#1)]
 [!code-csharp[XmlSchemaSetOverall Example#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaSetOverall Example/CS/xmlschemasetexample.cs#1)]
 [!code-vb[XmlSchemaSetOverall Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaSetOverall Example/VB/xmlschemasetexample.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Klasa XmlSchemaSet na potrzeby kompilacji schematu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [Praca ze schematami XML](../../../../docs/standard/data/xml/working-with-xml-schemas.md)
