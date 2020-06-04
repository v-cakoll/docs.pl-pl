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
ms.openlocfilehash: 3a2182d2937827bc8dc45e22307a3668420261a2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400205"
---
# <a name="xml-document-literal-visual-basic"></a><span data-ttu-id="d8115-102">Literał dokumentu XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d8115-102">XML Document Literal (Visual Basic)</span></span>
<span data-ttu-id="d8115-103">Literał reprezentujący <xref:System.Xml.Linq.XDocument> obiekt.</span><span class="sxs-lookup"><span data-stu-id="d8115-103">A literal representing an <xref:System.Xml.Linq.XDocument> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8115-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d8115-104">Syntax</span></span>  
  
```xml  
<?xml version="1.0" [encoding="encoding"] [standalone="standalone"] ?>  
[ piCommentList ]  
rootElement  
[ piCommentList ]  
```  
  
## <a name="parts"></a><span data-ttu-id="d8115-105">Części</span><span class="sxs-lookup"><span data-stu-id="d8115-105">Parts</span></span>  
  
|<span data-ttu-id="d8115-106">Termin</span><span class="sxs-lookup"><span data-stu-id="d8115-106">Term</span></span>|<span data-ttu-id="d8115-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="d8115-107">Definition</span></span>|  
|---|---|  
|`encoding`|<span data-ttu-id="d8115-108">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="d8115-108">Optional.</span></span> <span data-ttu-id="d8115-109">Tekst literału deklarujący kodowanie używane przez dokument.</span><span class="sxs-lookup"><span data-stu-id="d8115-109">Literal text declaring which encoding the document uses.</span></span>|  
|`standalone`|<span data-ttu-id="d8115-110">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="d8115-110">Optional.</span></span> <span data-ttu-id="d8115-111">Tekst literału.</span><span class="sxs-lookup"><span data-stu-id="d8115-111">Literal text.</span></span> <span data-ttu-id="d8115-112">Musi mieć wartość "yes" lub "No".</span><span class="sxs-lookup"><span data-stu-id="d8115-112">Must be "yes" or "no".</span></span>|  
|`piCommentList`|<span data-ttu-id="d8115-113">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="d8115-113">Optional.</span></span> <span data-ttu-id="d8115-114">Lista instrukcji przetwarzania XML i komentarzy XML.</span><span class="sxs-lookup"><span data-stu-id="d8115-114">List of XML processing instructions and XML comments.</span></span> <span data-ttu-id="d8115-115">Przyjmuje następujący format:</span><span class="sxs-lookup"><span data-stu-id="d8115-115">Takes the following format:</span></span><br /><br /> <span data-ttu-id="d8115-116">`piComment [` `piComment` `... ]`</span><span class="sxs-lookup"><span data-stu-id="d8115-116">`piComment [` `piComment` `... ]`</span></span><br /><br /> <span data-ttu-id="d8115-117">Każdy `piComment` z nich może być jednym z następujących:</span><span class="sxs-lookup"><span data-stu-id="d8115-117">Each `piComment` can be one of the following:</span></span><br /><br /> <span data-ttu-id="d8115-118">-   [Literał instrukcji przetwarzania XML](xml-processing-instruction-literal.md).</span><span class="sxs-lookup"><span data-stu-id="d8115-118">-   [XML Processing Instruction Literal](xml-processing-instruction-literal.md).</span></span><br /><span data-ttu-id="d8115-119">-   [Literał komentarza XML](xml-comment-literal.md).</span><span class="sxs-lookup"><span data-stu-id="d8115-119">-   [XML Comment Literal](xml-comment-literal.md).</span></span>|  
|`rootElement`|<span data-ttu-id="d8115-120">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="d8115-120">Required.</span></span> <span data-ttu-id="d8115-121">Element główny dokumentu.</span><span class="sxs-lookup"><span data-stu-id="d8115-121">Root element of the document.</span></span> <span data-ttu-id="d8115-122">Jest to jeden z następujących formatów:</span><span class="sxs-lookup"><span data-stu-id="d8115-122">The format is one of the following:</span></span><br /><br /> <ul><li><span data-ttu-id="d8115-123">[Literal elementu XML](xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="d8115-123">[XML Element Literal](xml-element-literal.md).</span></span></li><li><span data-ttu-id="d8115-124">Wyrażenie osadzone formularza `<%=` `elementExp` `%>` .</span><span class="sxs-lookup"><span data-stu-id="d8115-124">Embedded expression of the form `<%=` `elementExp` `%>`.</span></span> <span data-ttu-id="d8115-125">`elementExp`Zwraca jedną z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="d8115-125">The `elementExp` returns one of the following:</span></span><br /><br /> <ul><li><span data-ttu-id="d8115-126">Obiekt <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="d8115-126">An <xref:System.Xml.Linq.XElement> object.</span></span></li><li><span data-ttu-id="d8115-127">Kolekcja zawierająca jeden <xref:System.Xml.Linq.XElement> obiekt i dowolną liczbę <xref:System.Xml.Linq.XProcessingInstruction> <xref:System.Xml.Linq.XComment> obiektów i.</span><span class="sxs-lookup"><span data-stu-id="d8115-127">A collection that contains one <xref:System.Xml.Linq.XElement> object and any number of <xref:System.Xml.Linq.XProcessingInstruction> and <xref:System.Xml.Linq.XComment> objects.</span></span></li></ul></li></ul><br /> <span data-ttu-id="d8115-128">Aby uzyskać więcej informacji, zobacz [Embedded Expressions in XML](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="d8115-128">For more information, see [Embedded Expressions in XML](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="d8115-129">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d8115-129">Return Value</span></span>  
 <span data-ttu-id="d8115-130">Obiekt <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="d8115-130">An <xref:System.Xml.Linq.XDocument> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8115-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d8115-131">Remarks</span></span>  
 <span data-ttu-id="d8115-132">Literał dokumentu XML jest identyfikowany przez deklarację XML na początku literału.</span><span class="sxs-lookup"><span data-stu-id="d8115-132">An XML document literal is identified by the XML declaration at the start of the literal.</span></span> <span data-ttu-id="d8115-133">Chociaż każdy literał dokumentu XML musi mieć dokładnie jeden główny element XML, może zawierać dowolną liczbę instrukcji przetwarzania XML i komentarzy XML.</span><span class="sxs-lookup"><span data-stu-id="d8115-133">Although each XML document literal must have exactly one root XML element, it can have any number of XML processing instructions and XML comments.</span></span>  
  
 <span data-ttu-id="d8115-134">Literał dokumentu XML nie może występować w elemencie XML.</span><span class="sxs-lookup"><span data-stu-id="d8115-134">An XML document literal cannot appear in an XML element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d8115-135">Literał XML może obejmować wiele wierszy bez używania znaków kontynuacji wiersza.</span><span class="sxs-lookup"><span data-stu-id="d8115-135">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="d8115-136">Dzięki temu można skopiować zawartość z dokumentu XML i wkleić ją bezpośrednio do programu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d8115-136">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="d8115-137">Kompilator Visual Basic konwertuje literał dokumentu XML na wywołania <xref:System.Xml.Linq.XDocument.%23ctor%2A> <xref:System.Xml.Linq.XDeclaration.%23ctor%2A> konstruktorów i.</span><span class="sxs-lookup"><span data-stu-id="d8115-137">The Visual Basic compiler converts the XML document literal into calls to the <xref:System.Xml.Linq.XDocument.%23ctor%2A> and <xref:System.Xml.Linq.XDeclaration.%23ctor%2A> constructors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8115-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8115-138">Example</span></span>  
 <span data-ttu-id="d8115-139">Poniższy przykład tworzy dokument XML, który ma deklarację XML, instrukcję przetwarzania, komentarz i element, który zawiera inny element.</span><span class="sxs-lookup"><span data-stu-id="d8115-139">The following example creates an XML document that has an XML declaration, a processing instruction, a comment, and an element that contains another element.</span></span>  
  
 [!code-vb[VbXMLSamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="d8115-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8115-140">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- <xref:System.Xml.Linq.XProcessingInstruction>
- <xref:System.Xml.Linq.XComment>
- <xref:System.Xml.Linq.XDocument>
- [<span data-ttu-id="d8115-141">Literał instrukcji przetwarzającej kod XML</span><span class="sxs-lookup"><span data-stu-id="d8115-141">XML Processing Instruction Literal</span></span>](xml-processing-instruction-literal.md)
- [<span data-ttu-id="d8115-142">Literał komentarza XML</span><span class="sxs-lookup"><span data-stu-id="d8115-142">XML Comment Literal</span></span>](xml-comment-literal.md)
- [<span data-ttu-id="d8115-143">Literał elementu XML</span><span class="sxs-lookup"><span data-stu-id="d8115-143">XML Element Literal</span></span>](xml-element-literal.md)
- [<span data-ttu-id="d8115-144">Literały XML</span><span class="sxs-lookup"><span data-stu-id="d8115-144">XML Literals</span></span>](index.md)
- [<span data-ttu-id="d8115-145">Tworzenie XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d8115-145">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="d8115-146">Wyrażenia osadzone w XML</span><span class="sxs-lookup"><span data-stu-id="d8115-146">Embedded Expressions in XML</span></span>](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md)
