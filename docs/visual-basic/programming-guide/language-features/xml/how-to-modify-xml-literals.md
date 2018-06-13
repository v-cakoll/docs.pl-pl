---
title: 'Porady: modyfikowanie literałów XML (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], Value
- XML literals [Visual Basic]
- XML literals [Visual Basic], modifying
ms.assetid: 4e864522-a37a-43a2-8236-af80277c5482
ms.openlocfilehash: 17da86d6d10fb1602c16fc2a8c4d6f9f8acf8ff7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33656048"
---
# <a name="how-to-modify-xml-literals-visual-basic"></a>Porady: modyfikowanie literałów XML (Visual Basic)
Visual Basic umożliwia wygodne sposobów modyfikowanie literałów XML. Można dodawać i usuwać elementy i atrybuty, a także można zastąpić istniejącego elementu nowego elementu XML. Ten temat zawiera kilka przykładów sposobu modyfikowania istniejących literału XML.  
  
### <a name="to-modify-the-value-of-an-xml-literal"></a>Aby zmodyfikować wartość literału XML  
  
1.  Aby zmodyfikować wartość literału XML, uzyskać odwołania do pliku XML literału i ustaw `Value` na żądaną wartość.  
  
     Poniższy przykładowy kod aktualizuje wartość wszystkich \<cen > elementów w dokumencie XML.  
  
     [!code-vb[VbXmlSamples2#4](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_1.vb)]  
  
     Poniżej przedstawiono przykładowe źródło XML i zmodyfikować XML w tym przykładzie kodu.  
  
    ```  
    Source XML:  
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
  
    Modified XML:  
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
    >  `Value` Właściwość odwołuje się do pierwszego elementu XML w kolekcji. Jeśli istnieje więcej niż jeden element, który ma taką samą nazwę w kolekcji, ustawienie `Value` właściwość dotyczy tylko pierwszego elementu w kolekcji.  
  
### <a name="to-add-an-attribute-to-an-xml-literal"></a>Aby dodać atrybut do literał XML  
  
1.  Aby dodać atrybut literał XML, należy najpierw uzyskać odwołanie do literału XML. Następnie można dodać atrybutu, dodając nowe właściwości osi atrybutu XML. Można również dodać nowy <xref:System.Xml.Linq.XAttribute> obiekt do formatu XML przy użyciu literału <xref:System.Xml.Linq.XContainer.Add%2A> metody. W poniższym przykładzie przedstawiono obie opcje.  
  
     [!code-vb[VbXmlSamples2#5](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_2.vb)]  
  
     Poniżej przedstawiono przykładowe źródło XML i zmodyfikować XML w tym przykładzie kodu.  
  
    ```  
    Source XML:  
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
  
    Modified XML:  
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
  
1.  Aby dodać element do literał XML, należy najpierw uzyskać odwołanie do literału XML. Następnie można dodać nowego <xref:System.Xml.Linq.XElement> obiektu jako ostatniego elementu podrzędnego elementu przy użyciu <xref:System.Xml.Linq.XContainer.Add%2A> metody. Można dodać nowego <xref:System.Xml.Linq.XElement> obiektu jako pierwszego elementu podrzędnego przy użyciu <xref:System.Xml.Linq.XContainer.AddFirst%2A> metody.  
  
     Aby dodać nowego elementu w określonej lokalizacji względem innych elementów podrzędnych, należy najpierw uzyskać odwołanie do elementu podrzędnego sąsiadujących ze sobą. Następnie można dodać nowe <xref:System.Xml.Linq.XElement> obiektu przed sąsiadujących podelement przy użyciu <xref:System.Xml.Linq.XNode.AddBeforeSelf%2A> metody. Możesz także dodać nowe <xref:System.Xml.Linq.XElement> obiektu po sąsiadujących podelement przy użyciu <xref:System.Xml.Linq.XNode.AddAfterSelf%2A> metody.  
  
     W poniższym przykładzie przedstawiono przykłady każdego z poniższych metod.  
  
     [!code-vb[VbXmlSamples2#6](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_3.vb)]  
  
     Poniżej przedstawiono przykładowe źródło XML i zmodyfikować XML w tym przykładzie kodu.  
  
    ```  
    Source XML:  
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
  
    Modified XML:  
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
  
1.  Aby usunąć element lub atrybut z literał XML, uzyskać odwołania do elementu lub atrybutu i wywołanie `Remove` metody, jak pokazano w poniższym przykładzie.  
  
     [!code-vb[VbXmlSamples2#7](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_4.vb)]  
  
     Poniżej przedstawiono przykładowe źródło XML i zmodyfikować XML w tym przykładzie kodu.  
  
    ```  
    Source XML:  
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
  
    Modified XML:  
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
  
     Aby usunąć wszystkich elementów lub atrybutów z literał XML, uzyskać odwołania do literału XML i Wywołaj <xref:System.Xml.Linq.XElement.RemoveAll%2A> metody.  
  
### <a name="to-modify-an-xml-literal"></a>Aby zmodyfikować literał XML  
  
1.  Aby zmienić nazwę elementu XML, należy najpierw uzyskać odwołanie do elementu. Następnie możesz utworzyć nową <xref:System.Xml.Linq.XElement> obiektu, który ma nową nazwę, a następnie przekazać nowy <xref:System.Xml.Linq.XElement> do obiektu <xref:System.Xml.Linq.XNode.ReplaceWith%2A> metody istniejącej <xref:System.Xml.Linq.XElement> obiektu.  
  
     Jeśli element, który chcesz zamienić ma elementy podrzędne, które muszą zostać zachowane, ustaw wartość nowego <xref:System.Xml.Linq.XElement> do obiektu <xref:System.Xml.Linq.XContainer.Nodes%2A> właściwości istniejącego elementu. Spowoduje to ustawienie wartość nowego elementu do wewnętrzny kod XML z istniejącego elementu. W przeciwnym razie wartość nowy element można ustawić `Value` właściwości istniejącego elementu.  
  
     Poniższy przykładowy kod zastępuje wszystkie \<opis > elementy z \<abstrakcyjny > elementu. Zawartość \<opis > elementu zostaną zachowane w nowej \<abstrakcyjny > elementu za pomocą <xref:System.Xml.Linq.XContainer.Nodes%2A> właściwość \<opis > <xref:System.Xml.Linq.XElement> obiektu.  
  
     [!code-vb[VbXmlSamples2#8](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_5.vb)]  
  
     Poniżej przedstawiono przykładowe źródło XML i zmodyfikować XML w tym przykładzie kodu.  
  
    ```  
    Source XML:  
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
  
    Modified XML:  
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
 [Manipulowanie XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [Instrukcje: ładowanie kodu XML z pliku, ciągu lub strumienia](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
