---
title: Literał elementu XML
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralElement
helpviewer_keywords:
- XML element literal [Visual Basic]
- element literal [Visual Basic]
- XML literals [Visual Basic], element
ms.assetid: 95039642-7893-48b7-b23f-45a6c55d8f67
ms.openlocfilehash: d6a91de4e279816bafd29f46bb4f5422cbd934ff
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400192"
---
# <a name="xml-element-literal-visual-basic"></a><span data-ttu-id="2b4d2-102">Literał elementu XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2b4d2-102">XML Element Literal (Visual Basic)</span></span>

<span data-ttu-id="2b4d2-103">Literał reprezentujący <xref:System.Xml.Linq.XElement> obiekt.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-103">A literal that represents an <xref:System.Xml.Linq.XElement> object.</span></span>

## <a name="syntax"></a><span data-ttu-id="2b4d2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2b4d2-104">Syntax</span></span>

```xml
<name [ attributeList ] />
-or-
<name [ attributeList ] > [ elementContents ] </[ name ]>
```

## <a name="parts"></a><span data-ttu-id="2b4d2-105">Części</span><span class="sxs-lookup"><span data-stu-id="2b4d2-105">Parts</span></span>

- `<`

  <span data-ttu-id="2b4d2-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-106">Required.</span></span> <span data-ttu-id="2b4d2-107">Otwiera tag elementu początkowego.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-107">Opens the starting element tag.</span></span>

- `name`

  <span data-ttu-id="2b4d2-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-108">Required.</span></span> <span data-ttu-id="2b4d2-109">Nazwa elementu.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-109">Name of the element.</span></span> <span data-ttu-id="2b4d2-110">Jest to jeden z następujących formatów:</span><span class="sxs-lookup"><span data-stu-id="2b4d2-110">The format is one of the following:</span></span>

  - <span data-ttu-id="2b4d2-111">Tekst literału dla nazwy elementu w formularzu `[ePrefix:]eName` , gdzie:</span><span class="sxs-lookup"><span data-stu-id="2b4d2-111">Literal text for the element name, of the form `[ePrefix:]eName`, where:</span></span>

    |<span data-ttu-id="2b4d2-112">Część</span><span class="sxs-lookup"><span data-stu-id="2b4d2-112">Part</span></span>|<span data-ttu-id="2b4d2-113">Opis</span><span class="sxs-lookup"><span data-stu-id="2b4d2-113">Description</span></span>|
    |---|---|
    |`ePrefix`|<span data-ttu-id="2b4d2-114">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-114">Optional.</span></span> <span data-ttu-id="2b4d2-115">Prefiks przestrzeni nazw XML dla elementu.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-115">XML namespace prefix for the element.</span></span> <span data-ttu-id="2b4d2-116">Musi to być globalna przestrzeń nazw XML zdefiniowana za pomocą `Imports` instrukcji w pliku lub na poziomie projektu lub lokalnego obszaru nazw XML zdefiniowanego w tym elemencie lub elemencie nadrzędnym.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-116">Must be a global XML namespace that is defined with an `Imports` statement in the file or at the project level, or a local XML namespace that is defined in this element or a parent element.</span></span>|
    |`eName`|<span data-ttu-id="2b4d2-117">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-117">Required.</span></span> <span data-ttu-id="2b4d2-118">Nazwa elementu.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-118">Name of the element.</span></span> <span data-ttu-id="2b4d2-119">Jest to jeden z następujących formatów:</span><span class="sxs-lookup"><span data-stu-id="2b4d2-119">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="2b4d2-120">-Literal Text.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-120">- Literal text.</span></span> <span data-ttu-id="2b4d2-121">Zobacz [nazwy zadeklarowanych elementów i atrybutów XML](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="2b4d2-121">See [Names of Declared XML Elements and Attributes](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span><br /><span data-ttu-id="2b4d2-122">-Osadzone wyrażenie formularza `<%= eNameExp %>` .</span><span class="sxs-lookup"><span data-stu-id="2b4d2-122">- Embedded expression of the form `<%= eNameExp %>`.</span></span> <span data-ttu-id="2b4d2-123">Typ `eNameExp` musi być `String` lub typem, który jest niejawnie konwertowany na <xref:System.Xml.Linq.XName> .</span><span class="sxs-lookup"><span data-stu-id="2b4d2-123">The type of `eNameExp` must be `String` or a type that is implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span>|

  - <span data-ttu-id="2b4d2-124">Wyrażenie osadzone formularza `<%= nameExp %>` .</span><span class="sxs-lookup"><span data-stu-id="2b4d2-124">Embedded expression of the form `<%= nameExp %>`.</span></span> <span data-ttu-id="2b4d2-125">Typ elementu `nameExp` musi być `String` lub typem niejawnie konwertowanym na <xref:System.Xml.Linq.XName> .</span><span class="sxs-lookup"><span data-stu-id="2b4d2-125">The type of `nameExp` must be `String` or a type implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span> <span data-ttu-id="2b4d2-126">Wyrażenie osadzone jest niedozwolone w tagu zamykającym elementu.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-126">An embedded expression is not allowed in a closing tag of an element.</span></span>

