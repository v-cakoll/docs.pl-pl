---
title: Omówienie klas LINQ do klas XML (C#)
ms.date: 07/20/2015
ms.assetid: bf666100-5392-4968-97f4-f6b9d3287d7b
ms.openlocfilehash: 55be666fc0db0becb12ec8b525e7fc443536e1df
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69591885"
---
# <a name="linq-to-xml-classes-overview-c"></a>Omówienie klas LINQ do klas XML (C#)
W tym temacie znajduje [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] się <xref:System.Xml.Linq> lista klas w obszarze nazw i krótki opis każdego z nich.  
  
## <a name="linq-to-xml-classes"></a>LINQ do klas XML  
  
### <a name="xattribute-class"></a>Klasa XAttribute  
 <xref:System.Xml.Linq.XAttribute>reprezentuje atrybut XML. Aby uzyskać szczegółowe informacje i przykłady, zobacz [Przegląd klasy XAttribute (C#)](./xattribute-class-overview.md).  
  
### <a name="xcdata-class"></a>Klasa XCData  
 <xref:System.Xml.Linq.XCData>reprezentuje węzeł tekstowy CDATA.  
  
### <a name="xcomment-class"></a>Klasa XComment  
 <xref:System.Xml.Linq.XComment>reprezentuje komentarz XML.  
  
### <a name="xcontainer-class"></a>Klasa XContainer  
 <xref:System.Xml.Linq.XContainer>jest abstrakcyjną klasą podstawową dla wszystkich węzłów, które mogą mieć węzły podrzędne. Następujące klasy pochodzą od <xref:System.Xml.Linq.XContainer> klasy:  
  
- <xref:System.Xml.Linq.XElement>  
  
- <xref:System.Xml.Linq.XDocument>  
  
### <a name="xdeclaration-class"></a>Klasa XDeclaration  
 <xref:System.Xml.Linq.XDeclaration>reprezentuje deklarację XML. Deklaracja XML służy do deklarowania wersji XML i kodowania dokumentu. Ponadto deklaracja XML określa, czy dokument XML jest autonomiczny. Jeśli dokument jest autonomiczny, nie ma żadnych deklaracji zewnętrznych znaczników, w zewnętrznym DTD lub w jednostce parametru zewnętrznego, do której odwołuje się wewnętrzny podzbiór.  
  
### <a name="xdocument-class"></a>Klasa XDocument  
 <xref:System.Xml.Linq.XDocument>reprezentuje dokument XML. Aby uzyskać szczegółowe informacje i przykłady, zobacz [Przegląd klasy XDocument (C#)](./xdocument-class-overview.md).  
  
### <a name="xdocumenttype-class"></a>Klasa XDocumentType  
 <xref:System.Xml.Linq.XDocumentType>reprezentuje definicję typu dokumentu XML (DTD).  
  
### <a name="xelement-class"></a>Klasa XElement  
 <xref:System.Xml.Linq.XElement>reprezentuje element XML. Aby uzyskać szczegółowe informacje i przykłady, zobacz [Przegląd klasy XElement (C#)](./xelement-class-overview.md).  
  
### <a name="xname-class"></a>Klasa XName  
 <xref:System.Xml.Linq.XName>reprezentuje nazwy elementów<xref:System.Xml.Linq.XElement>( ) i<xref:System.Xml.Linq.XAttribute>atrybutów ( ). Aby uzyskać szczegółowe informacje i przykłady, zobacz [Przegląd klasy XDocument (C#)](./xdocument-class-overview.md).  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]został zaprojektowany tak, aby nazwy XML były tak proste, jak to tylko możliwe. Ze względu na ich złożoność nazwy XML są często uważane za zaawansowany temat w XML. Prawdopodobnie ta złożoność nie pochodzi z przestrzeni nazw, które deweloperzy używają regularnie w programowaniu, ale z prefiksów obszaru nazw. Prefiksy obszaru nazw mogą być przydatne do zmniejszenia naciśnięć klawiszy wymaganych podczas wprowadzania kodu XML lub do ułatwienia odczytu języka XML. Jednak prefiksy są często tylko skrót emitują pełny obszar nazw XML i nie są wymagane w większości przypadków. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]upraszcza nazwy XML, rozwiązując wszystkie prefiksy do odpowiadającej im przestrzeni nazw XML. Prefiksy są dostępne, jeśli są <xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A> wymagane, za pośrednictwem metody.  
  
 W razie potrzeby można kontrolować prefiksy obszaru nazw. W pewnych okolicznościach podczas pracy z innymi systemami XML, takimi jak XSLT lub XAML, należy sterować prefiksami obszaru nazw. Na przykład jeśli masz wyrażenie XPath, które używa prefiksów obszaru nazw i jest osadzone w arkuszu stylów XSLT, należy upewnić się, że dokument XML jest seryjny z prefiksami obszaru nazw, które pasują do tych używanych w wyrażeniu XPath.  
  
### <a name="xnamespace-class"></a>Klasa XNamespace  
 <xref:System.Xml.Linq.XNamespace>reprezentuje obszar nazw dla <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XAttribute>lub . Obszary nazw są składnikiem pliku <xref:System.Xml.Linq.XName>.  
  
### <a name="xnode-class"></a>Klasa XNode  
 <xref:System.Xml.Linq.XNode>jest klasą abstrakcyjną, która reprezentuje węzły drzewa XML. Następujące klasy pochodzą od <xref:System.Xml.Linq.XNode> klasy:  
  
- <xref:System.Xml.Linq.XText>  
  
- <xref:System.Xml.Linq.XContainer>  
  
- <xref:System.Xml.Linq.XComment>  
  
- <xref:System.Xml.Linq.XProcessingInstruction>  
  
- <xref:System.Xml.Linq.XDocumentType>  
  
### <a name="xnodedocumentordercomparer-class"></a>Klasa XNodeDocumentOrderComparer  
 <xref:System.Xml.Linq.XNodeDocumentOrderComparer>udostępnia funkcje do porównywania węzłów dla ich zamówienia dokumentu.  
  
### <a name="xnodeequalitycomparer-class"></a>Klasa XNodeEqualityComparer  
 <xref:System.Xml.Linq.XNodeEqualityComparer>udostępnia funkcje do porównywania węzłów dla równości wartości.  
  
### <a name="xobject-class"></a>Klasa XObject  
 <xref:System.Xml.Linq.XObject>jest abstrakcyjną klasą podstawową <xref:System.Xml.Linq.XNode> i <xref:System.Xml.Linq.XAttribute>. Zapewnia adnotacje i funkcje zdarzeń.  
  
### <a name="xobjectchange-class"></a>Klasa XObjectChange  
 <xref:System.Xml.Linq.XObjectChange>określa typ zdarzenia, gdy zdarzenie jest <xref:System.Xml.Linq.XObject>wywoływane dla .  
  
### <a name="xobjectchangeeventargs-class"></a>Klasa XObjectChangeEventArgs  
 <xref:System.Xml.Linq.XObjectChangeEventArgs>dostarcza danych <xref:System.Xml.Linq.XObject.Changing> dotyczących <xref:System.Xml.Linq.XObject.Changed> i zdarzeń.  
  
### <a name="xprocessinginstruction-class"></a>XProcessingInstruction Klasa  
 <xref:System.Xml.Linq.XProcessingInstruction>reprezentuje instrukcję przetwarzania XML. Instrukcja przetwarzania przekazuje informacje do aplikacji, która przetwarza XML.  
  
### <a name="xtext-class"></a>Klasa XText  
 <xref:System.Xml.Linq.XText>reprezentuje węzeł tekstowy. W większości przypadków nie trzeba używać tej klasy. Ta klasa jest używana głównie dla zawartości mieszanej.  
  
## <a name="see-also"></a>Zobacz też

- [Omówienie programowania LINQ do XML (C#)](./linq-to-xml-overview.md)
