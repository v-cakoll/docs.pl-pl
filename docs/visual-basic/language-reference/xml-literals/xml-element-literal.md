---
title: Literał elementu XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralElement
helpviewer_keywords:
- XML element literal [Visual Basic]
- element literal [Visual Basic]
- XML literals [Visual Basic], element
ms.assetid: 95039642-7893-48b7-b23f-45a6c55d8f67
ms.openlocfilehash: 7bd47d2461ba86dfbd1d5ff5993382914116f9ba
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842255"
---
# <a name="xml-element-literal-visual-basic"></a><span data-ttu-id="2116e-102">Literał elementu XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2116e-102">XML Element Literal (Visual Basic)</span></span>

<span data-ttu-id="2116e-103">Literał, która reprezentuje <xref:System.Xml.Linq.XElement> obiektu.</span><span class="sxs-lookup"><span data-stu-id="2116e-103">A literal that represents an <xref:System.Xml.Linq.XElement> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2116e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2116e-104">Syntax</span></span>  
  
```xml  
<name [ attributeList ] />  
-or-  
<name [ attributeList ] > [ elementContents ] </[ name ]>  
```  
  
## <a name="parts"></a><span data-ttu-id="2116e-105">Części</span><span class="sxs-lookup"><span data-stu-id="2116e-105">Parts</span></span>  
  
-   `<`  
  
     <span data-ttu-id="2116e-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="2116e-106">Required.</span></span> <span data-ttu-id="2116e-107">Zostanie otwarty początkowego tagu elementu.</span><span class="sxs-lookup"><span data-stu-id="2116e-107">Opens the starting element tag.</span></span>  
  
