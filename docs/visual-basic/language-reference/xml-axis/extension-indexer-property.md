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
ms.openlocfilehash: ab9eacc3fb3796139d8ed8382146a4a6c2b28a97
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43483713"
---
# <a name="extension-indexer-property-visual-basic"></a><span data-ttu-id="61b4a-102">Właściwość indeksatora rozszerzenia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="61b4a-102">Extension Indexer Property (Visual Basic)</span></span>
<span data-ttu-id="61b4a-103">Zapewnia dostęp do poszczególnych elementów w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="61b4a-103">Provides access to individual elements in a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61b4a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="61b4a-104">Syntax</span></span>  
  
```  
object(index)  
```  
  
## <a name="parts"></a><span data-ttu-id="61b4a-105">Części</span><span class="sxs-lookup"><span data-stu-id="61b4a-105">Parts</span></span>  
  
|<span data-ttu-id="61b4a-106">Termin</span><span class="sxs-lookup"><span data-stu-id="61b4a-106">Term</span></span>|<span data-ttu-id="61b4a-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="61b4a-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="61b4a-108">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="61b4a-108">Required.</span></span> <span data-ttu-id="61b4a-109">Kolekcja z obsługą zapytań.</span><span class="sxs-lookup"><span data-stu-id="61b4a-109">A queryable collection.</span></span> <span data-ttu-id="61b4a-110">Oznacza to, kolekcję, która implementuje <xref:System.Collections.Generic.IEnumerable%601> lub <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="61b4a-110">That is, a collection that implements <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span>|  
|<span data-ttu-id="61b4a-111">(</span><span class="sxs-lookup"><span data-stu-id="61b4a-111">(</span></span>|<span data-ttu-id="61b4a-112">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="61b4a-112">Required.</span></span> <span data-ttu-id="61b4a-113">Oznacza początek właściwość indeksatora.</span><span class="sxs-lookup"><span data-stu-id="61b4a-113">Denotes the start of the indexer property.</span></span>|  
|`index`|<span data-ttu-id="61b4a-114">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="61b4a-114">Required.</span></span> <span data-ttu-id="61b4a-115">Wyrażenie liczba całkowita, określająca liczona od zera pozycja elementu kolekcji.</span><span class="sxs-lookup"><span data-stu-id="61b4a-115">An integer expression that specifies the zero-based position of an element of the collection.</span></span>|  
|<span data-ttu-id="61b4a-116">)</span><span class="sxs-lookup"><span data-stu-id="61b4a-116">)</span></span>|<span data-ttu-id="61b4a-117">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="61b4a-117">Required.</span></span> <span data-ttu-id="61b4a-118">Oznacza koniec właściwości indeksatora.</span><span class="sxs-lookup"><span data-stu-id="61b4a-118">Denotes the end of the indexer property.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="61b4a-119">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="61b4a-119">Return Value</span></span>  
 <span data-ttu-id="61b4a-120">Obiekt z określonej lokalizacji w kolekcji lub `Nothing` Jeśli indeks jest poza zakresem.</span><span class="sxs-lookup"><span data-stu-id="61b4a-120">The object from the specified location in the collection, or `Nothing` if the index is out of range.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="61b4a-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="61b4a-121">Remarks</span></span>  
 <span data-ttu-id="61b4a-122">Właściwość indeksatora rozszerzenia umożliwia dostęp do poszczególnych elementów w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="61b4a-122">You can use the extension indexer property to access individual elements in a collection.</span></span> <span data-ttu-id="61b4a-123">Ta właściwość indeksatora zwykle jest używana dla danych wyjściowych właściwości osi XML.</span><span class="sxs-lookup"><span data-stu-id="61b4a-123">This indexer property is typically used on the output of XML axis properties.</span></span> <span data-ttu-id="61b4a-124">Elementu podrzędnego XML i właściwości osi descendant XML zwracają kolekcje <xref:System.Xml.Linq.XElement> obiektów lub wartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="61b4a-124">The XML child and XML descendent axis properties return collections of <xref:System.Xml.Linq.XElement> objects or an attribute value.</span></span>  
  
 <span data-ttu-id="61b4a-125">Kompilator Visual Basic konwertuje właściwości indeksatora rozszerzenia wywołania `ElementAtOrDefault` metody.</span><span class="sxs-lookup"><span data-stu-id="61b4a-125">The Visual Basic compiler converts extension indexer properties to calls to the `ElementAtOrDefault` method.</span></span> <span data-ttu-id="61b4a-126">W przeciwieństwie do indeksatora tablicy `ElementAtOrDefault` metoda zwraca `Nothing` Jeśli indeks jest poza zakresem.</span><span class="sxs-lookup"><span data-stu-id="61b4a-126">Unlike an array indexer, the `ElementAtOrDefault` method returns `Nothing` if the index is out of range.</span></span> <span data-ttu-id="61b4a-127">To zachowanie jest przydatne, gdy nie można określić, że liczba elementów w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="61b4a-127">This behavior is useful when you cannot easily determine the number of elements in a collection.</span></span>  
  
 <span data-ttu-id="61b4a-128">Ta właściwość indeksatora przypomina właściwości rozszerzenia dla kolekcji, które implementują <xref:System.Collections.Generic.IEnumerable%601> lub <xref:System.Linq.IQueryable%601>: jest używany tylko wtedy, gdy kolekcja nie ma indeksatora lub domyślnej właściwości.</span><span class="sxs-lookup"><span data-stu-id="61b4a-128">This indexer property is like an extension property for collections that implement <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>: it is used only if the collection does not have an indexer or a default property.</span></span>  
  
 <span data-ttu-id="61b4a-129">Aby uzyskać dostęp do wartości pierwszego elementu w kolekcji <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XAttribute> obiektów, można użyć pliku XML `Value` właściwości.</span><span class="sxs-lookup"><span data-stu-id="61b4a-129">To access the value of the first element in a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, you can use the XML `Value` property.</span></span> <span data-ttu-id="61b4a-130">Aby uzyskać więcej informacji, zobacz [właściwość wartości XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="61b4a-130">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="61b4a-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="61b4a-131">Example</span></span>  
 <span data-ttu-id="61b4a-132">Poniższy przykład pokazuje, jak używać indeksator rozszerzeń dostępu do drugiego węzła podrzędnego w zbiorze <xref:System.Xml.Linq.XElement> obiektów.</span><span class="sxs-lookup"><span data-stu-id="61b4a-132">The following example shows how to use the extension indexer to access the second child node in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="61b4a-133">Kolekcja jest dostępne przy użyciu właściwości osi elementu podrzędnego, który pobiera wszystkie elementy podrzędne, o nazwie `phone` w `contact` obiektu.</span><span class="sxs-lookup"><span data-stu-id="61b4a-133">The collection is accessed by using the child axis property, which gets all child elements named `phone` in the `contact` object.</span></span>  
  
 [!code-vb[VbXMLSamples#24](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/extension-indexer-property_1.vb)]  
  
 <span data-ttu-id="61b4a-134">Ten kod wyświetla następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="61b4a-134">This code displays the following text:</span></span>  
  
 `Second phone number: 425-555-0145`  
  
## <a name="see-also"></a><span data-ttu-id="61b4a-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="61b4a-135">See Also</span></span>  
 <xref:System.Xml.Linq.XElement>  
 [<span data-ttu-id="61b4a-136">Właściwości osi XML</span><span class="sxs-lookup"><span data-stu-id="61b4a-136">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)  
 [<span data-ttu-id="61b4a-137">Literały XML</span><span class="sxs-lookup"><span data-stu-id="61b4a-137">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="61b4a-138">Tworzenie XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="61b4a-138">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="61b4a-139">Właściwość wartości XML</span><span class="sxs-lookup"><span data-stu-id="61b4a-139">XML Value Property</span></span>](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
