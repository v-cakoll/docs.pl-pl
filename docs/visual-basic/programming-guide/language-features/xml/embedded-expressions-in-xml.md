---
title: "Wyrażenia osadzone w XML (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vb.XmlEmbeddedExpression
helpviewer_keywords:
- embedded expressions [Visual Basic]
- LINQ to XML [Visual Basic], embedded expressions
- XML literals [Visual Basic], embedded expressions
ms.assetid: bf2eb779-b751-4b7c-854f-9f2161482352
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b1cdba0a39a932f143ac98c2514240e1696a8fe0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="embedded-expressions-in-xml-visual-basic"></a><span data-ttu-id="04baa-102">Wyrażenia osadzone w XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="04baa-102">Embedded Expressions in XML (Visual Basic)</span></span>
<span data-ttu-id="04baa-103">Wyrażenia osadzone umożliwiają tworzenie literałów XML, które zawierają wyrażenia, które są oceniane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="04baa-103">Embedded expressions enable you to create XML literals that contain expressions that are evaluated at run time.</span></span> <span data-ttu-id="04baa-104">Składnia wyrażenia osadzonego jest `<%=` `expression` `%>`, który jest taki sam jak używać składni w [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)].</span><span class="sxs-lookup"><span data-stu-id="04baa-104">The syntax for an embedded expression is `<%=` `expression` `%>`, which is the same as the syntax used in [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)].</span></span>  
  
 <span data-ttu-id="04baa-105">Na przykład utworzeniem — element XML literału, łączenia wyrażenia osadzone pomocą zawartości tekstowej literału.</span><span class="sxs-lookup"><span data-stu-id="04baa-105">For example, you can create an XML element literal, combining embedded expressions with literal text content.</span></span>  
  
 [!code-vb[VbXMLSamples#27](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_1.vb)]  
  
 <span data-ttu-id="04baa-106">Jeśli `isbnNumber` zawiera całkowitą 12345 i `modifiedDate` zawiera datę 3/5/2006, gdy ten kod jest wykonywana, wartość `book` jest:</span><span class="sxs-lookup"><span data-stu-id="04baa-106">If `isbnNumber` contains the integer 12345 and `modifiedDate` contains the date 3/5/2006, when this code executes, the value of `book` is:</span></span>  
  
```xml  
<book category="fiction" isbn="12345">  
  <modifiedDate>3/5/2006</modifiedDate>  
</book>  
```  
  
## <a name="embedded-expression-location-and-validation"></a><span data-ttu-id="04baa-107">Wyrażenia osadzonego lokalizacji i sprawdzania poprawności</span><span class="sxs-lookup"><span data-stu-id="04baa-107">Embedded Expression Location and Validation</span></span>  
 <span data-ttu-id="04baa-108">Wyrażenia osadzone może występować tylko w określonych lokalizacjach w wyrażeniach literału XML.</span><span class="sxs-lookup"><span data-stu-id="04baa-108">Embedded expressions can appear only at certain locations within XML literal expressions.</span></span> <span data-ttu-id="04baa-109">Rozwiązania lokalizacji wyrażenie, które typy wyrażenie, które może zwracać i w jaki sposób `Nothing` jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="04baa-109">The expression location controls which types the expression can return and how `Nothing` is handled.</span></span> <span data-ttu-id="04baa-110">W poniższej tabeli opisano dozwolonych lokalizacji i typy osadzone wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="04baa-110">The following table describes the allowed locations and types of embedded expressions.</span></span>  
  
|<span data-ttu-id="04baa-111">Lokalizacja w literale</span><span class="sxs-lookup"><span data-stu-id="04baa-111">Location in literal</span></span>|<span data-ttu-id="04baa-112">Typ wyrażenia</span><span class="sxs-lookup"><span data-stu-id="04baa-112">Type of expression</span></span>|<span data-ttu-id="04baa-113">Obsługa`Nothing`</span><span class="sxs-lookup"><span data-stu-id="04baa-113">Handling of `Nothing`</span></span>|  
|---|---|---|  
|<span data-ttu-id="04baa-114">Nazwa elementu XML</span><span class="sxs-lookup"><span data-stu-id="04baa-114">XML element name</span></span>|<xref:System.Xml.Linq.XName>|<span data-ttu-id="04baa-115">Błąd</span><span class="sxs-lookup"><span data-stu-id="04baa-115">Error</span></span>|  
|<span data-ttu-id="04baa-116">Treść elementu XML.</span><span class="sxs-lookup"><span data-stu-id="04baa-116">XML element content</span></span>|<span data-ttu-id="04baa-117">`Object`tablica lub`Object`</span><span class="sxs-lookup"><span data-stu-id="04baa-117">`Object` or array of `Object`</span></span>|<span data-ttu-id="04baa-118">Ignorowane</span><span class="sxs-lookup"><span data-stu-id="04baa-118">Ignored</span></span>|  
|<span data-ttu-id="04baa-119">Nazwa atrybutu element XML</span><span class="sxs-lookup"><span data-stu-id="04baa-119">XML element attribute name</span></span>|<xref:System.Xml.Linq.XName>|<span data-ttu-id="04baa-120">Błąd, chyba że wartość atrybutu jest również`Nothing`</span><span class="sxs-lookup"><span data-stu-id="04baa-120">Error, unless the attribute value is also `Nothing`</span></span>|  
|<span data-ttu-id="04baa-121">Wartość atrybutu element XML</span><span class="sxs-lookup"><span data-stu-id="04baa-121">XML element attribute value</span></span>|`Object`|<span data-ttu-id="04baa-122">Atrybut deklaracja ignorowana</span><span class="sxs-lookup"><span data-stu-id="04baa-122">Attribute declaration ignored</span></span>|  
|<span data-ttu-id="04baa-123">Atrybut — element XML</span><span class="sxs-lookup"><span data-stu-id="04baa-123">XML element attribute</span></span>|<span data-ttu-id="04baa-124"><xref:System.Xml.Linq.XAttribute>lub kolekcji<xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="04baa-124"><xref:System.Xml.Linq.XAttribute> or a collection of <xref:System.Xml.Linq.XAttribute></span></span>|<span data-ttu-id="04baa-125">Ignorowane</span><span class="sxs-lookup"><span data-stu-id="04baa-125">Ignored</span></span>|  
|<span data-ttu-id="04baa-126">Element główny dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="04baa-126">XML document root element</span></span>|<span data-ttu-id="04baa-127"><xref:System.Xml.Linq.XElement>lub Kolekcja jednej <xref:System.Xml.Linq.XElement> obiekt i dowolnej liczby <xref:System.Xml.Linq.XProcessingInstruction> i <xref:System.Xml.Linq.XComment> obiektów</span><span class="sxs-lookup"><span data-stu-id="04baa-127"><xref:System.Xml.Linq.XElement> or a collection of one <xref:System.Xml.Linq.XElement> object and an arbitrary number of <xref:System.Xml.Linq.XProcessingInstruction> and <xref:System.Xml.Linq.XComment> objects</span></span>|<span data-ttu-id="04baa-128">Ignorowane</span><span class="sxs-lookup"><span data-stu-id="04baa-128">Ignored</span></span>|  
  
-   <span data-ttu-id="04baa-129">Przykład wyrażenia osadzonego w nazwie elementu XML:</span><span class="sxs-lookup"><span data-stu-id="04baa-129">Example of an embedded expression in an XML element name:</span></span>  
  
     [!code-vb[VbXMLSamples#32](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_2.vb)]  
  
-   <span data-ttu-id="04baa-130">Przykład wyrażenia osadzonego w zawartości elementu XML:</span><span class="sxs-lookup"><span data-stu-id="04baa-130">Example of an embedded expression in the content of an XML element:</span></span>  
  
     [!code-vb[VbXMLSamples#33](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_3.vb)]  
  
-   <span data-ttu-id="04baa-131">Przykład wyrażenia osadzonego w nazwie atrybutu elementu XML:</span><span class="sxs-lookup"><span data-stu-id="04baa-131">Example of an embedded expression in an XML element attribute name:</span></span>  
  
     [!code-vb[VbXMLSamples#34](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_4.vb)]  
  
-   <span data-ttu-id="04baa-132">Przykład wyrażenia osadzonego w wartości atrybutu XML elementu:</span><span class="sxs-lookup"><span data-stu-id="04baa-132">Example of an embedded expression in an XML element attribute value:</span></span>  
  
     [!code-vb[VbXMLSamples#35](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_5.vb)]  
  
-   <span data-ttu-id="04baa-133">Przykład wyrażenia osadzonego w atrybucie elementu XML:</span><span class="sxs-lookup"><span data-stu-id="04baa-133">Example of an embedded expression in an XML element attribute:</span></span>  
  
     [!code-vb[VbXMLSamples#36](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_6.vb)]  
  
-   <span data-ttu-id="04baa-134">Przykład wyrażenia osadzonego w głównym elementem dokumentu XML:</span><span class="sxs-lookup"><span data-stu-id="04baa-134">Example of an embedded expression in an XML document root element:</span></span>  
  
     [!code-vb[VbXMLSamples#37](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_7.vb)]  
  
 <span data-ttu-id="04baa-135">Po włączeniu `Option Strict`, kompilator sprawdza, czy typ każdego wyrażenia osadzonego rozszerzenie na wymagany typ.</span><span class="sxs-lookup"><span data-stu-id="04baa-135">If you enable `Option Strict`, the compiler checks that the type of each embedded expression widens to the required type.</span></span> <span data-ttu-id="04baa-136">Jedynym wyjątkiem jest dla elementu głównego dokumentu XML, która została zweryfikowana, gdy kod działa.</span><span class="sxs-lookup"><span data-stu-id="04baa-136">The only exception is for the root element of an XML document, which is verified when the code runs.</span></span> <span data-ttu-id="04baa-137">Jeśli kompilacja bez `Option Strict`, można osadzić wyrażeń typu `Object` i typem jest weryfikowana w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="04baa-137">If you compile without `Option Strict`, you can embed expressions of type `Object` and their type is verified at run time.</span></span>  
  
 <span data-ttu-id="04baa-138">W lokalizacji, której zawartość jest opcjonalne osadzone wyrażenia, które zawierają `Nothing` są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="04baa-138">In locations where content is optional, embedded expressions that contain `Nothing` are ignored.</span></span> <span data-ttu-id="04baa-139">Oznacza to, nie trzeba sprawdzić tej zawartości elementu wartości atrybutów i elementów tablicy nie są `Nothing` przed użyciem literał XML.</span><span class="sxs-lookup"><span data-stu-id="04baa-139">This means you do not have to check that element content, attribute values, and array elements are not `Nothing` before you use an XML literal.</span></span> <span data-ttu-id="04baa-140">Wymagane wartości, takich jak nazwy elementów i atrybutów, nie mogą być `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="04baa-140">Required values, such as element and attribute names, cannot be `Nothing`.</span></span>  
  
 <span data-ttu-id="04baa-141">Aby uzyskać więcej informacji o używaniu wyrażenia osadzonego w określonego typu literal, zobacz [literał dokumentu XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md), [literał elementu XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="04baa-141">For more information about using an embedded expression in a particular type of literal, see [XML Document Literal](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md), [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="scoping-rules"></a><span data-ttu-id="04baa-142">Zakres reguły</span><span class="sxs-lookup"><span data-stu-id="04baa-142">Scoping Rules</span></span>  
 <span data-ttu-id="04baa-143">Kompilator konwertuje literał XML na wywołanie konstruktora dla odpowiedniego typu literału.</span><span class="sxs-lookup"><span data-stu-id="04baa-143">The compiler converts each XML literal into a constructor call for the appropriate literal type.</span></span> <span data-ttu-id="04baa-144">Zawartość literalna i wyrażenia osadzone w literał XML są przekazywane jako argumenty konstruktora.</span><span class="sxs-lookup"><span data-stu-id="04baa-144">The literal content and embedded expressions in an XML literal are passed as arguments to the constructor.</span></span> <span data-ttu-id="04baa-145">Oznacza to, że wszystkie [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programistyczny literał XML dostępne są również dostępne dla jego wyrażenia osadzonego.</span><span class="sxs-lookup"><span data-stu-id="04baa-145">This means that all [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programming elements available to an XML literal are also available to its embedded expressions.</span></span>  
  
 <span data-ttu-id="04baa-146">Wewnątrz literału XML, można uzyskać dostępu do przestrzeni nazw XML prefiksy zadeklarowana z `Imports` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="04baa-146">Within an XML literal, you can access the XML namespace prefixes declared with the `Imports` statement.</span></span> <span data-ttu-id="04baa-147">Zadeklaruj nowy prefiks przestrzeni nazw XML lub w tle XML prefiks obszaru nazw, w elemencie przy użyciu `xmlns` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="04baa-147">You can declare a new XML namespace prefix, or shadow an existing XML namespace prefix, in an element by using the `xmlns` attribute.</span></span> <span data-ttu-id="04baa-148">Nowa przestrzeń nazw jest dostępna, do węzłów podrzędnych tego elementu, ale nie do literałów XML w wyrażeniach osadzonych.</span><span class="sxs-lookup"><span data-stu-id="04baa-148">The new namespace is available to the child nodes of that element, but not to XML literals in embedded expressions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="04baa-149">Gdy deklaruje prefiks przestrzeni nazw XML przy użyciu `xmlns` atrybutu przestrzeni nazw, wartość atrybutu musi być ciągiem stałym.</span><span class="sxs-lookup"><span data-stu-id="04baa-149">When you declare an XML namespace prefix by using the `xmlns` namespace attribute, the attribute value must be a constant string.</span></span> <span data-ttu-id="04baa-150">W tym zakresie przy użyciu `xmlns` przypomina przy użyciu atrybutu `Imports` instrukcji, aby zadeklarować przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="04baa-150">In this regard, using the `xmlns` attribute is like using the `Imports` statement to declare an XML namespace.</span></span> <span data-ttu-id="04baa-151">Aby określić wartość przestrzeni nazw XML, nie można użyć wyrażenia osadzonego.</span><span class="sxs-lookup"><span data-stu-id="04baa-151">You cannot use an embedded expression to specify the XML namespace value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04baa-152">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="04baa-152">See Also</span></span>  
 [<span data-ttu-id="04baa-153">Tworzenie XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="04baa-153">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="04baa-154">Literał dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="04baa-154">XML Document Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)  
 [<span data-ttu-id="04baa-155">Literał elementu XML</span><span class="sxs-lookup"><span data-stu-id="04baa-155">XML Element Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [<span data-ttu-id="04baa-156">Option Strict — instrukcja</span><span class="sxs-lookup"><span data-stu-id="04baa-156">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="04baa-157">Imports — instrukcja (.NET Namespace i Type)</span><span class="sxs-lookup"><span data-stu-id="04baa-157">Imports Statement (.NET Namespace and Type)</span></span>](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [<span data-ttu-id="04baa-158">Literały XML-Przegląd</span><span class="sxs-lookup"><span data-stu-id="04baa-158">XML Literals Overview</span></span>](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)
