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
ms.openlocfilehash: 91369392f33f2a86a7a4cb5ffb3faa668c113348
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965411"
---
# <a name="xml-comment-literal-visual-basic"></a><span data-ttu-id="e037e-102">Literał komentarza XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e037e-102">XML Comment Literal (Visual Basic)</span></span>
<span data-ttu-id="e037e-103">Literał reprezentujący <xref:System.Xml.Linq.XComment> obiekt.</span><span class="sxs-lookup"><span data-stu-id="e037e-103">A literal representing an <xref:System.Xml.Linq.XComment> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e037e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e037e-104">Syntax</span></span>  
  
```xml  
<!-- content -->  
```  
  
## <a name="parts"></a><span data-ttu-id="e037e-105">Części</span><span class="sxs-lookup"><span data-stu-id="e037e-105">Parts</span></span>  
  
|<span data-ttu-id="e037e-106">Termin</span><span class="sxs-lookup"><span data-stu-id="e037e-106">Term</span></span>|<span data-ttu-id="e037e-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="e037e-107">Definition</span></span>|  
|---|---|  
|`<!--`|<span data-ttu-id="e037e-108">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="e037e-108">Required.</span></span> <span data-ttu-id="e037e-109">Oznacza początek komentarza XML.</span><span class="sxs-lookup"><span data-stu-id="e037e-109">Denotes the start of the XML comment.</span></span>|  
|`content`|<span data-ttu-id="e037e-110">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="e037e-110">Required.</span></span> <span data-ttu-id="e037e-111">Tekst, który ma być wyświetlany w komentarzu XML.</span><span class="sxs-lookup"><span data-stu-id="e037e-111">Text to appear in the XML comment.</span></span> <span data-ttu-id="e037e-112">Nie może zawierać serii dwóch łączników (--) ani kończyć się łącznikiem przylegającym do taga zamykającego.</span><span class="sxs-lookup"><span data-stu-id="e037e-112">Cannot contain a series of two hyphens (--) or end with a hyphen adjacent to the closing tag.</span></span>|  
|`-->`|<span data-ttu-id="e037e-113">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="e037e-113">Required.</span></span> <span data-ttu-id="e037e-114">Oznacza koniec komentarza XML.</span><span class="sxs-lookup"><span data-stu-id="e037e-114">Denotes the end of the XML comment.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="e037e-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e037e-115">Return Value</span></span>  
 <span data-ttu-id="e037e-116"><xref:System.Xml.Linq.XComment> Obiekt.</span><span class="sxs-lookup"><span data-stu-id="e037e-116">An <xref:System.Xml.Linq.XComment> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e037e-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e037e-117">Remarks</span></span>  
 <span data-ttu-id="e037e-118">Literały komentarza XML nie zawierają zawartości dokumentu; zawierają one informacje o dokumencie.</span><span class="sxs-lookup"><span data-stu-id="e037e-118">XML comment literals do not contain document content; they contain information about the document.</span></span> <span data-ttu-id="e037e-119">Sekcja komentarza XML jest zakończona sekwencją "-->".</span><span class="sxs-lookup"><span data-stu-id="e037e-119">The XML comment section ends with the sequence "-->".</span></span> <span data-ttu-id="e037e-120">Oznacza to następujące kwestie:</span><span class="sxs-lookup"><span data-stu-id="e037e-120">This implies the following points:</span></span>  
  
- <span data-ttu-id="e037e-121">Nie można użyć wyrażenia osadzonego w literale komentarza XML, ponieważ ogranicznik wyrażenia osadzonego są prawidłową zawartością komentarza XML.</span><span class="sxs-lookup"><span data-stu-id="e037e-121">You cannot use an embedded expression in an XML comment literal because the embedded expression delimiters are valid XML comment content.</span></span>  
  
- <span data-ttu-id="e037e-122">Sekcje komentarza XML nie mogą być zagnieżdżane, ponieważ `content` nie mogą zawierać wartości "-->".</span><span class="sxs-lookup"><span data-stu-id="e037e-122">XML comment sections cannot be nested, because `content` cannot contain the value "-->".</span></span>  
  
 <span data-ttu-id="e037e-123">Do zmiennej można przypisać literał komentarza XML lub dodać go do literału elementu XML.</span><span class="sxs-lookup"><span data-stu-id="e037e-123">You can assign an XML comment literal to a variable, or you can include it in an XML element literal.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e037e-124">Literał XML może obejmować wiele wierszy bez używania znaków kontynuacji wiersza.</span><span class="sxs-lookup"><span data-stu-id="e037e-124">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="e037e-125">Ta funkcja umożliwia skopiowanie zawartości z dokumentu XML i wklejenie jej bezpośrednio do programu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e037e-125">This feature enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="e037e-126">Kompilator Visual Basic konwertuje literał komentarza XML na wywołanie <xref:System.Xml.Linq.XComment.%23ctor%2A> konstruktora.</span><span class="sxs-lookup"><span data-stu-id="e037e-126">The Visual Basic compiler converts the XML comment literal to a call to the <xref:System.Xml.Linq.XComment.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e037e-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="e037e-127">Example</span></span>  
 <span data-ttu-id="e037e-128">Poniższy przykład tworzy komentarz XML zawierający tekst "to jest komentarz".</span><span class="sxs-lookup"><span data-stu-id="e037e-128">The following example creates an XML comment that contains the text "This is a comment".</span></span>  
  
 [!code-vb[VbXMLSamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="e037e-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e037e-129">See also</span></span>

- <xref:System.Xml.Linq.XComment>
- [<span data-ttu-id="e037e-130">Literał elementu XML</span><span class="sxs-lookup"><span data-stu-id="e037e-130">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="e037e-131">Literały XML</span><span class="sxs-lookup"><span data-stu-id="e037e-131">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="e037e-132">Tworzenie kodu XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e037e-132">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
