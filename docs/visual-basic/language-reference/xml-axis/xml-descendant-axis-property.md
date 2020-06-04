---
title: Właściwości osi obiektu podrzędnego XML
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
ms.openlocfilehash: 52544619171dbc7034baeb5feb61395d81096387
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400256"
---
# <a name="xml-descendant-axis-property-visual-basic"></a><span data-ttu-id="fd244-102">Właściwości osi elementu podrzędnego XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fd244-102">XML Descendant Axis Property (Visual Basic)</span></span>

<span data-ttu-id="fd244-103">Zapewnia dostęp do elementów podrzędnych następujących obiektów: <xref:System.Xml.Linq.XElement> obiektu, <xref:System.Xml.Linq.XDocument> obiektu, kolekcji <xref:System.Xml.Linq.XElement> obiektów lub kolekcji <xref:System.Xml.Linq.XDocument> obiektów.</span><span class="sxs-lookup"><span data-stu-id="fd244-103">Provides access to the descendants of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>

## <a name="syntax"></a><span data-ttu-id="fd244-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fd244-104">Syntax</span></span>

```vb
object...<descendant>
```

## <a name="parts"></a><span data-ttu-id="fd244-105">Części</span><span class="sxs-lookup"><span data-stu-id="fd244-105">Parts</span></span>

<span data-ttu-id="fd244-106">`object`Wymagane.</span><span class="sxs-lookup"><span data-stu-id="fd244-106">`object` Required.</span></span> <span data-ttu-id="fd244-107"><xref:System.Xml.Linq.XElement>Obiekt, <xref:System.Xml.Linq.XDocument> obiekt, kolekcja <xref:System.Xml.Linq.XElement> obiektów lub kolekcja <xref:System.Xml.Linq.XDocument> obiektów.</span><span class="sxs-lookup"><span data-stu-id="fd244-107">An <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>

<span data-ttu-id="fd244-108">`...<`Wymagane.</span><span class="sxs-lookup"><span data-stu-id="fd244-108">`...<` Required.</span></span> <span data-ttu-id="fd244-109">Wskazuje początek właściwości osi elementu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="fd244-109">Denotes the start of a descendant axis property.</span></span>

