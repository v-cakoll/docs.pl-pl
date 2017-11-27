---
title: "Przegląd klasy XElement klasy (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 2b9f0cd8-a1d1-4037-accf-0f38a410fa11
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: bd3ffed4f164ac9edc5e46719f516363220c8d63
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="xelement-class-overview-c"></a>Przegląd klasy XElement klasy (C#)
<xref:System.Xml.Linq.XElement> Klasy jest jednym z podstawowych klas w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]. Reprezentuje XML element. Ta klasa służy do tworzenia elementów; zmienić zawartość elementu; Dodawanie, zmienianie lub usuwanie elementów podrzędnych; dodać atrybuty do elementu; lub serializacji zawartości elementu w postaci tekstu. Możesz również może współdziałać z innych klas w <xref:System.Xml?displayProperty=nameWithType>, takich jak <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, i <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
## <a name="xelement-functionality"></a>Funkcje klasy XElement  
 W tym temacie opisano funkcje udostępniane przez <xref:System.Xml.Linq.XElement> klasy.  
  
### <a name="constructing-xml-trees"></a>Konstruowanie drzewa XML  
 Można utworzyć drzewa XML na różne sposoby, m.in. następujące czynności:  
  
-   Można utworzyć drzewa XML w kodzie. Aby uzyskać więcej informacji, zobacz [tworzenia drzewa XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md).  
  
-   Może przeanalizować składni XML z różnych źródeł, takich jak <xref:System.IO.TextReader>, pliki tekstowe lub adres sieci Web (URL). Aby uzyskać więcej informacji, zobacz [analiza kodu XML (C#)](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md).  
  
-   Można użyć <xref:System.Xml.XmlReader> do wypełnienia drzewa. Aby uzyskać więcej informacji, zobacz <xref:System.Xml.Linq.XNode.ReadFrom%2A>.  
  
-   Jeśli masz moduł, który może zapisać zawartości do <xref:System.Xml.XmlWriter>, można użyć <xref:System.Xml.Linq.XContainer.CreateWriter%2A> metodę, aby utworzyć moduł zapisujący, Przekaż twórcę modułu, a następnie użyj zawartość, która jest zapisywany w <xref:System.Xml.XmlWriter> do wypełnienia drzewo składni XML.  
  
 Jednak najczęściej można utworzyć drzewa XML jest następująca:  
  
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
  
 Innej często techniki tworzenia drzewo XML polega na użyciu wyniki [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytanie, aby wypełnić drzewo XML, jak pokazano w poniższym przykładzie:  
  
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
  
### <a name="serializing-xml-trees"></a>Serializacja XML drzewa  
 Może wykonywać serializację drzewa XML do <xref:System.IO.File>, <xref:System.IO.TextWriter>, lub <xref:System.Xml.XmlWriter>.  
  
 Aby uzyskać więcej informacji, zobacz [drzew serializacji XML (C#)](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md).  
  
### <a name="retrieving-xml-data-via-axis-methods"></a>Pobieranie danych XML za pomocą metod osi  
 Można użyć metody osi można pobrać atrybutów, elementy podrzędne elementów podrzędnych i elementów nadrzędnych. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]zapytania działać na osi metod i podać kilka sposobów elastycznym i wydajnym do nawigowania i przetwarzania drzewo XML.  
  
 Aby uzyskać więcej informacji, zobacz [LINQ do osi XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md).  
  
### <a name="querying-xml-trees"></a>Wykonywanie zapytania drzewa XML  
 Można napisać [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytań, które wyodrębnić dane z drzewa XML.  
  
 Aby uzyskać więcej informacji, zobacz [zapytanie drzewa XML (C#)](../../../../csharp/programming-guide/concepts/linq/querying-xml-trees.md).  
  
### <a name="modifying-xml-trees"></a>Modyfikowanie drzew XML  
 Można zmodyfikować elementu na wiele sposobów, łącznie ze zmianą jego zawartości lub atrybutów. Można również usunąć element z jego elementu nadrzędnego.  
  
 Aby uzyskać więcej informacji, zobacz [modyfikowanie drzew XML (LINQ do XML) (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md).  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ do XML-przegląd programowania w języku (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
