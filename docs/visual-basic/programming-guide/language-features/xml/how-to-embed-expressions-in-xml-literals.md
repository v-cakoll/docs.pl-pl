---
title: 'Porady: osadzanie wyrażeń w literałach XML'
ms.date: 07/20/2015
helpviewer_keywords:
- embedded expressions [Visual Basic]
- XML literals [Visual Basic], embedded expressions
ms.assetid: 75016fad-0141-42de-8564-5051be29487e
ms.openlocfilehash: 2e8dd10b334b0271e3c9de11ed155c9d5d7aae48
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74332940"
---
# <a name="how-to-embed-expressions-in-xml-literals-visual-basic"></a><span data-ttu-id="71884-102">Porady: osadzanie wyrażeń w literałach XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="71884-102">How to: Embed Expressions in XML Literals (Visual Basic)</span></span>
<span data-ttu-id="71884-103">Literały XML można łączyć z osadzonymi wyrażeniami w celu utworzenia dokumentu XML, fragmentu lub elementu zawierającego zawartość utworzoną w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="71884-103">You can combine XML literals with embedded expressions to create an XML document, fragment, or element that contains content created at run time.</span></span> <span data-ttu-id="71884-104">W poniższych przykładach pokazano, jak używać osadzonych wyrażeń do wypełniania zawartości elementu, atrybutów i nazw elementów w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="71884-104">The following examples demonstrate how to use embedded expressions to populate element content, attributes, and element names at run time.</span></span>  
  
 <span data-ttu-id="71884-105">Składnia wyrażenia osadzonego jest `<%=` `exp` `%>`, która jest tą samą składnią, która ASP.NET używa.</span><span class="sxs-lookup"><span data-stu-id="71884-105">The syntax for an embedded expression is `<%=` `exp` `%>`, which is the same syntax that ASP.NET uses.</span></span> <span data-ttu-id="71884-106">Aby uzyskać więcej informacji, zobacz [Embedded Expressions in XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="71884-106">For more information, see [Embedded Expressions in XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>  
  
 <span data-ttu-id="71884-107">Można również użyć [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] interfejsów API do tworzenia obiektów [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="71884-107">You can also use the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] APIs to create [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects.</span></span> <span data-ttu-id="71884-108">Aby uzyskać więcej informacji, zobacz <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="71884-108">For more information, see <xref:System.Xml.Linq.XElement>.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="71884-109">Procedury</span><span class="sxs-lookup"><span data-stu-id="71884-109">Procedures</span></span>  
  
#### <a name="to-insert-text-as-element-content"></a><span data-ttu-id="71884-110">Aby wstawić tekst jako zawartość elementu</span><span class="sxs-lookup"><span data-stu-id="71884-110">To insert text as element content</span></span>  
  
- <span data-ttu-id="71884-111">Poniższy przykład pokazuje, jak wstawić tekst, który jest zawarty w zmiennej `contactName` między otwierającymi i zamykającymi elementami nazw.</span><span class="sxs-lookup"><span data-stu-id="71884-111">The following example shows how to insert the text that is contained in the `contactName` variable between the opening and closing name elements.</span></span>  
  
     [!code-vb[VbXMLSamples#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#39)]  
  
     <span data-ttu-id="71884-112">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="71884-112">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-as-an-attribute-value"></a><span data-ttu-id="71884-113">Aby wstawić tekst jako wartość atrybutu</span><span class="sxs-lookup"><span data-stu-id="71884-113">To insert text as an attribute value</span></span>  
  
- <span data-ttu-id="71884-114">Poniższy przykład pokazuje, jak wstawić tekst, który jest zawarty w zmiennej `phoneType` jako wartość atrybutu `type`.</span><span class="sxs-lookup"><span data-stu-id="71884-114">The following example shows how to insert the text that is contained in the `phoneType` variable as the value of the `type` attribute.</span></span>  
  
     [!code-vb[VbXMLSamples#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#40)]  
  
     <span data-ttu-id="71884-115">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="71884-115">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <phone type="home">206-555-0144</phone>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-for-an-element-name"></a><span data-ttu-id="71884-116">Aby wstawić tekst dla nazwy elementu</span><span class="sxs-lookup"><span data-stu-id="71884-116">To insert text for an element name</span></span>  
  
- <span data-ttu-id="71884-117">Poniższy przykład pokazuje, jak wstawić tekst, który jest zawarty w zmiennej `elementName` jako nazwę elementu.</span><span class="sxs-lookup"><span data-stu-id="71884-117">The following example shows how to insert the text that is contained in the `elementName` variable as the name of an element.</span></span>  
  
     <span data-ttu-id="71884-118">Podczas tworzenia elementów za pomocą tej techniki należy zamknąć je za pomocą tagu \</>.</span><span class="sxs-lookup"><span data-stu-id="71884-118">When creating elements by using this technique, you must close them with the \</> tag.</span></span>  
  
     [!code-vb[VbXMLSamples#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#41)]  
  
     <span data-ttu-id="71884-119">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="71884-119">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="71884-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="71884-120">See also</span></span>

- [<span data-ttu-id="71884-121">Instrukcje: tworzenie literałów XML</span><span class="sxs-lookup"><span data-stu-id="71884-121">How to: Create XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md)
- [<span data-ttu-id="71884-122">Wyrażenia osadzone w XML</span><span class="sxs-lookup"><span data-stu-id="71884-122">Embedded Expressions in XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [<span data-ttu-id="71884-123">Tworzenie kodu XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="71884-123">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="71884-124">XML</span><span class="sxs-lookup"><span data-stu-id="71884-124">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
