---
title: Zestawy węzłów w przekształceniach
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: ad034f0e-ff8b-4a71-9a4c-528c754263c4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fbcd9b93f63d48229c174b0f6518fd0150e98e18
ms.sourcegitcommit: 7bfe1682d9368cf88d43e895d1e80ba2d88c3a99
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71957032"
---
# <a name="node-sets-in-transformations"></a><span data-ttu-id="01e3e-102">Zestawy węzłów w przekształceniach</span><span class="sxs-lookup"><span data-stu-id="01e3e-102">Node Sets in Transformations</span></span>
<span data-ttu-id="01e3e-103">Zestawy węzłów to jeden z czterech podstawowych typów danych, które są zwracane z wyrażeń XPath (XML Path Language).</span><span class="sxs-lookup"><span data-stu-id="01e3e-103">Node sets are one of four basic data types that are returned from XML Path Language (XPath) expressions.</span></span> <span data-ttu-id="01e3e-104">Zestaw węzłów, który jest nieuporządkowaną kolekcją węzłów bez duplikatów, utworzonych w kolejności dokumentu, można przypisać do zmiennej w arkuszu stylów.</span><span class="sxs-lookup"><span data-stu-id="01e3e-104">A node set, which is an unordered collection of nodes without duplicates, created in document order, can be assigned to a variable in a style sheet.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="01e3e-105">Klasa <xref:System.Xml.Xsl.XslTransform> jest przestarzała w .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="01e3e-105">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="01e3e-106">Można wykonywać przekształcenia Extensible Stylesheet Language for Transformations (XSLT) przy użyciu klasy <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="01e3e-106">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="01e3e-107">Aby uzyskać więcej informacji, zobacz [Używanie klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) i [Migrowanie z klasy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) .</span><span class="sxs-lookup"><span data-stu-id="01e3e-107">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="01e3e-108">Zestawy węzłów są jednym z czterech podstawowych typów danych, które są zwracane z wyrażeń XPath.</span><span class="sxs-lookup"><span data-stu-id="01e3e-108">Node sets are one of four basic data types that are returned from XPath expressions.</span></span> <span data-ttu-id="01e3e-109">Zestaw węzłów, który jest nieuporządkowaną kolekcją węzłów bez duplikatów, utworzonych w kolejności dokumentu, można przypisać do zmiennej w arkuszu stylów.</span><span class="sxs-lookup"><span data-stu-id="01e3e-109">A node set, which is an unordered collection of nodes without duplicates, created in document order, can be assigned to a variable in a style sheet.</span></span> <span data-ttu-id="01e3e-110">Ten zestaw węzłów, który jest wynikiem wyrażenia XPath użytego w atrybucie `select` w przekształceniu, ma takie samo zachowanie jak zestaw węzłów na podstawie Document Object Model XML (DOM).</span><span class="sxs-lookup"><span data-stu-id="01e3e-110">This node set, which is a result of an XPath expression used in a `select` attribute in a transformation, has the same behavior as a node set from the XML Document Object Model (DOM).</span></span> <span data-ttu-id="01e3e-111">Można nawigować po zestawie węzłów za pomocą zestawu metod przedstawionych w obszarze [nawigacji zestawu węzłów za pomocą elementu XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md), w przeciwieństwie do fragmentu drzewa lub fragmentu drzewa wyników, który używa <xref:System.Xml.XPath.XPathNodeIterator> do nawigacji.</span><span class="sxs-lookup"><span data-stu-id="01e3e-111">You can navigate a node set using a set of methods shown in [Node Set Navigation Using XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md), unlike a result tree fragment or result tree fragment, which uses the <xref:System.Xml.XPath.XPathNodeIterator> for navigation.</span></span>  
  
 <span data-ttu-id="01e3e-112">Poniższy przykład kodu pokazuje, jak wykonać iterację zestawu węzłów, gdy element `variable` lub `parameter` w arkuszu stylów jest obliczany w zestawie węzłów.</span><span class="sxs-lookup"><span data-stu-id="01e3e-112">The following code sample shows how to iterate over a node set when a `variable` or `parameter` element in a style sheet evaluates to a node set.</span></span>  
  
## <a name="style-sheet"></a><span data-ttu-id="01e3e-113">Arkusz stylów</span><span class="sxs-lookup"><span data-stu-id="01e3e-113">Style Sheet</span></span>  
  
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
  
## <a name="input"></a><span data-ttu-id="01e3e-114">Dane wejściowe</span><span class="sxs-lookup"><span data-stu-id="01e3e-114">Input</span></span>  
  
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
  
## <a name="output"></a><span data-ttu-id="01e3e-115">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="01e3e-115">Output</span></span>  
  
```output  
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
  
## <a name="see-also"></a><span data-ttu-id="01e3e-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="01e3e-116">See also</span></span>

- <xref:System.Xml.XPath.XPathNodeIterator>
- [<span data-ttu-id="01e3e-117">Przekształcenia XSLT przy użyciu klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="01e3e-117">XSLT Transformations with the XslTransform Class</span></span>](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)
- [<span data-ttu-id="01e3e-118">Implementowanie procesora XSLT przy użyciu klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="01e3e-118">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
