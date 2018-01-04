---
title: "Element XPathNavigator w przekształcenia"
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
ms.assetid: 118f97d1-7110-4d1b-b0bd-4143252c0bb0
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c492d470fe29041f32039d98ecb854e18f40423c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="xpathnavigator-in-transformations"></a>Element XPathNavigator w przekształcenia
<xref:System.Xml.XPath.XPathNavigator> Klasy zapewnia dostęp losowy tylko do odczytu do danych i jest przeznaczony do użytku jako dane wejściowe rozszerzalny język arkusza stylów dla przekształceń XSLT (). Jest wdrażana w <xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDataDocument>, i <xref:System.Xml.XmlDocument>. <xref:System.Xml.XPath.XPathNavigator> Jest oparty na modelu danych w sieci World Wide Web konsorcjum W3C, zgodnie z opisem w sekcji 5 zalecenie XML Path Language (XPath).  
  
 <xref:System.Xml.XPath.XPathNavigator> Definiuje model kursor nad dowolnego magazynu i udostępnia kwerendy XPath szybkie, tylko do odczytu w porównaniu z dowolnego magazynu danych. <xref:System.Xml.XPath.XPathNavigator> Jest również klasy na potrzeby Iterowanie po fragmenty drzewa wynik.  
  
 Interfejs API umożliwia uzyskiwanie informacji z bieżącego węzła w magazynie i przejdź do połączonych węzłów. <xref:System.Xml.XPath.XPathNavigator> Model styl kursor, który wykonuje przechodzenie przez sklep przy użyciu zestawu **Przenieś** metody. <xref:System.Xml.XPath.XPathNavigator> Zawsze znajduje się w węźle. Wszelkie **Przenieś** metodę, która kończy się niepowodzeniem pozostawia <xref:System.Xml.XPath.XPathNavigator> bez zmian.  
  
 <xref:System.Xml.XPath.XPathNavigator> Jest klasa na potrzeby Iterowanie po fragmenty drzewa wynik. Poniższy przykład kodu tworzy wynikowego fragmentu drzewa w arkuszu stylów przez wywołanie funkcji z parametrem `fragment`, który zawiera kod XML.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Implementowanie procesora XSLT przy użyciu klasy XslTransform](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
