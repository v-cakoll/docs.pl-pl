---
title: Dane wejściowe obiektu XmlDataDocument klasy XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a0b536b6-cdb3-4a44-86c2-3b2ebc7bd4c9
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a5c2fb203a1a6975d2b30e47528b15a9005a2583
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916024"
---
# <a name="xmldatadocument-input-to-xsltransform"></a>Dane wejściowe obiektu XmlDataDocument klasy XslTransform
> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform> Klasa jest przestarzała w .NET Framework 2,0. Można wykonać przekształcenia Extensible Stylesheet Language for Transformations (XSLT) przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy. Aby uzyskać więcej informacji, zobacz [Używanie klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) i [Migrowanie z klasy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) .  
  
 Microsoft .NET Framework implementuje Document Object Model XML (DOM), aby zapewnić dostęp do danych w dokumentach XML i dodatkowych klasach do odczytu, zapisu i nawigowania w dokumentach XML. Program, który znajduje <xref:System.Xml> się w przestrzeni nazw, zapewnia relacyjny dostęp do danych z możliwością synchronizowania z danymi relacyjnymi w <xref:System.Data.DataSet>. <xref:System.Xml.XmlDataDocument> Możesz jednocześnie wyświetlać strukturalny kod XML i manipulować nim za pomocą relacyjnej <xref:System.Data.DataSet> reprezentacji lub manipulować częściowo strukturalnym kodem XML za pomocą reprezentacji <xref:System.Xml.XmlDataDocument>modelu DOM. W <xref:System.Xml.XmlDataDocument> związku z tym przecina granice XML i relacyjne światy.  
  
 Jeśli dane są przechowywane w strukturze relacyjnej i chcesz, aby były wprowadzane do transformacji XSLT, można załadować dane relacyjne do <xref:System.Data.DataSet> i skojarzyć je <xref:System.Xml.XmlDataDocument>z. , Dane wejściowe <xref:System.Xml.Xsl.XslTransform>do <xref:System.Xml.XmlDataDocument> , są<xref:System.Xml.XPath.IXPathNavigable> implementowane przez interfejs. <xref:System.Xml.XPath.XPathNavigator> Pobierając dane relacyjne, ładując je do <xref:System.Data.DataSet>i korzystając z synchronizacji <xref:System.Xml.XmlDataDocument>w ramach, dane relacyjne mogą teraz mieć przekształcenia XSLT wykonywane na nim.  
  
 Aby uzyskać więcej informacji na temat stosowania transformacji do danych relacyjnych, zobacz [stosowanie transformacji XSLT do zestawu danych](../../../../docs/framework/data/adonet/dataset-datatable-dataview/applying-an-xslt-transform-to-a-dataset.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.XmlDataDocument>
- [Synchronizacja elementów DataSet i XmlDataDocument](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md)
- [Przekształcenia XSLT przy użyciu klasy XslTransform](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)
- [Implementowanie procesora XSLT przy użyciu klasy XslTransform](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
- [Klasa XPathNavigator w przekształceniach](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)
- [Klasa XPathNodeIterator w przekształceniach](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)
- [Dane wejściowe obiektu XPathDocument klasy XslTransform](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)
- [Dane wejściowe obiektu XmlDocument klasy XslTransform](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
