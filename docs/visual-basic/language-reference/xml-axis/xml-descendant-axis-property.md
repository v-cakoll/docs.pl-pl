---
title: "Właściwości osi elementu podrzędnego XML (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlPropertyDescendantsAxis
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML descendant axis property [Visual Basic]
- descendant axis property [Visual Baisc]
- XML axis [Visual Basic], descendant
- XML [Visual Basic], accessing
ms.assetid: a178f85b-5d54-438f-8479-40b62af6fe76
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0f3c42b5134b058c010ca4c7a5ee7c24627c65fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="xml-descendant-axis-property-visual-basic"></a><span data-ttu-id="6906c-102">Właściwości osi elementu podrzędnego XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6906c-102">XML Descendant Axis Property (Visual Basic)</span></span>
<span data-ttu-id="6906c-103">Zapewnia dostęp do następujących obiektów podrzędnych: <xref:System.Xml.Linq.XElement> obiektu <xref:System.Xml.Linq.XDocument> obiektu, to zbiór <xref:System.Xml.Linq.XElement> obiektów lub zbiór <xref:System.Xml.Linq.XDocument> obiektów.</span><span class="sxs-lookup"><span data-stu-id="6906c-103">Provides access to the descendants of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6906c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6906c-104">Syntax</span></span>  
  
```  
object...<descendant>  
```  
  
## <a name="parts"></a><span data-ttu-id="6906c-105">Części</span><span class="sxs-lookup"><span data-stu-id="6906c-105">Parts</span></span>  
 `object`  
 <span data-ttu-id="6906c-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="6906c-106">Required.</span></span> <span data-ttu-id="6906c-107"><xref:System.Xml.Linq.XElement> Obiektu <xref:System.Xml.Linq.XDocument> obiektu, to zbiór <xref:System.Xml.Linq.XElement> obiektów lub zbiór <xref:System.Xml.Linq.XDocument> obiektów.</span><span class="sxs-lookup"><span data-stu-id="6906c-107">An <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>  
  
 <span data-ttu-id="6906c-108">...<</span><span class="sxs-lookup"><span data-stu-id="6906c-108">...<</span></span>  
 <span data-ttu-id="6906c-109">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="6906c-109">Required.</span></span> <span data-ttu-id="6906c-110">Oznacza początek właściwości osi elementu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="6906c-110">Denotes the start of a descendant axis property.</span></span>  
  
 `descendant`  
 <span data-ttu-id="6906c-111">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="6906c-111">Required.</span></span> <span data-ttu-id="6906c-112">Nazwy elementów podrzędnych węzłów do formularza [`prefix``:`]`name`.</span><span class="sxs-lookup"><span data-stu-id="6906c-112">Name of the descendant nodes to access, of the form [`prefix``:`]`name`.</span></span>  
  
