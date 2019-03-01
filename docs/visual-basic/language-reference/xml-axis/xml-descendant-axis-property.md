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
ms.openlocfilehash: f6d8a958b5a33c236ca5273cccda0e13693b564e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56973538"
---
# <a name="xml-descendant-axis-property-visual-basic"></a><span data-ttu-id="77fdb-102">Właściwości osi elementu podrzędnego XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="77fdb-102">XML Descendant Axis Property (Visual Basic)</span></span>
<span data-ttu-id="77fdb-103">Zapewnia dostęp do obiektów podrzędnych z następujących czynności: <xref:System.Xml.Linq.XElement> obiektu <xref:System.Xml.Linq.XDocument> object, zbiór <xref:System.Xml.Linq.XElement> obiektów lub kolekcji <xref:System.Xml.Linq.XDocument> obiektów.</span><span class="sxs-lookup"><span data-stu-id="77fdb-103">Provides access to the descendants of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77fdb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="77fdb-104">Syntax</span></span>  
  
```  
object...<descendant>  
```  
  
## <a name="parts"></a><span data-ttu-id="77fdb-105">Części</span><span class="sxs-lookup"><span data-stu-id="77fdb-105">Parts</span></span>  
 `object`  
 <span data-ttu-id="77fdb-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="77fdb-106">Required.</span></span> <span data-ttu-id="77fdb-107"><xref:System.Xml.Linq.XElement> Obiektu <xref:System.Xml.Linq.XDocument> object, zbiór <xref:System.Xml.Linq.XElement> obiektów lub kolekcji <xref:System.Xml.Linq.XDocument> obiektów.</span><span class="sxs-lookup"><span data-stu-id="77fdb-107">An <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>  
  
 <span data-ttu-id="77fdb-108">...<</span><span class="sxs-lookup"><span data-stu-id="77fdb-108">...<</span></span>  
 <span data-ttu-id="77fdb-109">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="77fdb-109">Required.</span></span> <span data-ttu-id="77fdb-110">Oznacza początek właściwości osi elementu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="77fdb-110">Denotes the start of a descendant axis property.</span></span>  
  
 `descendant`  
 <span data-ttu-id="77fdb-111">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="77fdb-111">Required.</span></span> <span data-ttu-id="77fdb-112">Nazwy węzłów podrzędnych dostępu, w postaci [`prefix:]name`.</span><span class="sxs-lookup"><span data-stu-id="77fdb-112">Name of the descendant nodes to access, of the form [`prefix:]name`.</span></span>  
  
|<span data-ttu-id="77fdb-113">Część</span><span class="sxs-lookup"><span data-stu-id="77fdb-113">Part</span></span>|<span data-ttu-id="77fdb-114">Opis</span><span class="sxs-lookup"><span data-stu-id="77fdb-114">Description</span></span>|  
|----------|-----------------|  
|`prefix`|<span data-ttu-id="77fdb-115">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="77fdb-115">Optional.</span></span> <span data-ttu-id="77fdb-116">Prefiks przestrzeni nazw XML dla elementów podrzędnych węzła.</span><span class="sxs-lookup"><span data-stu-id="77fdb-116">XML namespace prefix for the descendant node.</span></span> <span data-ttu-id="77fdb-117">Musi być globalnej przestrzeni nazw XML, która jest zdefiniowana za pomocą `Imports` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="77fdb-117">Must be a global XML namespace that is defined by using an `Imports` statement.</span></span>|  
|`name`|<span data-ttu-id="77fdb-118">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="77fdb-118">Required.</span></span> <span data-ttu-id="77fdb-119">Lokalna nazwa elementu podrzędnego węzła.</span><span class="sxs-lookup"><span data-stu-id="77fdb-119">Local name of the descendant node.</span></span> <span data-ttu-id="77fdb-120">Zobacz [nazwy deklarowanych elementów XML oraz atrybuty](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="77fdb-120">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
  
 \>  
 <span data-ttu-id="77fdb-121">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="77fdb-121">Required.</span></span> <span data-ttu-id="77fdb-122">Oznacza koniec właściwości osi elementu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="77fdb-122">Denotes the end of a descendant axis property.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="77fdb-123">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="77fdb-123">Return Value</span></span>  
 <span data-ttu-id="77fdb-124">Kolekcja <xref:System.Xml.Linq.XElement> obiektów.</span><span class="sxs-lookup"><span data-stu-id="77fdb-124">A collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="77fdb-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="77fdb-125">Remarks</span></span>  
 <span data-ttu-id="77fdb-126">Właściwości osi descendant XML umożliwia dostęp do węzłów podrzędnych za pomocą nazwy z <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument> obiektu, lub z kolekcji <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument> obiektów.</span><span class="sxs-lookup"><span data-stu-id="77fdb-126">You can use an XML descendant axis property to access descendant nodes by name from an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object, or from a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="77fdb-127">Użyj pliku XML `Value` właściwość, aby uzyskać dostęp do wartości pierwszego elementu podrzędnego węzła w zwrócona kolekcja.</span><span class="sxs-lookup"><span data-stu-id="77fdb-127">Use the XML `Value` property to access the value of the first descendant node in the returned collection.</span></span> <span data-ttu-id="77fdb-128">Aby uzyskać więcej informacji, zobacz [właściwość wartości XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="77fdb-128">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>  
  
 <span data-ttu-id="77fdb-129">Kompilator Visual Basic konwertuje właściwości osi elementu podrzędnego do wywołania <xref:System.Xml.Linq.XContainer.Descendants%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="77fdb-129">The Visual Basic compiler converts descendant axis properties into calls to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="77fdb-130">Obszary nazw XML</span><span class="sxs-lookup"><span data-stu-id="77fdb-130">XML Namespaces</span></span>  
 <span data-ttu-id="77fdb-131">Nazwa właściwości osi elementu podrzędnego można użyć tylko obszary nazw XML globalnie zadeklarowane za pomocą `Imports` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="77fdb-131">The name in a descendant axis property can use only XML namespaces declared globally with the `Imports` statement.</span></span> <span data-ttu-id="77fdb-132">Nie może używać przestrzeni nazw XML zadeklarowany lokalnie w literałach — element XML.</span><span class="sxs-lookup"><span data-stu-id="77fdb-132">It cannot use XML namespaces declared locally within XML element literals.</span></span> <span data-ttu-id="77fdb-133">Aby uzyskać więcej informacji, zobacz [Importy — instrukcja (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="77fdb-133">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="77fdb-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="77fdb-134">Example</span></span>  
 <span data-ttu-id="77fdb-135">Poniższy przykład pokazuje, jak uzyskać dostęp do wartości pierwszego elementu podrzędnego węzła o nazwie `name` i wartości wszystkich podrzędnych węzłów o nazwie `phone` z `contacts` obiektu.</span><span class="sxs-lookup"><span data-stu-id="77fdb-135">The following example shows how to access the value of the first descendant node named `name` and the values of all descendant nodes named `phone` from the `contacts` object.</span></span>  
  
 [!code-vb[VbXMLSamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#25)]  
  
 <span data-ttu-id="77fdb-136">Ten kod wyświetla następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="77fdb-136">This code displays the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="77fdb-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="77fdb-137">Example</span></span>  
 <span data-ttu-id="77fdb-138">Poniższy przykład deklaruje `ns` jako prefiks przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="77fdb-138">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="77fdb-139">Następnie używa prefiksu przestrzeni nazw tworzenie literałów XML i dostęp do wartości pierwszy węzeł podrzędny o nazwie kwalifikowanej `ns:name`.</span><span class="sxs-lookup"><span data-stu-id="77fdb-139">It then uses the prefix of the namespace to create an XML literal and access the value of the first child node with the qualified name `ns:name`.</span></span>  
  
 [!code-vb[VbXMLSamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples12.vb#26)]  
  
 <span data-ttu-id="77fdb-140">Ten kod wyświetla następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="77fdb-140">This code displays the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="77fdb-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="77fdb-141">See also</span></span>
- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="77fdb-142">Właściwości osi XML</span><span class="sxs-lookup"><span data-stu-id="77fdb-142">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)
- [<span data-ttu-id="77fdb-143">Literały XML</span><span class="sxs-lookup"><span data-stu-id="77fdb-143">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="77fdb-144">Tworzenie XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="77fdb-144">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="77fdb-145">Nazwy deklarowanych elementów i atrybutów XML</span><span class="sxs-lookup"><span data-stu-id="77fdb-145">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
