---
title: Literał dokumentu XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralDocument
helpviewer_keywords:
- XML document literal [Visual Basic]
- XML literals [Visual Basic], document
- XML documents [Visual Basic], creating
- document literal [Visual Basic]
ms.assetid: f7bbee56-0911-41de-b907-96f20450137b
ms.openlocfilehash: 86780d53c2261b6440f515fc09512fba313667dc
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56964958"
---
# <a name="xml-document-literal-visual-basic"></a><span data-ttu-id="ea784-102">Literał dokumentu XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ea784-102">XML Document Literal (Visual Basic)</span></span>
<span data-ttu-id="ea784-103">Literał reprezentujący <xref:System.Xml.Linq.XDocument> obiektu.</span><span class="sxs-lookup"><span data-stu-id="ea784-103">A literal representing an <xref:System.Xml.Linq.XDocument> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea784-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ea784-104">Syntax</span></span>  
  
```xml  
<?xml version="1.0" [encoding="encoding"] [standalone="standalone"] ?>  
[ piCommentList ]  
rootElement  
[ piCommentList ]  
```  
  
## <a name="parts"></a><span data-ttu-id="ea784-105">Części</span><span class="sxs-lookup"><span data-stu-id="ea784-105">Parts</span></span>  
  
|<span data-ttu-id="ea784-106">Termin</span><span class="sxs-lookup"><span data-stu-id="ea784-106">Term</span></span>|<span data-ttu-id="ea784-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="ea784-107">Definition</span></span>|  
|---|---|  
|`encoding`|<span data-ttu-id="ea784-108">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="ea784-108">Optional.</span></span> <span data-ttu-id="ea784-109">Tekst dosłowny deklarowanie kodowania, która używa dokumentu.</span><span class="sxs-lookup"><span data-stu-id="ea784-109">Literal text declaring which encoding the document uses.</span></span>|  
|`standalone`|<span data-ttu-id="ea784-110">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="ea784-110">Optional.</span></span> <span data-ttu-id="ea784-111">Literał tekstowy.</span><span class="sxs-lookup"><span data-stu-id="ea784-111">Literal text.</span></span> <span data-ttu-id="ea784-112">Musi być "yes" lub "no".</span><span class="sxs-lookup"><span data-stu-id="ea784-112">Must be "yes" or "no".</span></span>|  
|`piCommentList`|<span data-ttu-id="ea784-113">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="ea784-113">Optional.</span></span> <span data-ttu-id="ea784-114">Lista instrukcji przetwarzania XML i komentarze XML.</span><span class="sxs-lookup"><span data-stu-id="ea784-114">List of XML processing instructions and XML comments.</span></span> <span data-ttu-id="ea784-115">Ma następujący format:</span><span class="sxs-lookup"><span data-stu-id="ea784-115">Takes the following format:</span></span><br /><br /> <span data-ttu-id="ea784-116">`piComment [` `piComment` `... ]`</span><span class="sxs-lookup"><span data-stu-id="ea784-116">`piComment [` `piComment` `... ]`</span></span><br /><br /> <span data-ttu-id="ea784-117">Każdy `piComment` może być jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="ea784-117">Each `piComment` can be one of the following:</span></span><br /><br /> <span data-ttu-id="ea784-118">-   [Literał instrukcji przetwarzania XML](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span><span class="sxs-lookup"><span data-stu-id="ea784-118">-   [XML Processing Instruction Literal](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span></span><br /><span data-ttu-id="ea784-119">-   [Literał komentarza XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span><span class="sxs-lookup"><span data-stu-id="ea784-119">-   [XML Comment Literal](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span></span>|  
|`rootElement`|<span data-ttu-id="ea784-120">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="ea784-120">Required.</span></span> <span data-ttu-id="ea784-121">Element główny dokumentu.</span><span class="sxs-lookup"><span data-stu-id="ea784-121">Root element of the document.</span></span> <span data-ttu-id="ea784-122">Format jest jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="ea784-122">The format is one of the following:</span></span><br /><br /> <ul><li><span data-ttu-id="ea784-123">[Literał elementu XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="ea784-123">[XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span></li><li><span data-ttu-id="ea784-124">Osadzone wyrażenie w formie `<%=` `elementExp` `%>`.</span><span class="sxs-lookup"><span data-stu-id="ea784-124">Embedded expression of the form `<%=` `elementExp` `%>`.</span></span> <span data-ttu-id="ea784-125">`elementExp` Zwraca jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="ea784-125">The `elementExp` returns one of the following:</span></span><br /><br /> <ul><li><span data-ttu-id="ea784-126"><xref:System.Xml.Linq.XElement> Obiektu.</span><span class="sxs-lookup"><span data-stu-id="ea784-126">An <xref:System.Xml.Linq.XElement> object.</span></span></li><li><span data-ttu-id="ea784-127">Kolekcja zawierająca jeden <xref:System.Xml.Linq.XElement> obiektu i dowolną liczbę <xref:System.Xml.Linq.XProcessingInstruction> i <xref:System.Xml.Linq.XComment> obiektów.</span><span class="sxs-lookup"><span data-stu-id="ea784-127">A collection that contains one <xref:System.Xml.Linq.XElement> object and any number of <xref:System.Xml.Linq.XProcessingInstruction> and <xref:System.Xml.Linq.XComment> objects.</span></span></li></ul></li></ul><br /> <span data-ttu-id="ea784-128">Aby uzyskać więcej informacji, zobacz [wyrażenia osadzone w XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="ea784-128">For more information, see [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="ea784-129">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ea784-129">Return Value</span></span>  
 <span data-ttu-id="ea784-130"><xref:System.Xml.Linq.XDocument> Obiektu.</span><span class="sxs-lookup"><span data-stu-id="ea784-130">An <xref:System.Xml.Linq.XDocument> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ea784-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ea784-131">Remarks</span></span>  
 <span data-ttu-id="ea784-132">Literał dokumentu XML jest identyfikowany przez deklarację XML na początku literału.</span><span class="sxs-lookup"><span data-stu-id="ea784-132">An XML document literal is identified by the XML declaration at the start of the literal.</span></span> <span data-ttu-id="ea784-133">Mimo że literał dokumentu XML musi mieć dokładnie jeden element główny XML, może mieć dowolną liczbę instrukcji przetwarzania XML i komentarze XML.</span><span class="sxs-lookup"><span data-stu-id="ea784-133">Although each XML document literal must have exactly one root XML element, it can have any number of XML processing instructions and XML comments.</span></span>  
  
 <span data-ttu-id="ea784-134">Literał dokumentu XML nie może występować w elemencie XML.</span><span class="sxs-lookup"><span data-stu-id="ea784-134">An XML document literal cannot appear in an XML element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ea784-135">Literał XML może obejmować wiele wierszy, bez używania znaków kontynuacji wiersza.</span><span class="sxs-lookup"><span data-stu-id="ea784-135">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="ea784-136">Dzięki temu można skopiować zawartość z dokumentu XML i wklej go bezpośrednio w programie Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ea784-136">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="ea784-137">Kompilator Visual Basic konwertuje literał dokumentu XML na wywołania <xref:System.Xml.Linq.XDocument.%23ctor%2A> i <xref:System.Xml.Linq.XDeclaration.%23ctor%2A> konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="ea784-137">The Visual Basic compiler converts the XML document literal into calls to the <xref:System.Xml.Linq.XDocument.%23ctor%2A> and <xref:System.Xml.Linq.XDeclaration.%23ctor%2A> constructors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea784-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="ea784-138">Example</span></span>  
 <span data-ttu-id="ea784-139">Poniższy przykład tworzy dokument XML, który ma deklaracji XML, instrukcję przetwarzania, komentarz i element, który zawiera inny element.</span><span class="sxs-lookup"><span data-stu-id="ea784-139">The following example creates an XML document that has an XML declaration, a processing instruction, a comment, and an element that contains another element.</span></span>  
  
 [!code-vb[VbXMLSamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="ea784-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ea784-140">See also</span></span>
- <xref:System.Xml.Linq.XElement>
- <xref:System.Xml.Linq.XProcessingInstruction>
- <xref:System.Xml.Linq.XComment>
- <xref:System.Xml.Linq.XDocument>
- [<span data-ttu-id="ea784-141">Literał instrukcji przetwarzającej kod XML</span><span class="sxs-lookup"><span data-stu-id="ea784-141">XML Processing Instruction Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md)
- [<span data-ttu-id="ea784-142">Literał komentarza XML</span><span class="sxs-lookup"><span data-stu-id="ea784-142">XML Comment Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)
- [<span data-ttu-id="ea784-143">Literał elementu XML</span><span class="sxs-lookup"><span data-stu-id="ea784-143">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="ea784-144">Literały XML</span><span class="sxs-lookup"><span data-stu-id="ea784-144">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="ea784-145">Tworzenie XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ea784-145">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="ea784-146">Wyrażenia osadzone w XML</span><span class="sxs-lookup"><span data-stu-id="ea784-146">Embedded Expressions in XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
