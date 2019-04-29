---
title: Nawigacja po atrybutach i przestrzeni nazw węzła przy użyciu klasy XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 23975f88-e0af-4b88-93de-9e20e11880ad
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fd3b1cacc73743622aaaad72bfd4edb26dc26390
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61670069"
---
# <a name="attribute-and-namespace-node-navigation-using-xpathnavigator"></a>Nawigacja po atrybutach i przestrzeni nazw węzła przy użyciu klasy XPathNavigator
<xref:System.Xml.XPath.XPathNavigator> Klasa oferuje dwa rodzaje metod nawigowania, pierwszy zestaw znaleziony w [węzła zestawu nawigacji przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md) tematu, są używane do nawigacji *zestaw węzłów* w <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> obiektu. Drugi zestaw, opisane w tym temacie służą do nawigacji *węzłów atrybutu i przestrzeni nazw* w <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> obiektu.  
  
## <a name="attribute-node-navigation"></a>Nawigacja węzłów atrybutu  
 Atrybuty to właściwości elementu, nie elementów podrzędnych elementu. Ta różnica jest ważna, ze względu na metody <xref:System.Xml.XPath.XPathNavigator> klasy służące do nawigacji węzłów równorzędnych, nadrzędnych i podrzędnych.  
  
 Na przykład <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> i <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> metod nie są używane do nawigacji z elementu, atrybutu lub między atrybutami. Zamiast tego atrybuty mają różne metody nawigacji.  
  
 Poniżej przedstawiono atrybut metody nawigacji <xref:System.Xml.XPath.XPathNavigator> klasy.  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToAttribute%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToFirstAttribute%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToNextAttribute%2A>  
  
 Jeśli bieżący węzeł jest elementem, możesz użyć <xref:System.Xml.XPath.XPathNavigator.HasAttributes%2A> właściwości, aby zobaczyć, czy istnieją jakiekolwiek atrybuty skojarzone z elementem. Po wiadomo, że element ma atrybuty, istnieje kilka metod uzyskania dostępu do atrybutów. Aby pobrać jeden atrybut z elementu, użyj <xref:System.Xml.XPath.XPathNavigator.GetAttribute%2A> metody. Aby przenieść <xref:System.Xml.XPath.XPathNavigator> do określonego atrybutu, należy użyć <xref:System.Xml.XPath.XPathNavigator.MoveToAttribute%2A> metody. Można również wykonać iterację przez każdego atrybutu element przy użyciu <xref:System.Xml.XPath.XPathNavigator.MoveToFirstAttribute%2A> metody następuje wielu wywołań <xref:System.Xml.XPath.XPathNavigator.MoveToNextAttribute%2A> metody.  
  
> [!NOTE]
>  Gdy <xref:System.Xml.XPath.XPathNavigator> obiektu jest ustawiony na węzeł atrybutu lub nazw <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> i <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> metody zawsze zwracają `false`, i nie mają wpływu na pozycję <xref:System.Xml.XPath.XPathNavigator>. Wyjątki są <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>, i <xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A> metody.  
  
## <a name="namespace-node-navigation"></a>Nawigacja węzłów Namespace  
 Każdy element ma skojarzony zestaw przestrzeni nazw węzłów, jednej dla każdego prefiksu unikatowych nazw, który jest powiązany z przestrzeni nazw URI w zakresie elementu (łącznie z prefiksem XML powiązany z `http://www.w3.org/XML/1998/namespace` przestrzeń nazw, która została niejawnie zadeklarowana w każdym dokumencie XML) i jeden dla domyślny obszar nazw, jeśli znajduje się w zakresie dla elementu. Element jest elementem nadrzędnym każdego z tych węzłów nazw; jednak węzła obszaru nazw nie jest elementem podrzędnym odpowiedniego elementu nadrzędnego.  
  
 Podobnie jak w przypadku atrybutów, <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> i <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> metod nie są używane do nawigacji z elementu do węzła obszaru nazw lub między węzły przestrzeni nazw. Zamiast tego węzły przestrzeni nazw mają różne metody nawigacji.  
  
 Poniżej przedstawiono przestrzeń nazw metody nawigacji <xref:System.Xml.XPath.XPathNavigator> klasy.  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToNamespace%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A>  
  
 Istnieje co najmniej jeden węzeł przestrzeni nazw w zakresie dla każdego elementu w dokumencie XML. Jest to węzeł przestrzeni nazw z prefiksem `xml` i identyfikator URI przestrzeni nazw `http://www.w3.org/XML/1998/namespace`. Aby pobrać identyfikator URI w zakresie, w szczególności prefiks przestrzeni nazw, należy użyć <xref:System.Xml.XPath.XPathNavigator.GetNamespace%2A> metody. Aby przenieść <xref:System.Xml.XPath.XPathNavigator> obiektu użycia określonej przestrzeni nazw węzła <xref:System.Xml.XPath.XPathNavigator.MoveToNamespace%2A> metody. Można również iteracja każdego węzła obszaru nazw, w zakresie dla elementu za pomocą <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> metody następuje wielu wywołań <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> metody.  
  
