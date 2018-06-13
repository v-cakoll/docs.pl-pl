---
title: 'Porady: przekształcanie XML za pomocą LINQ (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], transforming
- LINQ to XML [Visual Basic], transforming XML
ms.assetid: 815687f4-0bc2-4c0b-adc6-d78744aa356f
ms.openlocfilehash: 94ad5180c7921a5ace09f9161de5f275475e46d4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652964"
---
# <a name="how-to-transform-xml-by-using-linq-visual-basic"></a>Porady: przekształcanie XML za pomocą LINQ (Visual Basic)
[Literały XML](../../../../visual-basic/language-reference/xml-literals/index.md) ułatwiają Odczytaj dane XML z jednego źródła i przekształcenie go do nowego formatu XML. Można korzystać z zapytania LINQ do pobierania zawartości do transformacji lub zmieniać zawartość istniejącego dokumentu do nowego formatu XML.  
  
 Przykład, w tym temacie przekształca zawartości z dokumentu XML źródła w formacie HTML do wyświetlenia w przeglądarce.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-transform-an-xml-document"></a>Do transformacji dokumentów XML  
  
1.  W programie Visual Studio Utwórz nowy projekt Visual Basic w **aplikacji konsoli** szablonu projektu.  
  
2.  Kliknij dwukrotnie plik Module1.vb utworzone w projekcie, aby zmodyfikować kod Visual Basic. Dodaj następujący kod do `Sub Main` z `Module1` modułu. Ten kod tworzy dokument XML źródła jako <xref:System.Xml.Linq.XDocument> obiektu.  
  
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
  
     [Porady: ładowanie XML z pliku, ciągu lub strumienia](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md).  
  
3.  Po kodzie można utworzyć dokumentu XML źródła, Dodaj następujący kod, aby pobrać wszystkie \<książki > elementy z obiektu i przekształcania dokumentu HTML. Lista \<książki > elementów jest tworzona przy użyciu zapytania LINQ, która zwraca kolekcję <xref:System.Xml.Linq.XElement> obiektów zawierających przekształcone HTML. Wyrażenia osadzone umożliwia umieszczanie wartości z dokumentu źródłowego do nowego formatu XML.  
  
     Wynikowy dokument HTML jest zapisywane w pliku za pomocą <xref:System.Xml.Linq.XElement.Save%2A> metody.  
  
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
  
4.  Po `Sub Main` z `Module1`, dodać nową metodę (`Sub`) do przekształcania \<opis > węzła w określonym formacie HTML. Ta metoda jest wywoływany przez kod w poprzednim kroku i pozwala zachować format \<opis > elementów.  
  
     Ta metoda zastępuje elementy podrzędne elementu \<opis > elementu HTML. `ReplaceWith` Metoda jest używana w celu zachowania położenie elementów podrzędnych. Po przekształceniu zawartość \<opis > element znajduje się w akapitu HTML (\<p >) elementu. <xref:System.Xml.Linq.XContainer.Nodes%2A> Właściwość służy do pobierania zawartości po przekształceniu \<opis > elementu. Daje to pewność, że elementy podrzędne są uwzględniane w zawartości po przekształceniu.  
  
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
  
6.  Naciśnij klawisz F5, aby uruchomić kod. Powstałe w ten sposób zapisać dokumentu będą wyglądać w następujący sposób:  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Literały XML](../../../../visual-basic/language-reference/xml-literals/index.md)  
 [Manipulowanie XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [Instrukcje: ładowanie kodu XML z pliku, ciągu lub strumienia](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
