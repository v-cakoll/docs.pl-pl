---
title: Kompilacja warunkowa w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], about conditional compilation
- compilation [Visual Basic], conditional
ms.assetid: 9c35e55e-7eee-44fb-a586-dad1f1884848
ms.openlocfilehash: 496df36242c6b43e7e3ec94ce675d11177e8b466
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="conditional-compilation-in-visual-basic"></a><span data-ttu-id="a6100-102">Kompilacja warunkowa w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a6100-102">Conditional Compilation in Visual Basic</span></span>
<span data-ttu-id="a6100-103">W *kompilacja warunkowa*, konkretnego bloki kodu w programie są kompilowane selektywnie, podczas gdy inne są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="a6100-103">In *conditional compilation*, particular blocks of code in a program are compiled selectively while others are ignored.</span></span>  
  
 <span data-ttu-id="a6100-104">Na przykład można zapisać debugowania instrukcji, które porównania szybkość różne podejścia do tego samego zadania programowania, lub może być do zlokalizowania aplikacji dla wielu języków.</span><span class="sxs-lookup"><span data-stu-id="a6100-104">For example, you may want to write debugging statements that compare the speed of different approaches to the same programming task, or you may want to localize an application for multiple languages.</span></span> <span data-ttu-id="a6100-105">Kompilacja warunkowa instrukcje są przeznaczone do uruchamiania w czasie kompilacji nie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="a6100-105">Conditional compilation statements are designed to run during compile time, not at run time.</span></span>  
  
 <span data-ttu-id="a6100-106">Oznaczenia bloki kodu do skompilowania warunkowo z `#If...Then...#Else` dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="a6100-106">You denote blocks of code to be conditionally compiled with the `#If...Then...#Else` directive.</span></span> <span data-ttu-id="a6100-107">Na przykład, aby utworzyć język niemiecki i francuski wersje tej samej aplikacji w taki sam kod źródłowy, osadzić segmenty kodu specyficzne dla platformy w `#If...Then` instrukcje przy użyciu wstępnie zdefiniowanych stałe `FrenchVersion` i `GermanVersion`.</span><span class="sxs-lookup"><span data-stu-id="a6100-107">For example, to create French- and German-language versions of the same application from the same source code, you embed platform-specific code segments in `#If...Then` statements using the predefined constants `FrenchVersion` and `GermanVersion`.</span></span> <span data-ttu-id="a6100-108">W poniższym przykładzie pokazano sposób:</span><span class="sxs-lookup"><span data-stu-id="a6100-108">The following example demonstrates how:</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#5](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/conditional-compilation_1.vb)]  
  
 <span data-ttu-id="a6100-109">Jeśli ustawisz wartość `FrenchVersion` Stała kompilacji warunkowej na `True` w czasie kompilacji jest skompilowany kod warunkowego Francuska wersja językowa.</span><span class="sxs-lookup"><span data-stu-id="a6100-109">If you set the value of the `FrenchVersion` conditional compilation constant to `True` at compile time, the conditional code for the French version is compiled.</span></span> <span data-ttu-id="a6100-110">Jeśli ustawisz wartość `GermanVersion` stała przeznaczona do `True`, kompilator używa niemiecka wersja językowa.</span><span class="sxs-lookup"><span data-stu-id="a6100-110">If you set the value of the `GermanVersion` constant to `True`, the compiler uses the German version.</span></span> <span data-ttu-id="a6100-111">Jeśli nie ustawiono `True`, kod w ciągu ostatnich `Else` blokowanie działa.</span><span class="sxs-lookup"><span data-stu-id="a6100-111">If neither is set to `True`, the code in the last `Else` block runs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a6100-112">Autocompletion spowoduje nieprawidłowe działanie podczas edytowania kodu i użycie dyrektywy warunkowej kompilacji, jeśli kod nie jest częścią bieżącej gałęzi.</span><span class="sxs-lookup"><span data-stu-id="a6100-112">Autocompletion will not function when editing code and using conditional compilation directives if the code is not part of the current branch.</span></span>  
  
