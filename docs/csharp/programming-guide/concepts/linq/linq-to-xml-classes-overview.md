---
title: LINQ to XML — Przegląd klas (C#)
ms.date: 07/20/2015
ms.assetid: bf666100-5392-4968-97f4-f6b9d3287d7b
ms.openlocfilehash: f93e3a791bfd56095df12ebf070f72540a8b21dc
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64597061"
---
# <a name="linq-to-xml-classes-overview-c"></a>LINQ to XML — Przegląd klas (C#)
Ten temat zawiera listę [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] klas w <xref:System.Xml.Linq> przestrzeni nazw oraz krótki opis każdego z nich.  
  
## <a name="linq-to-xml-classes"></a>LINQ to XML klasy  
  
### <a name="xattribute-class"></a>Klasy XAttribute  
 <xref:System.Xml.Linq.XAttribute> reprezentuje atrybut XML. Aby uzyskać szczegółowe informacje i przykłady, zobacz [XAttribute klasa — Przegląd (C#)](../../../../csharp/programming-guide/concepts/linq/xattribute-class-overview.md).  
  
### <a name="xcdata-class"></a>XCData Class  
 <xref:System.Xml.Linq.XCData> reprezentuje węzeł tekstowy CDATA.  
  
### <a name="xcomment-class"></a>Klasa XComment  
 <xref:System.Xml.Linq.XComment> reprezentuje komentarz XML.  
  
### <a name="xcontainer-class"></a>Klasa XContainer  
 <xref:System.Xml.Linq.XContainer> jest abstrakcyjna klasa bazowa dla wszystkich węzłów, które mogą mieć węzłów podrzędnych. Następujące klasy pochodzić od <xref:System.Xml.Linq.XContainer> klasy:  
  
- <xref:System.Xml.Linq.XElement>  
  
- <xref:System.Xml.Linq.XDocument>  
  
### <a name="xdeclaration-class"></a>Klasa XDeclaration  
 <xref:System.Xml.Linq.XDeclaration> reprezentuje deklaracji XML. Deklaracja XML jest używane do deklarowania wersji XML i kodowania dokumentu. Ponadto deklaracja XML określa, czy dokument XML jest autonomiczny. Dokument jest autonomiczna, czy nie deklaracje zewnętrzne znaczników w zewnętrznej definicji DTD lub w jednostce parametru zewnętrznych przywoływany w podzestawie wewnętrznym.  
  
### <a name="xdocument-class"></a>XDocument, klasa  
 <xref:System.Xml.Linq.XDocument> Reprezentuje dokumentu XML. Aby uzyskać szczegółowe informacje i przykłady, zobacz [Przegląd klasy XDocument (C#)](../../../../csharp/programming-guide/concepts/linq/xdocument-class-overview.md).  
  
### <a name="xdocumenttype-class"></a>Klasa XDocumentType  
 <xref:System.Xml.Linq.XDocumentType> reprezentuje XML dokumentu Type Definition (DTD).  
  
### <a name="xelement-class"></a>Klasy XElement  
 <xref:System.Xml.Linq.XElement> Reprezentuje XML element. Aby uzyskać szczegółowe informacje i przykłady, zobacz [Przegląd klasy XElement (C#)](../../../../csharp/programming-guide/concepts/linq/xelement-class-overview.md).  
  
### <a name="xname-class"></a>Klasa XName  
 <xref:System.Xml.Linq.XName> reprezentuje nazwy elementów (<xref:System.Xml.Linq.XElement>) i atrybuty (<xref:System.Xml.Linq.XAttribute>). Aby uzyskać szczegółowe informacje i przykłady, zobacz [Przegląd klasy XDocument (C#)](../../../../csharp/programming-guide/concepts/linq/xdocument-class-overview.md).  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zaprojektowaną do podejmowania nazwy XML jest tak proste, jak to możliwe. Z powodu ich złożoności nazwy XML są często uznawane za zaawansowanych tematów, w formacie XML. Można przypuszczać, że tę złożoność pochodzi spoza przestrzeni nazw, które deweloperzy regularnie używane w programowaniu, ale z prefiksy przestrzeni nazw. Prefiksy Namespace może być przydatne, aby zmniejszyć naciśnięć klawiszy wymagany podczas wprowadzania danych XML lub była łatwiejsza do odczytania XML. Jednak prefiksy są często po prostu skrót do usługi za pomocą pełnego przestrzeni nazw XML i nie są wymagane w większości przypadków. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] upraszcza nazw XML, rozwiązując wszystkie prefiksy do ich odpowiednich przestrzeni nazw XML. Prefiksy są dostępne, jeśli są wymagane, za pośrednictwem <xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A> metody.  
  
 Jest to możliwe, jeśli to konieczne, aby kontrolka prefiksy przestrzeni nazw. W pewnych okolicznościach Jeśli pracujesz z innymi systemami XML, takich jak XSLT lub XAML, musisz kontrolowanie prefiksów przestrzeni nazw. Na przykład jeśli wyrażenie XPath, który używa prefiksy przestrzeni nazw i jest osadzony w arkusz stylów XSLT, należy się upewnić, że dokument XML jest serializowana z prefiksy przestrzeni nazw, które pasują do terminów używanych w wyrażenie XPath.  
  
### <a name="xnamespace-class"></a>Klasa XNamespace  
 <xref:System.Xml.Linq.XNamespace> reprezentuje obszar nazw dla <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XAttribute>. Przestrzenie nazw są składnikiem <xref:System.Xml.Linq.XName>.  
  
### <a name="xnode-class"></a>Klasa XNode  
 <xref:System.Xml.Linq.XNode> jest klasą abstrakcyjną, która reprezentuje węzły drzewa XML. Następujące klasy pochodzić od <xref:System.Xml.Linq.XNode> klasy:  
  
- <xref:System.Xml.Linq.XText>  
  
- <xref:System.Xml.Linq.XContainer>  
  
- <xref:System.Xml.Linq.XComment>  
  
- <xref:System.Xml.Linq.XProcessingInstruction>  
  
- <xref:System.Xml.Linq.XDocumentType>  
  
### <a name="xnodedocumentordercomparer-class"></a>XNodeDocumentOrderComparer Class  
 <xref:System.Xml.Linq.XNodeDocumentOrderComparer> oferuje funkcje, aby porównać węzłów w celu ich kolejności dokumentu.  
  
### <a name="xnodeequalitycomparer-class"></a>XNodeEqualityComparer Class  
 <xref:System.Xml.Linq.XNodeEqualityComparer> oferuje funkcje, aby porównać węzłów na równoważność wartości.  
  
### <a name="xobject-class"></a>XObject Class  
 <xref:System.Xml.Linq.XObject> jest abstrakcyjna klasa bazowa <xref:System.Xml.Linq.XNode> i <xref:System.Xml.Linq.XAttribute>. Zapewnia funkcje adnotacji i zdarzeń.  
  
### <a name="xobjectchange-class"></a>Klasa XObjectChange  
 <xref:System.Xml.Linq.XObjectChange> Określa typ zdarzenia, gdy zdarzenie jest wywoływane dla <xref:System.Xml.Linq.XObject>.  
  
### <a name="xobjectchangeeventargs-class"></a>XObjectChangeEventArgs Class  
 <xref:System.Xml.Linq.XObjectChangeEventArgs> udostępnia dane dla <xref:System.Xml.Linq.XObject.Changing> i <xref:System.Xml.Linq.XObject.Changed> zdarzenia.  
  
### <a name="xprocessinginstruction-class"></a>Klasa XProcessingInstruction  
 <xref:System.Xml.Linq.XProcessingInstruction> reprezentuje instrukcji przetwarzania XML. Instrukcja przetwarzania komunikuje się informacji do aplikacji, która przetwarza dane XML.  
  
### <a name="xtext-class"></a>Klasa XText  
 <xref:System.Xml.Linq.XText> reprezentuje węzeł tekstowy. W większości przypadków nie trzeba używać tej klasy. Ta klasa służy przede wszystkim dla zawartości mieszanej.  
  
## <a name="see-also"></a>Zobacz także

- [LINQ to XML — przegląd programowania (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
