---
title: "Porady: osadzanie wyrażeń w literałach XML (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- embedded expressions [Visual Basic]
- XML literals [Visual Basic], embedded expressions
ms.assetid: 75016fad-0141-42de-8564-5051be29487e
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bef4662d69ca7ceddeb2641cbe265d93712c5d16
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-embed-expressions-in-xml-literals-visual-basic"></a><span data-ttu-id="f2c96-102">Porady: osadzanie wyrażeń w literałach XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2c96-102">How to: Embed Expressions in XML Literals (Visual Basic)</span></span>
<span data-ttu-id="f2c96-103">Literały XML można łączyć z wyrażenia osadzone, aby utworzyć dokumentu XML, fragment lub element zawartości utworzona w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="f2c96-103">You can combine XML literals with embedded expressions to create an XML document, fragment, or element that contains content created at run time.</span></span> <span data-ttu-id="f2c96-104">W poniższych przykładach pokazano, jak używać wyrażenia osadzone do wypełniania elementu zawartości, atrybuty i nazwy elementów w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="f2c96-104">The following examples demonstrate how to use embedded expressions to populate element content, attributes, and element names at run time.</span></span>  
  
 <span data-ttu-id="f2c96-105">Składnia wyrażenia osadzonego jest `<%=` `exp` `%>`, która jest taka sama składnia który [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] używa.</span><span class="sxs-lookup"><span data-stu-id="f2c96-105">The syntax for an embedded expression is `<%=` `exp` `%>`, which is the same syntax that [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] uses.</span></span> <span data-ttu-id="f2c96-106">Aby uzyskać więcej informacji, zobacz [wyrażenia osadzone w XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="f2c96-106">For more information, see [Embedded Expressions in XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>  
  
 <span data-ttu-id="f2c96-107">Można również użyć [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] interfejsów API, aby utworzyć [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obiektów.</span><span class="sxs-lookup"><span data-stu-id="f2c96-107">You can also use the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] APIs to create [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects.</span></span> <span data-ttu-id="f2c96-108">Aby uzyskać więcej informacji, zobacz <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="f2c96-108">For more information, see <xref:System.Xml.Linq.XElement>.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="f2c96-109">Procedury</span><span class="sxs-lookup"><span data-stu-id="f2c96-109">Procedures</span></span>  
  
#### <a name="to-insert-text-as-element-content"></a><span data-ttu-id="f2c96-110">Aby wstawić tekst jako element zawartości</span><span class="sxs-lookup"><span data-stu-id="f2c96-110">To insert text as element content</span></span>  
  
-   <span data-ttu-id="f2c96-111">Poniższy przykład przedstawia sposób wstawić tekst, który jest zawarty w `contactName` zmiennej między elementami nazwa otwierający i zamykający.</span><span class="sxs-lookup"><span data-stu-id="f2c96-111">The following example shows how to insert the text that is contained in the `contactName` variable between the opening and closing name elements.</span></span>  
  
     [!code-vb[VbXMLSamples#39](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_1.vb)]  
  
     <span data-ttu-id="f2c96-112">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="f2c96-112">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-as-an-attribute-value"></a><span data-ttu-id="f2c96-113">Aby wstawić tekst jako wartość atrybutu</span><span class="sxs-lookup"><span data-stu-id="f2c96-113">To insert text as an attribute value</span></span>  
  
-   <span data-ttu-id="f2c96-114">Poniższy przykład przedstawia sposób wstawić tekst, który znajduje się w `phoneType` zmiennej jako wartości `type` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="f2c96-114">The following example shows how to insert the text that is contained in the `phoneType` variable as the value of the `type` attribute.</span></span>  
  
     [!code-vb[VbXMLSamples#40](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_2.vb)]  
  
     <span data-ttu-id="f2c96-115">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="f2c96-115">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <phone type="home">206-555-0144</phone>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-for-an-element-name"></a><span data-ttu-id="f2c96-116">Aby wstawić tekst dla nazwy elementu</span><span class="sxs-lookup"><span data-stu-id="f2c96-116">To insert text for an element name</span></span>  
  
-   <span data-ttu-id="f2c96-117">Poniższy przykład przedstawia sposób wstawić tekst, który jest zawarty w `elementName` zmiennej jako nazwa elementu.</span><span class="sxs-lookup"><span data-stu-id="f2c96-117">The following example shows how to insert the text that is contained in the `elementName` variable as the name of an element.</span></span>  
  
     <span data-ttu-id="f2c96-118">Podczas tworzenia elementów za pomocą tej metody, należy zamknąć je za pomocą \</ > tagu.</span><span class="sxs-lookup"><span data-stu-id="f2c96-118">When creating elements by using this technique, you must close them with the \</> tag.</span></span>  
  
     [!code-vb[VbXMLSamples#41](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_3.vb)]  
  
     <span data-ttu-id="f2c96-119">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="f2c96-119">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="f2c96-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f2c96-120">See Also</span></span>  
 [<span data-ttu-id="f2c96-121">Porady: tworzenie literałów XML</span><span class="sxs-lookup"><span data-stu-id="f2c96-121">How to: Create XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md)  
 [<span data-ttu-id="f2c96-122">Wyrażenia osadzone w XML</span><span class="sxs-lookup"><span data-stu-id="f2c96-122">Embedded Expressions in XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)  
 [<span data-ttu-id="f2c96-123">Tworzenie XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f2c96-123">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="f2c96-124">XML</span><span class="sxs-lookup"><span data-stu-id="f2c96-124">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
