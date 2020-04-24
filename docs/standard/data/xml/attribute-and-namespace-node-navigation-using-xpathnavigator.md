---
title: Nawigacja po atrybutach i przestrzeni nazw węzła przy użyciu klasy XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 23975f88-e0af-4b88-93de-9e20e11880ad
ms.openlocfilehash: 6809a2a47a9ca25a16a9be75a0a8a8b03f98a21d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711158"
---
# <a name="attribute-and-namespace-node-navigation-using-xpathnavigator"></a>Nawigacja po atrybutach i przestrzeni nazw węzła przy użyciu klasy XPathNavigator
<xref:System.Xml.XPath.XPathNavigator> Klasa zawiera dwa zestawy metod nawigacji, pierwszy zestaw, który znajduje się w obszarze [nawigacji zestawu węzłów za pomocą](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md) elementu <xref:System.Xml.XPath.XPathDocument> XPathNavigator, służy do nawigowania po *zestawach węzłów* w <xref:System.Xml.XmlDocument> obiekcie lub. Drugi zestaw, opisany w tym temacie, służy do nawigowania po *węzłach atrybutów i przestrzeni nazw* <xref:System.Xml.XPath.XPathDocument> w <xref:System.Xml.XmlDocument> obiekcie or.  
  
## <a name="attribute-node-navigation"></a>Nawigacja węzła atrybutu  
 Atrybuty są właściwościami elementu, a nie elementem podrzędnym elementu. Ta różnica jest ważna, ponieważ metody <xref:System.Xml.XPath.XPathNavigator> klasy używane do nawigowania w węzłach równorzędnych, nadrzędnych i podrzędnych.  
  
 Na przykład metody <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> i <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> nie są używane do nawigowania po elemencie do atrybutu lub między atrybutami. Zamiast tego atrybuty mają różne metody nawigacji.  
  
 Poniżej przedstawiono metody nawigacji atrybutów <xref:System.Xml.XPath.XPathNavigator> klasy.  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToAttribute%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToFirstAttribute%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToNextAttribute%2A>  
  
 Gdy bieżącym węzłem jest element, można użyć <xref:System.Xml.XPath.XPathNavigator.HasAttributes%2A> właściwości, aby sprawdzić, czy istnieją atrybuty skojarzone z elementem. Gdy wiadomo, że element ma atrybuty, istnieje wiele metod uzyskiwania dostępu do atrybutów. Aby pobrać pojedynczy atrybut z elementu, użyj <xref:System.Xml.XPath.XPathNavigator.GetAttribute%2A> metody. Aby przenieść <xref:System.Xml.XPath.XPathNavigator> do określonego atrybutu, użyj <xref:System.Xml.XPath.XPathNavigator.MoveToAttribute%2A> metody. Można również wykonać iterację każdego atrybutu elementu przy użyciu <xref:System.Xml.XPath.XPathNavigator.MoveToFirstAttribute%2A> metody, a następnie wiele wywołań <xref:System.Xml.XPath.XPathNavigator.MoveToNextAttribute%2A> metody.  
  
> [!NOTE]
> Gdy <xref:System.Xml.XPath.XPathNavigator> obiekt jest umieszczony w węźle atrybutu lub przestrzeni nazw, metody <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A> <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> i <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> zawsze zwracają `false`i nie mają wpływu na położeniu. <xref:System.Xml.XPath.XPathNavigator> Wyjątkami są metody <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>, i <xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A> .  
  
## <a name="namespace-node-navigation"></a>Nawigowanie po węźle przestrzeni nazw  
 Każdy element ma skojarzony zestaw węzłów przestrzeni nazw, jeden dla każdego odrębnego prefiksu przestrzeni nazw, który jest powiązany z identyfikatorem URI przestrzeni nazw w zakresie dla elementu (łącznie z prefiksem XML związanym z `http://www.w3.org/XML/1998/namespace` przestrzenią nazw, która jest niejawnie zadeklarowana w każdym dokumencie XML) i jeden dla domyślnej przestrzeni nazw, jeśli jeden jest w zakresie dla elementu. Element jest elementem nadrzędnym każdego z tych węzłów nazw; jednak węzła obszaru nazw nie jest elementem podrzędnym odpowiedniego elementu nadrzędnego.  
  
 Podobnie jak w przypadku atrybutów <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> , <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> metody i nie są używane do nawigowania z elementu do węzła obszaru nazw lub między węzłami przestrzeni nazw. Zamiast tego węzły przestrzeni nazw mają różne metody nawigacji.  
  
 Poniżej przedstawiono metody nawigacji przestrzeni nazw <xref:System.Xml.XPath.XPathNavigator> klasy.  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToNamespace%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A>  
  
 W zakresie dla każdego elementu w dokumencie XML zawsze występuje co najmniej jeden węzeł przestrzeni nazw. Jest to węzeł przestrzeni nazw z prefiksem `xml` i identyfikatorem `http://www.w3.org/XML/1998/namespace`URI przestrzeni nazw. Aby pobrać identyfikator URI przestrzeni nazw w zakresie o określonym prefiksie, użyj <xref:System.Xml.XPath.XPathNavigator.GetNamespace%2A> metody. Aby przenieść <xref:System.Xml.XPath.XPathNavigator> obiekt do określonego węzła obszaru nazw, użyj <xref:System.Xml.XPath.XPathNavigator.MoveToNamespace%2A> metody. Można również wykonać iterację dla każdego węzła przestrzeni nazw w zakresie dla elementu przy użyciu <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> metody, a po niej wiele wywołań <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> metody.  
  
