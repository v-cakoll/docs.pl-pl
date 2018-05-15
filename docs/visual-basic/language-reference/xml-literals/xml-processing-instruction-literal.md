---
title: Literał instrukcji przetwarzającej kod XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralProcessingInstruction
helpviewer_keywords:
- XML literals [Visual Basic], processing instruction
- XML processing instruction literal [Visual Basic]
- processing instruction literal [Visual Basic]
ms.assetid: cef4f7f8-0011-4f64-8602-795077ad4f15
ms.openlocfilehash: e6d4c200822f58c7dbe5bf423282740d4aa86ac3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="xml-processing-instruction-literal-visual-basic"></a><span data-ttu-id="cd606-102">Literał instrukcji przetwarzającej kod XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd606-102">XML Processing Instruction Literal (Visual Basic)</span></span>
<span data-ttu-id="cd606-103">Literał reprezentujący <xref:System.Xml.Linq.XProcessingInstruction> obiektu.</span><span class="sxs-lookup"><span data-stu-id="cd606-103">A literal representing an <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd606-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cd606-104">Syntax</span></span>  
  
```xml  
<?piName [ = piData ] ?>  
```  
  
## <a name="parts"></a><span data-ttu-id="cd606-105">Części</span><span class="sxs-lookup"><span data-stu-id="cd606-105">Parts</span></span>  
 `<?`  
 <span data-ttu-id="cd606-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="cd606-106">Required.</span></span> <span data-ttu-id="cd606-107">Oznacza początek literał instrukcji przetwarzania XML.</span><span class="sxs-lookup"><span data-stu-id="cd606-107">Denotes the start of the XML processing instruction literal.</span></span>  
  
 `piName`  
 <span data-ttu-id="cd606-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="cd606-108">Required.</span></span> <span data-ttu-id="cd606-109">Nazwa wskazująca, która aplikacja docelowych instrukcji przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="cd606-109">Name indicating which application the processing instruction targets.</span></span> <span data-ttu-id="cd606-110">Nie może rozpoczynać się od "xml" lub "XML".</span><span class="sxs-lookup"><span data-stu-id="cd606-110">Cannot begin with "xml" or "XML".</span></span>  
  
 `piData`  
 <span data-ttu-id="cd606-111">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="cd606-111">Optional.</span></span> <span data-ttu-id="cd606-112">Ciąg wskazujący, jak aplikacja objęci `piName` powinna przetworzyć dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="cd606-112">String indicating how the application targeted by `piName` should process the XML document.</span></span>  
  
 `?>`  
 <span data-ttu-id="cd606-113">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="cd606-113">Required.</span></span> <span data-ttu-id="cd606-114">Oznacza koniec instrukcji przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="cd606-114">Denotes the end of the processing instruction.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cd606-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="cd606-115">Return Value</span></span>  
 <span data-ttu-id="cd606-116"><xref:System.Xml.Linq.XProcessingInstruction> Obiektu.</span><span class="sxs-lookup"><span data-stu-id="cd606-116">An <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd606-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cd606-117">Remarks</span></span>  
 <span data-ttu-id="cd606-118">Literały instrukcji przetwarzania XML wskazują, jak aplikacje powinna przetworzyć dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="cd606-118">XML processing instruction literals indicate how applications should process an XML document.</span></span> <span data-ttu-id="cd606-119">Podczas ładowania dokumentu XML aplikacji aplikacji można sprawdzić instrukcji przetwarzania XML do określenia sposobu przetwarzania dokumentu.</span><span class="sxs-lookup"><span data-stu-id="cd606-119">When an application loads an XML document, the application can check the XML processing instructions to determine how to process the document.</span></span> <span data-ttu-id="cd606-120">Aplikacja interpretuje znaczenie `piName` i `piData`.</span><span class="sxs-lookup"><span data-stu-id="cd606-120">The application interprets the meaning of `piName` and `piData`.</span></span>  
  
 <span data-ttu-id="cd606-121">Literał dokumentu XML używa składni, która jest podobna do instrukcji przetwarzania XML.</span><span class="sxs-lookup"><span data-stu-id="cd606-121">The XML document literal uses syntax that is similar to that of the XML processing instruction.</span></span> <span data-ttu-id="cd606-122">Aby uzyskać więcej informacji, zobacz [literał dokumentu XML](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).</span><span class="sxs-lookup"><span data-stu-id="cd606-122">For more information, see [XML Document Literal](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cd606-123">`piName` Elementu nie może rozpoczynać się od ciągów "xml" lub "XML" ponieważ Specyfikacja XML 1.0 rezerwuje tych identyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="cd606-123">The `piName` element cannot begin with the strings "xml" or "XML", because the XML 1.0 specification reserves those identifiers.</span></span>  
  
 <span data-ttu-id="cd606-124">Można przypisać literał instrukcji przetwarzania XML do zmiennej lub objąć literał dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="cd606-124">You can assign an XML processing instruction literal to a variable or include it in an XML document literal.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cd606-125">Literał XML może obejmować wiele wierszy bez konieczności znaki kontynuacji wiersza.</span><span class="sxs-lookup"><span data-stu-id="cd606-125">An XML literal can span multiple lines without needing line continuation characters.</span></span> <span data-ttu-id="cd606-126">Pozwala na kopiowanie zawartości z dokumentu XML i wklej go bezpośrednio w programie Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="cd606-126">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="cd606-127">Kompilator Visual Basic konwertuje literał instrukcji przetwarzania XML do wywołania <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> konstruktora.</span><span class="sxs-lookup"><span data-stu-id="cd606-127">The Visual Basic compiler converts the XML processing instruction literal to a call to the <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd606-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="cd606-128">Example</span></span>  
 <span data-ttu-id="cd606-129">Poniższy przykład tworzy instrukcji przetwarzania identyfikujący arkusz stylów dla dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="cd606-129">The following example creates a processing instruction identifying a style-sheet for an XML document.</span></span>  
  
 [!code-vb[VbXMLSamples#28](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-processing-instruction-literal_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="cd606-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cd606-130">See Also</span></span>  
 <xref:System.Xml.Linq.XProcessingInstruction>  
 [<span data-ttu-id="cd606-131">Literał dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="cd606-131">XML Document Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)  
 [<span data-ttu-id="cd606-132">Literały XML</span><span class="sxs-lookup"><span data-stu-id="cd606-132">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="cd606-133">Tworzenie XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cd606-133">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
