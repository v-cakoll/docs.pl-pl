---
title: Właściwości osi atrybutu XML (Visual Basic)
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
ms.openlocfilehash: cfc18df4487488bd90d7b0250a9053f55305d8a8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54631503"
---
# <a name="xml-attribute-axis-property-visual-basic"></a><span data-ttu-id="d2570-102">Właściwości osi atrybutu XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d2570-102">XML Attribute Axis Property (Visual Basic)</span></span>
<span data-ttu-id="d2570-103">Zapewnia dostęp do wartości atrybutu dla <xref:System.Xml.Linq.XElement> obiektu lub do pierwszego elementu w kolekcji <xref:System.Xml.Linq.XElement> obiektów.</span><span class="sxs-lookup"><span data-stu-id="d2570-103">Provides access to the value of an attribute for an <xref:System.Xml.Linq.XElement> object or to the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2570-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d2570-104">Syntax</span></span>  
  
```  
      object.@attribute  
-or-  
object.@<attribute>  
```  
  
## <a name="parts"></a><span data-ttu-id="d2570-105">Części</span><span class="sxs-lookup"><span data-stu-id="d2570-105">Parts</span></span>  
 `object`  
 <span data-ttu-id="d2570-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="d2570-106">Required.</span></span> <span data-ttu-id="d2570-107"><xref:System.Xml.Linq.XElement> Obiekt lub kolekcję <xref:System.Xml.Linq.XElement> obiektów.</span><span class="sxs-lookup"><span data-stu-id="d2570-107">An <xref:System.Xml.Linq.XElement> object or a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="d2570-108">.@</span><span class="sxs-lookup"><span data-stu-id="d2570-108">.@</span></span>  
 <span data-ttu-id="d2570-109">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="d2570-109">Required.</span></span> <span data-ttu-id="d2570-110">Oznacza początek właściwości osi atrybutu.</span><span class="sxs-lookup"><span data-stu-id="d2570-110">Denotes the start of an attribute axis property.</span></span>  
  
 <  
 <span data-ttu-id="d2570-111">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="d2570-111">Optional.</span></span> <span data-ttu-id="d2570-112">Oznacza początek nazwę atrybutu, gdy `attribute` nie jest prawidłowym identyfikatorem w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d2570-112">Denotes the beginning of the name of the attribute when `attribute` is not a valid identifier in Visual Basic.</span></span>  
  
 `attribute`  
 <span data-ttu-id="d2570-113">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="d2570-113">Required.</span></span> <span data-ttu-id="d2570-114">Nazwa atrybutu, aby uzyskać dostęp, w postaci [`prefix`:]`name`.</span><span class="sxs-lookup"><span data-stu-id="d2570-114">Name of the attribute to access, of the form [`prefix`:]`name`.</span></span>  
  