> [!NOTE]
> Gdy <xref:System.Xml.XPath.XPathNavigator> obiekt jest umieszczony w węźle atrybutu lub przestrzeni nazw, metody <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A> <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> i <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> zawsze zwracają `false`i nie mają wpływu na położeniu. <xref:System.Xml.XPath.XPathNavigator> Wyjątkami są metody <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>, i <xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A> .  
  
### <a name="the-xpathnamespacescope-enumeration"></a>Wyliczenie XPathNamespaceScope  
 Podczas nawigowania po węzłach <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> przestrzeni <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> nazw metody i mogą być wywoływane <xref:System.Xml.XPath.XPathNamespaceScope> z parametrem. Metody te zachowują się inaczej niż ich odpowiedniki wywołane bez parametrów. <xref:System.Xml.XPath.XPathNamespaceScope> Wyliczenie zawiera wartości <xref:System.Xml.XPath.XPathNamespaceScope.All>, <xref:System.Xml.XPath.XPathNamespaceScope.ExcludeXml>, lub <xref:System.Xml.XPath.XPathNamespaceScope.Local>.  
  
 W poniższych przykładach pokazano, jakie przestrzenie nazw <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> są <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> zwracane przez metody i w różnych zakresach w dokumencie XML.  
  
```xml  
<root>  
    <element1 xmlns="http://www.contoso.com" xmlns:books="http://www.contoso.com/books">  
        <element2 />  
    </element1>  
</root>  
```  
  
 Sekwencja przestrzeni nazw (przestrzeń nazw <xref:System.Xml.XPath.XPathNavigator> umieszczona po wywołaniu <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> metody, a następnie seria wywołań <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> metody) jest następująca.  
  
- Po ustawieniu `element2`: `xmlns:books="http://www.contoso.com/books"`, `xmlns="http://www.contoso.com"`, i. `xmlns:xml="http://www.w3.org/XML/1998/namespace"`  
  
- Po ustawieniu `element1`: `xmlns:books="http://www.contoso.com/books"`, `xmlns="http://www.contoso.com"`, i. `xmlns:xml="http://www.w3.org/XML/1998/namespace"`  
  
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
  
 Po włączeniu `child2`kolejność przestrzeni nazw (przestrzeń nazw <xref:System.Xml.XPath.XPathNavigator> umieszczona po wywołaniu <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> metody, a następnie seria wywołań <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> metody) jest następująca.  
  
- <xref:System.Xml.XPath.XPathNamespaceScope.All>: `xmlns:c="urn:c"`, `xmlns:a="urn:a"`, `xmlns=""` `xmlns:b="http://www.contoso.com/b"` `xmlns:a="http://www.contoso.com/a"`,,, i `xmlns:xml="http://www.w3.org/XML/1998/namespace"` `xmlns="http://www.contoso.com"`  
  
- <xref:System.Xml.XPath.XPathNamespaceScope.ExcludeXml>: `xmlns:c="urn:c"`, `xmlns:a="urn:a"`, `xmlns=""` `xmlns:b="http://www.contoso.com/b"`,, i `xmlns="http://www.contoso.com"` `xmlns:a="http://www.contoso.com/a"`  
  
- <xref:System.Xml.XPath.XPathNamespaceScope.Local>: `xmlns:c="urn:c"`.  
  
> [!NOTE]
> <xref:System.Xml.XPath.XPathNavigator> Klasa zwraca węzły przestrzeni nazw w kolejności odwrotnego dokumentu. W związku <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> z tym, zasadniczo przenoszone do ostatniego węzła przestrzeni nazw w bieżącym zakresie.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Przetwarzanie danych XML przy użyciu modelu danych XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Nawigacja po zestawie węzłów przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)
- [Wyodrębnianie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)
- [Uzyskiwanie dostępu do silnie typizowanych danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
