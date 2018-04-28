---
title: Właściwości osi elementu podrzędnego XML (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlPropertyChildAxis
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 89a59d00-985e-4f5c-b59f-29b47bad11cb
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: dadb21f4985497a90cc62f98c5fb2abdd7cc2781
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="xml-child-axis-property-visual-basic"></a><span data-ttu-id="49a85-102">Właściwości osi elementu podrzędnego XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="49a85-102">XML Child Axis Property (Visual Basic)</span></span>
<span data-ttu-id="49a85-103">Zapewnia dostęp do jednego z następujących elementów podrzędnych: <xref:System.Xml.Linq.XElement> obiektu <xref:System.Xml.Linq.XDocument> obiektu, to zbiór <xref:System.Xml.Linq.XElement> obiektów lub kolekcji <xref:System.Xml.Linq.XDocument> obiektów.</span><span class="sxs-lookup"><span data-stu-id="49a85-103">Provides access to the children of one of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49a85-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="49a85-104">Syntax</span></span>  
  
```  
object.<child>  
```  
  
## <a name="parts"></a><span data-ttu-id="49a85-105">Części</span><span class="sxs-lookup"><span data-stu-id="49a85-105">Parts</span></span>  
  
|<span data-ttu-id="49a85-106">Termin</span><span class="sxs-lookup"><span data-stu-id="49a85-106">Term</span></span>|<span data-ttu-id="49a85-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="49a85-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="49a85-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="49a85-108">Required.</span></span> <span data-ttu-id="49a85-109"><xref:System.Xml.Linq.XElement> Obiektu <xref:System.Xml.Linq.XDocument> obiektu, to zbiór <xref:System.Xml.Linq.XElement> obiektów lub zbiór <xref:System.Xml.Linq.XDocument> obiektów.</span><span class="sxs-lookup"><span data-stu-id="49a85-109">An <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>|  
|<span data-ttu-id="49a85-110">.<</span><span class="sxs-lookup"><span data-stu-id="49a85-110">.<</span></span>|<span data-ttu-id="49a85-111">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="49a85-111">Required.</span></span> <span data-ttu-id="49a85-112">Oznacza początek właściwości osi elementu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="49a85-112">Denotes the start of a child axis property.</span></span>|  
|`child`|<span data-ttu-id="49a85-113">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="49a85-113">Required.</span></span> <span data-ttu-id="49a85-114">Nazwa węzłów podrzędnych można uzyskać dostępu do formularza [`prefix``:`]`name`.</span><span class="sxs-lookup"><span data-stu-id="49a85-114">Name of the child nodes to access, of the form [`prefix``:`]`name`.</span></span><br /><br /> <span data-ttu-id="49a85-115">-   `Prefix` -Opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="49a85-115">-   `Prefix` - Optional.</span></span> <span data-ttu-id="49a85-116">Prefiks przestrzeni nazw XML dla węzła podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="49a85-116">XML namespace prefix for the child node.</span></span> <span data-ttu-id="49a85-117">Musi być globalnej przestrzeni nazw XML zdefiniowany za pomocą `Imports` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="49a85-117">Must be a global XML namespace defined with an `Imports` statement.</span></span><br /><span data-ttu-id="49a85-118">-   `Name` -Wymagane.</span><span class="sxs-lookup"><span data-stu-id="49a85-118">-   `Name` - Required.</span></span> <span data-ttu-id="49a85-119">Nazwy węzła podrzędnego lokalnego.</span><span class="sxs-lookup"><span data-stu-id="49a85-119">Local child node name.</span></span> <span data-ttu-id="49a85-120">Zobacz [nazwy deklarowanych elementów XML oraz atrybuty](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="49a85-120">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
|>|<span data-ttu-id="49a85-121">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="49a85-121">Required.</span></span> <span data-ttu-id="49a85-122">Oznacza koniec właściwości osi elementu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="49a85-122">Denotes the end of a child axis property.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="49a85-123">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="49a85-123">Return Value</span></span>  
 <span data-ttu-id="49a85-124">Kolekcja <xref:System.Xml.Linq.XElement> obiektów.</span><span class="sxs-lookup"><span data-stu-id="49a85-124">A collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="49a85-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="49a85-125">Remarks</span></span>  
 <span data-ttu-id="49a85-126">Umożliwia właściwości osi elementu podrzędnego XML węzłów podrzędnych dostępu według nazw z <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument> obiekt, lub z kolekcji <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument> obiektów.</span><span class="sxs-lookup"><span data-stu-id="49a85-126">You can use an XML child axis property to access child nodes by name from an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object, or from a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="49a85-127">Użyj pliku XML `Value` właściwość, aby uzyskać dostęp do wartości pierwszego węzła podrzędnego w zwracanej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="49a85-127">Use the XML `Value` property to access the value of the first child node in the returned collection.</span></span> <span data-ttu-id="49a85-128">Aby uzyskać więcej informacji, zobacz [właściwość wartości XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="49a85-128">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>  
  
 <span data-ttu-id="49a85-129">Kompilator Visual Basic konwertuje właściwości osi podrzędnej wywołań <xref:System.Xml.Linq.XContainer.Elements%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="49a85-129">The Visual Basic compiler converts child axis properties to calls to the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="49a85-130">Przestrzenie nazw XML</span><span class="sxs-lookup"><span data-stu-id="49a85-130">XML Namespaces</span></span>  
 <span data-ttu-id="49a85-131">Nazwa właściwości osi podrzędnej można użyć tylko takie prefiksy przestrzeni nazw XML, zadeklarowany globalnie z `Imports` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="49a85-131">The name in a child axis property can use only XML namespace prefixes declared globally with the `Imports` statement.</span></span> <span data-ttu-id="49a85-132">Nie można go użyć lokalnie zadeklarowane w literałach XML elementu prefiksy przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="49a85-132">It cannot use XML namespace prefixes declared locally within XML element literals.</span></span> <span data-ttu-id="49a85-133">Aby uzyskać więcej informacji, zobacz [Importy — instrukcja (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="49a85-133">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="49a85-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="49a85-134">Example</span></span>  
 <span data-ttu-id="49a85-135">Poniższy przykład pokazuje, jak uzyskać dostęp do węzłów podrzędnych o nazwie `phone` z `contact` obiektu.</span><span class="sxs-lookup"><span data-stu-id="49a85-135">The following example shows how to access the child nodes named `phone` from the `contact` object.</span></span>  
  
 [!code-vb[VbXMLSamples#17](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-child-axis-property_1.vb)]  
  
 <span data-ttu-id="49a85-136">Ten kod zawiera następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="49a85-136">This code displays the following text:</span></span>  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="49a85-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="49a85-137">Example</span></span>  
 <span data-ttu-id="49a85-138">Poniższy przykład pokazuje, jak uzyskać dostęp do węzłów podrzędnych o nazwie `phone` z kolekcji zwróconej przez `contact` właściwości osi elementu podrzędnego z `contacts` obiektu.</span><span class="sxs-lookup"><span data-stu-id="49a85-138">The following example shows how to access the child nodes named `phone` from the collection returned by the `contact` child axis property of the `contacts` object.</span></span>  
  
 [!code-vb[VbXMLSamples#18](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-child-axis-property_2.vb)]  
  
 <span data-ttu-id="49a85-139">Ten kod zawiera następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="49a85-139">This code displays the following text:</span></span>  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="49a85-140">Przykład</span><span class="sxs-lookup"><span data-stu-id="49a85-140">Example</span></span>  
 <span data-ttu-id="49a85-141">Poniższy przykład deklaruje `ns` jako prefiks przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="49a85-141">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="49a85-142">Następnie używa prefiks przestrzeni nazw do utworzenia literału XML i dostępu do pierwszy węzeł podrzędny o nazwie kwalifikowanej `ns:name`.</span><span class="sxs-lookup"><span data-stu-id="49a85-142">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name `ns:name`.</span></span>  
  
 [!code-vb[VbXMLSamples#19](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-child-axis-property_3.vb)]  
  
 <span data-ttu-id="49a85-143">Ten kod zawiera następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="49a85-143">This code displays the following text:</span></span>  
  
 `Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="49a85-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="49a85-144">See Also</span></span>  
 <xref:System.Xml.Linq.XElement>  
 [<span data-ttu-id="49a85-145">Właściwości osi XML</span><span class="sxs-lookup"><span data-stu-id="49a85-145">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [<span data-ttu-id="49a85-146">Literały XML</span><span class="sxs-lookup"><span data-stu-id="49a85-146">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="49a85-147">Tworzenie XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="49a85-147">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="49a85-148">Nazwy deklarowanych elementów i atrybutów XML</span><span class="sxs-lookup"><span data-stu-id="49a85-148">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