|<span data-ttu-id="d2570-115">Część</span><span class="sxs-lookup"><span data-stu-id="d2570-115">Part</span></span>|<span data-ttu-id="d2570-116">Opis</span><span class="sxs-lookup"><span data-stu-id="d2570-116">Description</span></span>|  
|----------|-----------------|  
|`prefix`|<span data-ttu-id="d2570-117">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="d2570-117">Optional.</span></span> <span data-ttu-id="d2570-118">Prefiks przestrzeni nazw XML dla atrybutu.</span><span class="sxs-lookup"><span data-stu-id="d2570-118">XML namespace prefix for the attribute.</span></span> <span data-ttu-id="d2570-119">Musi być globalnej przestrzeni nazw XML zdefiniowana z `Imports` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="d2570-119">Must be a global XML namespace defined with an `Imports` statement.</span></span>|  
|`name`|<span data-ttu-id="d2570-120">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="d2570-120">Required.</span></span> <span data-ttu-id="d2570-121">Nazwa atrybutu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="d2570-121">Local attribute name.</span></span> <span data-ttu-id="d2570-122">Zobacz [nazwy deklarowanych elementów XML oraz atrybuty](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="d2570-122">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
  
 \>  
 <span data-ttu-id="d2570-123">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="d2570-123">Optional.</span></span> <span data-ttu-id="d2570-124">Oznacza koniec nazwę atrybutu, gdy `attribute` nie jest prawidłowym identyfikatorem w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d2570-124">Denotes the end of the name of the attribute when `attribute` is not a valid identifier in Visual Basic.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d2570-125">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d2570-125">Return Value</span></span>  
 <span data-ttu-id="d2570-126">Ciąg, który zawiera wartość `attribute`.</span><span class="sxs-lookup"><span data-stu-id="d2570-126">A string that contains the value of `attribute`.</span></span> <span data-ttu-id="d2570-127">Jeśli nazwa atrybutu nie istnieje, `Nothing` jest zwracana.</span><span class="sxs-lookup"><span data-stu-id="d2570-127">If the attribute name does not exist, `Nothing` is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d2570-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d2570-128">Remarks</span></span>  
 <span data-ttu-id="d2570-129">Właściwości osi atrybutu XML umożliwia dostęp do wartości atrybutu za pomocą nazwy z <xref:System.Xml.Linq.XElement> obiektu lub od pierwszego elementu w kolekcji <xref:System.Xml.Linq.XElement> obiektów.</span><span class="sxs-lookup"><span data-stu-id="d2570-129">You can use an XML attribute axis property to access the value of an attribute by name from an <xref:System.Xml.Linq.XElement> object or from the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="d2570-130">Pobrać wartość atrybutu według nazwy lub dodać nowy atrybut do elementu, określając nowy nazwę poprzedzoną znakiem @ identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="d2570-130">You can retrieve an attribute value by name, or add a new attribute to an element by specifying a new name preceded by the @ identifier.</span></span>  
  
 <span data-ttu-id="d2570-131">Gdy odwołasz się do atrybutu XML przy użyciu @ identyfikator, wartość atrybutu jest zwracany jako ciąg znaków i nie trzeba jawnie określić <xref:System.Xml.Linq.XAttribute.Value%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="d2570-131">When you refer to an XML attribute using the @ identifier, the attribute value is returned as a string and you do not need to explicitly specify the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span>  
  
 <span data-ttu-id="d2570-132">Reguły nazewnictwa dotyczące atrybutów XML różnią się od reguł nazewnictwa identyfikatorów języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d2570-132">The naming rules for XML attributes differ from the naming rules for Visual Basic identifiers.</span></span> <span data-ttu-id="d2570-133">Aby uzyskać dostęp do atrybutu XML, który ma nazwę, która nie jest prawidłowym identyfikatorem języka Visual Basic, należy wpisać nazwę w nawiasy ostre (\< i >).</span><span class="sxs-lookup"><span data-stu-id="d2570-133">To access an XML attribute that has a name that is not a valid Visual Basic identifier, enclose the name in angle brackets (\< and >).</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="d2570-134">Obszary nazw XML</span><span class="sxs-lookup"><span data-stu-id="d2570-134">XML Namespaces</span></span>  
 <span data-ttu-id="d2570-135">Nazwa właściwości osi atrybutu można używać tylko takie prefiksy przestrzeni nazw XML, globalnie zadeklarowane za pomocą `Imports` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="d2570-135">The name in an attribute axis property can use only XML namespace prefixes declared globally by using the `Imports` statement.</span></span> <span data-ttu-id="d2570-136">Nie można go używać prefiksy przestrzeni nazw XML zadeklarowany lokalnie w literałach — element XML.</span><span class="sxs-lookup"><span data-stu-id="d2570-136">It cannot use XML namespace prefixes declared locally within XML element literals.</span></span> <span data-ttu-id="d2570-137">Aby uzyskać więcej informacji, zobacz [Importy — instrukcja (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="d2570-137">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2570-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="d2570-138">Example</span></span>  
 <span data-ttu-id="d2570-139">Poniższy przykład pokazuje, jak można pobrać wartości atrybutów XML o nazwie `type` z kolekcji elementów XML, które są nazwane `phone`.</span><span class="sxs-lookup"><span data-stu-id="d2570-139">The following example shows how to get the values of the XML attributes named `type` from a collection of XML elements that are named `phone`.</span></span>  
  
 [!code-vb[VbXMLSamples#12](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_1.vb)]  
  
 <span data-ttu-id="d2570-140">Ten kod wyświetla następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="d2570-140">This code displays the following text:</span></span>  
  
 `<phoneTypes>`  
  
 `<type>home</type>`  
  
 `<type>work</type>`  
  
 `</phoneTypes>`  
  
## <a name="example"></a><span data-ttu-id="d2570-141">Przykład</span><span class="sxs-lookup"><span data-stu-id="d2570-141">Example</span></span>  
 <span data-ttu-id="d2570-142">Poniższy przykład pokazuje, jak Utwórz atrybuty dla elementu XML zarówno deklaratywnie w ramach XML i dynamicznie przez dodawanie atrybutu do wystąpienia <xref:System.Xml.Linq.XElement> obiektu.</span><span class="sxs-lookup"><span data-stu-id="d2570-142">The following example shows how to create attributes for an XML element both declaratively, as part of the XML, and dynamically by adding an attribute to an instance of an <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="d2570-143">`type` Atrybut jest tworzony w sposób deklaratywny i `owner` atrybutu jest tworzony dynamicznie.</span><span class="sxs-lookup"><span data-stu-id="d2570-143">The `type` attribute is created declaratively and the `owner` attribute is created dynamically.</span></span>  
  
 [!code-vb[VbXMLSamples#44](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_2.vb)]  
  
 <span data-ttu-id="d2570-144">Ten kod wyświetla następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="d2570-144">This code displays the following text:</span></span>  
  
```xml  
<phone type="home" owner="Harris, Phyllis">206-555-0144</phone>  
```  
  
## <a name="example"></a><span data-ttu-id="d2570-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="d2570-145">Example</span></span>  
 <span data-ttu-id="d2570-146">W poniższym przykładzie użyto składnię nawiasu ostrego, aby uzyskać wartość atrybutu XML o nazwie `number-type`, który nie jest prawidłowym identyfikatorem w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d2570-146">The following example uses the angle bracket syntax to get the value of the XML attribute named `number-type`, which is not a valid identifier in Visual Basic.</span></span>  
  
 [!code-vb[VbXMLSamples#13](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_3.vb)]  
  
 <span data-ttu-id="d2570-147">Ten kod wyświetla następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="d2570-147">This code displays the following text:</span></span>  
  
 `Phone type: work`  
  
## <a name="example"></a><span data-ttu-id="d2570-148">Przykład</span><span class="sxs-lookup"><span data-stu-id="d2570-148">Example</span></span>  
 <span data-ttu-id="d2570-149">Poniższy przykład deklaruje `ns` jako prefiks przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="d2570-149">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="d2570-150">Następnie używa prefiksu przestrzeni nazw tworzenie literałów XML i dostępem pierwszy węzeł podrzędny o kwalifikowanej nazwie "`ns:name`".</span><span class="sxs-lookup"><span data-stu-id="d2570-150">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name "`ns:name`".</span></span>  
  
 [!code-vb[VbXMLSamples#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_4.vb)]  
  
 <span data-ttu-id="d2570-151">Ten kod wyświetla następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="d2570-151">This code displays the following text:</span></span>  
  
 `Phone type: home`  
  
## <a name="see-also"></a><span data-ttu-id="d2570-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d2570-152">See also</span></span>
- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="d2570-153">Właściwości osi XML</span><span class="sxs-lookup"><span data-stu-id="d2570-153">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)
- [<span data-ttu-id="d2570-154">Literały XML</span><span class="sxs-lookup"><span data-stu-id="d2570-154">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="d2570-155">Tworzenie XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d2570-155">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="d2570-156">Nazwy deklarowanych elementów i atrybutów XML</span><span class="sxs-lookup"><span data-stu-id="d2570-156">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
