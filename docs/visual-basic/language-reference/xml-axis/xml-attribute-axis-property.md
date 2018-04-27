---
title: Właściwości osi atrybutu XML (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlPropertyAttributeAxis
helpviewer_keywords:
- attribute axis property [Visual Basic]
- Visual Basic code, accessing XML
- XML attribute axis property [Visual Basic]
- XML axis [Visual Basic], attribute
- XML [Visual Basic], accessing
ms.assetid: 7a4777e1-0618-4de9-9510-fb9ace2bf4db
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9968e5de0f8cb45fb896ba43c80d9c9a3ab8ef08
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="xml-attribute-axis-property-visual-basic"></a><span data-ttu-id="f5706-102">Właściwości osi atrybutu XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f5706-102">XML Attribute Axis Property (Visual Basic)</span></span>
<span data-ttu-id="f5706-103">Zapewnia dostęp do wartości atrybutu <xref:System.Xml.Linq.XElement> obiektu lub do pierwszego elementu w kolekcji z <xref:System.Xml.Linq.XElement> obiektów.</span><span class="sxs-lookup"><span data-stu-id="f5706-103">Provides access to the value of an attribute for an <xref:System.Xml.Linq.XElement> object or to the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5706-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f5706-104">Syntax</span></span>  
  
```  
      object.@attribute  
-or-  
object.@<attribute>  
```  
  
## <a name="parts"></a><span data-ttu-id="f5706-105">Części</span><span class="sxs-lookup"><span data-stu-id="f5706-105">Parts</span></span>  
 `object`  
 <span data-ttu-id="f5706-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="f5706-106">Required.</span></span> <span data-ttu-id="f5706-107"><xref:System.Xml.Linq.XElement> Obiekcie lub kolekcji <xref:System.Xml.Linq.XElement> obiektów.</span><span class="sxs-lookup"><span data-stu-id="f5706-107">An <xref:System.Xml.Linq.XElement> object or a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="f5706-108">.@</span><span class="sxs-lookup"><span data-stu-id="f5706-108">.@</span></span>  
 <span data-ttu-id="f5706-109">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="f5706-109">Required.</span></span> <span data-ttu-id="f5706-110">Oznacza początek właściwości osi atrybutu.</span><span class="sxs-lookup"><span data-stu-id="f5706-110">Denotes the start of an attribute axis property.</span></span>  
  
 <  
 <span data-ttu-id="f5706-111">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="f5706-111">Optional.</span></span> <span data-ttu-id="f5706-112">Oznacza początek nazwę atrybutu, gdy `attribute` nie jest prawidłowym identyfikatorem w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f5706-112">Denotes the beginning of the name of the attribute when `attribute` is not a valid identifier in Visual Basic.</span></span>  
  
 `attribute`  
 <span data-ttu-id="f5706-113">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="f5706-113">Required.</span></span> <span data-ttu-id="f5706-114">Nazwa atrybutu, aby uzyskać dostęp w formie [`prefix`:]`name`.</span><span class="sxs-lookup"><span data-stu-id="f5706-114">Name of the attribute to access, of the form [`prefix`:]`name`.</span></span>  
  
|<span data-ttu-id="f5706-115">Część</span><span class="sxs-lookup"><span data-stu-id="f5706-115">Part</span></span>|<span data-ttu-id="f5706-116">Opis</span><span class="sxs-lookup"><span data-stu-id="f5706-116">Description</span></span>|  
|----------|-----------------|  
|`prefix`|<span data-ttu-id="f5706-117">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="f5706-117">Optional.</span></span> <span data-ttu-id="f5706-118">Prefiks przestrzeni nazw XML dla atrybutu.</span><span class="sxs-lookup"><span data-stu-id="f5706-118">XML namespace prefix for the attribute.</span></span> <span data-ttu-id="f5706-119">Musi być globalnej przestrzeni nazw XML zdefiniowany za pomocą `Imports` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="f5706-119">Must be a global XML namespace defined with an `Imports` statement.</span></span>|  
|`name`|<span data-ttu-id="f5706-120">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="f5706-120">Required.</span></span> <span data-ttu-id="f5706-121">Nazwa atrybutu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="f5706-121">Local attribute name.</span></span> <span data-ttu-id="f5706-122">Zobacz [nazwy deklarowanych elementów XML oraz atrybuty](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="f5706-122">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
  
 \>  
 <span data-ttu-id="f5706-123">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="f5706-123">Optional.</span></span> <span data-ttu-id="f5706-124">Oznacza koniec nazwę atrybutu, gdy `attribute` nie jest prawidłowym identyfikatorem w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f5706-124">Denotes the end of the name of the attribute when `attribute` is not a valid identifier in Visual Basic.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f5706-125">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f5706-125">Return Value</span></span>  
 <span data-ttu-id="f5706-126">Ciąg zawierający wartość `attribute`.</span><span class="sxs-lookup"><span data-stu-id="f5706-126">A string that contains the value of `attribute`.</span></span> <span data-ttu-id="f5706-127">Jeśli nazwa atrybutu nie istnieje, `Nothing` jest zwracany.</span><span class="sxs-lookup"><span data-stu-id="f5706-127">If the attribute name does not exist, `Nothing` is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5706-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f5706-128">Remarks</span></span>  
 <span data-ttu-id="f5706-129">Właściwości osi atrybutu XML służy do uzyskania dostępu do wartości atrybutu według nazwy z <xref:System.Xml.Linq.XElement> obiektu lub z pierwszego elementu w kolekcji z <xref:System.Xml.Linq.XElement> obiektów.</span><span class="sxs-lookup"><span data-stu-id="f5706-129">You can use an XML attribute axis property to access the value of an attribute by name from an <xref:System.Xml.Linq.XElement> object or from the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="f5706-130">Można pobrać wartość atrybutu o nazwie lub Dodaj nowy atrybut do elementu, określając nazwę nowej poprzedzone @ identyfikator.</span><span class="sxs-lookup"><span data-stu-id="f5706-130">You can retrieve an attribute value by name, or add a new attribute to an element by specifying a new name preceded by the @ identifier.</span></span>  
  
 <span data-ttu-id="f5706-131">Odwołań do atrybutu XML przy użyciu @ identyfikator, wartość atrybutu jest zwracana jako ciąg znaków i nie trzeba jawnie określać <xref:System.Xml.Linq.XAttribute.Value%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="f5706-131">When you refer to an XML attribute using the @ identifier, the attribute value is returned as a string and you do not need to explicitly specify the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span>  
  
 <span data-ttu-id="f5706-132">Reguły nazewnictwa dotyczące atrybutów XML różnią się od reguł nazewnictwa dla identyfikatorów języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f5706-132">The naming rules for XML attributes differ from the naming rules for Visual Basic identifiers.</span></span> <span data-ttu-id="f5706-133">Aby uzyskać dostęp do atrybutu XML o nazwie, która nie jest prawidłowym identyfikatorem języka Visual Basic, należy wpisać nazwę w nawiasy (\< i >).</span><span class="sxs-lookup"><span data-stu-id="f5706-133">To access an XML attribute that has a name that is not a valid Visual Basic identifier, enclose the name in angle brackets (\< and >).</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="f5706-134">Przestrzenie nazw XML</span><span class="sxs-lookup"><span data-stu-id="f5706-134">XML Namespaces</span></span>  
 <span data-ttu-id="f5706-135">Nazwa właściwości osi atrybutu można użyć tylko takie prefiksy przestrzeni nazw XML, zadeklarowany globalnie za pomocą `Imports` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="f5706-135">The name in an attribute axis property can use only XML namespace prefixes declared globally by using the `Imports` statement.</span></span> <span data-ttu-id="f5706-136">Nie można go użyć lokalnie zadeklarowane w literałach XML elementu prefiksy przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="f5706-136">It cannot use XML namespace prefixes declared locally within XML element literals.</span></span> <span data-ttu-id="f5706-137">Aby uzyskać więcej informacji, zobacz [Importy — instrukcja (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="f5706-137">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5706-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="f5706-138">Example</span></span>  
 <span data-ttu-id="f5706-139">Poniższy przykład pokazuje, jak można pobrać wartości atrybutów XML o nazwie `type` z kolekcji elementów XML, które są nazywane `phone`.</span><span class="sxs-lookup"><span data-stu-id="f5706-139">The following example shows how to get the values of the XML attributes named `type` from a collection of XML elements that are named `phone`.</span></span>  
  
 [!code-vb[VbXMLSamples#12](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_1.vb)]  
  
 <span data-ttu-id="f5706-140">Ten kod zawiera następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="f5706-140">This code displays the following text:</span></span>  
  
 `<phoneTypes>`  
  
 `<type>home</type>`  
  
 `<type>work</type>`  
  
 `</phoneTypes>`  
  
## <a name="example"></a><span data-ttu-id="f5706-141">Przykład</span><span class="sxs-lookup"><span data-stu-id="f5706-141">Example</span></span>  
 <span data-ttu-id="f5706-142">Poniższy przykład przedstawia deklaratywnie jako część pliku XML i dynamicznie przez dodanie atrybutu do wystąpienia utworzyć atrybuty elementu XML zarówno <xref:System.Xml.Linq.XElement> obiektu.</span><span class="sxs-lookup"><span data-stu-id="f5706-142">The following example shows how to create attributes for an XML element both declaratively, as part of the XML, and dynamically by adding an attribute to an instance of an <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="f5706-143">`type` Deklaratywnie utworzyć atrybutu i `owner` dynamicznie utworzyć atrybutu.</span><span class="sxs-lookup"><span data-stu-id="f5706-143">The `type` attribute is created declaratively and the `owner` attribute is created dynamically.</span></span>  
  
 [!code-vb[VbXMLSamples#44](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_2.vb)]  
  
 <span data-ttu-id="f5706-144">Ten kod zawiera następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="f5706-144">This code displays the following text:</span></span>  
  
```xml  
<phone type="home" owner="Harris, Phyllis">206-555-0144</phone>  
```  
  
## <a name="example"></a><span data-ttu-id="f5706-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="f5706-145">Example</span></span>  
 <span data-ttu-id="f5706-146">W poniższym przykładzie użyto składni nawiasu ostrego można pobrać wartości atrybutu XML o nazwie `number-type`, która nie jest prawidłowym identyfikatorem w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f5706-146">The following example uses the angle bracket syntax to get the value of the XML attribute named `number-type`, which is not a valid identifier in Visual Basic.</span></span>  
  
 [!code-vb[VbXMLSamples#13](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_3.vb)]  
  
 <span data-ttu-id="f5706-147">Ten kod zawiera następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="f5706-147">This code displays the following text:</span></span>  
  
 `Phone type: work`  
  
## <a name="example"></a><span data-ttu-id="f5706-148">Przykład</span><span class="sxs-lookup"><span data-stu-id="f5706-148">Example</span></span>  
 <span data-ttu-id="f5706-149">Poniższy przykład deklaruje `ns` jako prefiks przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="f5706-149">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="f5706-150">Następnie używa prefiks przestrzeni nazw do utworzenia literału XML i dostępu do pierwszy węzeł podrzędny o nazwie kwalifikowanej "`ns:name`".</span><span class="sxs-lookup"><span data-stu-id="f5706-150">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name "`ns:name`".</span></span>  
  
 [!code-vb[VbXMLSamples#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_4.vb)]  
  
 <span data-ttu-id="f5706-151">Ten kod zawiera następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="f5706-151">This code displays the following text:</span></span>  
  
 `Phone type: home`  
  
## <a name="see-also"></a><span data-ttu-id="f5706-152">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f5706-152">See Also</span></span>  
 <xref:System.Xml.Linq.XElement>  
 [<span data-ttu-id="f5706-153">Właściwości osi XML</span><span class="sxs-lookup"><span data-stu-id="f5706-153">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [<span data-ttu-id="f5706-154">Literały XML</span><span class="sxs-lookup"><span data-stu-id="f5706-154">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="f5706-155">Tworzenie XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f5706-155">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="f5706-156">Nazwy deklarowanych elementów i atrybutów XML</span><span class="sxs-lookup"><span data-stu-id="f5706-156">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
