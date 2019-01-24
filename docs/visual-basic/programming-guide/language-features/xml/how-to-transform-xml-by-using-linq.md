---
title: 'Instrukcje: Przekształcanie XML za pomocą LINQ (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], transforming
- LINQ to XML [Visual Basic], transforming XML
ms.assetid: 815687f4-0bc2-4c0b-adc6-d78744aa356f
ms.openlocfilehash: 628af13a4cdea41ade943b69e326ec2d9abcbf1c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54536350"
---
# <a name="how-to-transform-xml-by-using-linq-visual-basic"></a>Instrukcje: Przekształcanie XML za pomocą LINQ (Visual Basic)
[Literały XML](../../../../visual-basic/language-reference/xml-literals/index.md) ułatwiają Odczytaj dane XML z jednego źródła i przekształcić je do nowego formatu XML. Możesz korzystać z zalet zapytania LINQ, aby pobrać zawartość do przekształcenia lub zmieniać zawartość istniejącego dokumentu do nowego formatu XML.  
  
 W przykładzie w tym temacie przekształca zawartość w dokumencie źródłowym XML w formacie HTML do wyświetlenia w przeglądarce.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-transform-an-xml-document"></a>Aby przekształcić dokumentu XML  
  
1.  W programie Visual Studio Utwórz nowy projekt języka Visual Basic w **aplikację Konsolową** szablonu projektu.  
  
2.  Kliknij dwukrotnie plik Module1.vb utworzone w projekcie, aby zmodyfikować kod języka Visual Basic. Dodaj następujący kod do `Sub Main` z `Module1` modułu. Ten kod tworzy dokumencie źródłowym XML jako <xref:System.Xml.Linq.XDocument> obiektu.  
  
    ```vb  
    Dim catalog =   
      <?xml version="1.0"?>  
        <Catalog>  
          <Book id="bk101">  
            <Author>Garghentini, Davide</Author>  
            <Title>XML Developer's Guide</Title>  
            <Price>44.95</Price>  
            <Description>  
              An in-depth look at creating applications  
              with <technology>XML</technology>. For   
              <audience>beginners</audience> or   
              <audience>advanced</audience> developers.  
            </Description>  
          </Book>  
          <Book id="bk331">  
            <Author>Spencer, Phil</Author>  
            <Title>Developing Applications with Visual Basic .NET</Title>  
            <Price>45.95</Price>  
            <Description>  
              Get the expert insights, practical code samples,   
              and best practices you need   
              to advance your expertise with <technology>Visual   
              Basic .NET</technology>.   
              Learn how to create faster, more reliable applications  
              based on professional,   
              pragmatic guidance by today's top <audience>developers</audience>.  
            </Description>  
          </Book>  
        </Catalog>  
    ```  
  
     [Instrukcje: Ładowanie kodu XML z pliku, ciągu lub Stream](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md).  
  
3.  Po kodzie, który można utworzyć dokumentu XML źródła, Dodaj następujący kod, aby pobrać wszystkie \<książki > elementy z obiektu i przekształca je w dokumencie HTML. Lista \<książki > elementów jest tworzona przy użyciu zapytania LINQ, które zwraca kolekcję <xref:System.Xml.Linq.XElement> obiektów, które zawierają HTML przekształcone. Wyrażenia osadzone można użyć, aby umieszczać wartości z dokumentu źródłowego do nowego formatu XML.  
  
     Wynikowy dokumentu HTML są zapisywane do pliku za pomocą <xref:System.Xml.Linq.XElement.Save%2A> metody.  
  
    ```vb  
    Dim htmlOutput =   
      <html>  
        <body>  
          <%= From book In catalog.<Catalog>.<Book>   
              Select <div>  
                       <h1><%= book.<Title>.Value %></h1>  
                       <h3><%= "By " & book.<Author>.Value %></h3>  
                        <h3><%= "Price = " & book.<Price>.Value %></h3>  
                        <h2>Description</h2>  
                        <%= TransformDescription(book.<Description>(0)) %>  
                        <hr/>  
                      </div> %>  
        </body>  
      </html>  
  
    htmlOutput.Save("BookDescription.html")  
    ```  
  
4.  Po `Sub Main` z `Module1`, Dodaj nową metodę (`Sub`) do przekształcania \<opis > węzła w określonym formacie HTML. Ta metoda jest wywoływana przez kod w poprzednim kroku i służy do zachowania format \<opis > elementy.  
  
     Ta metoda zastępuje elementy podrzędne \<opis > elementu HTML. `ReplaceWith` Metoda jest używana, aby zachować położenie elementów podrzędnych. Po przekształceniu zawartość \<opis > element znajduje się w akapicie HTML (\<p >) elementu. <xref:System.Xml.Linq.XContainer.Nodes%2A> Właściwość jest używana do pobierania zawartości po przekształceniu \<opis > element. Daje to gwarancję, że elementy podrzędne są uwzględniane w przekształconej zawartości.  
  
     Dodaj następujący kod po `Sub Main` z `Module1`.  
  
    ```vb  
    Public Function TransformDescription(ByVal desc As XElement) As XElement  
  
      ' Replace <technology> elements with <b>.  
      Dim content = (From element In desc...<technology>).ToList()  
  
      If content.Count > 0 Then  
        For i = 0 To content.Count - 1  
          content(i).ReplaceWith(<b><%= content(i).Value %></b>)  
        Next  
      End If  
  
      ' Replace <audience> elements with <i>.  
      content = (From element In desc...<audience>).ToList()  
  
      If content.Count > 0 Then  
        For i = 0 To content.Count - 1  
          content(i).ReplaceWith(<i><%= content(i).Value %></i>)  
        Next  
      End If  
  
      ' Return the updated contents of the <Description> element.  
      Return <p><%= desc.Nodes %></p>  
    End Function  
    ```  
  
5.  Zapisz zmiany.  
  
6.  Naciśnij klawisz F5, aby uruchomić kod. Wartość wynikowa zapisany dokument będzie wyglądać w następujący sposób:  
  
    ```  
    <?xml version="1.0"?>  
    <html>  
      <body>  
        <div>  
          <h1>XML Developer's Guide</h1>  
          <h3>By Garghentini, Davide</h3>  
          <h3>Price = 44.95</h3>  
          <h2>Description</h2>  
          <p>  
            An in-depth look at creating applications  
            with <b>XML</b>. For   
            <i>beginners</i> or   
            <i>advanced</i> developers.  
          </p>  
          <hr />  
        </div>  
        <div>  
          <h1>Developing Applications with Visual Basic .NET</h1>  
          <h3>By Spencer, Phil</h3>  
          <h3>Price = 45.95</h3>  
          <h2>Description</h2>  
          <p>  
            Get the expert insights, practical code   
            samples, and best practices you need   
            to advance your expertise with <b>Visual   
            Basic .NET</b>. Learn how to create faster,  
            more reliable applications based on  
            professional, pragmatic guidance by today's   
            top <i>developers</i>.  
          </p>  
          <hr />  
        </div>  
      </body>  
    </html>  
    ```  
  
## <a name="see-also"></a>Zobacz także
- [Literały XML](../../../../visual-basic/language-reference/xml-literals/index.md)
- [Manipulowanie XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [Instrukcje: Ładowanie kodu XML z pliku, ciągu lub Stream](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
