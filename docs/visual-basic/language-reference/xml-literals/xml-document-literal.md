---
title: Literał dokumentu XML
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralDocument
helpviewer_keywords:
- XML document literal [Visual Basic]
- XML literals [Visual Basic], document
- XML documents [Visual Basic], creating
- document literal [Visual Basic]
ms.assetid: f7bbee56-0911-41de-b907-96f20450137b
ms.openlocfilehash: db77cccd26c87e271d6db45ce514ab6dabbc53e3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349384"
---
# <a name="xml-document-literal-visual-basic"></a><span data-ttu-id="4ade9-102">Literał dokumentu XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4ade9-102">XML Document Literal (Visual Basic)</span></span>
<span data-ttu-id="4ade9-103">Literał reprezentujący obiekt <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="4ade9-103">A literal representing an <xref:System.Xml.Linq.XDocument> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ade9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4ade9-104">Syntax</span></span>  
  
```xml  
<?xml version="1.0" [encoding="encoding"] [standalone="standalone"] ?>  
[ piCommentList ]  
rootElement  
[ piCommentList ]  
```  
  
## <a name="parts"></a><span data-ttu-id="4ade9-105">Części</span><span class="sxs-lookup"><span data-stu-id="4ade9-105">Parts</span></span>  
  
|<span data-ttu-id="4ade9-106">Termin</span><span class="sxs-lookup"><span data-stu-id="4ade9-106">Term</span></span>|<span data-ttu-id="4ade9-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="4ade9-107">Definition</span></span>|  
|---|---|  
|`encoding`|<span data-ttu-id="4ade9-108">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="4ade9-108">Optional.</span></span> <span data-ttu-id="4ade9-109">Tekst literału deklarujący kodowanie używane przez dokument.</span><span class="sxs-lookup"><span data-stu-id="4ade9-109">Literal text declaring which encoding the document uses.</span></span>|  
|`standalone`|<span data-ttu-id="4ade9-110">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="4ade9-110">Optional.</span></span> <span data-ttu-id="4ade9-111">Tekst literału.</span><span class="sxs-lookup"><span data-stu-id="4ade9-111">Literal text.</span></span> <span data-ttu-id="4ade9-112">Musi mieć wartość "yes" lub "No".</span><span class="sxs-lookup"><span data-stu-id="4ade9-112">Must be "yes" or "no".</span></span>|  
|`piCommentList`|<span data-ttu-id="4ade9-113">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="4ade9-113">Optional.</span></span> <span data-ttu-id="4ade9-114">Lista instrukcji przetwarzania XML i komentarzy XML.</span><span class="sxs-lookup"><span data-stu-id="4ade9-114">List of XML processing instructions and XML comments.</span></span> <span data-ttu-id="4ade9-115">Przyjmuje następujący format:</span><span class="sxs-lookup"><span data-stu-id="4ade9-115">Takes the following format:</span></span><br /><br /> <span data-ttu-id="4ade9-116">`piComment [` `piComment` `... ]`</span><span class="sxs-lookup"><span data-stu-id="4ade9-116">`piComment [` `piComment` `... ]`</span></span><br /><br /> <span data-ttu-id="4ade9-117">Każdy `piComment` może być jednym z następujących:</span><span class="sxs-lookup"><span data-stu-id="4ade9-117">Each `piComment` can be one of the following:</span></span><br /><br /> <span data-ttu-id="4ade9-118">-   [literał instrukcji przetwarzania XML](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span><span class="sxs-lookup"><span data-stu-id="4ade9-118">-   [XML Processing Instruction Literal](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span></span><br /><span data-ttu-id="4ade9-119">-   [literał komentarza XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span><span class="sxs-lookup"><span data-stu-id="4ade9-119">-   [XML Comment Literal](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span></span>|  
|`rootElement`|<span data-ttu-id="4ade9-120">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="4ade9-120">Required.</span></span> <span data-ttu-id="4ade9-121">Element główny dokumentu.</span><span class="sxs-lookup"><span data-stu-id="4ade9-121">Root element of the document.</span></span> <span data-ttu-id="4ade9-122">Jest to jeden z następujących formatów:</span><span class="sxs-lookup"><span data-stu-id="4ade9-122">The format is one of the following:</span></span><br /><br /> <ul><li><span data-ttu-id="4ade9-123">[Literal elementu XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="4ade9-123">[XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span></li><li><span data-ttu-id="4ade9-124">Osadzone wyrażenie `<%=` formularza `elementExp` `%>`.</span><span class="sxs-lookup"><span data-stu-id="4ade9-124">Embedded expression of the form `<%=` `elementExp` `%>`.</span></span> <span data-ttu-id="4ade9-125">`elementExp` zwraca jedną z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="4ade9-125">The `elementExp` returns one of the following:</span></span><br /><br /> <ul><li><span data-ttu-id="4ade9-126">Obiekt <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="4ade9-126">An <xref:System.Xml.Linq.XElement> object.</span></span></li><li><span data-ttu-id="4ade9-127">Kolekcja zawierająca jeden <xref:System.Xml.Linq.XElement> obiektu i dowolną liczbę obiektów <xref:System.Xml.Linq.XProcessingInstruction> i <xref:System.Xml.Linq.XComment>.</span><span class="sxs-lookup"><span data-stu-id="4ade9-127">A collection that contains one <xref:System.Xml.Linq.XElement> object and any number of <xref:System.Xml.Linq.XProcessingInstruction> and <xref:System.Xml.Linq.XComment> objects.</span></span></li></ul></li></ul><br /> <span data-ttu-id="4ade9-128">Aby uzyskać więcej informacji, zobacz [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="4ade9-128">For more information, see [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="4ade9-129">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4ade9-129">Return Value</span></span>  
 <span data-ttu-id="4ade9-130">Obiekt <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="4ade9-130">An <xref:System.Xml.Linq.XDocument> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4ade9-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4ade9-131">Remarks</span></span>  
 <span data-ttu-id="4ade9-132">Literał dokumentu XML jest identyfikowany przez deklarację XML na początku literału.</span><span class="sxs-lookup"><span data-stu-id="4ade9-132">An XML document literal is identified by the XML declaration at the start of the literal.</span></span> <span data-ttu-id="4ade9-133">Chociaż każdy literał dokumentu XML musi mieć dokładnie jeden główny element XML, może zawierać dowolną liczbę instrukcji przetwarzania XML i komentarzy XML.</span><span class="sxs-lookup"><span data-stu-id="4ade9-133">Although each XML document literal must have exactly one root XML element, it can have any number of XML processing instructions and XML comments.</span></span>  
  
 <span data-ttu-id="4ade9-134">Literał dokumentu XML nie może występować w elemencie XML.</span><span class="sxs-lookup"><span data-stu-id="4ade9-134">An XML document literal cannot appear in an XML element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4ade9-135">Literał XML może obejmować wiele wierszy bez używania znaków kontynuacji wiersza.</span><span class="sxs-lookup"><span data-stu-id="4ade9-135">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="4ade9-136">Dzięki temu można skopiować zawartość z dokumentu XML i wkleić ją bezpośrednio do programu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4ade9-136">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="4ade9-137">Kompilator Visual Basic konwertuje literał dokumentu XML na wywołania konstruktorów <xref:System.Xml.Linq.XDocument.%23ctor%2A> i <xref:System.Xml.Linq.XDeclaration.%23ctor%2A>.</span><span class="sxs-lookup"><span data-stu-id="4ade9-137">The Visual Basic compiler converts the XML document literal into calls to the <xref:System.Xml.Linq.XDocument.%23ctor%2A> and <xref:System.Xml.Linq.XDeclaration.%23ctor%2A> constructors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ade9-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="4ade9-138">Example</span></span>  
 <span data-ttu-id="4ade9-139">Poniższy przykład tworzy dokument XML, który ma deklarację XML, instrukcję przetwarzania, komentarz i element, który zawiera inny element.</span><span class="sxs-lookup"><span data-stu-id="4ade9-139">The following example creates an XML document that has an XML declaration, a processing instruction, a comment, and an element that contains another element.</span></span>  
  
 [!code-vb[VbXMLSamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="4ade9-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4ade9-140">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- <xref:System.Xml.Linq.XProcessingInstruction>
- <xref:System.Xml.Linq.XComment>
- <xref:System.Xml.Linq.XDocument>
- [<span data-ttu-id="4ade9-141">Literał instrukcji przetwarzającej kod XML</span><span class="sxs-lookup"><span data-stu-id="4ade9-141">XML Processing Instruction Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md)
- [<span data-ttu-id="4ade9-142">Literał komentarza XML</span><span class="sxs-lookup"><span data-stu-id="4ade9-142">XML Comment Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)
- [<span data-ttu-id="4ade9-143">Literał elementu XML</span><span class="sxs-lookup"><span data-stu-id="4ade9-143">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="4ade9-144">Literały XML</span><span class="sxs-lookup"><span data-stu-id="4ade9-144">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="4ade9-145">Tworzenie kodu XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4ade9-145">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="4ade9-146">Wyrażenia osadzone w XML</span><span class="sxs-lookup"><span data-stu-id="4ade9-146">Embedded Expressions in XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
