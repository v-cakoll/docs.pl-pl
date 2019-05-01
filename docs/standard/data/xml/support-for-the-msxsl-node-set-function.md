---
title: Obsługa funkcji msxsl:node-set()
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: d0cbf517-d9f6-4097-9851-4fa62903decd
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a37220816ab320340b2dd5c048cc4ff2ad9724a3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026916"
---
# <a name="support-for-the-msxslnode-set-function"></a><span data-ttu-id="92a72-102">Obsługa funkcji msxsl:node-set()</span><span class="sxs-lookup"><span data-stu-id="92a72-102">Support for the msxsl:node-set() Function</span></span>
<span data-ttu-id="92a72-103">`msxsl:node-set` Funkcja umożliwia konwertowanie wynikowego fragmentu drzewa w zestawie węzłów.</span><span class="sxs-lookup"><span data-stu-id="92a72-103">The `msxsl:node-set` function enables you to convert a result tree fragment into a node set.</span></span> <span data-ttu-id="92a72-104">Węzeł wynikowy ustawić opcji zawsze zawiera jeden węzeł i węzeł główny drzewa.</span><span class="sxs-lookup"><span data-stu-id="92a72-104">The resulting node set always contains a single node and is the root node of the tree.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="92a72-105"><xref:System.Xml.Xsl.XslTransform> Klasy jest przestarzała w [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="92a72-105">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="92a72-106">Można przeprowadzić rozszerzalny język arkusza stylów dla przekształceń przekształcenia (XSLT) przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy.</span><span class="sxs-lookup"><span data-stu-id="92a72-106">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="92a72-107">Zobacz [używanie klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) i [Migrowanie z klasy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="92a72-107">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="92a72-108">`msxsl:node-set` Funkcja umożliwia konwertowanie wynikowego fragmentu drzewa w zestawie węzłów.</span><span class="sxs-lookup"><span data-stu-id="92a72-108">The `msxsl:node-set` function enables you to convert a result tree fragment into a node set.</span></span> <span data-ttu-id="92a72-109">Węzeł wynikowy ustawić opcji zawsze zawiera jeden węzeł i węzeł główny drzewa.</span><span class="sxs-lookup"><span data-stu-id="92a72-109">The resulting node set always contains a single node and is the root node of the tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92a72-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="92a72-110">Example</span></span>  
 <span data-ttu-id="92a72-111">W poniższym przykładzie `$var` to zmienna, która jest węzeł drzewa w arkuszu stylów.</span><span class="sxs-lookup"><span data-stu-id="92a72-111">In the following example, `$var` is a variable that is a node tree in the style sheet.</span></span> <span data-ttu-id="92a72-112">Dla każdej instrukcji w połączeniu z `node-set` funkcja zezwala użytkownikowi na iterację w tym węźle drzewa jako zestaw węzłów.</span><span class="sxs-lookup"><span data-stu-id="92a72-112">The for-each statement combined with the `node-set` function allows the user to iterate over this node tree as a node set.</span></span>  
  
## <a name="nodesetxsl"></a><span data-ttu-id="92a72-113">nodeset.xsl</span><span class="sxs-lookup"><span data-stu-id="92a72-113">nodeset.xsl</span></span>  
  
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
                <author><xsl:value-of select="@author"/></author>  
            </xsl:for-each>  
        </authors>  
    </xsl:template>  
</xsl:stylesheet>  
```  
  
## <a name="output"></a><span data-ttu-id="92a72-114">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="92a72-114">Output</span></span>  
 <span data-ttu-id="92a72-115">Dane wyjściowe transformacji</span><span class="sxs-lookup"><span data-stu-id="92a72-115">The output of the transformation is</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<authors><author>Michael Howard</author><author>Michael Kay</author></authors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="92a72-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="92a72-116">See also</span></span>

- [<span data-ttu-id="92a72-117">Implementowanie procesora XSLT przy użyciu klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="92a72-117">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