<span data-ttu-id="fd244-110">`descendant`Wymagane.</span><span class="sxs-lookup"><span data-stu-id="fd244-110">`descendant` Required.</span></span> <span data-ttu-id="fd244-111">Nazwa węzłów podrzędnych do uzyskania dostępu do formularza [ `prefix:]name` .</span><span class="sxs-lookup"><span data-stu-id="fd244-111">Name of the descendant nodes to access, of the form [`prefix:]name`.</span></span>

|<span data-ttu-id="fd244-112">Część</span><span class="sxs-lookup"><span data-stu-id="fd244-112">Part</span></span>|<span data-ttu-id="fd244-113">Opis</span><span class="sxs-lookup"><span data-stu-id="fd244-113">Description</span></span>|
|----------|-----------------|
|`prefix`|<span data-ttu-id="fd244-114">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="fd244-114">Optional.</span></span> <span data-ttu-id="fd244-115">Prefiks przestrzeni nazw XML dla węzła podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="fd244-115">XML namespace prefix for the descendant node.</span></span> <span data-ttu-id="fd244-116">Musi to być globalna przestrzeń nazw XML, która jest definiowana przy użyciu `Imports` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="fd244-116">Must be a global XML namespace that is defined by using an `Imports` statement.</span></span>|
|`name`|<span data-ttu-id="fd244-117">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="fd244-117">Required.</span></span> <span data-ttu-id="fd244-118">Nazwa lokalna węzła podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="fd244-118">Local name of the descendant node.</span></span> <span data-ttu-id="fd244-119">Zobacz [nazwy zadeklarowanych elementów i atrybutów XML](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="fd244-119">See [Names of Declared XML Elements and Attributes](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|

<span data-ttu-id="fd244-120">`>`Wymagane.</span><span class="sxs-lookup"><span data-stu-id="fd244-120">`>` Required.</span></span> <span data-ttu-id="fd244-121">Oznacza koniec właściwości osi elementu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="fd244-121">Denotes the end of a descendant axis property.</span></span>

## <a name="return-value"></a><span data-ttu-id="fd244-122">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="fd244-122">Return Value</span></span>

<span data-ttu-id="fd244-123">Kolekcja obiektów <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="fd244-123">A collection of <xref:System.Xml.Linq.XElement> objects.</span></span>

## <a name="remarks"></a><span data-ttu-id="fd244-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fd244-124">Remarks</span></span>

<span data-ttu-id="fd244-125">Aby uzyskać dostęp do węzłów podrzędnych według nazwy <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument> z kolekcji <xref:System.Xml.Linq.XElement> lub obiektów, można użyć właściwości osi elementu podrzędnego XML <xref:System.Xml.Linq.XDocument> .</span><span class="sxs-lookup"><span data-stu-id="fd244-125">You can use an XML descendant axis property to access descendant nodes by name from an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object, or from a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="fd244-126">Użyj właściwości XML, `Value` Aby uzyskać dostęp do wartości pierwszego węzła podrzędnego w zwróconej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="fd244-126">Use the XML `Value` property to access the value of the first descendant node in the returned collection.</span></span> <span data-ttu-id="fd244-127">Aby uzyskać więcej informacji, zobacz [Właściwość wartości XML](xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="fd244-127">For more information, see [XML Value Property](xml-value-property.md).</span></span>

<span data-ttu-id="fd244-128">Kompilator Visual Basic konwertuje właściwości osi elementu podrzędnego na wywołania <xref:System.Xml.Linq.XContainer.Descendants%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="fd244-128">The Visual Basic compiler converts descendant axis properties into calls to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method.</span></span>

## <a name="xml-namespaces"></a><span data-ttu-id="fd244-129">Przestrzenie nazw XML</span><span class="sxs-lookup"><span data-stu-id="fd244-129">XML Namespaces</span></span>

<span data-ttu-id="fd244-130">Nazwa we właściwości osi podrzędnej może używać tylko przestrzeni nazw XML zadeklarowanych globalnie z `Imports` instrukcją.</span><span class="sxs-lookup"><span data-stu-id="fd244-130">The name in a descendant axis property can use only XML namespaces declared globally with the `Imports` statement.</span></span> <span data-ttu-id="fd244-131">Nie można używać przestrzeni nazw XML zadeklarowanych lokalnie w literałach elementu XML.</span><span class="sxs-lookup"><span data-stu-id="fd244-131">It cannot use XML namespaces declared locally within XML element literals.</span></span> <span data-ttu-id="fd244-132">Aby uzyskać więcej informacji, zobacz [Imports — Instrukcja (przestrzeń nazw XML)](../statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="fd244-132">For more information, see [Imports Statement (XML Namespace)](../statements/imports-statement-xml-namespace.md).</span></span>

## <a name="example"></a><span data-ttu-id="fd244-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="fd244-133">Example</span></span>

<span data-ttu-id="fd244-134">Poniższy przykład pokazuje, jak uzyskać dostęp do wartości pierwszego węzła podrzędnego o nazwie `name` i wartości wszystkich węzłów podrzędnych o nazwie `phone` z `contacts` obiektu.</span><span class="sxs-lookup"><span data-stu-id="fd244-134">The following example shows how to access the value of the first descendant node named `name` and the values of all descendant nodes named `phone` from the `contacts` object.</span></span>

[!code-vb[VbXMLSamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#25)]

<span data-ttu-id="fd244-135">Ten kod wyświetla następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="fd244-135">This code displays the following text:</span></span>

`Name: Patrick Hines`

`Home Phone = 206-555-0144`

## <a name="example"></a><span data-ttu-id="fd244-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="fd244-136">Example</span></span>

<span data-ttu-id="fd244-137">Poniższy przykład deklaruje `ns` jako prefiks przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="fd244-137">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="fd244-138">Następnie używa prefiksu przestrzeni nazw w celu utworzenia literału XML i uzyskania dostępu do wartości pierwszego węzła podrzędnego przy użyciu kwalifikowanej nazwy `ns:name` .</span><span class="sxs-lookup"><span data-stu-id="fd244-138">It then uses the prefix of the namespace to create an XML literal and access the value of the first child node with the qualified name `ns:name`.</span></span>

[!code-vb[VbXMLSamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples12.vb#26)]

<span data-ttu-id="fd244-139">Ten kod wyświetla następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="fd244-139">This code displays the following text:</span></span>

`Name: Patrick Hines`

## <a name="see-also"></a><span data-ttu-id="fd244-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fd244-140">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="fd244-141">Właściwości osi XML</span><span class="sxs-lookup"><span data-stu-id="fd244-141">XML Axis Properties</span></span>](index.md)
- [<span data-ttu-id="fd244-142">Literały XML</span><span class="sxs-lookup"><span data-stu-id="fd244-142">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="fd244-143">Tworzenie XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fd244-143">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="fd244-144">Nazwy deklarowanych elementów XML oraz atrybuty</span><span class="sxs-lookup"><span data-stu-id="fd244-144">Names of Declared XML Elements and Attributes</span></span>](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
