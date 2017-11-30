---
title: "Struktura programu i konwencje związane z kodami (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
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
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b38ba9623a20dcd1be4bc96f4aff1eb646b0a053
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="program-structure-and-code-conventions-visual-basic"></a><span data-ttu-id="cbab0-102">Struktura programu i konwencje związane z kodami (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cbab0-102">Program Structure and Code Conventions (Visual Basic)</span></span>
<span data-ttu-id="cbab0-103">W tej sekcji przedstawiono typowe [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programowania struktury, udostępnia prostą [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program "Hello, World", a w tym artykule omówiono [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kodu Konwencji.</span><span class="sxs-lookup"><span data-stu-id="cbab0-103">This section introduces the typical [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program structure, provides a simple [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program, "Hello, World", and discusses [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] code conventions.</span></span> <span data-ttu-id="cbab0-104">Konwencje związane z kodami są sugestie skoncentrowane nie na logice programu, ale na jego struktura fizyczna i wyglądu.</span><span class="sxs-lookup"><span data-stu-id="cbab0-104">Code conventions are suggestions that focus not on a program's logic but on its physical structure and appearance.</span></span> <span data-ttu-id="cbab0-105">Po ich ułatwia kodu do odczytu, zrozumieć i konserwacji.</span><span class="sxs-lookup"><span data-stu-id="cbab0-105">Following them makes your code easier to read, understand, and maintain.</span></span> <span data-ttu-id="cbab0-106">Konwencje związane z kodami należą między innymi:</span><span class="sxs-lookup"><span data-stu-id="cbab0-106">Code conventions can include, among others:</span></span>  
  
-   <span data-ttu-id="cbab0-107">Standardowych formatów etykietowanie i komentarzy kodu.</span><span class="sxs-lookup"><span data-stu-id="cbab0-107">Standardized formats for labeling and commenting code.</span></span>  
  
-   <span data-ttu-id="cbab0-108">Wytyczne dotyczące odstępów, formatowanie i kod wcięcia.</span><span class="sxs-lookup"><span data-stu-id="cbab0-108">Guidelines for spacing, formatting, and indenting code.</span></span>  
  
-   <span data-ttu-id="cbab0-109">Konwencje nazewnictwa dla obiektów, zmienne i procedur.</span><span class="sxs-lookup"><span data-stu-id="cbab0-109">Naming conventions for objects, variables, and procedures.</span></span>  
  
 <span data-ttu-id="cbab0-110">Poniższe tematy zawierają zestaw wytyczne dotyczące programowania [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programy, wraz z przykładem użycia dobra.</span><span class="sxs-lookup"><span data-stu-id="cbab0-110">The following topics present a set of programming guidelines for [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programs, along with examples of good usage.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cbab0-111">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="cbab0-111">In This Section</span></span>  
 [<span data-ttu-id="cbab0-112">Struktura programu w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cbab0-112">Structure of a Visual Basic Program</span></span>](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)  
 <span data-ttu-id="cbab0-113">Zawiera omówienie elementów, które tworzą [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program.</span><span class="sxs-lookup"><span data-stu-id="cbab0-113">Provides an overview of the elements that make up a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program.</span></span>  
  
 [<span data-ttu-id="cbab0-114">Procedura główna w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cbab0-114">Main Procedure in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/main-procedure.md)  
 <span data-ttu-id="cbab0-115">W tym artykule omówiono procedury, która służy jako początkowego punktu i ogólnej kontroli aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cbab0-115">Discusses the procedure that serves as the starting point and overall control for your application.</span></span>  
  
 [<span data-ttu-id="cbab0-116">Referencje i Importy — instrukcja</span><span class="sxs-lookup"><span data-stu-id="cbab0-116">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 <span data-ttu-id="cbab0-117">Omówiono sposób odwoływać się do obiektów w innych zestawów.</span><span class="sxs-lookup"><span data-stu-id="cbab0-117">Discusses how to reference objects in other assemblies.</span></span>  
  
 [<span data-ttu-id="cbab0-118">Przestrzenie nazw w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cbab0-118">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 <span data-ttu-id="cbab0-119">W tym artykule opisano, jak obszary nazw organizowanie obiektów w obrębie zestawów.</span><span class="sxs-lookup"><span data-stu-id="cbab0-119">Describes how namespaces organize objects within assemblies.</span></span>  
  
 [<span data-ttu-id="cbab0-120">Visual Basic — konwencje nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="cbab0-120">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 <span data-ttu-id="cbab0-121">Zawiera ogólne wskazówki dotyczące nazewnictwa procedur, stałe, zmienne, argumentów i obiektów.</span><span class="sxs-lookup"><span data-stu-id="cbab0-121">Includes general guidelines for naming procedures, constants, variables, arguments, and objects.</span></span>  
  
 [<span data-ttu-id="cbab0-122">Visual Basic — konwencje kodowania</span><span class="sxs-lookup"><span data-stu-id="cbab0-122">Visual Basic Coding Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)  
 <span data-ttu-id="cbab0-123">Przegląda wytyczne opracowano próbek w tej dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="cbab0-123">Reviews the guidelines used in developing the samples in this documentation.</span></span>  
  
 [<span data-ttu-id="cbab0-124">Kompilacja warunkowa</span><span class="sxs-lookup"><span data-stu-id="cbab0-124">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 <span data-ttu-id="cbab0-125">Opisuje sposób selektywnie kompilacji określonego bloki kodu podczas kierowania kompilatora, aby zignorować innych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="cbab0-125">Describes how to compile particular blocks of code selectively while directing the compiler to ignore others.</span></span>  
  
 [<span data-ttu-id="cbab0-126">Porady: przerywanie i łączenie instrukcji w Code</span><span class="sxs-lookup"><span data-stu-id="cbab0-126">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)  
 <span data-ttu-id="cbab0-127">Pokazano, jak długo instrukcje do wielu linii podziału i łączenie krótkich instrukcji w jednym wierszu.</span><span class="sxs-lookup"><span data-stu-id="cbab0-127">Shows how to divide long statements into multiple lines and combine short statements on one line.</span></span>  
  
 [<span data-ttu-id="cbab0-128">Porady: zwijanie i ukrywanie fragmentów kodu</span><span class="sxs-lookup"><span data-stu-id="cbab0-128">How to: Collapse and Hide Sections of Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)  
 <span data-ttu-id="cbab0-129">Pokazuje, jak zwijanie i ukrywanie fragmentów kodu w [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] edytora kodu.</span><span class="sxs-lookup"><span data-stu-id="cbab0-129">Shows how to collapse and hide sections of code in the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] code editor.</span></span>  
  
 [<span data-ttu-id="cbab0-130">Porady: etykietowanie instrukcji</span><span class="sxs-lookup"><span data-stu-id="cbab0-130">How to: Label Statements</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)  
 <span data-ttu-id="cbab0-131">Pokazuje, jak zaznacz wiersz kodu, aby zidentyfikować go do użytku w instrukcjach takich jak `On Error Goto`.</span><span class="sxs-lookup"><span data-stu-id="cbab0-131">Shows how to mark a line of code to identify it for use with statements such as `On Error Goto`.</span></span>  
  
 [<span data-ttu-id="cbab0-132">Znaki specjalne w Code</span><span class="sxs-lookup"><span data-stu-id="cbab0-132">Special Characters in Code</span></span>](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)  
 <span data-ttu-id="cbab0-133">Pokazuje, jak i gdzie można używać znaków innych niż alfanumeryczne i inne niż alfanumeryczne.</span><span class="sxs-lookup"><span data-stu-id="cbab0-133">Shows how and where to use non-numeric and non-alphabetic characters.</span></span>  
  
 [<span data-ttu-id="cbab0-134">Komentarze w kodzie</span><span class="sxs-lookup"><span data-stu-id="cbab0-134">Comments in Code</span></span>](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)  
 <span data-ttu-id="cbab0-135">W tym artykule omówiono sposób dodawania opisową komentarze w kodzie.</span><span class="sxs-lookup"><span data-stu-id="cbab0-135">Discusses how to add descriptive comments to your code.</span></span>  
  
 [<span data-ttu-id="cbab0-136">Słowa kluczowe jako nazwy elementów w Code</span><span class="sxs-lookup"><span data-stu-id="cbab0-136">Keywords as Element Names in Code</span></span>](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)  
 <span data-ttu-id="cbab0-137">W tym artykule opisano sposób użycia nawiasów (`[]`) do rozdzielenia nazwy zmiennych, które są również [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] słów kluczowych.</span><span class="sxs-lookup"><span data-stu-id="cbab0-137">Describes how to use brackets (`[]`) to delimit variable names that are also [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] keywords.</span></span>  
  
 [<span data-ttu-id="cbab0-138">Me, My, MyBase i MyClass</span><span class="sxs-lookup"><span data-stu-id="cbab0-138">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 <span data-ttu-id="cbab0-139">W tym artykule opisano różne sposoby odwołań do elementów [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program.</span><span class="sxs-lookup"><span data-stu-id="cbab0-139">Describes various ways to refer to elements of a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program.</span></span>  
  
 [<span data-ttu-id="cbab0-140">Ograniczenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cbab0-140">Visual Basic Limitations</span></span>](../../../visual-basic/programming-guide/program-structure/limitations.md)  
 <span data-ttu-id="cbab0-141">W tym artykule omówiono usunięcie znane ograniczenia kodowania [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cbab0-141">Discusses the removal of known coding limits within [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="cbab0-142">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="cbab0-142">Related Sections</span></span>  
 [<span data-ttu-id="cbab0-143">Związane z typografią i kodami konwencje</span><span class="sxs-lookup"><span data-stu-id="cbab0-143">Typographic and Code Conventions</span></span>](../../../visual-basic/language-reference/typographic-and-code-conventions.md)  
 <span data-ttu-id="cbab0-144">Miejsce na standardowej konwencji kodowania dla [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cbab0-144">Provides standard coding conventions for [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
 [<span data-ttu-id="cbab0-145">Pisanie kodu</span><span class="sxs-lookup"><span data-stu-id="cbab0-145">Writing Code</span></span>](/visualstudio/ide/writing-code-in-the-code-and-text-editor)  
 <span data-ttu-id="cbab0-146">W tym artykule opisano funkcje, które ułatwiają zapisu i zarządzać kodem.</span><span class="sxs-lookup"><span data-stu-id="cbab0-146">Describes features that make it easier for you to write and manage your code.</span></span>
