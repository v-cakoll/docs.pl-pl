---
title: Struktura programu i konwencje związane z kodami (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9980a815d83b21214f1be441d641c3da38c1b541
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="program-structure-and-code-conventions-visual-basic"></a><span data-ttu-id="6162f-102">Struktura programu i konwencje związane z kodami (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6162f-102">Program Structure and Code Conventions (Visual Basic)</span></span>
<span data-ttu-id="6162f-103">W tej sekcji przedstawiono typowe struktura programu Visual Basic, udostępnia prosty program Visual Basic, tekst "Hello, World" i w tym artykule omówiono kod Visual Basic — konwencje.</span><span class="sxs-lookup"><span data-stu-id="6162f-103">This section introduces the typical Visual Basic program structure, provides a simple Visual Basic program, "Hello, World", and discusses Visual Basic code conventions.</span></span> <span data-ttu-id="6162f-104">Konwencje związane z kodami są sugestie skoncentrowane nie na logice programu, ale na jego struktura fizyczna i wyglądu.</span><span class="sxs-lookup"><span data-stu-id="6162f-104">Code conventions are suggestions that focus not on a program's logic but on its physical structure and appearance.</span></span> <span data-ttu-id="6162f-105">Po ich ułatwia kodu do odczytu, zrozumieć i konserwacji.</span><span class="sxs-lookup"><span data-stu-id="6162f-105">Following them makes your code easier to read, understand, and maintain.</span></span> <span data-ttu-id="6162f-106">Konwencje związane z kodami należą między innymi:</span><span class="sxs-lookup"><span data-stu-id="6162f-106">Code conventions can include, among others:</span></span>  
  
-   <span data-ttu-id="6162f-107">Standardowych formatów etykietowanie i komentarzy kodu.</span><span class="sxs-lookup"><span data-stu-id="6162f-107">Standardized formats for labeling and commenting code.</span></span>  
  
-   <span data-ttu-id="6162f-108">Wytyczne dotyczące odstępów, formatowanie i kod wcięcia.</span><span class="sxs-lookup"><span data-stu-id="6162f-108">Guidelines for spacing, formatting, and indenting code.</span></span>  
  
-   <span data-ttu-id="6162f-109">Konwencje nazewnictwa dla obiektów, zmienne i procedur.</span><span class="sxs-lookup"><span data-stu-id="6162f-109">Naming conventions for objects, variables, and procedures.</span></span>  
  
 <span data-ttu-id="6162f-110">Poniższe tematy zawierają zestaw wytycznych programowania dla programów Visual Basic, wraz z przykładem użycia dobra.</span><span class="sxs-lookup"><span data-stu-id="6162f-110">The following topics present a set of programming guidelines for Visual Basic programs, along with examples of good usage.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6162f-111">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="6162f-111">In This Section</span></span>  
 [<span data-ttu-id="6162f-112">Struktura programu w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6162f-112">Structure of a Visual Basic Program</span></span>](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)  
 <span data-ttu-id="6162f-113">Zawiera omówienie elementy wchodzące w skład programu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="6162f-113">Provides an overview of the elements that make up a Visual Basic program.</span></span>  
  
 [<span data-ttu-id="6162f-114">Procedura główna w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6162f-114">Main Procedure in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/main-procedure.md)  
 <span data-ttu-id="6162f-115">W tym artykule omówiono procedury, która służy jako początkowego punktu i ogólnej kontroli aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6162f-115">Discusses the procedure that serves as the starting point and overall control for your application.</span></span>  
  
 [<span data-ttu-id="6162f-116">Referencje i instrukcja Imports</span><span class="sxs-lookup"><span data-stu-id="6162f-116">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 <span data-ttu-id="6162f-117">Omówiono sposób odwoływać się do obiektów w innych zestawów.</span><span class="sxs-lookup"><span data-stu-id="6162f-117">Discusses how to reference objects in other assemblies.</span></span>  
  
 [<span data-ttu-id="6162f-118">Przestrzenie nazw w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6162f-118">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 <span data-ttu-id="6162f-119">W tym artykule opisano, jak obszary nazw organizowanie obiektów w obrębie zestawów.</span><span class="sxs-lookup"><span data-stu-id="6162f-119">Describes how namespaces organize objects within assemblies.</span></span>  
  
 [<span data-ttu-id="6162f-120">Visual Basic — konwencje nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="6162f-120">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 <span data-ttu-id="6162f-121">Zawiera ogólne wskazówki dotyczące nazewnictwa procedur, stałe, zmienne, argumentów i obiektów.</span><span class="sxs-lookup"><span data-stu-id="6162f-121">Includes general guidelines for naming procedures, constants, variables, arguments, and objects.</span></span>  
  
 [<span data-ttu-id="6162f-122">Visual Basic — konwencje kodowania</span><span class="sxs-lookup"><span data-stu-id="6162f-122">Visual Basic Coding Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)  
 <span data-ttu-id="6162f-123">Przegląda wytyczne opracowano próbek w tej dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="6162f-123">Reviews the guidelines used in developing the samples in this documentation.</span></span>  
  
 [<span data-ttu-id="6162f-124">Kompilacja warunkowa</span><span class="sxs-lookup"><span data-stu-id="6162f-124">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 <span data-ttu-id="6162f-125">Opisuje sposób selektywnie kompilacji określonego bloki kodu podczas kierowania kompilatora, aby zignorować innych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="6162f-125">Describes how to compile particular blocks of code selectively while directing the compiler to ignore others.</span></span>  
  
 [<span data-ttu-id="6162f-126">Instrukcje: przerywanie i łączenie instrukcji w kodzie</span><span class="sxs-lookup"><span data-stu-id="6162f-126">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)  
 <span data-ttu-id="6162f-127">Pokazano, jak długo instrukcje do wielu linii podziału i łączenie krótkich instrukcji w jednym wierszu.</span><span class="sxs-lookup"><span data-stu-id="6162f-127">Shows how to divide long statements into multiple lines and combine short statements on one line.</span></span>  
  
 [<span data-ttu-id="6162f-128">Instrukcje: zwijanie i ukrywanie fragmentów kodu</span><span class="sxs-lookup"><span data-stu-id="6162f-128">How to: Collapse and Hide Sections of Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)  
 <span data-ttu-id="6162f-129">Przedstawia sposób zwijanie i ukrywanie fragmentów kodu w języku Visual Basic edytora kodu.</span><span class="sxs-lookup"><span data-stu-id="6162f-129">Shows how to collapse and hide sections of code in the Visual Basic code editor.</span></span>  
  
 [<span data-ttu-id="6162f-130">Instrukcje: etykietowanie instrukcji</span><span class="sxs-lookup"><span data-stu-id="6162f-130">How to: Label Statements</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)  
 <span data-ttu-id="6162f-131">Pokazuje, jak zaznacz wiersz kodu, aby zidentyfikować go do użytku w instrukcjach takich jak `On Error Goto`.</span><span class="sxs-lookup"><span data-stu-id="6162f-131">Shows how to mark a line of code to identify it for use with statements such as `On Error Goto`.</span></span>  
  
 [<span data-ttu-id="6162f-132">Znaki specjalne w kodzie</span><span class="sxs-lookup"><span data-stu-id="6162f-132">Special Characters in Code</span></span>](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)  
 <span data-ttu-id="6162f-133">Pokazuje, jak i gdzie można używać znaków innych niż alfanumeryczne i inne niż alfanumeryczne.</span><span class="sxs-lookup"><span data-stu-id="6162f-133">Shows how and where to use non-numeric and non-alphabetic characters.</span></span>  
  
 [<span data-ttu-id="6162f-134">Komentarze w kodzie</span><span class="sxs-lookup"><span data-stu-id="6162f-134">Comments in Code</span></span>](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)  
 <span data-ttu-id="6162f-135">W tym artykule omówiono sposób dodawania opisową komentarze w kodzie.</span><span class="sxs-lookup"><span data-stu-id="6162f-135">Discusses how to add descriptive comments to your code.</span></span>  
  
 [<span data-ttu-id="6162f-136">Słowa kluczowe jako nazwy elementów w kodzie</span><span class="sxs-lookup"><span data-stu-id="6162f-136">Keywords as Element Names in Code</span></span>](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)  
 <span data-ttu-id="6162f-137">W tym artykule opisano sposób użycia nawiasów (`[]`) do rozdzielenia nazwy zmiennych, które są również słowa kluczowe Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="6162f-137">Describes how to use brackets (`[]`) to delimit variable names that are also Visual Basic keywords.</span></span>  
  
 [<span data-ttu-id="6162f-138">Me, My, MyBase i MyClass</span><span class="sxs-lookup"><span data-stu-id="6162f-138">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 <span data-ttu-id="6162f-139">W tym artykule opisano różne sposoby odwołań do elementów programu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="6162f-139">Describes various ways to refer to elements of a Visual Basic program.</span></span>  
  
 [<span data-ttu-id="6162f-140">Ograniczenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6162f-140">Visual Basic Limitations</span></span>](../../../visual-basic/programming-guide/program-structure/limitations.md)  
 <span data-ttu-id="6162f-141">W tym artykule omówiono usunięcia znanych ograniczeń programowania w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="6162f-141">Discusses the removal of known coding limits within Visual Basic.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6162f-142">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="6162f-142">Related Sections</span></span>  
 [<span data-ttu-id="6162f-143">Konwencje związane z typografią i kodami</span><span class="sxs-lookup"><span data-stu-id="6162f-143">Typographic and Code Conventions</span></span>](../../../visual-basic/language-reference/typographic-and-code-conventions.md)  
 <span data-ttu-id="6162f-144">Udostępnia standardowej konwencji kodowania w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="6162f-144">Provides standard coding conventions for Visual Basic.</span></span>  
  
 [<span data-ttu-id="6162f-145">Pisanie kodu</span><span class="sxs-lookup"><span data-stu-id="6162f-145">Writing Code</span></span>](/visualstudio/ide/writing-code-in-the-code-and-text-editor)  
 <span data-ttu-id="6162f-146">W tym artykule opisano funkcje, które ułatwiają zapisu i zarządzać kodem.</span><span class="sxs-lookup"><span data-stu-id="6162f-146">Describes features that make it easier for you to write and manage your code.</span></span>
