---
title: Serializowanie przy użyciu deklaracji XML
ms.date: 07/20/2015
ms.assetid: 8726f79e-2bb0-4ba0-969d-197cca591647
ms.openlocfilehash: 96c95b4c94290016684721a194ca31a836a49740
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350634"
---
# <a name="serializing-with-an-xml-declaration-visual-basic"></a>Serializacja przy użyciu deklaracji XML (Visual Basic)
W tym temacie opisano sposób kontrolowania, czy Serializacja generuje deklarację XML.  
  
## <a name="xml-declaration-generation"></a>Generowanie deklaracji XML  
 Serializacja do <xref:System.IO.File> lub <xref:System.IO.TextWriter> przy użyciu metody <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> lub metody <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> generuje deklarację XML. Podczas serializacji do <xref:System.Xml.XmlWriter>ustawienia składnika zapisywania (określone w obiekcie <xref:System.Xml.XmlWriterSettings>) określają, czy deklaracja XML jest generowana, czy nie.  
  
 W przypadku serializacji do ciągu przy użyciu metody `ToString`, otrzymany kod XML nie będzie zawierał deklaracji XML.  
  
### <a name="serializing-with-an-xml-declaration"></a>Serializowanie przy użyciu deklaracji XML  
 Poniższy przykład tworzy <xref:System.Xml.Linq.XElement>, zapisuje dokument do pliku, a następnie drukuje plik do konsoli programu:  
  
```vb  
Dim root As XElement = <Root>  
                           <Child>child content</Child>  
                       </Root>  
root.Save("Root.xml")  
Dim str As String = File.ReadAllText("Root.xml")  
Console.WriteLine(str)  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Child>child content</Child>  
</Root>  
```  
  
### <a name="serializing-without-an-xml-declaration"></a>Serializacja bez deklaracji XML  
 Poniższy przykład pokazuje, jak zapisać <xref:System.Xml.Linq.XElement> w <xref:System.Xml.XmlWriter>.  
  
```vb  
Dim sb As StringBuilder = New StringBuilder()  
Dim xws As XmlWriterSettings = New XmlWriterSettings()  
xws.OmitXmlDeclaration = True  
  
Using xw As XmlWriter = XmlWriter.Create(sb, xws)  
    Dim root = <Root>  
                   <Child>child content</Child>  
               </Root>  
    root.Save(xw)  
End Using  
Console.WriteLine(sb.ToString())  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Root><Child>child content</Child></Root>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Serializowanie drzew XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
