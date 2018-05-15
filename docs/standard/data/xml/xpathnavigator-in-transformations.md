---
title: Element XPathNavigator w przekształcenia
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 118f97d1-7110-4d1b-b0bd-4143252c0bb0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 76cfa51c7d434a6dfdcdc1e6852779decaa601e4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="xpathnavigator-in-transformations"></a><span data-ttu-id="c954d-102">Element XPathNavigator w przekształcenia</span><span class="sxs-lookup"><span data-stu-id="c954d-102">XPathNavigator in Transformations</span></span>
<span data-ttu-id="c954d-103"><xref:System.Xml.XPath.XPathNavigator> Klasy zapewnia dostęp losowy tylko do odczytu do danych i jest przeznaczony do użytku jako dane wejściowe rozszerzalny język arkusza stylów dla przekształceń XSLT ().</span><span class="sxs-lookup"><span data-stu-id="c954d-103">The <xref:System.Xml.XPath.XPathNavigator> class provides read-only random access to data and is designed for use as an input to Extensible Stylesheet Language for Transformations (XSLT).</span></span> <span data-ttu-id="c954d-104">Jest wdrażana w <xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDataDocument>, i <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="c954d-104">It is implemented on the <xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDataDocument>, and <xref:System.Xml.XmlDocument>.</span></span> <span data-ttu-id="c954d-105"><xref:System.Xml.XPath.XPathNavigator> Jest oparty na modelu danych w sieci World Wide Web konsorcjum W3C, zgodnie z opisem w sekcji 5 zalecenie XML Path Language (XPath).</span><span class="sxs-lookup"><span data-stu-id="c954d-105">The <xref:System.Xml.XPath.XPathNavigator> is based upon the World Wide Web Consortium (W3C) Data Model as described in section 5 of the XML Path Language (XPath) recommendation.</span></span>  
  
 <span data-ttu-id="c954d-106"><xref:System.Xml.XPath.XPathNavigator> Definiuje model kursor nad dowolnego magazynu i udostępnia kwerendy XPath szybkie, tylko do odczytu w porównaniu z dowolnego magazynu danych.</span><span class="sxs-lookup"><span data-stu-id="c954d-106">The <xref:System.Xml.XPath.XPathNavigator> defines a cursor model over any store and provides fast, read-only XPath queries over any data store.</span></span> <span data-ttu-id="c954d-107"><xref:System.Xml.XPath.XPathNavigator> Jest również klasy na potrzeby Iterowanie po fragmenty drzewa wynik.</span><span class="sxs-lookup"><span data-stu-id="c954d-107">The <xref:System.Xml.XPath.XPathNavigator> is also the class to use for iterating over result tree fragments.</span></span>  
  
 <span data-ttu-id="c954d-108">Interfejs API umożliwia uzyskiwanie informacji z bieżącego węzła w magazynie i przejdź do połączonych węzłów.</span><span class="sxs-lookup"><span data-stu-id="c954d-108">The API enables you to get information from the current node in the store and move to connected nodes.</span></span> <span data-ttu-id="c954d-109"><xref:System.Xml.XPath.XPathNavigator> Model styl kursor, który wykonuje przechodzenie przez sklep przy użyciu zestawu **Przenieś** metody.</span><span class="sxs-lookup"><span data-stu-id="c954d-109">The <xref:System.Xml.XPath.XPathNavigator> is a cursor style model that performs traversal over a store using a set of **Move** methods.</span></span> <span data-ttu-id="c954d-110"><xref:System.Xml.XPath.XPathNavigator> Zawsze znajduje się w węźle.</span><span class="sxs-lookup"><span data-stu-id="c954d-110">The <xref:System.Xml.XPath.XPathNavigator> is always positioned on a node.</span></span> <span data-ttu-id="c954d-111">Wszelkie **Przenieś** metodę, która kończy się niepowodzeniem pozostawia <xref:System.Xml.XPath.XPathNavigator> bez zmian.</span><span class="sxs-lookup"><span data-stu-id="c954d-111">Any **Move** method that fails leaves the <xref:System.Xml.XPath.XPathNavigator> unchanged.</span></span>  
  
 <span data-ttu-id="c954d-112"><xref:System.Xml.XPath.XPathNavigator> Jest klasa na potrzeby Iterowanie po fragmenty drzewa wynik.</span><span class="sxs-lookup"><span data-stu-id="c954d-112">The <xref:System.Xml.XPath.XPathNavigator> is the class to use for iterating over result tree fragments.</span></span> <span data-ttu-id="c954d-113">Poniższy przykład kodu tworzy wynikowego fragmentu drzewa w arkuszu stylów przez wywołanie funkcji z parametrem `fragment`, który zawiera kod XML.</span><span class="sxs-lookup"><span data-stu-id="c954d-113">The following code sample creates a result tree fragment within a style sheet by calling the function with the parameter, `fragment`, which contains XML.</span></span>  
  
## <a name="testxsl"></a><span data-ttu-id="c954d-114">Test.xsl</span><span class="sxs-lookup"><span data-stu-id="c954d-114">test.xsl</span></span>  
  
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
  
## <a name="testxml"></a><span data-ttu-id="c954d-115">Test.XML</span><span class="sxs-lookup"><span data-stu-id="c954d-115">test.xml</span></span>  
  
```xml  
<root>Some text</root>  
```  
  
 <span data-ttu-id="c954d-116">Poniższy kod używa **test.xsl** arkusza stylów i **test.xml** dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="c954d-116">The following code uses the **test.xsl** style sheet and **test.xml** input data.</span></span>  
  
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
  
## <a name="output"></a><span data-ttu-id="c954d-117">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="c954d-117">Output</span></span>  
 <span data-ttu-id="c954d-118">Wynik transformacji znajduje się w pliku **out.xml**:</span><span class="sxs-lookup"><span data-stu-id="c954d-118">The result of the transformation is found in the file **out.xml**:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>Joe  
```  
  
## <a name="see-also"></a><span data-ttu-id="c954d-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c954d-119">See Also</span></span>  
 [<span data-ttu-id="c954d-120">Implementowanie procesora XSLT przy użyciu klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="c954d-120">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