|<span data-ttu-id="6906c-113">Część</span><span class="sxs-lookup"><span data-stu-id="6906c-113">Part</span></span>|<span data-ttu-id="6906c-114">Opis</span><span class="sxs-lookup"><span data-stu-id="6906c-114">Description</span></span>|  
|----------|-----------------|  
|`prefix`|<span data-ttu-id="6906c-115">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="6906c-115">Optional.</span></span> <span data-ttu-id="6906c-116">Prefiks przestrzeni nazw XML dla elementów podrzędnych węzła.</span><span class="sxs-lookup"><span data-stu-id="6906c-116">XML namespace prefix for the descendant node.</span></span> <span data-ttu-id="6906c-117">Musi być globalnej przestrzeni nazw XML, który jest zdefiniowany przy użyciu `Imports` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="6906c-117">Must be a global XML namespace that is defined by using an `Imports` statement.</span></span>|  
|`name`|<span data-ttu-id="6906c-118">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="6906c-118">Required.</span></span> <span data-ttu-id="6906c-119">Lokalna nazwa elementu podrzędnego węzła.</span><span class="sxs-lookup"><span data-stu-id="6906c-119">Local name of the descendant node.</span></span> <span data-ttu-id="6906c-120">Zobacz [nazwy deklarowanych elementów XML oraz atrybuty](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="6906c-120">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
  
 \>  
 <span data-ttu-id="6906c-121">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="6906c-121">Required.</span></span> <span data-ttu-id="6906c-122">Oznacza koniec właściwości osi elementu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="6906c-122">Denotes the end of a descendant axis property.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6906c-123">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6906c-123">Return Value</span></span>  
 <span data-ttu-id="6906c-124">Kolekcja <xref:System.Xml.Linq.XElement> obiektów.</span><span class="sxs-lookup"><span data-stu-id="6906c-124">A collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6906c-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6906c-125">Remarks</span></span>  
 <span data-ttu-id="6906c-126">Właściwości osi descendant XML umożliwia dostęp do elementów podrzędnych węzłów, nazwy z <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument> obiekt, lub z kolekcji <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument> obiektów.</span><span class="sxs-lookup"><span data-stu-id="6906c-126">You can use an XML descendant axis property to access descendant nodes by name from an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object, or from a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="6906c-127">Użyj pliku XML `Value` właściwość, aby uzyskać dostęp do wartości pierwszy węzeł elementu podrzędnego w zwracanej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="6906c-127">Use the XML `Value` property to access the value of the first descendant node in the returned collection.</span></span> <span data-ttu-id="6906c-128">Aby uzyskać więcej informacji, zobacz [właściwość wartości XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="6906c-128">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>  
  
 <span data-ttu-id="6906c-129">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Kompilatora konwertuje właściwości osi elementu podrzędnego wywołań <xref:System.Xml.Linq.XContainer.Descendants%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="6906c-129">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler converts descendant axis properties into calls to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="6906c-130">Przestrzenie nazw XML</span><span class="sxs-lookup"><span data-stu-id="6906c-130">XML Namespaces</span></span>  
 <span data-ttu-id="6906c-131">Nazwa właściwości osi elementu podrzędnego można użyć tylko obszary nazw XML zadeklarowany globalnie z `Imports` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="6906c-131">The name in a descendant axis property can use only XML namespaces declared globally with the `Imports` statement.</span></span> <span data-ttu-id="6906c-132">Nie może używać lokalnie zadeklarowane w literałach XML elementu przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="6906c-132">It cannot use XML namespaces declared locally within XML element literals.</span></span> <span data-ttu-id="6906c-133">Aby uzyskać więcej informacji, zobacz [Importy — instrukcja (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="6906c-133">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6906c-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="6906c-134">Example</span></span>  
 <span data-ttu-id="6906c-135">Poniższy przykład przedstawia sposób uzyskać dostęp do wartości pierwszego elementu podrzędnego węzła o nazwie `name` i wartości wszystkich węzłów elementów podrzędnych o nazwie `phone` z `contacts` obiektu.</span><span class="sxs-lookup"><span data-stu-id="6906c-135">The following example shows how to access the value of the first descendant node named `name` and the values of all descendant nodes named `phone` from the `contacts` object.</span></span>  
  
 [!code-vb[VbXMLSamples#25](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-descendant-axis-property_1.vb)]  
  
 <span data-ttu-id="6906c-136">Ten kod zawiera następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="6906c-136">This code displays the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="6906c-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="6906c-137">Example</span></span>  
 <span data-ttu-id="6906c-138">Poniższy przykład deklaruje `ns` jako prefiks przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="6906c-138">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="6906c-139">Następnie używa prefiks przestrzeni nazw do utworzenia literału XML i uzyskać dostęp do wartości pierwszy węzeł podrzędny o nazwie kwalifikowanej `ns:name`.</span><span class="sxs-lookup"><span data-stu-id="6906c-139">It then uses the prefix of the namespace to create an XML literal and access the value of the first child node with the qualified name `ns:name`.</span></span>  
  
 [!code-vb[VbXMLSamples#26](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-descendant-axis-property_2.vb)]  
  
 <span data-ttu-id="6906c-140">Ten kod zawiera następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="6906c-140">This code displays the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="6906c-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6906c-141">See Also</span></span>  
 <xref:System.Xml.Linq.XElement>  
 [<span data-ttu-id="6906c-142">Właściwości osi XML</span><span class="sxs-lookup"><span data-stu-id="6906c-142">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [<span data-ttu-id="6906c-143">Literały XML</span><span class="sxs-lookup"><span data-stu-id="6906c-143">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="6906c-144">Tworzenie XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6906c-144">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="6906c-145">Nazwy deklarowanych elementów XML oraz atrybuty</span><span class="sxs-lookup"><span data-stu-id="6906c-145">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
