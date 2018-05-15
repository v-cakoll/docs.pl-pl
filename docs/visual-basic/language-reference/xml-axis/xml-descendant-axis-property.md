---
title: Właściwości osi elementu podrzędnego XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyDescendantsAxis
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML descendant axis property [Visual Basic]
- descendant axis property [Visual Baisc]
- XML axis [Visual Basic], descendant
- XML [Visual Basic], accessing
ms.assetid: a178f85b-5d54-438f-8479-40b62af6fe76
ms.openlocfilehash: 02bb87235efbdef8a5474fec9799757f75877876
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="xml-descendant-axis-property-visual-basic"></a><span data-ttu-id="5cef8-102">Właściwości osi elementu podrzędnego XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5cef8-102">XML Descendant Axis Property (Visual Basic)</span></span>
<span data-ttu-id="5cef8-103">Zapewnia dostęp do następujących obiektów podrzędnych: <xref:System.Xml.Linq.XElement> obiektu <xref:System.Xml.Linq.XDocument> obiektu, to zbiór <xref:System.Xml.Linq.XElement> obiektów lub zbiór <xref:System.Xml.Linq.XDocument> obiektów.</span><span class="sxs-lookup"><span data-stu-id="5cef8-103">Provides access to the descendants of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cef8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5cef8-104">Syntax</span></span>  
  
```  
object...<descendant>  
```  
  
## <a name="parts"></a><span data-ttu-id="5cef8-105">Części</span><span class="sxs-lookup"><span data-stu-id="5cef8-105">Parts</span></span>  
 `object`  
 <span data-ttu-id="5cef8-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="5cef8-106">Required.</span></span> <span data-ttu-id="5cef8-107"><xref:System.Xml.Linq.XElement> Obiektu <xref:System.Xml.Linq.XDocument> obiektu, to zbiór <xref:System.Xml.Linq.XElement> obiektów lub zbiór <xref:System.Xml.Linq.XDocument> obiektów.</span><span class="sxs-lookup"><span data-stu-id="5cef8-107">An <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>  
  
 <span data-ttu-id="5cef8-108">...<</span><span class="sxs-lookup"><span data-stu-id="5cef8-108">...<</span></span>  
 <span data-ttu-id="5cef8-109">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="5cef8-109">Required.</span></span> <span data-ttu-id="5cef8-110">Oznacza początek właściwości osi elementu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="5cef8-110">Denotes the start of a descendant axis property.</span></span>  
  
 `descendant`  
 <span data-ttu-id="5cef8-111">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="5cef8-111">Required.</span></span> <span data-ttu-id="5cef8-112">Nazwy elementów podrzędnych węzłów do formularza [`prefix``:`]`name`.</span><span class="sxs-lookup"><span data-stu-id="5cef8-112">Name of the descendant nodes to access, of the form [`prefix``:`]`name`.</span></span>  
  
