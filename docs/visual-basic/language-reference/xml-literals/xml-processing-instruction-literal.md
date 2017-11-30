---
title: "Literał instrukcji przetwarzającej kod XML (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.XmlLiteralProcessingInstruction
helpviewer_keywords:
- XML literals [Visual Basic], processing instruction
- XML processing instruction literal [Visual Basic]
- processing instruction literal [Visual Basic]
ms.assetid: cef4f7f8-0011-4f64-8602-795077ad4f15
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9ce0f2d0dff80072beefdb4f84643ea28e2cf165
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="xml-processing-instruction-literal-visual-basic"></a><span data-ttu-id="9d0ff-102">Literał instrukcji przetwarzającej kod XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9d0ff-102">XML Processing Instruction Literal (Visual Basic)</span></span>
<span data-ttu-id="9d0ff-103">Literał reprezentujący <xref:System.Xml.Linq.XProcessingInstruction> obiektu.</span><span class="sxs-lookup"><span data-stu-id="9d0ff-103">A literal representing an <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d0ff-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9d0ff-104">Syntax</span></span>  
  
```xml  
<?piName [ = piData ] ?>  
```  
  
## <a name="parts"></a><span data-ttu-id="9d0ff-105">Części</span><span class="sxs-lookup"><span data-stu-id="9d0ff-105">Parts</span></span>  
 `<?`  
 <span data-ttu-id="9d0ff-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="9d0ff-106">Required.</span></span> <span data-ttu-id="9d0ff-107">Oznacza początek literał instrukcji przetwarzania XML.</span><span class="sxs-lookup"><span data-stu-id="9d0ff-107">Denotes the start of the XML processing instruction literal.</span></span>  
  
 `piName`  
 <span data-ttu-id="9d0ff-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="9d0ff-108">Required.</span></span> <span data-ttu-id="9d0ff-109">Nazwa wskazująca, która aplikacja docelowych instrukcji przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="9d0ff-109">Name indicating which application the processing instruction targets.</span></span> <span data-ttu-id="9d0ff-110">Nie może rozpoczynać się od "xml" lub "XML".</span><span class="sxs-lookup"><span data-stu-id="9d0ff-110">Cannot begin with "xml" or "XML".</span></span>  
  
 `piData`  
 <span data-ttu-id="9d0ff-111">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="9d0ff-111">Optional.</span></span> <span data-ttu-id="9d0ff-112">Ciąg wskazujący, jak aplikacja objęci `piName` powinna przetworzyć dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="9d0ff-112">String indicating how the application targeted by `piName` should process the XML document.</span></span>  
  
 `?>`  
 <span data-ttu-id="9d0ff-113">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="9d0ff-113">Required.</span></span> <span data-ttu-id="9d0ff-114">Oznacza koniec instrukcji przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="9d0ff-114">Denotes the end of the processing instruction.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9d0ff-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9d0ff-115">Return Value</span></span>  
 <span data-ttu-id="9d0ff-116"><xref:System.Xml.Linq.XProcessingInstruction> Obiektu.</span><span class="sxs-lookup"><span data-stu-id="9d0ff-116">An <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d0ff-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9d0ff-117">Remarks</span></span>  
 <span data-ttu-id="9d0ff-118">Literały instrukcji przetwarzania XML wskazują, jak aplikacje powinna przetworzyć dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="9d0ff-118">XML processing instruction literals indicate how applications should process an XML document.</span></span> <span data-ttu-id="9d0ff-119">Podczas ładowania dokumentu XML aplikacji aplikacji można sprawdzić instrukcji przetwarzania XML do określenia sposobu przetwarzania dokumentu.</span><span class="sxs-lookup"><span data-stu-id="9d0ff-119">When an application loads an XML document, the application can check the XML processing instructions to determine how to process the document.</span></span> <span data-ttu-id="9d0ff-120">Aplikacja interpretuje znaczenie `piName` i `piData`.</span><span class="sxs-lookup"><span data-stu-id="9d0ff-120">The application interprets the meaning of `piName` and `piData`.</span></span>  
  
 <span data-ttu-id="9d0ff-121">Literał dokumentu XML używa składni, która jest podobna do instrukcji przetwarzania XML.</span><span class="sxs-lookup"><span data-stu-id="9d0ff-121">The XML document literal uses syntax that is similar to that of the XML processing instruction.</span></span> <span data-ttu-id="9d0ff-122">Aby uzyskać więcej informacji, zobacz [literał dokumentu XML](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).</span><span class="sxs-lookup"><span data-stu-id="9d0ff-122">For more information, see [XML Document Literal](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9d0ff-123">`piName` Elementu nie może rozpoczynać się od ciągów "xml" lub "XML" ponieważ Specyfikacja XML 1.0 rezerwuje tych identyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="9d0ff-123">The `piName` element cannot begin with the strings "xml" or "XML", because the XML 1.0 specification reserves those identifiers.</span></span>  
  
 <span data-ttu-id="9d0ff-124">Można przypisać literał instrukcji przetwarzania XML do zmiennej lub objąć literał dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="9d0ff-124">You can assign an XML processing instruction literal to a variable or include it in an XML document literal.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9d0ff-125">Literał XML może obejmować wiele wierszy bez konieczności znaki kontynuacji wiersza.</span><span class="sxs-lookup"><span data-stu-id="9d0ff-125">An XML literal can span multiple lines without needing line continuation characters.</span></span> <span data-ttu-id="9d0ff-126">Dzięki temu można kopiować zawartości z dokumentu XML i wklej go bezpośrednio do [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program.</span><span class="sxs-lookup"><span data-stu-id="9d0ff-126">This enables you to copy content from an XML document and paste it directly into a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program.</span></span>  
  
 <span data-ttu-id="9d0ff-127">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Kompilatora konwertuje literał instrukcji przetwarzania XML do wywołania <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> konstruktora.</span><span class="sxs-lookup"><span data-stu-id="9d0ff-127">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler converts the XML processing instruction literal to a call to the <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d0ff-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="9d0ff-128">Example</span></span>  
 <span data-ttu-id="9d0ff-129">Poniższy przykład tworzy instrukcji przetwarzania identyfikujący arkusz stylów dla dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="9d0ff-129">The following example creates a processing instruction identifying a style-sheet for an XML document.</span></span>  
  
 [!code-vb[VbXMLSamples#28](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-processing-instruction-literal_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="9d0ff-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9d0ff-130">See Also</span></span>  
 <xref:System.Xml.Linq.XProcessingInstruction>  
 [<span data-ttu-id="9d0ff-131">Literał dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="9d0ff-131">XML Document Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)  
 [<span data-ttu-id="9d0ff-132">Literały XML</span><span class="sxs-lookup"><span data-stu-id="9d0ff-132">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="9d0ff-133">Tworzenie XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9d0ff-133">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
