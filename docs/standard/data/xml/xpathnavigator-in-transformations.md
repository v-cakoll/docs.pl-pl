---
title: Klasa XPathNavigator w przekształceniach
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 118f97d1-7110-4d1b-b0bd-4143252c0bb0
ms.openlocfilehash: 240f9ca7a887a4a146437fdef46de776b299705a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709754"
---
# <a name="xpathnavigator-in-transformations"></a>Klasa XPathNavigator w przekształceniach
Klasa <xref:System.Xml.XPath.XPathNavigator> zapewnia losowy dostęp tylko do odczytu do danych i jest przeznaczona do użycia jako dane wejściowe Extensible Stylesheet Language for Transformations (XSLT). Jest ona zaimplementowana w <xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDataDocument>i <xref:System.Xml.XmlDocument>. <xref:System.Xml.XPath.XPathNavigator> jest oparty na modelu danych organizacja World Wide Web Consortium (W3C) zgodnie z opisem w sekcji 5 zalecenia języka ścieżki XML (XPath).  
  
 <xref:System.Xml.XPath.XPathNavigator> definiuje model kursorów na dowolnym sklepie i zapewnia szybkie, tylko do odczytu zapytania XPath dla każdego magazynu danych. <xref:System.Xml.XPath.XPathNavigator> jest również klasą używaną do iteracji względem fragmentów drzewa wyników.  
  
 Interfejs API umożliwia uzyskanie informacji z bieżącego węzła w sklepie i przejście do podłączonych węzłów. <xref:System.Xml.XPath.XPathNavigator> to model stylu kursora, który przeprowadza przechodzenie przez magazyn przy użyciu zestawu metod **przenoszenia** . <xref:System.Xml.XPath.XPathNavigator> jest zawsze umieszczana w węźle. Jakakolwiek metoda **przenoszenia** , która kończy się niepowodzeniem, pozostawia <xref:System.Xml.XPath.XPathNavigator> bez zmian.  
  
 <xref:System.Xml.XPath.XPathNavigator> jest klasą, która ma być używana do iterowania fragmentów drzewa wyników. Poniższy przykład kodu tworzy fragment drzewa wyników w arkuszu stylów, wywołując funkcję z parametrem `fragment`, który zawiera kod XML.  
  
## <a name="testxsl"></a>test.xsl  
  
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
  
## <a name="testxml"></a>Test. XML  
  
```xml  
<root>Some text</root>  
```  
  
 Poniższy kod używa arkusza stylów **test. xsl** i danych wejściowych **test. XML** .  
  
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
 Wynik transformacji zostanie znaleziony w pliku **out. XML**:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>Joe  
```  
  
## <a name="see-also"></a>Zobacz także

- [Implementowanie procesora XSLT przy użyciu klasy XslTransform](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
