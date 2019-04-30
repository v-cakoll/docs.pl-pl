---
title: Kompilacja warunkowa w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], about conditional compilation
- compilation [Visual Basic], conditional
ms.assetid: 9c35e55e-7eee-44fb-a586-dad1f1884848
ms.openlocfilehash: 828edf2e5491394f5ac802b5c9babfb3df359e59
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61758460"
---
# <a name="conditional-compilation-in-visual-basic"></a><span data-ttu-id="f40cb-102">Kompilacja warunkowa w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f40cb-102">Conditional Compilation in Visual Basic</span></span>
<span data-ttu-id="f40cb-103">W *kompilacji warunkowej*, określonych bloków kodu w programie są kompilowane selektywnie, podczas gdy inne są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="f40cb-103">In *conditional compilation*, particular blocks of code in a program are compiled selectively while others are ignored.</span></span>  
  
 <span data-ttu-id="f40cb-104">Na przykład możesz chcieć napisać debugowania instrukcje pozwalające porównać szybkość różne podejścia do tego samego zadania programowania lub możesz chcieć Lokalizuj aplikację dla wielu języków.</span><span class="sxs-lookup"><span data-stu-id="f40cb-104">For example, you may want to write debugging statements that compare the speed of different approaches to the same programming task, or you may want to localize an application for multiple languages.</span></span> <span data-ttu-id="f40cb-105">Instrukcje kompilacji warunkowej są zaprojektowane do uruchamiania w czasie kompilacji, a nie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="f40cb-105">Conditional compilation statements are designed to run during compile time, not at run time.</span></span>  
  
 <span data-ttu-id="f40cb-106">Oznaczenia bloki kodu, aby warunkowo być skompilowana przy użyciu `#If...Then...#Else` dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="f40cb-106">You denote blocks of code to be conditionally compiled with the `#If...Then...#Else` directive.</span></span> <span data-ttu-id="f40cb-107">Na przykład, aby utworzyć język niemiecki i francuski wersji tej samej aplikacji w taki sam kod źródłowy, osadzanie segmenty kodu specyficznego dla platformy w `#If...Then` instrukcji przy użyciu wstępnie zdefiniowanych stałych `FrenchVersion` i `GermanVersion`.</span><span class="sxs-lookup"><span data-stu-id="f40cb-107">For example, to create French- and German-language versions of the same application from the same source code, you embed platform-specific code segments in `#If...Then` statements using the predefined constants `FrenchVersion` and `GermanVersion`.</span></span> <span data-ttu-id="f40cb-108">Poniższy przykład pokazuje, jak:</span><span class="sxs-lookup"><span data-stu-id="f40cb-108">The following example demonstrates how:</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#5)]  
  
 <span data-ttu-id="f40cb-109">Jeśli ustawisz wartość `FrenchVersion` Stała kompilacji warunkowej do `True` w czasie kompilacji jest skompilowany kod warunkowy Francuska wersja językowa.</span><span class="sxs-lookup"><span data-stu-id="f40cb-109">If you set the value of the `FrenchVersion` conditional compilation constant to `True` at compile time, the conditional code for the French version is compiled.</span></span> <span data-ttu-id="f40cb-110">Jeśli ustawisz wartość `GermanVersion` stała przeznaczona do `True`, kompilator używa niemiecka wersja językowa.</span><span class="sxs-lookup"><span data-stu-id="f40cb-110">If you set the value of the `GermanVersion` constant to `True`, the compiler uses the German version.</span></span> <span data-ttu-id="f40cb-111">Jeśli nie ustawiono `True`, kod w ciągu ostatnich `Else` block przebiegów.</span><span class="sxs-lookup"><span data-stu-id="f40cb-111">If neither is set to `True`, the code in the last `Else` block runs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f40cb-112">Automatycznego uzupełniania będzie działanie podczas edytowania kodu i za pomocą dyrektywy kompilacji warunkowej, jeśli kod nie jest częścią bieżącej gałęzi.</span><span class="sxs-lookup"><span data-stu-id="f40cb-112">Autocompletion will not function when editing code and using conditional compilation directives if the code is not part of the current branch.</span></span>  
  
