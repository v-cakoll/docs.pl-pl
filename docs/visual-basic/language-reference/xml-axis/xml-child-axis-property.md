---
title: Właściwości osi elementu podrzędnego XML
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyChildAxis
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 89a59d00-985e-4f5c-b59f-29b47bad11cb
ms.openlocfilehash: 728c17cd2ed8661e0a5f1f2b8e929059713a1edf
ms.sourcegitcommit: 8c99457955fc31785b36b3330c4ab6ce7984a7ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/29/2019
ms.locfileid: "75545120"
---
# <a name="xml-child-axis-property-visual-basic"></a><span data-ttu-id="f9140-102">Właściwości osi elementu podrzędnego XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f9140-102">XML Child Axis Property (Visual Basic)</span></span>
<span data-ttu-id="f9140-103">Zapewnia dostęp do elementów podrzędnych jednego z następujących: obiektu <xref:System.Xml.Linq.XElement>, obiektu <xref:System.Xml.Linq.XDocument>, kolekcji obiektów <xref:System.Xml.Linq.XElement> lub kolekcji obiektów <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="f9140-103">Provides access to the children of one of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9140-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f9140-104">Syntax</span></span>  
  
```vb  
object.<child>  
```  
  
## <a name="parts"></a><span data-ttu-id="f9140-105">Części</span><span class="sxs-lookup"><span data-stu-id="f9140-105">Parts</span></span>  
  
