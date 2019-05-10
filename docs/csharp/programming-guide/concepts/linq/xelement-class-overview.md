---
title: Przegląd klasy XElement (C#)
ms.date: 07/20/2015
ms.assetid: 2b9f0cd8-a1d1-4037-accf-0f38a410fa11
ms.openlocfilehash: cddb36ac6401c20478a1254fe3d63afe5bd13099
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64595758"
---
# <a name="xelement-class-overview-c"></a>Przegląd klasy XElement (C#)
<xref:System.Xml.Linq.XElement> Klasy jest jednym z podstawowych klas w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]. Reprezentuje XML element. Ta klasa służy do tworzenia elementów; Zmień zawartość elementu; Dodawanie, zmienianie lub usuwanie elementów podrzędnych; Dodawanie atrybutów do elementu; lub serializacji zawartość elementu w postaci tekstu. Może również współpracować z innych klas w <xref:System.Xml?displayProperty=nameWithType>, takich jak <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, i <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
## <a name="xelement-functionality"></a>Funkcje klasy XElement  
 W tym temacie opisano funkcje udostępniane przez <xref:System.Xml.Linq.XElement> klasy.  
  
### <a name="constructing-xml-trees"></a>Konstruowanie drzewa XML  
 Możesz utworzyć drzew XML na różne sposoby, m.in. następujące czynności:  
  
- Można skonstruować drzewa XML w kodzie. Aby uzyskać więcej informacji, zobacz [tworzenie drzew XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md).  
  
- Można teraz analizować XML z różnych źródeł, w tym <xref:System.IO.TextReader>, pliki tekstowe lub adres internetowy (URL). Aby uzyskać więcej informacji, zobacz [analiza kodu XML (C#)](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md).  
  
- Możesz użyć <xref:System.Xml.XmlReader> do wypełniania drzewa. Aby uzyskać więcej informacji, zobacz <xref:System.Xml.Linq.XNode.ReadFrom%2A>.  
  
- Jeśli masz moduł, który może zapisać zawartości <xref:System.Xml.XmlWriter>, możesz użyć <xref:System.Xml.Linq.XContainer.CreateWriter%2A> metodę, aby utworzyć moduł zapisujący, przekazać moduł zapisujący do modułu, a następnie użyć zawartości, który jest zapisywany <xref:System.Xml.XmlWriter> do wypełnianie drzewa XML.  
  
 Jednak Najczęstszym sposobem tworzenia drzewa XML jest następująca:  
  
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
  
 Inna technika bardzo często do tworzenia drzewa XML polega na wykorzystaniu wyników [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytanie, aby wypełnianie drzewa XML, jak pokazano w poniższym przykładzie:  
  
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
  
### <a name="serializing-xml-trees"></a>Serializowanie drzew XML  
 Może wykonywać serializację drzewa XML do <xref:System.IO.File>, <xref:System.IO.TextWriter>, lub <xref:System.Xml.XmlWriter>.  
  
 Aby uzyskać więcej informacji, zobacz [serializowanie drzew XML (C#)](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md).  
  
### <a name="retrieving-xml-data-via-axis-methods"></a>Pobieranie danych XML przy użyciu metody osi  
 Można użyć metody osi, można pobrać atrybutów, elementy podrzędne, elementów podrzędnych i elementów nadrzędnych. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania działają na metody osi i zapewniają kilka metod elastycznym i zaawansowanym nawigowania i przetworzyć drzewa XML.  
  
 Aby uzyskać więcej informacji, zobacz [LINQ do XML osi (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md).  
  
### <a name="querying-xml-trees"></a>Tworzenie zapytań dotyczących drzew XML  
 Można napisać [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytań, które umożliwiają wyodrębnianie danych z drzewa XML.  
  
 Aby uzyskać więcej informacji, zobacz [zapytań drzew XML (C#)](../../../../csharp/programming-guide/concepts/linq/querying-xml-trees.md).  
  
### <a name="modifying-xml-trees"></a>Modyfikowanie drzew XML  
 Można zmodyfikować elementu na różne sposoby, m.in. zmiana jego zawartości lub atrybutów. Można również usunąć element, po swoim obiekcie nadrzędnym.  
  
 Aby uzyskać więcej informacji, zobacz [modyfikowanie drzew XML (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md).  
  
## <a name="see-also"></a>Zobacz także

- [LINQ to XML — przegląd programowania (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
