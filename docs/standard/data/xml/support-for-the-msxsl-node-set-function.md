---
title: Obsługa funkcji msxsl:node-set()
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: d0cbf517-d9f6-4097-9851-4fa62903decd
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3670803ff20351fd9ff6892a0cef48b9caa70199
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939525"
---
# <a name="support-for-the-msxslnode-set-function"></a><span data-ttu-id="cbcdb-102">Obsługa funkcji msxsl:node-set()</span><span class="sxs-lookup"><span data-stu-id="cbcdb-102">Support for the msxsl:node-set() Function</span></span>
<span data-ttu-id="cbcdb-103">`msxsl:node-set` Funkcja umożliwia konwertowanie fragmentu drzewa wynikowego na zestaw węzłów.</span><span class="sxs-lookup"><span data-stu-id="cbcdb-103">The `msxsl:node-set` function enables you to convert a result tree fragment into a node set.</span></span> <span data-ttu-id="cbcdb-104">Zestaw węzłów powstających zawsze zawiera pojedynczy węzeł i jest węzłem głównym drzewa.</span><span class="sxs-lookup"><span data-stu-id="cbcdb-104">The resulting node set always contains a single node and is the root node of the tree.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cbcdb-105"><xref:System.Xml.Xsl.XslTransform> Klasa jest przestarzała w .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="cbcdb-105">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="cbcdb-106">Można wykonać przekształcenia Extensible Stylesheet Language for Transformations (XSLT) przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy.</span><span class="sxs-lookup"><span data-stu-id="cbcdb-106">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="cbcdb-107">Aby uzyskać więcej informacji, zobacz [Używanie klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) i [Migrowanie z klasy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) .</span><span class="sxs-lookup"><span data-stu-id="cbcdb-107">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="cbcdb-108">`msxsl:node-set` Funkcja umożliwia konwertowanie fragmentu drzewa wynikowego na zestaw węzłów.</span><span class="sxs-lookup"><span data-stu-id="cbcdb-108">The `msxsl:node-set` function enables you to convert a result tree fragment into a node set.</span></span> <span data-ttu-id="cbcdb-109">Zestaw węzłów powstających zawsze zawiera pojedynczy węzeł i jest węzłem głównym drzewa.</span><span class="sxs-lookup"><span data-stu-id="cbcdb-109">The resulting node set always contains a single node and is the root node of the tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cbcdb-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="cbcdb-110">Example</span></span>  
 <span data-ttu-id="cbcdb-111">W poniższym przykładzie `$var` jest to zmienna, która jest drzewem węzła w arkuszu stylów.</span><span class="sxs-lookup"><span data-stu-id="cbcdb-111">In the following example, `$var` is a variable that is a node tree in the style sheet.</span></span> <span data-ttu-id="cbcdb-112">Instrukcja for-each łączona z `node-set` funkcją pozwala użytkownikowi na iterację tego drzewa węzłów jako zestawu węzłów.</span><span class="sxs-lookup"><span data-stu-id="cbcdb-112">The for-each statement combined with the `node-set` function allows the user to iterate over this node tree as a node set.</span></span>  
  
## <a name="nodesetxsl"></a><span data-ttu-id="cbcdb-113">nodeset.xsl</span><span class="sxs-lookup"><span data-stu-id="cbcdb-113">nodeset.xsl</span></span>  
  
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
  
## <a name="output"></a><span data-ttu-id="cbcdb-114">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="cbcdb-114">Output</span></span>  
 <span data-ttu-id="cbcdb-115">Dane wyjściowe transformacji to</span><span class="sxs-lookup"><span data-stu-id="cbcdb-115">The output of the transformation is</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<authors><author>Michael Howard</author><author>Michael Kay</author></authors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cbcdb-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cbcdb-116">See also</span></span>

- [<span data-ttu-id="cbcdb-117">Implementowanie procesora XSLT przy użyciu klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="cbcdb-117">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
