---
title: Właściwości osi elementu podrzędnego XML (Visual Basic)
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
ms.openlocfilehash: 8f8283e7ed09e657a20addab0b203b3d99420d3a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58838816"
---
# <a name="xml-child-axis-property-visual-basic"></a><span data-ttu-id="ff035-102">Właściwości osi elementu podrzędnego XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ff035-102">XML Child Axis Property (Visual Basic)</span></span>
<span data-ttu-id="ff035-103">Zapewnia dostęp do elementów podrzędnych w jednej z następujących czynności: <xref:System.Xml.Linq.XElement> obiektu <xref:System.Xml.Linq.XDocument> object, zbiór <xref:System.Xml.Linq.XElement> obiektów lub kolekcji <xref:System.Xml.Linq.XDocument> obiektów.</span><span class="sxs-lookup"><span data-stu-id="ff035-103">Provides access to the children of one of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff035-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ff035-104">Syntax</span></span>  
  
```  
object.<child>  
```  
  
## <a name="parts"></a><span data-ttu-id="ff035-105">Części</span><span class="sxs-lookup"><span data-stu-id="ff035-105">Parts</span></span>  
  
|<span data-ttu-id="ff035-106">Termin</span><span class="sxs-lookup"><span data-stu-id="ff035-106">Term</span></span>|<span data-ttu-id="ff035-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="ff035-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="ff035-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="ff035-108">Required.</span></span> <span data-ttu-id="ff035-109"><xref:System.Xml.Linq.XElement> Obiektu <xref:System.Xml.Linq.XDocument> object, zbiór <xref:System.Xml.Linq.XElement> obiektów lub kolekcji <xref:System.Xml.Linq.XDocument> obiektów.</span><span class="sxs-lookup"><span data-stu-id="ff035-109">An <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>|  
|<span data-ttu-id="ff035-110">.<</span><span class="sxs-lookup"><span data-stu-id="ff035-110">.<</span></span>|<span data-ttu-id="ff035-111">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="ff035-111">Required.</span></span> <span data-ttu-id="ff035-112">Oznacza początek właściwości osi elementu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="ff035-112">Denotes the start of a child axis property.</span></span>|  
|`child`|<span data-ttu-id="ff035-113">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="ff035-113">Required.</span></span> <span data-ttu-id="ff035-114">Nazwy węzłów podrzędnych, aby uzyskać dostęp, w postaci [`prefix:]name`.</span><span class="sxs-lookup"><span data-stu-id="ff035-114">Name of the child nodes to access, of the form [`prefix:]name`.</span></span><br /><br /> <span data-ttu-id="ff035-115">-   `Prefix` — Opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="ff035-115">-   `Prefix` - Optional.</span></span> <span data-ttu-id="ff035-116">Prefiks przestrzeni nazw XML dla węzła podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="ff035-116">XML namespace prefix for the child node.</span></span> <span data-ttu-id="ff035-117">Musi być globalnej przestrzeni nazw XML zdefiniowana z `Imports` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="ff035-117">Must be a global XML namespace defined with an `Imports` statement.</span></span><br /><span data-ttu-id="ff035-118">-   `Name` — Wymagane.</span><span class="sxs-lookup"><span data-stu-id="ff035-118">-   `Name` - Required.</span></span> <span data-ttu-id="ff035-119">Nazwa węzła podrzędnego lokalnego.</span><span class="sxs-lookup"><span data-stu-id="ff035-119">Local child node name.</span></span> <span data-ttu-id="ff035-120">Zobacz [nazwy deklarowanych elementów XML oraz atrybuty](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="ff035-120">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
|>|<span data-ttu-id="ff035-121">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="ff035-121">Required.</span></span> <span data-ttu-id="ff035-122">Oznacza koniec właściwości osi elementu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="ff035-122">Denotes the end of a child axis property.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="ff035-123">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ff035-123">Return Value</span></span>  
 <span data-ttu-id="ff035-124">Kolekcja <xref:System.Xml.Linq.XElement> obiektów.</span><span class="sxs-lookup"><span data-stu-id="ff035-124">A collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff035-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ff035-125">Remarks</span></span>  
 <span data-ttu-id="ff035-126">Umożliwia właściwości osi elementu podrzędnego XML access węzłów podrzędnych za pomocą nazwy z <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument> obiektu, lub z kolekcji <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument> obiektów.</span><span class="sxs-lookup"><span data-stu-id="ff035-126">You can use an XML child axis property to access child nodes by name from an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object, or from a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="ff035-127">Użyj pliku XML `Value` właściwość, aby uzyskać dostęp do wartości pierwszy węzeł podrzędny w zwrócona kolekcja.</span><span class="sxs-lookup"><span data-stu-id="ff035-127">Use the XML `Value` property to access the value of the first child node in the returned collection.</span></span> <span data-ttu-id="ff035-128">Aby uzyskać więcej informacji, zobacz [właściwość wartości XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="ff035-128">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>  
  
 <span data-ttu-id="ff035-129">Kompilator Visual Basic konwertuje właściwości osi podrzędnej wywołania <xref:System.Xml.Linq.XContainer.Elements%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ff035-129">The Visual Basic compiler converts child axis properties to calls to the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="ff035-130">Obszary nazw XML</span><span class="sxs-lookup"><span data-stu-id="ff035-130">XML Namespaces</span></span>  
 <span data-ttu-id="ff035-131">Nazwa w właściwości osi elementu podrzędnego można użyć tylko takie prefiksy przestrzeni nazw XML, globalnie zadeklarowane za pomocą `Imports` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="ff035-131">The name in a child axis property can use only XML namespace prefixes declared globally with the `Imports` statement.</span></span> <span data-ttu-id="ff035-132">Nie można go używać prefiksy przestrzeni nazw XML zadeklarowany lokalnie w literałach — element XML.</span><span class="sxs-lookup"><span data-stu-id="ff035-132">It cannot use XML namespace prefixes declared locally within XML element literals.</span></span> <span data-ttu-id="ff035-133">Aby uzyskać więcej informacji, zobacz [Importy — instrukcja (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="ff035-133">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff035-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="ff035-134">Example</span></span>  
 <span data-ttu-id="ff035-135">Poniższy przykład pokazuje, jak uzyskać dostęp do węzłów podrzędnych o nazwie `phone` z `contact` obiektu.</span><span class="sxs-lookup"><span data-stu-id="ff035-135">The following example shows how to access the child nodes named `phone` from the `contact` object.</span></span>  
  
 [!code-vb[VbXMLSamples#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#17)]  
  
 <span data-ttu-id="ff035-136">Ten kod wyświetla następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="ff035-136">This code displays the following text:</span></span>  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="ff035-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="ff035-137">Example</span></span>  
 <span data-ttu-id="ff035-138">Poniższy przykład pokazuje, jak uzyskać dostęp do węzłów podrzędnych o nazwie `phone` w kolekcji zwróconej przez `contact` właściwości osi elementu podrzędnego z `contacts` obiektu.</span><span class="sxs-lookup"><span data-stu-id="ff035-138">The following example shows how to access the child nodes named `phone` from the collection returned by the `contact` child axis property of the `contacts` object.</span></span>  
  
 [!code-vb[VbXMLSamples#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#18)]  
  
 <span data-ttu-id="ff035-139">Ten kod wyświetla następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="ff035-139">This code displays the following text:</span></span>  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="ff035-140">Przykład</span><span class="sxs-lookup"><span data-stu-id="ff035-140">Example</span></span>  
 <span data-ttu-id="ff035-141">Poniższy przykład deklaruje `ns` jako prefiks przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="ff035-141">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="ff035-142">Następnie używa prefiksu przestrzeni nazw tworzenie literałów XML i dostępem pierwszy węzeł podrzędny o nazwie kwalifikowanej `ns:name`.</span><span class="sxs-lookup"><span data-stu-id="ff035-142">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name `ns:name`.</span></span>  
  
 [!code-vb[VbXMLSamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples8.vb#19)]  
  
 <span data-ttu-id="ff035-143">Ten kod wyświetla następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="ff035-143">This code displays the following text:</span></span>  
  
 `Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="ff035-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ff035-144">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="ff035-145">Właściwości osi XML</span><span class="sxs-lookup"><span data-stu-id="ff035-145">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)
- [<span data-ttu-id="ff035-146">Literały XML</span><span class="sxs-lookup"><span data-stu-id="ff035-146">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="ff035-147">Tworzenie XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ff035-147">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="ff035-148">Nazwy deklarowanych elementów i atrybutów XML</span><span class="sxs-lookup"><span data-stu-id="ff035-148">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
