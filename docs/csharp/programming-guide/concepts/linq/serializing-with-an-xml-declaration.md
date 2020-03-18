---
title: Serializacja za pomocą deklaracji XML (C#)
ms.date: 07/20/2015
ms.assetid: c237fa4a-a042-40fd-886f-17b54c66bb75
ms.openlocfilehash: 4533d69f2b0bee68b4adee6e18fe28dde18078ae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "66483485"
---
# <a name="serializing-with-an-xml-declaration-c"></a>Serializacja za pomocą deklaracji XML (C#)
W tym temacie opisano, jak kontrolować, czy serializacja generuje deklarację XML.  
  
## <a name="xml-declaration-generation"></a>Generowanie deklaracji XML  
 Serializacji do <xref:System.IO.File> lub <xref:System.IO.TextWriter> przy <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> użyciu <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> metody lub metody generuje deklarację XML. Podczas serializacji do <xref:System.Xml.XmlWriter>, ustawienia modułu zapisu <xref:System.Xml.XmlWriterSettings> (określone w obiekcie) określić, czy deklaracja XML jest generowany, czy nie.  
  
 Jeśli serializacji do ciągu przy `ToString` użyciu metody, wynikowy Kod XML nie będzie zawierać deklarację XML.  
  
### <a name="serializing-with-an-xml-declaration"></a>Serializowanie przy użyciu deklaracji XML  
 Poniższy przykład tworzy <xref:System.Xml.Linq.XElement>plik , zapisuje dokument w pliku, a następnie drukuje plik na konsoli:  
  
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
 W poniższym przykładzie pokazano, jak zapisać do <xref:System.Xml.Linq.XElement> . <xref:System.Xml.XmlWriter>  
  
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

- [Serializujące drzewa XML (C#)](serializing-to-files-textwriters-and-xmlwriters.md)
