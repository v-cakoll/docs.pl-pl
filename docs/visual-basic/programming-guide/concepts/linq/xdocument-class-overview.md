---
title: XDocument, klasa — przegląd
ms.date: 07/20/2015
ms.assetid: 45cb7e71-196a-47da-bfe9-7a5589db1eed
ms.openlocfilehash: 90c97349006407b2eca861be31080ec17901fa5b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413235"
---
# <a name="xdocument-class-overview-visual-basic"></a>MFC — Omówienie klasy (Visual Basic)
Ten temat zawiera wprowadzenie do <xref:System.Xml.Linq.XDocument> klasy.  
  
## <a name="overview-of-the-xdocument-class"></a>Przegląd klasy XDocument  
 <xref:System.Xml.Linq.XDocument>Klasa zawiera informacje niezbędne do prawidłowego dokumentu XML. Obejmuje to deklarację XML, instrukcje przetwarzania i komentarze.  
  
 Należy pamiętać, że tylko należy utworzyć <xref:System.Xml.Linq.XDocument> obiekty, jeśli wymagane są konkretne funkcje dostarczone przez <xref:System.Xml.Linq.XDocument> klasę. W wielu przypadkach można bezpośrednio korzystać z programu <xref:System.Xml.Linq.XElement> . Praca bezpośrednio z programem <xref:System.Xml.Linq.XElement> to prostszy model programowania.  
  
 <xref:System.Xml.Linq.XDocument>pochodzi od <xref:System.Xml.Linq.XContainer> . W związku z tym może zawierać węzłów podrzędnych. Jednak <xref:System.Xml.Linq.XDocument> obiekty mogą mieć tylko jeden węzeł podrzędny <xref:System.Xml.Linq.XElement> . Odzwierciedla to standard XML, że w dokumencie XML może istnieć tylko jeden element główny.  
  
## <a name="components-of-xdocument"></a>Składniki klasy XDocument  
 <xref:System.Xml.Linq.XDocument>Może zawierać następujące elementy:  
  
- Jeden <xref:System.Xml.Linq.XDeclaration> obiekt. <xref:System.Xml.Linq.XDeclaration>umożliwia określenie odpowiednich części deklaracji XML: wersji XML, kodowania dokumentu oraz tego, czy dokument XML jest autonomiczny.  
  
- Jeden <xref:System.Xml.Linq.XElement> obiekt. Jest to główny węzeł dokumentu XML.  
  
- Dowolna liczba <xref:System.Xml.Linq.XProcessingInstruction> obiektów. Instrukcja przetwarzania komunikuje informacje z aplikacją, która przetwarza kod XML.  
  
- Dowolna liczba <xref:System.Xml.Linq.XComment> obiektów. Komentarze będą elementy równorzędne z elementem głównym. <xref:System.Xml.Linq.XComment>Obiekt nie może być pierwszym argumentem na liście, ponieważ nie jest on prawidłowy dla dokumentu XML, aby można było zacząć od komentarza.  
  
- Jeden <xref:System.Xml.Linq.XDocumentType> dla DTD.  
  
 W przypadku serializacji elementu <xref:System.Xml.Linq.XDocument> , nawet jeśli `XDocument.Declaration` jest `null` , wynik będzie miał deklarację XML, jeśli moduł zapisujący ma `Writer.Settings.OmitXmlDeclaration` ustawioną wartość `false` (wartość domyślna).  
  
 Domyślnie program [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Ustawia wersję na "1,0" i ustawia kodowanie na "UTF-8".  
  
## <a name="using-xelement-without-xdocument"></a>Korzystanie z XElement bez klasy XDocument  
 Jak wspomniano wcześniej, <xref:System.Xml.Linq.XElement> Klasa jest klasą główną w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] interfejsie programowania. W wielu przypadkach aplikacja nie będzie wymagać tworzenia dokumentu. Korzystając z <xref:System.Xml.Linq.XElement> klasy, można utworzyć drzewo XML, dodać do niego inne drzewa XML, zmodyfikować drzewo XML i zapisać.  
  
## <a name="using-xdocument"></a>Przy użyciu metody XDocument  
 Aby utworzyć obiekt <xref:System.Xml.Linq.XDocument> , użyj konstrukcji funkcjonalnej, tak jak w przypadku konstruowania <xref:System.Xml.Linq.XElement> obiektów.  
  
 Poniższy kod tworzy <xref:System.Xml.Linq.XDocument> obiekt i powiązane z nim obiekty zawarte.  
  
```vb  
Dim doc As XDocument = <?xml version="1.0" encoding="utf-8"?>  
                       <!--This is a comment.-->  
                       <?xml-stylesheet href='mystyle.css' title='Compact' type='text/css'?>  
                       <Pubs>  
                           <Book>  
                               <Title>Artifacts of Roman Civilization</Title>  
                               <Author>Moreno, Jordao</Author>  
                           </Book>  
                           <Book>  
                               <Title>Midieval Tools and Implements</Title>  
                               <Author>Gazit, Inbar</Author>  
                           </Book>  
                       </Pubs>  
                       <!--This is another comment.-->  
doc.Save("test.xml")  
```  
  
 Podczas badania pliku test. XML otrzymujesz następujące dane wyjściowe:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<!--This is a comment.-->  
<?xml-stylesheet href='mystyle.css' title='Compact' type='text/css'?>  
<Pubs>  
  <Book>  
    <Title>Artifacts of Roman Civilization</Title>  
    <Author>Moreno, Jordao</Author>  
  </Book>  
  <Book>  
    <Title>Midieval Tools and Implements</Title>  
    <Author>Gazit, Inbar</Author>  
  </Book>  
</Pubs>  
<!--This is another comment.-->  
```  
  
## <a name="see-also"></a>Zobacz też

- [Omówienie programowania LINQ to XML (Visual Basic)](linq-to-xml-programming-overview.md)
