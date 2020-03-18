---
title: Omówienie klasy XElement (C#)
ms.date: 07/20/2015
ms.assetid: 2b9f0cd8-a1d1-4037-accf-0f38a410fa11
ms.openlocfilehash: 6a93dd4bdaf16fddff800b08b0f3146ecb63f9b7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167897"
---
# <a name="xelement-class-overview-c"></a>Omówienie klasy XElement (C#)
Klasa <xref:System.Xml.Linq.XElement> jest jedną z podstawowych [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]klas w . Reprezentuje element XML. Ta klasa służy do tworzenia elementów; zmienić zawartość elementu; dodawanie, zmienianie lub usuwanie elementów podrzędnych; dodawanie atrybutów do elementu; lub serializować zawartość elementu w formie tekstowej. Można również współpracować z <xref:System.Xml?displayProperty=nameWithType>innymi klasami <xref:System.Xml.XmlWriter>w <xref:System.Xml.Xsl.XslCompiledTransform>, takich jak <xref:System.Xml.XmlReader>, , i .  
  
W tym temacie opisano <xref:System.Xml.Linq.XElement> funkcje dostarczane przez klasę.  
  
## <a name="constructing-xml-trees"></a>Konstruowanie drzew XML  
 Drzewa XML można konstruować na różne sposoby, w tym na następujące sposoby:  
  
- Można skonstruować drzewo XML w kodzie. Aby uzyskać więcej informacji, zobacz [Tworzenie drzew XML (C#)](./linq-to-xml-overview.md).  
  
- Można analizować XML z różnych źródeł, <xref:System.IO.TextReader>w tym z plików tekstowych lub adresu URL. Aby uzyskać więcej informacji, zobacz [Analizowanie języka XML (C#)](./how-to-parse-a-string.md).  
  
- Można użyć <xref:System.Xml.XmlReader> do wypełnienia drzewa. Aby uzyskać więcej informacji, zobacz <xref:System.Xml.Linq.XNode.ReadFrom%2A>.  
  
- Jeśli masz moduł, który można <xref:System.Xml.XmlWriter>zapisywać zawartość <xref:System.Xml.Linq.XContainer.CreateWriter%2A> do , można użyć metody do utworzenia modułu zapisującego, przekazać <xref:System.Xml.XmlWriter> moduł umodułu, a następnie użyć zawartości, która jest zapisywana do wypełnienia drzewa XML.  
  
 Jednak najczęstszym sposobem tworzenia drzewa XML jest następujący:  
  
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
  
 Inną bardzo często techniką tworzenia drzewa XML polega na wykorzystaniu wyników kwerendy LINQ do wypełnienia drzewa XML, jak pokazano w poniższym przykładzie:  
  
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
 Drzewo XML można serializować na <xref:System.IO.File>, <xref:System.IO.TextWriter>a <xref:System.Xml.XmlWriter>, lub .  
  
 Aby uzyskać więcej informacji, zobacz [Serializowanie drzew XML (C#)](./preserving-white-space-while-serializing.md).  
  
## <a name="retrieving-xml-data-via-axis-methods"></a>Pobieranie danych XML za pomocą metod osi  
 Metody osi można używać do pobierania atrybutów, elementów podrzędnych, elementów podrzędnych i elementów elementów przodka. Zapytania LINQ działają na metodach osi i zapewniają kilka elastycznych i zaawansowanych sposobów poruszania się po drzewie XML i przetwarzania go.  
  
 Aby uzyskać więcej informacji, zobacz [LINQ do XML Axes (C#)](./linq-to-xml-axes-overview.md).  
  
## <a name="querying-xml-trees"></a>Tworzenie zapytań dotyczących drzew XML  
 Można napisać zapytania LINQ, które wyodrębniają dane z drzewa XML.  
  
 Aby uzyskać więcej informacji, zobacz [Wykonywanie kwerenddrzew XML (C#)](./how-to-find-an-element-with-a-specific-attribute.md).  
  
## <a name="modifying-xml-trees"></a>Modyfikowanie drzew XML  
 Element można modyfikować na różne sposoby, w tym zmieniać jego zawartość lub atrybuty. Można również usunąć element z jego elementu nadrzędnego.  
  
 Aby uzyskać więcej informacji, zobacz [Modyfikowanie drzew XML (LINQ do XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).  
  
## <a name="see-also"></a>Zobacz też

- [Omówienie programowania LINQ do XML (C#)](serializing-to-files-textwriters-and-xmlwriters.md)
