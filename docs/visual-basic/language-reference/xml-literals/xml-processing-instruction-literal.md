---
title: Literał instrukcji przetwarzającej kod XML
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralProcessingInstruction
helpviewer_keywords:
- XML literals [Visual Basic], processing instruction
- XML processing instruction literal [Visual Basic]
- processing instruction literal [Visual Basic]
ms.assetid: cef4f7f8-0011-4f64-8602-795077ad4f15
ms.openlocfilehash: 3602a81feae9287a77d060bb46f10eefee4fc05d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347043"
---
# <a name="xml-processing-instruction-literal-visual-basic"></a><span data-ttu-id="2b863-102">Literał instrukcji przetwarzającej kod XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2b863-102">XML Processing Instruction Literal (Visual Basic)</span></span>
<span data-ttu-id="2b863-103">A literal representing an <xref:System.Xml.Linq.XProcessingInstruction> object.</span><span class="sxs-lookup"><span data-stu-id="2b863-103">A literal representing an <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b863-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2b863-104">Syntax</span></span>  
  
```xml  
<?piName [ = piData ] ?>  
```  
  
## <a name="parts"></a><span data-ttu-id="2b863-105">Części</span><span class="sxs-lookup"><span data-stu-id="2b863-105">Parts</span></span>  
 `<?`  
 <span data-ttu-id="2b863-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="2b863-106">Required.</span></span> <span data-ttu-id="2b863-107">Denotes the start of the XML processing instruction literal.</span><span class="sxs-lookup"><span data-stu-id="2b863-107">Denotes the start of the XML processing instruction literal.</span></span>  
  
 `piName`  
 <span data-ttu-id="2b863-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="2b863-108">Required.</span></span> <span data-ttu-id="2b863-109">Name indicating which application the processing instruction targets.</span><span class="sxs-lookup"><span data-stu-id="2b863-109">Name indicating which application the processing instruction targets.</span></span> <span data-ttu-id="2b863-110">Cannot begin with "xml" or "XML".</span><span class="sxs-lookup"><span data-stu-id="2b863-110">Cannot begin with "xml" or "XML".</span></span>  
  
 `piData`  
 <span data-ttu-id="2b863-111">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="2b863-111">Optional.</span></span> <span data-ttu-id="2b863-112">String indicating how the application targeted by `piName` should process the XML document.</span><span class="sxs-lookup"><span data-stu-id="2b863-112">String indicating how the application targeted by `piName` should process the XML document.</span></span>  
  
 `?>`  
 <span data-ttu-id="2b863-113">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="2b863-113">Required.</span></span> <span data-ttu-id="2b863-114">Denotes the end of the processing instruction.</span><span class="sxs-lookup"><span data-stu-id="2b863-114">Denotes the end of the processing instruction.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2b863-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2b863-115">Return Value</span></span>  
 <span data-ttu-id="2b863-116">An <xref:System.Xml.Linq.XProcessingInstruction> object.</span><span class="sxs-lookup"><span data-stu-id="2b863-116">An <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2b863-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2b863-117">Remarks</span></span>  
 <span data-ttu-id="2b863-118">XML processing instruction literals indicate how applications should process an XML document.</span><span class="sxs-lookup"><span data-stu-id="2b863-118">XML processing instruction literals indicate how applications should process an XML document.</span></span> <span data-ttu-id="2b863-119">When an application loads an XML document, the application can check the XML processing instructions to determine how to process the document.</span><span class="sxs-lookup"><span data-stu-id="2b863-119">When an application loads an XML document, the application can check the XML processing instructions to determine how to process the document.</span></span> <span data-ttu-id="2b863-120">The application interprets the meaning of `piName` and `piData`.</span><span class="sxs-lookup"><span data-stu-id="2b863-120">The application interprets the meaning of `piName` and `piData`.</span></span>  
  
 <span data-ttu-id="2b863-121">The XML document literal uses syntax that is similar to that of the XML processing instruction.</span><span class="sxs-lookup"><span data-stu-id="2b863-121">The XML document literal uses syntax that is similar to that of the XML processing instruction.</span></span> <span data-ttu-id="2b863-122">For more information, see [XML Document Literal](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).</span><span class="sxs-lookup"><span data-stu-id="2b863-122">For more information, see [XML Document Literal](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2b863-123">The `piName` element cannot begin with the strings "xml" or "XML", because the XML 1.0 specification reserves those identifiers.</span><span class="sxs-lookup"><span data-stu-id="2b863-123">The `piName` element cannot begin with the strings "xml" or "XML", because the XML 1.0 specification reserves those identifiers.</span></span>  
  
 <span data-ttu-id="2b863-124">You can assign an XML processing instruction literal to a variable or include it in an XML document literal.</span><span class="sxs-lookup"><span data-stu-id="2b863-124">You can assign an XML processing instruction literal to a variable or include it in an XML document literal.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2b863-125">An XML literal can span multiple lines without needing line continuation characters.</span><span class="sxs-lookup"><span data-stu-id="2b863-125">An XML literal can span multiple lines without needing line continuation characters.</span></span> <span data-ttu-id="2b863-126">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span><span class="sxs-lookup"><span data-stu-id="2b863-126">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="2b863-127">The Visual Basic compiler converts the XML processing instruction literal to a call to the <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> constructor.</span><span class="sxs-lookup"><span data-stu-id="2b863-127">The Visual Basic compiler converts the XML processing instruction literal to a call to the <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b863-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="2b863-128">Example</span></span>  
 <span data-ttu-id="2b863-129">The following example creates a processing instruction identifying a style-sheet for an XML document.</span><span class="sxs-lookup"><span data-stu-id="2b863-129">The following example creates a processing instruction identifying a style-sheet for an XML document.</span></span>  
  
 [!code-vb[VbXMLSamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="2b863-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2b863-130">See also</span></span>

- <xref:System.Xml.Linq.XProcessingInstruction>
- [<span data-ttu-id="2b863-131">Literał dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="2b863-131">XML Document Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [<span data-ttu-id="2b863-132">Literały XML</span><span class="sxs-lookup"><span data-stu-id="2b863-132">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="2b863-133">Creating XML in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2b863-133">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
