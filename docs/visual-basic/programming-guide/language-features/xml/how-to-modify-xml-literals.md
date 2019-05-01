---
title: 'Instrukcje: Modyfikowanie literałów XML (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], Value
- XML literals [Visual Basic]
- XML literals [Visual Basic], modifying
ms.assetid: 4e864522-a37a-43a2-8236-af80277c5482
ms.openlocfilehash: 003715b04f3a5c0fb41e846beb189f117378ea58
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053031"
---
# <a name="how-to-modify-xml-literals-visual-basic"></a>Instrukcje: Modyfikowanie literałów XML (Visual Basic)

Zapewnia wygodne metody modyfikowanie literałów XML w Visual Basic. Możesz dodawać lub usuwać elementy i atrybuty, a za pomocą nowego elementu XML może również zastąpić istniejący element. Ten temat zawiera kilka przykładów sposobu modyfikowania istniejących literał XML.

### <a name="to-modify-the-value-of-an-xml-literal"></a>Aby zmodyfikować wartość literał XML

1. Aby zmodyfikować wartość literał XML, Uzyskaj odwołanie do pliku XML literału i ustaw `Value` właściwości na żądaną wartość.

    Poniższy kod aktualizuje wartość wszystkich \<cena > elementów w dokumencie XML.

    [!code-vb[VbXmlSamples2#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#4)]

    Poniżej przedstawiono przykładowe źródło XML i zmodyfikować XML w tym przykładzie kodu.

    Źródło XML:

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

    Zmodyfikowany kod XML:

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
    > `Value` Właściwość odwołuje się do pierwszego elementu XML w kolekcji. Jeśli istnieje więcej niż jeden element, który ma taką samą nazwę w kolekcji, ustawienie `Value` właściwość dotyczy tylko pierwszego elementu w kolekcji.

### <a name="to-add-an-attribute-to-an-xml-literal"></a>Aby dodać atrybut na literał XML

1. Aby dodać atrybut literał XML, należy najpierw uzyskać odwołanie do literał XML. Następnie można dodać atrybutu przez dodanie nowych właściwości osi atrybutu XML. Można również dodać nowy <xref:System.Xml.Linq.XAttribute> obiekt do formatu XML literału przy użyciu <xref:System.Xml.Linq.XContainer.Add%2A> metody. Poniższy kod przedstawia obie opcje.

    [!code-vb[VbXmlSamples2#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#5)]

    Poniżej przedstawiono przykładowe źródło XML i zmodyfikować XML w tym przykładzie kodu.

    Źródło XML:

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

    Zmodyfikowany kod XML:

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

    Aby uzyskać więcej informacji na temat właściwości osi atrybutu XML, zobacz [właściwości osi atrybutu XML](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md).

### <a name="to-add-an-element-to-an-xml-literal"></a>Aby dodać element do literał XML

1. Aby dodać element do literał XML, należy najpierw uzyskać odwołanie do literał XML. Następnie można dodać nowego <xref:System.Xml.Linq.XElement> obiektu jako ostatniego elementu podrzędnego elementu za pomocą <xref:System.Xml.Linq.XContainer.Add%2A> metody. Można dodać nowego <xref:System.Xml.Linq.XElement> obiektu jako pierwszego elementu podrzędnego przy użyciu <xref:System.Xml.Linq.XContainer.AddFirst%2A> metody.

    Aby dodać nowy element w określonej lokalizacji względnej wobec innych elementów podrzędnych, należy najpierw uzyskać odwołanie do sąsiadujących elementu podrzędnego. Następnie można dodać nowego <xref:System.Xml.Linq.XElement> obiektu przed sąsiadujących elementu podrzędnego przy użyciu <xref:System.Xml.Linq.XNode.AddBeforeSelf%2A> metody. Możesz także dodać nowe <xref:System.Xml.Linq.XElement> obiektu po sąsiadujących elementu podrzędnego przy użyciu <xref:System.Xml.Linq.XNode.AddAfterSelf%2A> metody.

    Poniższy przykład pokazuje przykłady każdego z tych metod.

    [!code-vb[VbXmlSamples2#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#6)]

    Poniżej przedstawiono przykładowe źródło XML i zmodyfikować XML w tym przykładzie kodu.

    Źródło XML:

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

    Zmodyfikowany kod XML:

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

### <a name="to-remove-an-element-or-attribute-from-an-xml-literal"></a>Aby usunąć element lub atrybut z literał XML

1. Usuwanie elementu lub atrybutu literał XML, Uzyskaj odwołanie do elementu lub atrybutu i wywołania `Remove` metodzie, jak pokazano w poniższym przykładzie.

    [!code-vb[VbXmlSamples2#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#7)]

    Poniżej przedstawiono przykładowe źródło XML i zmodyfikować XML w tym przykładzie kodu.

    Źródło XML:

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

    Zmodyfikowany kod XML:

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

    Aby usunąć wszystkie elementy lub atrybuty z literał XML, Uzyskaj odwołanie do literał XML, a następnie wywołać <xref:System.Xml.Linq.XElement.RemoveAll%2A> metody.

### <a name="to-modify-an-xml-literal"></a>Aby zmodyfikować literał XML

1. Aby zmienić nazwę elementu XML, należy najpierw uzyskać odwołanie do elementu. Następnie możesz utworzyć nową <xref:System.Xml.Linq.XElement> obiekt, który ma nową nazwę, a następnie przekazać nowy <xref:System.Xml.Linq.XElement> obiekt <xref:System.Xml.Linq.XNode.ReplaceWith%2A> metoda istniejącej <xref:System.Xml.Linq.XElement> obiektu.

    Jeśli element, który jest zamieniany ma elementy podrzędne, które muszą zostać zachowane, ustaw wartość nowego <xref:System.Xml.Linq.XElement> obiekt <xref:System.Xml.Linq.XContainer.Nodes%2A> właściwości istniejącego elementu. Spowoduje to ustawienie wartość nowego elementu do wewnętrzny kod XML z istniejącego elementu. W przeciwnym razie można ustawić wartość nowy element do `Value` właściwości istniejącego elementu.

    Poniższy przykładowy kod zastępuje wszystkie \<opis > elementy z \<abstrakcyjne > element. Zawartość \<opis > element są zachowywane w nowym \<abstrakcyjne > element przy użyciu <xref:System.Xml.Linq.XContainer.Nodes%2A> właściwość \<opis > <xref:System.Xml.Linq.XElement> obiektu.

    [!code-vb[VbXmlSamples2#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#8)]

    Poniżej przedstawiono przykładowe źródło XML i zmodyfikować XML w tym przykładzie kodu.

    Źródło XML:

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

    Zmodyfikowany kod XML:

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

## <a name="see-also"></a>Zobacz także

- [Manipulowanie XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [Instrukcje: Ładowanie kodu XML z pliku, ciągu lub Stream](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
