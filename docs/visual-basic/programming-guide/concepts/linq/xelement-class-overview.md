---
title: XElement, klasa — przegląd
ms.date: 07/20/2015
ms.assetid: 52331fcd-6023-4d19-b423-7b24f2d86ded
ms.openlocfilehash: ff751a14abf9a9cb5d64e44e601c5d0ca6218c7d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349320"
---
# <a name="xelement-class-overview-visual-basic"></a>Przegląd klasy XElement (Visual Basic)
Klasa <xref:System.Xml.Linq.XElement> jest jedną z podstawowych klas w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]. Reprezentuje element XML. Możesz użyć tej klasy do tworzenia elementów; Zmień zawartość elementu; Dodawanie, zmienianie lub usuwanie elementów podrzędnych; Dodaj atrybuty do elementu; lub serializować zawartości elementu w postaci tekstowej. Możesz również współpracować z innymi klasami w <xref:System.Xml?displayProperty=nameWithType>, takich jak <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>i <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
## <a name="xelement-functionality"></a>Funkcja XElement  
 W tym temacie opisano funkcje udostępniane przez klasę <xref:System.Xml.Linq.XElement>.  
  
### <a name="constructing-xml-trees"></a>Konstruowanie drzew XML  
 Drzewa XML można konstruować na różne sposoby, w tym następujące:  
  
- Drzewo XML można skonstruować w kodzie. Aby uzyskać więcej informacji, zobacz [Tworzenie drzew XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).  
  
- Można analizować XML z różnych źródeł, w tym <xref:System.IO.TextReader>, pliki tekstowe lub adresy sieci Web (URL). Aby uzyskać więcej informacji, zobacz [Analizowanie XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md).  
  
- Aby wypełnić drzewo, można użyć <xref:System.Xml.XmlReader>. Aby uzyskać więcej informacji, zobacz temat <xref:System.Xml.Linq.XNode.ReadFrom%2A>.  
  
- Jeśli masz moduł, który może zapisywać zawartość w <xref:System.Xml.XmlWriter>, możesz użyć metody <xref:System.Xml.Linq.XContainer.CreateWriter%2A> do utworzenia składnika zapisywania, przekazania składnika zapisywania do modułu, a następnie użyć zawartości zapisanej w <xref:System.Xml.XmlWriter>, aby wypełnić drzewo XML.  
  
 Jednak najbardziej typowym sposobem tworzenia drzewa XML jest:  
  
```vb  
Dim contacts As XElement = _  
    <Contacts>  
        <Contact>  
            <Name>Patrick Hines</Name>  
            <Phone>206-555-0144</Phone>  
            <Address>  
                <Street1>123 Main St</Street1>  
                <City>Mercer Island</City>  
                <State>WA</State>  
                <Postal>68042</Postal>  
            </Address>  
        </Contact>  
    </Contacts>  
```  
  
 Inna bardzo często stosowana technika tworzenia drzewa XML obejmuje użycie wyników zapytania [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], aby wypełnić drzewo XML, jak pokazano w następującym przykładzie:  
  
```vb  
Dim srcTree As XElement = _  
    <Root>  
        <Element>1</Element>  
        <Element>2</Element>  
        <Element>3</Element>  
        <Element>4</Element>  
        <Element>5</Element>  
    </Root>  
Dim xmlTree As XElement = _  
    <Root>  
        <Child>1</Child>  
        <Child>2</Child>  
        <%= From el In srcTree.Elements() _  
            Where el.Value > 2 _  
            Select el %>  
    </Root>  
Console.WriteLine(xmlTree)  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
### <a name="serializing-xml-trees"></a>Serializowanie drzew XML  
 Można serializować drzewo XML do <xref:System.IO.File>, <xref:System.IO.TextWriter>lub <xref:System.Xml.XmlWriter>.  
  
 Aby uzyskać więcej informacji, zobacz [Serializowanie drzew XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md).  
  
### <a name="retrieving-xml-data-via-axis-methods"></a>Pobieranie danych XML za pomocą metod osi  
 Możesz użyć metod osi do pobierania atrybutów, elementów podrzędnych, elementów podrzędnych i elementów nadrzędnych. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania działają na podstawie metod osi i zapewniają kilka elastycznych i wydajnych sposobów nawigowania i przetwarzania drzewa XML.  
  
 Aby uzyskać więcej informacji, zobacz [LINQ to XML osi (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md).  
  
### <a name="querying-xml-trees"></a>Tworzenie zapytań dotyczących drzew XML  
 Można pisać [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytań, które wyodrębniają dane z drzewa XML.  
  
 Aby uzyskać więcej informacji, zobacz temat Tworzenie [zapytań dotyczących drzew XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/querying-xml-trees.md).  
  
### <a name="modifying-xml-trees"></a>Modyfikowanie drzew XML  
 Można zmodyfikować element na różne sposoby, w tym zmieniać jego zawartość lub atrybuty. Można również usunąć element z jego elementu nadrzędnego.  
  
 Aby uzyskać więcej informacji, zobacz [Modyfikowanie drzew XML (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md).  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie programowania LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
