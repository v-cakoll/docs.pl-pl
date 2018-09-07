---
title: Nawigacja po zestawie węzłów przy użyciu klasy XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1a954b41-7173-40bc-8544-d430f209b1e5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f062f7fd58efe6c350b3a119ec3bdd4d27b896db
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44086369"
---
# <a name="node-set-navigation-using-xpathnavigator"></a>Nawigacja po zestawie węzłów przy użyciu klasy XPathNavigator
Możesz nawigować przez węzły w <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> obiektu przy użyciu metody nawigacji ustaw węzeł <xref:System.Xml.XPath.XPathNavigator> klasy. Możesz przejść za pośrednictwem wszystkich węzłów lub wybrany zestaw węzłów zwrócony przez jedną z metod wybór <xref:System.Xml.XPath.XPathNavigator> klasy.  
  
## <a name="element-node-set-navigation"></a>Nawigacja po zestawie węzłów — element  
 <xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia kilka metod, używany do przechodzenia węzłów elementów. W poniższej tabeli przedstawiono dostępne metody nawigacji i opis przenoszeniem; nie ma metody służące do nawigacji węzłów atrybutu i przestrzeni nazw.  
  
 Aby uzyskać więcej informacji na temat wybierania węzły w <xref:System.Xml.XPath.XPathNavigator> obiektu, zobacz [Wybieranie, Obliczanie i dopasowywanie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md). Aby uzyskać więcej informacji na temat Nawigacja węzłów atrybutu i przestrzeni nazw, zobacz [atrybut i klasy Namespace węzła nawigacji za pomocą XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md).  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>|Przenosi <xref:System.Xml.XPath.XPathNavigator> do tej samej pozycji <xref:System.Xml.XPath.XPathNavigator> określony.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>|Przenosi <xref:System.Xml.XPath.XPathNavigator> do węzła podrzędnego bieżącego węzła.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>|Przenosi <xref:System.Xml.XPath.XPathNavigator> do pierwszego węzła równorzędnego bieżącego węzła.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>|Przenosi <xref:System.Xml.XPath.XPathNavigator> do pierwszego węzła podrzędnego bieżącego węzła.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>|Przenosi <xref:System.Xml.XPath.XPathNavigator> do określonego elementu w kolejności dokumentu.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>|Przenosi <xref:System.Xml.XPath.XPathNavigator> do węzła, który ma atrybut typu `ID` z wartością, która odpowiada danym <xref:System.String>.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>|Przenosi <xref:System.Xml.XPath.XPathNavigator> do kolejnego węzła równorzędnego bieżącego węzła.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>|Przenosi <xref:System.Xml.XPath.XPathNavigator> do węzła nadrzędnego bieżącego węzła.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>|Przenosi <xref:System.Xml.XPath.XPathNavigator> do poprzedniego węzła równorzędnego bieżącego węzła.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A>|Przenosi <xref:System.Xml.XPath.XPathNavigator> do węzła głównego dokumentu XML.|  
  
## <a name="comments-and-processing-instruction-node-navigation"></a>Komentarze i nawigacja węzłów instrukcji przetwarzania  
 Następujące <xref:System.Xml.XPath.XPathNavigator> metod klasy są prawidłowe w przypadku przenoszenia do komentarze lub przetwarzania instrukcji z innych węzłów w dokumencie XML.  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.XmlDocument>  
- <xref:System.Xml.XPath.XPathDocument>  
- <xref:System.Xml.XPath.XPathNavigator>  
- [Przetwarzanie danych XML przy użyciu modelu danych XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
- [Nawigacja po atrybutach i przestrzeni nazw węzła przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)  
- [Wyodrębnianie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)  
- [Uzyskiwanie dostępu do silnie typizowanych danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
