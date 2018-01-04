---
title: "Atrybut i Namespace węzła nawigacji użyciu klasy XPathNavigator"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 23975f88-e0af-4b88-93de-9e20e11880ad
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2f86abb7da5509a80cceede0f1092a75cef4d8da
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="attribute-and-namespace-node-navigation-using-xpathnavigator"></a>Atrybut i Namespace węzła nawigacji użyciu klasy XPathNavigator
<xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia dwa zestawy metod nawigacji, pierwszy zestaw znaleziony w [węzła ustawić nawigacji przy użyciu Element XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md) tematu, są używane do przechodzenia *zestaw węzłów* w <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> obiektu. Drugi zestaw opisanych w tym temacie służą do nawigacji *węzłów atrybutu i przestrzeni nazw* w <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> obiektu.  
  
## <a name="attribute-node-navigation"></a>Atrybut węzła nawigacji  
 Atrybuty są właściwości elementu nie elementów podrzędnych elementu. Ta różnica jest istotna, z powodu metody <xref:System.Xml.XPath.XPathNavigator> klasy służące do tego samego poziomu, nadrzędnych i podrzędnych węzłów nawigacji.  
  
 Na przykład <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> i <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> metod nie są używane do nawigacji z elementu, atrybutu lub między atrybutami. Zamiast tego atrybuty mają różne metody nawigacji.  
  
 Poniżej przedstawiono atrybutu metody nawigacji <xref:System.Xml.XPath.XPathNavigator> klasy.  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToAttribute%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToFirstAttribute%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToNextAttribute%2A>  
  
 Jeśli bieżący węzeł jest elementem, możesz użyć <xref:System.Xml.XPath.XPathNavigator.HasAttributes%2A> właściwość w celu sprawdzenia, czy istnieją jakiekolwiek atrybuty skojarzone z elementem. Po wiadomo, że element ma atrybuty, istnieje wiele metod dostępu do atrybutów. Aby uzyskać jeden atrybut z elementu, użyj <xref:System.Xml.XPath.XPathNavigator.GetAttribute%2A> metody. Aby przenieść <xref:System.Xml.XPath.XPathNavigator> do określonego atrybutu, użyj <xref:System.Xml.XPath.XPathNavigator.MoveToAttribute%2A> metody. Można również iteracja każdego atrybutu elementu za pomocą <xref:System.Xml.XPath.XPathNavigator.MoveToFirstAttribute%2A> metody następuje wiele wywołań <xref:System.Xml.XPath.XPathNavigator.MoveToNextAttribute%2A> metody.  
  
> [!NOTE]
>  Gdy <xref:System.Xml.XPath.XPathNavigator> obiekt znajduje się w węźle atrybutu lub przestrzeni nazw <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> i <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> metody zawsze zwracają `false`, i nie mają wpływu na pozycję <xref:System.Xml.XPath.XPathNavigator>. Wyjątki są <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>, i <xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A> metody.  
  
## <a name="namespace-node-navigation"></a>Namespace węzła nawigacji  
 Każdy element ma związany jest zestaw węzłów przestrzeni nazw, po jednej dla każdego prefiks unikatowych nazw, który jest powiązany z identyfikatora URI w zakresie elementu przestrzeni nazw (łącznie z prefiksem XML powiązany z `http://www.w3.org/XML/1998/namespace` przestrzeni nazw jest niejawnie zadeklarowany w każdy dokument XML) i jedno dla domyślnej przestrzeni nazw, jeśli jest w zakresie dla elementu. Element jest elementem nadrzędnym każdego z tych węzłów nazw; jednak węzła obszaru nazw nie jest elementem podrzędnym odpowiedniego elementu nadrzędnego.  
  
 Podobnie jak w przypadku atrybutów, <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> i <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> metod nie są używane do przechodzenia między element do węzła przestrzeni nazw lub między węzłami przestrzeni nazw. Zamiast tego obszaru nazw węzły mają różne metody nawigacji.  
  
 Poniżej przedstawiono przestrzeń nazw metody nawigacji <xref:System.Xml.XPath.XPathNavigator> klasy.  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToNamespace%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A>  
  
 Istnieje co najmniej jeden węzeł przestrzeni nazw w zakresie dla każdego elementu w dokumencie XML. To jest węzeł przestrzeni nazw z prefiksem `xml` i identyfikator URI przestrzeni nazw `http://www.w3.org/XML/1998/namespace`. Aby uzyskać identyfikator URI w zakresie danego danego prefiksu przestrzeni nazw, użyj <xref:System.Xml.XPath.XPathNavigator.GetNamespace%2A> metody. Aby przenieść <xref:System.Xml.XPath.XPathNavigator> obiekt do węzła określonego obszaru nazw, użyj <xref:System.Xml.XPath.XPathNavigator.MoveToNamespace%2A> metody. Można również iteracja każdy węzeł przestrzeni nazw w zakresie elementu za pomocą <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> metody następuje wiele wywołań <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> metody.  
  
