---
title: "Literał CDATA XML (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.XmlLiteralCdata
helpviewer_keywords:
- CDATA literal [Visual Basic]
- XML CDATA literal [Visual Basic]
- XML literals [Visual Basic], CDATA
ms.assetid: 9eafb6a4-dd9d-4866-85e8-0654c65abc44
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 906fd2494dd952c08088b9b7e38dba4505780481
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="xml-cdata-literal-visual-basic"></a><span data-ttu-id="52b09-102">Literał CDATA XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="52b09-102">XML CDATA Literal (Visual Basic)</span></span>
<span data-ttu-id="52b09-103">Literał reprezentujący <xref:System.Xml.Linq.XCData> obiektu.</span><span class="sxs-lookup"><span data-stu-id="52b09-103">A literal representing an <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52b09-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="52b09-104">Syntax</span></span>  
  
```xml  
<![CDATA[content]]>  
```  
  
## <a name="parts"></a><span data-ttu-id="52b09-105">Części</span><span class="sxs-lookup"><span data-stu-id="52b09-105">Parts</span></span>  
 `<![CDATA[`  
 <span data-ttu-id="52b09-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="52b09-106">Required.</span></span> <span data-ttu-id="52b09-107">Oznacza początek sekcji XML CDATA.</span><span class="sxs-lookup"><span data-stu-id="52b09-107">Denotes the start of the XML CDATA section.</span></span>  
  
 `content`  
 <span data-ttu-id="52b09-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="52b09-108">Required.</span></span> <span data-ttu-id="52b09-109">Zawartość tekstowa pojawią się w sekcji XML CDATA.</span><span class="sxs-lookup"><span data-stu-id="52b09-109">Text content to appear in the XML CDATA section.</span></span>  
  
 `]]>`  
 <span data-ttu-id="52b09-110">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="52b09-110">Required.</span></span> <span data-ttu-id="52b09-111">Oznacza koniec sekcji.</span><span class="sxs-lookup"><span data-stu-id="52b09-111">Denotes the end of the section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="52b09-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="52b09-112">Return Value</span></span>  
 <span data-ttu-id="52b09-113"><xref:System.Xml.Linq.XCData> Obiektu.</span><span class="sxs-lookup"><span data-stu-id="52b09-113">An <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52b09-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="52b09-114">Remarks</span></span>  
 <span data-ttu-id="52b09-115">Sekcji XML CDATA zawiera pierwotne tekst, który powinny być włączone, lecz nie przeanalizować, XML, który go zawiera.</span><span class="sxs-lookup"><span data-stu-id="52b09-115">XML CDATA sections contain raw text that should be included, but not parsed, with the XML that contains it.</span></span> <span data-ttu-id="52b09-116">Sekcja XML CDATA mogą zawierać dowolny tekst.</span><span class="sxs-lookup"><span data-stu-id="52b09-116">A XML CDATA section can contain any text.</span></span> <span data-ttu-id="52b09-117">W tym zarezerwowanych znaków XML.</span><span class="sxs-lookup"><span data-stu-id="52b09-117">This includes reserved XML characters.</span></span> <span data-ttu-id="52b09-118">W sekcji XML CDATA kończy sekwencja "]] >".</span><span class="sxs-lookup"><span data-stu-id="52b09-118">The XML CDATA section ends with the sequence "]]>".</span></span> <span data-ttu-id="52b09-119">Oznacza to następujące kwestie:</span><span class="sxs-lookup"><span data-stu-id="52b09-119">This implies the following points:</span></span>  
  
-   <span data-ttu-id="52b09-120">Nie można użyć wyrażenia osadzonego w literał CDATA XML, ponieważ prawidłowa zawartość XML CDATA są ograniczniki wyrażenia osadzonego.</span><span class="sxs-lookup"><span data-stu-id="52b09-120">You cannot use an embedded expression in an XML CDATA literal because the embedded expression delimiters are valid XML CDATA content.</span></span>  
  
-   <span data-ttu-id="52b09-121">Nie można zagnieździć sekcji XML CDATA, ponieważ `content` nie może zawierać wartości "]] >".</span><span class="sxs-lookup"><span data-stu-id="52b09-121">XML CDATA sections cannot be nested, because `content` cannot contain the value "]]>".</span></span>  
  
 <span data-ttu-id="52b09-122">Można przypisać literał CDATA XML do zmiennej lub objąć literał elementu XML.</span><span class="sxs-lookup"><span data-stu-id="52b09-122">You can assign an XML CDATA literal to a variable, or include it in an XML element literal.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="52b09-123">Literał XML może obejmować wiele wierszy, ale nie są używane znaki kontynuacji wiersza.</span><span class="sxs-lookup"><span data-stu-id="52b09-123">An XML literal can span multiple lines but does not use line continuation characters.</span></span> <span data-ttu-id="52b09-124">Dzięki temu można kopiować zawartości z dokumentu XML i wklej go bezpośrednio do [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program.</span><span class="sxs-lookup"><span data-stu-id="52b09-124">This enables you to copy content from an XML document and paste it directly into a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program.</span></span>  
  
 <span data-ttu-id="52b09-125">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Kompilatora konwertuje literał CDATA XML do wywołania <xref:System.Xml.Linq.XCData.%23ctor%2A> konstruktora.</span><span class="sxs-lookup"><span data-stu-id="52b09-125">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler converts the XML CDATA literal to a call to the <xref:System.Xml.Linq.XCData.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="52b09-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="52b09-126">Example</span></span>  
 <span data-ttu-id="52b09-127">Poniższy przykład tworzy sekcji CDATA, która zawiera tekst "może zawierać literału \<XML > tagi".</span><span class="sxs-lookup"><span data-stu-id="52b09-127">The following example creates a CDATA section that contains the text "Can contain literal \<XML> tags".</span></span>  
  
 [!code-vb[VbXMLSamples#23](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-cdata-literal_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="52b09-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="52b09-128">See Also</span></span>  
 <xref:System.Xml.Linq.XCData>  
 [<span data-ttu-id="52b09-129">Literał elementu XML</span><span class="sxs-lookup"><span data-stu-id="52b09-129">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [<span data-ttu-id="52b09-130">Literały XML</span><span class="sxs-lookup"><span data-stu-id="52b09-130">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="52b09-131">Tworzenie XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="52b09-131">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
