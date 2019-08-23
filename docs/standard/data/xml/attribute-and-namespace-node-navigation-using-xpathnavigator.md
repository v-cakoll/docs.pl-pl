---
title: Nawigacja po atrybutach i przestrzeni nazw węzła przy użyciu klasy XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 23975f88-e0af-4b88-93de-9e20e11880ad
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4188896fb36d8535f86b245c3b1942f5a058da9b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936833"
---
# <a name="attribute-and-namespace-node-navigation-using-xpathnavigator"></a>Nawigacja po atrybutach i przestrzeni nazw węzła przy użyciu klasy XPathNavigator
<xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> [](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md) Klasa zawiera dwa zestawy metod nawigacji, pierwszy zestaw, który znajduje się w obszarze nawigacji zestawu węzłów za pomocą elementu XPathNavigator, służy do nawigowania po zestawach węzłów w obiekcie lub. <xref:System.Xml.XPath.XPathNavigator> Drugi zestaw, opisany w tym temacie, służy do nawigowania po *węzłach atrybutów i przestrzeni nazw* <xref:System.Xml.XPath.XPathDocument> w <xref:System.Xml.XmlDocument> obiekcie or.  
  
## <a name="attribute-node-navigation"></a>Nawigacja węzła atrybutu  
 Atrybuty są właściwościami elementu, a nie elementem podrzędnym elementu. Ta różnica jest ważna, ponieważ metody <xref:System.Xml.XPath.XPathNavigator> klasy używane do nawigowania w węzłach równorzędnych, nadrzędnych i podrzędnych.  
  
 Na przykład <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> metody i <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> nie są używane do nawigowania po elemencie do atrybutu lub między atrybutami. Zamiast tego atrybuty mają różne metody nawigacji.  
  
 Poniżej przedstawiono metody <xref:System.Xml.XPath.XPathNavigator> nawigacji atrybutów klasy.  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToAttribute%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToFirstAttribute%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToNextAttribute%2A>  
  
 Gdy bieżącym węzłem jest element, można użyć <xref:System.Xml.XPath.XPathNavigator.HasAttributes%2A> właściwości, aby sprawdzić, czy istnieją atrybuty skojarzone z elementem. Gdy wiadomo, że element ma atrybuty, istnieje wiele metod uzyskiwania dostępu do atrybutów. Aby pobrać pojedynczy atrybut z elementu, użyj <xref:System.Xml.XPath.XPathNavigator.GetAttribute%2A> metody. Aby przenieść <xref:System.Xml.XPath.XPathNavigator> do określonego atrybutu, <xref:System.Xml.XPath.XPathNavigator.MoveToAttribute%2A> Użyj metody. Można również <xref:System.Xml.XPath.XPathNavigator.MoveToFirstAttribute%2A> <xref:System.Xml.XPath.XPathNavigator.MoveToNextAttribute%2A> wykonać iterację każdego atrybutu elementu przy użyciu metody, a następnie wiele wywołań metody.  
  
> [!NOTE]
> <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A> <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A> <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A> <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A> <xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A> `false` <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> Gdy obiekt jest umieszczony w węźle atrybutu lub przestrzeni nazw, metody<xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> ,,,, i zawsze zwracają, <xref:System.Xml.XPath.XPathNavigator> i nie mają wpływu na pozycję <xref:System.Xml.XPath.XPathNavigator>. Wyjątkami są <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>metody, <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>, i <xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A> .  
  
## <a name="namespace-node-navigation"></a>Nawigowanie po węźle przestrzeni nazw  
 Każdy element ma skojarzony zestaw węzłów przestrzeni nazw, jeden dla każdego odrębnego prefiksu przestrzeni nazw, który jest powiązany z identyfikatorem URI przestrzeni nazw w zakresie dla elementu (łącznie z prefiksem XML związanym `http://www.w3.org/XML/1998/namespace` z przestrzenią nazw, która jest niejawnie zadeklarowana w każdym dokumencie XML). i jeden dla domyślnej przestrzeni nazw, jeśli jest w zakresie dla elementu. Element jest elementem nadrzędnym każdego z tych węzłów nazw; jednak węzła obszaru nazw nie jest elementem podrzędnym odpowiedniego elementu nadrzędnego.  
  
 Podobnie jak w przypadku atrybutów <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> , <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> metody i nie są używane do nawigowania z elementu do węzła obszaru nazw lub między węzłami przestrzeni nazw. Zamiast tego węzły przestrzeni nazw mają różne metody nawigacji.  
  
 Poniżej przedstawiono metody <xref:System.Xml.XPath.XPathNavigator> nawigacji przestrzeni nazw klasy.  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToNamespace%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A>  
  
 W zakresie dla każdego elementu w dokumencie XML zawsze występuje co najmniej jeden węzeł przestrzeni nazw. Jest to węzeł przestrzeni nazw z prefiksem `xml` i identyfikatorem `http://www.w3.org/XML/1998/namespace`URI przestrzeni nazw. Aby pobrać identyfikator URI przestrzeni nazw w zakresie o określonym prefiksie, użyj <xref:System.Xml.XPath.XPathNavigator.GetNamespace%2A> metody. Aby przenieść <xref:System.Xml.XPath.XPathNavigator> obiekt do określonego węzła obszaru nazw, <xref:System.Xml.XPath.XPathNavigator.MoveToNamespace%2A> Użyj metody. Można również wykonać iterację dla każdego węzła przestrzeni nazw w zakresie dla elementu przy użyciu <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> metody, a po niej wiele wywołań <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> metody.  
  