|<span data-ttu-id="f9140-106">Termin</span><span class="sxs-lookup"><span data-stu-id="f9140-106">Term</span></span>|<span data-ttu-id="f9140-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="f9140-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="f9140-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="f9140-108">Required.</span></span> <span data-ttu-id="f9140-109">Obiekt <xref:System.Xml.Linq.XElement>, obiekt <xref:System.Xml.Linq.XDocument>, kolekcja obiektów <xref:System.Xml.Linq.XElement> lub kolekcja obiektów <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="f9140-109">An <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>|  
|<span data-ttu-id="f9140-110">.<</span><span class="sxs-lookup"><span data-stu-id="f9140-110">.<</span></span>|<span data-ttu-id="f9140-111">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="f9140-111">Required.</span></span> <span data-ttu-id="f9140-112">Wskazuje początek właściwości osi podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="f9140-112">Denotes the start of a child axis property.</span></span>|  
|`child`|<span data-ttu-id="f9140-113">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="f9140-113">Required.</span></span> <span data-ttu-id="f9140-114">Nazwa węzłów podrzędnych do uzyskania dostępu w formularzu `[prefix:]name`.</span><span class="sxs-lookup"><span data-stu-id="f9140-114">Name of the child nodes to access, of the form `[prefix:]name`.</span></span><br /><br /> <span data-ttu-id="f9140-115">-   `Prefix` — opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="f9140-115">-   `Prefix` - Optional.</span></span> <span data-ttu-id="f9140-116">Prefiks przestrzeni nazw XML dla węzła podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="f9140-116">XML namespace prefix for the child node.</span></span> <span data-ttu-id="f9140-117">Musi to być globalna przestrzeń nazw XML zdefiniowana za pomocą instrukcji `Imports`.</span><span class="sxs-lookup"><span data-stu-id="f9140-117">Must be a global XML namespace defined with an `Imports` statement.</span></span><br /><span data-ttu-id="f9140-118">-   `Name` — wymagane.</span><span class="sxs-lookup"><span data-stu-id="f9140-118">-   `Name` - Required.</span></span> <span data-ttu-id="f9140-119">Nazwa lokalnego węzła podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="f9140-119">Local child node name.</span></span> <span data-ttu-id="f9140-120">Zobacz [nazwy zadeklarowanych elementów i atrybutów XML](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="f9140-120">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
|>|<span data-ttu-id="f9140-121">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="f9140-121">Required.</span></span> <span data-ttu-id="f9140-122">Oznacza koniec właściwości osi podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="f9140-122">Denotes the end of a child axis property.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="f9140-123">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="f9140-123">Return Value</span></span>  
 <span data-ttu-id="f9140-124">Kolekcja obiektów <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="f9140-124">A collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f9140-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f9140-125">Remarks</span></span>  
 <span data-ttu-id="f9140-126">Można użyć właściwości osi elementu podrzędnego XML, aby uzyskać dostęp do węzłów podrzędnych według nazwy z obiektu <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument> lub z kolekcji obiektów <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="f9140-126">You can use an XML child axis property to access child nodes by name from an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object, or from a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="f9140-127">Użyj właściwości `Value` XML, aby uzyskać dostęp do wartości pierwszego węzła podrzędnego w zwróconej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="f9140-127">Use the XML `Value` property to access the value of the first child node in the returned collection.</span></span> <span data-ttu-id="f9140-128">Aby uzyskać więcej informacji, zobacz [Właściwość wartości XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="f9140-128">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>  
  
 <span data-ttu-id="f9140-129">Kompilator Visual Basic konwertuje właściwości osi podrzędnej na wywołania metody <xref:System.Xml.Linq.XContainer.Elements%2A>.</span><span class="sxs-lookup"><span data-stu-id="f9140-129">The Visual Basic compiler converts child axis properties to calls to the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="f9140-130">Przestrzenie nazw XML</span><span class="sxs-lookup"><span data-stu-id="f9140-130">XML Namespaces</span></span>  
 <span data-ttu-id="f9140-131">Nazwa we właściwości osi podrzędnej może używać tylko prefiksów przestrzeni nazw XML zadeklarowanych globalnie z instrukcją `Imports`.</span><span class="sxs-lookup"><span data-stu-id="f9140-131">The name in a child axis property can use only XML namespace prefixes declared globally with the `Imports` statement.</span></span> <span data-ttu-id="f9140-132">Nie może używać prefiksów przestrzeni nazw XML zadeklarowanych lokalnie w literałach elementu XML.</span><span class="sxs-lookup"><span data-stu-id="f9140-132">It cannot use XML namespace prefixes declared locally within XML element literals.</span></span> <span data-ttu-id="f9140-133">Aby uzyskać więcej informacji, zobacz [Imports — Instrukcja (przestrzeń nazw XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="f9140-133">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9140-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9140-134">Example</span></span>  
 <span data-ttu-id="f9140-135">Poniższy przykład pokazuje, jak uzyskać dostęp do węzłów podrzędnych o nazwie `phone` z obiektu `contact`.</span><span class="sxs-lookup"><span data-stu-id="f9140-135">The following example shows how to access the child nodes named `phone` from the `contact` object.</span></span>  
  
 [!code-vb[VbXMLSamples#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#17)]  
  
 <span data-ttu-id="f9140-136">Ten kod wyświetla następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="f9140-136">This code displays the following text:</span></span>  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="f9140-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9140-137">Example</span></span>  
 <span data-ttu-id="f9140-138">Poniższy przykład pokazuje, jak uzyskać dostęp do węzłów podrzędnych o nazwie `phone` z kolekcji zwróconej przez właściwość oś podrzędną `contact` obiektu `contacts`.</span><span class="sxs-lookup"><span data-stu-id="f9140-138">The following example shows how to access the child nodes named `phone` from the collection returned by the `contact` child axis property of the `contacts` object.</span></span>  
  
 [!code-vb[VbXMLSamples#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#18)]  
  
 <span data-ttu-id="f9140-139">Ten kod wyświetla następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="f9140-139">This code displays the following text:</span></span>  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="f9140-140">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9140-140">Example</span></span>  
 <span data-ttu-id="f9140-141">Poniższy przykład deklaruje `ns` jako prefiks przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="f9140-141">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="f9140-142">Następnie używa prefiksu przestrzeni nazw, aby utworzyć literał XML i uzyskać dostęp do pierwszego węzła podrzędnego przy użyciu kwalifikowanej nazwy `ns:name`.</span><span class="sxs-lookup"><span data-stu-id="f9140-142">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name `ns:name`.</span></span>  
  
 [!code-vb[VbXMLSamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples8.vb#19)]  
  
 <span data-ttu-id="f9140-143">Ten kod wyświetla następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="f9140-143">This code displays the following text:</span></span>  
  
 `Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="f9140-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f9140-144">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="f9140-145">Właściwości osi XML</span><span class="sxs-lookup"><span data-stu-id="f9140-145">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)
- [<span data-ttu-id="f9140-146">Literały XML</span><span class="sxs-lookup"><span data-stu-id="f9140-146">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="f9140-147">Tworzenie kodu XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f9140-147">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="f9140-148">Nazwy deklarowanych elementów i atrybutów XML</span><span class="sxs-lookup"><span data-stu-id="f9140-148">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
