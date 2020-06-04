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
ms.openlocfilehash: 3f60190a949856cb2bbc2eba09d097c09089bea7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408435"
---
# <a name="xml-attribute-axis-property-visual-basic"></a><span data-ttu-id="961a8-102">Właściwości osi atrybutu XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="961a8-102">XML Attribute Axis Property (Visual Basic)</span></span>
<span data-ttu-id="961a8-103">Zapewnia dostęp do wartości atrybutu dla <xref:System.Xml.Linq.XElement> obiektu lub do pierwszego elementu w kolekcji <xref:System.Xml.Linq.XElement> obiektów.</span><span class="sxs-lookup"><span data-stu-id="961a8-103">Provides access to the value of an attribute for an <xref:System.Xml.Linq.XElement> object or to the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="961a8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="961a8-104">Syntax</span></span>  
  
```vb  
object.@attribute  
' -or-  
object.@<attribute>  
```  
  
## <a name="parts"></a><span data-ttu-id="961a8-105">Części</span><span class="sxs-lookup"><span data-stu-id="961a8-105">Parts</span></span>  
 `object`  
 <span data-ttu-id="961a8-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="961a8-106">Required.</span></span> <span data-ttu-id="961a8-107"><xref:System.Xml.Linq.XElement>Obiekt lub kolekcja <xref:System.Xml.Linq.XElement> obiektów.</span><span class="sxs-lookup"><span data-stu-id="961a8-107">An <xref:System.Xml.Linq.XElement> object or a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="961a8-108">.@</span><span class="sxs-lookup"><span data-stu-id="961a8-108">.@</span></span>  
 <span data-ttu-id="961a8-109">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="961a8-109">Required.</span></span> <span data-ttu-id="961a8-110">Wskazuje początek właściwości osi atrybutu.</span><span class="sxs-lookup"><span data-stu-id="961a8-110">Denotes the start of an attribute axis property.</span></span>  
  
 <  
 <span data-ttu-id="961a8-111">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="961a8-111">Optional.</span></span> <span data-ttu-id="961a8-112">Oznacza początek nazwy atrybutu, gdy `attribute` nie jest prawidłowym identyfikatorem w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="961a8-112">Denotes the beginning of the name of the attribute when `attribute` is not a valid identifier in Visual Basic.</span></span>  
  
 `attribute`  
 <span data-ttu-id="961a8-113">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="961a8-113">Required.</span></span> <span data-ttu-id="961a8-114">Nazwa atrybutu do uzyskania dostępu w postaci [ `prefix` :] `name` .</span><span class="sxs-lookup"><span data-stu-id="961a8-114">Name of the attribute to access, of the form [`prefix`:]`name`.</span></span>  
  
