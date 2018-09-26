---
title: Klasa XPathNodeIterator w przekształceniach
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 2bc6ddc6-674a-4f75-b264-abc35e4e5857
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6f71d409729707f4af93fd7f8d5b82a99404579b
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47077268"
---
# <a name="xpathnodeiterator-in-transformations"></a><span data-ttu-id="198a2-102">Klasa XPathNodeIterator w przekształceniach</span><span class="sxs-lookup"><span data-stu-id="198a2-102">XPathNodeIterator in Transformations</span></span>
<span data-ttu-id="198a2-103"><xref:System.Xml.XPath.XPathNodeIterator> Zawiera metody do wykonywania iteracji zestaw węzłów utworzone w wyniku kwerendy XML Path Language (XPath) lub wynikowego fragmentu drzewa, konwertowana do węzła przy użyciu metody zestawu węzłów.</span><span class="sxs-lookup"><span data-stu-id="198a2-103">The <xref:System.Xml.XPath.XPathNodeIterator> provides methods to iterate over a set of nodes created as the result of an XML Path Language (XPath) query or a result tree fragment converted to a node set by use of the node-set method.</span></span> <span data-ttu-id="198a2-104"><xref:System.Xml.XPath.XPathNodeIterator> Umożliwia iteracyjne przeglądanie węzłów w ramach tego zestawu węzłów.</span><span class="sxs-lookup"><span data-stu-id="198a2-104">The <xref:System.Xml.XPath.XPathNodeIterator> enables you to iterate over the nodes within that node set.</span></span> <span data-ttu-id="198a2-105">Po pobraniu zestawu węzłów <xref:System.Xml.XPath.XPathNodeIterator> klasa udostępnia tylko do odczytu, tylko do przodu kursor do wybranego zestawu węzłów.</span><span class="sxs-lookup"><span data-stu-id="198a2-105">Once a node set is retrieved, the <xref:System.Xml.XPath.XPathNodeIterator> class provides a read-only, forward-only cursor to the selected set of nodes.</span></span> <span data-ttu-id="198a2-106">Zestaw węzłów jest tworzone w kolejności dokumentu, wywołanie tej metody przechodzi do następnego węzła w kolejności dokumentu.</span><span class="sxs-lookup"><span data-stu-id="198a2-106">The node set is created in document order, so calling this method moves to the next node in document order.</span></span> <span data-ttu-id="198a2-107"><xref:System.Xml.XPath.XPathNodeIterator> nie są kompilowane w węźle drzewa wszystkich węzłów w zestawie.</span><span class="sxs-lookup"><span data-stu-id="198a2-107"><xref:System.Xml.XPath.XPathNodeIterator> does not build a node tree of all the nodes in the set.</span></span> <span data-ttu-id="198a2-108">Zamiast tego zapewnia okno z jednego węzła do danych, udostępnianie węzła podstawowego, który wskazuje on, ponieważ poruszanie się w drzewie.</span><span class="sxs-lookup"><span data-stu-id="198a2-108">Instead, it provides a single node window into the data, exposing the underlying node it points to as you move around in the tree.</span></span> <span data-ttu-id="198a2-109">Metody i właściwości dostępne z <xref:System.Xml.XPath.XPathNodeIterator> klasy pozwalają użytkownikom czerpać informacje z bieżącego węzła.</span><span class="sxs-lookup"><span data-stu-id="198a2-109">The methods and properties available from the <xref:System.Xml.XPath.XPathNodeIterator> class enable you to get information from the current node.</span></span> <span data-ttu-id="198a2-110">Aby uzyskać listę dostępnych metod i właściwości, zobacz <xref:System.Windows.Forms.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="198a2-110">For a list of the available methods and properties, see <xref:System.Windows.Forms.ToolBar>.</span></span>  
  
 <span data-ttu-id="198a2-111">Ponieważ <xref:System.Xml.XPath.XPathNodeIterator> przechodzi przez zestaw węzłów utworzone na podstawie zapytania XPath i przejście do tylko, umożliwiają przeniesienie znajduje się za pomocą <xref:System.Xml.XPath.XPathNodeIterator.MoveNext%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="198a2-111">Since an <xref:System.Xml.XPath.XPathNodeIterator> moves over a set of nodes created from an XPath query and moves forward only, the way to move is by using the <xref:System.Xml.XPath.XPathNodeIterator.MoveNext%2A> method.</span></span> <span data-ttu-id="198a2-112">Typ zwracany przez tę metodę jest `Boolean`, zwracanie `true` po przeniesieniu do następnego wybrany węzeł i `false` przypadku nie ma więcej wybranych węzłów.</span><span class="sxs-lookup"><span data-stu-id="198a2-112">The return type of this method is `Boolean`, returning `true` if it moves to the next selected node, and `false` if there are no more selected nodes.</span></span> <span data-ttu-id="198a2-113">Jeśli zostanie zwrócona `true`, na poniższej liście przedstawiono dostępne właściwości:</span><span class="sxs-lookup"><span data-stu-id="198a2-113">If it returns `true`, the following list shows the properties available:</span></span>  
  
