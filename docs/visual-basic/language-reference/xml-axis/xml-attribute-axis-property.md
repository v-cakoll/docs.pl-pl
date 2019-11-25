---
title: Właściwości osi atrybutu XML
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyAttributeAxis
helpviewer_keywords:
- attribute axis property [Visual Basic]
- Visual Basic code, accessing XML
- XML attribute axis property [Visual Basic]
- XML axis [Visual Basic], attribute
- XML [Visual Basic], accessing
ms.assetid: 7a4777e1-0618-4de9-9510-fb9ace2bf4db
ms.openlocfilehash: 109c4b45a5e3ed4e3e4db49687df5cb127a5e0c6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352671"
---
# <a name="xml-attribute-axis-property-visual-basic"></a><span data-ttu-id="cbc47-102">Właściwości osi atrybutu XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cbc47-102">XML Attribute Axis Property (Visual Basic)</span></span>
<span data-ttu-id="cbc47-103">Provides access to the value of an attribute for an <xref:System.Xml.Linq.XElement> object or to the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span><span class="sxs-lookup"><span data-stu-id="cbc47-103">Provides access to the value of an attribute for an <xref:System.Xml.Linq.XElement> object or to the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbc47-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cbc47-104">Syntax</span></span>  
  
```vb  
object.@attribute  
' -or-  
object.@<attribute>  
```  
  
## <a name="parts"></a><span data-ttu-id="cbc47-105">Części</span><span class="sxs-lookup"><span data-stu-id="cbc47-105">Parts</span></span>  
 `object`  
 <span data-ttu-id="cbc47-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="cbc47-106">Required.</span></span> <span data-ttu-id="cbc47-107">An <xref:System.Xml.Linq.XElement> object or a collection of <xref:System.Xml.Linq.XElement> objects.</span><span class="sxs-lookup"><span data-stu-id="cbc47-107">An <xref:System.Xml.Linq.XElement> object or a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="cbc47-108">.@</span><span class="sxs-lookup"><span data-stu-id="cbc47-108">.@</span></span>  
 <span data-ttu-id="cbc47-109">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="cbc47-109">Required.</span></span> <span data-ttu-id="cbc47-110">Denotes the start of an attribute axis property.</span><span class="sxs-lookup"><span data-stu-id="cbc47-110">Denotes the start of an attribute axis property.</span></span>  
  
 <  
 <span data-ttu-id="cbc47-111">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="cbc47-111">Optional.</span></span> <span data-ttu-id="cbc47-112">Denotes the beginning of the name of the attribute when `attribute` is not a valid identifier in Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="cbc47-112">Denotes the beginning of the name of the attribute when `attribute` is not a valid identifier in Visual Basic.</span></span>  
  
 `attribute`  
 <span data-ttu-id="cbc47-113">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="cbc47-113">Required.</span></span> <span data-ttu-id="cbc47-114">Name of the attribute to access, of the form [`prefix`:]`name`.</span><span class="sxs-lookup"><span data-stu-id="cbc47-114">Name of the attribute to access, of the form [`prefix`:]`name`.</span></span>  
  
