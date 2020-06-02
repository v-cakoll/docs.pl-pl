---
title: Nawigacja po atrybutach i przestrzeni nazw węzła przy użyciu klasy XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 23975f88-e0af-4b88-93de-9e20e11880ad
ms.openlocfilehash: 90c8fe7450a6ca853aaea452e30a292dbdcd9d98
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291620"
---
# <a name="attribute-and-namespace-node-navigation-using-xpathnavigator"></a>Nawigacja po atrybutach i przestrzeni nazw węzła przy użyciu klasy XPathNavigator
<xref:System.Xml.XPath.XPathNavigator>Klasa zawiera dwa zestawy metod nawigacji, pierwszy zestaw, który znajduje się w obszarze [nawigacji zestawu węzłów za pomocą elementu XPathNavigator](node-set-navigation-using-xpathnavigator.md) , służy do nawigowania po *zestawach węzłów* w <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> obiekcie lub. Drugi zestaw, opisany w tym temacie, służy do nawigowania po *węzłach atrybutów i przestrzeni nazw* w <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> obiekcie or.  
  
## <a name="attribute-node-navigation"></a>Nawigacja węzła atrybutu  
 Atrybuty są właściwościami elementu, a nie elementem podrzędnym elementu. Ta różnica jest ważna, ponieważ metody <xref:System.Xml.XPath.XPathNavigator> klasy używane do nawigowania w węzłach równorzędnych, nadrzędnych i podrzędnych.  
  
 Na przykład <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> metody i nie są używane do nawigowania po elemencie do atrybutu lub między atrybutami. Zamiast tego atrybuty mają różne metody nawigacji.  
  
 Poniżej przedstawiono metody nawigacji atrybutów <xref:System.Xml.XPath.XPathNavigator> klasy.  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToAttribute%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToFirstAttribute%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToNextAttribute%2A>  
  
 Gdy bieżącym węzłem jest element, można użyć <xref:System.Xml.XPath.XPathNavigator.HasAttributes%2A> właściwości, aby sprawdzić, czy istnieją atrybuty skojarzone z elementem. Gdy wiadomo, że element ma atrybuty, istnieje wiele metod uzyskiwania dostępu do atrybutów. Aby pobrać pojedynczy atrybut z elementu, użyj <xref:System.Xml.XPath.XPathNavigator.GetAttribute%2A> metody. Aby przenieść <xref:System.Xml.XPath.XPathNavigator> do określonego atrybutu, użyj <xref:System.Xml.XPath.XPathNavigator.MoveToAttribute%2A> metody. Można również wykonać iterację każdego atrybutu elementu przy użyciu <xref:System.Xml.XPath.XPathNavigator.MoveToFirstAttribute%2A> metody, a następnie wiele wywołań <xref:System.Xml.XPath.XPathNavigator.MoveToNextAttribute%2A> metody.  
  
> [!NOTE]
> Gdy <xref:System.Xml.XPath.XPathNavigator> obiekt jest umieszczony w węźle atrybutu lub przestrzeni nazw, <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A> <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A> metody,,,, <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A> <xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A> <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A> <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> i <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> zawsze zwracają `false` i nie mają wpływu na położeniu <xref:System.Xml.XPath.XPathNavigator> . Wyjątkami są <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A> metody, <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A> , i <xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A> .  
  
## <a name="namespace-node-navigation"></a>Nawigowanie po węźle przestrzeni nazw  
 Każdy element ma skojarzony zestaw węzłów przestrzeni nazw, jeden dla każdego odrębnego prefiksu przestrzeni nazw, który jest powiązany z identyfikatorem URI przestrzeni nazw w zakresie dla elementu (łącznie z prefiksem XML związanym z `http://www.w3.org/XML/1998/namespace` przestrzenią nazw, która jest niejawnie zadeklarowana w każdym dokumencie XML) i jeden dla domyślnej przestrzeni nazw, jeśli jeden jest w zakresie dla elementu. Element jest elementem nadrzędnym każdego z tych węzłów nazw; jednak węzła obszaru nazw nie jest elementem podrzędnym odpowiedniego elementu nadrzędnego.  
  
 Podobnie jak w przypadku atrybutów <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> , <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> metody i nie są używane do nawigowania z elementu do węzła obszaru nazw lub między węzłami przestrzeni nazw. Zamiast tego węzły przestrzeni nazw mają różne metody nawigacji.  
  
 Poniżej przedstawiono metody nawigacji przestrzeni nazw <xref:System.Xml.XPath.XPathNavigator> klasy.  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToNamespace%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A>  
  
 W zakresie dla każdego elementu w dokumencie XML zawsze występuje co najmniej jeden węzeł przestrzeni nazw. Jest to węzeł przestrzeni nazw z prefiksem `xml` i identyfikatorem URI przestrzeni nazw `http://www.w3.org/XML/1998/namespace` . Aby pobrać identyfikator URI przestrzeni nazw w zakresie o określonym prefiksie, użyj <xref:System.Xml.XPath.XPathNavigator.GetNamespace%2A> metody. Aby przenieść <xref:System.Xml.XPath.XPathNavigator> obiekt do określonego węzła obszaru nazw, użyj <xref:System.Xml.XPath.XPathNavigator.MoveToNamespace%2A> metody. Można również wykonać iterację dla każdego węzła przestrzeni nazw w zakresie dla elementu przy użyciu <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> metody, a po niej wiele wywołań <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> metody.  
  
