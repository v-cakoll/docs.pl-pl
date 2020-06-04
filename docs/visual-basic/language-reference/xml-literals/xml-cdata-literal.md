---
title: Literał CDATA XML
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralCdata
helpviewer_keywords:
- CDATA literal [Visual Basic]
- XML CDATA literal [Visual Basic]
- XML literals [Visual Basic], CDATA
ms.assetid: 9eafb6a4-dd9d-4866-85e8-0654c65abc44
ms.openlocfilehash: b9cc830d27625f192d8f5e059bd3783d05d8ba3b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400231"
---
# <a name="xml-cdata-literal-visual-basic"></a><span data-ttu-id="24fba-102">Literał CDATA XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="24fba-102">XML CDATA Literal (Visual Basic)</span></span>
<span data-ttu-id="24fba-103">Literał reprezentujący <xref:System.Xml.Linq.XCData> obiekt.</span><span class="sxs-lookup"><span data-stu-id="24fba-103">A literal representing an <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24fba-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="24fba-104">Syntax</span></span>  
  
```xml  
<![CDATA[content]]>  
```  
  
## <a name="parts"></a><span data-ttu-id="24fba-105">Części</span><span class="sxs-lookup"><span data-stu-id="24fba-105">Parts</span></span>  
 `<![CDATA[`  
 <span data-ttu-id="24fba-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="24fba-106">Required.</span></span> <span data-ttu-id="24fba-107">Wskazuje początek sekcji CDATA XML.</span><span class="sxs-lookup"><span data-stu-id="24fba-107">Denotes the start of the XML CDATA section.</span></span>  
  
 `content`  
 <span data-ttu-id="24fba-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="24fba-108">Required.</span></span> <span data-ttu-id="24fba-109">Zawartość tekstowa do wyświetlenia w sekcji CDATA XML.</span><span class="sxs-lookup"><span data-stu-id="24fba-109">Text content to appear in the XML CDATA section.</span></span>  
  
 `]]>`  
 <span data-ttu-id="24fba-110">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="24fba-110">Required.</span></span> <span data-ttu-id="24fba-111">Oznacza koniec sekcji.</span><span class="sxs-lookup"><span data-stu-id="24fba-111">Denotes the end of the section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="24fba-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="24fba-112">Return Value</span></span>  
 <span data-ttu-id="24fba-113">Obiekt <xref:System.Xml.Linq.XCData>.</span><span class="sxs-lookup"><span data-stu-id="24fba-113">An <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24fba-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="24fba-114">Remarks</span></span>  
 <span data-ttu-id="24fba-115">Sekcje CDATA XML zawierają nieprzetworzony tekst, który powinien być uwzględniony, ale nie jest analizowany, z XML, który zawiera.</span><span class="sxs-lookup"><span data-stu-id="24fba-115">XML CDATA sections contain raw text that should be included, but not parsed, with the XML that contains it.</span></span> <span data-ttu-id="24fba-116">Sekcja CDATA XML może zawierać dowolny tekst.</span><span class="sxs-lookup"><span data-stu-id="24fba-116">A XML CDATA section can contain any text.</span></span> <span data-ttu-id="24fba-117">Obejmuje to zastrzeżone znaki XML.</span><span class="sxs-lookup"><span data-stu-id="24fba-117">This includes reserved XML characters.</span></span> <span data-ttu-id="24fba-118">Sekcja CDATA XML zostanie zakończona z sekwencją "]] >".</span><span class="sxs-lookup"><span data-stu-id="24fba-118">The XML CDATA section ends with the sequence "]]>".</span></span> <span data-ttu-id="24fba-119">Oznacza to następujące kwestie:</span><span class="sxs-lookup"><span data-stu-id="24fba-119">This implies the following points:</span></span>  
  
- <span data-ttu-id="24fba-120">Nie można użyć wyrażenia osadzonego w literale CDATA XML, ponieważ ogranicznik wyrażenia osadzonego są prawidłową zawartością elementu XML CDATA.</span><span class="sxs-lookup"><span data-stu-id="24fba-120">You cannot use an embedded expression in an XML CDATA literal because the embedded expression delimiters are valid XML CDATA content.</span></span>  
  
- <span data-ttu-id="24fba-121">Sekcje CDATA XML nie mogą być zagnieżdżane, ponieważ `content` nie mogą zawierać wartości "]] >".</span><span class="sxs-lookup"><span data-stu-id="24fba-121">XML CDATA sections cannot be nested, because `content` cannot contain the value "]]>".</span></span>  
  
 <span data-ttu-id="24fba-122">Do zmiennej można przypisać literał XML CDATA lub dodać go do literału elementu XML.</span><span class="sxs-lookup"><span data-stu-id="24fba-122">You can assign an XML CDATA literal to a variable, or include it in an XML element literal.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="24fba-123">Literał XML może obejmować wiele wierszy, ale nie używa znaków kontynuacji wiersza.</span><span class="sxs-lookup"><span data-stu-id="24fba-123">An XML literal can span multiple lines but does not use line continuation characters.</span></span> <span data-ttu-id="24fba-124">Dzięki temu można skopiować zawartość z dokumentu XML i wkleić ją bezpośrednio do programu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="24fba-124">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="24fba-125">Kompilator Visual Basic konwertuje literał XML CDATA na wywołanie <xref:System.Xml.Linq.XCData.%23ctor%2A> konstruktora.</span><span class="sxs-lookup"><span data-stu-id="24fba-125">The Visual Basic compiler converts the XML CDATA literal to a call to the <xref:System.Xml.Linq.XCData.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24fba-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="24fba-126">Example</span></span>  
 <span data-ttu-id="24fba-127">Poniższy przykład tworzy sekcję CDATA, która zawiera tekst "może zawierać Tagi literału \<XML> ".</span><span class="sxs-lookup"><span data-stu-id="24fba-127">The following example creates a CDATA section that contains the text "Can contain literal \<XML> tags".</span></span>  
  
 [!code-vb[VbXMLSamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="24fba-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="24fba-128">See also</span></span>

- <xref:System.Xml.Linq.XCData>
- [<span data-ttu-id="24fba-129">Literał elementu XML</span><span class="sxs-lookup"><span data-stu-id="24fba-129">XML Element Literal</span></span>](xml-element-literal.md)
- [<span data-ttu-id="24fba-130">Literały XML</span><span class="sxs-lookup"><span data-stu-id="24fba-130">XML Literals</span></span>](index.md)
- [<span data-ttu-id="24fba-131">Tworzenie XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="24fba-131">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
