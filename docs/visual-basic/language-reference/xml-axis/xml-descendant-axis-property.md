---
title: Właściwości osi elementu podrzędnego XML
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyDescendantsAxis
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML descendant axis property [Visual Basic]
- descendant axis property [Visual Basic]
- XML axis [Visual Basic], descendant
- XML [Visual Basic], accessing
ms.assetid: a178f85b-5d54-438f-8479-40b62af6fe76
ms.openlocfilehash: b2bf524214fa8ecca215d50c198b23d127e3b400
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349447"
---
# <a name="xml-descendant-axis-property-visual-basic"></a><span data-ttu-id="fd2d9-102">Właściwości osi elementu podrzędnego XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fd2d9-102">XML Descendant Axis Property (Visual Basic)</span></span>

<span data-ttu-id="fd2d9-103">Zapewnia dostęp do elementów podrzędnych następujących: obiektu <xref:System.Xml.Linq.XElement>, obiektu <xref:System.Xml.Linq.XDocument>, kolekcji obiektów <xref:System.Xml.Linq.XElement> lub kolekcji obiektów <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="fd2d9-103">Provides access to the descendants of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>

## <a name="syntax"></a><span data-ttu-id="fd2d9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fd2d9-104">Syntax</span></span>

```vb
object...<descendant>
```

## <a name="parts"></a><span data-ttu-id="fd2d9-105">Części</span><span class="sxs-lookup"><span data-stu-id="fd2d9-105">Parts</span></span>

<span data-ttu-id="fd2d9-106">Wymagane `object`.</span><span class="sxs-lookup"><span data-stu-id="fd2d9-106">`object` Required.</span></span> <span data-ttu-id="fd2d9-107">Obiekt <xref:System.Xml.Linq.XElement>, obiekt <xref:System.Xml.Linq.XDocument>, kolekcja obiektów <xref:System.Xml.Linq.XElement> lub kolekcja obiektów <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="fd2d9-107">An <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>

<span data-ttu-id="fd2d9-108">Wymagane `...<`.</span><span class="sxs-lookup"><span data-stu-id="fd2d9-108">`...<` Required.</span></span> <span data-ttu-id="fd2d9-109">Wskazuje początek właściwości osi elementu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="fd2d9-109">Denotes the start of a descendant axis property.</span></span>

