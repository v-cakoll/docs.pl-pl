---
title: 'Porady: modyfikowanie literałów XML'
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], Value
- XML literals [Visual Basic]
- XML literals [Visual Basic], modifying
ms.assetid: 4e864522-a37a-43a2-8236-af80277c5482
ms.openlocfilehash: a2ac2e9802d4c8ab522bb430d15cce5616430437
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84374904"
---
# <a name="how-to-modify-xml-literals-visual-basic"></a>Porady: modyfikowanie literałów XML (Visual Basic)

Visual Basic zapewnia wygodny sposób modyfikacji literałów XML. Można dodawać lub usuwać elementy i atrybuty, a także zastąpić istniejący element nowym elementem XML. Ten temat zawiera kilka przykładów modyfikacji istniejącego literału XML.

### <a name="to-modify-the-value-of-an-xml-literal"></a>Aby zmodyfikować wartość literału XML

1. Aby zmodyfikować wartość literału XML, Uzyskaj odwołanie do literału XML i ustaw `Value` Właściwość na żądaną wartość.

    Poniższy przykład kodu aktualizuje wartość wszystkich \<Price> elementów w dokumencie XML.

    [!code-vb[VbXmlSamples2#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#4)]

    Poniżej przedstawiono przykładowy źródłowy kod XML i zmodyfikowany kod XML z tego przykładu kodu.

    Źródłowy kod XML:

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book>
    </Catalog>
    ```

    Zmodyfikowano kod XML:

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>47.20</Price>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>48.25</Price>
      </Book>
    </Catalog>
    ```

    > [!NOTE]
    > `Value`Właściwość odwołuje się do pierwszego elementu XML w kolekcji. Jeśli istnieje więcej niż jeden element o tej samej nazwie w kolekcji, ustawienie `Value` właściwości dotyczy tylko pierwszego elementu w kolekcji.

### <a name="to-add-an-attribute-to-an-xml-literal"></a>Aby dodać atrybut do literału XML

1. Aby dodać atrybut do literału XML, najpierw Uzyskaj odwołanie do literału XML. Następnie można dodać atrybut, dodając nową właściwość osi atrybutu XML. Można również dodać nowy <xref:System.Xml.Linq.XAttribute> obiekt do literału XML przy użyciu <xref:System.Xml.Linq.XContainer.Add%2A> metody. W poniższym przykładzie przedstawiono obie opcje.

    [!code-vb[VbXmlSamples2#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#5)]

    Poniżej przedstawiono przykładowy źródłowy kod XML i zmodyfikowany kod XML z tego przykładu kodu.

    Źródłowy kod XML:

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" >
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book>
    </Catalog>
    ```

    Zmodyfikowano kod XML:

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" genre="Computer" editorEmail="someone@example.com">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk331" genre="Computer" editorEmail="someone@example.com">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book>
    </Catalog>
    ```

    Aby uzyskać więcej informacji na temat właściwości osi atrybutu XML, zobacz [Właściwość osi atrybutu XML](../../../language-reference/xml-axis/xml-attribute-axis-property.md).

### <a name="to-add-an-element-to-an-xml-literal"></a>Aby dodać element do literału XML

1. Aby dodać element do literału XML, najpierw Uzyskaj odwołanie do literału XML. Następnie można dodać nowy <xref:System.Xml.Linq.XElement> obiekt jako ostatni element podrzędny elementu przy użyciu <xref:System.Xml.Linq.XContainer.Add%2A> metody. Nowy obiekt można dodać <xref:System.Xml.Linq.XElement> jako pierwszy podelement przy użyciu <xref:System.Xml.Linq.XContainer.AddFirst%2A> metody.

    Aby dodać nowy element w określonej lokalizacji względem innych elementów podrzędnych, najpierw Uzyskaj odwołanie do sąsiadującego elementu podrzędnego. Następnie można dodać nowy <xref:System.Xml.Linq.XElement> obiekt przed sąsiednim podelementem za pomocą <xref:System.Xml.Linq.XNode.AddBeforeSelf%2A> metody. Możesz również dodać nowy <xref:System.Xml.Linq.XElement> obiekt po sąsiednim podelemencie przy użyciu <xref:System.Xml.Linq.XNode.AddAfterSelf%2A> metody.

    W poniższym przykładzie przedstawiono przykłady poszczególnych technik.

    [!code-vb[VbXmlSamples2#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#6)]

    Poniżej przedstawiono przykładowy źródłowy kod XML i zmodyfikowany kod XML z tego przykładu kodu.

    Źródłowy kod XML:

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" >
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book>
    </Catalog>
    ```

    Zmodyfikowano kod XML:

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" >
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk000"></Book>
      <Book id="bk331">
        <Publisher>Microsoft Press</Publisher>
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
        <PublishDate>2005-2-14</PublishDate>
      </Book>
      <Book id="bk999"></Book>
    </Catalog>
    ```

### <a name="to-remove-an-element-or-attribute-from-an-xml-literal"></a>Aby usunąć element lub atrybut z literału XML

1. Aby usunąć element lub atrybut z literału XML, Uzyskaj odwołanie do elementu lub atrybutu i Wywołaj `Remove` metodę, jak pokazano w poniższym przykładzie.

    [!code-vb[VbXmlSamples2#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#7)]

    Poniżej przedstawiono przykładowy źródłowy kod XML i zmodyfikowany kod XML z tego przykładu kodu.

    Źródłowy kod XML:

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" genre="Computer" editorEmail="someone@example.com">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk000"></Book>
      <Book id="bk331" genre="Computer" editorEmail="someone@example.com">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book>
      <Book id="bk999"></Book>
    </Catalog>
    ```

    Zmodyfikowano kod XML:

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" editorEmail="someone@example.com">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk000"></Book>
      <Book id="bk331" editorEmail="someone@example.com">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book></Catalog>
    ```

    Aby usunąć wszystkie elementy lub atrybuty z literału XML, Uzyskaj odwołanie do literału XML i Wywołaj <xref:System.Xml.Linq.XElement.RemoveAll%2A> metodę.

### <a name="to-modify-an-xml-literal"></a>Aby zmodyfikować literał XML

1. Aby zmienić nazwę elementu XML, najpierw Uzyskaj odwołanie do elementu. Następnie można utworzyć nowy <xref:System.Xml.Linq.XElement> obiekt, który ma nową nazwę i przekazać nowy <xref:System.Xml.Linq.XElement> obiekt do <xref:System.Xml.Linq.XNode.ReplaceWith%2A> metody istniejącego <xref:System.Xml.Linq.XElement> obiektu.

    Jeśli zastępowany element ma elementy podrzędne, które muszą zostać zachowane, ustaw wartość nowego <xref:System.Xml.Linq.XElement> obiektu na <xref:System.Xml.Linq.XContainer.Nodes%2A> Właściwość istniejącego elementu. Spowoduje to ustawienie wartości nowego elementu na wewnętrzny kod XML istniejącego elementu. W przeciwnym razie można ustawić wartość nowego elementu na `Value` Właściwość istniejącego elementu.

    Poniższy przykład kodu zastępuje wszystkie \<Description> elementy \<Abstract> elementem. Zawartość \<Description> elementu jest zachowywana w nowym \<Abstract> elemencie przy użyciu <xref:System.Xml.Linq.XContainer.Nodes%2A> właściwości \<Description> <xref:System.Xml.Linq.XElement> obiektu.

    [!code-vb[VbXmlSamples2#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#8)]

    Poniżej przedstawiono przykładowy źródłowy kod XML i zmodyfikowany kod XML z tego przykładu kodu.

    Źródłowy kod XML:

    ```xml
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
          Get the expert insights, practical code samples, and best
          practices you need to advance your expertise with
          <technology>Visual Basic .NET</technology>.
          Learn how to create faster, more reliable applications
          based on professional, pragmatic guidance by today's top
          <audience>developers</audience>.
        </Description>
      </Book>
    </Catalog>
    ```

    Zmodyfikowano kod XML:

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <MSRP>44.95</MSRP>    <Abstract>
          An in-depth look at creating applications
          with <technology>XML</technology>. For
          <audience>beginners</audience> or
          <audience>advanced</audience> developers.
        </Abstract>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <MSRP>45.95</MSRP>    <Abstract>
          Get the expert insights, practical code samples, and best
          practices you need to advance your expertise with
          <technology>Visual Basic .NET</technology>.
          Learn how to create faster, more reliable applications
          based on professional, pragmatic guidance by today's top
          <audience>developers</audience>.
        </Abstract>
      </Book>
    </Catalog>
    ```

## <a name="see-also"></a>Zobacz też

- [Manipulowanie XML w Visual Basic](manipulating-xml.md)
- [XML](index.md)
- [Porady: ładowanie XML z pliku, ciągu lub strumienia](how-to-load-xml-from-a-file-string-or-stream.md)
- [LINQ](../linq/index.md)
- [Wprowadzenie do LINQ w Visual Basic](../linq/introduction-to-linq.md)
