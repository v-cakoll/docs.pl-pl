---
title: Klasa XPathNavigator w przekształceniach
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 118f97d1-7110-4d1b-b0bd-4143252c0bb0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 57290af1df8d370c928a97aba1622e41a6a33589
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2018
ms.locfileid: "45668070"
---
# <a name="xpathnavigator-in-transformations"></a>Klasa XPathNavigator w przekształceniach
<xref:System.Xml.XPath.XPathNavigator> Klasy zapewnia dostęp losowy tylko do odczytu do danych i jest przeznaczony do użytku jako dane wejściowe rozszerzalny język arkusza stylów przekształcenia (XSLT). Jest wdrażana w <xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDataDocument>, i <xref:System.Xml.XmlDocument>. <xref:System.Xml.XPath.XPathNavigator> Opartą na modelu danych w sieci World Wide Web Consortium (W3C) zgodnie z opisem w sekcji 5 z zaleceniem XML Path Language (XPath).  
  
 <xref:System.Xml.XPath.XPathNavigator> Definiuje model zarządzanego przez kursor nad dowolnym magazynu i udostępnia szybką, tylko do odczytu kwerendy XPath w porównaniu z dowolnego magazynu danych. <xref:System.Xml.XPath.XPathNavigator> Jest również klasą, na potrzeby Iterowanie fragmenty drzewa wynik.  
  
 Interfejs API umożliwia pobieranie informacji z bieżącego węzła w magazynie i przejść do połączonych węzłów. <xref:System.Xml.XPath.XPathNavigator> Model styl kursor, który wykonuje przechodzenie magazynu, korzystając z zestawu **przenieść** metody. <xref:System.Xml.XPath.XPathNavigator> Zawsze znajduje się w węźle. Wszelkie **przenieść** metodę, która kończy się niepowodzeniem pozostawia <xref:System.Xml.XPath.XPathNavigator> bez zmian.  
  
 <xref:System.Xml.XPath.XPathNavigator> Jest klasa na potrzeby Iterowanie fragmenty drzewa wynik. Poniższy przykład kodu tworzy wynikowego fragmentu drzewa w arkuszu stylów, wywołując funkcję z parametrem `fragment`, który zawiera kod XML.  
  
## <a name="testxsl"></a>Test.xsl  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
                xmlns:msxsl ="urn:schemas-microsoft-com:xslt"  
                xmlns:user="http://www.adventure-works.com"  
                version="1.0">  
  
<xsl:variable name="fragment">  
    <authorlist>  
       <author>Joe</author>  
    </authorlist>  
</xsl:variable>  
  
<msxsl:script language="C#" implements-prefix="user">  
<![CDATA[  
   string NodeFragment(XPathNavigator nav)  
   {  
      if (nav.HasChildren)  
        return nav.Value;  
      else  
        return "";  
   }  
]]>  
</msxsl:script>  
  
<xsl:template match="/">  
     <xsl:value-of select="user:NodeFragment($fragment)"/>  
</xsl:template>  
  
</xsl:stylesheet>  
```  
  
## <a name="testxml"></a>Test.XML  
  
```xml  
<root>Some text</root>  
```  
  
 Poniższy kod używa **test.xsl** arkusza stylów i **test.xml** dane wejściowe.  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.Xsl  
Imports System.Xml.XPath  
Imports System.Text  
Public Class sample  
  
    Public Shared Sub Main()  
        Dim xslt As New XslTransform()  
        xslt.Load("test.xsl")  
  
        Dim xd As New XPathDocument("test.xml")  
  
        Dim strmTemp = New FileStream("out.xml", FileMode.Create, FileAccess.ReadWrite)  
        xslt.Transform(xd, Nothing, strmTemp, Nothing)  
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
        XslTransform xslt = new XslTransform();  
        xslt.Load("test.xsl");  
  
        XPathDocument xd = new XPathDocument("test.xml");  
  
        Stream strmTemp = new FileStream("out.xml", FileMode.Create, FileAccess.ReadWrite);  
        xslt.Transform(xd, null, strmTemp, null);  
    }  
}  
```  
  
## <a name="output"></a>Dane wyjściowe  
 Wynik transformacji znajduje się w pliku **out.xml**:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>Joe  
```  
  
## <a name="see-also"></a>Zobacz także

- [Implementowanie procesora XSLT przy użyciu klasy XslTransform](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