> [!NOTE]
> Gdy <xref:System.Xml.XPath.XPathNavigator> obiekt jest umieszczony w węźle atrybutu lub przestrzeni nazw, <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A> <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A> metody,,,, <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A> <xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A> <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A> <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> i <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> zawsze zwracają `false` i nie mają wpływu na położeniu <xref:System.Xml.XPath.XPathNavigator> . Wyjątkami są <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A> metody, <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A> , i <xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A> .  
  
### <a name="the-xpathnamespacescope-enumeration"></a>Wyliczenie XPathNamespaceScope  
 Podczas nawigowania po węzłach przestrzeni nazw <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> metody i mogą być wywoływane z <xref:System.Xml.XPath.XPathNamespaceScope> parametrem. Metody te zachowują się inaczej niż ich odpowiedniki wywołane bez parametrów. <xref:System.Xml.XPath.XPathNamespaceScope>Wyliczenie zawiera wartości <xref:System.Xml.XPath.XPathNamespaceScope.All> , <xref:System.Xml.XPath.XPathNamespaceScope.ExcludeXml> , lub <xref:System.Xml.XPath.XPathNamespaceScope.Local> .  
  
 W poniższych przykładach pokazano, jakie przestrzenie nazw są zwracane przez <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> metody i w <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> różnych zakresach w dokumencie XML.  
  
```xml  
<root>  
    <element1 xmlns="http://www.contoso.com" xmlns:books="http://www.contoso.com/books">  
        <element2 />  
    </element1>  
</root>  
```  
  
 Sekwencja przestrzeni nazw (przestrzeń nazw <xref:System.Xml.XPath.XPathNavigator> umieszczona po wywołaniu <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> metody, a następnie seria wywołań <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> metody) jest następująca.  
  
- Po ustawieniu `element2` : `xmlns:books="http://www.contoso.com/books"` , `xmlns="http://www.contoso.com"` , i `xmlns:xml="http://www.w3.org/XML/1998/namespace"` .  
  
- Po ustawieniu `element1` : `xmlns:books="http://www.contoso.com/books"` , `xmlns="http://www.contoso.com"` , i `xmlns:xml="http://www.w3.org/XML/1998/namespace"` .  
  
- Po ustawieniu `root` :`xmlns:xml="http://www.w3.org/XML/1998/namespace".`  
  
> [!NOTE]
> <xref:System.Xml.XPath.XPathNavigator>Klasa zwraca węzły przestrzeni nazw w kolejności odwrotnego dokumentu. W związku z tym, <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> zasadniczo przenoszone do ostatniego węzła przestrzeni nazw w bieżącym zakresie.  
  
 W poniższych przykładach pokazano, jakie przestrzenie nazw są zwracane przez <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> metody i z <xref:System.Xml.XPath.XPathNamespaceScope> wyliczeniem określonym w różnych zakresach w dokumencie XML.  
  
```xml  
<root xmlns="http://www.contoso.com" xmlns:a="http://www.contoso.com/a" xmlns:b="http://www.contoso.com/b">  
    <child1 xmlns="" xmlns:a="urn:a">  
        <child2 xmlns:c="urn:c" />  
    </child1>  
</root>  
```  
  
 Po włączeniu `child2` kolejność przestrzeni nazw (przestrzeń nazw <xref:System.Xml.XPath.XPathNavigator> umieszczona po wywołaniu <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> metody, a następnie seria wywołań <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> metody) jest następująca.  
  
- <xref:System.Xml.XPath.XPathNamespaceScope.All>: `xmlns:c="urn:c"` ,,,,, `xmlns:a="urn:a"` `xmlns=""` `xmlns:b="http://www.contoso.com/b"` `xmlns:a="http://www.contoso.com/a"` `xmlns="http://www.contoso.com"` i `xmlns:xml="http://www.w3.org/XML/1998/namespace"` .  
  
- <xref:System.Xml.XPath.XPathNamespaceScope.ExcludeXml>: `xmlns:c="urn:c"` , `xmlns:a="urn:a"` ,,, `xmlns=""` `xmlns:b="http://www.contoso.com/b"` `xmlns:a="http://www.contoso.com/a"` i `xmlns="http://www.contoso.com"` .  
  
- <xref:System.Xml.XPath.XPathNamespaceScope.Local>: `xmlns:c="urn:c"`.  
  
> [!NOTE]
> <xref:System.Xml.XPath.XPathNavigator>Klasa zwraca węzły przestrzeni nazw w kolejności odwrotnego dokumentu. W związku z tym, <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> zasadniczo przenoszone do ostatniego węzła przestrzeni nazw w bieżącym zakresie.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Przetwarzanie danych XML przy użyciu modelu danych XPath](process-xml-data-using-the-xpath-data-model.md)
- [Nawigacja po zestawie węzłów przy użyciu klasy XPathNavigator](node-set-navigation-using-xpathnavigator.md)
- [Wyodrębnianie danych XML przy użyciu klasy XPathNavigator](extract-xml-data-using-xpathnavigator.md)
- [Uzyskiwanie dostępu do silnie typizowanych danych XML przy użyciu klasy XPathNavigator](accessing-strongly-typed-xml-data-using-xpathnavigator.md)