<span data-ttu-id="fd2d9-110">Wymagane `descendant`.</span><span class="sxs-lookup"><span data-stu-id="fd2d9-110">`descendant` Required.</span></span> <span data-ttu-id="fd2d9-111">Nazwa węzłów podrzędnych, do których można uzyskać dostęp, w postaci [`prefix:]name`.</span><span class="sxs-lookup"><span data-stu-id="fd2d9-111">Name of the descendant nodes to access, of the form [`prefix:]name`.</span></span>

|<span data-ttu-id="fd2d9-112">Części</span><span class="sxs-lookup"><span data-stu-id="fd2d9-112">Part</span></span>|<span data-ttu-id="fd2d9-113">Opis</span><span class="sxs-lookup"><span data-stu-id="fd2d9-113">Description</span></span>|
|----------|-----------------|
|`prefix`|<span data-ttu-id="fd2d9-114">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="fd2d9-114">Optional.</span></span> <span data-ttu-id="fd2d9-115">Prefiks przestrzeni nazw XML dla węzła podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="fd2d9-115">XML namespace prefix for the descendant node.</span></span> <span data-ttu-id="fd2d9-116">Musi to być globalna przestrzeń nazw XML, która jest definiowana przy użyciu instrukcji `Imports`.</span><span class="sxs-lookup"><span data-stu-id="fd2d9-116">Must be a global XML namespace that is defined by using an `Imports` statement.</span></span>|
|`name`|<span data-ttu-id="fd2d9-117">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="fd2d9-117">Required.</span></span> <span data-ttu-id="fd2d9-118">Nazwa lokalna węzła podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="fd2d9-118">Local name of the descendant node.</span></span> <span data-ttu-id="fd2d9-119">Zobacz [nazwy zadeklarowanych elementów i atrybutów XML](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="fd2d9-119">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|

<span data-ttu-id="fd2d9-120">Wymagane `>`.</span><span class="sxs-lookup"><span data-stu-id="fd2d9-120">`>` Required.</span></span> <span data-ttu-id="fd2d9-121">Oznacza koniec właściwości osi elementu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="fd2d9-121">Denotes the end of a descendant axis property.</span></span>

## <a name="return-value"></a><span data-ttu-id="fd2d9-122">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="fd2d9-122">Return Value</span></span>

<span data-ttu-id="fd2d9-123">Kolekcja obiektów <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="fd2d9-123">A collection of <xref:System.Xml.Linq.XElement> objects.</span></span>

## <a name="remarks"></a><span data-ttu-id="fd2d9-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fd2d9-124">Remarks</span></span>

<span data-ttu-id="fd2d9-125">Aby uzyskać dostęp do węzłów podrzędnych według nazwy z obiektu <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument> lub z kolekcji obiektów <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument>, można użyć właściwości osi elementu podrzędnego XML.</span><span class="sxs-lookup"><span data-stu-id="fd2d9-125">You can use an XML descendant axis property to access descendant nodes by name from an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object, or from a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="fd2d9-126">Użyj właściwości `Value` XML, aby uzyskać dostęp do wartości pierwszego węzła podrzędnego w zwróconej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="fd2d9-126">Use the XML `Value` property to access the value of the first descendant node in the returned collection.</span></span> <span data-ttu-id="fd2d9-127">Aby uzyskać więcej informacji, zobacz [Właściwość wartości XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="fd2d9-127">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>

<span data-ttu-id="fd2d9-128">Kompilator Visual Basic konwertuje właściwości osi elementu podrzędnego na wywołania metody <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span><span class="sxs-lookup"><span data-stu-id="fd2d9-128">The Visual Basic compiler converts descendant axis properties into calls to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method.</span></span>

## <a name="xml-namespaces"></a><span data-ttu-id="fd2d9-129">Przestrzenie nazw XML</span><span class="sxs-lookup"><span data-stu-id="fd2d9-129">XML Namespaces</span></span>

<span data-ttu-id="fd2d9-130">Nazwa we właściwości osi zależnej może używać tylko przestrzeni nazw XML zadeklarowanych globalnie za pomocą instrukcji `Imports`.</span><span class="sxs-lookup"><span data-stu-id="fd2d9-130">The name in a descendant axis property can use only XML namespaces declared globally with the `Imports` statement.</span></span> <span data-ttu-id="fd2d9-131">Nie można używać przestrzeni nazw XML zadeklarowanych lokalnie w literałach elementu XML.</span><span class="sxs-lookup"><span data-stu-id="fd2d9-131">It cannot use XML namespaces declared locally within XML element literals.</span></span> <span data-ttu-id="fd2d9-132">Aby uzyskać więcej informacji, zobacz [Imports — Instrukcja (przestrzeń nazw XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="fd2d9-132">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>

## <a name="example"></a><span data-ttu-id="fd2d9-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="fd2d9-133">Example</span></span>

<span data-ttu-id="fd2d9-134">Poniższy przykład pokazuje, jak uzyskać dostęp do wartości pierwszego węzła podrzędnego o nazwie `name` i wartości wszystkich węzłów podrzędnych o nazwie `phone` z obiektu `contacts`.</span><span class="sxs-lookup"><span data-stu-id="fd2d9-134">The following example shows how to access the value of the first descendant node named `name` and the values of all descendant nodes named `phone` from the `contacts` object.</span></span>

[!code-vb[VbXMLSamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#25)]

<span data-ttu-id="fd2d9-135">Ten kod wyświetla następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="fd2d9-135">This code displays the following text:</span></span>

`Name: Patrick Hines`

`Home Phone = 206-555-0144`

## <a name="example"></a><span data-ttu-id="fd2d9-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="fd2d9-136">Example</span></span>

<span data-ttu-id="fd2d9-137">Poniższy przykład deklaruje `ns` jako prefiks przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="fd2d9-137">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="fd2d9-138">Następnie używa prefiksu przestrzeni nazw w celu utworzenia literału XML i uzyskania dostępu do wartości pierwszego węzła podrzędnego przy użyciu kwalifikowanej nazwy `ns:name`.</span><span class="sxs-lookup"><span data-stu-id="fd2d9-138">It then uses the prefix of the namespace to create an XML literal and access the value of the first child node with the qualified name `ns:name`.</span></span>

[!code-vb[VbXMLSamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples12.vb#26)]

<span data-ttu-id="fd2d9-139">Ten kod wyświetla następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="fd2d9-139">This code displays the following text:</span></span>

`Name: Patrick Hines`

## <a name="see-also"></a><span data-ttu-id="fd2d9-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fd2d9-140">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="fd2d9-141">Właściwości osi XML</span><span class="sxs-lookup"><span data-stu-id="fd2d9-141">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)
- [<span data-ttu-id="fd2d9-142">Literały XML</span><span class="sxs-lookup"><span data-stu-id="fd2d9-142">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="fd2d9-143">Tworzenie kodu XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fd2d9-143">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="fd2d9-144">Nazwy deklarowanych elementów i atrybutów XML</span><span class="sxs-lookup"><span data-stu-id="fd2d9-144">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
