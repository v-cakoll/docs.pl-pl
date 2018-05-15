---
title: Obsługa msxsl:node-set() — funkcja
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: d0cbf517-d9f6-4097-9851-4fa62903decd
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d3eb24d76ffb07b36b837056ffa5cde0cbd37f5f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="support-for-the-msxslnode-set-function"></a><span data-ttu-id="b0419-102">Obsługa msxsl:node-set() — funkcja</span><span class="sxs-lookup"><span data-stu-id="b0419-102">Support for the msxsl:node-set() Function</span></span>
<span data-ttu-id="b0419-103">`msxsl:node-set` Funkcja umożliwia konwertowanie wynikowego fragmentu drzewa na zestaw węzłów.</span><span class="sxs-lookup"><span data-stu-id="b0419-103">The `msxsl:node-set` function enables you to convert a result tree fragment into a node set.</span></span> <span data-ttu-id="b0419-104">Wynikowy węzeł ustawić zawsze zawiera jeden węzeł i węzła głównego drzewa.</span><span class="sxs-lookup"><span data-stu-id="b0419-104">The resulting node set always contains a single node and is the root node of the tree.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b0419-105"><xref:System.Xml.Xsl.XslTransform> Klasa jest przestarzała w [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b0419-105">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="b0419-106">Może wykonywać rozszerzalny język arkusza stylów dla transformacji przekształcenia XSLT () przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy.</span><span class="sxs-lookup"><span data-stu-id="b0419-106">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="b0419-107">Zobacz [za pomocą klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) i [migracji z klasy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="b0419-107">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="b0419-108">`msxsl:node-set` Funkcja umożliwia konwertowanie wynikowego fragmentu drzewa na zestaw węzłów.</span><span class="sxs-lookup"><span data-stu-id="b0419-108">The `msxsl:node-set` function enables you to convert a result tree fragment into a node set.</span></span> <span data-ttu-id="b0419-109">Wynikowy węzeł ustawić zawsze zawiera jeden węzeł i węzła głównego drzewa.</span><span class="sxs-lookup"><span data-stu-id="b0419-109">The resulting node set always contains a single node and is the root node of the tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0419-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="b0419-110">Example</span></span>  
 <span data-ttu-id="b0419-111">W poniższym przykładzie `$var` jest zmienna, która jest węzeł drzewa w arkuszu stylów.</span><span class="sxs-lookup"><span data-stu-id="b0419-111">In the following example, `$var` is a variable that is a node tree in the style sheet.</span></span> <span data-ttu-id="b0419-112">Dla każdej instrukcji połączone z `node-set` funkcja umożliwia użytkownikowi iteracja tego węzła drzewa jako zestawu węzłów.</span><span class="sxs-lookup"><span data-stu-id="b0419-112">The for-each statement combined with the `node-set` function allows the user to iterate over this node tree as a node set.</span></span>  
  
## <a name="nodesetxsl"></a><span data-ttu-id="b0419-113">NodeSet.xsl</span><span class="sxs-lookup"><span data-stu-id="b0419-113">nodeset.xsl</span></span>  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
                xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
                xmlns:user="http://www.contoso.com"  
                version="1.0">  
    <xsl:variable name="books">  
        <book author="Michael Howard">Writing Secure Code</book>  
        <book author="Michael Kay">XSLT Reference</book>  
    </xsl:variable>  
  
    <xsl:template match="/">  
        <authors>  
            <xsl:for-each select="msxsl:node-set($books)/book">   
                <author><xsl:value-of select="@author"/)</author>  
            </xsl:for-each>  
        </authors>  
    </xsl:template>  
</xsl:stylesheet>  
```  
  
## <a name="output"></a><span data-ttu-id="b0419-114">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="b0419-114">Output</span></span>  
 <span data-ttu-id="b0419-115">Dane wyjściowe transformacji</span><span class="sxs-lookup"><span data-stu-id="b0419-115">The output of the transformation is</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<authors><author>Michael Howard</author><author>Michael Kay</author></authors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b0419-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b0419-116">See Also</span></span>  
 [<span data-ttu-id="b0419-117">Implementowanie procesora XSLT przy użyciu klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="b0419-117">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
