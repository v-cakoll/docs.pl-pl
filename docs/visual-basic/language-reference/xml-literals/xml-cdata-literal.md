---
title: Literał CDATA XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralCdata
helpviewer_keywords:
- CDATA literal [Visual Basic]
- XML CDATA literal [Visual Basic]
- XML literals [Visual Basic], CDATA
ms.assetid: 9eafb6a4-dd9d-4866-85e8-0654c65abc44
ms.openlocfilehash: ee269ca5cf9635fec35165d1ea65d6a6483cadef
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58828605"
---
# <a name="xml-cdata-literal-visual-basic"></a><span data-ttu-id="c24ae-102">Literał CDATA XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c24ae-102">XML CDATA Literal (Visual Basic)</span></span>
<span data-ttu-id="c24ae-103">Literał reprezentujący <xref:System.Xml.Linq.XCData> obiektu.</span><span class="sxs-lookup"><span data-stu-id="c24ae-103">A literal representing an <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c24ae-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c24ae-104">Syntax</span></span>  
  
```xml  
<![CDATA[content]]>  
```  
  
## <a name="parts"></a><span data-ttu-id="c24ae-105">Części</span><span class="sxs-lookup"><span data-stu-id="c24ae-105">Parts</span></span>  
 `<![CDATA[`  
 <span data-ttu-id="c24ae-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="c24ae-106">Required.</span></span> <span data-ttu-id="c24ae-107">Oznacza początek sekcja XML CDATA.</span><span class="sxs-lookup"><span data-stu-id="c24ae-107">Denotes the start of the XML CDATA section.</span></span>  
  
 `content`  
 <span data-ttu-id="c24ae-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="c24ae-108">Required.</span></span> <span data-ttu-id="c24ae-109">Zawartość tekstowa pojawią się w sekcji XML CDATA.</span><span class="sxs-lookup"><span data-stu-id="c24ae-109">Text content to appear in the XML CDATA section.</span></span>  
  
 `]]>`  
 <span data-ttu-id="c24ae-110">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="c24ae-110">Required.</span></span> <span data-ttu-id="c24ae-111">Oznacza koniec sekcji.</span><span class="sxs-lookup"><span data-stu-id="c24ae-111">Denotes the end of the section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c24ae-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c24ae-112">Return Value</span></span>  
 <span data-ttu-id="c24ae-113"><xref:System.Xml.Linq.XCData> Obiektu.</span><span class="sxs-lookup"><span data-stu-id="c24ae-113">An <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c24ae-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c24ae-114">Remarks</span></span>  
 <span data-ttu-id="c24ae-115">Sekcje XML CDATA zawierają nieprzetworzony tekst, które powinny być włączone, lecz nie analizować za pomocą XML, który go zawiera.</span><span class="sxs-lookup"><span data-stu-id="c24ae-115">XML CDATA sections contain raw text that should be included, but not parsed, with the XML that contains it.</span></span> <span data-ttu-id="c24ae-116">Sekcja XML CDATA może zawierać dowolny tekst.</span><span class="sxs-lookup"><span data-stu-id="c24ae-116">A XML CDATA section can contain any text.</span></span> <span data-ttu-id="c24ae-117">Obejmuje to zarezerwowanych znaków XML.</span><span class="sxs-lookup"><span data-stu-id="c24ae-117">This includes reserved XML characters.</span></span> <span data-ttu-id="c24ae-118">Sekcja XML CDATA kończy się wraz z sekwencji "]] >".</span><span class="sxs-lookup"><span data-stu-id="c24ae-118">The XML CDATA section ends with the sequence "]]>".</span></span> <span data-ttu-id="c24ae-119">Oznacza to następujące kwestie:</span><span class="sxs-lookup"><span data-stu-id="c24ae-119">This implies the following points:</span></span>  
  
-   <span data-ttu-id="c24ae-120">Nie można użyć wyrażenia osadzone w literał CDATA XML, ponieważ ograniczniki osadzone wyrażenia są prawidłowa zawartość XML CDATA.</span><span class="sxs-lookup"><span data-stu-id="c24ae-120">You cannot use an embedded expression in an XML CDATA literal because the embedded expression delimiters are valid XML CDATA content.</span></span>  
  
-   <span data-ttu-id="c24ae-121">Nie można zagnieżdżać sekcji XML CDATA, ponieważ `content` nie może zawierać wartość "]] >".</span><span class="sxs-lookup"><span data-stu-id="c24ae-121">XML CDATA sections cannot be nested, because `content` cannot contain the value "]]>".</span></span>  
  
 <span data-ttu-id="c24ae-122">Możesz przypisać literał CDATA XML do zmiennej lub ją dołączyć literał elementu XML.</span><span class="sxs-lookup"><span data-stu-id="c24ae-122">You can assign an XML CDATA literal to a variable, or include it in an XML element literal.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c24ae-123">Literał XML może obejmować wiele wierszy, ale nie mogą używać znaków kontynuacji wiersza.</span><span class="sxs-lookup"><span data-stu-id="c24ae-123">An XML literal can span multiple lines but does not use line continuation characters.</span></span> <span data-ttu-id="c24ae-124">Dzięki temu można skopiować zawartość z dokumentu XML i wklej go bezpośrednio w programie Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c24ae-124">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="c24ae-125">Kompilator Visual Basic konwertuje literał CDATA XML do wywołania <xref:System.Xml.Linq.XCData.%23ctor%2A> konstruktora.</span><span class="sxs-lookup"><span data-stu-id="c24ae-125">The Visual Basic compiler converts the XML CDATA literal to a call to the <xref:System.Xml.Linq.XCData.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c24ae-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="c24ae-126">Example</span></span>  
 <span data-ttu-id="c24ae-127">Poniższy przykład obejmuje tworzenie sekcji CDATA, która zawiera tekst "może zawierać literału \<XML > tagi".</span><span class="sxs-lookup"><span data-stu-id="c24ae-127">The following example creates a CDATA section that contains the text "Can contain literal \<XML> tags".</span></span>  
  
 [!code-vb[VbXMLSamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="c24ae-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c24ae-128">See also</span></span>

- <xref:System.Xml.Linq.XCData>
- [<span data-ttu-id="c24ae-129">Literał elementu XML</span><span class="sxs-lookup"><span data-stu-id="c24ae-129">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="c24ae-130">Literały XML</span><span class="sxs-lookup"><span data-stu-id="c24ae-130">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="c24ae-131">Tworzenie XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c24ae-131">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
