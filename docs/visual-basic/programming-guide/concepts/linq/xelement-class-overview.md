---
title: XElement, klasa — przegląd
ms.date: 07/20/2015
ms.assetid: 52331fcd-6023-4d19-b423-7b24f2d86ded
ms.openlocfilehash: a0e50c8a5a14150ee09a328f4dcdd5bc88363621
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413222"
---
# <a name="xelement-class-overview-visual-basic"></a>Przegląd klasy XElement (Visual Basic)
<xref:System.Xml.Linq.XElement>Klasa jest jedną z podstawowych klas w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] . Reprezentuje element XML. Możesz użyć tej klasy do tworzenia elementów; Zmień zawartość elementu; Dodawanie, zmienianie lub usuwanie elementów podrzędnych; Dodaj atrybuty do elementu; lub serializować zawartości elementu w postaci tekstowej. Możesz również współpracować z innymi klasami w <xref:System.Xml?displayProperty=nameWithType> , takich jak <xref:System.Xml.XmlReader> , <xref:System.Xml.XmlWriter> , i <xref:System.Xml.Xsl.XslCompiledTransform> .  
  
## <a name="xelement-functionality"></a>Funkcja XElement  
 W tym temacie opisano funkcje udostępniane przez <xref:System.Xml.Linq.XElement> klasę.  
  
### <a name="constructing-xml-trees"></a>Konstruowanie drzew XML  
 Drzewa XML można konstruować na różne sposoby, w tym następujące:  
  
- Drzewo XML można skonstruować w kodzie. Aby uzyskać więcej informacji, zobacz [Tworzenie drzew XML (Visual Basic)](creating-xml-trees.md).  
  
- Można analizować XML z różnych źródeł, w tym <xref:System.IO.TextReader> plików tekstowych lub adresów sieci Web (URL). Aby uzyskać więcej informacji, zobacz [Analizowanie XML (Visual Basic)](parsing-xml.md).  
  
- <xref:System.Xml.XmlReader>Aby wypełnić drzewo, można użyć elementu. Aby uzyskać więcej informacji, zobacz <xref:System.Xml.Linq.XNode.ReadFrom%2A>.  
  
- Jeśli masz moduł, który może zapisywać zawartość w <xref:System.Xml.XmlWriter> programie, możesz użyć <xref:System.Xml.Linq.XContainer.CreateWriter%2A> metody do utworzenia składnika zapisywania, przekazania składnika zapisywania do modułu, a następnie użyć zawartości zapisanej w programie w <xref:System.Xml.XmlWriter> celu wypełnienia drzewa XML.  
  
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
  
 Inna bardzo często stosowana technika tworzenia drzewa XML obejmuje użycie wyników zapytania LINQ do wypełnienia drzewa XML, jak pokazano w następującym przykładzie:  
  
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
 Można serializować drzewo XML do <xref:System.IO.File> , a <xref:System.IO.TextWriter> lub <xref:System.Xml.XmlWriter> .  
  
 Aby uzyskać więcej informacji, zobacz [Serializowanie drzew XML (Visual Basic)](serializing-xml-trees.md).  
  
### <a name="retrieving-xml-data-via-axis-methods"></a>Pobieranie danych XML za pomocą metod osi  
 Możesz użyć metod osi do pobierania atrybutów, elementów podrzędnych, elementów podrzędnych i elementów nadrzędnych. Zapytania LINQ działają na podstawie metod osi i zapewniają kilka elastycznych i wydajnych sposobów nawigowania i przetwarzania drzewa XML.  
  
 Aby uzyskać więcej informacji, zobacz [LINQ to XML osi (Visual Basic)](linq-to-xml-axes.md).  
  
### <a name="querying-xml-trees"></a>Tworzenie zapytań dotyczących drzew XML  
 Można napisać zapytania LINQ wyodrębniające dane z drzewa XML.  
  
 Aby uzyskać więcej informacji, zobacz temat Tworzenie [zapytań dotyczących drzew XML (Visual Basic)](querying-xml-trees.md).  
  
### <a name="modifying-xml-trees"></a>Modyfikowanie drzew XML  
 Można zmodyfikować element na różne sposoby, w tym zmieniać jego zawartość lub atrybuty. Można również usunąć element z jego elementu nadrzędnego.  
  
 Aby uzyskać więcej informacji, zobacz [Modyfikowanie drzew XML (LINQ to XML) (Visual Basic)](modifying-xml-trees-linq-to-xml.md).  
  
## <a name="see-also"></a>Zobacz też

- [Omówienie programowania LINQ to XML (Visual Basic)](linq-to-xml-programming-overview.md)