|<span data-ttu-id="cbc47-115">Part</span><span class="sxs-lookup"><span data-stu-id="cbc47-115">Part</span></span>|<span data-ttu-id="cbc47-116">Opis</span><span class="sxs-lookup"><span data-stu-id="cbc47-116">Description</span></span>|  
|----------|-----------------|  
|`prefix`|<span data-ttu-id="cbc47-117">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="cbc47-117">Optional.</span></span> <span data-ttu-id="cbc47-118">XML namespace prefix for the attribute.</span><span class="sxs-lookup"><span data-stu-id="cbc47-118">XML namespace prefix for the attribute.</span></span> <span data-ttu-id="cbc47-119">Must be a global XML namespace defined with an `Imports` statement.</span><span class="sxs-lookup"><span data-stu-id="cbc47-119">Must be a global XML namespace defined with an `Imports` statement.</span></span>|  
|`name`|<span data-ttu-id="cbc47-120">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="cbc47-120">Required.</span></span> <span data-ttu-id="cbc47-121">Local attribute name.</span><span class="sxs-lookup"><span data-stu-id="cbc47-121">Local attribute name.</span></span> <span data-ttu-id="cbc47-122">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="cbc47-122">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
  
 \>  
 <span data-ttu-id="cbc47-123">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="cbc47-123">Optional.</span></span> <span data-ttu-id="cbc47-124">Denotes the end of the name of the attribute when `attribute` is not a valid identifier in Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="cbc47-124">Denotes the end of the name of the attribute when `attribute` is not a valid identifier in Visual Basic.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cbc47-125">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="cbc47-125">Return Value</span></span>  
 <span data-ttu-id="cbc47-126">A string that contains the value of `attribute`.</span><span class="sxs-lookup"><span data-stu-id="cbc47-126">A string that contains the value of `attribute`.</span></span> <span data-ttu-id="cbc47-127">If the attribute name does not exist, `Nothing` is returned.</span><span class="sxs-lookup"><span data-stu-id="cbc47-127">If the attribute name does not exist, `Nothing` is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cbc47-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cbc47-128">Remarks</span></span>  
 <span data-ttu-id="cbc47-129">You can use an XML attribute axis property to access the value of an attribute by name from an <xref:System.Xml.Linq.XElement> object or from the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span><span class="sxs-lookup"><span data-stu-id="cbc47-129">You can use an XML attribute axis property to access the value of an attribute by name from an <xref:System.Xml.Linq.XElement> object or from the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="cbc47-130">You can retrieve an attribute value by name, or add a new attribute to an element by specifying a new name preceded by the @ identifier.</span><span class="sxs-lookup"><span data-stu-id="cbc47-130">You can retrieve an attribute value by name, or add a new attribute to an element by specifying a new name preceded by the @ identifier.</span></span>  
  
 <span data-ttu-id="cbc47-131">When you refer to an XML attribute using the @ identifier, the attribute value is returned as a string and you do not need to explicitly specify the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span><span class="sxs-lookup"><span data-stu-id="cbc47-131">When you refer to an XML attribute using the @ identifier, the attribute value is returned as a string and you do not need to explicitly specify the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span>  
  
 <span data-ttu-id="cbc47-132">The naming rules for XML attributes differ from the naming rules for Visual Basic identifiers.</span><span class="sxs-lookup"><span data-stu-id="cbc47-132">The naming rules for XML attributes differ from the naming rules for Visual Basic identifiers.</span></span> <span data-ttu-id="cbc47-133">To access an XML attribute that has a name that is not a valid Visual Basic identifier, enclose the name in angle brackets (\< and >).</span><span class="sxs-lookup"><span data-stu-id="cbc47-133">To access an XML attribute that has a name that is not a valid Visual Basic identifier, enclose the name in angle brackets (\< and >).</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="cbc47-134">XML Namespaces</span><span class="sxs-lookup"><span data-stu-id="cbc47-134">XML Namespaces</span></span>  
 <span data-ttu-id="cbc47-135">The name in an attribute axis property can use only XML namespace prefixes declared globally by using the `Imports` statement.</span><span class="sxs-lookup"><span data-stu-id="cbc47-135">The name in an attribute axis property can use only XML namespace prefixes declared globally by using the `Imports` statement.</span></span> <span data-ttu-id="cbc47-136">It cannot use XML namespace prefixes declared locally within XML element literals.</span><span class="sxs-lookup"><span data-stu-id="cbc47-136">It cannot use XML namespace prefixes declared locally within XML element literals.</span></span> <span data-ttu-id="cbc47-137">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="cbc47-137">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cbc47-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="cbc47-138">Example</span></span>  
 <span data-ttu-id="cbc47-139">The following example shows how to get the values of the XML attributes named `type` from a collection of XML elements that are named `phone`.</span><span class="sxs-lookup"><span data-stu-id="cbc47-139">The following example shows how to get the values of the XML attributes named `type` from a collection of XML elements that are named `phone`.</span></span>  
  
 [!code-vb[VbXMLSamples#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#12)]  
  
 <span data-ttu-id="cbc47-140">This code displays the following text:</span><span class="sxs-lookup"><span data-stu-id="cbc47-140">This code displays the following text:</span></span>  
  
 `<phoneTypes>`  
  
 `<type>home</type>`  
  
 `<type>work</type>`  
  
 `</phoneTypes>`  
  
## <a name="example"></a><span data-ttu-id="cbc47-141">Przykład</span><span class="sxs-lookup"><span data-stu-id="cbc47-141">Example</span></span>  
 <span data-ttu-id="cbc47-142">The following example shows how to create attributes for an XML element both declaratively, as part of the XML, and dynamically by adding an attribute to an instance of an <xref:System.Xml.Linq.XElement> object.</span><span class="sxs-lookup"><span data-stu-id="cbc47-142">The following example shows how to create attributes for an XML element both declaratively, as part of the XML, and dynamically by adding an attribute to an instance of an <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="cbc47-143">The `type` attribute is created declaratively and the `owner` attribute is created dynamically.</span><span class="sxs-lookup"><span data-stu-id="cbc47-143">The `type` attribute is created declaratively and the `owner` attribute is created dynamically.</span></span>  
  
 [!code-vb[VbXMLSamples#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#44)]  
  
 <span data-ttu-id="cbc47-144">This code displays the following text:</span><span class="sxs-lookup"><span data-stu-id="cbc47-144">This code displays the following text:</span></span>  
  
```xml  
<phone type="home" owner="Harris, Phyllis">206-555-0144</phone>  
```  
  
## <a name="example"></a><span data-ttu-id="cbc47-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="cbc47-145">Example</span></span>  
 <span data-ttu-id="cbc47-146">The following example uses the angle bracket syntax to get the value of the XML attribute named `number-type`, which is not a valid identifier in Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="cbc47-146">The following example uses the angle bracket syntax to get the value of the XML attribute named `number-type`, which is not a valid identifier in Visual Basic.</span></span>  
  
 [!code-vb[VbXMLSamples#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#13)]  
  
 <span data-ttu-id="cbc47-147">This code displays the following text:</span><span class="sxs-lookup"><span data-stu-id="cbc47-147">This code displays the following text:</span></span>  
  
 `Phone type: work`  
  
## <a name="example"></a><span data-ttu-id="cbc47-148">Przykład</span><span class="sxs-lookup"><span data-stu-id="cbc47-148">Example</span></span>  
 <span data-ttu-id="cbc47-149">The following example declares `ns` as an XML namespace prefix.</span><span class="sxs-lookup"><span data-stu-id="cbc47-149">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="cbc47-150">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name "`ns:name`".</span><span class="sxs-lookup"><span data-stu-id="cbc47-150">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name "`ns:name`".</span></span>  
  
 [!code-vb[VbXMLSamples#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples6.vb#14)]  
  
 <span data-ttu-id="cbc47-151">This code displays the following text:</span><span class="sxs-lookup"><span data-stu-id="cbc47-151">This code displays the following text:</span></span>  
  
 `Phone type: home`  
  
## <a name="see-also"></a><span data-ttu-id="cbc47-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cbc47-152">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="cbc47-153">Właściwości osi XML</span><span class="sxs-lookup"><span data-stu-id="cbc47-153">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)
- [<span data-ttu-id="cbc47-154">Literały XML</span><span class="sxs-lookup"><span data-stu-id="cbc47-154">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="cbc47-155">Creating XML in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cbc47-155">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="cbc47-156">Nazwy deklarowanych elementów i atrybutów XML</span><span class="sxs-lookup"><span data-stu-id="cbc47-156">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
