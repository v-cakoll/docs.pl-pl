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
# <a name="xpathnavigator-in-transformations"></a><span data-ttu-id="a6fe6-102">Klasa XPathNavigator w przekształceniach</span><span class="sxs-lookup"><span data-stu-id="a6fe6-102">XPathNavigator in Transformations</span></span>
<span data-ttu-id="a6fe6-103"><xref:System.Xml.XPath.XPathNavigator> Klasa zapewnia dostęp losowy tylko do odczytu do danych i jest przeznaczona do użycia jako dane wejściowe do Extensible Stylesheet Language for Transformations (XSLT).</span><span class="sxs-lookup"><span data-stu-id="a6fe6-103">The <xref:System.Xml.XPath.XPathNavigator> class provides read-only random access to data and is designed for use as an input to Extensible Stylesheet Language for Transformations (XSLT).</span></span> <span data-ttu-id="a6fe6-104">Jest ona zaimplementowana <xref:System.Xml.XPath.XPathDocument>w <xref:System.Xml.XmlDataDocument>,, <xref:System.Xml.XmlDocument>i.</span><span class="sxs-lookup"><span data-stu-id="a6fe6-104">It is implemented on the <xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDataDocument>, and <xref:System.Xml.XmlDocument>.</span></span> <span data-ttu-id="a6fe6-105"><xref:System.Xml.XPath.XPathNavigator> Jest oparty na modelu danych organizacja World Wide Web Consortium (W3C) zgodnie z opisem w sekcji 5 zalecenia XML Path Language (XPath).</span><span class="sxs-lookup"><span data-stu-id="a6fe6-105">The <xref:System.Xml.XPath.XPathNavigator> is based upon the World Wide Web Consortium (W3C) Data Model as described in section 5 of the XML Path Language (XPath) recommendation.</span></span>  
  
 <span data-ttu-id="a6fe6-106"><xref:System.Xml.XPath.XPathNavigator> Definiuje model kursora na dowolnym sklepie i zapewnia szybkie, tylko do odczytu zapytania XPath w dowolnym magazynie danych.</span><span class="sxs-lookup"><span data-stu-id="a6fe6-106">The <xref:System.Xml.XPath.XPathNavigator> defines a cursor model over any store and provides fast, read-only XPath queries over any data store.</span></span> <span data-ttu-id="a6fe6-107"><xref:System.Xml.XPath.XPathNavigator> Jest również klasą używaną do iteracji względem fragmentów drzewa wyników.</span><span class="sxs-lookup"><span data-stu-id="a6fe6-107">The <xref:System.Xml.XPath.XPathNavigator> is also the class to use for iterating over result tree fragments.</span></span>  
  
 <span data-ttu-id="a6fe6-108">Interfejs API umożliwia uzyskanie informacji z bieżącego węzła w sklepie i przejście do podłączonych węzłów.</span><span class="sxs-lookup"><span data-stu-id="a6fe6-108">The API enables you to get information from the current node in the store and move to connected nodes.</span></span> <span data-ttu-id="a6fe6-109"><xref:System.Xml.XPath.XPathNavigator> Jest modelem stylu kursora, który przeprowadza przechodzenie przez magazyn przy użyciu zestawu metod **przenoszenia** .</span><span class="sxs-lookup"><span data-stu-id="a6fe6-109">The <xref:System.Xml.XPath.XPathNavigator> is a cursor style model that performs traversal over a store using a set of **Move** methods.</span></span> <span data-ttu-id="a6fe6-110">Element <xref:System.Xml.XPath.XPathNavigator> jest zawsze umieszczony na węźle.</span><span class="sxs-lookup"><span data-stu-id="a6fe6-110">The <xref:System.Xml.XPath.XPathNavigator> is always positioned on a node.</span></span> <span data-ttu-id="a6fe6-111">Wszelkie metody **przenoszenia** , które nie powiodło się, opuszczają <xref:System.Xml.XPath.XPathNavigator> niezmienione.</span><span class="sxs-lookup"><span data-stu-id="a6fe6-111">Any **Move** method that fails leaves the <xref:System.Xml.XPath.XPathNavigator> unchanged.</span></span>  
  
 <span data-ttu-id="a6fe6-112"><xref:System.Xml.XPath.XPathNavigator> Jest klasą, która ma być używana do iterowania fragmentów drzewa wyników.</span><span class="sxs-lookup"><span data-stu-id="a6fe6-112">The <xref:System.Xml.XPath.XPathNavigator> is the class to use for iterating over result tree fragments.</span></span> <span data-ttu-id="a6fe6-113">Poniższy przykład kodu tworzy fragment drzewa wyników w arkuszu stylów, wywołując funkcję z parametrem, `fragment`, który zawiera kod XML.</span><span class="sxs-lookup"><span data-stu-id="a6fe6-113">The following code sample creates a result tree fragment within a style sheet by calling the function with the parameter, `fragment`, which contains XML.</span></span>  
  
## <a name="testxsl"></a><span data-ttu-id="a6fe6-114">Test. xsl</span><span class="sxs-lookup"><span data-stu-id="a6fe6-114">test.xsl</span></span>  
  
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
  
## <a name="testxml"></a><span data-ttu-id="a6fe6-115">Test. XML</span><span class="sxs-lookup"><span data-stu-id="a6fe6-115">test.xml</span></span>  
  
```xml  
<root>Some text</root>  
```  
  
 <span data-ttu-id="a6fe6-116">Poniższy kod używa arkusza stylów **test. xsl** i danych wejściowych **test. XML** .</span><span class="sxs-lookup"><span data-stu-id="a6fe6-116">The following code uses the **test.xsl** style sheet and **test.xml** input data.</span></span>  
  
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
  
## <a name="output"></a><span data-ttu-id="a6fe6-117">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="a6fe6-117">Output</span></span>  
 <span data-ttu-id="a6fe6-118">Wynik transformacji zostanie znaleziony w pliku **out. XML**:</span><span class="sxs-lookup"><span data-stu-id="a6fe6-118">The result of the transformation is found in the file **out.xml**:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>Joe  
```  
  
## <a name="see-also"></a><span data-ttu-id="a6fe6-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a6fe6-119">See also</span></span>

- [<span data-ttu-id="a6fe6-120">Implementowanie procesora XSLT przy użyciu klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="a6fe6-120">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
