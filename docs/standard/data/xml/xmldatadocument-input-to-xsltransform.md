---
title: Dane wejściowe obiektu XmlDataDocument klasy XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a0b536b6-cdb3-4a44-86c2-3b2ebc7bd4c9
ms.openlocfilehash: 01c6ba8b14f8de167892ee9eeaff615f1f9ca37d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290269"
---
# <a name="xmldatadocument-input-to-xsltransform"></a>Dane wejściowe obiektu XmlDataDocument klasy XslTransform
> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform>Klasa jest przestarzała w .NET Framework 2,0. Można wykonać przekształcenia Extensible Stylesheet Language for Transformations (XSLT) przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy. Aby uzyskać więcej informacji, zobacz [Używanie klasy XslCompiledTransform](using-the-xslcompiledtransform-class.md) i [Migrowanie z klasy XslTransform](migrating-from-the-xsltransform-class.md) .  
  
 Microsoft .NET Framework implementuje Document Object Model XML (DOM), aby zapewnić dostęp do danych w dokumentach XML i dodatkowych klasach do odczytu, zapisu i nawigowania w dokumentach XML. <xref:System.Xml.XmlDataDocument>Program, który znajduje się w <xref:System.Xml> przestrzeni nazw, zapewnia relacyjny dostęp do danych z możliwością synchronizowania z danymi relacyjnymi w <xref:System.Data.DataSet> . Możesz jednocześnie wyświetlać strukturalny kod XML i manipulować nim za pomocą relacyjnej reprezentacji <xref:System.Data.DataSet> lub manipulować częściowo strukturalnym kodem XML za pomocą reprezentacji modelu dom <xref:System.Xml.XmlDataDocument> . W <xref:System.Xml.XmlDataDocument> związku z tym przecina granice XML i relacyjne światy.  
  
 Jeśli dane są przechowywane w strukturze relacyjnej i chcesz, aby były wprowadzane do transformacji XSLT, można załadować dane relacyjne do <xref:System.Data.DataSet> i skojarzyć je z <xref:System.Xml.XmlDataDocument> . <xref:System.Xml.XPath.XPathNavigator>, Dane wejściowe do <xref:System.Xml.Xsl.XslTransform> , są implementowane <xref:System.Xml.XmlDataDocument> przez <xref:System.Xml.XPath.IXPathNavigable> interfejs. Pobierając dane relacyjne, ładując je do <xref:System.Data.DataSet> i korzystając z synchronizacji w ramach <xref:System.Xml.XmlDataDocument> , dane relacyjne mogą teraz mieć przekształcenia XSLT wykonywane na nim.  
  
 Aby uzyskać więcej informacji na temat stosowania transformacji do danych relacyjnych, zobacz [stosowanie transformacji XSLT do zestawu danych](../../../framework/data/adonet/dataset-datatable-dataview/applying-an-xslt-transform-to-a-dataset.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.XmlDataDocument>
- [Synchronizacja elementów DataSet i XmlDataDocument](../../../framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md)
- [Przekształcenia XSLT przy użyciu klasy XslTransform](xslt-transformations-with-the-xsltransform-class.md)
- [Implementowanie procesora XSLT przy użyciu klasy XslTransform](xsltransform-class-implements-the-xslt-processor.md)
- [Klasa XPathNavigator w przekształceniach](xpathnavigator-in-transformations.md)
- [Klasa XPathNodeIterator w przekształceniach](xpathnodeiterator-in-transformations.md)
- [Dane wejściowe obiektu XPathDocument klasy XslTransform](xpathdocument-input-to-xsltransform.md)
- [Dane wejściowe obiektu XmlDocument klasy XslTransform](xmldocument-input-to-xsltransform.md)
