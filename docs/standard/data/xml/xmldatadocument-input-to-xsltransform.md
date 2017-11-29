---
title: "Dane wejściowe dokumentu XmlDataDocument XslTransform"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a0b536b6-cdb3-4a44-86c2-3b2ebc7bd4c9
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 813c240ca0115015158988e1226d25890cde6939
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="xmldatadocument-input-to-xsltransform"></a>Dane wejściowe dokumentu XmlDataDocument XslTransform
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Klasa jest przestarzała w [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Może wykonywać rozszerzalny język arkusza stylów dla transformacji przekształcenia XSLT () przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy. Zobacz [za pomocą klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) i [migracji z klasy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Aby uzyskać więcej informacji.  
  
 Microsoft [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] implementuje XML modelu DOM (Document Object) umożliwia dostęp do danych w dokumentach XML i dodatkowych klas do odczytu, zapisu i przejdź w dokumentach XML. <xref:System.Xml.XmlDataDocument>, Liczba znalezionych w <xref:System.Xml> przestrzeni nazw, zapewnia możliwość synchronizacji z danych relacyjnych w relacyjnych dostęp do danych <xref:System.Data.DataSet>. Jednocześnie można wyświetlać i manipulowania strukturalnych XML za pomocą relacyjne reprezentację <xref:System.Data.DataSet> lub modyfikowania częściowo ustrukturyzowanych XML za pomocą modelu DOM reprezentację <xref:System.Xml.XmlDataDocument>. <xref:System.Xml.XmlDataDocument> w związku z tym przecina granice XML i względem relacyjne.  
  
 Jeśli dane są przechowywane w strukturze relacyjnych i ma to być dane wejściowe transformację XSLT, można załadować danych relacyjnych do <xref:System.Data.DataSet> i skojarz ją z <xref:System.Xml.XmlDataDocument>. <xref:System.Xml.XPath.XPathNavigator>, Dane wejściowe <xref:System.Xml.Xsl.XslTransform>, jest wdrażana w <xref:System.Xml.XmlDataDocument> za pośrednictwem <xref:System.Xml.XPath.IXPathNavigable> interfejsu. Wykonując danych relacyjnych załadowanie go do <xref:System.Data.DataSet>i przy użyciu synchronizacji w <xref:System.Xml.XmlDataDocument>, danych relacyjnych można już wykonywać na nim przekształcenia XSLT.  
  
 Aby uzyskać więcej informacji na temat stosowania przekształcenia do danych relacyjnych, zobacz [stosowania przekształcenie XSLT do zestawu danych](../../../../docs/framework/data/adonet/dataset-datatable-dataview/applying-an-xslt-transform-to-a-dataset.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.XmlDataDocument>  
 [Zestaw danych i dokumentu XmlDataDocument synchronizacji](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md)  
 [Przekształcenia XSLT przy użyciu klasy XslTransform](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 [Klasa XslTransform implementuje procesorze XSLT](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)  
 [Element XPathNavigator w przekształcenia](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)  
 [Element XPathNodeIterator w przekształcenia](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)  
 [Dane wejściowe XPathDocument XslTransform](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)  
 [Dane wejściowe XmlDocument XslTransform](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
