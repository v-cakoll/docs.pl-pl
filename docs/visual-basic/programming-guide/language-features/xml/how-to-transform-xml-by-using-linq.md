---
title: 'Porady: przekształcanie XML za pomocą LINQ'
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], transforming
- LINQ to XML [Visual Basic], transforming XML
ms.assetid: 815687f4-0bc2-4c0b-adc6-d78744aa356f
ms.openlocfilehash: dab394ec45567589e002b5d2ac76ec19fb0f76c6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84374885"
---
# <a name="how-to-transform-xml-by-using-linq-visual-basic"></a>Porady: przekształcanie XML za pomocą LINQ (Visual Basic)

[Literały XML](../../../language-reference/xml-literals/index.md) ułatwiają odczytywanie XML z jednego źródła i przekształcanie go w nowy format XML. Można wykorzystać zapytania LINQ do pobrania zawartości do przekształcenia lub zmiany zawartości w istniejącym dokumencie na nowy format XML.

Przykład w tym temacie przekształca zawartość dokumentu źródłowego XML do formatu HTML, który ma być wyświetlany w przeglądarce.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

### <a name="to-transform-an-xml-document"></a>Aby przekształcić dokument XML

1. W programie Visual Studio Utwórz nowy projekt Visual Basic w szablonie projektu **aplikacji konsolowej** .

2. Kliknij dwukrotnie plik Module1. vb utworzony w projekcie, aby zmodyfikować kod Visual Basic. Dodaj następujący kod do `Sub Main` `Module1` modułu. Ten kod tworzy źródłowy dokument XML jako <xref:System.Xml.Linq.XDocument> obiekt.

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

     [Instrukcje: ładowanie kodu XML z pliku, ciągu lub strumienia](how-to-load-xml-from-a-file-string-or-stream.md).

3. Po kodzie do utworzenia źródłowego dokumentu XML Dodaj następujący kod, aby pobrać wszystkie \<Book> elementy z obiektu i przekształcić je w dokument HTML. Lista \<Book> elementów jest tworzona przy użyciu zapytania LINQ, które zwraca kolekcję <xref:System.Xml.Linq.XElement> obiektów, które zawierają przekształcony kod HTML. Możesz użyć osadzonych wyrażeń, aby umieścić wartości z dokumentu źródłowego w nowym formacie XML.

     Utworzony dokument HTML jest zapisywana w pliku przy użyciu <xref:System.Xml.Linq.XElement.Save%2A> metody.

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

4. Następnie `Sub Main` `Module1` Dodaj nową metodę ( `Sub` ), aby przekształcić \<Description> węzeł w określony format HTML. Ta metoda jest wywoływana przez kod w poprzednim kroku i służy do zachowywania formatu \<Description> elementów.

     Ta metoda zastępuje elementy podrzędne \<Description> elementu kodem HTML. `ReplaceWith`Metoda jest używana do zachowywania lokalizacji elementów podrzędnych. Przekształcona zawartość \<Description> elementu jest dołączana do elementu akapitu HTML ( \<p> ). <xref:System.Xml.Linq.XContainer.Nodes%2A>Właściwość służy do pobierania przekształconej zawartości \<Description> elementu. Gwarantuje to, że elementy podrzędne zostaną uwzględnione w przekształconej zawartości.

     Dodaj poniższy kod po `Sub Main` `Module1` .

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

5. Zapisz zmiany.

6. Naciśnij klawisz F5, aby uruchomić kod. Wynikowy zapisany dokument będzie wyglądać następująco:

    ```html
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

- [Literały XML](../../../language-reference/xml-literals/index.md)
- [Manipulowanie XML w Visual Basic](manipulating-xml.md)
- [XML](index.md)
- [Porady: ładowanie XML z pliku, ciągu lub strumienia](how-to-load-xml-from-a-file-string-or-stream.md)
- [LINQ](../linq/index.md)
- [Wprowadzenie do LINQ w Visual Basic](../linq/introduction-to-linq.md)
