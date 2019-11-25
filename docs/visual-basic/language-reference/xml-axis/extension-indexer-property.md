---
title: Właściwość indeksatora rozszerzenia
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyExtensionIndexer
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML extension indexer [Visual Basic]
- extension indexer [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: a16a4b13-54be-432c-82b3-a87091464ada
ms.openlocfilehash: 5f91dc8a6b1a0d82daa4891cf826c16e2716839f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352699"
---
# <a name="extension-indexer-property-visual-basic"></a><span data-ttu-id="eb509-102">Właściwość indeksatora rozszerzenia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eb509-102">Extension Indexer Property (Visual Basic)</span></span>
<span data-ttu-id="eb509-103">Provides access to individual elements in a collection.</span><span class="sxs-lookup"><span data-stu-id="eb509-103">Provides access to individual elements in a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb509-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="eb509-104">Syntax</span></span>  
  
```vb  
object(index)  
```  
  
## <a name="parts"></a><span data-ttu-id="eb509-105">Części</span><span class="sxs-lookup"><span data-stu-id="eb509-105">Parts</span></span>  
  
|<span data-ttu-id="eb509-106">Termin</span><span class="sxs-lookup"><span data-stu-id="eb509-106">Term</span></span>|<span data-ttu-id="eb509-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="eb509-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="eb509-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="eb509-108">Required.</span></span> <span data-ttu-id="eb509-109">A queryable collection.</span><span class="sxs-lookup"><span data-stu-id="eb509-109">A queryable collection.</span></span> <span data-ttu-id="eb509-110">That is, a collection that implements <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="eb509-110">That is, a collection that implements <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span>|  
|<span data-ttu-id="eb509-111">(</span><span class="sxs-lookup"><span data-stu-id="eb509-111">(</span></span>|<span data-ttu-id="eb509-112">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="eb509-112">Required.</span></span> <span data-ttu-id="eb509-113">Denotes the start of the indexer property.</span><span class="sxs-lookup"><span data-stu-id="eb509-113">Denotes the start of the indexer property.</span></span>|  
|`index`|<span data-ttu-id="eb509-114">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="eb509-114">Required.</span></span> <span data-ttu-id="eb509-115">An integer expression that specifies the zero-based position of an element of the collection.</span><span class="sxs-lookup"><span data-stu-id="eb509-115">An integer expression that specifies the zero-based position of an element of the collection.</span></span>|  
|<span data-ttu-id="eb509-116">)</span><span class="sxs-lookup"><span data-stu-id="eb509-116">)</span></span>|<span data-ttu-id="eb509-117">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="eb509-117">Required.</span></span> <span data-ttu-id="eb509-118">Denotes the end of the indexer property.</span><span class="sxs-lookup"><span data-stu-id="eb509-118">Denotes the end of the indexer property.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="eb509-119">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="eb509-119">Return Value</span></span>  
 <span data-ttu-id="eb509-120">The object from the specified location in the collection, or `Nothing` if the index is out of range.</span><span class="sxs-lookup"><span data-stu-id="eb509-120">The object from the specified location in the collection, or `Nothing` if the index is out of range.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eb509-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="eb509-121">Remarks</span></span>  
 <span data-ttu-id="eb509-122">You can use the extension indexer property to access individual elements in a collection.</span><span class="sxs-lookup"><span data-stu-id="eb509-122">You can use the extension indexer property to access individual elements in a collection.</span></span> <span data-ttu-id="eb509-123">This indexer property is typically used on the output of XML axis properties.</span><span class="sxs-lookup"><span data-stu-id="eb509-123">This indexer property is typically used on the output of XML axis properties.</span></span> <span data-ttu-id="eb509-124">The XML child and XML descendent axis properties return collections of <xref:System.Xml.Linq.XElement> objects or an attribute value.</span><span class="sxs-lookup"><span data-stu-id="eb509-124">The XML child and XML descendent axis properties return collections of <xref:System.Xml.Linq.XElement> objects or an attribute value.</span></span>  
  
 <span data-ttu-id="eb509-125">The Visual Basic compiler converts extension indexer properties to calls to the `ElementAtOrDefault` method.</span><span class="sxs-lookup"><span data-stu-id="eb509-125">The Visual Basic compiler converts extension indexer properties to calls to the `ElementAtOrDefault` method.</span></span> <span data-ttu-id="eb509-126">Unlike an array indexer, the `ElementAtOrDefault` method returns `Nothing` if the index is out of range.</span><span class="sxs-lookup"><span data-stu-id="eb509-126">Unlike an array indexer, the `ElementAtOrDefault` method returns `Nothing` if the index is out of range.</span></span> <span data-ttu-id="eb509-127">This behavior is useful when you cannot easily determine the number of elements in a collection.</span><span class="sxs-lookup"><span data-stu-id="eb509-127">This behavior is useful when you cannot easily determine the number of elements in a collection.</span></span>  
  
 <span data-ttu-id="eb509-128">This indexer property is like an extension property for collections that implement <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>: it is used only if the collection does not have an indexer or a default property.</span><span class="sxs-lookup"><span data-stu-id="eb509-128">This indexer property is like an extension property for collections that implement <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>: it is used only if the collection does not have an indexer or a default property.</span></span>  
  
 <span data-ttu-id="eb509-129">To access the value of the first element in a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, you can use the XML `Value` property.</span><span class="sxs-lookup"><span data-stu-id="eb509-129">To access the value of the first element in a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, you can use the XML `Value` property.</span></span> <span data-ttu-id="eb509-130">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="eb509-130">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb509-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="eb509-131">Example</span></span>  
 <span data-ttu-id="eb509-132">The following example shows how to use the extension indexer to access the second child node in a collection of <xref:System.Xml.Linq.XElement> objects.</span><span class="sxs-lookup"><span data-stu-id="eb509-132">The following example shows how to use the extension indexer to access the second child node in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="eb509-133">The collection is accessed by using the child axis property, which gets all child elements named `phone` in the `contact` object.</span><span class="sxs-lookup"><span data-stu-id="eb509-133">The collection is accessed by using the child axis property, which gets all child elements named `phone` in the `contact` object.</span></span>  
  
 [!code-vb[VbXMLSamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#24)]  
  
 <span data-ttu-id="eb509-134">This code displays the following text:</span><span class="sxs-lookup"><span data-stu-id="eb509-134">This code displays the following text:</span></span>  
  
 `Second phone number: 425-555-0145`  
  
## <a name="see-also"></a><span data-ttu-id="eb509-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eb509-135">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="eb509-136">Właściwości osi XML</span><span class="sxs-lookup"><span data-stu-id="eb509-136">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)
- [<span data-ttu-id="eb509-137">Literały XML</span><span class="sxs-lookup"><span data-stu-id="eb509-137">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="eb509-138">Creating XML in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="eb509-138">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="eb509-139">Właściwość wartości XML</span><span class="sxs-lookup"><span data-stu-id="eb509-139">XML Value Property</span></span>](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
