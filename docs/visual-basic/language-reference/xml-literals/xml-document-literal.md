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
ms.openlocfilehash: bd2ecfb93cfcdb7cf9c115f9a44ac47dd74c4b53
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="xml-document-literal-visual-basic"></a><span data-ttu-id="d6064-102">Literał dokumentu XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d6064-102">XML Document Literal (Visual Basic)</span></span>
<span data-ttu-id="d6064-103">Literał reprezentujący <xref:System.Xml.Linq.XDocument> obiektu.</span><span class="sxs-lookup"><span data-stu-id="d6064-103">A literal representing an <xref:System.Xml.Linq.XDocument> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6064-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d6064-104">Syntax</span></span>  
  
```xml  
<?xml version="1.0" [encoding="encoding"] [standalone="standalone"] ?>  
[ piCommentList ]  
rootElement  
[ piCommentList ]  
```  
  
## <a name="parts"></a><span data-ttu-id="d6064-105">Części</span><span class="sxs-lookup"><span data-stu-id="d6064-105">Parts</span></span>  
  
|<span data-ttu-id="d6064-106">Termin</span><span class="sxs-lookup"><span data-stu-id="d6064-106">Term</span></span>|<span data-ttu-id="d6064-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="d6064-107">Definition</span></span>|  
|---|---|  
|`encoding`|<span data-ttu-id="d6064-108">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="d6064-108">Optional.</span></span> <span data-ttu-id="d6064-109">Używa literały tekstowe zadeklarowanie, które kodowania dokumentu.</span><span class="sxs-lookup"><span data-stu-id="d6064-109">Literal text declaring which encoding the document uses.</span></span>|  
|`standalone`|<span data-ttu-id="d6064-110">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="d6064-110">Optional.</span></span> <span data-ttu-id="d6064-111">Literały tekstowe.</span><span class="sxs-lookup"><span data-stu-id="d6064-111">Literal text.</span></span> <span data-ttu-id="d6064-112">Musi być "tak" lub "no".</span><span class="sxs-lookup"><span data-stu-id="d6064-112">Must be "yes" or "no".</span></span>|  
|`piCommentList`|<span data-ttu-id="d6064-113">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="d6064-113">Optional.</span></span> <span data-ttu-id="d6064-114">Lista instrukcji przetwarzania XML i komentarze XML.</span><span class="sxs-lookup"><span data-stu-id="d6064-114">List of XML processing instructions and XML comments.</span></span> <span data-ttu-id="d6064-115">Ma następujący format:</span><span class="sxs-lookup"><span data-stu-id="d6064-115">Takes the following format:</span></span><br /><br /> <span data-ttu-id="d6064-116">`piComment [` `piComment` `... ]`</span><span class="sxs-lookup"><span data-stu-id="d6064-116">`piComment [` `piComment` `... ]`</span></span><br /><br /> <span data-ttu-id="d6064-117">Każdy `piComment` może być jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="d6064-117">Each `piComment` can be one of the following:</span></span><br /><br /> <span data-ttu-id="d6064-118">-   [Literał instrukcji przetwarzającej kod XML](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span><span class="sxs-lookup"><span data-stu-id="d6064-118">-   [XML Processing Instruction Literal](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span></span><br /><span data-ttu-id="d6064-119">-   [Literał komentarza XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span><span class="sxs-lookup"><span data-stu-id="d6064-119">-   [XML Comment Literal](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span></span>|  
|`rootElement`|<span data-ttu-id="d6064-120">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="d6064-120">Required.</span></span> <span data-ttu-id="d6064-121">Element główny dokumentu.</span><span class="sxs-lookup"><span data-stu-id="d6064-121">Root element of the document.</span></span> <span data-ttu-id="d6064-122">Format jest jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="d6064-122">The format is one of the following:</span></span><br /><br /> <ul><li><span data-ttu-id="d6064-123">[Literał elementu XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="d6064-123">[XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span></li><li><span data-ttu-id="d6064-124">Osadzone wyrażenie w postaci `<%=` `elementExp` `%>`.</span><span class="sxs-lookup"><span data-stu-id="d6064-124">Embedded expression of the form `<%=` `elementExp` `%>`.</span></span> <span data-ttu-id="d6064-125">`elementExp` Zwraca jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="d6064-125">The `elementExp` returns one of the following:</span></span><br /><br /> <ul><li><span data-ttu-id="d6064-126"><xref:System.Xml.Linq.XElement> Obiektu.</span><span class="sxs-lookup"><span data-stu-id="d6064-126">An <xref:System.Xml.Linq.XElement> object.</span></span></li><li><span data-ttu-id="d6064-127">Kolekcja, która zawiera jedną <xref:System.Xml.Linq.XElement> obiekt i dowolną liczbę <xref:System.Xml.Linq.XProcessingInstruction> i <xref:System.Xml.Linq.XComment> obiektów.</span><span class="sxs-lookup"><span data-stu-id="d6064-127">A collection that contains one <xref:System.Xml.Linq.XElement> object and any number of <xref:System.Xml.Linq.XProcessingInstruction> and <xref:System.Xml.Linq.XComment> objects.</span></span></li></ul></li></ul><br /> <span data-ttu-id="d6064-128">Aby uzyskać więcej informacji, zobacz [wyrażenia osadzone w XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="d6064-128">For more information, see [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="d6064-129">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d6064-129">Return Value</span></span>  
 <span data-ttu-id="d6064-130"><xref:System.Xml.Linq.XDocument> Obiektu.</span><span class="sxs-lookup"><span data-stu-id="d6064-130">An <xref:System.Xml.Linq.XDocument> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6064-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d6064-131">Remarks</span></span>  
 <span data-ttu-id="d6064-132">Literał dokumentu XML jest identyfikowany przez deklaracja XML na początku literału.</span><span class="sxs-lookup"><span data-stu-id="d6064-132">An XML document literal is identified by the XML declaration at the start of the literal.</span></span> <span data-ttu-id="d6064-133">Mimo że literał dokumentu XML musi mieć dokładnie jeden głównego elementu XML, może mieć dowolną liczbę instrukcji przetwarzania XML i komentarze XML.</span><span class="sxs-lookup"><span data-stu-id="d6064-133">Although each XML document literal must have exactly one root XML element, it can have any number of XML processing instructions and XML comments.</span></span>  
  
 <span data-ttu-id="d6064-134">Literał dokumentu XML nie może występować w elemencie XML.</span><span class="sxs-lookup"><span data-stu-id="d6064-134">An XML document literal cannot appear in an XML element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d6064-135">Literał XML może obejmować wiele wierszy bez użycia znaki kontynuacji wiersza.</span><span class="sxs-lookup"><span data-stu-id="d6064-135">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="d6064-136">Pozwala na kopiowanie zawartości z dokumentu XML i wklej go bezpośrednio w programie Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d6064-136">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="d6064-137">Kompilator Visual Basic konwertuje literał dokumentu XML na wywołania <xref:System.Xml.Linq.XDocument.%23ctor%2A> i <xref:System.Xml.Linq.XDeclaration.%23ctor%2A> konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="d6064-137">The Visual Basic compiler converts the XML document literal into calls to the <xref:System.Xml.Linq.XDocument.%23ctor%2A> and <xref:System.Xml.Linq.XDeclaration.%23ctor%2A> constructors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6064-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="d6064-138">Example</span></span>  
 <span data-ttu-id="d6064-139">Poniższy przykład tworzy dokument XML zawierający deklaracja XML, instrukcji przetwarzania komentarz i element, który zawiera inny element.</span><span class="sxs-lookup"><span data-stu-id="d6064-139">The following example creates an XML document that has an XML declaration, a processing instruction, a comment, and an element that contains another element.</span></span>  
  
 [!code-vb[VbXMLSamples#30](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-document-literal_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d6064-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d6064-140">See Also</span></span>  
 <xref:System.Xml.Linq.XElement>  
 <xref:System.Xml.Linq.XProcessingInstruction>  
 <xref:System.Xml.Linq.XComment>  
 <xref:System.Xml.Linq.XDocument>  
 [<span data-ttu-id="d6064-141">Literał instrukcji przetwarzającej kod XML</span><span class="sxs-lookup"><span data-stu-id="d6064-141">XML Processing Instruction Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md)  
 [<span data-ttu-id="d6064-142">Literał komentarza XML</span><span class="sxs-lookup"><span data-stu-id="d6064-142">XML Comment Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)  
 [<span data-ttu-id="d6064-143">Literał elementu XML</span><span class="sxs-lookup"><span data-stu-id="d6064-143">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [<span data-ttu-id="d6064-144">Literały XML</span><span class="sxs-lookup"><span data-stu-id="d6064-144">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="d6064-145">Tworzenie XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d6064-145">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="d6064-146">Wyrażenia osadzone w XML</span><span class="sxs-lookup"><span data-stu-id="d6064-146">Embedded Expressions in XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
