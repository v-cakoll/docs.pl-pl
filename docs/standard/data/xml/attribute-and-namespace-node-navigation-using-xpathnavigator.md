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
Klasa <xref:System.Xml.XPath.XPathNavigator> udostępnia dwa zestawy metod nawigacji, pierwszy zestaw, który znajduje się w [nawigacji zestawu węzłów za pomocą elementu XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md) , służy do nawigowania po *zestawach węzłów* w obiekcie <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument>. Drugi zestaw, opisany w tym temacie, służy do nawigowania po *węzłach atrybutów i przestrzeni nazw* w obiekcie <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument>.  
  
## <a name="attribute-node-navigation"></a>Nawigacja węzła atrybutu  
 Atrybuty są właściwościami elementu, a nie elementem podrzędnym elementu. Ta różnica jest ważna, ponieważ metody klasy <xref:System.Xml.XPath.XPathNavigator> używane do nawigowania w węzłach równorzędnych, nadrzędnych i podrzędnych.  
  
 Na przykład metody <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> i <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> nie są używane do nawigowania po elemencie do atrybutu lub między atrybutami. Zamiast tego atrybuty mają różne metody nawigacji.  
  
 Poniżej przedstawiono metody nawigacji atrybutów klasy <xref:System.Xml.XPath.XPathNavigator>.  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToAttribute%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToFirstAttribute%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToNextAttribute%2A>  
  
 Gdy bieżącym węzłem jest element, można użyć właściwości <xref:System.Xml.XPath.XPathNavigator.HasAttributes%2A>, aby sprawdzić, czy istnieją atrybuty skojarzone z elementem. Gdy wiadomo, że element ma atrybuty, istnieje wiele metod uzyskiwania dostępu do atrybutów. Aby pobrać pojedynczy atrybut z elementu, użyj metody <xref:System.Xml.XPath.XPathNavigator.GetAttribute%2A>. Aby przenieść <xref:System.Xml.XPath.XPathNavigator> do określonego atrybutu, użyj metody <xref:System.Xml.XPath.XPathNavigator.MoveToAttribute%2A>. Możesz również wykonać iterację każdego atrybutu elementu przy użyciu metody <xref:System.Xml.XPath.XPathNavigator.MoveToFirstAttribute%2A>, a następnie wiele wywołań metody <xref:System.Xml.XPath.XPathNavigator.MoveToNextAttribute%2A>.  
  
> [!NOTE]
> Gdy obiekt <xref:System.Xml.XPath.XPathNavigator> jest umieszczony w węźle atrybutu lub przestrzeni nazw, metody <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> i <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> zawsze zwracają `false`i nie mają wpływu na pozycję <xref:System.Xml.XPath.XPathNavigator>. Wyjątkami są metody <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>i <xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A>.  
  
## <a name="namespace-node-navigation"></a>Nawigowanie po węźle przestrzeni nazw  
 Każdy element ma skojarzony zestaw węzłów przestrzeni nazw, jeden dla każdego odrębnego prefiksu przestrzeni nazw, który jest powiązany z identyfikatorem URI przestrzeni nazw w zakresie dla elementu (łącznie z prefiksem XML związanym z przestrzenią nazw `http://www.w3.org/XML/1998/namespace`, która jest niejawnie zadeklarowana w każdym dokumencie XML) i jeden dla domyślnej przestrzeni nazw, jeśli jeden jest w zakresie dla elementu. Element jest elementem nadrzędnym każdego z tych węzłów nazw; jednak węzła obszaru nazw nie jest elementem podrzędnym odpowiedniego elementu nadrzędnego.  
  
 Podobnie jak w przypadku atrybutów, metody <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> i <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> nie są używane do nawigowania z elementu do węzła obszaru nazw lub między węzłami przestrzeni nazw. Zamiast tego węzły przestrzeni nazw mają różne metody nawigacji.  
  
 Poniżej przedstawiono metody nawigacji przestrzeni nazw klasy <xref:System.Xml.XPath.XPathNavigator>.  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToNamespace%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A>  
  
 W zakresie dla każdego elementu w dokumencie XML zawsze występuje co najmniej jeden węzeł przestrzeni nazw. Jest to węzeł przestrzeni nazw z prefiksem `xml` i `http://www.w3.org/XML/1998/namespace`URI przestrzeni nazw. Aby pobrać identyfikator URI przestrzeni nazw w zakresie o określonym prefiksie, użyj metody <xref:System.Xml.XPath.XPathNavigator.GetNamespace%2A>. Aby przenieść obiekt <xref:System.Xml.XPath.XPathNavigator> do określonego węzła obszaru nazw, użyj metody <xref:System.Xml.XPath.XPathNavigator.MoveToNamespace%2A>. Można również wykonać iterację dla każdego węzła przestrzeni nazw w zakresie dla elementu przy użyciu metody <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A>, a po niej wiele wywołań metody <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A>.  
  
