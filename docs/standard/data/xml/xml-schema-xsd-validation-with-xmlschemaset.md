---
title: "Sprawdzanie poprawności schematu (XSD) XML z XmlSchemaSet"
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
ms.assetid: 359b10eb-ec05-4cc6-ac96-c2b060afc4de
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a6cf857ccecbdac88453fd1fba6e93d609196b1a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="xml-schema-xsd-validation-with-xmlschemaset"></a>Sprawdzanie poprawności schematu (XSD) XML z XmlSchemaSet
Dokumenty XML może zostać zweryfikowany względem schematu XML schema definition language (XSD) w <xref:System.Xml.Schema.XmlSchemaSet>.  
  
## <a name="validating-xml-documents"></a>Sprawdzanie poprawności dokumentów XML  
 Dokumenty XML są weryfikowane przez <xref:System.Xml.XmlReader.Create%2A> metody <xref:System.Xml.XmlReader> klasy. Aby sprawdzić poprawność dokument XML, utworzyć <xref:System.Xml.XmlReaderSettings> obiekt, który zawiera schemat XML schematu definition language (XSD) używanemu do walidacji dokumentu XML.  
  
> [!NOTE]
>  <xref:System.Xml.Schema> Przestrzeń nazw zawiera metody rozszerzenia, które ułatwiają sprawdzanie poprawności drzewo XML przed plik XSD, korzystając z [LINQ do XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13). Aby uzyskać więcej informacji dotyczących sprawdzania poprawności dokumentów XML za pomocą LINQ do XML, zobacz [porady: Sprawdzanie poprawności za pomocą schematu XSD](http://msdn.microsoft.com/library/481a97fa-6e96-46f2-8c9a-415555fac33b).  
  
 Poszczególne schematu lub zestawu schematów (jako <xref:System.Xml.Schema.XmlSchemaSet>) mogą być dodawane do <xref:System.Xml.Schema.XmlSchemaSet> przez przekazanie dowolnego z nich jako parametr <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metody <xref:System.Xml.Schema.XmlSchemaSet>. Należy pamiętać, że podczas sprawdzania poprawności dokumentu docelowego obszaru nazw dokumentu musi odpowiadać docelowa przestrzeń nazw schematu w zestawie schematów.  
  
 Poniżej przedstawiono przykładowy dokument XML.  
  
 [!code-xml[XSDInference Examples#5](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xml#5)]  
  
 Oto schemat sprawdzania przykładowy dokument XML.  
  
 [!code-xml[XSDInference Examples#6](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xsd#6)]  
  
 W następującym przykładzie kodu powyższego schematu jest dodawany do <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.XmlReaderSettings.Schemas%2A> właściwość <xref:System.Xml.XmlReaderSettings> obiektu. <xref:System.Xml.XmlReaderSettings> Obiekt został przekazany jako parametr <xref:System.Xml.XmlReader.Create%2A> metody <xref:System.Xml.XmlReader> obiektu, który sprawdza poprawność powyżej dokumentu XML.  
  
 <xref:System.Xml.XmlReaderSettings.ValidationType%2A> Właściwość <xref:System.Xml.XmlReaderSettings> obiektu ma ustawioną wartość `Schema` wymusić dokumentu XML przez <xref:System.Xml.XmlReader.Create%2A> metody <xref:System.Xml.XmlReader> obiektu. A <xref:System.Xml.Schema.ValidationEventHandler> jest dodawany do <xref:System.Xml.XmlReaderSettings> obiektu do obsługi dowolnej <xref:System.Xml.Schema.XmlSeverityType.Warning> lub <xref:System.Xml.Schema.XmlSeverityType.Error> zdarzenia wywoływane przez błędy znalezione w procesie weryfikacji dokumentu XML i schematu.  
  
 [!code-cpp[XmlSchemaSetOverall Example#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaSetOverall Example/CPP/xmlschemasetexample.cpp#1)]
 [!code-csharp[XmlSchemaSetOverall Example#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaSetOverall Example/CS/xmlschemasetexample.cs#1)]
 [!code-vb[XmlSchemaSetOverall Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaSetOverall Example/VB/xmlschemasetexample.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 [Zestaw XmlSchemaSet schematu kompilacji](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 [Praca z schematy XML](../../../../docs/standard/data/xml/working-with-xml-schemas.md)
