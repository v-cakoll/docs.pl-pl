---
title: 'Instrukcje: Osadzanie wyrażeń w literałach XML (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- embedded expressions [Visual Basic]
- XML literals [Visual Basic], embedded expressions
ms.assetid: 75016fad-0141-42de-8564-5051be29487e
ms.openlocfilehash: ca80ac666e8676e4e58a9741b00125c0126570fa
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64598381"
---
# <a name="how-to-embed-expressions-in-xml-literals-visual-basic"></a><span data-ttu-id="065f8-102">Instrukcje: Osadzanie wyrażeń w literałach XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="065f8-102">How to: Embed Expressions in XML Literals (Visual Basic)</span></span>
<span data-ttu-id="065f8-103">Literały XML można połączyć z wyrażenia osadzone, aby utworzyć dokumentu XML, fragment lub element, który zawiera zawartość tworzony w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="065f8-103">You can combine XML literals with embedded expressions to create an XML document, fragment, or element that contains content created at run time.</span></span> <span data-ttu-id="065f8-104">W poniższych przykładach pokazano sposób użycia wyrażenia osadzone w celu wypełnienia zawartości elementu i atrybuty nazwy elementów w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="065f8-104">The following examples demonstrate how to use embedded expressions to populate element content, attributes, and element names at run time.</span></span>  
  
 <span data-ttu-id="065f8-105">Składnia wyrażenia osadzone jest `<%=` `exp` `%>`, który jest w tej samej składni, [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] używa.</span><span class="sxs-lookup"><span data-stu-id="065f8-105">The syntax for an embedded expression is `<%=` `exp` `%>`, which is the same syntax that [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] uses.</span></span> <span data-ttu-id="065f8-106">Aby uzyskać więcej informacji, zobacz [wyrażenia osadzone w XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="065f8-106">For more information, see [Embedded Expressions in XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>  
  
 <span data-ttu-id="065f8-107">Można również użyć [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] interfejsów API, aby utworzyć [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obiektów.</span><span class="sxs-lookup"><span data-stu-id="065f8-107">You can also use the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] APIs to create [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects.</span></span> <span data-ttu-id="065f8-108">Aby uzyskać więcej informacji, zobacz <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="065f8-108">For more information, see <xref:System.Xml.Linq.XElement>.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="065f8-109">Procedury</span><span class="sxs-lookup"><span data-stu-id="065f8-109">Procedures</span></span>  
  
#### <a name="to-insert-text-as-element-content"></a><span data-ttu-id="065f8-110">Aby wstawić tekst jako element zawartości</span><span class="sxs-lookup"><span data-stu-id="065f8-110">To insert text as element content</span></span>  
  
- <span data-ttu-id="065f8-111">Poniższy przykład pokazuje, jak wstawić tekst, który jest zawarty w `contactName` zmiennej między elementami nazwa otwierający i zamykający.</span><span class="sxs-lookup"><span data-stu-id="065f8-111">The following example shows how to insert the text that is contained in the `contactName` variable between the opening and closing name elements.</span></span>  
  
     [!code-vb[VbXMLSamples#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#39)]  
  
     <span data-ttu-id="065f8-112">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="065f8-112">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-as-an-attribute-value"></a><span data-ttu-id="065f8-113">Aby wstawić tekst jako wartość atrybutu</span><span class="sxs-lookup"><span data-stu-id="065f8-113">To insert text as an attribute value</span></span>  
  
- <span data-ttu-id="065f8-114">Poniższy przykład pokazuje, jak wstawić tekst, który jest zawarty w `phoneType` zmiennej jako wartości `type` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="065f8-114">The following example shows how to insert the text that is contained in the `phoneType` variable as the value of the `type` attribute.</span></span>  
  
     [!code-vb[VbXMLSamples#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#40)]  
  
     <span data-ttu-id="065f8-115">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="065f8-115">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <phone type="home">206-555-0144</phone>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-for-an-element-name"></a><span data-ttu-id="065f8-116">Aby wstawić tekst dla nazwy elementu</span><span class="sxs-lookup"><span data-stu-id="065f8-116">To insert text for an element name</span></span>  
  
- <span data-ttu-id="065f8-117">Poniższy przykład pokazuje, jak wstawić tekst, który jest zawarty w `elementName` zmiennej jako nazwę elementu.</span><span class="sxs-lookup"><span data-stu-id="065f8-117">The following example shows how to insert the text that is contained in the `elementName` variable as the name of an element.</span></span>  
  
     <span data-ttu-id="065f8-118">Podczas tworzenia elementów za pomocą tej techniki, należy zamknąć je za pomocą \</ > tag.</span><span class="sxs-lookup"><span data-stu-id="065f8-118">When creating elements by using this technique, you must close them with the \</> tag.</span></span>  
  
     [!code-vb[VbXMLSamples#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#41)]  
  
     <span data-ttu-id="065f8-119">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="065f8-119">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="065f8-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="065f8-120">See also</span></span>

- [<span data-ttu-id="065f8-121">Instrukcje: Tworzenie literałów XML</span><span class="sxs-lookup"><span data-stu-id="065f8-121">How to: Create XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md)
- [<span data-ttu-id="065f8-122">Wyrażenia osadzone w XML</span><span class="sxs-lookup"><span data-stu-id="065f8-122">Embedded Expressions in XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [<span data-ttu-id="065f8-123">Tworzenie XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="065f8-123">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="065f8-124">XML</span><span class="sxs-lookup"><span data-stu-id="065f8-124">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