## <a name="declaring-conditional-compilation-constants"></a><span data-ttu-id="f40cb-113">Deklarowanie stałych kompilacji warunkowej</span><span class="sxs-lookup"><span data-stu-id="f40cb-113">Declaring Conditional Compilation Constants</span></span>  
 <span data-ttu-id="f40cb-114">Stałe kompilacji warunkowej można ustawić w jeden z trzech sposobów:</span><span class="sxs-lookup"><span data-stu-id="f40cb-114">You can set conditional compilation constants in one of three ways:</span></span>  
  
- <span data-ttu-id="f40cb-115">W **Projektant projektu**</span><span class="sxs-lookup"><span data-stu-id="f40cb-115">In the **Project Designer**</span></span>  
  
- <span data-ttu-id="f40cb-116">W wierszu polecenia, korzystając z wiersza polecenia kompilatora</span><span class="sxs-lookup"><span data-stu-id="f40cb-116">At the command line when using the command-line compiler</span></span>  
  
- <span data-ttu-id="f40cb-117">W kodzie</span><span class="sxs-lookup"><span data-stu-id="f40cb-117">In your code</span></span>  
  
 <span data-ttu-id="f40cb-118">Stałe kompilacji warunkowej mają specjalne zakres i nie są dostępne od standardowego kodu.</span><span class="sxs-lookup"><span data-stu-id="f40cb-118">Conditional compilation constants have a special scope and cannot be accessed from standard code.</span></span> <span data-ttu-id="f40cb-119">Zakres Stała kompilacji warunkowej jest zależna od sposób, który jest ustawiony.</span><span class="sxs-lookup"><span data-stu-id="f40cb-119">The scope of a conditional compilation constant is dependent on the way it is set.</span></span> <span data-ttu-id="f40cb-120">W poniższej tabeli wymieniono zakres stałe zadeklarowane za pomocą każdego z trzech sposobów wymienionych powyżej.</span><span class="sxs-lookup"><span data-stu-id="f40cb-120">The following table lists the scope of constants declared using each of the three ways mentioned above.</span></span>  
  
|<span data-ttu-id="f40cb-121">Ustawianie — stała</span><span class="sxs-lookup"><span data-stu-id="f40cb-121">How constant is set</span></span>|<span data-ttu-id="f40cb-122">Zakres — stała</span><span class="sxs-lookup"><span data-stu-id="f40cb-122">Scope of constant</span></span>|  
|---|---|  
|<span data-ttu-id="f40cb-123">**Projektant projektu**</span><span class="sxs-lookup"><span data-stu-id="f40cb-123">**Project Designer**</span></span>|<span data-ttu-id="f40cb-124">Publiczne do wszystkich plików w projekcie</span><span class="sxs-lookup"><span data-stu-id="f40cb-124">Public to all files in the project</span></span>|  
|<span data-ttu-id="f40cb-125">Wiersz polecenia</span><span class="sxs-lookup"><span data-stu-id="f40cb-125">Command line</span></span>|<span data-ttu-id="f40cb-126">Publiczne do wszystkich plików przekazywane do wiersza polecenia kompilatora</span><span class="sxs-lookup"><span data-stu-id="f40cb-126">Public to all files passed to the command-line compiler</span></span>|  
|<span data-ttu-id="f40cb-127">`#Const` instrukcji w kodzie</span><span class="sxs-lookup"><span data-stu-id="f40cb-127">`#Const` statement in code</span></span>|<span data-ttu-id="f40cb-128">Prywatne dla pliku, w której jest zadeklarowana</span><span class="sxs-lookup"><span data-stu-id="f40cb-128">Private to the file in which it is declared</span></span>|  
  
|<span data-ttu-id="f40cb-129">Aby ustawić stałe w Projektancie projektu</span><span class="sxs-lookup"><span data-stu-id="f40cb-129">To set constants in the Project Designer</span></span>|  
|---|  
|<span data-ttu-id="f40cb-130">— Przed utworzeniem pliku wykonywalnego, należy ustawić stałe w **projektanta projektu** postępując zgodnie z krokami opisanymi w [właściwościami Zarządzanie projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties).</span><span class="sxs-lookup"><span data-stu-id="f40cb-130">-   Before creating your executable file, set constants in the **Project Designer** by following the steps provided in [Managing Project and Solution Properties](/visualstudio/ide/managing-project-and-solution-properties).</span></span>|  
  
