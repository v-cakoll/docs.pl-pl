---
title: Nawigacja po zestawie węzłów przy użyciu klasy XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1a954b41-7173-40bc-8544-d430f209b1e5
ms.openlocfilehash: 91115af03b635d7660721fac5ce8bd749953e4ff
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710573"
---
# <a name="node-set-navigation-using-xpathnavigator"></a>Nawigacja po zestawie węzłów przy użyciu klasy XPathNavigator
Można przechodzić między węzłami w <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> obiektu przy użyciu metod nawigacji zestawu węzłów klasy <xref:System.Xml.XPath.XPathNavigator>. Można poruszać się we wszystkich węzłach lub na wybranym zestawie węzłów zwróconym przez jedną z metod wyboru klasy <xref:System.Xml.XPath.XPathNavigator>.  
  
## <a name="element-node-set-navigation"></a>Nawigacja zestawu węzłów elementu  
 Klasa <xref:System.Xml.XPath.XPathNavigator> udostępnia kilka metod służących do nawigowania po węzłach elementów. W poniższej tabeli przedstawiono dostępne metody nawigacji oraz opis sposobu ich przenoszenia; nie obejmuje to metod służących do nawigowania po węzłach atrybutów i przestrzeni nazw.  
  
 Aby uzyskać więcej informacji na temat wybierania węzłów w obiekcie <xref:System.Xml.XPath.XPathNavigator>, zobacz [Wybieranie, ocenianie i dopasowywanie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md). Aby uzyskać więcej informacji na temat nawigowania po węzłach atrybutów i przestrzeni nazw, zobacz [nawigowanie po węźle atrybutów i przestrzeni nazw za pomocą elementu XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md).  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>|Przenosi <xref:System.Xml.XPath.XPathNavigator> do tej samej pozycji podanej <xref:System.Xml.XPath.XPathNavigator>.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>|Przenosi <xref:System.Xml.XPath.XPathNavigator> do węzła podrzędnego bieżącego węzła.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>|Przenosi <xref:System.Xml.XPath.XPathNavigator> do pierwszego węzła równorzędnego bieżącego węzła.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>|Przenosi <xref:System.Xml.XPath.XPathNavigator> do pierwszego węzła podrzędnego bieżącego węzła.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>|Przenosi <xref:System.Xml.XPath.XPathNavigator> do określonego elementu w kolejności dokumentu.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>|Przenosi <xref:System.Xml.XPath.XPathNavigator> do węzła, który ma atrybut typu `ID` z wartością zgodną z danym <xref:System.String>.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>|Przenosi <xref:System.Xml.XPath.XPathNavigator> do następnego węzła równorzędnego bieżącego węzła.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>|Przenosi <xref:System.Xml.XPath.XPathNavigator> do węzła nadrzędnego bieżącego węzła.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>|Przenosi <xref:System.Xml.XPath.XPathNavigator> do poprzedniego węzła równorzędnego bieżącego węzła.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A>|Przenosi <xref:System.Xml.XPath.XPathNavigator> do węzła głównego dokumentu XML.|  
  
## <a name="comments-and-processing-instruction-node-navigation"></a>Nawigacja w węźle instrukcji Comments i Processing  
 Następujące metody klasy <xref:System.Xml.XPath.XPathNavigator> są prawidłowe do przechodzenia do komentarzy lub przetwarzania instrukcji z innych węzłów w dokumencie XML.  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Przetwarzanie danych XML przy użyciu modelu danych XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Nawigacja po atrybutach i przestrzeni nazw węzła przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)
- [Wyodrębnianie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)
- [Uzyskiwanie dostępu do silnie typizowanych danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
