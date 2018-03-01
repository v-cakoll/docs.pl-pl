---
title: "Literał elementu XML (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlLiteralElement
helpviewer_keywords:
- XML element literal [Visual Basic]
- element literal [Visual Basic]
- XML literals [Visual Basic], element
ms.assetid: 95039642-7893-48b7-b23f-45a6c55d8f67
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: de5825a6af1dd1b93c3c85651125cf817dc564f2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="xml-element-literal-visual-basic"></a><span data-ttu-id="5de6f-102">Literał elementu XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5de6f-102">XML Element Literal (Visual Basic)</span></span>

<span data-ttu-id="5de6f-103">Literał, która reprezentuje <xref:System.Xml.Linq.XElement> obiektu.</span><span class="sxs-lookup"><span data-stu-id="5de6f-103">A literal that represents an <xref:System.Xml.Linq.XElement> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5de6f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5de6f-104">Syntax</span></span>  
  
```xml  
<name [ attributeList ] />  
-or-  
<name [ attributeList ] > [ elementContents ] </[ name ]>  
```  
  
## <a name="parts"></a><span data-ttu-id="5de6f-105">Części</span><span class="sxs-lookup"><span data-stu-id="5de6f-105">Parts</span></span>  
  
-   `<`  
  
     <span data-ttu-id="5de6f-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="5de6f-106">Required.</span></span> <span data-ttu-id="5de6f-107">Otwiera początkowego tagu elementu.</span><span class="sxs-lookup"><span data-stu-id="5de6f-107">Opens the starting element tag.</span></span>  
  
