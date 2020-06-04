---
title: Wyrażenia osadzone w XML
ms.date: 07/20/2015
f1_keywords:
- vb.XmlEmbeddedExpression
helpviewer_keywords:
- embedded expressions [Visual Basic]
- LINQ to XML [Visual Basic], embedded expressions
- XML literals [Visual Basic], embedded expressions
ms.assetid: bf2eb779-b751-4b7c-854f-9f2161482352
ms.openlocfilehash: d4ff9442aa82a3eb46d56500159562174646ea58
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410260"
---
# <a name="embedded-expressions-in-xml-visual-basic"></a><span data-ttu-id="244ae-102">Wyrażenia osadzone w XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="244ae-102">Embedded Expressions in XML (Visual Basic)</span></span>
<span data-ttu-id="244ae-103">Wyrażenia osadzone umożliwiają tworzenie literałów XML zawierających wyrażenia, które są oceniane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="244ae-103">Embedded expressions enable you to create XML literals that contain expressions that are evaluated at run time.</span></span> <span data-ttu-id="244ae-104">Składnia wyrażenia osadzonego jest `<%=` `expression` `%>` taka sama jak składnia użyta w ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="244ae-104">The syntax for an embedded expression is `<%=` `expression` `%>`, which is the same as the syntax used in ASP.NET.</span></span>  
  
 <span data-ttu-id="244ae-105">Na przykład można utworzyć literał elementu XML, łącząc osadzone wyrażenia z zawartością tekstu literalnego.</span><span class="sxs-lookup"><span data-stu-id="244ae-105">For example, you can create an XML element literal, combining embedded expressions with literal text content.</span></span>  
  
 [!code-vb[VbXMLSamples#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#27)]  
  
 <span data-ttu-id="244ae-106">Jeśli `isbnNumber` zawiera liczbę całkowitą 12345 i `modifiedDate` zawiera datę 3/5/2006, gdy ten kod jest wykonywany, wartość `book` jest:</span><span class="sxs-lookup"><span data-stu-id="244ae-106">If `isbnNumber` contains the integer 12345 and `modifiedDate` contains the date 3/5/2006, when this code executes, the value of `book` is:</span></span>  
  
```xml  
<book category="fiction" isbn="12345">  
  <modifiedDate>3/5/2006</modifiedDate>  
</book>  
```  
  
## <a name="embedded-expression-location-and-validation"></a><span data-ttu-id="244ae-107">Lokalizacja i walidacja wyrażenia osadzonego</span><span class="sxs-lookup"><span data-stu-id="244ae-107">Embedded Expression Location and Validation</span></span>  
 <span data-ttu-id="244ae-108">Wyrażenia osadzone mogą występować tylko w określonych lokalizacjach w wyrażeniach literałów XML.</span><span class="sxs-lookup"><span data-stu-id="244ae-108">Embedded expressions can appear only at certain locations within XML literal expressions.</span></span> <span data-ttu-id="244ae-109">Lokalizacja wyrażenia kontroluje, które typy mogą być zwracane przez wyrażenie i jak `Nothing` są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="244ae-109">The expression location controls which types the expression can return and how `Nothing` is handled.</span></span> <span data-ttu-id="244ae-110">W poniższej tabeli opisano dozwolone lokalizacje i typy osadzonych wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="244ae-110">The following table describes the allowed locations and types of embedded expressions.</span></span>  
  
|<span data-ttu-id="244ae-111">Lokalizacja w literale</span><span class="sxs-lookup"><span data-stu-id="244ae-111">Location in literal</span></span>|<span data-ttu-id="244ae-112">Typ wyrażenia</span><span class="sxs-lookup"><span data-stu-id="244ae-112">Type of expression</span></span>|<span data-ttu-id="244ae-113">Obsługa`Nothing`</span><span class="sxs-lookup"><span data-stu-id="244ae-113">Handling of `Nothing`</span></span>|  
|---|---|---|  
|<span data-ttu-id="244ae-114">Nazwa elementu XML</span><span class="sxs-lookup"><span data-stu-id="244ae-114">XML element name</span></span>|<xref:System.Xml.Linq.XName>|<span data-ttu-id="244ae-115">Błąd</span><span class="sxs-lookup"><span data-stu-id="244ae-115">Error</span></span>|  
|<span data-ttu-id="244ae-116">Zawartość elementu XML</span><span class="sxs-lookup"><span data-stu-id="244ae-116">XML element content</span></span>|<span data-ttu-id="244ae-117">`Object`lub tablica`Object`</span><span class="sxs-lookup"><span data-stu-id="244ae-117">`Object` or array of `Object`</span></span>|<span data-ttu-id="244ae-118">Ignorowane</span><span class="sxs-lookup"><span data-stu-id="244ae-118">Ignored</span></span>|  
|<span data-ttu-id="244ae-119">Nazwa atrybutu elementu XML</span><span class="sxs-lookup"><span data-stu-id="244ae-119">XML element attribute name</span></span>|<xref:System.Xml.Linq.XName>|<span data-ttu-id="244ae-120">Błąd, chyba że wartość atrybutu jest również`Nothing`</span><span class="sxs-lookup"><span data-stu-id="244ae-120">Error, unless the attribute value is also `Nothing`</span></span>|  
|<span data-ttu-id="244ae-121">Wartość atrybutu elementu XML</span><span class="sxs-lookup"><span data-stu-id="244ae-121">XML element attribute value</span></span>|`Object`|<span data-ttu-id="244ae-122">Zignorowano deklarację atrybutu</span><span class="sxs-lookup"><span data-stu-id="244ae-122">Attribute declaration ignored</span></span>|  
|<span data-ttu-id="244ae-123">Atrybut elementu XML</span><span class="sxs-lookup"><span data-stu-id="244ae-123">XML element attribute</span></span>|<span data-ttu-id="244ae-124"><xref:System.Xml.Linq.XAttribute>lub kolekcja<xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="244ae-124"><xref:System.Xml.Linq.XAttribute> or a collection of <xref:System.Xml.Linq.XAttribute></span></span>|<span data-ttu-id="244ae-125">Ignorowane</span><span class="sxs-lookup"><span data-stu-id="244ae-125">Ignored</span></span>|  
|<span data-ttu-id="244ae-126">Element główny dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="244ae-126">XML document root element</span></span>|<span data-ttu-id="244ae-127"><xref:System.Xml.Linq.XElement>lub kolekcja jednego <xref:System.Xml.Linq.XElement> obiektu i dowolnej liczby <xref:System.Xml.Linq.XProcessingInstruction> <xref:System.Xml.Linq.XComment> obiektów i</span><span class="sxs-lookup"><span data-stu-id="244ae-127"><xref:System.Xml.Linq.XElement> or a collection of one <xref:System.Xml.Linq.XElement> object and an arbitrary number of <xref:System.Xml.Linq.XProcessingInstruction> and <xref:System.Xml.Linq.XComment> objects</span></span>|<span data-ttu-id="244ae-128">Ignorowane</span><span class="sxs-lookup"><span data-stu-id="244ae-128">Ignored</span></span>|  
  
- <span data-ttu-id="244ae-129">Przykład wyrażenia osadzonego w nazwie elementu XML:</span><span class="sxs-lookup"><span data-stu-id="244ae-129">Example of an embedded expression in an XML element name:</span></span>  
  
     [!code-vb[VbXMLSamples#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#32)]  
  
- <span data-ttu-id="244ae-130">Przykład wyrażenia osadzonego w zawartości elementu XML:</span><span class="sxs-lookup"><span data-stu-id="244ae-130">Example of an embedded expression in the content of an XML element:</span></span>  
  
     [!code-vb[VbXMLSamples#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#33)]  
  
- <span data-ttu-id="244ae-131">Przykład wyrażenia osadzonego w nazwie atrybutu XML elementu:</span><span class="sxs-lookup"><span data-stu-id="244ae-131">Example of an embedded expression in an XML element attribute name:</span></span>  
  
     [!code-vb[VbXMLSamples#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#34)]  
  
- <span data-ttu-id="244ae-132">Przykład wyrażenia osadzonego w wartości atrybutu elementu XML:</span><span class="sxs-lookup"><span data-stu-id="244ae-132">Example of an embedded expression in an XML element attribute value:</span></span>  
  
     [!code-vb[VbXMLSamples#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#35)]  
  
- <span data-ttu-id="244ae-133">Przykład wyrażenia osadzonego w atrybucie elementu XML:</span><span class="sxs-lookup"><span data-stu-id="244ae-133">Example of an embedded expression in an XML element attribute:</span></span>  
  
     [!code-vb[VbXMLSamples#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#36)]  
  
- <span data-ttu-id="244ae-134">Przykład wyrażenia osadzonego w elemencie głównym dokumentu XML:</span><span class="sxs-lookup"><span data-stu-id="244ae-134">Example of an embedded expression in an XML document root element:</span></span>  
  
     [!code-vb[VbXMLSamples#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#37)]  
  
 <span data-ttu-id="244ae-135">W przypadku włączenia `Option Strict` programu kompilator sprawdza, czy typ każdego osadzonego wyrażenia jest rozszerzony do wymaganego typu.</span><span class="sxs-lookup"><span data-stu-id="244ae-135">If you enable `Option Strict`, the compiler checks that the type of each embedded expression widens to the required type.</span></span> <span data-ttu-id="244ae-136">Jedynym wyjątkiem jest element główny dokumentu XML, który jest sprawdzany, gdy kod jest uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="244ae-136">The only exception is for the root element of an XML document, which is verified when the code runs.</span></span> <span data-ttu-id="244ae-137">Jeśli kompilujesz bez `Option Strict` , możesz osadzić wyrażenia typu `Object` i ich typ jest weryfikowany w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="244ae-137">If you compile without `Option Strict`, you can embed expressions of type `Object` and their type is verified at run time.</span></span>  
  
 <span data-ttu-id="244ae-138">W lokalizacjach, w których zawartość jest opcjonalna, osadzone wyrażenia, które zawierają `Nothing` są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="244ae-138">In locations where content is optional, embedded expressions that contain `Nothing` are ignored.</span></span> <span data-ttu-id="244ae-139">Oznacza to, że nie trzeba sprawdzać zawartości elementu, wartości atrybutów ani elementów tablicy `Nothing` przed użyciem literału XML.</span><span class="sxs-lookup"><span data-stu-id="244ae-139">This means you do not have to check that element content, attribute values, and array elements are not `Nothing` before you use an XML literal.</span></span> <span data-ttu-id="244ae-140">Wymagane wartości, takie jak nazwy elementów i atrybutów, nie mogą być `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="244ae-140">Required values, such as element and attribute names, cannot be `Nothing`.</span></span>  
  
 <span data-ttu-id="244ae-141">Aby uzyskać więcej informacji o używaniu wyrażenia osadzonego w określonym typie literału, zobacz [literał dokumentu XML](../../../language-reference/xml-literals/xml-document-literal.md), [literał elementu XML](../../../language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="244ae-141">For more information about using an embedded expression in a particular type of literal, see [XML Document Literal](../../../language-reference/xml-literals/xml-document-literal.md), [XML Element Literal](../../../language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="scoping-rules"></a><span data-ttu-id="244ae-142">Reguły określania zakresu</span><span class="sxs-lookup"><span data-stu-id="244ae-142">Scoping Rules</span></span>  
 <span data-ttu-id="244ae-143">Kompilator konwertuje każdy literał XML na wywołanie konstruktora dla odpowiedniego typu literału.</span><span class="sxs-lookup"><span data-stu-id="244ae-143">The compiler converts each XML literal into a constructor call for the appropriate literal type.</span></span> <span data-ttu-id="244ae-144">Zawartość literału i osadzone wyrażenia w literale XML są przekazane jako argumenty do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="244ae-144">The literal content and embedded expressions in an XML literal are passed as arguments to the constructor.</span></span> <span data-ttu-id="244ae-145">Oznacza to, że wszystkie Visual Basic elementy programistyczne dostępne dla literału XML są również dostępne dla jego osadzonych wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="244ae-145">This means that all Visual Basic programming elements available to an XML literal are also available to its embedded expressions.</span></span>  
  
 <span data-ttu-id="244ae-146">W literale XML można uzyskać dostęp do prefiksów przestrzeni nazw XML zadeklarowanych za pomocą `Imports` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="244ae-146">Within an XML literal, you can access the XML namespace prefixes declared with the `Imports` statement.</span></span> <span data-ttu-id="244ae-147">Można zadeklarować nowy prefiks przestrzeni nazw XML lub zaobserwować istniejący prefiks przestrzeni nazw XML w elemencie przy użyciu `xmlns` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="244ae-147">You can declare a new XML namespace prefix, or shadow an existing XML namespace prefix, in an element by using the `xmlns` attribute.</span></span> <span data-ttu-id="244ae-148">Nowa przestrzeń nazw jest dostępna dla węzłów podrzędnych tego elementu, ale nie do literałów XML w wyrażeniach osadzonych.</span><span class="sxs-lookup"><span data-stu-id="244ae-148">The new namespace is available to the child nodes of that element, but not to XML literals in embedded expressions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="244ae-149">W przypadku deklarowania prefiksu przestrzeni nazw XML przy użyciu `xmlns` atrybutu Namespace wartość atrybutu musi być ciągiem stałym.</span><span class="sxs-lookup"><span data-stu-id="244ae-149">When you declare an XML namespace prefix by using the `xmlns` namespace attribute, the attribute value must be a constant string.</span></span> <span data-ttu-id="244ae-150">W tym zakresie użycie `xmlns` atrybutu jest podobne do użycia instrukcji w `Imports` celu zadeklarowania przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="244ae-150">In this regard, using the `xmlns` attribute is like using the `Imports` statement to declare an XML namespace.</span></span> <span data-ttu-id="244ae-151">Nie można użyć wyrażenia osadzonego do określenia wartości przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="244ae-151">You cannot use an embedded expression to specify the XML namespace value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="244ae-152">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="244ae-152">See also</span></span>

- [<span data-ttu-id="244ae-153">Tworzenie XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="244ae-153">Creating XML in Visual Basic</span></span>](creating-xml.md)
- [<span data-ttu-id="244ae-154">Literał dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="244ae-154">XML Document Literal</span></span>](../../../language-reference/xml-literals/xml-document-literal.md)
- [<span data-ttu-id="244ae-155">Literał elementu XML</span><span class="sxs-lookup"><span data-stu-id="244ae-155">XML Element Literal</span></span>](../../../language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="244ae-156">Option Strict — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="244ae-156">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="244ae-157">Imports — Instrukcja (.NET Namespace i Type)</span><span class="sxs-lookup"><span data-stu-id="244ae-157">Imports Statement (.NET Namespace and Type)</span></span>](../../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="244ae-158">Literały XML - Przegląd</span><span class="sxs-lookup"><span data-stu-id="244ae-158">XML Literals Overview</span></span>](xml-literals-overview.md)