## <a name="declaring-conditional-compilation-constants"></a><span data-ttu-id="a6100-113">Deklarowanie stałych kompilacja warunkowa</span><span class="sxs-lookup"><span data-stu-id="a6100-113">Declaring Conditional Compilation Constants</span></span>  
 <span data-ttu-id="a6100-114">Kompilacja warunkowa stałe można ustawić w jeden z trzech sposobów:</span><span class="sxs-lookup"><span data-stu-id="a6100-114">You can set conditional compilation constants in one of three ways:</span></span>  
  
-   <span data-ttu-id="a6100-115">W **Projektant projektu**</span><span class="sxs-lookup"><span data-stu-id="a6100-115">In the **Project Designer**</span></span>  
  
-   <span data-ttu-id="a6100-116">W wierszu polecenia, korzystając z wiersza polecenia kompilatora</span><span class="sxs-lookup"><span data-stu-id="a6100-116">At the command line when using the command-line compiler</span></span>  
  
-   <span data-ttu-id="a6100-117">W kodzie</span><span class="sxs-lookup"><span data-stu-id="a6100-117">In your code</span></span>  
  
 <span data-ttu-id="a6100-118">Kompilacja warunkowa stałe ma specjalne zakresu i nie można uzyskać dostępu z standardowego kodu.</span><span class="sxs-lookup"><span data-stu-id="a6100-118">Conditional compilation constants have a special scope and cannot be accessed from standard code.</span></span> <span data-ttu-id="a6100-119">Zakres Stała kompilacji warunkowej zależy od sposobu jest ustawiona.</span><span class="sxs-lookup"><span data-stu-id="a6100-119">The scope of a conditional compilation constant is dependent on the way it is set.</span></span> <span data-ttu-id="a6100-120">W poniższej tabeli wymieniono zakresu stałe zadeklarowane za pomocą każdego z trzech sposobów wymienionych powyżej.</span><span class="sxs-lookup"><span data-stu-id="a6100-120">The following table lists the scope of constants declared using each of the three ways mentioned above.</span></span>  
  
|<span data-ttu-id="a6100-121">Ustawianie stałej</span><span class="sxs-lookup"><span data-stu-id="a6100-121">How constant is set</span></span>|<span data-ttu-id="a6100-122">Zakres stała</span><span class="sxs-lookup"><span data-stu-id="a6100-122">Scope of constant</span></span>|  
|---|---|  
|<span data-ttu-id="a6100-123">**Projektant projektu**</span><span class="sxs-lookup"><span data-stu-id="a6100-123">**Project Designer**</span></span>|<span data-ttu-id="a6100-124">Publicznego do wszystkich plików w projekcie</span><span class="sxs-lookup"><span data-stu-id="a6100-124">Public to all files in the project</span></span>|  
|<span data-ttu-id="a6100-125">Wiersz polecenia</span><span class="sxs-lookup"><span data-stu-id="a6100-125">Command line</span></span>|<span data-ttu-id="a6100-126">Publiczny, aby wszystkie pliki przekazywane do wiersza polecenia kompilatora</span><span class="sxs-lookup"><span data-stu-id="a6100-126">Public to all files passed to the command-line compiler</span></span>|  
|<span data-ttu-id="a6100-127">`#Const` instrukcji w code</span><span class="sxs-lookup"><span data-stu-id="a6100-127">`#Const` statement in code</span></span>|<span data-ttu-id="a6100-128">Prywatny do pliku, w którym jest zadeklarowana</span><span class="sxs-lookup"><span data-stu-id="a6100-128">Private to the file in which it is declared</span></span>|  
  
|<span data-ttu-id="a6100-129">Aby ustawić stałe w Projektancie projektu</span><span class="sxs-lookup"><span data-stu-id="a6100-129">To set constants in the Project Designer</span></span>|  
|---|  
|<span data-ttu-id="a6100-130">— Przed utworzeniem pliku wykonywalnego, należy ustawić stałe **projektanta projektu** , postępując zgodnie z krokami opisanymi w [właściwościami Zarządzanie projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties).</span><span class="sxs-lookup"><span data-stu-id="a6100-130">-   Before creating your executable file, set constants in the **Project Designer** by following the steps provided in [Managing Project and Solution Properties](/visualstudio/ide/managing-project-and-solution-properties).</span></span>|  
  