- `attributeList`

  <span data-ttu-id="2b4d2-127">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-127">Optional.</span></span> <span data-ttu-id="2b4d2-128">Lista atrybutów zadeklarowanych w literale.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-128">List of attributes declared in the literal.</span></span>

  `attribute [ attribute ... ]`

  <span data-ttu-id="2b4d2-129">Każda `attribute` z nich ma jedną z następujących składni:</span><span class="sxs-lookup"><span data-stu-id="2b4d2-129">Each `attribute` has one of the following syntaxes:</span></span>

  - <span data-ttu-id="2b4d2-130">Przypisanie atrybutu w formularzu `[aPrefix:]aName=aValue` , gdzie:</span><span class="sxs-lookup"><span data-stu-id="2b4d2-130">Attribute assignment, of the form `[aPrefix:]aName=aValue`, where:</span></span>

    |<span data-ttu-id="2b4d2-131">Część</span><span class="sxs-lookup"><span data-stu-id="2b4d2-131">Part</span></span>|<span data-ttu-id="2b4d2-132">Opis</span><span class="sxs-lookup"><span data-stu-id="2b4d2-132">Description</span></span>|
    |---|---|
    |`aPrefix`|<span data-ttu-id="2b4d2-133">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-133">Optional.</span></span> <span data-ttu-id="2b4d2-134">Prefiks przestrzeni nazw XML dla atrybutu.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-134">XML namespace prefix for the attribute.</span></span> <span data-ttu-id="2b4d2-135">Musi być globalną przestrzenią nazw XML zdefiniowaną za pomocą `Imports` instrukcji lub lokalną przestrzenią nazw XML, która jest zdefiniowana w tym elemencie lub elemencie nadrzędnym.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-135">Must be a global XML namespace that is defined with an `Imports` statement, or a local XML namespace that is defined in this element or a parent element.</span></span>|
    |`aName`|<span data-ttu-id="2b4d2-136">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-136">Required.</span></span> <span data-ttu-id="2b4d2-137">Nazwa atrybutu.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-137">Name of the attribute.</span></span> <span data-ttu-id="2b4d2-138">Jest to jeden z następujących formatów:</span><span class="sxs-lookup"><span data-stu-id="2b4d2-138">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="2b4d2-139">-Literal Text.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-139">- Literal text.</span></span> <span data-ttu-id="2b4d2-140">Zobacz [nazwy zadeklarowanych elementów i atrybutów XML](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="2b4d2-140">See [Names of Declared XML Elements and Attributes](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span><br /><span data-ttu-id="2b4d2-141">-Osadzone wyrażenie formularza `<%= aNameExp %>` .</span><span class="sxs-lookup"><span data-stu-id="2b4d2-141">- Embedded expression of the form `<%= aNameExp %>`.</span></span> <span data-ttu-id="2b4d2-142">Typ `aNameExp` musi być `String` lub typem, który jest niejawnie konwertowany na <xref:System.Xml.Linq.XName> .</span><span class="sxs-lookup"><span data-stu-id="2b4d2-142">The type of `aNameExp` must be `String` or a type that is implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span>|
    |`aValue`|<span data-ttu-id="2b4d2-143">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-143">Optional.</span></span> <span data-ttu-id="2b4d2-144">Wartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-144">Value of the attribute.</span></span> <span data-ttu-id="2b4d2-145">Jest to jeden z następujących formatów:</span><span class="sxs-lookup"><span data-stu-id="2b4d2-145">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="2b4d2-146">-Literalny tekst ujęty w cudzysłów.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-146">- Literal text, enclosed in quotation marks.</span></span><br /><span data-ttu-id="2b4d2-147">-Osadzone wyrażenie formularza `<%= aValueExp %>` .</span><span class="sxs-lookup"><span data-stu-id="2b4d2-147">- Embedded expression of the form `<%= aValueExp %>`.</span></span> <span data-ttu-id="2b4d2-148">Dozwolony jest dowolny typ.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-148">Any type is allowed.</span></span>|

  - <span data-ttu-id="2b4d2-149">Wyrażenie osadzone formularza `<%= aExp %>` .</span><span class="sxs-lookup"><span data-stu-id="2b4d2-149">Embedded expression of the form `<%= aExp %>`.</span></span>

