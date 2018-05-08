---
title: Przegląd klasy XDocument (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 45cb7e71-196a-47da-bfe9-7a5589db1eed
ms.openlocfilehash: 98ab095d67add2375eaf912ade71114c022b2ebb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="xdocument-class-overview-visual-basic"></a>Przegląd klasy XDocument (Visual Basic)
W tym temacie przedstawiono <xref:System.Xml.Linq.XDocument> klasy.  
  
## <a name="overview-of-the-xdocument-class"></a>Przegląd klasy XDocument  
 <xref:System.Xml.Linq.XDocument> Klasa zawiera informacje niezbędne do prawidłowego dokumentu XML. W tym deklaracja XML przetwarzania instrukcje i komentarze.  
  
 Należy pamiętać, że należy utworzyć <xref:System.Xml.Linq.XDocument> obiekty, jeśli są wymagane określone funkcje udostępniane przez <xref:System.Xml.Linq.XDocument> klasy. W wielu sytuacjach może współpracować bezpośrednio z <xref:System.Xml.Linq.XElement>. Praca bezpośrednio z <xref:System.Xml.Linq.XElement> jest prostszy model programowania.  
  
 <xref:System.Xml.Linq.XDocument> pochodną <xref:System.Xml.Linq.XContainer>. W związku z tym może zawierać węzłów podrzędnych. Jednak <xref:System.Xml.Linq.XDocument> obiekty mogą mieć tylko jeden element podrzędny <xref:System.Xml.Linq.XElement> węzła. Ta właściwość odzwierciedla standardu XML, że może istnieć tylko jeden element główny dokumentu XML.  
  
## <a name="components-of-xdocument"></a>Składniki XDocument  
 <xref:System.Xml.Linq.XDocument> Może zawierać następujące elementy:  
  
-   Jeden <xref:System.Xml.Linq.XDeclaration> obiektu. <xref:System.Xml.Linq.XDeclaration> Umożliwia określenie odpowiednich części deklaracji XML: Wersja XML, kodowania dokumentu, oraz czy dokument XML jest autonomiczny.  
  
-   Jeden <xref:System.Xml.Linq.XElement> obiektu. To jest węzeł główny dokumentu XML.  
  
-   Dowolną liczbę <xref:System.Xml.Linq.XProcessingInstruction> obiektów. Instrukcja przetwarzania komunikuje się informacji do aplikacji, która przetwarza dane XML.  
  
-   Dowolną liczbę <xref:System.Xml.Linq.XComment> obiektów. Komentarze będzie elementów równorzędnych do elementu głównego. <xref:System.Xml.Linq.XComment> Obiekt nie może być pierwszego argumentu na liście, ponieważ nie jest prawidłowa dla dokumentu XML można uruchomić w komentarzu.  
  
-   Jeden <xref:System.Xml.Linq.XDocumentType> dla definicji DTD.  
  
 Podczas serializacji <xref:System.Xml.Linq.XDocument>, nawet jeśli `XDocument.Declaration` jest `null`, dane wyjściowe będą miały deklaracja XML, jeśli moduł zapisujący `Writer.Settings.OmitXmlDeclaration` ustawioną `false` (ustawienie domyślne).  
  
 Domyślnie [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ustawienie wersji "1.0", a kodowanie "utf-8".  
  
## <a name="using-xelement-without-xdocument"></a>Przy użyciu klasy XElement bez klasy XDocument  
 Jak wcześniej wspomniano, <xref:System.Xml.Linq.XElement> klasy jest główna klasa w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] interfejsu programowania. W wielu przypadkach aplikacji nie będzie wymagać tworzenia dokumentu. Za pomocą <xref:System.Xml.Linq.XElement> klasy, można Utwórz drzewo XML, Dodaj do niej inne drzewa XML, zmodyfikuj drzewa XML i zapisz go.  
  
## <a name="using-xdocument"></a>Przy użyciu klasy XDocument  
 Aby utworzyć <xref:System.Xml.Linq.XDocument>, użyj konstrukcji funkcjonalności, tak samo, jak należy utworzyć <xref:System.Xml.Linq.XElement> obiektów.  
  
 Poniższy kod tworzy <xref:System.Xml.Linq.XDocument> obiekt i jego skojarzony zawarte obiekty.  
  
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
  
 Po sprawdzeniu test.xml plików można uzyskać następujące dane wyjściowe:  
  
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
 [LINQ do programowania w języku XML-Przegląd (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