|<span data-ttu-id="a6100-131">Aby ustawić stałe w wierszu polecenia</span><span class="sxs-lookup"><span data-stu-id="a6100-131">To set constants at the command line</span></span>|  
|---|  
|<span data-ttu-id="a6100-132">-Użyj **/d** przełącznik, aby wprowadzić stałe kompilacja warunkowa, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="a6100-132">-   Use the **/d** switch to enter conditional compilation constants, as in the following example:</span></span><br />     `vbc MyProj.vb /d:conFrenchVersion=–1:conANSI=0`<br />     <span data-ttu-id="a6100-133">Miejsce nie jest wymagany między **/d** przełącznika i pierwszy stałą.</span><span class="sxs-lookup"><span data-stu-id="a6100-133">No space is required between the **/d** switch and the first constant.</span></span> <span data-ttu-id="a6100-134">Aby uzyskać więcej informacji, zobacz [/ define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md).</span><span class="sxs-lookup"><span data-stu-id="a6100-134">For more information, see [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md).</span></span><br />     <span data-ttu-id="a6100-135">Deklaracje wiersza polecenia zastąpienia w deklaracjach **projektanta projektu**, ale nie usuwaj je.</span><span class="sxs-lookup"><span data-stu-id="a6100-135">Command-line declarations override declarations entered in the **Project Designer**, but do not erase them.</span></span> <span data-ttu-id="a6100-136">Argumenty ustawione **projektanta projektu** będą obowiązywać przez kolejne kompilacje.</span><span class="sxs-lookup"><span data-stu-id="a6100-136">Arguments set in **Project Designer** remain in effect for subsequent compilations.</span></span><br />     <span data-ttu-id="a6100-137">Podczas zapisywania stałe w kodu, Brak reguł strict klienckiemu, ich umieszczania, ponieważ ich zakres jest cały moduł, w którym jest zadeklarowany.</span><span class="sxs-lookup"><span data-stu-id="a6100-137">When writing constants in the code itself, there are no strict rules as to their placement, since their scope is the entire module in which they are declared.</span></span>|  
  
|<span data-ttu-id="a6100-138">Aby ustawić stałe w kodzie</span><span class="sxs-lookup"><span data-stu-id="a6100-138">To set constants in your code</span></span>|  
|---|  
|<span data-ttu-id="a6100-139">-Umieść stałe w bloku deklaracji modułu, w którym są używane.</span><span class="sxs-lookup"><span data-stu-id="a6100-139">-   Place the constants in the declaration block of the module in which they are used.</span></span> <span data-ttu-id="a6100-140">Dzięki temu kodu organizowane i łatwiejsze do odczytania.</span><span class="sxs-lookup"><span data-stu-id="a6100-140">This helps keep your code organized and easier to read.</span></span>|  
  
## <a name="related-topics"></a><span data-ttu-id="a6100-141">Tematy pokrewne</span><span class="sxs-lookup"><span data-stu-id="a6100-141">Related Topics</span></span>  
  
|<span data-ttu-id="a6100-142">Tytuł</span><span class="sxs-lookup"><span data-stu-id="a6100-142">Title</span></span>|<span data-ttu-id="a6100-143">Opis</span><span class="sxs-lookup"><span data-stu-id="a6100-143">Description</span></span>|  
|---|---|  
|[<span data-ttu-id="a6100-144">Struktura programu i konwencje związane z kodami</span><span class="sxs-lookup"><span data-stu-id="a6100-144">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)|<span data-ttu-id="a6100-145">Zawiera sugestie dotyczące dzięki kodu można łatwo odczytać i obsługa.</span><span class="sxs-lookup"><span data-stu-id="a6100-145">Provides suggestions for making your code easy to read and maintain.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="a6100-146">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="a6100-146">Reference</span></span>  
 [<span data-ttu-id="a6100-147">#Const, dyrektywa</span><span class="sxs-lookup"><span data-stu-id="a6100-147">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)  
  
 [<span data-ttu-id="a6100-148">#If...Then...#Else, dyrektywy</span><span class="sxs-lookup"><span data-stu-id="a6100-148">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
  
 [<span data-ttu-id="a6100-149">/ define (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a6100-149">/define (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/define.md)
