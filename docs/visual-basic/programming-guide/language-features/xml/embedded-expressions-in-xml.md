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
ms.openlocfilehash: 0cdb960160457108ddf18c554dae5f5993269833
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74332355"
---
# <a name="embedded-expressions-in-xml-visual-basic"></a><span data-ttu-id="da5fa-102">Wyrażenia osadzone w XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="da5fa-102">Embedded Expressions in XML (Visual Basic)</span></span>
<span data-ttu-id="da5fa-103">Wyrażenia osadzone umożliwiają tworzenie literałów XML zawierających wyrażenia, które są oceniane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="da5fa-103">Embedded expressions enable you to create XML literals that contain expressions that are evaluated at run time.</span></span> <span data-ttu-id="da5fa-104">Składnia wyrażenia osadzonego jest `<%=` `expression` `%>`, która jest taka sama jak składnia używana w ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="da5fa-104">The syntax for an embedded expression is `<%=` `expression` `%>`, which is the same as the syntax used in ASP.NET.</span></span>  
  
 <span data-ttu-id="da5fa-105">Na przykład można utworzyć literał elementu XML, łącząc osadzone wyrażenia z zawartością tekstu literalnego.</span><span class="sxs-lookup"><span data-stu-id="da5fa-105">For example, you can create an XML element literal, combining embedded expressions with literal text content.</span></span>  
  
 [!code-vb[VbXMLSamples#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#27)]  
  
 <span data-ttu-id="da5fa-106">Jeśli `isbnNumber` zawiera liczbę całkowitą 12345 i `modifiedDate` zawiera datę 3/5/2006, gdy ten kod jest wykonywany, wartością `book` jest:</span><span class="sxs-lookup"><span data-stu-id="da5fa-106">If `isbnNumber` contains the integer 12345 and `modifiedDate` contains the date 3/5/2006, when this code executes, the value of `book` is:</span></span>  
  
```xml  
<book category="fiction" isbn="12345">  
  <modifiedDate>3/5/2006</modifiedDate>  
</book>  
```  
  
## <a name="embedded-expression-location-and-validation"></a><span data-ttu-id="da5fa-107">Lokalizacja i walidacja wyrażenia osadzonego</span><span class="sxs-lookup"><span data-stu-id="da5fa-107">Embedded Expression Location and Validation</span></span>  
 <span data-ttu-id="da5fa-108">Wyrażenia osadzone mogą występować tylko w określonych lokalizacjach w wyrażeniach literałów XML.</span><span class="sxs-lookup"><span data-stu-id="da5fa-108">Embedded expressions can appear only at certain locations within XML literal expressions.</span></span> <span data-ttu-id="da5fa-109">Lokalizacja wyrażenia określa typy, które mogą być zwracane przez wyrażenie, oraz sposób obsługi `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="da5fa-109">The expression location controls which types the expression can return and how `Nothing` is handled.</span></span> <span data-ttu-id="da5fa-110">W poniższej tabeli opisano dozwolone lokalizacje i typy osadzonych wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="da5fa-110">The following table describes the allowed locations and types of embedded expressions.</span></span>  
  
|<span data-ttu-id="da5fa-111">Lokalizacja w literale</span><span class="sxs-lookup"><span data-stu-id="da5fa-111">Location in literal</span></span>|<span data-ttu-id="da5fa-112">Typ wyrażenia</span><span class="sxs-lookup"><span data-stu-id="da5fa-112">Type of expression</span></span>|<span data-ttu-id="da5fa-113">Obsługa `Nothing`</span><span class="sxs-lookup"><span data-stu-id="da5fa-113">Handling of `Nothing`</span></span>|  
|---|---|---|  
|<span data-ttu-id="da5fa-114">Nazwa elementu XML</span><span class="sxs-lookup"><span data-stu-id="da5fa-114">XML element name</span></span>|<xref:System.Xml.Linq.XName>|<span data-ttu-id="da5fa-115">Błąd</span><span class="sxs-lookup"><span data-stu-id="da5fa-115">Error</span></span>|  
|<span data-ttu-id="da5fa-116">Zawartość elementu XML</span><span class="sxs-lookup"><span data-stu-id="da5fa-116">XML element content</span></span>|<span data-ttu-id="da5fa-117">`Object` lub tablica `Object`</span><span class="sxs-lookup"><span data-stu-id="da5fa-117">`Object` or array of `Object`</span></span>|<span data-ttu-id="da5fa-118">Ignorowane</span><span class="sxs-lookup"><span data-stu-id="da5fa-118">Ignored</span></span>|  
|<span data-ttu-id="da5fa-119">Nazwa atrybutu elementu XML</span><span class="sxs-lookup"><span data-stu-id="da5fa-119">XML element attribute name</span></span>|<xref:System.Xml.Linq.XName>|<span data-ttu-id="da5fa-120">Błąd, chyba że wartość atrybutu jest również `Nothing`</span><span class="sxs-lookup"><span data-stu-id="da5fa-120">Error, unless the attribute value is also `Nothing`</span></span>|  
|<span data-ttu-id="da5fa-121">Wartość atrybutu elementu XML</span><span class="sxs-lookup"><span data-stu-id="da5fa-121">XML element attribute value</span></span>|`Object`|<span data-ttu-id="da5fa-122">Zignorowano deklarację atrybutu</span><span class="sxs-lookup"><span data-stu-id="da5fa-122">Attribute declaration ignored</span></span>|  
|<span data-ttu-id="da5fa-123">Atrybut elementu XML</span><span class="sxs-lookup"><span data-stu-id="da5fa-123">XML element attribute</span></span>|<span data-ttu-id="da5fa-124"><xref:System.Xml.Linq.XAttribute> lub kolekcja <xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="da5fa-124"><xref:System.Xml.Linq.XAttribute> or a collection of <xref:System.Xml.Linq.XAttribute></span></span>|<span data-ttu-id="da5fa-125">Ignorowane</span><span class="sxs-lookup"><span data-stu-id="da5fa-125">Ignored</span></span>|  
|<span data-ttu-id="da5fa-126">Element główny dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="da5fa-126">XML document root element</span></span>|<span data-ttu-id="da5fa-127"><xref:System.Xml.Linq.XElement> lub kolekcja jednego obiektu <xref:System.Xml.Linq.XElement> i dowolną liczbę obiektów <xref:System.Xml.Linq.XProcessingInstruction> i <xref:System.Xml.Linq.XComment></span><span class="sxs-lookup"><span data-stu-id="da5fa-127"><xref:System.Xml.Linq.XElement> or a collection of one <xref:System.Xml.Linq.XElement> object and an arbitrary number of <xref:System.Xml.Linq.XProcessingInstruction> and <xref:System.Xml.Linq.XComment> objects</span></span>|<span data-ttu-id="da5fa-128">Ignorowane</span><span class="sxs-lookup"><span data-stu-id="da5fa-128">Ignored</span></span>|  
  
- <span data-ttu-id="da5fa-129">Przykład wyrażenia osadzonego w nazwie elementu XML:</span><span class="sxs-lookup"><span data-stu-id="da5fa-129">Example of an embedded expression in an XML element name:</span></span>  
  
     [!code-vb[VbXMLSamples#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#32)]  
  
- <span data-ttu-id="da5fa-130">Przykład wyrażenia osadzonego w zawartości elementu XML:</span><span class="sxs-lookup"><span data-stu-id="da5fa-130">Example of an embedded expression in the content of an XML element:</span></span>  
  
     [!code-vb[VbXMLSamples#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#33)]  
  
- <span data-ttu-id="da5fa-131">Przykład wyrażenia osadzonego w nazwie atrybutu XML elementu:</span><span class="sxs-lookup"><span data-stu-id="da5fa-131">Example of an embedded expression in an XML element attribute name:</span></span>  
  
     [!code-vb[VbXMLSamples#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#34)]  
  
- <span data-ttu-id="da5fa-132">Przykład wyrażenia osadzonego w wartości atrybutu elementu XML:</span><span class="sxs-lookup"><span data-stu-id="da5fa-132">Example of an embedded expression in an XML element attribute value:</span></span>  
  
     [!code-vb[VbXMLSamples#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#35)]  
  
- <span data-ttu-id="da5fa-133">Przykład wyrażenia osadzonego w atrybucie elementu XML:</span><span class="sxs-lookup"><span data-stu-id="da5fa-133">Example of an embedded expression in an XML element attribute:</span></span>  
  
     [!code-vb[VbXMLSamples#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#36)]  
  
- <span data-ttu-id="da5fa-134">Przykład wyrażenia osadzonego w elemencie głównym dokumentu XML:</span><span class="sxs-lookup"><span data-stu-id="da5fa-134">Example of an embedded expression in an XML document root element:</span></span>  
  
     [!code-vb[VbXMLSamples#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#37)]  
  
 <span data-ttu-id="da5fa-135">Jeśli włączysz `Option Strict`, kompilator sprawdzi, czy typ poszczególnych wyrażeń osadzonych poszerza do wymaganego typu.</span><span class="sxs-lookup"><span data-stu-id="da5fa-135">If you enable `Option Strict`, the compiler checks that the type of each embedded expression widens to the required type.</span></span> <span data-ttu-id="da5fa-136">Jedynym wyjątkiem jest element główny dokumentu XML, który jest sprawdzany, gdy kod jest uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="da5fa-136">The only exception is for the root element of an XML document, which is verified when the code runs.</span></span> <span data-ttu-id="da5fa-137">Jeśli kompilujesz bez `Option Strict`, możesz osadzić wyrażenia typu `Object` i ich typ jest weryfikowany w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="da5fa-137">If you compile without `Option Strict`, you can embed expressions of type `Object` and their type is verified at run time.</span></span>  
  
 <span data-ttu-id="da5fa-138">W lokalizacjach, w których zawartość jest opcjonalna, osadzone wyrażenia zawierające `Nothing` są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="da5fa-138">In locations where content is optional, embedded expressions that contain `Nothing` are ignored.</span></span> <span data-ttu-id="da5fa-139">Oznacza to, że nie trzeba sprawdzać zawartości elementu, wartości atrybutów ani elementów tablicy nie `Nothing` przed użyciem literału XML.</span><span class="sxs-lookup"><span data-stu-id="da5fa-139">This means you do not have to check that element content, attribute values, and array elements are not `Nothing` before you use an XML literal.</span></span> <span data-ttu-id="da5fa-140">Nie można `Nothing`wymaganych wartości, takich jak nazwy elementów i atrybutów.</span><span class="sxs-lookup"><span data-stu-id="da5fa-140">Required values, such as element and attribute names, cannot be `Nothing`.</span></span>  
  
 <span data-ttu-id="da5fa-141">Aby uzyskać więcej informacji o używaniu wyrażenia osadzonego w określonym typie literału, zobacz [literał dokumentu XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md), [literał elementu XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="da5fa-141">For more information about using an embedded expression in a particular type of literal, see [XML Document Literal](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md), [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="scoping-rules"></a><span data-ttu-id="da5fa-142">Reguły określania zakresu</span><span class="sxs-lookup"><span data-stu-id="da5fa-142">Scoping Rules</span></span>  
 <span data-ttu-id="da5fa-143">Kompilator konwertuje każdy literał XML na wywołanie konstruktora dla odpowiedniego typu literału.</span><span class="sxs-lookup"><span data-stu-id="da5fa-143">The compiler converts each XML literal into a constructor call for the appropriate literal type.</span></span> <span data-ttu-id="da5fa-144">Zawartość literału i osadzone wyrażenia w literale XML są przekazane jako argumenty do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="da5fa-144">The literal content and embedded expressions in an XML literal are passed as arguments to the constructor.</span></span> <span data-ttu-id="da5fa-145">Oznacza to, że wszystkie Visual Basic elementy programistyczne dostępne dla literału XML są również dostępne dla jego osadzonych wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="da5fa-145">This means that all Visual Basic programming elements available to an XML literal are also available to its embedded expressions.</span></span>  
  
 <span data-ttu-id="da5fa-146">W literale XML można uzyskać dostęp do prefiksów przestrzeni nazw XML zadeklarowanych za pomocą instrukcji `Imports`.</span><span class="sxs-lookup"><span data-stu-id="da5fa-146">Within an XML literal, you can access the XML namespace prefixes declared with the `Imports` statement.</span></span> <span data-ttu-id="da5fa-147">Można zadeklarować nowy prefiks przestrzeni nazw XML lub zaobserwować istniejący prefiks przestrzeni nazw XML w elemencie przy użyciu atrybutu `xmlns`.</span><span class="sxs-lookup"><span data-stu-id="da5fa-147">You can declare a new XML namespace prefix, or shadow an existing XML namespace prefix, in an element by using the `xmlns` attribute.</span></span> <span data-ttu-id="da5fa-148">Nowa przestrzeń nazw jest dostępna dla węzłów podrzędnych tego elementu, ale nie do literałów XML w wyrażeniach osadzonych.</span><span class="sxs-lookup"><span data-stu-id="da5fa-148">The new namespace is available to the child nodes of that element, but not to XML literals in embedded expressions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="da5fa-149">W przypadku deklarowania prefiksu przestrzeni nazw XML przy użyciu atrybutu przestrzeni nazw `xmlns`, wartość atrybutu musi być ciągiem stałym.</span><span class="sxs-lookup"><span data-stu-id="da5fa-149">When you declare an XML namespace prefix by using the `xmlns` namespace attribute, the attribute value must be a constant string.</span></span> <span data-ttu-id="da5fa-150">W tym względzie użycie atrybutu `xmlns` jest podobne do deklarowania przestrzeni nazw XML przy użyciu instrukcji `Imports`.</span><span class="sxs-lookup"><span data-stu-id="da5fa-150">In this regard, using the `xmlns` attribute is like using the `Imports` statement to declare an XML namespace.</span></span> <span data-ttu-id="da5fa-151">Nie można użyć wyrażenia osadzonego do określenia wartości przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="da5fa-151">You cannot use an embedded expression to specify the XML namespace value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da5fa-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="da5fa-152">See also</span></span>

- [<span data-ttu-id="da5fa-153">Tworzenie kodu XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="da5fa-153">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="da5fa-154">Literał dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="da5fa-154">XML Document Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [<span data-ttu-id="da5fa-155">Literał elementu XML</span><span class="sxs-lookup"><span data-stu-id="da5fa-155">XML Element Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="da5fa-156">Option Strict, instrukcja</span><span class="sxs-lookup"><span data-stu-id="da5fa-156">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="da5fa-157">Imports, instrukcja (przestrzeń nazw i typ .NET)</span><span class="sxs-lookup"><span data-stu-id="da5fa-157">Imports Statement (.NET Namespace and Type)</span></span>](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="da5fa-158">Literały XML — przegląd</span><span class="sxs-lookup"><span data-stu-id="da5fa-158">XML Literals Overview</span></span>](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)
