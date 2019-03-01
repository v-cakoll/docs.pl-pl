---
title: Wyrażenia osadzone w XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlEmbeddedExpression
helpviewer_keywords:
- embedded expressions [Visual Basic]
- LINQ to XML [Visual Basic], embedded expressions
- XML literals [Visual Basic], embedded expressions
ms.assetid: bf2eb779-b751-4b7c-854f-9f2161482352
ms.openlocfilehash: feb0168c216b23ff02ca9350f868e091fefca689
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965790"
---
# <a name="embedded-expressions-in-xml-visual-basic"></a><span data-ttu-id="31983-102">Wyrażenia osadzone w XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31983-102">Embedded Expressions in XML (Visual Basic)</span></span>
<span data-ttu-id="31983-103">Wyrażenia osadzone umożliwiają tworzenie literałów XML, które zawierają wyrażenia, które są oceniane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="31983-103">Embedded expressions enable you to create XML literals that contain expressions that are evaluated at run time.</span></span> <span data-ttu-id="31983-104">Składnia wyrażenia osadzone jest `<%=` `expression` `%>`, która jest taka sama jak składnia używane w [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)].</span><span class="sxs-lookup"><span data-stu-id="31983-104">The syntax for an embedded expression is `<%=` `expression` `%>`, which is the same as the syntax used in [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)].</span></span>  
  
 <span data-ttu-id="31983-105">Na przykład można utworzysz XML element literału, łącząc osadzone wyrażenia zawierające tekst dosłowny zawartości.</span><span class="sxs-lookup"><span data-stu-id="31983-105">For example, you can create an XML element literal, combining embedded expressions with literal text content.</span></span>  
  
 [!code-vb[VbXMLSamples#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#27)]  
  
 <span data-ttu-id="31983-106">Jeśli `isbnNumber` zawiera całkowitą 12345 i `modifiedDate` zawiera datę 3/5/2006, kiedy ten kod jest wykonywany, wartość `book` jest:</span><span class="sxs-lookup"><span data-stu-id="31983-106">If `isbnNumber` contains the integer 12345 and `modifiedDate` contains the date 3/5/2006, when this code executes, the value of `book` is:</span></span>  
  
```xml  
<book category="fiction" isbn="12345">  
  <modifiedDate>3/5/2006</modifiedDate>  
</book>  
```  
  
## <a name="embedded-expression-location-and-validation"></a><span data-ttu-id="31983-107">Wyrażenia osadzone lokalizacji i sprawdzania poprawności</span><span class="sxs-lookup"><span data-stu-id="31983-107">Embedded Expression Location and Validation</span></span>  
 <span data-ttu-id="31983-108">Wyrażenia osadzone może znajdować się tylko w określonych lokalizacjach w ramach wyrażeń literałów XML.</span><span class="sxs-lookup"><span data-stu-id="31983-108">Embedded expressions can appear only at certain locations within XML literal expressions.</span></span> <span data-ttu-id="31983-109">Formanty lokalizacji wyrażenie, które typy wyrażenie może zwrócić i w jaki sposób `Nothing` jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="31983-109">The expression location controls which types the expression can return and how `Nothing` is handled.</span></span> <span data-ttu-id="31983-110">W poniższej tabeli opisano dozwolone lokalizacje i typy wyrażenia osadzone.</span><span class="sxs-lookup"><span data-stu-id="31983-110">The following table describes the allowed locations and types of embedded expressions.</span></span>  
  
|<span data-ttu-id="31983-111">Lokalizacja w literału</span><span class="sxs-lookup"><span data-stu-id="31983-111">Location in literal</span></span>|<span data-ttu-id="31983-112">Typ wyrażenia</span><span class="sxs-lookup"><span data-stu-id="31983-112">Type of expression</span></span>|<span data-ttu-id="31983-113">Obsługa `Nothing`</span><span class="sxs-lookup"><span data-stu-id="31983-113">Handling of `Nothing`</span></span>|  
|---|---|---|  
|<span data-ttu-id="31983-114">Nazwa elementu XML</span><span class="sxs-lookup"><span data-stu-id="31983-114">XML element name</span></span>|<xref:System.Xml.Linq.XName>|<span data-ttu-id="31983-115">Błąd</span><span class="sxs-lookup"><span data-stu-id="31983-115">Error</span></span>|  
|<span data-ttu-id="31983-116">Treść elementu XML.</span><span class="sxs-lookup"><span data-stu-id="31983-116">XML element content</span></span>|<span data-ttu-id="31983-117">`Object` tablica lub `Object`</span><span class="sxs-lookup"><span data-stu-id="31983-117">`Object` or array of `Object`</span></span>|<span data-ttu-id="31983-118">Ignorowane</span><span class="sxs-lookup"><span data-stu-id="31983-118">Ignored</span></span>|  
|<span data-ttu-id="31983-119">Nazwa atrybutu — element XML</span><span class="sxs-lookup"><span data-stu-id="31983-119">XML element attribute name</span></span>|<xref:System.Xml.Linq.XName>|<span data-ttu-id="31983-120">Błąd, chyba że wartość atrybutu jest również `Nothing`</span><span class="sxs-lookup"><span data-stu-id="31983-120">Error, unless the attribute value is also `Nothing`</span></span>|  
|<span data-ttu-id="31983-121">Wartość atrybutu — element XML</span><span class="sxs-lookup"><span data-stu-id="31983-121">XML element attribute value</span></span>|`Object`|<span data-ttu-id="31983-122">Atrybut deklaracja ignorowana</span><span class="sxs-lookup"><span data-stu-id="31983-122">Attribute declaration ignored</span></span>|  
|<span data-ttu-id="31983-123">Atrybut — element XML</span><span class="sxs-lookup"><span data-stu-id="31983-123">XML element attribute</span></span>|<span data-ttu-id="31983-124"><xref:System.Xml.Linq.XAttribute> lub kolekcji <xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="31983-124"><xref:System.Xml.Linq.XAttribute> or a collection of <xref:System.Xml.Linq.XAttribute></span></span>|<span data-ttu-id="31983-125">Ignorowane</span><span class="sxs-lookup"><span data-stu-id="31983-125">Ignored</span></span>|  
|<span data-ttu-id="31983-126">Element główny dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="31983-126">XML document root element</span></span>|<span data-ttu-id="31983-127"><xref:System.Xml.Linq.XElement> lub kolekcji jednego <xref:System.Xml.Linq.XElement> obiektu i dowolną liczbę <xref:System.Xml.Linq.XProcessingInstruction> i <xref:System.Xml.Linq.XComment> obiektów</span><span class="sxs-lookup"><span data-stu-id="31983-127"><xref:System.Xml.Linq.XElement> or a collection of one <xref:System.Xml.Linq.XElement> object and an arbitrary number of <xref:System.Xml.Linq.XProcessingInstruction> and <xref:System.Xml.Linq.XComment> objects</span></span>|<span data-ttu-id="31983-128">Ignorowane</span><span class="sxs-lookup"><span data-stu-id="31983-128">Ignored</span></span>|  
  
-   <span data-ttu-id="31983-129">Przykład wyrażenia osadzone w nazwa elementu XML:</span><span class="sxs-lookup"><span data-stu-id="31983-129">Example of an embedded expression in an XML element name:</span></span>  
  
     [!code-vb[VbXMLSamples#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#32)]  
  
-   <span data-ttu-id="31983-130">Przykład wyrażenia osadzone w zawartości elementu XML:</span><span class="sxs-lookup"><span data-stu-id="31983-130">Example of an embedded expression in the content of an XML element:</span></span>  
  
     [!code-vb[VbXMLSamples#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#33)]  
  
-   <span data-ttu-id="31983-131">Przykład wyrażenia osadzone w nazwie atrybutu elementu XML:</span><span class="sxs-lookup"><span data-stu-id="31983-131">Example of an embedded expression in an XML element attribute name:</span></span>  
  
     [!code-vb[VbXMLSamples#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#34)]  
  
-   <span data-ttu-id="31983-132">Przykład wyrażenia osadzone w wartości atrybutu elementu XML:</span><span class="sxs-lookup"><span data-stu-id="31983-132">Example of an embedded expression in an XML element attribute value:</span></span>  
  
     [!code-vb[VbXMLSamples#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#35)]  
  
-   <span data-ttu-id="31983-133">Przykład wyrażenia osadzone w atrybucie — element XML:</span><span class="sxs-lookup"><span data-stu-id="31983-133">Example of an embedded expression in an XML element attribute:</span></span>  
  
     [!code-vb[VbXMLSamples#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#36)]  
  
-   <span data-ttu-id="31983-134">Przykład wyrażenia osadzone w głównym elementem dokumentu XML:</span><span class="sxs-lookup"><span data-stu-id="31983-134">Example of an embedded expression in an XML document root element:</span></span>  
  
     [!code-vb[VbXMLSamples#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#37)]  
  
 <span data-ttu-id="31983-135">Po włączeniu `Option Strict`, kompilator sprawdza, czy typ każdego osadzone wyrażenia rozszerza się na wymagany typ.</span><span class="sxs-lookup"><span data-stu-id="31983-135">If you enable `Option Strict`, the compiler checks that the type of each embedded expression widens to the required type.</span></span> <span data-ttu-id="31983-136">Jedynym wyjątkiem jest, aby uzyskać element główny dokumentu XML, który jest weryfikowany, gdy kod działa.</span><span class="sxs-lookup"><span data-stu-id="31983-136">The only exception is for the root element of an XML document, which is verified when the code runs.</span></span> <span data-ttu-id="31983-137">Jeśli kompilujesz bez `Option Strict`, możesz osadzić wyrażeń o typie `Object` i ich typ jest weryfikowana w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="31983-137">If you compile without `Option Strict`, you can embed expressions of type `Object` and their type is verified at run time.</span></span>  
  
 <span data-ttu-id="31983-138">W lokalizacji, w którym zawartość jest opcjonalne osadzone wyrażenia, które zawierają `Nothing` są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="31983-138">In locations where content is optional, embedded expressions that contain `Nothing` are ignored.</span></span> <span data-ttu-id="31983-139">Oznacza to, nie trzeba sprawdzić zawartość elementu, wartości atrybutów i elementów tablicy nie są `Nothing` przed użyciem literał XML.</span><span class="sxs-lookup"><span data-stu-id="31983-139">This means you do not have to check that element content, attribute values, and array elements are not `Nothing` before you use an XML literal.</span></span> <span data-ttu-id="31983-140">Wymagane wartości, takich jak nazwy elementów i atrybutów, nie może być `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="31983-140">Required values, such as element and attribute names, cannot be `Nothing`.</span></span>  
  
 <span data-ttu-id="31983-141">Aby uzyskać więcej informacji na temat za pomocą wyrażenia osadzone w określonym typie literału, zobacz [literał dokumentu XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md), [literał elementu XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="31983-141">For more information about using an embedded expression in a particular type of literal, see [XML Document Literal](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md), [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="scoping-rules"></a><span data-ttu-id="31983-142">Wyznaczanie zakresu reguły</span><span class="sxs-lookup"><span data-stu-id="31983-142">Scoping Rules</span></span>  
 <span data-ttu-id="31983-143">Kompilator konwertuje literał XML wywołanie konstruktora dla odpowiedniego typu literału.</span><span class="sxs-lookup"><span data-stu-id="31983-143">The compiler converts each XML literal into a constructor call for the appropriate literal type.</span></span> <span data-ttu-id="31983-144">Zawartość literałową i wyrażenia osadzone w literał XML są przekazywane jako argumenty do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="31983-144">The literal content and embedded expressions in an XML literal are passed as arguments to the constructor.</span></span> <span data-ttu-id="31983-145">Oznacza to, że wszystkie dostępne literał XML elementy programowania Visual Basic są również dostępne dla jego wyrażenia osadzone.</span><span class="sxs-lookup"><span data-stu-id="31983-145">This means that all Visual Basic programming elements available to an XML literal are also available to its embedded expressions.</span></span>  
  
 <span data-ttu-id="31983-146">W literał XML, można uzyskać dostęp do przestrzeni nazw XML prefiksy zadeklarowanych za pomocą `Imports` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="31983-146">Within an XML literal, you can access the XML namespace prefixes declared with the `Imports` statement.</span></span> <span data-ttu-id="31983-147">Zadeklaruj nowy prefiks przestrzeni nazw XML lub w tle XML prefiks obszaru nazw, w elemencie przy użyciu `xmlns` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="31983-147">You can declare a new XML namespace prefix, or shadow an existing XML namespace prefix, in an element by using the `xmlns` attribute.</span></span> <span data-ttu-id="31983-148">Nowy obszar nazw jest dostępna, do węzłów podrzędnych tego elementu, ale nie do literałów XML w wyrażenia osadzone.</span><span class="sxs-lookup"><span data-stu-id="31983-148">The new namespace is available to the child nodes of that element, but not to XML literals in embedded expressions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="31983-149">Kiedy Deklarujesz prefiks przestrzeni nazw XML przy użyciu `xmlns` atrybut przestrzeni nazw, wartość atrybutu musi być ciągiem stałym.</span><span class="sxs-lookup"><span data-stu-id="31983-149">When you declare an XML namespace prefix by using the `xmlns` namespace attribute, the attribute value must be a constant string.</span></span> <span data-ttu-id="31983-150">W tym zakresie za pomocą `xmlns` przypomina za pomocą atrybutu `Imports` instrukcję, aby zadeklarować przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="31983-150">In this regard, using the `xmlns` attribute is like using the `Imports` statement to declare an XML namespace.</span></span> <span data-ttu-id="31983-151">Wyrażenia osadzone nie można użyć do określenia wartości przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="31983-151">You cannot use an embedded expression to specify the XML namespace value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31983-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="31983-152">See also</span></span>
- [<span data-ttu-id="31983-153">Tworzenie XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="31983-153">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="31983-154">Literał dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="31983-154">XML Document Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [<span data-ttu-id="31983-155">Literał elementu XML</span><span class="sxs-lookup"><span data-stu-id="31983-155">XML Element Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="31983-156">Option Strict, instrukcja</span><span class="sxs-lookup"><span data-stu-id="31983-156">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="31983-157">Imports, instrukcja (przestrzeń nazw i typ .NET)</span><span class="sxs-lookup"><span data-stu-id="31983-157">Imports Statement (.NET Namespace and Type)</span></span>](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="31983-158">Literały XML — przegląd</span><span class="sxs-lookup"><span data-stu-id="31983-158">XML Literals Overview</span></span>](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)