-   <xref:System.Xml.XPath.XPathNodeIterator.Current%2A>  
  
-   <xref:System.Xml.XPath.XPathNodeIterator.CurrentPosition%2A>  
  
-   <xref:System.Xml.XPath.XPathNodeIterator.Count%2A>  
  
 <span data-ttu-id="198a2-114">Kiedy przeglądasz węzła ustawić po raz pierwszy, po wywołaniu <xref:System.Xml.XPath.XPathNodeIterator.MoveNext%2A> muszą zostać wprowadzone pozycji <xref:System.Xml.XPath.XPathNodeIterator> w pierwszym węźle wybranego zestawu.</span><span class="sxs-lookup"><span data-stu-id="198a2-114">When you are looking at a node set for the first time, a call to <xref:System.Xml.XPath.XPathNodeIterator.MoveNext%2A> must be made to position the <xref:System.Xml.XPath.XPathNodeIterator> on the first node of the selected set.</span></span> <span data-ttu-id="198a2-115">Dzięki temu chwilę pętli do zapisania.</span><span class="sxs-lookup"><span data-stu-id="198a2-115">This allows a while loop to be written.</span></span>  
  
 <span data-ttu-id="198a2-116">Poniższy przykład kodu pokazuje sposób przekazywania <xref:System.Xml.XPath.XPathNodeIterator> do <xref:System.Xml.Xsl.XslTransform> jako parametr w <xref:System.Xml.Xsl.XsltArgumentList>.</span><span class="sxs-lookup"><span data-stu-id="198a2-116">The following code example shows how to pass an <xref:System.Xml.XPath.XPathNodeIterator> to an <xref:System.Xml.Xsl.XslTransform> as a parameter in the <xref:System.Xml.Xsl.XsltArgumentList>.</span></span> <span data-ttu-id="198a2-117">Dane wejściowe do kodu **books.xml**, i arkusz stylów jest **text.xsl**.</span><span class="sxs-lookup"><span data-stu-id="198a2-117">The input to the code is **books.xml**, and the style sheet is **text.xsl**.</span></span> <span data-ttu-id="198a2-118">Plik **test.xml** jest <xref:System.Xml.XPath.XPathDocument>.</span><span class="sxs-lookup"><span data-stu-id="198a2-118">The file **test.xml** is the <xref:System.Xml.XPath.XPathDocument>.</span></span>  
  
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
  
## <a name="booksxml"></a><span data-ttu-id="198a2-119">Books.XML</span><span class="sxs-lookup"><span data-stu-id="198a2-119">books.xml</span></span>  
  
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
  
## <a name="testxsl"></a><span data-ttu-id="198a2-120">Test.xsl</span><span class="sxs-lookup"><span data-stu-id="198a2-120">test.xsl</span></span>  
  
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
  
## <a name="testxml"></a><span data-ttu-id="198a2-121">Test.XML</span><span class="sxs-lookup"><span data-stu-id="198a2-121">test.xml</span></span>  
  
```xml  
<Title attr="Test">this is a test</Title>  
```  
  
## <a name="output-outxml"></a><span data-ttu-id="198a2-122">Dane wyjściowe (out.xml)</span><span class="sxs-lookup"><span data-stu-id="198a2-122">Output (out.xml)</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<out>  
  <title>Seven Years in Trenton</title>  
  <title>History of Trenton</title>  
</out>  
```  
  
## <a name="see-also"></a><span data-ttu-id="198a2-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="198a2-123">See also</span></span>

- [<span data-ttu-id="198a2-124">Implementowanie procesora XSLT przy użyciu klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="198a2-124">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
