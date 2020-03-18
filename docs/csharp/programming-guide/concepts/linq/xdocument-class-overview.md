---
title: Przegląd klasy XDocument (C#)
ms.date: 07/20/2015
ms.assetid: 63305603-ab54-49fc-84e4-f76eecc59549
ms.openlocfilehash: de49dc071d22dd77dddea29ca114663261e3edda
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69590841"
---
# <a name="xdocument-class-overview-c"></a>Przegląd klasy XDocument (C#)
W tym temacie <xref:System.Xml.Linq.XDocument> przedstawiono klasę.  
  
## <a name="overview-of-the-xdocument-class"></a>Omówienie klasy XDocument  
 Klasa <xref:System.Xml.Linq.XDocument> zawiera informacje niezbędne dla prawidłowego dokumentu XML. Obejmuje to deklarację XML, instrukcje przetwarzania i komentarze.  
  
 Należy zauważyć, że <xref:System.Xml.Linq.XDocument> należy utworzyć obiekty tylko wtedy, <xref:System.Xml.Linq.XDocument> gdy wymagane są określone funkcje dostarczone przez klasę. W wielu okolicznościach można <xref:System.Xml.Linq.XElement>pracować bezpośrednio z . Praca bezpośrednio <xref:System.Xml.Linq.XElement> z jest prostszy model programowania.  
  
 <xref:System.Xml.Linq.XDocument>pochodzi z <xref:System.Xml.Linq.XContainer>. W związku z tym może zawierać węzły podrzędne. Jednak <xref:System.Xml.Linq.XDocument> obiekty mogą mieć <xref:System.Xml.Linq.XElement> tylko jeden węzeł podrzędny. Odzwierciedla to standard XML, że w dokumencie XML może znajdować się tylko jeden element główny.  
  
## <a name="components-of-xdocument"></a>Składniki XDocument  
 <xref:System.Xml.Linq.XDocument> Może zawierać następujące elementy:  
  
- Jeden <xref:System.Xml.Linq.XDeclaration> obiekt. <xref:System.Xml.Linq.XDeclaration>umożliwia określenie istotnych części deklaracji XML: wersji XML, kodowania dokumentu i tego, czy dokument XML jest autonomiczny.  
  
- Jeden <xref:System.Xml.Linq.XElement> obiekt. Jest to węzeł główny dokumentu XML.  
  
- Dowolna <xref:System.Xml.Linq.XProcessingInstruction> liczba obiektów. Instrukcja przetwarzania przekazuje informacje do aplikacji, która przetwarza XML.  
  
- Dowolna <xref:System.Xml.Linq.XComment> liczba obiektów. Komentarze będą rodzeństwem elementu głównego. Obiekt <xref:System.Xml.Linq.XComment> nie może być pierwszym argumentem na liście, ponieważ nie jest prawidłowy dla dokumentu XML, aby rozpocząć od komentarza.  
  
- Jeden <xref:System.Xml.Linq.XDocumentType> dla DTD.  
  
 Podczas serializacji <xref:System.Xml.Linq.XDocument>, nawet `XDocument.Declaration` jeśli `null`jest , dane wyjściowe będą miały `Writer.Settings.OmitXmlDeclaration` deklarację `false` XML, jeśli moduł zapisujący ustawiono (domyślnie).  
  
 Domyślnie [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ustawia wersję na "1.0" i ustawia kodowanie na "utf-8".  
  
## <a name="using-xelement-without-xdocument"></a>Korzystanie z XElement bez XDocument  
 Jak wcześniej wspomniano, <xref:System.Xml.Linq.XElement> klasa jest główną [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] klasą w interfejsie programowania. W wielu przypadkach aplikacja nie będzie wymagać utworzenia dokumentu. Za pomocą <xref:System.Xml.Linq.XElement> klasy, można utworzyć drzewo XML, dodać inne drzewa XML do niego, zmodyfikować drzewo XML i zapisać go.  
  
## <a name="using-xdocument"></a>Korzystanie z XDocument  
 Aby zbudować konstrukcję funkcjonalną, <xref:System.Xml.Linq.XDocument>tak <xref:System.Xml.Linq.XElement> jak do konstruowania obiektów.  
  
 Poniższy kod tworzy <xref:System.Xml.Linq.XDocument> obiekt i jego skojarzone zawarte obiekty.  
  
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
  
 Podczas badania pliku test.xml, otrzymasz następujące dane wyjściowe:  
  
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

- [Omówienie programowania LINQ do XML (C#)](./linq-to-xml-overview.md)