> [!NOTE]
> Gdy obiekt <xref:System.Xml.XPath.XPathNavigator> jest umieszczony w węźle atrybutu lub przestrzeni nazw, metody <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> i <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> zawsze zwracają `false`i nie mają wpływu na pozycję <xref:System.Xml.XPath.XPathNavigator>. Wyjątkami są metody <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>i <xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A>.  
  
### <a name="the-xpathnamespacescope-enumeration"></a>Wyliczenie XPathNamespaceScope  
 Podczas nawigowania w węzłach przestrzeni nazw metody <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> i <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> mogą być wywoływane przy użyciu parametru <xref:System.Xml.XPath.XPathNamespaceScope>. Metody te zachowują się inaczej niż ich odpowiedniki wywołane bez parametrów. Wyliczenie <xref:System.Xml.XPath.XPathNamespaceScope> ma wartości <xref:System.Xml.XPath.XPathNamespaceScope.All>, <xref:System.Xml.XPath.XPathNamespaceScope.ExcludeXml>lub <xref:System.Xml.XPath.XPathNamespaceScope.Local>.  
  
 W poniższych przykładach pokazano, jakie przestrzenie nazw są zwracane przez <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> i <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> metod w różnych zakresach w dokumencie XML.  
  
```xml  
<root>  
    <element1 xmlns="http://www.contoso.com" xmlns:books="http://www.contoso.com/books">  
        <element2 />  
    </element1>  
</root>  
```  
  
 Sekwencja przestrzeni nazw (przestrzeń nazw <xref:System.Xml.XPath.XPathNavigator> jest umieszczona po wywołaniu metody <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A>, a po niej seria wywołań metody <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A>) jest następująca.  
  
- Po rozłożeniu na `element2`: `xmlns:books="http://www.contoso.com/books"`, `xmlns="http://www.contoso.com"`i `xmlns:xml="http://www.w3.org/XML/1998/namespace"`.  
  
- Po rozłożeniu na `element1`: `xmlns:books="http://www.contoso.com/books"`, `xmlns="http://www.contoso.com"`i `xmlns:xml="http://www.w3.org/XML/1998/namespace"`.  
  
- Po rozłożeniu na `root`: `xmlns:xml="http://www.w3.org/XML/1998/namespace".`  
  
> [!NOTE]
> Klasa <xref:System.Xml.XPath.XPathNavigator> zwraca węzły przestrzeni nazw w kolejności odwrotnego dokumentu. Dlatego <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> zasadniczo przenoszone do ostatniego węzła przestrzeni nazw w bieżącym zakresie.  
  
 W poniższych przykładach pokazano, jakie przestrzenie nazw są zwracane przez <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> i <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> metody z wyliczeniem <xref:System.Xml.XPath.XPathNamespaceScope> określonym w różnych zakresach w dokumencie XML.  
  
```xml  
<root xmlns="http://www.contoso.com" xmlns:a="http://www.contoso.com/a" xmlns:b="http://www.contoso.com/b">  
    <child1 xmlns="" xmlns:a="urn:a">  
        <child2 xmlns:c="urn:c" />  
    </child1>  
</root>  
```  
  
 Po ustawieniu na `child2`, sekwencja przestrzeni nazw (przestrzeń nazw, w której znajduje się <xref:System.Xml.XPath.XPathNavigator> po wywołaniu metody <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A>, a następnie seria wywołań metody <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A>) jest następująca.  
  
- <xref:System.Xml.XPath.XPathNamespaceScope.All>: `xmlns:c="urn:c"`, `xmlns:a="urn:a"`, `xmlns=""`, `xmlns:b="http://www.contoso.com/b"`, `xmlns:a="http://www.contoso.com/a"`, `xmlns="http://www.contoso.com"`i `xmlns:xml="http://www.w3.org/XML/1998/namespace"`.  
  
- <xref:System.Xml.XPath.XPathNamespaceScope.ExcludeXml>: `xmlns:c="urn:c"`, `xmlns:a="urn:a"`, `xmlns=""`, `xmlns:b="http://www.contoso.com/b"`, `xmlns:a="http://www.contoso.com/a"`i `xmlns="http://www.contoso.com"`.  
  
- <xref:System.Xml.XPath.XPathNamespaceScope.Local>: `xmlns:c="urn:c"`.  
  
> [!NOTE]
> Klasa <xref:System.Xml.XPath.XPathNavigator> zwraca węzły przestrzeni nazw w kolejności odwrotnego dokumentu. Dlatego <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> zasadniczo przenoszone do ostatniego węzła przestrzeni nazw w bieżącym zakresie.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Przetwarzanie danych XML przy użyciu modelu danych XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Nawigacja po zestawie węzłów przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)
- [Wyodrębnianie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)
- [Uzyskiwanie dostępu do silnie typizowanych danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