> [!NOTE]
>  Gdy <xref:System.Xml.XPath.XPathNavigator> obiektu jest ustawiony na węzeł atrybutu lub nazw <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> i <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> metody zawsze zwracają `false`, i nie mają wpływu na pozycję <xref:System.Xml.XPath.XPathNavigator>. Wyjątki są <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>, i <xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A> metody.  
  
### <a name="the-xpathnamespacescope-enumeration"></a>Wyliczenie XPathNamespaceScope  
 Podczas przechodzenia węzły przestrzeni nazw <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> i <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> można wywołać metody <xref:System.Xml.XPath.XPathNamespaceScope> parametru. Te metody będą działały inaczej niż ich odpowiedniki o nazwie bez parametrów. <xref:System.Xml.XPath.XPathNamespaceScope> Wyliczenie ma wartości <xref:System.Xml.XPath.XPathNamespaceScope.All>, <xref:System.Xml.XPath.XPathNamespaceScope.ExcludeXml>, lub <xref:System.Xml.XPath.XPathNamespaceScope.Local>.  
  
 W poniższych przykładach pokazano, jakie przestrzenie nazw są zwracane przez <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> i <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> metod na różnych zakresów w dokumentach XML.  
  
```xml  
<root>  
    <element1 xmlns="http://www.contoso.com" xmlns:books="http://www.contoso.com/books">  
        <element2 />  
    </element1>  
</root>  
```  
  
 Sekwencja przestrzeni nazw (przestrzeń nazw <xref:System.Xml.XPath.XPathNavigator> jest umieszczony na po wywołaniu <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> metody następuje szereg wywołań do <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> metody) jest następujący.  
  
- Ustawiony na `element2`: `xmlns:books="http://www.contoso.com/books"`, `xmlns="http://www.contoso.com"`, i `xmlns:xml="http://www.w3.org/XML/1998/namespace"`.  
  
- Ustawiony na `element1`: `xmlns:books="http://www.contoso.com/books"`, `xmlns="http://www.contoso.com"`, i `xmlns:xml="http://www.w3.org/XML/1998/namespace"`.  
  
- Ustawiony na `root`: `xmlns:xml="http://www.w3.org/XML/1998/namespace".`  
  
> [!NOTE]
>  <xref:System.Xml.XPath.XPathNavigator> Klasa zwraca węzły przestrzeni nazw w kolejności odwrotnej dokumentu. W związku z tym <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> zasadniczo przechodzi do ostatniego węzła obszaru nazw w bieżącym zakresie.  
  
 W poniższych przykładach pokazano, jakie przestrzenie nazw są zwracane przez <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> i <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> metod z <xref:System.Xml.XPath.XPathNamespaceScope> wyliczenie określona w różnych zakresów w dokumentach XML.  
  
```xml  
<root xmlns="http://www.contoso.com" xmlns:a="http://www.contoso.com/a" xmlns:b="http://www.contoso.com/b">  
    <child1 xmlns="" xmlns:a="urn:a">  
        <child2 xmlns:c="urn:c" />  
    </child1>  
</root>  
```  
  
 Ustawiony na `child2`, sekwencji nazw (przestrzeń nazw <xref:System.Xml.XPath.XPathNavigator> jest umieszczony na po wywołaniu <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> metody następuje szereg wywołań do <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> metody) jest następująca.  
  
- <xref:System.Xml.XPath.XPathNamespaceScope.All>: `xmlns:c="urn:c"`, `xmlns:a="urn:a"`, `xmlns=""`, `xmlns:b="http://www.contoso.com/b"`, `xmlns:a="http://www.contoso.com/a"`, `xmlns="http://www.contoso.com"`, i `xmlns:xml="http://www.w3.org/XML/1998/namespace"`.  
  
- <xref:System.Xml.XPath.XPathNamespaceScope.ExcludeXml>: `xmlns:c="urn:c"`, `xmlns:a="urn:a"`, `xmlns=""`, `xmlns:b="http://www.contoso.com/b"`, `xmlns:a="http://www.contoso.com/a"`, i `xmlns="http://www.contoso.com"`.  
  
- <xref:System.Xml.XPath.XPathNamespaceScope.Local>: `xmlns:c="urn:c"`.  
  
> [!NOTE]
>  <xref:System.Xml.XPath.XPathNavigator> Klasa zwraca węzły przestrzeni nazw w kolejności odwrotnej dokumentu. W związku z tym <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> zasadniczo przechodzi do ostatniego węzła obszaru nazw w bieżącym zakresie.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Przetwarzanie danych XML przy użyciu modelu danych XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Nawigacja po zestawie węzłów przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)
- [Wyodrębnianie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)
- [Uzyskiwanie dostępu do silnie typizowanych danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