|<span data-ttu-id="5cef8-113">Część</span><span class="sxs-lookup"><span data-stu-id="5cef8-113">Part</span></span>|<span data-ttu-id="5cef8-114">Opis</span><span class="sxs-lookup"><span data-stu-id="5cef8-114">Description</span></span>|  
|----------|-----------------|  
|`prefix`|<span data-ttu-id="5cef8-115">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="5cef8-115">Optional.</span></span> <span data-ttu-id="5cef8-116">Prefiks przestrzeni nazw XML dla elementów podrzędnych węzła.</span><span class="sxs-lookup"><span data-stu-id="5cef8-116">XML namespace prefix for the descendant node.</span></span> <span data-ttu-id="5cef8-117">Musi być globalnej przestrzeni nazw XML, który jest zdefiniowany przy użyciu `Imports` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="5cef8-117">Must be a global XML namespace that is defined by using an `Imports` statement.</span></span>|  
|`name`|<span data-ttu-id="5cef8-118">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="5cef8-118">Required.</span></span> <span data-ttu-id="5cef8-119">Lokalna nazwa elementu podrzędnego węzła.</span><span class="sxs-lookup"><span data-stu-id="5cef8-119">Local name of the descendant node.</span></span> <span data-ttu-id="5cef8-120">Zobacz [nazwy deklarowanych elementów XML oraz atrybuty](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="5cef8-120">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
  
 \>  
 <span data-ttu-id="5cef8-121">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="5cef8-121">Required.</span></span> <span data-ttu-id="5cef8-122">Oznacza koniec właściwości osi elementu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="5cef8-122">Denotes the end of a descendant axis property.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5cef8-123">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5cef8-123">Return Value</span></span>  
 <span data-ttu-id="5cef8-124">Kolekcja <xref:System.Xml.Linq.XElement> obiektów.</span><span class="sxs-lookup"><span data-stu-id="5cef8-124">A collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5cef8-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5cef8-125">Remarks</span></span>  
 <span data-ttu-id="5cef8-126">Właściwości osi descendant XML umożliwia dostęp do elementów podrzędnych węzłów, nazwy z <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument> obiekt, lub z kolekcji <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument> obiektów.</span><span class="sxs-lookup"><span data-stu-id="5cef8-126">You can use an XML descendant axis property to access descendant nodes by name from an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object, or from a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="5cef8-127">Użyj pliku XML `Value` właściwość, aby uzyskać dostęp do wartości pierwszy węzeł elementu podrzędnego w zwracanej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="5cef8-127">Use the XML `Value` property to access the value of the first descendant node in the returned collection.</span></span> <span data-ttu-id="5cef8-128">Aby uzyskać więcej informacji, zobacz [właściwość wartości XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="5cef8-128">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>  
  
 <span data-ttu-id="5cef8-129">Kompilator Visual Basic konwertuje właściwości osi elementu podrzędnego wywołań <xref:System.Xml.Linq.XContainer.Descendants%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="5cef8-129">The Visual Basic compiler converts descendant axis properties into calls to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="5cef8-130">Przestrzenie nazw XML</span><span class="sxs-lookup"><span data-stu-id="5cef8-130">XML Namespaces</span></span>  
 <span data-ttu-id="5cef8-131">Nazwa właściwości osi elementu podrzędnego można użyć tylko obszary nazw XML zadeklarowany globalnie z `Imports` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="5cef8-131">The name in a descendant axis property can use only XML namespaces declared globally with the `Imports` statement.</span></span> <span data-ttu-id="5cef8-132">Nie może używać lokalnie zadeklarowane w literałach XML elementu przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="5cef8-132">It cannot use XML namespaces declared locally within XML element literals.</span></span> <span data-ttu-id="5cef8-133">Aby uzyskać więcej informacji, zobacz [Importy — instrukcja (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="5cef8-133">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5cef8-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="5cef8-134">Example</span></span>  
 <span data-ttu-id="5cef8-135">Poniższy przykład przedstawia sposób uzyskać dostęp do wartości pierwszego elementu podrzędnego węzła o nazwie `name` i wartości wszystkich węzłów elementów podrzędnych o nazwie `phone` z `contacts` obiektu.</span><span class="sxs-lookup"><span data-stu-id="5cef8-135">The following example shows how to access the value of the first descendant node named `name` and the values of all descendant nodes named `phone` from the `contacts` object.</span></span>  
  
 [!code-vb[VbXMLSamples#25](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-descendant-axis-property_1.vb)]  
  
 <span data-ttu-id="5cef8-136">Ten kod zawiera następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="5cef8-136">This code displays the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="5cef8-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="5cef8-137">Example</span></span>  
 <span data-ttu-id="5cef8-138">Poniższy przykład deklaruje `ns` jako prefiks przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="5cef8-138">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="5cef8-139">Następnie używa prefiks przestrzeni nazw do utworzenia literału XML i uzyskać dostęp do wartości pierwszy węzeł podrzędny o nazwie kwalifikowanej `ns:name`.</span><span class="sxs-lookup"><span data-stu-id="5cef8-139">It then uses the prefix of the namespace to create an XML literal and access the value of the first child node with the qualified name `ns:name`.</span></span>  
  
 [!code-vb[VbXMLSamples#26](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-descendant-axis-property_2.vb)]  
  
 <span data-ttu-id="5cef8-140">Ten kod zawiera następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="5cef8-140">This code displays the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="5cef8-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5cef8-141">See Also</span></span>  
 <xref:System.Xml.Linq.XElement>  
 [<span data-ttu-id="5cef8-142">Właściwości osi XML</span><span class="sxs-lookup"><span data-stu-id="5cef8-142">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [<span data-ttu-id="5cef8-143">Literały XML</span><span class="sxs-lookup"><span data-stu-id="5cef8-143">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="5cef8-144">Tworzenie XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5cef8-144">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="5cef8-145">Nazwy deklarowanych elementów i atrybutów XML</span><span class="sxs-lookup"><span data-stu-id="5cef8-145">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