- `/>`

  <span data-ttu-id="2b4d2-150">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-150">Optional.</span></span> <span data-ttu-id="2b4d2-151">Wskazuje, że element jest pusty, bez zawartości.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-151">Indicates that the element is an empty element, without content.</span></span>

- `>`

  <span data-ttu-id="2b4d2-152">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-152">Required.</span></span> <span data-ttu-id="2b4d2-153">Zamyka tag początkowego lub pustego elementu.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-153">Ends the beginning or empty element tag.</span></span>

- `elementContents`

  <span data-ttu-id="2b4d2-154">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-154">Optional.</span></span> <span data-ttu-id="2b4d2-155">Zawartość elementu.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-155">Content of the element.</span></span>

  `content [ content ... ]`

  <span data-ttu-id="2b4d2-156">Każdy `content` z nich może być jednym z następujących:</span><span class="sxs-lookup"><span data-stu-id="2b4d2-156">Each `content` can be one of the following:</span></span>

  - <span data-ttu-id="2b4d2-157">Tekst literału.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-157">Literal text.</span></span> <span data-ttu-id="2b4d2-158">Całe białe miejsce w programie `elementContents` jest znaczące, jeśli istnieje dowolny tekst w postaci literału.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-158">All the white space in `elementContents` becomes significant if there is any literal text.</span></span>

  - <span data-ttu-id="2b4d2-159">Wyrażenie osadzone formularza `<%= contentExp %>` .</span><span class="sxs-lookup"><span data-stu-id="2b4d2-159">Embedded expression of the form `<%= contentExp %>`.</span></span>

  - <span data-ttu-id="2b4d2-160">Literal elementu XML.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-160">XML element literal.</span></span>

  - <span data-ttu-id="2b4d2-161">Literał komentarza XML.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-161">XML comment literal.</span></span> <span data-ttu-id="2b4d2-162">Zobacz [literał komentarza XML](xml-comment-literal.md).</span><span class="sxs-lookup"><span data-stu-id="2b4d2-162">See [XML Comment Literal](xml-comment-literal.md).</span></span>

  - <span data-ttu-id="2b4d2-163">Literał instrukcji przetwarzania XML.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-163">XML processing instruction literal.</span></span> <span data-ttu-id="2b4d2-164">Zobacz [literał instrukcji przetwarzania XML](xml-processing-instruction-literal.md).</span><span class="sxs-lookup"><span data-stu-id="2b4d2-164">See [XML Processing Instruction Literal](xml-processing-instruction-literal.md).</span></span>

  - <span data-ttu-id="2b4d2-165">Literał CDATA XML.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-165">XML CDATA literal.</span></span> <span data-ttu-id="2b4d2-166">Zobacz [LITERAŁ CDATA XML](xml-cdata-literal.md).</span><span class="sxs-lookup"><span data-stu-id="2b4d2-166">See [XML CDATA Literal](xml-cdata-literal.md).</span></span>

- `</[name]>`

  <span data-ttu-id="2b4d2-167">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-167">Optional.</span></span> <span data-ttu-id="2b4d2-168">Reprezentuje tag zamykający elementu.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-168">Represents the closing tag for the element.</span></span> <span data-ttu-id="2b4d2-169">Opcjonalny `name` parametr jest niedozwolony, jeśli jest wynikiem wyrażenia osadzonego.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-169">The optional `name` parameter is not allowed when it is the result of an embedded expression.</span></span>

## <a name="return-value"></a><span data-ttu-id="2b4d2-170">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2b4d2-170">Return Value</span></span>

<span data-ttu-id="2b4d2-171">Obiekt <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-171">An <xref:System.Xml.Linq.XElement> object.</span></span>

## <a name="remarks"></a><span data-ttu-id="2b4d2-172">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2b4d2-172">Remarks</span></span>

<span data-ttu-id="2b4d2-173">Można użyć składni literału elementu XML do tworzenia <xref:System.Xml.Linq.XElement> obiektów w kodzie.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-173">You can use the XML element literal syntax to create <xref:System.Xml.Linq.XElement> objects in your code.</span></span>

