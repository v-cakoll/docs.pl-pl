---
title: Literał instrukcji przetwarzającej kod XML (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlLiteralProcessingInstruction
helpviewer_keywords:
- XML literals [Visual Basic], processing instruction
- XML processing instruction literal [Visual Basic]
- processing instruction literal [Visual Basic]
ms.assetid: cef4f7f8-0011-4f64-8602-795077ad4f15
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2d2df93a46d426358988b3ad7f3161c7ae0c7b9e
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="xml-processing-instruction-literal-visual-basic"></a><span data-ttu-id="5213d-102">Literał instrukcji przetwarzającej kod XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5213d-102">XML Processing Instruction Literal (Visual Basic)</span></span>
<span data-ttu-id="5213d-103">Literał reprezentujący <xref:System.Xml.Linq.XProcessingInstruction> obiektu.</span><span class="sxs-lookup"><span data-stu-id="5213d-103">A literal representing an <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5213d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5213d-104">Syntax</span></span>  
  
```xml  
<?piName [ = piData ] ?>  
```  
  
## <a name="parts"></a><span data-ttu-id="5213d-105">Części</span><span class="sxs-lookup"><span data-stu-id="5213d-105">Parts</span></span>  
 `<?`  
 <span data-ttu-id="5213d-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="5213d-106">Required.</span></span> <span data-ttu-id="5213d-107">Oznacza początek literał instrukcji przetwarzania XML.</span><span class="sxs-lookup"><span data-stu-id="5213d-107">Denotes the start of the XML processing instruction literal.</span></span>  
  
 `piName`  
 <span data-ttu-id="5213d-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="5213d-108">Required.</span></span> <span data-ttu-id="5213d-109">Nazwa wskazująca, która aplikacja docelowych instrukcji przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="5213d-109">Name indicating which application the processing instruction targets.</span></span> <span data-ttu-id="5213d-110">Nie może rozpoczynać się od "xml" lub "XML".</span><span class="sxs-lookup"><span data-stu-id="5213d-110">Cannot begin with "xml" or "XML".</span></span>  
  
 `piData`  
 <span data-ttu-id="5213d-111">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="5213d-111">Optional.</span></span> <span data-ttu-id="5213d-112">Ciąg wskazujący, jak aplikacja objęci `piName` powinna przetworzyć dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="5213d-112">String indicating how the application targeted by `piName` should process the XML document.</span></span>  
  
 `?>`  
 <span data-ttu-id="5213d-113">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="5213d-113">Required.</span></span> <span data-ttu-id="5213d-114">Oznacza koniec instrukcji przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="5213d-114">Denotes the end of the processing instruction.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5213d-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5213d-115">Return Value</span></span>  
 <span data-ttu-id="5213d-116"><xref:System.Xml.Linq.XProcessingInstruction> Obiektu.</span><span class="sxs-lookup"><span data-stu-id="5213d-116">An <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5213d-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5213d-117">Remarks</span></span>  
 <span data-ttu-id="5213d-118">Literały instrukcji przetwarzania XML wskazują, jak aplikacje powinna przetworzyć dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="5213d-118">XML processing instruction literals indicate how applications should process an XML document.</span></span> <span data-ttu-id="5213d-119">Podczas ładowania dokumentu XML aplikacji aplikacji można sprawdzić instrukcji przetwarzania XML do określenia sposobu przetwarzania dokumentu.</span><span class="sxs-lookup"><span data-stu-id="5213d-119">When an application loads an XML document, the application can check the XML processing instructions to determine how to process the document.</span></span> <span data-ttu-id="5213d-120">Aplikacja interpretuje znaczenie `piName` i `piData`.</span><span class="sxs-lookup"><span data-stu-id="5213d-120">The application interprets the meaning of `piName` and `piData`.</span></span>  
  
 <span data-ttu-id="5213d-121">Literał dokumentu XML używa składni, która jest podobna do instrukcji przetwarzania XML.</span><span class="sxs-lookup"><span data-stu-id="5213d-121">The XML document literal uses syntax that is similar to that of the XML processing instruction.</span></span> <span data-ttu-id="5213d-122">Aby uzyskać więcej informacji, zobacz [literał dokumentu XML](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).</span><span class="sxs-lookup"><span data-stu-id="5213d-122">For more information, see [XML Document Literal](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5213d-123">`piName` Elementu nie może rozpoczynać się od ciągów "xml" lub "XML" ponieważ Specyfikacja XML 1.0 rezerwuje tych identyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="5213d-123">The `piName` element cannot begin with the strings "xml" or "XML", because the XML 1.0 specification reserves those identifiers.</span></span>  
  
 <span data-ttu-id="5213d-124">Można przypisać literał instrukcji przetwarzania XML do zmiennej lub objąć literał dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="5213d-124">You can assign an XML processing instruction literal to a variable or include it in an XML document literal.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5213d-125">Literał XML może obejmować wiele wierszy bez konieczności znaki kontynuacji wiersza.</span><span class="sxs-lookup"><span data-stu-id="5213d-125">An XML literal can span multiple lines without needing line continuation characters.</span></span> <span data-ttu-id="5213d-126">Pozwala na kopiowanie zawartości z dokumentu XML i wklej go bezpośrednio w programie Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5213d-126">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="5213d-127">Kompilator Visual Basic konwertuje literał instrukcji przetwarzania XML do wywołania <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> konstruktora.</span><span class="sxs-lookup"><span data-stu-id="5213d-127">The Visual Basic compiler converts the XML processing instruction literal to a call to the <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5213d-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="5213d-128">Example</span></span>  
 <span data-ttu-id="5213d-129">Poniższy przykład tworzy instrukcji przetwarzania identyfikujący arkusz stylów dla dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="5213d-129">The following example creates a processing instruction identifying a style-sheet for an XML document.</span></span>  
  
 [!code-vb[VbXMLSamples#28](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-processing-instruction-literal_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="5213d-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5213d-130">See Also</span></span>  
 <xref:System.Xml.Linq.XProcessingInstruction>  
 [<span data-ttu-id="5213d-131">Literał dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="5213d-131">XML Document Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)  
 [<span data-ttu-id="5213d-132">Literały XML</span><span class="sxs-lookup"><span data-stu-id="5213d-132">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="5213d-133">Tworzenie XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5213d-133">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
