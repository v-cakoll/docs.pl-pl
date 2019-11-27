---
title: XDocument, klasa — przegląd
ms.date: 07/20/2015
ms.assetid: 45cb7e71-196a-47da-bfe9-7a5589db1eed
ms.openlocfilehash: cbc1ccca53978da07f31c0ba7e54eca9f06b0e72
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349287"
---
# <a name="xdocument-class-overview-visual-basic"></a>MFC — Omówienie klasy (Visual Basic)
Ten temat zawiera wprowadzenie do klasy <xref:System.Xml.Linq.XDocument>.  
  
## <a name="overview-of-the-xdocument-class"></a>Przegląd klasy XDocument  
 Klasa <xref:System.Xml.Linq.XDocument> zawiera informacje niezbędne do prawidłowego dokumentu XML. Obejmuje to deklarację XML, instrukcje przetwarzania i komentarze.  
  
 Należy pamiętać, że należy tylko utworzyć obiekty <xref:System.Xml.Linq.XDocument>, jeśli potrzebujesz określonych funkcji dostarczonych przez klasę <xref:System.Xml.Linq.XDocument>. W wielu przypadkach można bezpośrednio korzystać z <xref:System.Xml.Linq.XElement>. Praca bezpośrednio z <xref:System.Xml.Linq.XElement> jest prostszym modelem programowania.  
  
 <xref:System.Xml.Linq.XDocument> pochodzi od <xref:System.Xml.Linq.XContainer>. W związku z tym może zawierać węzłów podrzędnych. Jednak obiekty <xref:System.Xml.Linq.XDocument> mogą mieć tylko jeden węzeł podrzędny <xref:System.Xml.Linq.XElement>. Odzwierciedla to standard XML, że w dokumencie XML może istnieć tylko jeden element główny.  
  
## <a name="components-of-xdocument"></a>Składniki klasy XDocument  
 <xref:System.Xml.Linq.XDocument> może zawierać następujące elementy:  
  
- Jeden <xref:System.Xml.Linq.XDeclaration> obiektu. <xref:System.Xml.Linq.XDeclaration> umożliwia określenie odpowiednich części deklaracji XML: wersji XML, kodowania dokumentu oraz tego, czy dokument XML jest autonomiczny.  
  
- Jeden <xref:System.Xml.Linq.XElement> obiektu. Jest to główny węzeł dokumentu XML.  
  
- Dowolna liczba obiektów <xref:System.Xml.Linq.XProcessingInstruction>. Instrukcja przetwarzania komunikuje informacje z aplikacją, która przetwarza kod XML.  
  
- Dowolna liczba obiektów <xref:System.Xml.Linq.XComment>. Komentarze będą elementy równorzędne z elementem głównym. Obiekt <xref:System.Xml.Linq.XComment> nie może być pierwszym argumentem na liście, ponieważ nie jest on prawidłowy dla dokumentu XML, aby można było zacząć od komentarza.  
  
- Jeden <xref:System.Xml.Linq.XDocumentType> DTD.  
  
 Podczas serializacji <xref:System.Xml.Linq.XDocument>, nawet jeśli `XDocument.Declaration` jest `null`, dane wyjściowe będą zawierały deklarację XML, jeśli składnik zapisywania ma `Writer.Settings.OmitXmlDeclaration` ustawione na `false` (wartość domyślna).  
  
 Domyślnie program [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ustawia wersję na "1,0" i ustawia kodowanie na "UTF-8".  
  
## <a name="using-xelement-without-xdocument"></a>Korzystanie z XElement bez klasy XDocument  
 Jak wspomniano wcześniej, Klasa <xref:System.Xml.Linq.XElement> jest klasą główną w interfejsie programowania [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]. W wielu przypadkach aplikacja nie będzie wymagać tworzenia dokumentu. Korzystając z klasy <xref:System.Xml.Linq.XElement>, można utworzyć drzewo XML, dodać do niego inne drzewa XML, zmodyfikować drzewo XML i zapisać.  
  
## <a name="using-xdocument"></a>Przy użyciu metody XDocument  
 Aby skonstruować <xref:System.Xml.Linq.XDocument>, użyj konstrukcji funkcjonalnej, tak jak w przypadku konstruowania obiektów <xref:System.Xml.Linq.XElement>.  
  
 Poniższy kod tworzy obiekt <xref:System.Xml.Linq.XDocument> i jego skojarzone zawarte obiekty.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Omówienie programowania LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
