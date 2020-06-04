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
ms.openlocfilehash: 90dc22d12be5566fa1ee40f6b0e48eff8088e67b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400269"
---
# <a name="xml-child-axis-property-visual-basic"></a><span data-ttu-id="2d766-102">Właściwości osi elementu podrzędnego XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2d766-102">XML Child Axis Property (Visual Basic)</span></span>
<span data-ttu-id="2d766-103">Zapewnia dostęp do elementów podrzędnych jednego z następujących: <xref:System.Xml.Linq.XElement> obiektu, <xref:System.Xml.Linq.XDocument> obiektu, kolekcji <xref:System.Xml.Linq.XElement> obiektów lub kolekcji <xref:System.Xml.Linq.XDocument> obiektów.</span><span class="sxs-lookup"><span data-stu-id="2d766-103">Provides access to the children of one of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d766-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2d766-104">Syntax</span></span>  
  
```vb  
object.<child>  
```  
  
## <a name="parts"></a><span data-ttu-id="2d766-105">Części</span><span class="sxs-lookup"><span data-stu-id="2d766-105">Parts</span></span>  
  
|<span data-ttu-id="2d766-106">Termin</span><span class="sxs-lookup"><span data-stu-id="2d766-106">Term</span></span>|<span data-ttu-id="2d766-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="2d766-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="2d766-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="2d766-108">Required.</span></span> <span data-ttu-id="2d766-109"><xref:System.Xml.Linq.XElement>Obiekt, <xref:System.Xml.Linq.XDocument> obiekt, kolekcja <xref:System.Xml.Linq.XElement> obiektów lub kolekcja <xref:System.Xml.Linq.XDocument> obiektów.</span><span class="sxs-lookup"><span data-stu-id="2d766-109">An <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>|  
|<span data-ttu-id="2d766-110">. <</span><span class="sxs-lookup"><span data-stu-id="2d766-110">.<</span></span>|<span data-ttu-id="2d766-111">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="2d766-111">Required.</span></span> <span data-ttu-id="2d766-112">Wskazuje początek właściwości osi podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="2d766-112">Denotes the start of a child axis property.</span></span>|  
|`child`|<span data-ttu-id="2d766-113">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="2d766-113">Required.</span></span> <span data-ttu-id="2d766-114">Nazwa węzłów podrzędnych do uzyskania dostępu do formularza `[prefix:]name` .</span><span class="sxs-lookup"><span data-stu-id="2d766-114">Name of the child nodes to access, of the form `[prefix:]name`.</span></span><br /><br /> <span data-ttu-id="2d766-115">-   `Prefix`Obowiązkowe.</span><span class="sxs-lookup"><span data-stu-id="2d766-115">-   `Prefix` - Optional.</span></span> <span data-ttu-id="2d766-116">Prefiks przestrzeni nazw XML dla węzła podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="2d766-116">XML namespace prefix for the child node.</span></span> <span data-ttu-id="2d766-117">Musi być globalną przestrzenią nazw XML zdefiniowaną za pomocą `Imports` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="2d766-117">Must be a global XML namespace defined with an `Imports` statement.</span></span><br /><span data-ttu-id="2d766-118">-   `Name`Potrzeb.</span><span class="sxs-lookup"><span data-stu-id="2d766-118">-   `Name` - Required.</span></span> <span data-ttu-id="2d766-119">Nazwa lokalnego węzła podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="2d766-119">Local child node name.</span></span> <span data-ttu-id="2d766-120">Zobacz [nazwy zadeklarowanych elementów i atrybutów XML](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="2d766-120">See [Names of Declared XML Elements and Attributes](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
|>|<span data-ttu-id="2d766-121">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="2d766-121">Required.</span></span> <span data-ttu-id="2d766-122">Oznacza koniec właściwości osi podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="2d766-122">Denotes the end of a child axis property.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="2d766-123">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2d766-123">Return Value</span></span>  
 <span data-ttu-id="2d766-124">Kolekcja obiektów <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="2d766-124">A collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d766-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2d766-125">Remarks</span></span>  
 <span data-ttu-id="2d766-126">Można użyć właściwości osi elementu podrzędnego XML, aby uzyskać dostęp do węzłów podrzędnych przy użyciu nazwy <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument> obiektu lub z kolekcji <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument> obiektów.</span><span class="sxs-lookup"><span data-stu-id="2d766-126">You can use an XML child axis property to access child nodes by name from an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object, or from a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="2d766-127">Użyj właściwości XML, `Value` Aby uzyskać dostęp do wartości pierwszego węzła podrzędnego w zwróconej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="2d766-127">Use the XML `Value` property to access the value of the first child node in the returned collection.</span></span> <span data-ttu-id="2d766-128">Aby uzyskać więcej informacji, zobacz [Właściwość wartości XML](xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="2d766-128">For more information, see [XML Value Property](xml-value-property.md).</span></span>  
  
 <span data-ttu-id="2d766-129">Kompilator Visual Basic konwertuje właściwości osi podrzędnej na wywołania <xref:System.Xml.Linq.XContainer.Elements%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="2d766-129">The Visual Basic compiler converts child axis properties to calls to the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="2d766-130">Przestrzenie nazw XML</span><span class="sxs-lookup"><span data-stu-id="2d766-130">XML Namespaces</span></span>  
 <span data-ttu-id="2d766-131">Nazwa we właściwości osi podrzędnej może używać tylko prefiksów przestrzeni nazw XML zadeklarowanych globalnie z `Imports` instrukcją.</span><span class="sxs-lookup"><span data-stu-id="2d766-131">The name in a child axis property can use only XML namespace prefixes declared globally with the `Imports` statement.</span></span> <span data-ttu-id="2d766-132">Nie może używać prefiksów przestrzeni nazw XML zadeklarowanych lokalnie w literałach elementu XML.</span><span class="sxs-lookup"><span data-stu-id="2d766-132">It cannot use XML namespace prefixes declared locally within XML element literals.</span></span> <span data-ttu-id="2d766-133">Aby uzyskać więcej informacji, zobacz [Imports — Instrukcja (przestrzeń nazw XML)](../statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="2d766-133">For more information, see [Imports Statement (XML Namespace)](../statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d766-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d766-134">Example</span></span>  
 <span data-ttu-id="2d766-135">Poniższy przykład pokazuje, jak uzyskać dostęp do węzłów podrzędnych o nazwie `phone` z `contact` obiektu.</span><span class="sxs-lookup"><span data-stu-id="2d766-135">The following example shows how to access the child nodes named `phone` from the `contact` object.</span></span>  
  
 [!code-vb[VbXMLSamples#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#17)]  
  
 <span data-ttu-id="2d766-136">Ten kod wyświetla następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="2d766-136">This code displays the following text:</span></span>  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="2d766-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d766-137">Example</span></span>  
 <span data-ttu-id="2d766-138">Poniższy przykład pokazuje, jak uzyskać dostęp do węzłów podrzędnych o nazwie `phone` z kolekcji zwróconej przez `contact` Właściwość osi elementu podrzędnego `contacts` obiektu.</span><span class="sxs-lookup"><span data-stu-id="2d766-138">The following example shows how to access the child nodes named `phone` from the collection returned by the `contact` child axis property of the `contacts` object.</span></span>  
  
 [!code-vb[VbXMLSamples#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#18)]  
  
 <span data-ttu-id="2d766-139">Ten kod wyświetla następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="2d766-139">This code displays the following text:</span></span>  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="2d766-140">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d766-140">Example</span></span>  
 <span data-ttu-id="2d766-141">Poniższy przykład deklaruje `ns` jako prefiks przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="2d766-141">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="2d766-142">Następnie używa prefiksu przestrzeni nazw w celu utworzenia literału XML i uzyskania dostępu do pierwszego węzła podrzędnego przy użyciu kwalifikowanej nazwy `ns:name` .</span><span class="sxs-lookup"><span data-stu-id="2d766-142">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name `ns:name`.</span></span>  
  
 [!code-vb[VbXMLSamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples8.vb#19)]  
  
 <span data-ttu-id="2d766-143">Ten kod wyświetla następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="2d766-143">This code displays the following text:</span></span>  
  
 `Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="2d766-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d766-144">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="2d766-145">Właściwości osi XML</span><span class="sxs-lookup"><span data-stu-id="2d766-145">XML Axis Properties</span></span>](index.md)
- [<span data-ttu-id="2d766-146">Literały XML</span><span class="sxs-lookup"><span data-stu-id="2d766-146">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="2d766-147">Tworzenie XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2d766-147">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="2d766-148">Nazwy deklarowanych elementów XML oraz atrybuty</span><span class="sxs-lookup"><span data-stu-id="2d766-148">Names of Declared XML Elements and Attributes</span></span>](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
