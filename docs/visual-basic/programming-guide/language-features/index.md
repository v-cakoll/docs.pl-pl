---
title: "Funkcje języka Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, elements of
- Visual Basic code
ms.assetid: b0b21730-298c-47e6-9a2f-cc81f628067b
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f7074206baa51259592cca3fdc224d99438791f9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="visual-basic-language-features"></a><span data-ttu-id="38580-102">Funkcje języka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="38580-102">Visual Basic Language Features</span></span>
<span data-ttu-id="38580-103">Poniższe tematy przedstawienie i omówienie podstawowych składników [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], zorientowany obiektowo język programowania.</span><span class="sxs-lookup"><span data-stu-id="38580-103">The following topics introduce and discuss the essential components of [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], an object-oriented programming language.</span></span> <span data-ttu-id="38580-104">Po utworzeniu aplikacji przy użyciu formularzy i kontrolek interfejsu użytkownika, należy napisać kod, który definiuje zachowanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="38580-104">After creating the user interface for your application using forms and controls, you need to write the code that defines the application's behavior.</span></span> <span data-ttu-id="38580-105">Podobnie jak w przypadku nowoczesny język programowania, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] obsługuje szereg typowych narzędzi programistycznych i elementy języka.</span><span class="sxs-lookup"><span data-stu-id="38580-105">As with any modern programming language, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] supports a number of common programming constructs and language elements.</span></span>  
  
 <span data-ttu-id="38580-106">Jeśli użytkownik ma zaprogramowane w innych językach, znacznie materiału opisanych w tej sekcji mogą wydawać się zapoznać.</span><span class="sxs-lookup"><span data-stu-id="38580-106">If you have programmed in other languages, much of the material covered in this section might seem familiar.</span></span> <span data-ttu-id="38580-107">Podczas gdy większość składników są podobne do tych w innych językach charakter sterowane zdarzeniami [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] wprowadza pewne niewielkie różnice.</span><span class="sxs-lookup"><span data-stu-id="38580-107">While most of the constructs are similar to those in other languages, the event-driven nature of [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] introduces some subtle differences.</span></span>  
  
 <span data-ttu-id="38580-108">Jeśli dopiero zaczynasz do programowania, materiałów w tej sekcji służy jako wprowadzenie do podstawowych bloków konstrukcyjnych dla pisania kodu.</span><span class="sxs-lookup"><span data-stu-id="38580-108">If you are new to programming, the material in this section serves as an introduction to the basic building blocks for writing code.</span></span> <span data-ttu-id="38580-109">Po zrozumieniu podstaw można tworzyć zaawansowane aplikacje przy użyciu [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="38580-109">Once you understand the basics, you can create powerful applications using [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="38580-110">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="38580-110">In This Section</span></span>  
 [<span data-ttu-id="38580-111">Tablice</span><span class="sxs-lookup"><span data-stu-id="38580-111">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 <span data-ttu-id="38580-112">W tym artykule omówiono tworzenie kodu compact i bardziej zaawansowanych deklarowanie i użycie tablic, które zawierają wiele powiązanych wartości.</span><span class="sxs-lookup"><span data-stu-id="38580-112">Discusses making your code more compact and powerful by declaring and using arrays, which hold multiple related values.</span></span>  
  
 [<span data-ttu-id="38580-113">Inicjatory kolekcji</span><span class="sxs-lookup"><span data-stu-id="38580-113">Collection Initializers</span></span>](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)  
 <span data-ttu-id="38580-114">W tym artykule opisano inicjatory kolekcji, które umożliwiają tworzenie kolekcji i wypełnić ją początkowego zestawu wartości.</span><span class="sxs-lookup"><span data-stu-id="38580-114">Describes collection initializers, which enable you to create a collection and populate it with an initial set of values.</span></span>  
  
 [<span data-ttu-id="38580-115">Stałe i wyliczenia</span><span class="sxs-lookup"><span data-stu-id="38580-115">Constants and Enumerations</span></span>](../../../visual-basic/programming-guide/language-features/constants-enums/index.md)  
 <span data-ttu-id="38580-116">W tym artykule omówiono przechowywania niezmiennych wartości do wielokrotnego użycia, między innymi zestawy związanych wartości stałych.</span><span class="sxs-lookup"><span data-stu-id="38580-116">Discusses storing unchanging values for repeated use, including sets of related constant values.</span></span>  
  
 [<span data-ttu-id="38580-117">Przepływ sterowania</span><span class="sxs-lookup"><span data-stu-id="38580-117">Control Flow</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 <span data-ttu-id="38580-118">Pokazuje, jak sterowanie przepływem wykonywania programu.</span><span class="sxs-lookup"><span data-stu-id="38580-118">Shows how to regulate the flow of your program's execution.</span></span>  
  
 [<span data-ttu-id="38580-119">Typy danych</span><span class="sxs-lookup"><span data-stu-id="38580-119">Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 <span data-ttu-id="38580-120">Opis elementu programistycznego jakiego rodzaju dane można przechowywać i przechowywania danych.</span><span class="sxs-lookup"><span data-stu-id="38580-120">Describes what kinds of data a programming element can hold and how that data is stored.</span></span>  
  
 [<span data-ttu-id="38580-121">Zadeklarowane elementy</span><span class="sxs-lookup"><span data-stu-id="38580-121">Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/index.md)  
 <span data-ttu-id="38580-122">Obejmuje programowania można zadeklarować elementów, ich nazwy i właściwości, oraz jak kompilator usuwa odwołania do nich.</span><span class="sxs-lookup"><span data-stu-id="38580-122">Covers programming elements you can declare, their names and characteristics, and how the compiler resolves references to them.</span></span>  
  
 [<span data-ttu-id="38580-123">Obiekty delegowane</span><span class="sxs-lookup"><span data-stu-id="38580-123">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 <span data-ttu-id="38580-124">Wprowadzenie do obiektów delegowanych i sposób ich użycia w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="38580-124">Provides an introduction to delegates and how they are used in Visual Basic.</span></span>  
  
 [<span data-ttu-id="38580-125">Wczesne i późne powiązania</span><span class="sxs-lookup"><span data-stu-id="38580-125">Early and Late Binding</span></span>](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)  
 <span data-ttu-id="38580-126">Opis powiązania, które jest wykonywane przez kompilator, gdy obiekt jest przypisany do zmiennej obiektu i różnice między obiektami z wczesnym wiązaniem i późnym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="38580-126">Describes binding, which is performed by the compiler when an object is assigned to an object variable, and the differences between early-bound and late-bound objects.</span></span>  
  
 [<span data-ttu-id="38580-127">Error — typy</span><span class="sxs-lookup"><span data-stu-id="38580-127">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)  
 <span data-ttu-id="38580-128">Zawiera omówienie błędy składni, błędy środowiska wykonawczego i błędy logiczne.</span><span class="sxs-lookup"><span data-stu-id="38580-128">Provides an overview of syntax errors, run-time errors, and logic errors.</span></span>  
  
 [<span data-ttu-id="38580-129">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="38580-129">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)  
 <span data-ttu-id="38580-130">Przedstawia sposób deklarowanie i użycie zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="38580-130">Shows how to declare and use events.</span></span>  
  
 [<span data-ttu-id="38580-131">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="38580-131">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)  
 <span data-ttu-id="38580-132">Opisuje interfejsy są oraz sposób ich użycia w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="38580-132">Describes what interfaces are and how you can use them in your applications.</span></span>  
  
 [<span data-ttu-id="38580-133">LINQ</span><span class="sxs-lookup"><span data-stu-id="38580-133">LINQ</span></span>](../../../visual-basic/programming-guide/language-features/linq/index.md)  
 <span data-ttu-id="38580-134">Zawiera łącza do tematów, które [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] programowanie i funkcje.</span><span class="sxs-lookup"><span data-stu-id="38580-134">Provides links to topics that introduce [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] features and programming.</span></span>  
  
 [<span data-ttu-id="38580-135">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="38580-135">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 <span data-ttu-id="38580-136">Zawiera omówienie obiekty i klasy, sposób ich użycia, ich relacje między sobą i właściwości, metod i zdarzeń, które udostępniają.</span><span class="sxs-lookup"><span data-stu-id="38580-136">Provides an overview of objects and classes, how they are used, their relationships to each other, and the properties, methods, and events they expose.</span></span>  
  
 [<span data-ttu-id="38580-137">Operatory i wyrażenia</span><span class="sxs-lookup"><span data-stu-id="38580-137">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 <span data-ttu-id="38580-138">W tym artykule opisano elementy kodu, które modyfikowania elementów używane do przechowywania wartości, sposobu ich używania wydajne i sposób łączenia ich umożliwiające uzyskanie nowych wartości.</span><span class="sxs-lookup"><span data-stu-id="38580-138">Describes the code elements that manipulate value-holding elements, how to use them efficiently, and how to combine them to yield new values.</span></span>  
  
 [<span data-ttu-id="38580-139">Procedury</span><span class="sxs-lookup"><span data-stu-id="38580-139">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 <span data-ttu-id="38580-140">W tym artykule opisano `Sub`, `Function`, `Property`, i `Operator` procedur, a także Tematy zaawansowane, takie jak cyklicznego i procedury przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="38580-140">Describes `Sub`, `Function`, `Property`, and `Operator` procedures, as well as advanced topics such as recursive and overloaded procedures.</span></span>  
  
 [<span data-ttu-id="38580-141">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="38580-141">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)  
 <span data-ttu-id="38580-142">W tym artykule opisano instrukcje deklaracji i plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="38580-142">Describes declaration and executable statements.</span></span>  
  
 [<span data-ttu-id="38580-143">Ciągi</span><span class="sxs-lookup"><span data-stu-id="38580-143">Strings</span></span>](../../../visual-basic/programming-guide/language-features/strings/index.md)  
 <span data-ttu-id="38580-144">Zawiera łącza do tematów opisujących podstawowe pojęcia dotyczące używania ciągów w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="38580-144">Provides links to topics that describe the basic concepts about using strings in Visual Basic.</span></span>  
  
 [<span data-ttu-id="38580-145">Zmienne</span><span class="sxs-lookup"><span data-stu-id="38580-145">Variables</span></span>](../../../visual-basic/programming-guide/language-features/variables/index.md)  
 <span data-ttu-id="38580-146">Wprowadzono zmienne i informacje dotyczące używania ich w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="38580-146">Introduces variables and describes how to use them in Visual Basic.</span></span>  
  
 [<span data-ttu-id="38580-147">XML</span><span class="sxs-lookup"><span data-stu-id="38580-147">XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/index.md)  
 <span data-ttu-id="38580-148">Zawiera łącza do tematów opisujących sposób użycia XML w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="38580-148">Provides links to topics that describe how to use XML in Visual Basic.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="38580-149">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="38580-149">Related Sections</span></span>  
 [<span data-ttu-id="38580-150">Kolekcje</span><span class="sxs-lookup"><span data-stu-id="38580-150">Collections</span></span>](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)  
 <span data-ttu-id="38580-151">Opisano niektóre typy kolekcji, które znajdują się w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="38580-151">Describes some of the types of collections that are provided by the .NET Framework.</span></span> <span data-ttu-id="38580-152">Pokazuje, jak używać prostych kolekcji i kolekcji par klucz/wartość.</span><span class="sxs-lookup"><span data-stu-id="38580-152">Demonstrates how to use simple collections and collections of key/value pairs.</span></span>  
  
 [<span data-ttu-id="38580-153">Dokumentacja języka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="38580-153">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)  
 <span data-ttu-id="38580-154">Zawiera informacje dotyczące różnych aspektów [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programowania.</span><span class="sxs-lookup"><span data-stu-id="38580-154">Provides reference information on various aspects of [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programming.</span></span>
