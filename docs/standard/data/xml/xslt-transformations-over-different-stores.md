---
title: "Przekształcenia XSLT w sklepach"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 369850e9-004a-45d2-b5c3-5060d9135adb
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b909b754c1d0d3007e06cd04376413d02cbc2f76
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="xslt-transformations-over-different-stores"></a>Przekształcenia XSLT w sklepach
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Klasa jest przestarzała w [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Może wykonywać rozszerzalny język arkusza stylów dla transformacji przekształcenia XSLT () przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy. Zobacz [za pomocą klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) i [migracji z klasy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Aby uzyskać więcej informacji.  
  
 ADO.NET i XML klas w [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zapewnienia ujednoliconego modelu programowania uzyskują dostęp do danych. Te dane jest reprezentowany jako danych XML, który jest wartością tekstową rozdzielonych według znaczników, i danych relacyjnych, czyli tabele składające się z wierszy i kolumn. Kod XML w [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] odczytuje dane XML z jakimkolwiek strumieniu danych do drzewa węzła XML modelu DOM (Document Object), w których danych można uzyskać programistycznie, gdy ADO.NET udostępnia środki do uzyskiwania dostępu i manipulowania relacyjnej bazie danych w ramach <xref:System.Data.DataSet> obiektu.  
  
 W modelu DOM XML zapewnia dostęp do danych w dokumentach XML i dodatkowych klas do odczytu, zapisu i przejdź w dokumentach XML. Te klasy są obsługiwane w <xref:System.Xml> przestrzeni nazw, które również łączy w modelu DOM XML z usługi dostępu do danych, które są udostępniane przez ADO.NET. <xref:System.Xml.XmlDataDocument> Zapewnia relacyjne dostęp do danych. <xref:System.Xml.XmlDataDocument> Mapy XML do danych relacyjnych w ADO.NET <xref:System.Data.DataSet>. Wszelkie [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]-aplikacji można używać klas w <xref:System.Xml> przestrzeni nazw do uzyskania dostępu i manipulowania zarówno dokumentów XML i danych relacyjnych w <xref:System.Xml.XmlDataDocument>. Ta implementacja obsługuje wielowarstwowej architektury zbierania i dystrybucji danych. Aby uzyskać więcej informacji, zobacz [XML integracji z danych relacyjnych i ADO.NET](../../../../docs/standard/data/xml/xml-integration-with-relational-data-and-adonet.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa XslTransform implementuje procesorze XSLT](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
