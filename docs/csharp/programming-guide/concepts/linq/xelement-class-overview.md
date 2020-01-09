---
title: XElement — Omówienie klasyC#()
ms.date: 07/20/2015
ms.assetid: 2b9f0cd8-a1d1-4037-accf-0f38a410fa11
ms.openlocfilehash: d77c725b3c786b8a8fa2b0eeab4bc4b30f298218
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635473"
---
# <a name="xelement-class-overview-c"></a>XElement — Omówienie klasyC#()
Klasa <xref:System.Xml.Linq.XElement> jest jedną z podstawowych klas w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]. Reprezentuje element XML. Możesz użyć tej klasy do tworzenia elementów; Zmień zawartość elementu; Dodawanie, zmienianie lub usuwanie elementów podrzędnych; Dodaj atrybuty do elementu; lub serializować zawartości elementu w postaci tekstowej. Możesz również współpracować z innymi klasami w <xref:System.Xml?displayProperty=nameWithType>, takich jak <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>i <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
W tym temacie opisano funkcje udostępniane przez klasę <xref:System.Xml.Linq.XElement>.  
  
## <a name="constructing-xml-trees"></a>Konstruowanie drzew XML  
 Drzewa XML można konstruować na różne sposoby, w tym następujące:  
  
- Drzewo XML można skonstruować w kodzie. Aby uzyskać więcej informacji, zobacz [Tworzenie drzew XMLC#()](./linq-to-xml-overview.md).  
  
- Można analizować XML z różnych źródeł, w tym <xref:System.IO.TextReader>, pliki tekstowe lub adresy sieci Web (URL). Aby uzyskać więcej informacji, zobacz [Analizowanie XMLC#()](./how-to-parse-a-string.md).  
  
- Aby wypełnić drzewo, można użyć <xref:System.Xml.XmlReader>. Aby uzyskać więcej informacji, zobacz temat <xref:System.Xml.Linq.XNode.ReadFrom%2A>.  
  
- Jeśli masz moduł, który może zapisywać zawartość w <xref:System.Xml.XmlWriter>, możesz użyć metody <xref:System.Xml.Linq.XContainer.CreateWriter%2A> do utworzenia składnika zapisywania, przekazania składnika zapisywania do modułu, a następnie użyć zawartości zapisanej w <xref:System.Xml.XmlWriter>, aby wypełnić drzewo XML.  
  
 Jednak najbardziej typowym sposobem tworzenia drzewa XML jest:  
  
```csharp  
XElement contacts =  
    new XElement("Contacts",  
        new XElement("Contact",  
            new XElement("Name", "Patrick Hines"),   
            new XElement("Phone", "206-555-0144"),  
            new XElement("Address",  
                new XElement("Street1", "123 Main St"),  
                new XElement("City", "Mercer Island"),  
                new XElement("State", "WA"),  
                new XElement("Postal", "68042")  
            )  
        )  
    );  
```  
  
 Inna bardzo często stosowana technika tworzenia drzewa XML obejmuje użycie wyników zapytania LINQ do wypełnienia drzewa XML, jak pokazano w następującym przykładzie:  
  
```csharp  
XElement srcTree = new XElement("Root",  
    new XElement("Element", 1),  
    new XElement("Element", 2),  
    new XElement("Element", 3),  
    new XElement("Element", 4),  
    new XElement("Element", 5)  
);  
XElement xmlTree = new XElement("Root",  
    new XElement("Child", 1),  
    new XElement("Child", 2),  
    from el in srcTree.Elements()  
    where (int)el > 2  
    select el  
);  
Console.WriteLine(xmlTree);  
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
  
## <a name="serializing-xml-trees"></a>Serializowanie drzew XML  
 Można serializować drzewo XML do <xref:System.IO.File>, <xref:System.IO.TextWriter>lub <xref:System.Xml.XmlWriter>.  
  
 Aby uzyskać więcej informacji, zobacz [Serializowanie drzew XMLC#()](./preserving-white-space-while-serializing.md).  
  
## <a name="retrieving-xml-data-via-axis-methods"></a>Pobieranie danych XML za pomocą metod osi  
 Możesz użyć metod osi do pobierania atrybutów, elementów podrzędnych, elementów podrzędnych i elementów nadrzędnych. Zapytania LINQ działają na podstawie metod osi i zapewniają kilka elastycznych i wydajnych sposobów nawigowania i przetwarzania drzewa XML.  
  
 Aby uzyskać więcej informacji, zobacz [LINQ to XML osiC#()](./linq-to-xml-axes-overview.md).  
  
## <a name="querying-xml-trees"></a>Tworzenie zapytań dotyczących drzew XML  
 Można napisać zapytania LINQ wyodrębniające dane z drzewa XML.  
  
 Aby uzyskać więcej informacji, zobacz temat Tworzenie [zapytań dotyczącychC#drzew XML ()](./how-to-find-an-element-with-a-specific-attribute.md).  
  
## <a name="modifying-xml-trees"></a>Modyfikowanie drzew XML  
 Można zmodyfikować element na różne sposoby, w tym zmieniać jego zawartość lub atrybuty. Można również usunąć element z jego elementu nadrzędnego.  
  
 Aby uzyskać więcej informacji, zobacz [Modyfikowanie drzew XML (LINQ to XML)C#()](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie programowania LINQ to XML (C#)](serializing-to-files-textwriters-and-xmlwriters.md)
