---
title: "Przegląd klasy XDocument (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 63305603-ab54-49fc-84e4-f76eecc59549
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5dcb221dadcae934c382d20a2a93149af9541db9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="xdocument-class-overview-c"></a>Przegląd klasy XDocument (C#)
W tym temacie przedstawiono <xref:System.Xml.Linq.XDocument> klasy.  
  
## <a name="overview-of-the-xdocument-class"></a>Przegląd klasy XDocument  
 <xref:System.Xml.Linq.XDocument> Klasa zawiera informacje niezbędne do prawidłowego dokumentu XML. W tym deklaracja XML przetwarzania instrukcje i komentarze.  
  
 Należy pamiętać, że należy utworzyć <xref:System.Xml.Linq.XDocument> obiekty, jeśli są wymagane określone funkcje udostępniane przez <xref:System.Xml.Linq.XDocument> klasy. W wielu sytuacjach może współpracować bezpośrednio z <xref:System.Xml.Linq.XElement>. Praca bezpośrednio z <xref:System.Xml.Linq.XElement> jest prostszy model programowania.  
  
 <xref:System.Xml.Linq.XDocument>pochodną <xref:System.Xml.Linq.XContainer>. W związku z tym może zawierać węzłów podrzędnych. Jednak <xref:System.Xml.Linq.XDocument> obiekty mogą mieć tylko jeden element podrzędny <xref:System.Xml.Linq.XElement> węzła. Ta właściwość odzwierciedla standardu XML, że może istnieć tylko jeden element główny dokumentu XML.  
  
## <a name="components-of-xdocument"></a>Składniki XDocument  
 <xref:System.Xml.Linq.XDocument> Może zawierać następujące elementy:  
  
-   Jeden <xref:System.Xml.Linq.XDeclaration> obiektu. <xref:System.Xml.Linq.XDeclaration>Umożliwia określenie odpowiednich części deklaracji XML: Wersja XML, kodowania dokumentu, oraz czy dokument XML jest autonomiczny.  
  
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
 [LINQ do XML-przegląd programowania w języku (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