> [!NOTE]
>  Gdy <xref:System.Xml.XPath.XPathNavigator> obiekt znajduje się w węźle atrybutu lub przestrzeni nazw <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> i <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> metody zawsze zwracają `false`, i nie mają wpływu na pozycję <xref:System.Xml.XPath.XPathNavigator>. Wyjątki są <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>, i <xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A> metody.  
  
### <a name="the-xpathnamespacescope-enumeration"></a>Wyliczenie XPathNamespaceScope  
 Podczas nawigowania węzłów przestrzeni nazw <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> i <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> można wywołać metody <xref:System.Xml.XPath.XPathNamespaceScope> parametru. Te metody zachowywać się inaczej, niż ich odpowiedniki wywoływana bez parametrów. <xref:System.Xml.XPath.XPathNamespaceScope> Wyliczenie ma wartości <xref:System.Xml.XPath.XPathNamespaceScope.All>, <xref:System.Xml.XPath.XPathNamespaceScope.ExcludeXml>, lub <xref:System.Xml.XPath.XPathNamespaceScope.Local>.  
  
 W poniższych przykładach pokazano, co przestrzenie nazw są zwracane przez <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> i <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> metody w różnych zakresów w dokumentach XML.  
  
```xml  
<root>  
    <element1 xmlns="http://www.contoso.com" xmlns:books="http://www.contoso.com/books">  
        <element2 />  
    </element1>  
</root>  
```  
  
 Sekwencja przestrzeni nazw (przestrzeni nazw <xref:System.Xml.XPath.XPathNavigator> znajduje się na po wywołaniu <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> metody następuje szereg wywołań <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> — metoda) ma następującą składnię.  
  
-   Ustawiony na `element2`: `xmlns:books="http://www.contoso.com/books"`, `xmlns="http://www.contoso.com"`, i `xmlns:xml="http://www.w3.org/XML/1998/namespace"`.  
  
-   Ustawiony na `element1`: `xmlns:books="http://www.contoso.com/books"`, `xmlns="http://www.contoso.com"`, i `xmlns:xml="http://www.w3.org/XML/1998/namespace"`.  
  
-   Ustawiony na `root`:`xmlns:xml="http://www.w3.org/XML/1998/namespace".`  
  
> [!NOTE]
>  <xref:System.Xml.XPath.XPathNavigator> Klasa zwraca węzłów przestrzeni nazw w kolejności odwrotnej dokumentu. W związku z tym <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> zasadniczo przenosi do ostatniego węzła przestrzeni nazw w bieżącym zakresie.  
  
 W poniższych przykładach pokazano, co przestrzenie nazw są zwracane przez <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> i <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> metod <xref:System.Xml.XPath.XPathNamespaceScope> wyliczenie określona w różnych zakresów w dokumentach XML.  
  
```xml  
<root xmlns="http://www.contoso.com" xmlns:a="http://www.contoso.com/a" xmlns:b="http://www.contoso.com/b">  
    <child1 xmlns="" xmlns:a="urn:a">  
        <child2 xmlns:c="urn:c" />  
    </child1>  
</root>  
```  
  
 Ustawiony na `child2`, sekwencji przestrzeni nazw (przestrzeń nazw <xref:System.Xml.XPath.XPathNavigator> znajduje się na po wywołaniu <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> metody następuje szereg wywołań <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> — metoda) ma następującą składnię.  
  
-   <xref:System.Xml.XPath.XPathNamespaceScope.All>: `xmlns:c="urn:c"`, `xmlns:a="urn:a"`, `xmlns=""`, `xmlns:b="http://www.contoso.com/b"`, `xmlns:a="http://www.contoso.com/a"`, `xmlns="http://www.contoso.com"`, i `xmlns:xml="http://www.w3.org/XML/1998/namespace"`.  
  
-   <xref:System.Xml.XPath.XPathNamespaceScope.ExcludeXml>: `xmlns:c="urn:c"`, `xmlns:a="urn:a"`, `xmlns=""`, `xmlns:b="http://www.contoso.com/b"`, `xmlns:a="http://www.contoso.com/a"`, i `xmlns="http://www.contoso.com"`.  
  
-   <xref:System.Xml.XPath.XPathNamespaceScope.Local>: `xmlns:c="urn:c"`.  
  
> [!NOTE]
>  <xref:System.Xml.XPath.XPathNavigator> Klasa zwraca węzłów przestrzeni nazw w kolejności odwrotnej dokumentu. W związku z tym <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> zasadniczo przenosi do ostatniego węzła przestrzeni nazw w bieżącym zakresie.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [Przetwarzanie danych XML przy użyciu modelu danych XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [Nawigacja po zestawie węzłów przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)  
 [Wyodrębnianie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)  
 [Uzyskiwanie dostępu do silnie typizowanych danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
