---
title: Struktura programu i konwencje związane z kodami (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions
- Visual Basic code, coding conventions
- coding conventions [Visual Basic], Visual Basic
- programs [Visual Basic], structure
- program structure [Visual Basic]
- naming conventions [Visual Basic], Visual Basic
- best practices [Visual Basic], coding conventions
- conventions [Visual Basic], Visual Basic coding
- Visual Basic code
- programming [Visual Basic], Visual Basic coding conventions
ms.assetid: dd9be76f-6944-4e78-ad72-0b6084a3fc13
ms.openlocfilehash: 9dbe8fe977b2aa11573ab7a1ac1d79be0b5204af
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624330"
---
# <a name="program-structure-and-code-conventions-visual-basic"></a><span data-ttu-id="a6530-102">Struktura programu i konwencje związane z kodami (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a6530-102">Program Structure and Code Conventions (Visual Basic)</span></span>
<span data-ttu-id="a6530-103">W tej sekcji przedstawiono typowy struktura programu Visual Basic, zapewnia prosty program Visual Basic, "Hello, World" i omawia Visual Basic — konwencje kodu.</span><span class="sxs-lookup"><span data-stu-id="a6530-103">This section introduces the typical Visual Basic program structure, provides a simple Visual Basic program, "Hello, World", and discusses Visual Basic code conventions.</span></span> <span data-ttu-id="a6530-104">Konwencje kodu są propozycjami, które koncentrują się na logice program nie, ale na jego fizycznej strukturze i wyglądzie.</span><span class="sxs-lookup"><span data-stu-id="a6530-104">Code conventions are suggestions that focus not on a program's logic but on its physical structure and appearance.</span></span> <span data-ttu-id="a6530-105">Zastosowanie się do nich sprawia, że Twój kod łatwiej odczytać, zrozumieć i konserwować.</span><span class="sxs-lookup"><span data-stu-id="a6530-105">Following them makes your code easier to read, understand, and maintain.</span></span> <span data-ttu-id="a6530-106">Konwencje kod mogą zawierać, między innymi:</span><span class="sxs-lookup"><span data-stu-id="a6530-106">Code conventions can include, among others:</span></span>  
  
- <span data-ttu-id="a6530-107">Standardowe formaty etykietowania i komentowania kodu.</span><span class="sxs-lookup"><span data-stu-id="a6530-107">Standardized formats for labeling and commenting code.</span></span>  
  
- <span data-ttu-id="a6530-108">Wytyczne dotyczące odstępów, formatowania i wcięć w kodzie.</span><span class="sxs-lookup"><span data-stu-id="a6530-108">Guidelines for spacing, formatting, and indenting code.</span></span>  
  
- <span data-ttu-id="a6530-109">Konwencje nazewnictwa dla obiektów, zmiennych i procedur.</span><span class="sxs-lookup"><span data-stu-id="a6530-109">Naming conventions for objects, variables, and procedures.</span></span>  
  
 <span data-ttu-id="a6530-110">Poniższe tematy zawierają zbiór wytycznych programowania dla programów Visual Basic, a także przykłady dobrego użycia.</span><span class="sxs-lookup"><span data-stu-id="a6530-110">The following topics present a set of programming guidelines for Visual Basic programs, along with examples of good usage.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a6530-111">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="a6530-111">In This Section</span></span>  
 [<span data-ttu-id="a6530-112">Struktura programu w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a6530-112">Structure of a Visual Basic Program</span></span>](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)  
 <span data-ttu-id="a6530-113">Zawiera omówienie elementów, które tworzą program Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a6530-113">Provides an overview of the elements that make up a Visual Basic program.</span></span>  
  
 [<span data-ttu-id="a6530-114">Procedura główna w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a6530-114">Main Procedure in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/main-procedure.md)  
 <span data-ttu-id="a6530-115">W tym artykule omówiono procedurę, która służy jako początkowy punkt i ogólna kontrola dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a6530-115">Discusses the procedure that serves as the starting point and overall control for your application.</span></span>  
  
 [<span data-ttu-id="a6530-116">Referencje i instrukcja Imports</span><span class="sxs-lookup"><span data-stu-id="a6530-116">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 <span data-ttu-id="a6530-117">Omawia sposób odwoływać się do obiektów w innych zestawach.</span><span class="sxs-lookup"><span data-stu-id="a6530-117">Discusses how to reference objects in other assemblies.</span></span>  
  
 [<span data-ttu-id="a6530-118">Przestrzenie nazw w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a6530-118">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 <span data-ttu-id="a6530-119">W tym artykule opisano, jak przestrzenie nazw organizują obiekty w ramach zgromadzeń.</span><span class="sxs-lookup"><span data-stu-id="a6530-119">Describes how namespaces organize objects within assemblies.</span></span>  
  
 [<span data-ttu-id="a6530-120">Visual Basic — konwencje nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="a6530-120">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 <span data-ttu-id="a6530-121">Zawiera ogólne wskazówki dotyczące nazewnictwa procedur, stałe, zmienne, argumenty i obiekty.</span><span class="sxs-lookup"><span data-stu-id="a6530-121">Includes general guidelines for naming procedures, constants, variables, arguments, and objects.</span></span>  
  
 [<span data-ttu-id="a6530-122">Visual Basic — konwencje kodowania</span><span class="sxs-lookup"><span data-stu-id="a6530-122">Visual Basic Coding Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)  
 <span data-ttu-id="a6530-123">Przegląda wytyczne stosowane w opracowywaniu przykładów w tej dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="a6530-123">Reviews the guidelines used in developing the samples in this documentation.</span></span>  
  
 [<span data-ttu-id="a6530-124">Kompilacja warunkowa</span><span class="sxs-lookup"><span data-stu-id="a6530-124">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 <span data-ttu-id="a6530-125">Opisuje sposób skompilowania określonych bloków kodu selektywnie podczas nakazywania kompilatorowi ignorowanie innych.</span><span class="sxs-lookup"><span data-stu-id="a6530-125">Describes how to compile particular blocks of code selectively while directing the compiler to ignore others.</span></span>  
  
 [<span data-ttu-id="a6530-126">Instrukcje: przerywanie i łączenie instrukcji w kodzie</span><span class="sxs-lookup"><span data-stu-id="a6530-126">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)  
 <span data-ttu-id="a6530-127">Pokazuje sposób podzielić długie instrukcje na wiele wierszy i połączyć krótkie instrukcje w jednym wierszu.</span><span class="sxs-lookup"><span data-stu-id="a6530-127">Shows how to divide long statements into multiple lines and combine short statements on one line.</span></span>  
  
 [<span data-ttu-id="a6530-128">Instrukcje: zwijanie i ukrywanie fragmentów kodu</span><span class="sxs-lookup"><span data-stu-id="a6530-128">How to: Collapse and Hide Sections of Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)  
 <span data-ttu-id="a6530-129">Pokazuje, jak zwijanie i ukrywanie fragmentów kodu w języku Visual Basic edytora kodu.</span><span class="sxs-lookup"><span data-stu-id="a6530-129">Shows how to collapse and hide sections of code in the Visual Basic code editor.</span></span>  
  
 [<span data-ttu-id="a6530-130">Instrukcje: etykietowanie instrukcji</span><span class="sxs-lookup"><span data-stu-id="a6530-130">How to: Label Statements</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)  
 <span data-ttu-id="a6530-131">Przedstawia sposób znaczyć linię kodu w celu identyfikowania go do użycia przy użyciu instrukcji takich jak `On Error Goto`.</span><span class="sxs-lookup"><span data-stu-id="a6530-131">Shows how to mark a line of code to identify it for use with statements such as `On Error Goto`.</span></span>  
  
 [<span data-ttu-id="a6530-132">Znaki specjalne w kodzie</span><span class="sxs-lookup"><span data-stu-id="a6530-132">Special Characters in Code</span></span>](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)  
 <span data-ttu-id="a6530-133">Pokazuje, jak i gdzie Aby wykorzystać znaki nienumeryczne i spoza alfabetu.</span><span class="sxs-lookup"><span data-stu-id="a6530-133">Shows how and where to use non-numeric and non-alphabetic characters.</span></span>  
  
 [<span data-ttu-id="a6530-134">Komentarze w kodzie</span><span class="sxs-lookup"><span data-stu-id="a6530-134">Comments in Code</span></span>](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)  
 <span data-ttu-id="a6530-135">W tym artykule omówiono sposób dodawania opisowych komentarzy w kodzie.</span><span class="sxs-lookup"><span data-stu-id="a6530-135">Discusses how to add descriptive comments to your code.</span></span>  
  
 [<span data-ttu-id="a6530-136">Słowa kluczowe jako nazwy elementów w kodzie</span><span class="sxs-lookup"><span data-stu-id="a6530-136">Keywords as Element Names in Code</span></span>](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)  
 <span data-ttu-id="a6530-137">W tym artykule opisano sposób używania nawiasy (`[]`) do rozdzielenia nazwy zmiennych, które są także słowa kluczowe Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a6530-137">Describes how to use brackets (`[]`) to delimit variable names that are also Visual Basic keywords.</span></span>  
  
 [<span data-ttu-id="a6530-138">Me, My, MyBase i MyClass</span><span class="sxs-lookup"><span data-stu-id="a6530-138">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 <span data-ttu-id="a6530-139">W tym artykule opisano różne sposoby, aby odwoływać się do elementów programu w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a6530-139">Describes various ways to refer to elements of a Visual Basic program.</span></span>  
  
 [<span data-ttu-id="a6530-140">Ograniczenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a6530-140">Visual Basic Limitations</span></span>](../../../visual-basic/programming-guide/program-structure/limitations.md)  
 <span data-ttu-id="a6530-141">Omawia usuwanie znanych limitów kodu w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a6530-141">Discusses the removal of known coding limits within Visual Basic.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a6530-142">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="a6530-142">Related Sections</span></span>  
 [<span data-ttu-id="a6530-143">Konwencje związane z typografią i kodami</span><span class="sxs-lookup"><span data-stu-id="a6530-143">Typographic and Code Conventions</span></span>](../../../visual-basic/language-reference/typographic-and-code-conventions.md)  
 <span data-ttu-id="a6530-144">Oferuje standardowe konwencje kodowania dla języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a6530-144">Provides standard coding conventions for Visual Basic.</span></span>  
  
 [<span data-ttu-id="a6530-145">Pisanie kodu</span><span class="sxs-lookup"><span data-stu-id="a6530-145">Writing Code</span></span>](/visualstudio/ide/writing-code-in-the-code-and-text-editor)  
 <span data-ttu-id="a6530-146">Opisuje funkcje, które ułatwiają umożliwia pisanie kodu i zarządzanie.</span><span class="sxs-lookup"><span data-stu-id="a6530-146">Describes features that make it easier for you to write and manage your code.</span></span>
