---
title: Rozszerzanie arkuszy stylów XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: df4ba2bf-a99e-4d22-bbf3-04fc67669dbc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ff952df59dc8291b12df2b238052d4c40c834e2a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="extending-xslt-style-sheets"></a><span data-ttu-id="a92c3-102">Rozszerzanie arkuszy stylów XSLT</span><span class="sxs-lookup"><span data-stu-id="a92c3-102">Extending XSLT Style Sheets</span></span>
<span data-ttu-id="a92c3-103">W tej sekcji opisano różne metody rozszerzania funkcji XSLT.</span><span class="sxs-lookup"><span data-stu-id="a92c3-103">This section describes the different methods of extending the XSLT functionality.</span></span> <span data-ttu-id="a92c3-104">Możesz dodać rozszerzenie obiektów lub parametry, używając <xref:System.Xml.Xsl.XsltArgumentList> klasy.</span><span class="sxs-lookup"><span data-stu-id="a92c3-104">You can add extension objects or parameters using the <xref:System.Xml.Xsl.XsltArgumentList> class.</span></span> <span data-ttu-id="a92c3-105">Następnie można wywołać rozszerzenie obiektów lub parametrów z arkusza stylów.</span><span class="sxs-lookup"><span data-stu-id="a92c3-105">The extension objects or parameters can then be called from the style sheet.</span></span> <span data-ttu-id="a92c3-106">Ponadto można również osadzać blokach skryptu do arkusza stylów przy użyciu `msxsl:script` elementu.</span><span class="sxs-lookup"><span data-stu-id="a92c3-106">In addition, you can also embed script blocks into the style sheet by using the `msxsl:script` element.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a92c3-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="a92c3-107">In This Section</span></span>  
 [<span data-ttu-id="a92c3-108">Obiekty rozszerzeń XSLT</span><span class="sxs-lookup"><span data-stu-id="a92c3-108">XSLT Extension Objects</span></span>](../../../../docs/standard/data/xml/xslt-extension-objects.md)  
 <span data-ttu-id="a92c3-109">Omówienie korzystania z <xref:System.Xml.Xsl.XsltArgumentList> klasy obiektów rozszerzenia XSLT procesów.</span><span class="sxs-lookup"><span data-stu-id="a92c3-109">Discusses using the <xref:System.Xml.Xsl.XsltArgumentList> class to process XSLT extension objects.</span></span>  
  
 [<span data-ttu-id="a92c3-110">Parametry XSLT</span><span class="sxs-lookup"><span data-stu-id="a92c3-110">XSLT Parameters</span></span>](../../../../docs/standard/data/xml/xslt-parameters.md)  
 <span data-ttu-id="a92c3-111">Omówienie korzystania z <xref:System.Xml.Xsl.XsltArgumentList> klasy parametrów XSLT procesu.</span><span class="sxs-lookup"><span data-stu-id="a92c3-111">Discusses using the <xref:System.Xml.Xsl.XsltArgumentList> class to process XSLT parameters.</span></span>  
  
 [<span data-ttu-id="a92c3-112">Bloki skryptów i element msxsl:script</span><span class="sxs-lookup"><span data-stu-id="a92c3-112">Script Blocks Using msxsl:script</span></span>](../../../../docs/standard/data/xml/script-blocks-using-msxsl-script.md)  
 <span data-ttu-id="a92c3-113">Omówienie korzystania z `msxsl:script` elementu.</span><span class="sxs-lookup"><span data-stu-id="a92c3-113">Discusses using the `msxsl:script` element.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a92c3-114">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="a92c3-114">Related Sections</span></span>  
 [<span data-ttu-id="a92c3-115">Przekształcenia XSLT</span><span class="sxs-lookup"><span data-stu-id="a92c3-115">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)