> [!NOTE]
> <span data-ttu-id="2b4d2-174">Literał XML może obejmować wiele wierszy bez używania znaków kontynuacji wiersza.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-174">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="2b4d2-175">Ta funkcja umożliwia skopiowanie zawartości z dokumentu XML i wklejenie jej bezpośrednio do programu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-175">This feature enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>

<span data-ttu-id="2b4d2-176">Osadzone wyrażenia formularza `<%= exp %>` umożliwiają dodawanie dynamicznych informacji do literału elementu XML.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-176">Embedded expressions of the form `<%= exp %>` enable you to add dynamic information to an XML element literal.</span></span> <span data-ttu-id="2b4d2-177">Aby uzyskać więcej informacji, zobacz [Embedded Expressions in XML](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="2b4d2-177">For more information, see [Embedded Expressions in XML](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>

<span data-ttu-id="2b4d2-178">Kompilator Visual Basic konwertuje literał elementu XML na wywołania <xref:System.Xml.Linq.XElement.%23ctor%2A> konstruktora i, jeśli jest wymagany, <xref:System.Xml.Linq.XAttribute.%23ctor%2A> Konstruktor.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-178">The Visual Basic compiler converts the XML element literal into calls to the <xref:System.Xml.Linq.XElement.%23ctor%2A> constructor and, if it is required, the <xref:System.Xml.Linq.XAttribute.%23ctor%2A> constructor.</span></span>

## <a name="xml-namespaces"></a><span data-ttu-id="2b4d2-179">Przestrzenie nazw XML</span><span class="sxs-lookup"><span data-stu-id="2b4d2-179">XML Namespaces</span></span>

