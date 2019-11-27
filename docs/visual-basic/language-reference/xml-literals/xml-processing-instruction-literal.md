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
# <a name="xml-processing-instruction-literal-visual-basic"></a><span data-ttu-id="c76f0-102">Literał instrukcji przetwarzającej kod XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c76f0-102">XML Processing Instruction Literal (Visual Basic)</span></span>
<span data-ttu-id="c76f0-103">Literał reprezentujący obiekt <xref:System.Xml.Linq.XProcessingInstruction>.</span><span class="sxs-lookup"><span data-stu-id="c76f0-103">A literal representing an <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c76f0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c76f0-104">Syntax</span></span>  
  
```xml  
<?piName [ = piData ] ?>  
```  
  
## <a name="parts"></a><span data-ttu-id="c76f0-105">Części</span><span class="sxs-lookup"><span data-stu-id="c76f0-105">Parts</span></span>  
 `<?`  
 <span data-ttu-id="c76f0-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="c76f0-106">Required.</span></span> <span data-ttu-id="c76f0-107">Wskazuje początek literału instrukcji przetwarzania XML.</span><span class="sxs-lookup"><span data-stu-id="c76f0-107">Denotes the start of the XML processing instruction literal.</span></span>  
  
 `piName`  
 <span data-ttu-id="c76f0-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="c76f0-108">Required.</span></span> <span data-ttu-id="c76f0-109">Nazwa wskazująca, która aplikacja jest celem instrukcji przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="c76f0-109">Name indicating which application the processing instruction targets.</span></span> <span data-ttu-id="c76f0-110">Nie można rozpocząć od "XML" lub "XML".</span><span class="sxs-lookup"><span data-stu-id="c76f0-110">Cannot begin with "xml" or "XML".</span></span>  
  
 `piData`  
 <span data-ttu-id="c76f0-111">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="c76f0-111">Optional.</span></span> <span data-ttu-id="c76f0-112">Ciąg wskazujący, w jaki sposób aplikacja, do której należy `piName`, powinna przetwarzać dokument XML.</span><span class="sxs-lookup"><span data-stu-id="c76f0-112">String indicating how the application targeted by `piName` should process the XML document.</span></span>  
  
 `?>`  
 <span data-ttu-id="c76f0-113">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="c76f0-113">Required.</span></span> <span data-ttu-id="c76f0-114">Oznacza koniec instrukcji przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="c76f0-114">Denotes the end of the processing instruction.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c76f0-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c76f0-115">Return Value</span></span>  
 <span data-ttu-id="c76f0-116">Obiekt <xref:System.Xml.Linq.XProcessingInstruction>.</span><span class="sxs-lookup"><span data-stu-id="c76f0-116">An <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c76f0-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c76f0-117">Remarks</span></span>  
 <span data-ttu-id="c76f0-118">Literały instrukcji przetwarzania XML wskazują, w jaki sposób aplikacje powinny przetwarzać dokument XML.</span><span class="sxs-lookup"><span data-stu-id="c76f0-118">XML processing instruction literals indicate how applications should process an XML document.</span></span> <span data-ttu-id="c76f0-119">Gdy aplikacja ładuje dokument XML, aplikacja może sprawdzić instrukcje przetwarzania XML, aby określić sposób przetwarzania dokumentu.</span><span class="sxs-lookup"><span data-stu-id="c76f0-119">When an application loads an XML document, the application can check the XML processing instructions to determine how to process the document.</span></span> <span data-ttu-id="c76f0-120">Aplikacja interpretuje znaczenie `piName` i `piData`.</span><span class="sxs-lookup"><span data-stu-id="c76f0-120">The application interprets the meaning of `piName` and `piData`.</span></span>  
  
 <span data-ttu-id="c76f0-121">Literał dokumentu XML używa składni podobnej do tej instrukcji przetwarzania XML.</span><span class="sxs-lookup"><span data-stu-id="c76f0-121">The XML document literal uses syntax that is similar to that of the XML processing instruction.</span></span> <span data-ttu-id="c76f0-122">Aby uzyskać więcej informacji, zobacz [literał dokumentu XML](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).</span><span class="sxs-lookup"><span data-stu-id="c76f0-122">For more information, see [XML Document Literal](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c76f0-123">Element `piName` nie może rozpoczynać się od ciągu "XML" lub "XML", ponieważ specyfikacja XML 1,0 rezerwuje te identyfikatory.</span><span class="sxs-lookup"><span data-stu-id="c76f0-123">The `piName` element cannot begin with the strings "xml" or "XML", because the XML 1.0 specification reserves those identifiers.</span></span>  
  
 <span data-ttu-id="c76f0-124">Do zmiennej można przypisać literał instrukcji przetwarzania XML lub dodać go do literału dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="c76f0-124">You can assign an XML processing instruction literal to a variable or include it in an XML document literal.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c76f0-125">Literał XML może obejmować wiele wierszy bez znaków kontynuacji wiersza.</span><span class="sxs-lookup"><span data-stu-id="c76f0-125">An XML literal can span multiple lines without needing line continuation characters.</span></span> <span data-ttu-id="c76f0-126">Dzięki temu można skopiować zawartość z dokumentu XML i wkleić ją bezpośrednio do programu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c76f0-126">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="c76f0-127">Kompilator Visual Basic konwertuje literał instrukcji przetwarzania XML na wywołanie konstruktora <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A>.</span><span class="sxs-lookup"><span data-stu-id="c76f0-127">The Visual Basic compiler converts the XML processing instruction literal to a call to the <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c76f0-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="c76f0-128">Example</span></span>  
 <span data-ttu-id="c76f0-129">Poniższy przykład tworzy instrukcję przetwarzania identyfikującą arkusz stylów dla dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="c76f0-129">The following example creates a processing instruction identifying a style-sheet for an XML document.</span></span>  
  
 [!code-vb[VbXMLSamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="c76f0-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c76f0-130">See also</span></span>

- <xref:System.Xml.Linq.XProcessingInstruction>
- [<span data-ttu-id="c76f0-131">Literał dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="c76f0-131">XML Document Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [<span data-ttu-id="c76f0-132">Literały XML</span><span class="sxs-lookup"><span data-stu-id="c76f0-132">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="c76f0-133">Tworzenie kodu XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c76f0-133">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
