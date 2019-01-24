---
title: XDocument, klasa — Przegląd (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 45cb7e71-196a-47da-bfe9-7a5589db1eed
ms.openlocfilehash: 99a219087afdc097b62822ff290f61b96fb12b22
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54653726"
---
# <a name="xdocument-class-overview-visual-basic"></a>XDocument, klasa — Przegląd (Visual Basic)
W tym temacie przedstawiono <xref:System.Xml.Linq.XDocument> klasy.  
  
## <a name="overview-of-the-xdocument-class"></a>Omówienie XDocument, klasa  
 <xref:System.Xml.Linq.XDocument> Klasa zawiera informacje niezbędne do prawidłowy dokument XML. Dotyczy to również deklaracji XML, takich jak przetwarzanie instrukcji i komentarze.  
  
 Należy zauważyć, że trzeba utworzyć <xref:System.Xml.Linq.XDocument> obiekty, jeśli potrzebujesz określonej funkcje udostępniane przez <xref:System.Xml.Linq.XDocument> klasy. W wielu sytuacjach może współpracować bezpośrednio z <xref:System.Xml.Linq.XElement>. Praca bezpośrednio z <xref:System.Xml.Linq.XElement> jest prostsze modelu programowania.  
  
 <xref:System.Xml.Linq.XDocument> pochodzi od klasy <xref:System.Xml.Linq.XContainer>. W związku z tym może zawierać węzłów podrzędnych. Jednak <xref:System.Xml.Linq.XDocument> obiekty mogą mieć tylko jeden element podrzędny <xref:System.Xml.Linq.XElement> węzła. Odzwierciedla standardu XML, że może istnieć tylko jeden element główny dokumentu XML.  
  
## <a name="components-of-xdocument"></a>Składniki XDocument  
 <xref:System.Xml.Linq.XDocument> Może zawierać następujące elementy:  
  
-   Jeden <xref:System.Xml.Linq.XDeclaration> obiektu. <xref:System.Xml.Linq.XDeclaration> można określić odpowiednie części deklaracji XML: Wersja XML, kodowania dokumentu, oraz czy dokument XML jest autonomicznym.  
  
-   Jeden <xref:System.Xml.Linq.XElement> obiektu. Jest to węzeł główny dokumentu XML.  
  
-   Dowolną liczbę <xref:System.Xml.Linq.XProcessingInstruction> obiektów. Instrukcja przetwarzania komunikuje się informacji do aplikacji, która przetwarza dane XML.  
  
-   Dowolną liczbę <xref:System.Xml.Linq.XComment> obiektów. Komentarze będą powiązane z elementem głównym. <xref:System.Xml.Linq.XComment> Obiekt nie może być pierwszy argument na liście, ponieważ nie jest prawidłowy dla dokumentu XML, można uruchomić z komentarzem.  
  
-   Jeden <xref:System.Xml.Linq.XDocumentType> DTD.  
  
 Podczas serializacji <xref:System.Xml.Linq.XDocument>, nawet jeśli `XDocument.Declaration` jest `null`, dane wyjściowe będą mieć deklaracji XML, jeśli moduł zapisujący `Writer.Settings.OmitXmlDeclaration` równa `false` (ustawienie domyślne).  
  
 Domyślnie [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ustawia wersji "1.0" i ustawia kodowanie "utf-8".  
  
## <a name="using-xelement-without-xdocument"></a>Za pomocą klasy XElement bez klasy XDocument  
 Jak wcześniej wspomniano, <xref:System.Xml.Linq.XElement> klasa jest klasą głównego w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] interfejs programowania. W wielu przypadkach, Twoja aplikacja nie będzie wymagać tworzenia dokumentu. Za pomocą <xref:System.Xml.Linq.XElement> klasy, można utworzyć drzewa XML, dodać inne drzew XML do niego, modyfikowanie drzewa XML i zapisz go.  
  
## <a name="using-xdocument"></a>Za pomocą klasy XDocument  
 Do konstruowania <xref:System.Xml.Linq.XDocument>, użyj konstrukcja funkcjonalna tak samo, jak możesz zrobić, aby skonstruować <xref:System.Xml.Linq.XElement> obiektów.  
  
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
  
 Podczas badania test.xml pliku możesz uzyskać następujące wyniki:  
  
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
- [LINQ to XML — przegląd programowania (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
