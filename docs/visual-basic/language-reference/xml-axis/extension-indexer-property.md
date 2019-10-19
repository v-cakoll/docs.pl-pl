---
title: Właściwość indeksatora rozszerzenia (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyExtensionIndexer
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML extension indexer [Visual Basic]
- extension indexer [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: a16a4b13-54be-432c-82b3-a87091464ada
ms.openlocfilehash: 660cebadc78d260350f2849f7f4926f9cef7c8d2
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582183"
---
# <a name="extension-indexer-property-visual-basic"></a><span data-ttu-id="7ebef-102">Właściwość indeksatora rozszerzenia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7ebef-102">Extension Indexer Property (Visual Basic)</span></span>
<span data-ttu-id="7ebef-103">Zapewnia dostęp do poszczególnych elementów w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="7ebef-103">Provides access to individual elements in a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ebef-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7ebef-104">Syntax</span></span>  
  
```vb  
object(index)  
```  
  
## <a name="parts"></a><span data-ttu-id="7ebef-105">Części</span><span class="sxs-lookup"><span data-stu-id="7ebef-105">Parts</span></span>  
  
|<span data-ttu-id="7ebef-106">Termin</span><span class="sxs-lookup"><span data-stu-id="7ebef-106">Term</span></span>|<span data-ttu-id="7ebef-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="7ebef-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="7ebef-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="7ebef-108">Required.</span></span> <span data-ttu-id="7ebef-109">Kolekcja queryable.</span><span class="sxs-lookup"><span data-stu-id="7ebef-109">A queryable collection.</span></span> <span data-ttu-id="7ebef-110">Oznacza to, że kolekcja implementująca <xref:System.Collections.Generic.IEnumerable%601> lub <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="7ebef-110">That is, a collection that implements <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span>|  
|<span data-ttu-id="7ebef-111">(</span><span class="sxs-lookup"><span data-stu-id="7ebef-111">(</span></span>|<span data-ttu-id="7ebef-112">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="7ebef-112">Required.</span></span> <span data-ttu-id="7ebef-113">Wskazuje początek właściwości indeksatora.</span><span class="sxs-lookup"><span data-stu-id="7ebef-113">Denotes the start of the indexer property.</span></span>|  
|`index`|<span data-ttu-id="7ebef-114">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="7ebef-114">Required.</span></span> <span data-ttu-id="7ebef-115">Wyrażenie liczb całkowitych określające pozycję elementu w kolekcji liczony od zera.</span><span class="sxs-lookup"><span data-stu-id="7ebef-115">An integer expression that specifies the zero-based position of an element of the collection.</span></span>|  
|<span data-ttu-id="7ebef-116">)</span><span class="sxs-lookup"><span data-stu-id="7ebef-116">)</span></span>|<span data-ttu-id="7ebef-117">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="7ebef-117">Required.</span></span> <span data-ttu-id="7ebef-118">Oznacza koniec właściwości indeksatora.</span><span class="sxs-lookup"><span data-stu-id="7ebef-118">Denotes the end of the indexer property.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="7ebef-119">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7ebef-119">Return Value</span></span>  
 <span data-ttu-id="7ebef-120">Obiekt z określonej lokalizacji w kolekcji lub `Nothing`, jeśli indeks jest poza zakresem.</span><span class="sxs-lookup"><span data-stu-id="7ebef-120">The object from the specified location in the collection, or `Nothing` if the index is out of range.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7ebef-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7ebef-121">Remarks</span></span>  
 <span data-ttu-id="7ebef-122">Aby uzyskać dostęp do poszczególnych elementów w kolekcji, można użyć właściwości indeksatora rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="7ebef-122">You can use the extension indexer property to access individual elements in a collection.</span></span> <span data-ttu-id="7ebef-123">Ta właściwość indeksatora jest zwykle używana w danych wyjściowych właściwości osi XML.</span><span class="sxs-lookup"><span data-stu-id="7ebef-123">This indexer property is typically used on the output of XML axis properties.</span></span> <span data-ttu-id="7ebef-124">Właściwości osi elementów potomnych XML i XML zwracają kolekcje <xref:System.Xml.Linq.XElement> obiektów lub wartości atrybutu.</span><span class="sxs-lookup"><span data-stu-id="7ebef-124">The XML child and XML descendent axis properties return collections of <xref:System.Xml.Linq.XElement> objects or an attribute value.</span></span>  
  
 <span data-ttu-id="7ebef-125">Kompilator Visual Basic konwertuje właściwości indeksatora rozszerzenia na wywołania metody `ElementAtOrDefault`.</span><span class="sxs-lookup"><span data-stu-id="7ebef-125">The Visual Basic compiler converts extension indexer properties to calls to the `ElementAtOrDefault` method.</span></span> <span data-ttu-id="7ebef-126">W przeciwieństwie do indeksatora tablicy Metoda `ElementAtOrDefault` zwraca `Nothing`, jeśli indeks jest poza zakresem.</span><span class="sxs-lookup"><span data-stu-id="7ebef-126">Unlike an array indexer, the `ElementAtOrDefault` method returns `Nothing` if the index is out of range.</span></span> <span data-ttu-id="7ebef-127">To zachowanie jest przydatne, gdy nie można łatwo określić liczby elementów w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="7ebef-127">This behavior is useful when you cannot easily determine the number of elements in a collection.</span></span>  
  
 <span data-ttu-id="7ebef-128">Ta właściwość indeksatora jest taka sama jak Właściwość rozszerzenia dla kolekcji implementujących <xref:System.Collections.Generic.IEnumerable%601> lub <xref:System.Linq.IQueryable%601>: jest używana tylko wtedy, gdy kolekcja nie ma indeksatora ani właściwości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="7ebef-128">This indexer property is like an extension property for collections that implement <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>: it is used only if the collection does not have an indexer or a default property.</span></span>  
  
 <span data-ttu-id="7ebef-129">Aby uzyskać dostęp do wartości pierwszego elementu w kolekcji obiektów <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XAttribute>, można użyć właściwości XML `Value`.</span><span class="sxs-lookup"><span data-stu-id="7ebef-129">To access the value of the first element in a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, you can use the XML `Value` property.</span></span> <span data-ttu-id="7ebef-130">Aby uzyskać więcej informacji, zobacz [Właściwość wartości XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="7ebef-130">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ebef-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="7ebef-131">Example</span></span>  
 <span data-ttu-id="7ebef-132">Poniższy przykład pokazuje, jak za pomocą indeksatora rozszerzeń uzyskać dostęp do drugiego węzła podrzędnego w kolekcji obiektów <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="7ebef-132">The following example shows how to use the extension indexer to access the second child node in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="7ebef-133">Do kolekcji uzyskuje się dostęp za pomocą Właściwości oś podrzędna, która pobiera wszystkie elementy podrzędne o nazwie `phone` w obiekcie `contact`.</span><span class="sxs-lookup"><span data-stu-id="7ebef-133">The collection is accessed by using the child axis property, which gets all child elements named `phone` in the `contact` object.</span></span>  
  
 [!code-vb[VbXMLSamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#24)]  
  
 <span data-ttu-id="7ebef-134">Ten kod wyświetla następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="7ebef-134">This code displays the following text:</span></span>  
  
 `Second phone number: 425-555-0145`  
  
## <a name="see-also"></a><span data-ttu-id="7ebef-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7ebef-135">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="7ebef-136">Właściwości osi XML</span><span class="sxs-lookup"><span data-stu-id="7ebef-136">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)
- [<span data-ttu-id="7ebef-137">Literały XML</span><span class="sxs-lookup"><span data-stu-id="7ebef-137">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="7ebef-138">Tworzenie kodu XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7ebef-138">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="7ebef-139">Właściwość wartości XML</span><span class="sxs-lookup"><span data-stu-id="7ebef-139">XML Value Property</span></span>](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
