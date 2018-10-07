---
title: Dane wejściowe obiektu XmlDataDocument klasy xsltransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a0b536b6-cdb3-4a44-86c2-3b2ebc7bd4c9
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e7fb30104f36a565f4e6742c8f808c48e4ef39ec
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2018
ms.locfileid: "48842557"
---
# <a name="xmldatadocument-input-to-xsltransform"></a>Dane wejściowe obiektu XmlDataDocument klasy xsltransform
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Klasy jest przestarzała w [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Można przeprowadzić rozszerzalny język arkusza stylów dla przekształceń przekształcenia (XSLT) przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy. Zobacz [używanie klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) i [Migrowanie z klasy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Aby uzyskać więcej informacji.  
  
 Microsoft [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] implementuje Model obiektu dokumentu (DOM) XML, aby zapewnić dostęp do danych w dokumentach XML i dodatkowych klas do odczytu, zapisu i nawigacja w dokumentach XML. <xref:System.Xml.XmlDataDocument>Znajdujące się w <xref:System.Xml> przestrzeni nazw, zapewnia możliwość zsynchronizować z danymi relacyjnymi w relacyjnych dostęp do danych <xref:System.Data.DataSet>. Jednocześnie można wyświetlać i manipulowania XML ze strukturą za pośrednictwem relacyjnych reprezentacja <xref:System.Data.DataSet> i umożliwiają manipulowanie XML lub częściową strukturą, za pośrednictwem modelu DOM reprezentacja <xref:System.Xml.XmlDataDocument>. <xref:System.Xml.XmlDataDocument> w związku z tym przekracza granice XML i relacyjnych podejść.  
  
 Jeśli dane są przechowywane w strukturze relacyjnej, ma być użyty jako wejście do transformacji XSLT można załadować danych relacyjnych w <xref:System.Data.DataSet> i powiąż ją z <xref:System.Xml.XmlDataDocument>. <xref:System.Xml.XPath.XPathNavigator>, Dane wejściowe <xref:System.Xml.Xsl.XslTransform>, jest wdrażana w <xref:System.Xml.XmlDataDocument> za pośrednictwem <xref:System.Xml.XPath.IXPathNavigable> interfejsu. Wykonując opartego na danych relacyjnych, załadowanie go do <xref:System.Data.DataSet>i za pomocą synchronizacji w ramach <xref:System.Xml.XmlDataDocument>, dane relacyjne mogą teraz zawierać przekształcenia XSLT na nich wykonane.  
  
 Aby uzyskać więcej informacji na temat stosowania transformacji na dane relacyjne zobacz [stosowanie przekształcenia XSLT do zestawu danych](../../../../docs/framework/data/adonet/dataset-datatable-dataview/applying-an-xslt-transform-to-a-dataset.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.XmlDataDocument>  
- [Synchronizacja elementów DataSet i XmlDataDocument](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md)  
- [Przekształcenia XSLT przy użyciu klasy XslTransform](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
- [Implementowanie procesora XSLT przy użyciu klasy XslTransform](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)  
- [Klasa XPathNavigator w przekształceniach](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)  
- [Klasa XPathNodeIterator w przekształceniach](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)  
- [Dane wejściowe obiektu XPathDocument klasy XslTransform](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)  
- [Dane wejściowe obiektu XmlDocument klasy XslTransform](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
