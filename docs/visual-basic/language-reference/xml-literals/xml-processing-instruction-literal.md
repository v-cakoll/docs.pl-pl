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
ms.openlocfilehash: 3fbb16a4d47801b671d37566573215d3a57afff1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58820155"
---
# <a name="xml-processing-instruction-literal-visual-basic"></a><span data-ttu-id="d2ed9-102">Literał instrukcji przetwarzającej kod XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d2ed9-102">XML Processing Instruction Literal (Visual Basic)</span></span>
<span data-ttu-id="d2ed9-103">Literał reprezentujący <xref:System.Xml.Linq.XProcessingInstruction> obiektu.</span><span class="sxs-lookup"><span data-stu-id="d2ed9-103">A literal representing an <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2ed9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d2ed9-104">Syntax</span></span>  
  
```xml  
<?piName [ = piData ] ?>  
```  
  
## <a name="parts"></a><span data-ttu-id="d2ed9-105">Części</span><span class="sxs-lookup"><span data-stu-id="d2ed9-105">Parts</span></span>  
 `<?`  
 <span data-ttu-id="d2ed9-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="d2ed9-106">Required.</span></span> <span data-ttu-id="d2ed9-107">Oznacza początek literał instrukcji przetwarzania XML.</span><span class="sxs-lookup"><span data-stu-id="d2ed9-107">Denotes the start of the XML processing instruction literal.</span></span>  
  
 `piName`  
 <span data-ttu-id="d2ed9-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="d2ed9-108">Required.</span></span> <span data-ttu-id="d2ed9-109">Nadaj nazwę wskazującą, która aplikacja przetwarzanie instrukcji celów.</span><span class="sxs-lookup"><span data-stu-id="d2ed9-109">Name indicating which application the processing instruction targets.</span></span> <span data-ttu-id="d2ed9-110">Nie może zaczynać od "xml" lub "XML".</span><span class="sxs-lookup"><span data-stu-id="d2ed9-110">Cannot begin with "xml" or "XML".</span></span>  
  
 `piData`  
 <span data-ttu-id="d2ed9-111">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="d2ed9-111">Optional.</span></span> <span data-ttu-id="d2ed9-112">Ciąg wskazujący, jak aplikacja objęte `piName` powinien przetworzyć dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="d2ed9-112">String indicating how the application targeted by `piName` should process the XML document.</span></span>  
  
 `?>`  
 <span data-ttu-id="d2ed9-113">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="d2ed9-113">Required.</span></span> <span data-ttu-id="d2ed9-114">Oznacza koniec instrukcji przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="d2ed9-114">Denotes the end of the processing instruction.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d2ed9-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d2ed9-115">Return Value</span></span>  
 <span data-ttu-id="d2ed9-116"><xref:System.Xml.Linq.XProcessingInstruction> Obiektu.</span><span class="sxs-lookup"><span data-stu-id="d2ed9-116">An <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d2ed9-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d2ed9-117">Remarks</span></span>  
 <span data-ttu-id="d2ed9-118">Literały instrukcji przetwarzania XML wskazują, jak aplikacje należy przetworzyć dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="d2ed9-118">XML processing instruction literals indicate how applications should process an XML document.</span></span> <span data-ttu-id="d2ed9-119">Podczas ładowania dokumentu XML aplikacji Aplikacja może sprawdzać, czy instrukcje przetwarzania XML w celu ustalenia sposobu przetwarzania dokumentu.</span><span class="sxs-lookup"><span data-stu-id="d2ed9-119">When an application loads an XML document, the application can check the XML processing instructions to determine how to process the document.</span></span> <span data-ttu-id="d2ed9-120">Aplikacja interpretuje słowa kluczowe znaczenie `piName` i `piData`.</span><span class="sxs-lookup"><span data-stu-id="d2ed9-120">The application interprets the meaning of `piName` and `piData`.</span></span>  
  
 <span data-ttu-id="d2ed9-121">Literał dokumentu XML używa składni, która jest podobna do instrukcji przetwarzania XML.</span><span class="sxs-lookup"><span data-stu-id="d2ed9-121">The XML document literal uses syntax that is similar to that of the XML processing instruction.</span></span> <span data-ttu-id="d2ed9-122">Aby uzyskać więcej informacji, zobacz [literał dokumentu XML](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).</span><span class="sxs-lookup"><span data-stu-id="d2ed9-122">For more information, see [XML Document Literal](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d2ed9-123">`piName` Element nie może rozpoczynać się ciągi "xml" lub "XML", ponieważ Specyfikacja XML 1.0 rezerwuje tych identyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="d2ed9-123">The `piName` element cannot begin with the strings "xml" or "XML", because the XML 1.0 specification reserves those identifiers.</span></span>  
  
 <span data-ttu-id="d2ed9-124">Można przypisać literał instrukcji przetwarzania XML do zmiennej lub ją dołączyć literał dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="d2ed9-124">You can assign an XML processing instruction literal to a variable or include it in an XML document literal.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d2ed9-125">Literał XML może obejmować wiele wierszy, bez konieczności używania znaków kontynuacji wiersza.</span><span class="sxs-lookup"><span data-stu-id="d2ed9-125">An XML literal can span multiple lines without needing line continuation characters.</span></span> <span data-ttu-id="d2ed9-126">Dzięki temu można skopiować zawartość z dokumentu XML i wklej go bezpośrednio w programie Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d2ed9-126">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="d2ed9-127">Kompilator Visual Basic konwertuje literał instrukcji przetwarzania XML do wywołania <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> konstruktora.</span><span class="sxs-lookup"><span data-stu-id="d2ed9-127">The Visual Basic compiler converts the XML processing instruction literal to a call to the <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2ed9-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="d2ed9-128">Example</span></span>  
 <span data-ttu-id="d2ed9-129">Poniższy przykład tworzy instrukcja przetwarzania zidentyfikowanie arkusza stylów dla dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="d2ed9-129">The following example creates a processing instruction identifying a style-sheet for an XML document.</span></span>  
  
 [!code-vb[VbXMLSamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="d2ed9-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d2ed9-130">See also</span></span>

- <xref:System.Xml.Linq.XProcessingInstruction>
- [<span data-ttu-id="d2ed9-131">Literał dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="d2ed9-131">XML Document Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [<span data-ttu-id="d2ed9-132">Literały XML</span><span class="sxs-lookup"><span data-stu-id="d2ed9-132">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="d2ed9-133">Tworzenie XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d2ed9-133">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