-   `name`  
  
     <span data-ttu-id="2116e-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="2116e-108">Required.</span></span> <span data-ttu-id="2116e-109">Nazwa elementu.</span><span class="sxs-lookup"><span data-stu-id="2116e-109">Name of the element.</span></span> <span data-ttu-id="2116e-110">Format jest jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="2116e-110">The format is one of the following:</span></span>  
  
    -   <span data-ttu-id="2116e-111">Tekst dosłowny dla nazwy elementu, w postaci `[ePrefix:]eName`, gdzie:</span><span class="sxs-lookup"><span data-stu-id="2116e-111">Literal text for the element name, of the form `[ePrefix:]eName`, where:</span></span>  
  
        |<span data-ttu-id="2116e-112">Część</span><span class="sxs-lookup"><span data-stu-id="2116e-112">Part</span></span>|<span data-ttu-id="2116e-113">Opis</span><span class="sxs-lookup"><span data-stu-id="2116e-113">Description</span></span>|  
        |---|---|  
        |`ePrefix`|<span data-ttu-id="2116e-114">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="2116e-114">Optional.</span></span> <span data-ttu-id="2116e-115">Prefiks przestrzeni nazw XML dla elementu.</span><span class="sxs-lookup"><span data-stu-id="2116e-115">XML namespace prefix for the element.</span></span> <span data-ttu-id="2116e-116">Musi być globalnej przestrzeni nazw XML, która jest zdefiniowana za pomocą `Imports` instrukcja w pliku lub na poziomie projektu lub lokalną przestrzeń nazw XML, który jest zdefiniowany w tym elemencie lub elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="2116e-116">Must be a global XML namespace that is defined with an `Imports` statement in the file or at the project level, or a local XML namespace that is defined in this element or a parent element.</span></span>|  
        |`eName`|<span data-ttu-id="2116e-117">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="2116e-117">Required.</span></span> <span data-ttu-id="2116e-118">Nazwa elementu.</span><span class="sxs-lookup"><span data-stu-id="2116e-118">Name of the element.</span></span> <span data-ttu-id="2116e-119">Format jest jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="2116e-119">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="2116e-120">-Literał tekstowy.</span><span class="sxs-lookup"><span data-stu-id="2116e-120">-   Literal text.</span></span> <span data-ttu-id="2116e-121">Zobacz [nazwy deklarowanych elementów XML oraz atrybuty](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="2116e-121">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span><br /><span data-ttu-id="2116e-122">— Osadzone wyrażenie w formie `<%= eNameExp %>`.</span><span class="sxs-lookup"><span data-stu-id="2116e-122">-   Embedded expression of the form `<%= eNameExp %>`.</span></span> <span data-ttu-id="2116e-123">Typ `eNameExp` musi być `String` lub typ, który jest niejawnie konwertowany na <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="2116e-123">The type of `eNameExp` must be `String` or a type that is implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span>|  
  
    -   <span data-ttu-id="2116e-124">Osadzone wyrażenie w formie `<%= nameExp %>`.</span><span class="sxs-lookup"><span data-stu-id="2116e-124">Embedded expression of the form `<%= nameExp %>`.</span></span> <span data-ttu-id="2116e-125">Typ `nameExp` musi być `String` lub niejawnie konwertowane na typ <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="2116e-125">The type of `nameExp` must be `String` or a type implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span> <span data-ttu-id="2116e-126">Wyrażenia osadzone nie jest dozwolona w tagu zamykającego elementu.</span><span class="sxs-lookup"><span data-stu-id="2116e-126">An embedded expression is not allowed in a closing tag of an element.</span></span>  
  
-   `attributeList`  
  
     <span data-ttu-id="2116e-127">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="2116e-127">Optional.</span></span> <span data-ttu-id="2116e-128">Lista atrybutów zadeklarowany w literału.</span><span class="sxs-lookup"><span data-stu-id="2116e-128">List of attributes declared in the literal.</span></span>  
  
     `attribute [ attribute ... ]`  
  
     <span data-ttu-id="2116e-129">Każdy `attribute` ma jedną z poniższych składni:</span><span class="sxs-lookup"><span data-stu-id="2116e-129">Each `attribute` has one of the following syntaxes:</span></span>  
  
    -   <span data-ttu-id="2116e-130">Atrybut przypisania formularza `[aPrefix:]aName=aValue`, gdzie:</span><span class="sxs-lookup"><span data-stu-id="2116e-130">Attribute assignment, of the form `[aPrefix:]aName=aValue`, where:</span></span>  
  
        |<span data-ttu-id="2116e-131">Część</span><span class="sxs-lookup"><span data-stu-id="2116e-131">Part</span></span>|<span data-ttu-id="2116e-132">Opis</span><span class="sxs-lookup"><span data-stu-id="2116e-132">Description</span></span>|  
        |---|---|  
        |`aPrefix`|<span data-ttu-id="2116e-133">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="2116e-133">Optional.</span></span> <span data-ttu-id="2116e-134">Prefiks przestrzeni nazw XML dla atrybutu.</span><span class="sxs-lookup"><span data-stu-id="2116e-134">XML namespace prefix for the attribute.</span></span> <span data-ttu-id="2116e-135">Musi być globalnej przestrzeni nazw XML, która jest zdefiniowana za pomocą `Imports` instrukcji lub lokalną przestrzeń nazw XML, który jest zdefiniowany w tym elemencie lub elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="2116e-135">Must be a global XML namespace that is defined with an `Imports` statement, or a local XML namespace that is defined in this element or a parent element.</span></span>|  
        |`aName`|<span data-ttu-id="2116e-136">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="2116e-136">Required.</span></span> <span data-ttu-id="2116e-137">Nazwa atrybutu.</span><span class="sxs-lookup"><span data-stu-id="2116e-137">Name of the attribute.</span></span> <span data-ttu-id="2116e-138">Format jest jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="2116e-138">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="2116e-139">-Literał tekstowy.</span><span class="sxs-lookup"><span data-stu-id="2116e-139">-   Literal text.</span></span> <span data-ttu-id="2116e-140">Zobacz [nazwy deklarowanych elementów XML oraz atrybuty](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="2116e-140">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span><br /><span data-ttu-id="2116e-141">— Osadzone wyrażenie w formie `<%= aNameExp %>`.</span><span class="sxs-lookup"><span data-stu-id="2116e-141">-   Embedded expression of the form `<%= aNameExp %>`.</span></span> <span data-ttu-id="2116e-142">Typ `aNameExp` musi być `String` lub typ, który jest niejawnie konwertowany na <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="2116e-142">The type of `aNameExp` must be `String` or a type that is implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span>|  
        |`aValue`|<span data-ttu-id="2116e-143">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="2116e-143">Optional.</span></span> <span data-ttu-id="2116e-144">Wartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="2116e-144">Value of the attribute.</span></span> <span data-ttu-id="2116e-145">Format jest jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="2116e-145">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="2116e-146">— Tekst literał ujęta w znaki cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="2116e-146">-   Literal text, enclosed in quotation marks.</span></span><br /><span data-ttu-id="2116e-147">— Osadzone wyrażenie w formie `<%= aValueExp %>`.</span><span class="sxs-lookup"><span data-stu-id="2116e-147">-   Embedded expression of the form `<%= aValueExp %>`.</span></span> <span data-ttu-id="2116e-148">Dowolny typ jest dozwolone.</span><span class="sxs-lookup"><span data-stu-id="2116e-148">Any type is allowed.</span></span>|  
  
    -   <span data-ttu-id="2116e-149">Osadzone wyrażenie w formie `<%= aExp %>`.</span><span class="sxs-lookup"><span data-stu-id="2116e-149">Embedded expression of the form `<%= aExp %>`.</span></span>  
  
-   `/>`  
  
     <span data-ttu-id="2116e-150">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="2116e-150">Optional.</span></span> <span data-ttu-id="2116e-151">Wskazuje, że element jest elementem pustym, bez zawartości.</span><span class="sxs-lookup"><span data-stu-id="2116e-151">Indicates that the element is an empty element, without content.</span></span>  
  
-   `>`  
  
     <span data-ttu-id="2116e-152">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="2116e-152">Required.</span></span> <span data-ttu-id="2116e-153">Kończy się tagu elementu zaczynające się lub jest pusty.</span><span class="sxs-lookup"><span data-stu-id="2116e-153">Ends the beginning or empty element tag.</span></span>  
  
-   `elementContents`  
  
     <span data-ttu-id="2116e-154">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="2116e-154">Optional.</span></span> <span data-ttu-id="2116e-155">Zawartość elementu.</span><span class="sxs-lookup"><span data-stu-id="2116e-155">Content of the element.</span></span>  
  
     `content [ content ... ]`  
  
     <span data-ttu-id="2116e-156">Każdy `content` może być jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="2116e-156">Each `content` can be one of the following:</span></span>  
  
    -   <span data-ttu-id="2116e-157">Literał tekstowy.</span><span class="sxs-lookup"><span data-stu-id="2116e-157">Literal text.</span></span> <span data-ttu-id="2116e-158">Wszystkie biały znak w `elementContents` staje się istotne, jeśli dowolny tekst literału.</span><span class="sxs-lookup"><span data-stu-id="2116e-158">All the white space in `elementContents` becomes significant if there is any literal text.</span></span>  
  
    -   <span data-ttu-id="2116e-159">Osadzone wyrażenie w formie `<%= contentExp %>`.</span><span class="sxs-lookup"><span data-stu-id="2116e-159">Embedded expression of the form `<%= contentExp %>`.</span></span>  
  
    -   <span data-ttu-id="2116e-160">Literał elementu XML.</span><span class="sxs-lookup"><span data-stu-id="2116e-160">XML element literal.</span></span>  
  
    -   <span data-ttu-id="2116e-161">Literał komentarza XML.</span><span class="sxs-lookup"><span data-stu-id="2116e-161">XML comment literal.</span></span> <span data-ttu-id="2116e-162">Zobacz [literał komentarza XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span><span class="sxs-lookup"><span data-stu-id="2116e-162">See [XML Comment Literal](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span></span>  
  
    -   <span data-ttu-id="2116e-163">Literał instrukcji przetwarzania XML.</span><span class="sxs-lookup"><span data-stu-id="2116e-163">XML processing instruction literal.</span></span> <span data-ttu-id="2116e-164">Zobacz [literał instrukcji przetwarzania XML](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span><span class="sxs-lookup"><span data-stu-id="2116e-164">See [XML Processing Instruction Literal](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span></span>  
  
    -   <span data-ttu-id="2116e-165">Literał CDATA XML.</span><span class="sxs-lookup"><span data-stu-id="2116e-165">XML CDATA literal.</span></span> <span data-ttu-id="2116e-166">Zobacz [literał XML CDATA](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md).</span><span class="sxs-lookup"><span data-stu-id="2116e-166">See [XML CDATA Literal](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md).</span></span>  
  
-   `</[name]>`  
  
     <span data-ttu-id="2116e-167">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="2116e-167">Optional.</span></span> <span data-ttu-id="2116e-168">Reprezentuje tag zamykający dla elementu.</span><span class="sxs-lookup"><span data-stu-id="2116e-168">Represents the closing tag for the element.</span></span> <span data-ttu-id="2116e-169">Opcjonalny `name` parametr nie jest dozwolona, gdy jest wynikiem wyrażenia osadzone.</span><span class="sxs-lookup"><span data-stu-id="2116e-169">The optional `name` parameter is not allowed when it is the result of an embedded expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2116e-170">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2116e-170">Return Value</span></span>  
 <span data-ttu-id="2116e-171"><xref:System.Xml.Linq.XElement> Obiektu.</span><span class="sxs-lookup"><span data-stu-id="2116e-171">An <xref:System.Xml.Linq.XElement> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2116e-172">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2116e-172">Remarks</span></span>  
 <span data-ttu-id="2116e-173">Składnia literał elementu XML służy do tworzenia <xref:System.Xml.Linq.XElement> obiektów w kodzie.</span><span class="sxs-lookup"><span data-stu-id="2116e-173">You can use the XML element literal syntax to create <xref:System.Xml.Linq.XElement> objects in your code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2116e-174">Literał XML może obejmować wiele wierszy, bez używania znaków kontynuacji wiersza.</span><span class="sxs-lookup"><span data-stu-id="2116e-174">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="2116e-175">Ta funkcja pozwala na kopiowanie zawartości z dokumentu XML i wklej go bezpośrednio w programie Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2116e-175">This feature enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="2116e-176">Osadzone wyrażenia formularza `<%= exp %>` umożliwiają dodawanie informacji dynamicznych do literał elementu XML.</span><span class="sxs-lookup"><span data-stu-id="2116e-176">Embedded expressions of the form `<%= exp %>` enable you to add dynamic information to an XML element literal.</span></span> <span data-ttu-id="2116e-177">Aby uzyskać więcej informacji, zobacz [wyrażenia osadzone w XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="2116e-177">For more information, see [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>  
  
 <span data-ttu-id="2116e-178">Kompilator Visual Basic konwertuje literał elementu XML do wywołania <xref:System.Xml.Linq.XElement.%23ctor%2A> Konstruktor i, jeśli jest to konieczne, <xref:System.Xml.Linq.XAttribute.%23ctor%2A> konstruktora.</span><span class="sxs-lookup"><span data-stu-id="2116e-178">The Visual Basic compiler converts the XML element literal into calls to the <xref:System.Xml.Linq.XElement.%23ctor%2A> constructor and, if it is required, the <xref:System.Xml.Linq.XAttribute.%23ctor%2A> constructor.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="2116e-179">Obszary nazw XML</span><span class="sxs-lookup"><span data-stu-id="2116e-179">XML Namespaces</span></span>  
 <span data-ttu-id="2116e-180">Prefiksy przestrzeni nazw XML są przydatne, gdy trzeba utworzyć literałów XML przy użyciu tej samej przestrzeni nazw wiele razy w kodzie elementów.</span><span class="sxs-lookup"><span data-stu-id="2116e-180">XML namespace prefixes are useful when you have to create XML literals with elements from the same namespace many times in code.</span></span> <span data-ttu-id="2116e-181">Możesz użyć globalne prefiksy przestrzeni nazw XML, które definiują przy użyciu `Imports` instrukcji lub lokalnej prefiksy, które definiują przy użyciu `xmlns:xmlPrefix="xmlNamespace"` atrybutu składni.</span><span class="sxs-lookup"><span data-stu-id="2116e-181">You can use global XML namespace prefixes, which you define by using the `Imports` statement, or local prefixes, which you define by using the `xmlns:xmlPrefix="xmlNamespace"` attribute syntax.</span></span> <span data-ttu-id="2116e-182">Aby uzyskać więcej informacji, zobacz [Importy — instrukcja (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="2116e-182">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
 <span data-ttu-id="2116e-183">Zgodnie z regułami zakresu dla przestrzeni nazw XML lokalnej prefiksy mają pierwszeństwo przed globalne prefiksy.</span><span class="sxs-lookup"><span data-stu-id="2116e-183">In accordance with the scoping rules for XML namespaces, local prefixes take precedence over global prefixes.</span></span> <span data-ttu-id="2116e-184">Jednak jeśli literał XML definiuje obszar nazw XML, przestrzeń nazw nie jest dostępne dla wyrażeń, które są wyświetlane w wyrażeniu osadzonych.</span><span class="sxs-lookup"><span data-stu-id="2116e-184">However, if an XML literal defines an XML namespace, that namespace is not available to expressions that appear in an embedded expression.</span></span> <span data-ttu-id="2116e-185">Wyrażenia osadzone mogą uzyskiwać dostęp tylko globalnej przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="2116e-185">The embedded expression can access only the global XML namespace.</span></span>  
  
 <span data-ttu-id="2116e-186">Kompilator Visual Basic konwertuje każdy globalnej przestrzeni nazw XML, używany przez literał XML w jednej definicji lokalną przestrzeń nazw w wygenerowanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="2116e-186">The Visual Basic compiler converts each global XML namespace that is used by an XML literal into a one local namespace definition in the generated code.</span></span> <span data-ttu-id="2116e-187">Globalnej przestrzeni nazw XML, które nie są używane, nie są wyświetlane w wygenerowanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="2116e-187">Global XML namespaces that are not used do not appear in the generated code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2116e-188">Przykład</span><span class="sxs-lookup"><span data-stu-id="2116e-188">Example</span></span>  
 <span data-ttu-id="2116e-189">Poniższy przykład pokazuje, jak utworzyć prosty element XML, który ma dwa pustych elementów zagnieżdżonych.</span><span class="sxs-lookup"><span data-stu-id="2116e-189">The following example shows how to create a simple XML element that has two nested empty elements.</span></span>  
  
 [!code-vb[VbXMLSamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples9.vb#20)]  
  
 <span data-ttu-id="2116e-190">W przykładzie wyświetlono następujący tekst.</span><span class="sxs-lookup"><span data-stu-id="2116e-190">The example displays the following text.</span></span> <span data-ttu-id="2116e-191">Należy zauważyć, że literału zachowuje strukturę pustych elementów.</span><span class="sxs-lookup"><span data-stu-id="2116e-191">Notice that the literal preserves the structure of the empty elements.</span></span>  
  
```xml  
<outer>  
  <inner1></inner1>  
  <inner2 />  
</outer>  
```  
  
## <a name="example"></a><span data-ttu-id="2116e-192">Przykład</span><span class="sxs-lookup"><span data-stu-id="2116e-192">Example</span></span>  
 <span data-ttu-id="2116e-193">Poniższy przykład pokazuje, jak za pomocą wyrażenia osadzone nazwy elementu i utworzyć atrybuty.</span><span class="sxs-lookup"><span data-stu-id="2116e-193">The following example shows how to use embedded expressions to name an element and create attributes.</span></span>  
  
 [!code-vb[VbXMLSamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples9.vb#21)]  
  
 <span data-ttu-id="2116e-194">Ten kod wyświetla następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="2116e-194">This code displays the following text:</span></span>  
  
```xml  
<book isbn="1234" author="My Author" year="1999" title="My Book" />  
```  
  
## <a name="example"></a><span data-ttu-id="2116e-195">Przykład</span><span class="sxs-lookup"><span data-stu-id="2116e-195">Example</span></span>  
 <span data-ttu-id="2116e-196">Poniższy przykład deklaruje `ns` jako prefiks przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="2116e-196">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="2116e-197">Następnie używa prefiksu przestrzeni nazw, aby utworzyć literał XML i wyświetla formularz końcowego elementu.</span><span class="sxs-lookup"><span data-stu-id="2116e-197">It then uses the prefix of the namespace to create an XML literal and displays the element's final form.</span></span>  
  
 [!code-vb[VbXMLSamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples10.vb#22)]  
  
 <span data-ttu-id="2116e-198">Ten kod wyświetla następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="2116e-198">This code displays the following text:</span></span>  
  
```xml  
<ns:outer xmlns:ns="http://SomeNamespace">  
  <ns:middle xmlns:ns="http://NewNamespace">  
    <ns:inner1 />  
    <inner2 xmlns="http://SomeNamespace" />  
  </ns:middle>  
</ns:outer>  
```  
  
 <span data-ttu-id="2116e-199">Należy zauważyć, że kompilator konwertowane prefiks globalnej przestrzeni nazw XML na definicję prefiksu przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="2116e-199">Notice that the compiler converted the prefix of the global XML namespace into a prefix definition for the XML namespace.</span></span> <span data-ttu-id="2116e-200">\<Ns:middle > element redefiniuje prefiks przestrzeni nazw XML dla \<ns:inner1 > element.</span><span class="sxs-lookup"><span data-stu-id="2116e-200">The \<ns:middle> element redefines the XML namespace prefix for the \<ns:inner1> element.</span></span> <span data-ttu-id="2116e-201">Jednak \<ns:inner2 > element korzysta z przestrzenią nazw zdefiniowaną przez `Imports` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="2116e-201">However, the \<ns:inner2> element uses the namespace defined by the `Imports` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2116e-202">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2116e-202">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="2116e-203">Nazwy deklarowanych elementów i atrybutów XML</span><span class="sxs-lookup"><span data-stu-id="2116e-203">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
- [<span data-ttu-id="2116e-204">Literał komentarza XML</span><span class="sxs-lookup"><span data-stu-id="2116e-204">XML Comment Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)
- [<span data-ttu-id="2116e-205">Literał CDATA XML</span><span class="sxs-lookup"><span data-stu-id="2116e-205">XML CDATA Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md)
- [<span data-ttu-id="2116e-206">Literały XML</span><span class="sxs-lookup"><span data-stu-id="2116e-206">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="2116e-207">Tworzenie XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2116e-207">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="2116e-208">Wyrażenia osadzone w XML</span><span class="sxs-lookup"><span data-stu-id="2116e-208">Embedded Expressions in XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [<span data-ttu-id="2116e-209">Imports, instrukcja (przestrzeń nazw XML)</span><span class="sxs-lookup"><span data-stu-id="2116e-209">Imports Statement (XML Namespace)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
