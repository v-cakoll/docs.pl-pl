---
title: Klasy LINQ to XML — przegląd
ms.date: 07/20/2015
ms.assetid: f11b62b5-d522-4c23-92ae-23186dc16447
ms.openlocfilehash: 468435a0dfac64c85b3447f15f9cde63eb98aeb0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84368884"
---
# <a name="linq-to-xml-classes-overview-visual-basic"></a>Przegląd klas LINQ to XML (Visual Basic)
Ten temat zawiera listę [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] klas w <xref:System.Xml.Linq> przestrzeni nazw oraz Krótki opis każdego z nich.  
  
## <a name="linq-to-xml-classes"></a>Klasy LINQ to XML  
  
### <a name="xattribute-class"></a>Klasa XAttribute  
 <xref:System.Xml.Linq.XAttribute>reprezentuje atrybut XML. Aby uzyskać szczegółowe informacje i przykłady, zobacz [XAttribute Class Overview (Visual Basic)](xattribute-class-overview.md).  
  
### <a name="xcdata-class"></a>Klasa XCData  
 <xref:System.Xml.Linq.XCData>reprezentuje węzeł tekstu CDATA.  
  
### <a name="xcomment-class"></a>Klasa XComment  
 <xref:System.Xml.Linq.XComment>Reprezentuje komentarz XML.  
  
### <a name="xcontainer-class"></a>Klasa XContainer  
 <xref:System.Xml.Linq.XContainer>jest abstrakcyjną klasą bazową dla wszystkich węzłów, które mogą mieć węzły podrzędne. Następujące klasy pochodzą od <xref:System.Xml.Linq.XContainer> klasy:  
  
- <xref:System.Xml.Linq.XElement>  
  
- <xref:System.Xml.Linq.XDocument>  
  
### <a name="xdeclaration-class"></a>Klasa XDeclaration  
 <xref:System.Xml.Linq.XDeclaration>reprezentuje deklarację XML. Deklaracja XML jest używana do deklarowania wersji XML i kodowania dokumentu. Ponadto deklaracja XML określa, czy dokument XML jest autonomiczny. Jeśli dokument jest autonomiczny, nie ma żadnych deklaracji znaczników zewnętrznych, w zewnętrznym DTD lub w jednostce parametru zewnętrznego, do której odwołuje się podzbiór wewnętrzny.  
  
### <a name="xdocument-class"></a>Klasa XDocument  
 <xref:System.Xml.Linq.XDocument>reprezentuje dokument XML. Aby uzyskać szczegółowe informacje i przykłady, zobacz [Klasa XDocument — omówienie (Visual Basic)](xdocument-class-overview.md).  
  
### <a name="xdocumenttype-class"></a>XDocumenttype — Klasa  
 <xref:System.Xml.Linq.XDocumentType>reprezentuje definicję typu dokumentu XML (DTD).  
  
### <a name="xelement-class"></a>Klasa XElement  
 <xref:System.Xml.Linq.XElement>reprezentuje element XML. Aby uzyskać szczegółowe informacje i przykłady, zobacz [XElement Class Overview (Visual Basic)](xelement-class-overview.md).  
  