> [!NOTE]
> <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A> <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A> <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A> <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A> <xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A> `false` <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> Gdy obiekt jest umieszczony w węźle atrybutu lub przestrzeni nazw, metody<xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> ,,,, i zawsze zwracają, <xref:System.Xml.XPath.XPathNavigator> i nie mają wpływu na pozycję <xref:System.Xml.XPath.XPathNavigator>. Wyjątkami są <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>metody, <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>, i <xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A> .  
  
### <a name="the-xpathnamespacescope-enumeration"></a>Wyliczenie XPathNamespaceScope  
 Podczas nawigowania po węzłach <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> przestrzeni <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> nazw metody i <xref:System.Xml.XPath.XPathNamespaceScope> mogą być wywoływane z parametrem. Metody te zachowują się inaczej niż ich odpowiedniki wywołane bez parametrów. Wyliczenie zawiera <xref:System.Xml.XPath.XPathNamespaceScope.All>wartości ,<xref:System.Xml.XPath.XPathNamespaceScope.ExcludeXml>, lub <xref:System.Xml.XPath.XPathNamespaceScope.Local>. <xref:System.Xml.XPath.XPathNamespaceScope>  
  
 W poniższych przykładach pokazano, jakie przestrzenie nazw <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> są <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> zwracane przez metody i w różnych zakresach w dokumencie XML.  
  
```xml  
<root>  
    <element1 xmlns="http://www.contoso.com" xmlns:books="http://www.contoso.com/books">  
        <element2 />  
    </element1>  
</root>  
```  
  
 Sekwencja przestrzeni nazw (przestrzeń nazw <xref:System.Xml.XPath.XPathNavigator> umieszczona po <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> wywołaniu metody, a następnie <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> seria wywołań metody) jest następująca.  
  
- Po ustawieniu `element2`: `xmlns:books="http://www.contoso.com/books"`, `xmlns="http://www.contoso.com"`, i `xmlns:xml="http://www.w3.org/XML/1998/namespace"`.  
  
- Po ustawieniu `element1`: `xmlns:books="http://www.contoso.com/books"`, `xmlns="http://www.contoso.com"`, i `xmlns:xml="http://www.w3.org/XML/1998/namespace"`.  
  
- Po ustawieniu `root`:`xmlns:xml="http://www.w3.org/XML/1998/namespace".`  
  
> [!NOTE]
> <xref:System.Xml.XPath.XPathNavigator> Klasa zwraca węzły przestrzeni nazw w kolejności odwrotnego dokumentu. W związku <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> z tym, zasadniczo przenoszone do ostatniego węzła przestrzeni nazw w bieżącym zakresie.  
  
 W poniższych przykładach pokazano, jakie przestrzenie nazw <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> są <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> zwracane przez metody <xref:System.Xml.XPath.XPathNamespaceScope> i z wyliczeniem określonym w różnych zakresach w dokumencie XML.  
  
```xml  
<root xmlns="http://www.contoso.com" xmlns:a="http://www.contoso.com/a" xmlns:b="http://www.contoso.com/b">  
    <child1 xmlns="" xmlns:a="urn:a">  
        <child2 xmlns:c="urn:c" />  
    </child1>  
</root>  
```  
  
 Po włączeniu `child2`kolejność przestrzeni nazw ( <xref:System.Xml.XPath.XPathNavigator> przestrzeń nazw <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> umieszczona po wywołaniu metody, <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> a następnie seria wywołań metody) jest następująca.  
  
- <xref:System.Xml.XPath.XPathNamespaceScope.All>: `xmlns:c="urn:c"`, `xmlns:a="urn:a"`, ,,`xmlns=""`, i .`xmlns:xml="http://www.w3.org/XML/1998/namespace"` `xmlns:b="http://www.contoso.com/b"` `xmlns:a="http://www.contoso.com/a"` `xmlns="http://www.contoso.com"`  
  
- <xref:System.Xml.XPath.XPathNamespaceScope.ExcludeXml>: `xmlns:c="urn:c"`, `xmlns:a="urn:a"`, ,,`xmlns=""`i .`xmlns="http://www.contoso.com"` `xmlns:b="http://www.contoso.com/b"` `xmlns:a="http://www.contoso.com/a"`  
  
- <xref:System.Xml.XPath.XPathNamespaceScope.Local>: `xmlns:c="urn:c"`.  
  
> [!NOTE]
> <xref:System.Xml.XPath.XPathNavigator> Klasa zwraca węzły przestrzeni nazw w kolejności odwrotnego dokumentu. W związku <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> z tym, zasadniczo przenoszone do ostatniego węzła przestrzeni nazw w bieżącym zakresie.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Przetwarzanie danych XML przy użyciu modelu danych XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Nawigacja po zestawie węzłów przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)
- [Wyodrębnianie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)
- [Uzyskiwanie dostępu do silnie typizowanych danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
