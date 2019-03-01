---
title: Literał komentarza XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralComment
helpviewer_keywords:
- comment literal [Visual Basic]
- XML comments, adding [Visual Basic]
- XML comment literal [Visual Basic]
- XML literals [Visual Basic], comment
ms.assetid: 634c1cee-5e01-48d0-88d7-2dd55e4a9e52
ms.openlocfilehash: 1f8526c4b67b7d975b11f6ef5dada2b45bb6b1df
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56964188"
---
# <a name="xml-comment-literal-visual-basic"></a><span data-ttu-id="aaf28-102">Literał komentarza XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aaf28-102">XML Comment Literal (Visual Basic)</span></span>
<span data-ttu-id="aaf28-103">Literał reprezentujący <xref:System.Xml.Linq.XComment> obiektu.</span><span class="sxs-lookup"><span data-stu-id="aaf28-103">A literal representing an <xref:System.Xml.Linq.XComment> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aaf28-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="aaf28-104">Syntax</span></span>  
  
```xml  
<!-- content -->  
```  
  
## <a name="parts"></a><span data-ttu-id="aaf28-105">Części</span><span class="sxs-lookup"><span data-stu-id="aaf28-105">Parts</span></span>  
  
|<span data-ttu-id="aaf28-106">Termin</span><span class="sxs-lookup"><span data-stu-id="aaf28-106">Term</span></span>|<span data-ttu-id="aaf28-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="aaf28-107">Definition</span></span>|  
|---|---|  
|`<!--`|<span data-ttu-id="aaf28-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="aaf28-108">Required.</span></span> <span data-ttu-id="aaf28-109">Oznacza początek komentarza XML.</span><span class="sxs-lookup"><span data-stu-id="aaf28-109">Denotes the start of the XML comment.</span></span>|  
|`content`|<span data-ttu-id="aaf28-110">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="aaf28-110">Required.</span></span> <span data-ttu-id="aaf28-111">Tekst wyświetlany w komentarzu XML.</span><span class="sxs-lookup"><span data-stu-id="aaf28-111">Text to appear in the XML comment.</span></span> <span data-ttu-id="aaf28-112">Nie może zawierać szereg dwa łączniki (-) ani kończyć się łącznikiem przylegające do tagu zamykającego.</span><span class="sxs-lookup"><span data-stu-id="aaf28-112">Cannot contain a series of two hyphens (--) or end with a hyphen adjacent to the closing tag.</span></span>|  
|`-->`|<span data-ttu-id="aaf28-113">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="aaf28-113">Required.</span></span> <span data-ttu-id="aaf28-114">Oznacza koniec komentarza XML.</span><span class="sxs-lookup"><span data-stu-id="aaf28-114">Denotes the end of the XML comment.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="aaf28-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="aaf28-115">Return Value</span></span>  
 <span data-ttu-id="aaf28-116"><xref:System.Xml.Linq.XComment> Obiektu.</span><span class="sxs-lookup"><span data-stu-id="aaf28-116">An <xref:System.Xml.Linq.XComment> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aaf28-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="aaf28-117">Remarks</span></span>  
 <span data-ttu-id="aaf28-118">Literały komentarza XML nie zawierają treści dokumentu; zawierają informacje o tym dokumencie.</span><span class="sxs-lookup"><span data-stu-id="aaf28-118">XML comment literals do not contain document content; they contain information about the document.</span></span> <span data-ttu-id="aaf28-119">Sekcja komentarz XML kończy się za pomocą sekwencji "-->".</span><span class="sxs-lookup"><span data-stu-id="aaf28-119">The XML comment section ends with the sequence "-->".</span></span> <span data-ttu-id="aaf28-120">Oznacza to następujące kwestie:</span><span class="sxs-lookup"><span data-stu-id="aaf28-120">This implies the following points:</span></span>  
  
-   <span data-ttu-id="aaf28-121">Nie można użyć wyrażenia osadzone w komentarzu XML literału, ponieważ ograniczniki osadzone wyrażenia są prawidłowa zawartość komentarza XML.</span><span class="sxs-lookup"><span data-stu-id="aaf28-121">You cannot use an embedded expression in an XML comment literal because the embedded expression delimiters are valid XML comment content.</span></span>  
  
-   <span data-ttu-id="aaf28-122">Sekcje komentarza XML nie mogą być zagnieżdżone, ponieważ `content` nie może zawierać wartość "-->".</span><span class="sxs-lookup"><span data-stu-id="aaf28-122">XML comment sections cannot be nested, because `content` cannot contain the value "-->".</span></span>  
  
 <span data-ttu-id="aaf28-123">Literał komentarza XML można przypisać do zmiennej lub literał elementu XML można dołączyć go.</span><span class="sxs-lookup"><span data-stu-id="aaf28-123">You can assign an XML comment literal to a variable, or you can include it in an XML element literal.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aaf28-124">Literał XML może obejmować wiele wierszy, bez używania znaków kontynuacji wiersza.</span><span class="sxs-lookup"><span data-stu-id="aaf28-124">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="aaf28-125">Ta funkcja pozwala na kopiowanie zawartości z dokumentu XML i wklej go bezpośrednio w programie Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="aaf28-125">This feature enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="aaf28-126">Kompilator Visual Basic konwertuje literał komentarza XML do wywołania <xref:System.Xml.Linq.XComment.%23ctor%2A> konstruktora.</span><span class="sxs-lookup"><span data-stu-id="aaf28-126">The Visual Basic compiler converts the XML comment literal to a call to the <xref:System.Xml.Linq.XComment.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aaf28-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="aaf28-127">Example</span></span>  
 <span data-ttu-id="aaf28-128">Poniższy przykład tworzy zawierający tekst komentarza XML "To jest komentarz".</span><span class="sxs-lookup"><span data-stu-id="aaf28-128">The following example creates an XML comment that contains the text "This is a comment".</span></span>  
  
 [!code-vb[VbXMLSamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="aaf28-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aaf28-129">See also</span></span>
- <xref:System.Xml.Linq.XComment>
- [<span data-ttu-id="aaf28-130">Literał elementu XML</span><span class="sxs-lookup"><span data-stu-id="aaf28-130">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="aaf28-131">Literały XML</span><span class="sxs-lookup"><span data-stu-id="aaf28-131">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="aaf28-132">Tworzenie XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="aaf28-132">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