### <a name="xname-class"></a>Klasa XName  
 <xref:System.Xml.Linq.XName>reprezentuje nazwy elementów ( <xref:System.Xml.Linq.XElement> ) i atrybutów ( <xref:System.Xml.Linq.XAttribute> ). Aby uzyskać szczegółowe informacje i przykłady, zobacz [Klasa XDocument — omówienie (Visual Basic)](xdocument-class-overview.md).  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]został zaprojektowany tak, aby nazwy XML były tak proste, jak to możliwe. Ze względu na złożoność nazwy XML często są uważane za zaawansowaną temat w języku XML. Raczej, ta złożoność nie pochodzi z przestrzeni nazw, które deweloperzy wykorzystują regularnie w programowaniu, ale z prefiksów przestrzeni nazw. Prefiksy przestrzeni nazw mogą być przydatne, aby zmniejszyć liczbę naciśnięć klawiszy wymaganych podczas wprowadzania danych XML lub ułatwić odczytywanie kodu XML. Jednak prefiksy są często tylko skrótem do używania pełnej przestrzeni nazw XML i nie są wymagane w większości przypadków. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]upraszcza nazwy XML, rozwiązując wszystkie prefiksy do odpowiednich nazw XML. Prefiksy są dostępne, jeśli są wymagane przez <xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A> metodę.  
  
 W razie potrzeby można kontrolować prefiksy przestrzeni nazw. W niektórych sytuacjach, jeśli pracujesz z innymi systemami XML, takimi jak XSLT lub XAML, musisz kontrolować prefiksy przestrzeni nazw. Na przykład jeśli masz wyrażenie XPath używające prefiksów przestrzeni nazw i osadzone w arkuszu stylów XSLT, musisz upewnić się, że dokument XML jest serializowany z prefiksami przestrzeni nazw, które pasują do tych używanych w wyrażeniu XPath.  
  
### <a name="xnamespace-class"></a>Klasa XNamespace  
 <xref:System.Xml.Linq.XNamespace>reprezentuje przestrzeń nazw dla <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XAttribute> . Przestrzenie nazw są składnikiem <xref:System.Xml.Linq.XName> .  
  
### <a name="xnode-class"></a>Klasa XNode  
 <xref:System.Xml.Linq.XNode>jest klasą abstrakcyjną, która reprezentuje węzły drzewa XML. Następujące klasy pochodzą od <xref:System.Xml.Linq.XNode> klasy:  
  
- <xref:System.Xml.Linq.XText>  
  
- <xref:System.Xml.Linq.XContainer>  
  
- <xref:System.Xml.Linq.XComment>  
  
- <xref:System.Xml.Linq.XProcessingInstruction>  
  
- <xref:System.Xml.Linq.XDocumentType>  
  
### <a name="xnodedocumentordercomparer-class"></a>Klasa XNodeDocumentOrderComparer  
 <xref:System.Xml.Linq.XNodeDocumentOrderComparer>oferuje funkcje do porównywania węzłów dla ich kolejności dokumentów.  
  
### <a name="xnodeequalitycomparer-class"></a>Klasa XNodeEqualityComparer  
 <xref:System.Xml.Linq.XNodeEqualityComparer>oferuje funkcje do porównywania węzłów pod kątem równości wartości.  
  
### <a name="xobject-class"></a>Klasa XObject  
 <xref:System.Xml.Linq.XObject>jest abstrakcyjną klasą bazową <xref:System.Xml.Linq.XNode> i <xref:System.Xml.Linq.XAttribute> . Zapewnia funkcję adnotacji i zdarzeń.  
  
### <a name="xobjectchange-class"></a>Klasa XObjectChange  
 <xref:System.Xml.Linq.XObjectChange>Określa typ zdarzenia, gdy zdarzenie jest zgłaszane dla elementu <xref:System.Xml.Linq.XObject> .  
  
### <a name="xobjectchangeeventargs-class"></a>Klasa XObjectChangeEventArgs  
 <xref:System.Xml.Linq.XObjectChangeEventArgs>dostarcza dane dla <xref:System.Xml.Linq.XObject.Changing> zdarzeń i <xref:System.Xml.Linq.XObject.Changed> .  
  
### <a name="xprocessinginstruction-class"></a>Klasa XProcessingInstruction  
 <xref:System.Xml.Linq.XProcessingInstruction>reprezentuje instrukcję przetwarzania XML. Instrukcja przetwarzania komunikuje informacje z aplikacją, która przetwarza kod XML.  
  
### <a name="xtext-class"></a>Klasa XText  
 <xref:System.Xml.Linq.XText>reprezentuje węzeł tekstowy. W większości przypadków nie trzeba używać tej klasy. Ta klasa jest używana głównie do zawartości mieszanej.  
  
## <a name="see-also"></a>Zobacz też

- [Omówienie programowania LINQ to XML (Visual Basic)](linq-to-xml-programming-overview.md)