|<span data-ttu-id="961a8-115">Część</span><span class="sxs-lookup"><span data-stu-id="961a8-115">Part</span></span>|<span data-ttu-id="961a8-116">Opis</span><span class="sxs-lookup"><span data-stu-id="961a8-116">Description</span></span>|  
|----------|-----------------|  
|`prefix`|<span data-ttu-id="961a8-117">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="961a8-117">Optional.</span></span> <span data-ttu-id="961a8-118">Prefiks przestrzeni nazw XML dla atrybutu.</span><span class="sxs-lookup"><span data-stu-id="961a8-118">XML namespace prefix for the attribute.</span></span> <span data-ttu-id="961a8-119">Musi być globalną przestrzenią nazw XML zdefiniowaną za pomocą `Imports` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="961a8-119">Must be a global XML namespace defined with an `Imports` statement.</span></span>|  
|`name`|<span data-ttu-id="961a8-120">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="961a8-120">Required.</span></span> <span data-ttu-id="961a8-121">Nazwa atrybutu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="961a8-121">Local attribute name.</span></span> <span data-ttu-id="961a8-122">Zobacz [nazwy zadeklarowanych elementów i atrybutów XML](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="961a8-122">See [Names of Declared XML Elements and Attributes](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
  
 \>  
 <span data-ttu-id="961a8-123">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="961a8-123">Optional.</span></span> <span data-ttu-id="961a8-124">Oznacza koniec nazwy atrybutu, gdy `attribute` nie jest prawidłowym identyfikatorem w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="961a8-124">Denotes the end of the name of the attribute when `attribute` is not a valid identifier in Visual Basic.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="961a8-125">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="961a8-125">Return Value</span></span>  
 <span data-ttu-id="961a8-126">Ciąg, który zawiera wartość `attribute` .</span><span class="sxs-lookup"><span data-stu-id="961a8-126">A string that contains the value of `attribute`.</span></span> <span data-ttu-id="961a8-127">Jeśli nazwa atrybutu nie istnieje, `Nothing` jest zwracana.</span><span class="sxs-lookup"><span data-stu-id="961a8-127">If the attribute name does not exist, `Nothing` is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="961a8-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="961a8-128">Remarks</span></span>  
 <span data-ttu-id="961a8-129">Można użyć właściwości osi atrybutu XML, aby uzyskać dostęp do wartości atrybutu według nazwy z <xref:System.Xml.Linq.XElement> obiektu lub z pierwszego elementu w kolekcji <xref:System.Xml.Linq.XElement> obiektów.</span><span class="sxs-lookup"><span data-stu-id="961a8-129">You can use an XML attribute axis property to access the value of an attribute by name from an <xref:System.Xml.Linq.XElement> object or from the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="961a8-130">Możesz pobrać wartość atrybutu według nazwy lub dodać nowy atrybut do elementu, określając nową nazwę poprzedzoną identyfikatorem @.</span><span class="sxs-lookup"><span data-stu-id="961a8-130">You can retrieve an attribute value by name, or add a new attribute to an element by specifying a new name preceded by the @ identifier.</span></span>  
  
 <span data-ttu-id="961a8-131">W przypadku odwoływania się do atrybutu XML przy użyciu @ identyfikatora wartość atrybutu jest zwracana jako ciąg i nie trzeba jawnie określać <xref:System.Xml.Linq.XAttribute.Value%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="961a8-131">When you refer to an XML attribute using the @ identifier, the attribute value is returned as a string and you do not need to explicitly specify the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span>  
  
 <span data-ttu-id="961a8-132">Reguły nazewnictwa dla atrybutów XML różnią się od reguł nazewnictwa dla identyfikatorów Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="961a8-132">The naming rules for XML attributes differ from the naming rules for Visual Basic identifiers.</span></span> <span data-ttu-id="961a8-133">Aby uzyskać dostęp do atrybutu XML o nazwie, która nie jest prawidłowym identyfikatorem Visual Basic, ujmij ją w nawiasy kątowe ( \< and > ).</span><span class="sxs-lookup"><span data-stu-id="961a8-133">To access an XML attribute that has a name that is not a valid Visual Basic identifier, enclose the name in angle brackets (\< and >).</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="961a8-134">Przestrzenie nazw XML</span><span class="sxs-lookup"><span data-stu-id="961a8-134">XML Namespaces</span></span>  
 <span data-ttu-id="961a8-135">Nazwa we właściwości osi atrybutu może używać tylko prefiksów przestrzeni nazw XML zadeklarowanych globalnie przy użyciu `Imports` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="961a8-135">The name in an attribute axis property can use only XML namespace prefixes declared globally by using the `Imports` statement.</span></span> <span data-ttu-id="961a8-136">Nie może używać prefiksów przestrzeni nazw XML zadeklarowanych lokalnie w literałach elementu XML.</span><span class="sxs-lookup"><span data-stu-id="961a8-136">It cannot use XML namespace prefixes declared locally within XML element literals.</span></span> <span data-ttu-id="961a8-137">Aby uzyskać więcej informacji, zobacz [Imports — Instrukcja (przestrzeń nazw XML)](../statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="961a8-137">For more information, see [Imports Statement (XML Namespace)](../statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="961a8-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="961a8-138">Example</span></span>  
 <span data-ttu-id="961a8-139">Poniższy przykład pokazuje, jak pobrać wartości atrybutów XML o nazwie `type` z kolekcji elementów XML o nazwie `phone` .</span><span class="sxs-lookup"><span data-stu-id="961a8-139">The following example shows how to get the values of the XML attributes named `type` from a collection of XML elements that are named `phone`.</span></span>  
  
 [!code-vb[VbXMLSamples#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#12)]  
  
 <span data-ttu-id="961a8-140">Ten kod wyświetla następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="961a8-140">This code displays the following text:</span></span>  
  
 `<phoneTypes>`  
  
 `<type>home</type>`  
  
 `<type>work</type>`  
  
 `</phoneTypes>`  
  
## <a name="example"></a><span data-ttu-id="961a8-141">Przykład</span><span class="sxs-lookup"><span data-stu-id="961a8-141">Example</span></span>  
 <span data-ttu-id="961a8-142">Poniższy przykład pokazuje, jak utworzyć atrybuty dla elementu XML w sposób deklaratywny, jako część pliku XML i dynamicznie przez dodanie atrybutu do wystąpienia <xref:System.Xml.Linq.XElement> obiektu.</span><span class="sxs-lookup"><span data-stu-id="961a8-142">The following example shows how to create attributes for an XML element both declaratively, as part of the XML, and dynamically by adding an attribute to an instance of an <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="961a8-143">Ten `type` atrybut jest tworzony deklaratywnie, a `owner` atrybut jest tworzony dynamicznie.</span><span class="sxs-lookup"><span data-stu-id="961a8-143">The `type` attribute is created declaratively and the `owner` attribute is created dynamically.</span></span>  
  
 [!code-vb[VbXMLSamples#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#44)]  
  
 <span data-ttu-id="961a8-144">Ten kod wyświetla następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="961a8-144">This code displays the following text:</span></span>  
  
```xml  
<phone type="home" owner="Harris, Phyllis">206-555-0144</phone>  
```  
  
## <a name="example"></a><span data-ttu-id="961a8-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="961a8-145">Example</span></span>  
 <span data-ttu-id="961a8-146">W poniższym przykładzie użyto składni nawiasu ostrego, aby uzyskać wartość atrybutu XML o nazwie `number-type` , który nie jest prawidłowym identyfikatorem w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="961a8-146">The following example uses the angle bracket syntax to get the value of the XML attribute named `number-type`, which is not a valid identifier in Visual Basic.</span></span>  
  
 [!code-vb[VbXMLSamples#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#13)]  
  
 <span data-ttu-id="961a8-147">Ten kod wyświetla następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="961a8-147">This code displays the following text:</span></span>  
  
 `Phone type: work`  
  
## <a name="example"></a><span data-ttu-id="961a8-148">Przykład</span><span class="sxs-lookup"><span data-stu-id="961a8-148">Example</span></span>  
 <span data-ttu-id="961a8-149">Poniższy przykład deklaruje `ns` jako prefiks przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="961a8-149">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="961a8-150">Następnie używa prefiksu przestrzeni nazw w celu utworzenia literału XML i uzyskania dostępu do pierwszego węzła podrzędnego przy użyciu kwalifikowanej nazwy " `ns:name` ".</span><span class="sxs-lookup"><span data-stu-id="961a8-150">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name "`ns:name`".</span></span>  
  
 [!code-vb[VbXMLSamples#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples6.vb#14)]  
  
 <span data-ttu-id="961a8-151">Ten kod wyświetla następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="961a8-151">This code displays the following text:</span></span>  
  
 `Phone type: home`  
  
## <a name="see-also"></a><span data-ttu-id="961a8-152">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="961a8-152">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="961a8-153">Właściwości osi XML</span><span class="sxs-lookup"><span data-stu-id="961a8-153">XML Axis Properties</span></span>](index.md)
- [<span data-ttu-id="961a8-154">Literały XML</span><span class="sxs-lookup"><span data-stu-id="961a8-154">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="961a8-155">Tworzenie XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="961a8-155">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="961a8-156">Nazwy deklarowanych elementów XML oraz atrybuty</span><span class="sxs-lookup"><span data-stu-id="961a8-156">Names of Declared XML Elements and Attributes</span></span>](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
