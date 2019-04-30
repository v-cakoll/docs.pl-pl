---
title: Zestawy węzłów w przekształceniach
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: ad034f0e-ff8b-4a71-9a4c-528c754263c4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 23632a5df10c1ab2d1afa654d5438a4ebd903d5f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698840"
---
# <a name="node-sets-in-transformations"></a><span data-ttu-id="b72e4-102">Zestawy węzłów w przekształceniach</span><span class="sxs-lookup"><span data-stu-id="b72e4-102">Node Sets in Transformations</span></span>
<span data-ttu-id="b72e4-103">Węzeł zestawy są zestawu obejmującego cztery typy danych podstawowych, które są zwracane z wyrażeniami języka ścieżki XML (XPath).</span><span class="sxs-lookup"><span data-stu-id="b72e4-103">Node sets are one of four basic data types that are returned from XML Path Language (XPath) expressions.</span></span> <span data-ttu-id="b72e4-104">Zestaw węzłów, który jest nieuporządkowanej kolekcji węzłów bez duplikatów, utworzone w kolejności dokumentu, można przypisać do zmiennej w arkuszu stylów.</span><span class="sxs-lookup"><span data-stu-id="b72e4-104">A node set, which is an unordered collection of nodes without duplicates, created in document order, can be assigned to a variable in a style sheet.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b72e4-105"><xref:System.Xml.Xsl.XslTransform> Klasy jest przestarzała w [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b72e4-105">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="b72e4-106">Można przeprowadzić rozszerzalny język arkusza stylów dla przekształceń przekształcenia (XSLT) przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy.</span><span class="sxs-lookup"><span data-stu-id="b72e4-106">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="b72e4-107">Zobacz [używanie klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) i [Migrowanie z klasy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="b72e4-107">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="b72e4-108">Węzeł zestawy są zestawu obejmującego cztery typy danych podstawowych, które są zwracane z wyrażenia XPath.</span><span class="sxs-lookup"><span data-stu-id="b72e4-108">Node sets are one of four basic data types that are returned from XPath expressions.</span></span> <span data-ttu-id="b72e4-109">Zestaw węzłów, który jest nieuporządkowanej kolekcji węzłów bez duplikatów, utworzone w kolejności dokumentu, można przypisać do zmiennej w arkuszu stylów.</span><span class="sxs-lookup"><span data-stu-id="b72e4-109">A node set, which is an unordered collection of nodes without duplicates, created in document order, can be assigned to a variable in a style sheet.</span></span> <span data-ttu-id="b72e4-110">Zestawu węzłów, który jest wynikiem użyte w wyrażenie XPath `select` atrybutu w transformacji, ma takie samo zachowanie jako węzeł zestawu z XML Document Object Model (DOM).</span><span class="sxs-lookup"><span data-stu-id="b72e4-110">This node set, which is a result of an XPath expression used in a `select` attribute in a transformation, has the same behavior as a node set from the XML Document Object Model (DOM).</span></span> <span data-ttu-id="b72e4-111">Możesz przejść węzłem, korzystając z zestawu metod pokazano w [węzła zestawu nawigacji przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md), w przeciwieństwie do wynikowego fragmentu drzewa lub wynikowego fragmentu drzewa, która używa <xref:System.Xml.XPath.XPathNodeIterator> nawigacji.</span><span class="sxs-lookup"><span data-stu-id="b72e4-111">You can navigate a node set using a set of methods shown in [Node Set Navigation Using XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md), unlike a result tree fragment or result tree fragment, which uses the <xref:System.Xml.XPath.XPathNodeIterator> for navigation.</span></span>  
  
 <span data-ttu-id="b72e4-112">Poniższy przykładowy kod przedstawia sposób iterowania przez zestaw węzłów, gdy `variable` lub `parameter` elementu w arkuszu stylów zwróci zestawu węzłów.</span><span class="sxs-lookup"><span data-stu-id="b72e4-112">The following code sample shows how to iterate over a node set when a `variable` or `parameter` element in a style sheet evaluates to a node set.</span></span>  
  
## <a name="style-sheet"></a><span data-ttu-id="b72e4-113">Arkusz stylów</span><span class="sxs-lookup"><span data-stu-id="b72e4-113">Style Sheet</span></span>  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">  
  
    <xsl:variable name="x" select="bookstore/book/title"></xsl:variable>  
  
    <xsl:template match="/">  
        <xsl:for-each select="$x">  
            ******  
            <xsl:value-of select="."></xsl:value-of>  
            ******  
        </xsl:for-each>  
    </xsl:template>  
  
</xsl:stylesheet>  
```  
  
## <a name="input"></a><span data-ttu-id="b72e4-114">Dane wejściowe</span><span class="sxs-lookup"><span data-stu-id="b72e4-114">Input</span></span>  
  
```xml  
<bookstore>  
   <book style="autobiography">  
      <title>Seven Years in Trenton</title>  
   </book>  
  
   <book style="autobiography">  
      <title>Seven Years in Trenton2</title>  
   </book>  
  
   <book style="textbook">  
      <title>History of Trenton Vol 3</title>  
   </book>  
</bookstore>  
```  
  
## <a name="output"></a><span data-ttu-id="b72e4-115">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="b72e4-115">Output</span></span>  
  
```  
******  
Seven Years in Trenton  
******  
  
******  
Seven Years in Trenton2  
******  
  
******  
History of Trenton Vol 3  
******  
```  
  
## <a name="see-also"></a><span data-ttu-id="b72e4-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b72e4-116">See also</span></span>

- <xref:System.Xml.XPath.XPathNodeIterator>
- [<span data-ttu-id="b72e4-117">Przekształcenia XSLT przy użyciu klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="b72e4-117">XSLT Transformations with the XslTransform Class</span></span>](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)
- [<span data-ttu-id="b72e4-118">Implementowanie procesora XSLT przy użyciu klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="b72e4-118">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