-   `name`  
  
     <span data-ttu-id="5de6f-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="5de6f-108">Required.</span></span> <span data-ttu-id="5de6f-109">Nazwa elementu.</span><span class="sxs-lookup"><span data-stu-id="5de6f-109">Name of the element.</span></span> <span data-ttu-id="5de6f-110">Format jest jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="5de6f-110">The format is one of the following:</span></span>  
  
    -   <span data-ttu-id="5de6f-111">Literały tekstowe dla nazwy elementu w postaci `[ePrefix:]eName`, gdzie:</span><span class="sxs-lookup"><span data-stu-id="5de6f-111">Literal text for the element name, of the form `[ePrefix:]eName`, where:</span></span>  
  
        |<span data-ttu-id="5de6f-112">Część</span><span class="sxs-lookup"><span data-stu-id="5de6f-112">Part</span></span>|<span data-ttu-id="5de6f-113">Opis</span><span class="sxs-lookup"><span data-stu-id="5de6f-113">Description</span></span>|  
        |---|---|  
        |`ePrefix`|<span data-ttu-id="5de6f-114">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="5de6f-114">Optional.</span></span> <span data-ttu-id="5de6f-115">Prefiks przestrzeni nazw XML dla elementu.</span><span class="sxs-lookup"><span data-stu-id="5de6f-115">XML namespace prefix for the element.</span></span> <span data-ttu-id="5de6f-116">Musi być globalnej przestrzeni nazw XML, która jest zdefiniowana z `Imports` instrukcji w pliku lub na poziomie projektu lub lokalnej przestrzeni nazw XML, który jest zdefiniowany w tym elemencie lub elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="5de6f-116">Must be a global XML namespace that is defined with an `Imports` statement in the file or at the project level, or a local XML namespace that is defined in this element or a parent element.</span></span>|  
        |`eName`|<span data-ttu-id="5de6f-117">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="5de6f-117">Required.</span></span> <span data-ttu-id="5de6f-118">Nazwa elementu.</span><span class="sxs-lookup"><span data-stu-id="5de6f-118">Name of the element.</span></span> <span data-ttu-id="5de6f-119">Format jest jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="5de6f-119">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="5de6f-120">— Tekst literału.</span><span class="sxs-lookup"><span data-stu-id="5de6f-120">-   Literal text.</span></span> <span data-ttu-id="5de6f-121">Zobacz [nazwy deklarowanych elementów XML oraz atrybuty](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="5de6f-121">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span><br /><span data-ttu-id="5de6f-122">— Osadzone wyrażenie w postaci `<%= eNameExp %>`.</span><span class="sxs-lookup"><span data-stu-id="5de6f-122">-   Embedded expression of the form `<%= eNameExp %>`.</span></span> <span data-ttu-id="5de6f-123">Typ `eNameExp` musi być `String` lub typu, który jest niejawnie przekonwertować <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="5de6f-123">The type of `eNameExp` must be `String` or a type that is implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span>|  
  
    -   <span data-ttu-id="5de6f-124">Osadzone wyrażenie w postaci `<%= nameExp %>`.</span><span class="sxs-lookup"><span data-stu-id="5de6f-124">Embedded expression of the form `<%= nameExp %>`.</span></span> <span data-ttu-id="5de6f-125">Typ `nameExp` musi być `String` lub umożliwiają niejawnej konwersji na typ <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="5de6f-125">The type of `nameExp` must be `String` or a type implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span> <span data-ttu-id="5de6f-126">Wyrażenie osadzone nie jest dozwolona w tagu zamykającego elementu.</span><span class="sxs-lookup"><span data-stu-id="5de6f-126">An embedded expression is not allowed in a closing tag of an element.</span></span>  
  
-   `attributeList`  
  
     <span data-ttu-id="5de6f-127">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="5de6f-127">Optional.</span></span> <span data-ttu-id="5de6f-128">Lista atrybutów zadeklarowany w literału.</span><span class="sxs-lookup"><span data-stu-id="5de6f-128">List of attributes declared in the literal.</span></span>  
  
     `attribute [ attribute ... ]`  
  
     <span data-ttu-id="5de6f-129">Każdy `attribute` ma następujące parametry:</span><span class="sxs-lookup"><span data-stu-id="5de6f-129">Each `attribute` has one of the following syntaxes:</span></span>  
  
    -   <span data-ttu-id="5de6f-130">Atrybut przypisania w postaci `[aPrefix:]aName=aValue`, gdzie:</span><span class="sxs-lookup"><span data-stu-id="5de6f-130">Attribute assignment, of the form `[aPrefix:]aName=aValue`, where:</span></span>  
  
        |<span data-ttu-id="5de6f-131">Część</span><span class="sxs-lookup"><span data-stu-id="5de6f-131">Part</span></span>|<span data-ttu-id="5de6f-132">Opis</span><span class="sxs-lookup"><span data-stu-id="5de6f-132">Description</span></span>|  
        |---|---|  
        |`aPrefix`|<span data-ttu-id="5de6f-133">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="5de6f-133">Optional.</span></span> <span data-ttu-id="5de6f-134">Prefiks przestrzeni nazw XML dla atrybutu.</span><span class="sxs-lookup"><span data-stu-id="5de6f-134">XML namespace prefix for the attribute.</span></span> <span data-ttu-id="5de6f-135">Musi być globalnej przestrzeni nazw XML, która jest zdefiniowana z `Imports` instrukcji lub lokalnej przestrzeni nazw XML, który jest zdefiniowany w tym elemencie lub elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="5de6f-135">Must be a global XML namespace that is defined with an `Imports` statement, or a local XML namespace that is defined in this element or a parent element.</span></span>|  
        |`aName`|<span data-ttu-id="5de6f-136">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="5de6f-136">Required.</span></span> <span data-ttu-id="5de6f-137">Nazwa atrybutu.</span><span class="sxs-lookup"><span data-stu-id="5de6f-137">Name of the attribute.</span></span> <span data-ttu-id="5de6f-138">Format jest jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="5de6f-138">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="5de6f-139">— Tekst literału.</span><span class="sxs-lookup"><span data-stu-id="5de6f-139">-   Literal text.</span></span> <span data-ttu-id="5de6f-140">Zobacz [nazwy deklarowanych elementów XML oraz atrybuty](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="5de6f-140">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span><br /><span data-ttu-id="5de6f-141">— Osadzone wyrażenie w postaci `<%= aNameExp %>`.</span><span class="sxs-lookup"><span data-stu-id="5de6f-141">-   Embedded expression of the form `<%= aNameExp %>`.</span></span> <span data-ttu-id="5de6f-142">Typ `aNameExp` musi być `String` lub typu, który jest niejawnie przekonwertować <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="5de6f-142">The type of `aNameExp` must be `String` or a type that is implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span>|  
        |`aValue`|<span data-ttu-id="5de6f-143">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="5de6f-143">Optional.</span></span> <span data-ttu-id="5de6f-144">Wartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="5de6f-144">Value of the attribute.</span></span> <span data-ttu-id="5de6f-145">Format jest jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="5de6f-145">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="5de6f-146">— Tekst literału ujęty w cudzysłów.</span><span class="sxs-lookup"><span data-stu-id="5de6f-146">-   Literal text, enclosed in quotation marks.</span></span><br /><span data-ttu-id="5de6f-147">— Osadzone wyrażenie w postaci `<%= aValueExp %>`.</span><span class="sxs-lookup"><span data-stu-id="5de6f-147">-   Embedded expression of the form `<%= aValueExp %>`.</span></span> <span data-ttu-id="5de6f-148">Dowolny typ jest dozwolone.</span><span class="sxs-lookup"><span data-stu-id="5de6f-148">Any type is allowed.</span></span>|  
  
    -   <span data-ttu-id="5de6f-149">Osadzone wyrażenie w postaci `<%= aExp %>`.</span><span class="sxs-lookup"><span data-stu-id="5de6f-149">Embedded expression of the form `<%= aExp %>`.</span></span>  
  
-   `/>`  
  
     <span data-ttu-id="5de6f-150">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="5de6f-150">Optional.</span></span> <span data-ttu-id="5de6f-151">Wskazuje, czy element jest elementem pustym, bez zawartości.</span><span class="sxs-lookup"><span data-stu-id="5de6f-151">Indicates that the element is an empty element, without content.</span></span>  
  
-   `>`  
  
     <span data-ttu-id="5de6f-152">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="5de6f-152">Required.</span></span> <span data-ttu-id="5de6f-153">Kończy się tagu elementu początkowy lub jest pusty.</span><span class="sxs-lookup"><span data-stu-id="5de6f-153">Ends the beginning or empty element tag.</span></span>  
  
-   `elementContents`  
  
     <span data-ttu-id="5de6f-154">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="5de6f-154">Optional.</span></span> <span data-ttu-id="5de6f-155">Zawartość elementu.</span><span class="sxs-lookup"><span data-stu-id="5de6f-155">Content of the element.</span></span>  
  
     `content [ content ... ]`  
  
     <span data-ttu-id="5de6f-156">Każdy `content` może być jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="5de6f-156">Each `content` can be one of the following:</span></span>  
  
    -   <span data-ttu-id="5de6f-157">Literały tekstowe.</span><span class="sxs-lookup"><span data-stu-id="5de6f-157">Literal text.</span></span> <span data-ttu-id="5de6f-158">Wszystkie biały znak w `elementContents` staje się istotne, jeśli ma żadnych literału tekstu.</span><span class="sxs-lookup"><span data-stu-id="5de6f-158">All the white space in `elementContents` becomes significant if there is any literal text.</span></span>  
  
    -   <span data-ttu-id="5de6f-159">Osadzone wyrażenie w postaci `<%= contentExp %>`.</span><span class="sxs-lookup"><span data-stu-id="5de6f-159">Embedded expression of the form `<%= contentExp %>`.</span></span>  
  
    -   <span data-ttu-id="5de6f-160">Literał elementu XML.</span><span class="sxs-lookup"><span data-stu-id="5de6f-160">XML element literal.</span></span>  
  
    -   <span data-ttu-id="5de6f-161">Literał komentarza XML.</span><span class="sxs-lookup"><span data-stu-id="5de6f-161">XML comment literal.</span></span> <span data-ttu-id="5de6f-162">Zobacz [literał komentarza XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span><span class="sxs-lookup"><span data-stu-id="5de6f-162">See [XML Comment Literal](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span></span>  
  
    -   <span data-ttu-id="5de6f-163">Literał instrukcji przetwarzania XML.</span><span class="sxs-lookup"><span data-stu-id="5de6f-163">XML processing instruction literal.</span></span> <span data-ttu-id="5de6f-164">Zobacz [literał instrukcji przetwarzającej kod XML](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span><span class="sxs-lookup"><span data-stu-id="5de6f-164">See [XML Processing Instruction Literal](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span></span>  
  
    -   <span data-ttu-id="5de6f-165">Literał CDATA XML.</span><span class="sxs-lookup"><span data-stu-id="5de6f-165">XML CDATA literal.</span></span> <span data-ttu-id="5de6f-166">Zobacz [literał XML CDATA](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md).</span><span class="sxs-lookup"><span data-stu-id="5de6f-166">See [XML CDATA Literal](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md).</span></span>  
  
-   `</[name]>`  
  
     <span data-ttu-id="5de6f-167">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="5de6f-167">Optional.</span></span> <span data-ttu-id="5de6f-168">Reprezentuje tag zamykający dla elementu.</span><span class="sxs-lookup"><span data-stu-id="5de6f-168">Represents the closing tag for the element.</span></span> <span data-ttu-id="5de6f-169">Opcjonalny `name` parametru nie jest dozwolona, gdy jest to wynik wyrażenia osadzonego.</span><span class="sxs-lookup"><span data-stu-id="5de6f-169">The optional `name` parameter is not allowed when it is the result of an embedded expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5de6f-170">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5de6f-170">Return Value</span></span>  
 <span data-ttu-id="5de6f-171"><xref:System.Xml.Linq.XElement> Obiektu.</span><span class="sxs-lookup"><span data-stu-id="5de6f-171">An <xref:System.Xml.Linq.XElement> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5de6f-172">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5de6f-172">Remarks</span></span>  
 <span data-ttu-id="5de6f-173">Składnia literał elementu XML umożliwia utworzenie <xref:System.Xml.Linq.XElement> obiektów w kodzie.</span><span class="sxs-lookup"><span data-stu-id="5de6f-173">You can use the XML element literal syntax to create <xref:System.Xml.Linq.XElement> objects in your code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5de6f-174">Literał XML może obejmować wiele wierszy bez użycia znaki kontynuacji wiersza.</span><span class="sxs-lookup"><span data-stu-id="5de6f-174">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="5de6f-175">Ta funkcja umożliwia kopiowanie zawartości z dokumentu XML i wklej go bezpośrednio do [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program.</span><span class="sxs-lookup"><span data-stu-id="5de6f-175">This feature enables you to copy content from an XML document and paste it directly into a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program.</span></span>  
  
 <span data-ttu-id="5de6f-176">Osadzone wyrażenia w postaci `<%= exp %>` umożliwiają dodanie informacji dynamicznych na literał elementu XML.</span><span class="sxs-lookup"><span data-stu-id="5de6f-176">Embedded expressions of the form `<%= exp %>` enable you to add dynamic information to an XML element literal.</span></span> <span data-ttu-id="5de6f-177">Aby uzyskać więcej informacji, zobacz [wyrażenia osadzone w XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="5de6f-177">For more information, see [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>  
  
 <span data-ttu-id="5de6f-178">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Kompilatora konwertuje literał elementu XML do wywołania <xref:System.Xml.Linq.XElement.%23ctor%2A> Konstruktor i, jeśli jest to wymagane, <xref:System.Xml.Linq.XAttribute.%23ctor%2A> konstruktora.</span><span class="sxs-lookup"><span data-stu-id="5de6f-178">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler converts the XML element literal into calls to the <xref:System.Xml.Linq.XElement.%23ctor%2A> constructor and, if it is required, the <xref:System.Xml.Linq.XAttribute.%23ctor%2A> constructor.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="5de6f-179">Przestrzenie nazw XML</span><span class="sxs-lookup"><span data-stu-id="5de6f-179">XML Namespaces</span></span>  
 <span data-ttu-id="5de6f-180">Prefiksy przestrzeni nazw XML są przydatne, gdy trzeba utworzyć literałów XML z elementami z tego samego obszaru nazw wiele razy w kodzie.</span><span class="sxs-lookup"><span data-stu-id="5de6f-180">XML namespace prefixes are useful when you have to create XML literals with elements from the same namespace many times in code.</span></span> <span data-ttu-id="5de6f-181">Można użyć globalne prefiksy przestrzeni nazw XML, które definiują przy użyciu `Imports` instrukcji lub lokalnego prefiksy, które definiują przy użyciu `xmlns:xmlPrefix="xmlNamespace"` atrybutu składni.</span><span class="sxs-lookup"><span data-stu-id="5de6f-181">You can use global XML namespace prefixes, which you define by using the `Imports` statement, or local prefixes, which you define by using the `xmlns:xmlPrefix="xmlNamespace"` attribute syntax.</span></span> <span data-ttu-id="5de6f-182">Aby uzyskać więcej informacji, zobacz [Importy — instrukcja (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="5de6f-182">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
 <span data-ttu-id="5de6f-183">Zgodnie z regułami zakresu dla obszarów nazw XML prefiksy lokalnego mają pierwszeństwo przed prefiksy globalnego.</span><span class="sxs-lookup"><span data-stu-id="5de6f-183">In accordance with the scoping rules for XML namespaces, local prefixes take precedence over global prefixes.</span></span> <span data-ttu-id="5de6f-184">Jednak jeśli literał XML definiuje obszar nazw XML, tej przestrzeni nazw nie jest dostępny do wyrażeń, które są widoczne w wyrażenia osadzonego.</span><span class="sxs-lookup"><span data-stu-id="5de6f-184">However, if an XML literal defines an XML namespace, that namespace is not available to expressions that appear in an embedded expression.</span></span> <span data-ttu-id="5de6f-185">Wyrażenia osadzonego mogą uzyskiwać dostęp tylko globalnej przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="5de6f-185">The embedded expression can access only the global XML namespace.</span></span>  
  
 <span data-ttu-id="5de6f-186">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Kompilatora konwertuje każdego globalnej przestrzeni nazw XML, używany przez literał XML w jednej definicji lokalną przestrzeń nazw w wygenerowanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="5de6f-186">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler converts each global XML namespace that is used by an XML literal into a one local namespace definition in the generated code.</span></span> <span data-ttu-id="5de6f-187">Globalne przestrzenie nazw XML, które nie są używane, nie są wyświetlane w wygenerowanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="5de6f-187">Global XML namespaces that are not used do not appear in the generated code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5de6f-188">Przykład</span><span class="sxs-lookup"><span data-stu-id="5de6f-188">Example</span></span>  
 <span data-ttu-id="5de6f-189">Poniższy przykład przedstawia sposób tworzenia prostego elementu XML, która ma dwa puste elementy zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="5de6f-189">The following example shows how to create a simple XML element that has two nested empty elements.</span></span>  
  
 [!code-vb[VbXMLSamples#20](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_1.vb)]  
  
 <span data-ttu-id="5de6f-190">W przykładzie przedstawiono następujący tekst.</span><span class="sxs-lookup"><span data-stu-id="5de6f-190">The example displays the following text.</span></span> <span data-ttu-id="5de6f-191">Zwróć uwagę, że literał zachowa struktury elementów pustych.</span><span class="sxs-lookup"><span data-stu-id="5de6f-191">Notice that the literal preserves the structure of the empty elements.</span></span>  
  
```xml  
<outer>  
  <inner1></inner1>  
  <inner2 />  
</outer>  
```  
  
## <a name="example"></a><span data-ttu-id="5de6f-192">Przykład</span><span class="sxs-lookup"><span data-stu-id="5de6f-192">Example</span></span>  
 <span data-ttu-id="5de6f-193">Poniższy przykład przedstawia użycie wyrażenia osadzone nadać nazwy elementu i utworzyć atrybuty.</span><span class="sxs-lookup"><span data-stu-id="5de6f-193">The following example shows how to use embedded expressions to name an element and create attributes.</span></span>  
  
 [!code-vb[VbXMLSamples#21](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_2.vb)]  
  
 <span data-ttu-id="5de6f-194">Ten kod zawiera następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="5de6f-194">This code displays the following text:</span></span>  
  
```xml  
<book isbn="1234" author="My Author" year="1999" title="My Book" />  
```  
  
## <a name="example"></a><span data-ttu-id="5de6f-195">Przykład</span><span class="sxs-lookup"><span data-stu-id="5de6f-195">Example</span></span>  
 <span data-ttu-id="5de6f-196">Poniższy przykład deklaruje `ns` jako prefiks przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="5de6f-196">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="5de6f-197">Następnie używa prefiks przestrzeni nazw w celu utworzenia literału XML i wyświetla formularz końcowego elementu.</span><span class="sxs-lookup"><span data-stu-id="5de6f-197">It then uses the prefix of the namespace to create an XML literal and displays the element's final form.</span></span>  
  
 [!code-vb[VbXMLSamples#22](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_3.vb)]  
  
 <span data-ttu-id="5de6f-198">Ten kod zawiera następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="5de6f-198">This code displays the following text:</span></span>  
  
```xml  
<ns:outer xmlns:ns="http://SomeNamespace">  
  <ns:middle xmlns:ns="http://NewNamespace">  
    <ns:inner1 />  
    <inner2 xmlns="http://SomeNamespace" />  
  </ns:middle>  
</ns:outer>  
```  
  
 <span data-ttu-id="5de6f-199">Zwróć uwagę, że kompilator przekształcone prefiks globalnej przestrzeni nazw XML definicję prefiksu dla przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="5de6f-199">Notice that the compiler converted the prefix of the global XML namespace into a prefix definition for the XML namespace.</span></span> <span data-ttu-id="5de6f-200">\<Ns:middle > prefiks przestrzeni nazw XML dla ponownie definiuje element \<ns:inner1 > elementu.</span><span class="sxs-lookup"><span data-stu-id="5de6f-200">The \<ns:middle> element redefines the XML namespace prefix for the \<ns:inner1> element.</span></span> <span data-ttu-id="5de6f-201">Jednak \<ns:inner2 > element używa przestrzeń nazw zdefiniowana przez `Imports` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="5de6f-201">However, the \<ns:inner2> element uses the namespace defined by the `Imports` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5de6f-202">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5de6f-202">See Also</span></span>  
 <xref:System.Xml.Linq.XElement>  
 [<span data-ttu-id="5de6f-203">Nazwy deklarowanych elementów XML oraz atrybuty</span><span class="sxs-lookup"><span data-stu-id="5de6f-203">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)  
 [<span data-ttu-id="5de6f-204">Literał komentarza XML</span><span class="sxs-lookup"><span data-stu-id="5de6f-204">XML Comment Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)  
 [<span data-ttu-id="5de6f-205">Literał XML CDATA</span><span class="sxs-lookup"><span data-stu-id="5de6f-205">XML CDATA Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md)  
 [<span data-ttu-id="5de6f-206">Literały XML</span><span class="sxs-lookup"><span data-stu-id="5de6f-206">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="5de6f-207">Tworzenie XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5de6f-207">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="5de6f-208">Wyrażenia osadzone w XML</span><span class="sxs-lookup"><span data-stu-id="5de6f-208">Embedded Expressions in XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)  
 [<span data-ttu-id="5de6f-209">Imports — instrukcja (Namespace XML)</span><span class="sxs-lookup"><span data-stu-id="5de6f-209">Imports Statement (XML Namespace)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
