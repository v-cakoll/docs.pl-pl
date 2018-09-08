---
title: Serializowanie przy użyciu deklaracji XML (C#)
ms.date: 07/20/2015
ms.assetid: c237fa4a-a042-40fd-886f-17b54c66bb75
ms.openlocfilehash: 613280efc8c734c53c4af9252b4b83e2dd942f36
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44132665"
---
# <a name="serializing-with-an-xml-declaration-c"></a>Serializowanie przy użyciu deklaracji XML (C#)
W tym temacie opisano sposób kontroluje, czy serializacji generuje deklaracji XML.  
  
## <a name="xml-declaration-generation"></a>Generowanie deklaracji XML  
 Serializowanie do <xref:System.IO.File> lub <xref:System.IO.TextWriter> przy użyciu <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> metody lub <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> metoda generuje deklaracji XML. Podczas serializacji do <xref:System.Xml.XmlWriter>, ustawień edytora (określony w <xref:System.Xml.XmlWriterSettings> obiektu) określić, czy deklaracja XML jest generowany, czy nie.  
  
 Jeśli są serializacji na ciąg za pośrednictwem `ToString` metody, wynikowy kod XML nie zostaną uwzględnione w deklaracji XML.  
  
### <a name="serializing-with-an-xml-declaration"></a>Serializowanie przy użyciu deklaracji XML  
 Poniższy przykład tworzy <xref:System.Xml.Linq.XElement>, zapisuje dokument do pliku, a następnie drukuje pliku do konsoli:  
  
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
 Poniższy przykład pokazuje, jak zapisać <xref:System.Xml.Linq.XElement> do <xref:System.Xml.XmlWriter>.  
  
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

- [Serializowanie drzew XML (C#)](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)
