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
ms.openlocfilehash: 60c354215c627683fd6c69d9ca66fc115c26ccda
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="xml-comment-literal-visual-basic"></a><span data-ttu-id="4a734-102">Literał komentarza XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4a734-102">XML Comment Literal (Visual Basic)</span></span>
<span data-ttu-id="4a734-103">Literał reprezentujący <xref:System.Xml.Linq.XComment> obiektu.</span><span class="sxs-lookup"><span data-stu-id="4a734-103">A literal representing an <xref:System.Xml.Linq.XComment> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a734-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4a734-104">Syntax</span></span>  
  
```xml  
<!-- content -->  
```  
  
## <a name="parts"></a><span data-ttu-id="4a734-105">Części</span><span class="sxs-lookup"><span data-stu-id="4a734-105">Parts</span></span>  
  
|<span data-ttu-id="4a734-106">Termin</span><span class="sxs-lookup"><span data-stu-id="4a734-106">Term</span></span>|<span data-ttu-id="4a734-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="4a734-107">Definition</span></span>|  
|---|---|  
|`<!--`|<span data-ttu-id="4a734-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="4a734-108">Required.</span></span> <span data-ttu-id="4a734-109">Oznacza początek komentarza XML.</span><span class="sxs-lookup"><span data-stu-id="4a734-109">Denotes the start of the XML comment.</span></span>|  
|`content`|<span data-ttu-id="4a734-110">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="4a734-110">Required.</span></span> <span data-ttu-id="4a734-111">Tekst wyświetlany w komentarzu XML.</span><span class="sxs-lookup"><span data-stu-id="4a734-111">Text to appear in the XML comment.</span></span> <span data-ttu-id="4a734-112">Nie może zawierać szereg dwa łączniki (-) lub kończyć się łącznikiem sąsiadujące tagu zamykającego.</span><span class="sxs-lookup"><span data-stu-id="4a734-112">Cannot contain a series of two hyphens (--) or end with a hyphen adjacent to the closing tag.</span></span>|  
|`-->`|<span data-ttu-id="4a734-113">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="4a734-113">Required.</span></span> <span data-ttu-id="4a734-114">Oznacza koniec komentarza XML.</span><span class="sxs-lookup"><span data-stu-id="4a734-114">Denotes the end of the XML comment.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="4a734-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4a734-115">Return Value</span></span>  
 <span data-ttu-id="4a734-116"><xref:System.Xml.Linq.XComment> Obiektu.</span><span class="sxs-lookup"><span data-stu-id="4a734-116">An <xref:System.Xml.Linq.XComment> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a734-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4a734-117">Remarks</span></span>  
 <span data-ttu-id="4a734-118">Literały komentarza XML nie zawierają zawartości dokumentu; zawierają informacje o dokumentu.</span><span class="sxs-lookup"><span data-stu-id="4a734-118">XML comment literals do not contain document content; they contain information about the document.</span></span> <span data-ttu-id="4a734-119">W sekcji komentarza XML kończy sekwencji "-->".</span><span class="sxs-lookup"><span data-stu-id="4a734-119">The XML comment section ends with the sequence "-->".</span></span> <span data-ttu-id="4a734-120">Oznacza to następujące kwestie:</span><span class="sxs-lookup"><span data-stu-id="4a734-120">This implies the following points:</span></span>  
  
-   <span data-ttu-id="4a734-121">Nie można użyć wyrażenia osadzonego w komentarzu XML literału, ponieważ ogranicznika wyrażenia osadzonego to prawidłowa zawartość komentarza XML.</span><span class="sxs-lookup"><span data-stu-id="4a734-121">You cannot use an embedded expression in an XML comment literal because the embedded expression delimiters are valid XML comment content.</span></span>  
  
-   <span data-ttu-id="4a734-122">Sekcje komentarza XML nie mogą być zagnieżdżone, ponieważ `content` nie może zawierać wartości "-->".</span><span class="sxs-lookup"><span data-stu-id="4a734-122">XML comment sections cannot be nested, because `content` cannot contain the value "-->".</span></span>  
  
 <span data-ttu-id="4a734-123">Literał komentarza XML można przypisać do zmiennej lub można objąć literał elementu XML.</span><span class="sxs-lookup"><span data-stu-id="4a734-123">You can assign an XML comment literal to a variable, or you can include it in an XML element literal.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4a734-124">Literał XML może obejmować wiele wierszy bez użycia znaki kontynuacji wiersza.</span><span class="sxs-lookup"><span data-stu-id="4a734-124">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="4a734-125">Ta funkcja umożliwia kopiowanie zawartości z dokumentu XML i wklej go bezpośrednio w programie Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4a734-125">This feature enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="4a734-126">Kompilator Visual Basic konwertuje literał komentarza XML na wywołanie <xref:System.Xml.Linq.XComment.%23ctor%2A> konstruktora.</span><span class="sxs-lookup"><span data-stu-id="4a734-126">The Visual Basic compiler converts the XML comment literal to a call to the <xref:System.Xml.Linq.XComment.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a734-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="4a734-127">Example</span></span>  
 <span data-ttu-id="4a734-128">Poniższy przykład tworzy komentarz XML, który zawiera tekst "Jest komentarz".</span><span class="sxs-lookup"><span data-stu-id="4a734-128">The following example creates an XML comment that contains the text "This is a comment".</span></span>  
  
 [!code-vb[VbXMLSamples#9](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-comment-literal_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="4a734-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4a734-129">See Also</span></span>  
 <xref:System.Xml.Linq.XComment>  
 [<span data-ttu-id="4a734-130">Literał elementu XML</span><span class="sxs-lookup"><span data-stu-id="4a734-130">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [<span data-ttu-id="4a734-131">Literały XML</span><span class="sxs-lookup"><span data-stu-id="4a734-131">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="4a734-132">Tworzenie XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4a734-132">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
