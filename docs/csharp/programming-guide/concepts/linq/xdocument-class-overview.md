---
title: XDocument, klasa — Przegląd (C#)
ms.date: 07/20/2015
ms.assetid: 63305603-ab54-49fc-84e4-f76eecc59549
ms.openlocfilehash: 0d182593cfedd30042c4e3a5d776bb00ce267ff7
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43504861"
---
# <a name="xdocument-class-overview-c"></a>XDocument, klasa — Przegląd (C#)
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
  
```csharp  
XDocument d = new XDocument(  
    new XComment("This is a comment."),  
    new XProcessingInstruction("xml-stylesheet",  
        "href='mystyle.css' title='Compact' type='text/css'"),  
    new XElement("Pubs",  
        new XElement("Book",  
            new XElement("Title", "Artifacts of Roman Civilization"),  
            new XElement("Author", "Moreno, Jordao")  
        ),  
        new XElement("Book",  
            new XElement("Title", "Midieval Tools and Implements"),  
            new XElement("Author", "Gazit, Inbar")  
        )  
    ),  
    new XComment("This is another comment.")  
);  
d.Declaration = new XDeclaration("1.0", "utf-8", "true");  
Console.WriteLine(d);  
  
d.Save("test.xml");  
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
  
## <a name="see-also"></a>Zobacz też

- [LINQ to XML — przegląd programowania (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