|<span data-ttu-id="f40cb-131">Aby ustawić stałe w wierszu polecenia</span><span class="sxs-lookup"><span data-stu-id="f40cb-131">To set constants at the command line</span></span>|  
|---|  
|<span data-ttu-id="f40cb-132">-Użyj **/d** przełącznik, aby wprowadzić stałe kompilacji warunkowej, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="f40cb-132">-   Use the **/d** switch to enter conditional compilation constants, as in the following example:</span></span><br />     `vbc MyProj.vb /d:conFrenchVersion=–1:conANSI=0`<br />     <span data-ttu-id="f40cb-133">Miejsce nie jest wymagany między **/d** przełącznika i pierwszy stałą.</span><span class="sxs-lookup"><span data-stu-id="f40cb-133">No space is required between the **/d** switch and the first constant.</span></span> <span data-ttu-id="f40cb-134">Aby uzyskać więcej informacji, zobacz [/ define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md).</span><span class="sxs-lookup"><span data-stu-id="f40cb-134">For more information, see [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md).</span></span><br />     <span data-ttu-id="f40cb-135">Deklaracje wiersza polecenia zastępują wprowadzonego w deklaracji **projektanta projektu**, ale nie usuwaj je.</span><span class="sxs-lookup"><span data-stu-id="f40cb-135">Command-line declarations override declarations entered in the **Project Designer**, but do not erase them.</span></span> <span data-ttu-id="f40cb-136">Argumenty ustawione **projektanta projektu** będą używane w kolejnych kompilacjach.</span><span class="sxs-lookup"><span data-stu-id="f40cb-136">Arguments set in **Project Designer** remain in effect for subsequent compilations.</span></span><br />     <span data-ttu-id="f40cb-137">Podczas pisania stałe w sam kod, Brak reguł strict do ich umieszczania ich zakres jest cały moduł, w którym są one zgłoszone.</span><span class="sxs-lookup"><span data-stu-id="f40cb-137">When writing constants in the code itself, there are no strict rules as to their placement, since their scope is the entire module in which they are declared.</span></span>|  
  
|<span data-ttu-id="f40cb-138">Aby ustawić stałe w kodzie</span><span class="sxs-lookup"><span data-stu-id="f40cb-138">To set constants in your code</span></span>|  
|---|  
|<span data-ttu-id="f40cb-139">— Umieść stałych w bloku deklaracja modułu, w którym są używane.</span><span class="sxs-lookup"><span data-stu-id="f40cb-139">-   Place the constants in the declaration block of the module in which they are used.</span></span> <span data-ttu-id="f40cb-140">Dzięki temu kod zorganizowany i łatwiejsza do odczytania.</span><span class="sxs-lookup"><span data-stu-id="f40cb-140">This helps keep your code organized and easier to read.</span></span>|  
  
## <a name="related-topics"></a><span data-ttu-id="f40cb-141">Tematy pokrewne</span><span class="sxs-lookup"><span data-stu-id="f40cb-141">Related Topics</span></span>  
  
|<span data-ttu-id="f40cb-142">Tytuł</span><span class="sxs-lookup"><span data-stu-id="f40cb-142">Title</span></span>|<span data-ttu-id="f40cb-143">Opis</span><span class="sxs-lookup"><span data-stu-id="f40cb-143">Description</span></span>|  
|---|---|  
|[<span data-ttu-id="f40cb-144">Konwencje dotyczące struktury programów i kodu</span><span class="sxs-lookup"><span data-stu-id="f40cb-144">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)|<span data-ttu-id="f40cb-145">Zawiera sugestie dotyczące wprowadzania kodu można łatwo odczytać i obsługa.</span><span class="sxs-lookup"><span data-stu-id="f40cb-145">Provides suggestions for making your code easy to read and maintain.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="f40cb-146">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="f40cb-146">Reference</span></span>  
 [<span data-ttu-id="f40cb-147">#Const, dyrektywa</span><span class="sxs-lookup"><span data-stu-id="f40cb-147">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)  
  
 [<span data-ttu-id="f40cb-148">#If...Then...#Else, dyrektywy</span><span class="sxs-lookup"><span data-stu-id="f40cb-148">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
  
 [<span data-ttu-id="f40cb-149">/ define (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f40cb-149">/define (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/define.md)
