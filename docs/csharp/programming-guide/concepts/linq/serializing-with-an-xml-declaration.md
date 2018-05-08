---
title: Serializacja z deklaracją XML (C#)
ms.date: 07/20/2015
ms.assetid: c237fa4a-a042-40fd-886f-17b54c66bb75
ms.openlocfilehash: 3f331f1226e7e5a905471f4a793f9a415bdd858a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="serializing-with-an-xml-declaration-c"></a>Serializacja z deklaracją XML (C#)
W tym temacie opisano sposób kontrolowania, czy serializacji generuje deklaracji XML.  
  
## <a name="xml-declaration-generation"></a>Generowanie deklaracji XML  
 Serializacja do <xref:System.IO.File> lub <xref:System.IO.TextWriter> przy użyciu <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> metody lub <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> metoda generuje deklaracji XML. Podczas serializacji do <xref:System.Xml.XmlWriter>, ustawień edytora (określony w <xref:System.Xml.XmlWriterSettings> obiektu) ustalić, czy deklaracja XML jest generowany, czy nie.  
  
 Jeśli są serializacji przy użyciu ciągu `ToString` metody, wynikowy kod XML nie zostaną uwzględnione w deklaracji XML.  
  
### <a name="serializing-with-an-xml-declaration"></a>Serializacja z deklaracją XML  
 Poniższy przykład tworzy <xref:System.Xml.Linq.XElement>, dokument jest zapisywany do pliku i następnie drukuje plik do konsoli:  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child", "child content")  
);  
root.Save("Root.xml");  
string str = File.ReadAllText("Root.xml");  
Console.WriteLine(str);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Child>child content</Child>  
</Root>  
```  
  
### <a name="serializing-without-an-xml-declaration"></a>Serializacja bez deklaracji XML  
 Poniższy przykład przedstawia sposób zapisania <xref:System.Xml.Linq.XElement> do <xref:System.Xml.XmlWriter>.  
  
```csharp  
StringBuilder sb = new StringBuilder();  
XmlWriterSettings xws = new XmlWriterSettings();  
xws.OmitXmlDeclaration = true;  
  
using (XmlWriter xw = XmlWriter.Create(sb, xws)) {  
    XElement root = new XElement("Root",  
        new XElement("Child", "child content")  
    );  
    root.Save(xw);  
}  
Console.WriteLine(sb.ToString());  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Root><Child>child content</Child></Root>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Serializacja XML drzew (C#)](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)
