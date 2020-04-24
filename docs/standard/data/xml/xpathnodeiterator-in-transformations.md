---
title: Klasa XPathNodeIterator w przekształceniach
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 2bc6ddc6-674a-4f75-b264-abc35e4e5857
ms.openlocfilehash: 63beeb3ca9d3f3cb6e6bde418e99ee2bd0a12e20
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709741"
---
# <a name="xpathnodeiterator-in-transformations"></a>Klasa XPathNodeIterator w przekształceniach
<xref:System.Xml.XPath.XPathNodeIterator> Zapewnia metody do iteracji nad zestawem węzłów utworzonych w wyniku zapytania XML Path Language (XPath) lub fragmentu drzewa wynik przekonwertowany na węzeł ustawiony za pomocą metody zestawu węzłów. <xref:System.Xml.XPath.XPathNodeIterator> Pozwala na iterację węzłów w tym zestawie węzłów. Po pobraniu zestawu węzłów <xref:System.Xml.XPath.XPathNodeIterator> Klasa zawiera kursor tylko do odczytu, który przesunięty do wybranego zestawu węzłów. Zestaw węzłów jest tworzony w kolejności dokumentu, dlatego wywołanie tej metody jest przenoszone do następnego węzła w kolejności dokumentu. <xref:System.Xml.XPath.XPathNodeIterator>nie kompiluje drzewa węzłów wszystkich węzłów w zestawie. Zamiast tego zapewnia ono pojedyncze okno węzła do danych, udostępniając węzeł podstawowy, który wskazuje, w miarę poruszania się w drzewie. Metody i właściwości dostępne z <xref:System.Xml.XPath.XPathNodeIterator> klasy umożliwiają uzyskanie informacji z bieżącego węzła. Listę dostępnych metod i właściwości można znaleźć w temacie <xref:System.Windows.Forms.ToolBar>.  
  
 Ponieważ <xref:System.Xml.XPath.XPathNodeIterator> przenosi się na zestaw węzłów utworzonych na podstawie zapytania XPath i przenosi tylko do przodu, <xref:System.Xml.XPath.XPathNodeIterator.MoveNext%2A> Metoda przenoszenia odbywa się przy użyciu metody. Zwracany typ tej metody to `Boolean`, zwracając `true` jeśli przechodzi do następnego wybranego węzła i `false` Jeśli nie ma więcej wybranych węzłów. Jeśli zwróci `true`, Poniższa lista zawiera dostępne właściwości:  
  
- <xref:System.Xml.XPath.XPathNodeIterator.Current%2A>  
  
- <xref:System.Xml.XPath.XPathNodeIterator.CurrentPosition%2A>  
  
- <xref:System.Xml.XPath.XPathNodeIterator.Count%2A>  
  
 Gdy przeglądasz węzeł zestaw po raz pierwszy, wywołanie <xref:System.Xml.XPath.XPathNodeIterator.MoveNext%2A> musi być wykonane w celu umieszczenia <xref:System.Xml.XPath.XPathNodeIterator> na pierwszym węźle wybranego zestawu. Pozwala to na zapisanie pętli while.  
  
 Poniższy przykład kodu pokazuje, jak przekazać obiekt <xref:System.Xml.XPath.XPathNodeIterator> <xref:System.Xml.Xsl.XslTransform> jako parametr w. <xref:System.Xml.Xsl.XsltArgumentList> Dane wejściowe do kodu to **Books. XML**, a arkusz stylów to **Text. xsl**. Plik **test. XML** jest <xref:System.Xml.XPath.XPathDocument>.  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.Xsl  
Imports System.Xml.XPath  
Imports System.Text  
  
Public Class sample  
  
   Public Shared Sub Main()  
      Dim Doc As New XPathDocument("books.xml")  
      Dim nav As XPathNavigator = Doc.CreateNavigator()  
      Dim Iterator As XPathNodeIterator = nav.Select("/bookstore/book")  
  
      Dim arg As New XsltArgumentList()  
      arg.AddParam("param1", "", Iterator)  
  
      Dim xslt As New XslTransform()  
      xslt.Load("test.xsl")  
  
      Dim xd As New XPathDocument("test.xml")  
  
      Dim strmTemp = New FileStream("out.xml", FileMode.Create, FileAccess.ReadWrite)  
      xslt.Transform(xd, arg, strmTemp, Nothing)  
   End Sub 'Main  
End Class 'sample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.Xsl;  
using System.Xml.XPath;  
using System.Text;  
  
public class sample  
{  
    public static void Main()  
    {  
        XPathDocument Doc = new XPathDocument("books.xml");  
        XPathNavigator nav = Doc.CreateNavigator();  
        XPathNodeIterator Iterator = nav.Select("/bookstore/book");  
  
        XsltArgumentList arg = new XsltArgumentList();  
        arg.AddParam("param1", "", Iterator);  
  
        XslTransform xslt = new XslTransform();  
        xslt.Load("test.xsl");  
  
        XPathDocument xd = new XPathDocument("test.xml");  
  
        Stream strmTemp = new FileStream("out.xml", FileMode.Create, FileAccess.ReadWrite);  
        xslt.Transform(xd, arg, strmTemp, null);  
    }  
}  
```  
  
## <a name="booksxml"></a>Books. XML  
  
```xml  
<?xml version='1.0'?>  
<!-- This file represents a fragment of a book store inventory database. -->  
<bookstore specialty="novel">  
    <book style="autobiography">  
    <title>Seven Years in Trenton</title>  
        <author>  
            <first-name>Jay</first-name>  
            <last-name>Adams</last-name>  
            <award>Trenton Literary Review Honorable Mention</award>  
            <country>USA</country>  
        </author>  
        <price>12</price>  
    </book>  
    <book style="textbook">  
        <title>History of Trenton</title>  
        <author>  
            <first-name>Kim</first-name>  
            <last-name>Akers</last-name>  
            <publication>  
                Selected Short Stories of  
                <first-name>Scott</first-name>  
                <last-name>Bishop</last-name>  
                <country>US</country>  
            </publication>  
        </author>  
        <price>55</price>  
    </book>  
</bookstore>  
```  
  
## <a name="testxsl"></a>Test. xsl  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
xmlns:msxsl="urn:schemas-microsoft-com:xslt" exclude-result-prefixes="msxsl">  
  
<xsl:output method="xml" indent="yes"/>  
<xsl:param name="param1"/>  
  
<xsl:template match="/">  
    <out>  
        <xsl:for-each select="$param1/title">  
            <title><xsl:value-of select="."/></title>  
        </xsl:for-each>  
    </out>  
</xsl:template>  
  
</xsl:stylesheet>  
```  
  
## <a name="testxml"></a>Test. XML  
  
```xml  
<Title attr="Test">this is a test</Title>  
```  
  
## <a name="output-outxml"></a>Wyjście (out. xml)  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<out>  
  <title>Seven Years in Trenton</title>  
  <title>History of Trenton</title>  
</out>  
```  
  
## <a name="see-also"></a>Zobacz też

- [Implementowanie procesora XSLT przy użyciu klasy XslTransform](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
