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
ms.openlocfilehash: f58c1365e145166dfe122d455854d44526300a1e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58814630"
---
# <a name="xml-document-literal-visual-basic"></a><span data-ttu-id="40633-102">Literał dokumentu XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="40633-102">XML Document Literal (Visual Basic)</span></span>
<span data-ttu-id="40633-103">Literał reprezentujący <xref:System.Xml.Linq.XDocument> obiektu.</span><span class="sxs-lookup"><span data-stu-id="40633-103">A literal representing an <xref:System.Xml.Linq.XDocument> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40633-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="40633-104">Syntax</span></span>  
  
```xml  
<?xml version="1.0" [encoding="encoding"] [standalone="standalone"] ?>  
[ piCommentList ]  
rootElement  
[ piCommentList ]  
```  
  
## <a name="parts"></a><span data-ttu-id="40633-105">Części</span><span class="sxs-lookup"><span data-stu-id="40633-105">Parts</span></span>  
  
|<span data-ttu-id="40633-106">Termin</span><span class="sxs-lookup"><span data-stu-id="40633-106">Term</span></span>|<span data-ttu-id="40633-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="40633-107">Definition</span></span>|  
|---|---|  
|`encoding`|<span data-ttu-id="40633-108">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="40633-108">Optional.</span></span> <span data-ttu-id="40633-109">Tekst dosłowny deklarowanie kodowania, która używa dokumentu.</span><span class="sxs-lookup"><span data-stu-id="40633-109">Literal text declaring which encoding the document uses.</span></span>|  
|`standalone`|<span data-ttu-id="40633-110">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="40633-110">Optional.</span></span> <span data-ttu-id="40633-111">Literał tekstowy.</span><span class="sxs-lookup"><span data-stu-id="40633-111">Literal text.</span></span> <span data-ttu-id="40633-112">Musi być "yes" lub "no".</span><span class="sxs-lookup"><span data-stu-id="40633-112">Must be "yes" or "no".</span></span>|  
|`piCommentList`|<span data-ttu-id="40633-113">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="40633-113">Optional.</span></span> <span data-ttu-id="40633-114">Lista instrukcji przetwarzania XML i komentarze XML.</span><span class="sxs-lookup"><span data-stu-id="40633-114">List of XML processing instructions and XML comments.</span></span> <span data-ttu-id="40633-115">Ma następujący format:</span><span class="sxs-lookup"><span data-stu-id="40633-115">Takes the following format:</span></span><br /><br /> <span data-ttu-id="40633-116">`piComment [` `piComment` `... ]`</span><span class="sxs-lookup"><span data-stu-id="40633-116">`piComment [` `piComment` `... ]`</span></span><br /><br /> <span data-ttu-id="40633-117">Każdy `piComment` może być jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="40633-117">Each `piComment` can be one of the following:</span></span><br /><br /> <span data-ttu-id="40633-118">-   [Literał instrukcji przetwarzania XML](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span><span class="sxs-lookup"><span data-stu-id="40633-118">-   [XML Processing Instruction Literal](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span></span><br /><span data-ttu-id="40633-119">-   [Literał komentarza XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span><span class="sxs-lookup"><span data-stu-id="40633-119">-   [XML Comment Literal](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span></span>|  
|`rootElement`|<span data-ttu-id="40633-120">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="40633-120">Required.</span></span> <span data-ttu-id="40633-121">Element główny dokumentu.</span><span class="sxs-lookup"><span data-stu-id="40633-121">Root element of the document.</span></span> <span data-ttu-id="40633-122">Format jest jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="40633-122">The format is one of the following:</span></span><br /><br /> <ul><li><span data-ttu-id="40633-123">[Literał elementu XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="40633-123">[XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span></li><li><span data-ttu-id="40633-124">Osadzone wyrażenie w formie `<%=` `elementExp` `%>`.</span><span class="sxs-lookup"><span data-stu-id="40633-124">Embedded expression of the form `<%=` `elementExp` `%>`.</span></span> <span data-ttu-id="40633-125">`elementExp` Zwraca jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="40633-125">The `elementExp` returns one of the following:</span></span><br /><br /> <ul><li><span data-ttu-id="40633-126"><xref:System.Xml.Linq.XElement> Obiektu.</span><span class="sxs-lookup"><span data-stu-id="40633-126">An <xref:System.Xml.Linq.XElement> object.</span></span></li><li><span data-ttu-id="40633-127">Kolekcja zawierająca jeden <xref:System.Xml.Linq.XElement> obiektu i dowolną liczbę <xref:System.Xml.Linq.XProcessingInstruction> i <xref:System.Xml.Linq.XComment> obiektów.</span><span class="sxs-lookup"><span data-stu-id="40633-127">A collection that contains one <xref:System.Xml.Linq.XElement> object and any number of <xref:System.Xml.Linq.XProcessingInstruction> and <xref:System.Xml.Linq.XComment> objects.</span></span></li></ul></li></ul><br /> <span data-ttu-id="40633-128">Aby uzyskać więcej informacji, zobacz [wyrażenia osadzone w XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="40633-128">For more information, see [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="40633-129">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="40633-129">Return Value</span></span>  
 <span data-ttu-id="40633-130"><xref:System.Xml.Linq.XDocument> Obiektu.</span><span class="sxs-lookup"><span data-stu-id="40633-130">An <xref:System.Xml.Linq.XDocument> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="40633-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="40633-131">Remarks</span></span>  
 <span data-ttu-id="40633-132">Literał dokumentu XML jest identyfikowany przez deklarację XML na początku literału.</span><span class="sxs-lookup"><span data-stu-id="40633-132">An XML document literal is identified by the XML declaration at the start of the literal.</span></span> <span data-ttu-id="40633-133">Mimo że literał dokumentu XML musi mieć dokładnie jeden element główny XML, może mieć dowolną liczbę instrukcji przetwarzania XML i komentarze XML.</span><span class="sxs-lookup"><span data-stu-id="40633-133">Although each XML document literal must have exactly one root XML element, it can have any number of XML processing instructions and XML comments.</span></span>  
  
 <span data-ttu-id="40633-134">Literał dokumentu XML nie może występować w elemencie XML.</span><span class="sxs-lookup"><span data-stu-id="40633-134">An XML document literal cannot appear in an XML element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="40633-135">Literał XML może obejmować wiele wierszy, bez używania znaków kontynuacji wiersza.</span><span class="sxs-lookup"><span data-stu-id="40633-135">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="40633-136">Dzięki temu można skopiować zawartość z dokumentu XML i wklej go bezpośrednio w programie Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="40633-136">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="40633-137">Kompilator Visual Basic konwertuje literał dokumentu XML na wywołania <xref:System.Xml.Linq.XDocument.%23ctor%2A> i <xref:System.Xml.Linq.XDeclaration.%23ctor%2A> konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="40633-137">The Visual Basic compiler converts the XML document literal into calls to the <xref:System.Xml.Linq.XDocument.%23ctor%2A> and <xref:System.Xml.Linq.XDeclaration.%23ctor%2A> constructors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40633-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="40633-138">Example</span></span>  
 <span data-ttu-id="40633-139">Poniższy przykład tworzy dokument XML, który ma deklaracji XML, instrukcję przetwarzania, komentarz i element, który zawiera inny element.</span><span class="sxs-lookup"><span data-stu-id="40633-139">The following example creates an XML document that has an XML declaration, a processing instruction, a comment, and an element that contains another element.</span></span>  
  
 [!code-vb[VbXMLSamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="40633-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="40633-140">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- <xref:System.Xml.Linq.XProcessingInstruction>
- <xref:System.Xml.Linq.XComment>
- <xref:System.Xml.Linq.XDocument>
- [<span data-ttu-id="40633-141">Literał instrukcji przetwarzającej kod XML</span><span class="sxs-lookup"><span data-stu-id="40633-141">XML Processing Instruction Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md)
- [<span data-ttu-id="40633-142">Literał komentarza XML</span><span class="sxs-lookup"><span data-stu-id="40633-142">XML Comment Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)
- [<span data-ttu-id="40633-143">Literał elementu XML</span><span class="sxs-lookup"><span data-stu-id="40633-143">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="40633-144">Literały XML</span><span class="sxs-lookup"><span data-stu-id="40633-144">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="40633-145">Tworzenie XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="40633-145">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="40633-146">Wyrażenia osadzone w XML</span><span class="sxs-lookup"><span data-stu-id="40633-146">Embedded Expressions in XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
