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
ms.openlocfilehash: 248f3cf31f686de3af2ea06012aa4a6d4f3f29fc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942918"
---
# <a name="xml-cdata-literal-visual-basic"></a><span data-ttu-id="dcd7a-102">Literał CDATA XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dcd7a-102">XML CDATA Literal (Visual Basic)</span></span>
<span data-ttu-id="dcd7a-103">Literał reprezentujący <xref:System.Xml.Linq.XCData> obiekt.</span><span class="sxs-lookup"><span data-stu-id="dcd7a-103">A literal representing an <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcd7a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dcd7a-104">Syntax</span></span>  
  
```xml  
<![CDATA[content]]>  
```  
  
## <a name="parts"></a><span data-ttu-id="dcd7a-105">Części</span><span class="sxs-lookup"><span data-stu-id="dcd7a-105">Parts</span></span>  
 `<![CDATA[`  
 <span data-ttu-id="dcd7a-106">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="dcd7a-106">Required.</span></span> <span data-ttu-id="dcd7a-107">Wskazuje początek sekcji CDATA XML.</span><span class="sxs-lookup"><span data-stu-id="dcd7a-107">Denotes the start of the XML CDATA section.</span></span>  
  
 `content`  
 <span data-ttu-id="dcd7a-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="dcd7a-108">Required.</span></span> <span data-ttu-id="dcd7a-109">Zawartość tekstowa do wyświetlenia w sekcji CDATA XML.</span><span class="sxs-lookup"><span data-stu-id="dcd7a-109">Text content to appear in the XML CDATA section.</span></span>  
  
 `]]>`  
 <span data-ttu-id="dcd7a-110">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="dcd7a-110">Required.</span></span> <span data-ttu-id="dcd7a-111">Oznacza koniec sekcji.</span><span class="sxs-lookup"><span data-stu-id="dcd7a-111">Denotes the end of the section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dcd7a-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="dcd7a-112">Return Value</span></span>  
 <span data-ttu-id="dcd7a-113"><xref:System.Xml.Linq.XCData> Obiekt.</span><span class="sxs-lookup"><span data-stu-id="dcd7a-113">An <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dcd7a-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dcd7a-114">Remarks</span></span>  
 <span data-ttu-id="dcd7a-115">Sekcje CDATA XML zawierają nieprzetworzony tekst, który powinien być uwzględniony, ale nie jest analizowany, z XML, który zawiera.</span><span class="sxs-lookup"><span data-stu-id="dcd7a-115">XML CDATA sections contain raw text that should be included, but not parsed, with the XML that contains it.</span></span> <span data-ttu-id="dcd7a-116">Sekcja CDATA XML może zawierać dowolny tekst.</span><span class="sxs-lookup"><span data-stu-id="dcd7a-116">A XML CDATA section can contain any text.</span></span> <span data-ttu-id="dcd7a-117">Obejmuje to zastrzeżone znaki XML.</span><span class="sxs-lookup"><span data-stu-id="dcd7a-117">This includes reserved XML characters.</span></span> <span data-ttu-id="dcd7a-118">Sekcja CDATA XML zostanie zakończona z sekwencją "]] >".</span><span class="sxs-lookup"><span data-stu-id="dcd7a-118">The XML CDATA section ends with the sequence "]]>".</span></span> <span data-ttu-id="dcd7a-119">Oznacza to następujące kwestie:</span><span class="sxs-lookup"><span data-stu-id="dcd7a-119">This implies the following points:</span></span>  
  
- <span data-ttu-id="dcd7a-120">Nie można użyć wyrażenia osadzonego w literale CDATA XML, ponieważ ogranicznik wyrażenia osadzonego są prawidłową zawartością elementu XML CDATA.</span><span class="sxs-lookup"><span data-stu-id="dcd7a-120">You cannot use an embedded expression in an XML CDATA literal because the embedded expression delimiters are valid XML CDATA content.</span></span>  
  
- <span data-ttu-id="dcd7a-121">Sekcje CDATA XML nie mogą być zagnieżdżane `content` , ponieważ nie mogą zawierać wartości "]] >".</span><span class="sxs-lookup"><span data-stu-id="dcd7a-121">XML CDATA sections cannot be nested, because `content` cannot contain the value "]]>".</span></span>  
  
 <span data-ttu-id="dcd7a-122">Do zmiennej można przypisać literał XML CDATA lub dodać go do literału elementu XML.</span><span class="sxs-lookup"><span data-stu-id="dcd7a-122">You can assign an XML CDATA literal to a variable, or include it in an XML element literal.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dcd7a-123">Literał XML może obejmować wiele wierszy, ale nie używa znaków kontynuacji wiersza.</span><span class="sxs-lookup"><span data-stu-id="dcd7a-123">An XML literal can span multiple lines but does not use line continuation characters.</span></span> <span data-ttu-id="dcd7a-124">Dzięki temu można skopiować zawartość z dokumentu XML i wkleić ją bezpośrednio do programu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="dcd7a-124">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="dcd7a-125">Kompilator Visual Basic konwertuje literał XML CDATA na wywołanie <xref:System.Xml.Linq.XCData.%23ctor%2A> konstruktora.</span><span class="sxs-lookup"><span data-stu-id="dcd7a-125">The Visual Basic compiler converts the XML CDATA literal to a call to the <xref:System.Xml.Linq.XCData.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dcd7a-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="dcd7a-126">Example</span></span>  
 <span data-ttu-id="dcd7a-127">Poniższy przykład tworzy sekcję CDATA, która zawiera tekst "może zawierać literały \<XML >.</span><span class="sxs-lookup"><span data-stu-id="dcd7a-127">The following example creates a CDATA section that contains the text "Can contain literal \<XML> tags".</span></span>  
  
 [!code-vb[VbXMLSamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="dcd7a-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dcd7a-128">See also</span></span>

- <xref:System.Xml.Linq.XCData>
- [<span data-ttu-id="dcd7a-129">Literał elementu XML</span><span class="sxs-lookup"><span data-stu-id="dcd7a-129">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="dcd7a-130">Literały XML</span><span class="sxs-lookup"><span data-stu-id="dcd7a-130">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="dcd7a-131">Tworzenie kodu XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dcd7a-131">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
