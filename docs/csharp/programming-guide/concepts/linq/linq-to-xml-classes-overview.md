---
title: LINQ do XML-Przegląd klasy (C#)
ms.date: 07/20/2015
ms.assetid: bf666100-5392-4968-97f4-f6b9d3287d7b
ms.openlocfilehash: 619bf59c2b10cbb699f8e5b177991da9a0a2b238
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33329897"
---
# <a name="linq-to-xml-classes-overview-c"></a>LINQ do XML-Przegląd klasy (C#)
Ten temat zawiera listę [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] klas w <xref:System.Xml.Linq> przestrzeni nazw oraz krótki opis każdego z nich.  
  
## <a name="linq-to-xml-classes"></a>LINQ do XML klas  
  
### <a name="xattribute-class"></a>Klasa XAttribute  
 <xref:System.Xml.Linq.XAttribute> Reprezentuje atrybut XML. Aby uzyskać szczegółowe informacje i przykłady, zobacz [XAttribute Przegląd klasy (C#)](../../../../csharp/programming-guide/concepts/linq/xattribute-class-overview.md).  
  
### <a name="xcdata-class"></a>Klasa XCData  
 <xref:System.Xml.Linq.XCData> reprezentuje węzeł tekstowy CDATA.  
  
### <a name="xcomment-class"></a>Klasa XComment  
 <xref:System.Xml.Linq.XComment> Reprezentuje komentarz XML.  
  
### <a name="xcontainer-class"></a>Klasa XContainer  
 <xref:System.Xml.Linq.XContainer> jest to abstrakcyjna klasa podstawowa dla wszystkich węzłów, które mogą mieć węzłów podrzędnych. Następujące klasy pochodzi od <xref:System.Xml.Linq.XContainer> klasy:  
  
-   <xref:System.Xml.Linq.XElement>  
  
-   <xref:System.Xml.Linq.XDocument>  
  
### <a name="xdeclaration-class"></a>Klasa XDeclaration  
 <xref:System.Xml.Linq.XDeclaration> Reprezentuje deklaracji XML. Deklaracja XML służy do deklarowania wersji XML i kodowania dokumentu. Ponadto deklaracja XML określa, czy dokument XML jest autonomiczny. Jeśli dokument jest autonomicznym, nie ma żadnych deklaracji znaczników zewnętrznych, w zewnętrznej definicji DTD lub w jednostce parametru zewnętrzne odwołanie z podzestawu wewnętrznego.  
  
### <a name="xdocument-class"></a>Klasy XDocument  
 <xref:System.Xml.Linq.XDocument> Reprezentuje dokumentu XML. Aby uzyskać szczegółowe informacje i przykłady, zobacz [Przegląd klasy XDocument (C#)](../../../../csharp/programming-guide/concepts/linq/xdocument-class-overview.md).  
  
### <a name="xdocumenttype-class"></a>Klasa XDocumentType  
 <xref:System.Xml.Linq.XDocumentType> Reprezentuje definicja typu dokumentu XML (DTD).  
  
### <a name="xelement-class"></a>Klasy XElement — klasa  
 <xref:System.Xml.Linq.XElement> Reprezentuje XML element. Aby uzyskać szczegółowe informacje i przykłady, zobacz [klasy XElement Przegląd klasy (C#)](../../../../csharp/programming-guide/concepts/linq/xelement-class-overview.md).  
  
### <a name="xname-class"></a>Klasa XName  
 <xref:System.Xml.Linq.XName> reprezentuje nazwy elementów (<xref:System.Xml.Linq.XElement>) i atrybuty (<xref:System.Xml.Linq.XAttribute>). Aby uzyskać szczegółowe informacje i przykłady, zobacz [Przegląd klasy XDocument (C#)](../../../../csharp/programming-guide/concepts/linq/xdocument-class-overview.md).  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Umożliwia nazw XML równie proste, jak to możliwe. Ze względu na złożoność nazwy XML są często uważane zaawansowane tematu w kodzie XML. Można przypuszczać, że ta złożoności pochodzi nie z przestrzeni nazw, deweloperom używany regularnie programowania, ale z prefiksy przestrzeni nazw. Prefiksy Namespace może być przydatna, aby zmniejszyć naciśnięcia klawiszy wymagane podczas wprowadzania danych XML lub aby ułatwić XML. Jednak prefiksy są często tylko skrót przy użyciu pełnego przestrzeni nazw XML i nie są wymagane w większości przypadków. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] upraszcza nazw XML, rozwiązując wszystkie prefiksy do ich odpowiednich przestrzeni nazw XML. Prefiksy są dostępne, jeśli są wymagane przez <xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A> metody.  
  
 Jest to możliwe, jeśli to konieczne, aby formant prefiksy przestrzeni nazw. W niektórych sytuacjach podczas pracy z innymi systemami XML, takiego jak XSLT lub XAML, należy kontrolować prefiksy przestrzeni nazw. Na przykład jeśli wyrażenie XPath, która korzysta z prefiksy przestrzeni nazw i jest osadzony w arkusz stylów XSLT, należy się upewnić, że dokument XML jest serializowany z prefiksy przestrzeni nazw, które pasują do wyrażenia XPath.  
  
### <a name="xnamespace-class"></a>Klasa XNamespace  
 <xref:System.Xml.Linq.XNamespace> reprezentuje obszar nazw dla <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XAttribute>. Przestrzenie nazw są składnika <xref:System.Xml.Linq.XName>.  
  
### <a name="xnode-class"></a>Klasa XNode  
 <xref:System.Xml.Linq.XNode> jest klasą abstrakcyjną, reprezentujący węzły drzewa XML. Następujące klasy pochodzi od <xref:System.Xml.Linq.XNode> klasy:  
  
-   <xref:System.Xml.Linq.XText>  
  
-   <xref:System.Xml.Linq.XContainer>  
  
-   <xref:System.Xml.Linq.XComment>  
  
-   <xref:System.Xml.Linq.XProcessingInstruction>  
  
-   <xref:System.Xml.Linq.XDocumentType>  
  
### <a name="xnodedocumentordercomparer-class"></a>Klasa XNodeDocumentOrderComparer  
 <xref:System.Xml.Linq.XNodeDocumentOrderComparer> zapewnia funkcje do porównania węzły ich kolejności dokumentu.  
  
### <a name="xnodeequalitycomparer-class"></a>Klasa XNodeEqualityComparer  
 <xref:System.Xml.Linq.XNodeEqualityComparer> zapewnia funkcje do porównania węzły równości wartości.  
  
### <a name="xobject-class"></a>Klasa XObject  
 <xref:System.Xml.Linq.XObject> jest abstrakcyjna klasa podstawowa dla <xref:System.Xml.Linq.XNode> i <xref:System.Xml.Linq.XAttribute>. Zawiera funkcję adnotacji i zdarzeń.  
  
### <a name="xobjectchange-class"></a>Klasa XObjectChange  
 <xref:System.Xml.Linq.XObjectChange> Określa typ zdarzenia, gdy zdarzenie jest wywoływane dla <xref:System.Xml.Linq.XObject>.  
  
### <a name="xobjectchangeeventargs-class"></a>Klasa XObjectChangeEventArgs  
 <xref:System.Xml.Linq.XObjectChangeEventArgs> udostępnia dane dla <xref:System.Xml.Linq.XObject.Changing> i <xref:System.Xml.Linq.XObject.Changed> zdarzenia.  
  
### <a name="xprocessinginstruction-class"></a>Klasa XProcessingInstruction  
 <xref:System.Xml.Linq.XProcessingInstruction> Reprezentuje instrukcji przetwarzania XML. Instrukcja przetwarzania komunikuje się informacji do aplikacji, która przetwarza dane XML.  
  
### <a name="xtext-class"></a>Klasa XText  
 <xref:System.Xml.Linq.XText> Reprezentuje węzeł tekstowy. W większości przypadków nie trzeba używać tej klasy. Ta klasa jest używana głównie dla zawartości mieszanej.  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ do XML-przegląd programowania w języku (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