<span data-ttu-id="2b4d2-180">Prefiksy przestrzeni nazw XML są przydatne, gdy trzeba utworzyć literały XML z elementami z tego samego obszaru nazw wiele razy w kodzie.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-180">XML namespace prefixes are useful when you have to create XML literals with elements from the same namespace many times in code.</span></span> <span data-ttu-id="2b4d2-181">Można użyć globalnych prefiksów przestrzeni nazw XML, które można zdefiniować przy użyciu `Imports` instrukcji lub lokalnych prefiksów, które można zdefiniować przy użyciu `xmlns:xmlPrefix="xmlNamespace"` składni atrybutu.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-181">You can use global XML namespace prefixes, which you define by using the `Imports` statement, or local prefixes, which you define by using the `xmlns:xmlPrefix="xmlNamespace"` attribute syntax.</span></span> <span data-ttu-id="2b4d2-182">Aby uzyskać więcej informacji, zobacz [Imports — Instrukcja (przestrzeń nazw XML)](../statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="2b4d2-182">For more information, see [Imports Statement (XML Namespace)](../statements/imports-statement-xml-namespace.md).</span></span>

<span data-ttu-id="2b4d2-183">Zgodnie z regułami określania zakresu dla przestrzeni nazw XML, lokalne prefiksy mają pierwszeństwo przed globalnymi prefiksami.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-183">In accordance with the scoping rules for XML namespaces, local prefixes take precedence over global prefixes.</span></span> <span data-ttu-id="2b4d2-184">Jeśli jednak literał XML definiuje przestrzeń nazw XML, ta przestrzeń nazw nie jest dostępna dla wyrażeń, które pojawiają się w wyrażeniu osadzonym.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-184">However, if an XML literal defines an XML namespace, that namespace is not available to expressions that appear in an embedded expression.</span></span> <span data-ttu-id="2b4d2-185">Wyrażenie osadzone może uzyskać dostęp tylko do globalnej przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-185">The embedded expression can access only the global XML namespace.</span></span>

<span data-ttu-id="2b4d2-186">Kompilator Visual Basic konwertuje każdą globalną przestrzeń nazw XML, która jest używana przez literał XML w jedną definicję lokalnego obszaru nazw w wygenerowanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-186">The Visual Basic compiler converts each global XML namespace that is used by an XML literal into a one local namespace definition in the generated code.</span></span> <span data-ttu-id="2b4d2-187">Globalne obszary nazw XML, które nie są używane, nie są wyświetlane w wygenerowanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-187">Global XML namespaces that are not used do not appear in the generated code.</span></span>

## <a name="example"></a><span data-ttu-id="2b4d2-188">Przykład</span><span class="sxs-lookup"><span data-stu-id="2b4d2-188">Example</span></span>

<span data-ttu-id="2b4d2-189">Poniższy przykład pokazuje, jak utworzyć prosty element XML, który ma dwa zagnieżdżone puste elementy.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-189">The following example shows how to create a simple XML element that has two nested empty elements.</span></span>

[!code-vb[VbXMLSamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples9.vb#20)]

<span data-ttu-id="2b4d2-190">Przykład wyświetla następujący tekst.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-190">The example displays the following text.</span></span> <span data-ttu-id="2b4d2-191">Zauważ, że literał zachowuje strukturę pustych elementów.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-191">Notice that the literal preserves the structure of the empty elements.</span></span>

```xml
<outer>
  <inner1></inner1>
  <inner2 />
</outer>
```

## <a name="example"></a><span data-ttu-id="2b4d2-192">Przykład</span><span class="sxs-lookup"><span data-stu-id="2b4d2-192">Example</span></span>

<span data-ttu-id="2b4d2-193">Poniższy przykład pokazuje, jak używać osadzonych wyrażeń, aby nazwać element i utworzyć atrybuty.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-193">The following example shows how to use embedded expressions to name an element and create attributes.</span></span>

[!code-vb[VbXMLSamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples9.vb#21)]

<span data-ttu-id="2b4d2-194">Ten kod wyświetla następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="2b4d2-194">This code displays the following text:</span></span>

```xml
<book isbn="1234" author="My Author" year="1999" title="My Book" />
```

## <a name="example"></a><span data-ttu-id="2b4d2-195">Przykład</span><span class="sxs-lookup"><span data-stu-id="2b4d2-195">Example</span></span>

<span data-ttu-id="2b4d2-196">Poniższy przykład deklaruje `ns` jako prefiks przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-196">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="2b4d2-197">Następnie używa prefiksu przestrzeni nazw w celu utworzenia literału XML i wyświetla ostateczną postać elementu.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-197">It then uses the prefix of the namespace to create an XML literal and displays the element's final form.</span></span>

[!code-vb[VbXMLSamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples10.vb#22)]

<span data-ttu-id="2b4d2-198">Ten kod wyświetla następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="2b4d2-198">This code displays the following text:</span></span>

```xml
<ns:outer xmlns:ns="http://SomeNamespace">
  <ns:middle xmlns:ns="http://NewNamespace">
    <ns:inner1 />
    <inner2 xmlns="http://SomeNamespace" />
  </ns:middle>
</ns:outer>
```

<span data-ttu-id="2b4d2-199">Zwróć uwagę, że kompilator przekonwertował prefiks globalnej przestrzeni nazw XML na definicję prefiksu dla przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-199">Notice that the compiler converted the prefix of the global XML namespace into a prefix definition for the XML namespace.</span></span> <span data-ttu-id="2b4d2-200">\<ns:middle>Element ponownie definiuje prefiks przestrzeni nazw XML dla \<ns:inner1> elementu.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-200">The \<ns:middle> element redefines the XML namespace prefix for the \<ns:inner1> element.</span></span> <span data-ttu-id="2b4d2-201">Jednak \<ns:inner2> element używa przestrzeni nazw zdefiniowanej przez `Imports` instrukcję.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-201">However, the \<ns:inner2> element uses the namespace defined by the `Imports` statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="2b4d2-202">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2b4d2-202">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="2b4d2-203">Nazwy deklarowanych elementów XML oraz atrybuty</span><span class="sxs-lookup"><span data-stu-id="2b4d2-203">Names of Declared XML Elements and Attributes</span></span>](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
- [<span data-ttu-id="2b4d2-204">Literał komentarza XML</span><span class="sxs-lookup"><span data-stu-id="2b4d2-204">XML Comment Literal</span></span>](xml-comment-literal.md)
- [<span data-ttu-id="2b4d2-205">Literał CDATA XML</span><span class="sxs-lookup"><span data-stu-id="2b4d2-205">XML CDATA Literal</span></span>](xml-cdata-literal.md)
- [<span data-ttu-id="2b4d2-206">Literały XML</span><span class="sxs-lookup"><span data-stu-id="2b4d2-206">XML Literals</span></span>](index.md)
- [<span data-ttu-id="2b4d2-207">Tworzenie XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2b4d2-207">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="2b4d2-208">Wyrażenia osadzone w XML</span><span class="sxs-lookup"><span data-stu-id="2b4d2-208">Embedded Expressions in XML</span></span>](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [<span data-ttu-id="2b4d2-209">Imports — Instrukcja (przestrzeń nazw XML)</span><span class="sxs-lookup"><span data-stu-id="2b4d2-209">Imports Statement (XML Namespace)</span></span>](../statements/imports-statement-xml-namespace.md)
