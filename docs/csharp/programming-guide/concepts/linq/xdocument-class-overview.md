---
title: Klasa XDocument — OmówienieC#()
ms.date: 07/20/2015
ms.assetid: 63305603-ab54-49fc-84e4-f76eecc59549
ms.openlocfilehash: de49dc071d22dd77dddea29ca114663261e3edda
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590841"
---
# <a name="xdocument-class-overview-c"></a>Klasa XDocument — OmówienieC#()
Ten temat zawiera wprowadzenie <xref:System.Xml.Linq.XDocument> do klasy.  
  
## <a name="overview-of-the-xdocument-class"></a>Przegląd klasy XDocument  
 <xref:System.Xml.Linq.XDocument> Klasa zawiera informacje niezbędne do prawidłowego dokumentu XML. Obejmuje to deklarację XML, instrukcje przetwarzania i komentarze.  
  
 Należy pamiętać, że tylko należy utworzyć <xref:System.Xml.Linq.XDocument> obiekty, jeśli wymagane są konkretne funkcje dostarczone <xref:System.Xml.Linq.XDocument> przez klasę. W wielu przypadkach można bezpośrednio korzystać z <xref:System.Xml.Linq.XElement>programu. Praca bezpośrednio z <xref:System.Xml.Linq.XElement> programem to prostszy model programowania.  
  
 <xref:System.Xml.Linq.XDocument>pochodzi od <xref:System.Xml.Linq.XContainer>. W związku z tym może zawierać węzłów podrzędnych. Jednak obiekty mogą mieć tylko jeden węzeł podrzędny <xref:System.Xml.Linq.XElement>. <xref:System.Xml.Linq.XDocument> Odzwierciedla to standard XML, że w dokumencie XML może istnieć tylko jeden element główny.  
  
## <a name="components-of-xdocument"></a>Składniki klasy XDocument  
 <xref:System.Xml.Linq.XDocument> Może zawierać następujące elementy:  
  
- Jeden <xref:System.Xml.Linq.XDeclaration> obiekt. <xref:System.Xml.Linq.XDeclaration>umożliwia określenie odpowiednich części deklaracji XML: wersji XML, kodowania dokumentu oraz tego, czy dokument XML jest autonomiczny.  
  
- Jeden <xref:System.Xml.Linq.XElement> obiekt. Jest to główny węzeł dokumentu XML.  
  
- Dowolna liczba <xref:System.Xml.Linq.XProcessingInstruction> obiektów. Instrukcja przetwarzania komunikuje informacje z aplikacją, która przetwarza kod XML.  
  
- Dowolna liczba <xref:System.Xml.Linq.XComment> obiektów. Komentarze będą elementy równorzędne z elementem głównym. <xref:System.Xml.Linq.XComment> Obiekt nie może być pierwszym argumentem na liście, ponieważ nie jest on prawidłowy dla dokumentu XML, aby można było zacząć od komentarza.  
  
- Jeden <xref:System.Xml.Linq.XDocumentType> dla DTD.  
  
 W przypadku serializacji elementu <xref:System.Xml.Linq.XDocument>, nawet jeśli `XDocument.Declaration` jest `null`, wynik będzie miał deklarację `false` XML, jeśli moduł zapisujący `Writer.Settings.OmitXmlDeclaration` ma ustawioną wartość (wartość domyślna).  
  
 Domyślnie program [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ustawia wersję na "1,0" i ustawia kodowanie na "UTF-8".  
  
## <a name="using-xelement-without-xdocument"></a>Korzystanie z XElement bez klasy XDocument  
 Jak wspomniano wcześniej, <xref:System.Xml.Linq.XElement> Klasa jest klasą główną [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] w interfejsie programowania. W wielu przypadkach aplikacja nie będzie wymagać tworzenia dokumentu. Korzystając z <xref:System.Xml.Linq.XElement> klasy, można utworzyć drzewo XML, dodać do niego inne drzewa XML, zmodyfikować drzewo XML i zapisać.  
  
## <a name="using-xdocument"></a>Przy użyciu metody XDocument  
 Aby utworzyć <xref:System.Xml.Linq.XDocument>obiekt, użyj konstrukcji funkcjonalnej, tak jak w przypadku konstruowania <xref:System.Xml.Linq.XElement> obiektów.  
  
 Poniższy kod tworzy obiekt i <xref:System.Xml.Linq.XDocument> powiązane z nim obiekty zawarte.  
  
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

- [Omówienie programowania LINQ to XML (C#)](./linq-to-xml-overview.md)
