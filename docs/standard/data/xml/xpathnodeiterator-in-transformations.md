---
title: "Element XPathNodeIterator w przekształcenia"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 2bc6ddc6-674a-4f75-b264-abc35e4e5857
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 523a4774de9975812838b22bbb5193e59cd58130
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="xpathnodeiterator-in-transformations"></a>Element XPathNodeIterator w przekształcenia
<xref:System.Xml.XPath.XPathNodeIterator> Zawiera metody do wykonywania iteracji zestawu węzłów utworzone w wyniku zapytania XML Path Language (XPath) lub wynikowego fragmentu drzewa przekonwertowane do węzła przy użyciu metody zestaw węzłów. <xref:System.Xml.XPath.XPathNodeIterator> Umożliwia iteracja węzłów w ramach tego zestawu węzłów. Po pobraniu zestawu węzłów <xref:System.Xml.XPath.XPathNodeIterator> klasa udostępnia tylko do odczytu, tylko do przodu kursor do wybranego zestawu węzłów. Zestaw węzłów jest tworzone w kolejności dokumentu wywołaniem tej metody przechodzi do następnego węzła w kolejności dokumentu. <xref:System.Xml.XPath.XPathNodeIterator>nie Konstruuj węzła drzewa wszystkich węzłów w zestawie. Zamiast tego zawiera okno jednego węzła na dane, udostępnianie podstawowej węzła, który wskazuje jako poruszanie się w drzewie. Metody i właściwości dostępne z <xref:System.Xml.XPath.XPathNodeIterator> klasy umożliwiające uzyskiwanie informacji z bieżącego węzła. Aby uzyskać listę dostępnych metod i właściwości, zobacz <xref:System.Windows.Forms.ToolBar>.  
  
 Ponieważ <xref:System.Xml.XPath.XPathNodeIterator> przenosi na zestaw węzłów utworzone na podstawie kwerendy XPath i przejście do tylko, sposób, aby przenieść polega na użyciu <xref:System.Xml.XPath.XPathNodeIterator.MoveNext%2A> metody. Typ zwrotny tej metody jest `Boolean`, zwracająca `true` po przeniesieniu do następnego wybrany węzeł i `false` , jeśli nie ma już wybranych węzłów. Jeśli zmienna zwraca `true`, na poniższej liście przedstawiono dostępne właściwości:  
  
-   <xref:System.Xml.XPath.XPathNodeIterator.Current%2A>  
  
-   <xref:System.Xml.XPath.XPathNodeIterator.CurrentPosition%2A>  
  
-   <xref:System.Xml.XPath.XPathNodeIterator.Count%2A>  
  
 Ustaw podczas szukania w węźle po raz pierwszy, wywołanie <xref:System.Xml.XPath.XPathNodeIterator.MoveNext%2A> muszą zostać wprowadzone w pozycji <xref:System.Xml.XPath.XPathNodeIterator> w pierwszym węźle wybranego zestawu. Dzięki temu chwilę pętli do zapisania.  
  
 Poniższy przykład kodu pokazuje sposób przekazywania <xref:System.Xml.XPath.XPathNodeIterator> do <xref:System.Xml.Xsl.XslTransform> jako parametru w <xref:System.Xml.Xsl.XsltArgumentList>. Wejściowy kod jest **books.xml**, i arkusza stylów jest **text.xsl**. Plik **test.xml** jest <xref:System.Xml.XPath.XPathDocument>.  
  
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
  
## <a name="booksxml"></a>Books.XML  
  
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
  
## <a name="testxsl"></a>Test.xsl  
  
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
  
## <a name="testxml"></a>Test.XML  
  
```xml  
<Title attr="Test">this is a test</Title>  
```  
  
## <a name="output-outxml"></a>Dane wyjściowe (out.xml)  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<out>  
  <title>Seven Years in Trenton</title>  
  <title>History of Trenton</title>  
</out>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Implementowanie procesora XSLT przy użyciu klasy XslTransform](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
