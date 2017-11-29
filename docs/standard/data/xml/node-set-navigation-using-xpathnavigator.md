---
title: "Węzeł nawigacji zestawu użyciu klasy XPathNavigator"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1a954b41-7173-40bc-8544-d430f209b1e5
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9ac0135227599d6a72813bcf57b209705545da66
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="node-set-navigation-using-xpathnavigator"></a>Węzeł nawigacji zestawu użyciu klasy XPathNavigator
Można nawigować przez węzły w <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> obiekt przy użyciu zestawu węzłów nawigacji metody <xref:System.Xml.XPath.XPathNavigator> klasy. Można przejść na wszystkich węzłach lub wybrany zestaw zwrócony przez jedną z metod wybór węzłów <xref:System.Xml.XPath.XPathNavigator> klasy.  
  
## <a name="element-node-set-navigation"></a>Element węzła zestawu nawigacji  
 <xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia kilka metod służące do nawigacji węzłów elementów. W poniższej tabeli przedstawiono dostępne metody nawigacji oraz opis przenoszeniem; nie ma metody używane do przechodzenia węzłów atrybutu i przestrzeni nazw.  
  
 Aby uzyskać więcej informacji o wybieraniu węzłów w <xref:System.Xml.XPath.XPathNavigator> obiektów, zobacz [wybranie opcji, Evaluating i dopasowywania danych XML przy użyciu Element XPathNavigator](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md). Aby uzyskać więcej informacji na temat Nawigacja węzłów atrybutu i przestrzeni nazw, zobacz [atrybut i element Namespace węzła nawigacji przy użyciu XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md).  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>|Przenosi <xref:System.Xml.XPath.XPathNavigator> do tej samej pozycji <xref:System.Xml.XPath.XPathNavigator> określony.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>|Przenosi <xref:System.Xml.XPath.XPathNavigator> do elementem podrzędnym bieżącego węzła.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>|Przenosi <xref:System.Xml.XPath.XPathNavigator> pierwszy węzeł równorzędny bieżącego węzła.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>|Przenosi <xref:System.Xml.XPath.XPathNavigator> do pierwszego podrzędnym bieżącego węzła.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>|Przenosi <xref:System.Xml.XPath.XPathNavigator> do określonego elementu w kolejności dokumentu.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>|Przenosi <xref:System.Xml.XPath.XPathNavigator> do węzła, który ma atrybut typu `ID` z wartością, która odpowiada danym <xref:System.String>.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>|Przenosi <xref:System.Xml.XPath.XPathNavigator> do następnego węzła tego samego poziomu bieżącego węzła.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>|Przenosi <xref:System.Xml.XPath.XPathNavigator> do węzła nadrzędnego bieżącego węzła.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>|Przenosi <xref:System.Xml.XPath.XPathNavigator> do poprzedniego węzła tego samego poziomu bieżącego węzła.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A>|Przenosi <xref:System.Xml.XPath.XPathNavigator> do węzła głównego dokumentu XML.|  
  
## <a name="comments-and-processing-instruction-node-navigation"></a>Komentarze i przetwarzania instrukcji węzła nawigacji  
 Następujące <xref:System.Xml.XPath.XPathNavigator> metod klasy są prawidłowe w przypadku przenoszenia do komentarzy lub przetwarzania instrukcji inne węzły w dokumencie XML.  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [Przetwarzania danych XML przy użyciu modelu danych XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [Atrybut i Namespace węzła nawigacji użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)  
 [Wyodrębnianie danych XML przy użyciu parametrem XPathNavigator](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)  
 [Uzyskiwanie dostępu do silnie typu danych XML przy użyciu parametrem XPathNavigator](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
