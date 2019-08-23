---
title: Kompilacja warunkowa w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], about conditional compilation
- compilation [Visual Basic], conditional
ms.assetid: 9c35e55e-7eee-44fb-a586-dad1f1884848
ms.openlocfilehash: 1bee64568ff92468e29226a395f7e5335387e256
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945584"
---
# <a name="conditional-compilation-in-visual-basic"></a><span data-ttu-id="89eb5-102">Kompilacja warunkowa w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="89eb5-102">Conditional Compilation in Visual Basic</span></span>
<span data-ttu-id="89eb5-103">W *kompilacji warunkowej*poszczególne bloki kodu w programie są kompilowane wybiórczo, podczas gdy inne są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="89eb5-103">In *conditional compilation*, particular blocks of code in a program are compiled selectively while others are ignored.</span></span>  
  
 <span data-ttu-id="89eb5-104">Na przykład możesz chcieć napisać instrukcje debugowania, które porównują szybkość różnych podejść do tego samego zadania programistycznego, lub można zlokalizować aplikację dla wielu języków.</span><span class="sxs-lookup"><span data-stu-id="89eb5-104">For example, you may want to write debugging statements that compare the speed of different approaches to the same programming task, or you may want to localize an application for multiple languages.</span></span> <span data-ttu-id="89eb5-105">Instrukcje kompilacji warunkowej są przeznaczone do uruchamiania w czasie kompilacji, a nie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="89eb5-105">Conditional compilation statements are designed to run during compile time, not at run time.</span></span>  
  
 <span data-ttu-id="89eb5-106">Należy zauważyć, `#If...Then...#Else` że bloki kodu mają być warunkowo kompilowane z dyrektywą.</span><span class="sxs-lookup"><span data-stu-id="89eb5-106">You denote blocks of code to be conditionally compiled with the `#If...Then...#Else` directive.</span></span> <span data-ttu-id="89eb5-107">Aby na przykład utworzyć wersje językowe języka francuskiego i niemieckiego tej samej aplikacji z tego samego kodu źródłowego, segmenty kodu specyficzne dla platformy można osadzić `#If...Then` w instrukcjach korzystających `FrenchVersion` ze `GermanVersion`wstępnie zdefiniowanych stałych i.</span><span class="sxs-lookup"><span data-stu-id="89eb5-107">For example, to create French- and German-language versions of the same application from the same source code, you embed platform-specific code segments in `#If...Then` statements using the predefined constants `FrenchVersion` and `GermanVersion`.</span></span> <span data-ttu-id="89eb5-108">W poniższym przykładzie pokazano, jak:</span><span class="sxs-lookup"><span data-stu-id="89eb5-108">The following example demonstrates how:</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#5)]  
  
 <span data-ttu-id="89eb5-109">Jeśli ustawisz wartość `FrenchVersion` stałej kompilacji warunkowej na `True` w czasie kompilacji, zostanie skompilowany kod warunkowy dla wersji francuskiej.</span><span class="sxs-lookup"><span data-stu-id="89eb5-109">If you set the value of the `FrenchVersion` conditional compilation constant to `True` at compile time, the conditional code for the French version is compiled.</span></span> <span data-ttu-id="89eb5-110">Jeśli wartość `GermanVersion` stała jest ustawiona na `True`, kompilator używa wersji niemieckiej.</span><span class="sxs-lookup"><span data-stu-id="89eb5-110">If you set the value of the `GermanVersion` constant to `True`, the compiler uses the German version.</span></span> <span data-ttu-id="89eb5-111">Jeśli żaden z nich nie `True`jest ustawiony na, kod w `Else` ostatnim bloku zostanie uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="89eb5-111">If neither is set to `True`, the code in the last `Else` block runs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="89eb5-112">Funkcja autouzupełniania nie będzie działać podczas edytowania kodu i stosowania dyrektyw warunkowej kompilacji, jeśli kod nie jest częścią bieżącej gałęzi.</span><span class="sxs-lookup"><span data-stu-id="89eb5-112">Autocompletion will not function when editing code and using conditional compilation directives if the code is not part of the current branch.</span></span>  
  
## <a name="declaring-conditional-compilation-constants"></a><span data-ttu-id="89eb5-113">Deklarowanie stałych kompilacji warunkowej</span><span class="sxs-lookup"><span data-stu-id="89eb5-113">Declaring Conditional Compilation Constants</span></span>  
 <span data-ttu-id="89eb5-114">Stałe kompilacji warunkowej można ustawić na jeden z trzech sposobów:</span><span class="sxs-lookup"><span data-stu-id="89eb5-114">You can set conditional compilation constants in one of three ways:</span></span>  
  
- <span data-ttu-id="89eb5-115">W **projektancie projektu**</span><span class="sxs-lookup"><span data-stu-id="89eb5-115">In the **Project Designer**</span></span>  
  
- <span data-ttu-id="89eb5-116">W wierszu polecenia przy użyciu kompilatora wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="89eb5-116">At the command line when using the command-line compiler</span></span>  
  
- <span data-ttu-id="89eb5-117">W kodzie</span><span class="sxs-lookup"><span data-stu-id="89eb5-117">In your code</span></span>  
  
 <span data-ttu-id="89eb5-118">Stałe kompilacji warunkowej mają specjalny zakres i nie można uzyskać do niego dostępu z poziomu kodu standardowego.</span><span class="sxs-lookup"><span data-stu-id="89eb5-118">Conditional compilation constants have a special scope and cannot be accessed from standard code.</span></span> <span data-ttu-id="89eb5-119">Zakres stałej kompilacji warunkowej zależy od sposobu jej ustawienia.</span><span class="sxs-lookup"><span data-stu-id="89eb5-119">The scope of a conditional compilation constant is dependent on the way it is set.</span></span> <span data-ttu-id="89eb5-120">W poniższej tabeli wymieniono zakres stałych zadeklarowanych przy użyciu każdego z trzech sposobów wymienionych powyżej.</span><span class="sxs-lookup"><span data-stu-id="89eb5-120">The following table lists the scope of constants declared using each of the three ways mentioned above.</span></span>  
  
|<span data-ttu-id="89eb5-121">Jak stała jest ustawiona</span><span class="sxs-lookup"><span data-stu-id="89eb5-121">How constant is set</span></span>|<span data-ttu-id="89eb5-122">Zakres stałej</span><span class="sxs-lookup"><span data-stu-id="89eb5-122">Scope of constant</span></span>|  
|---|---|  
|<span data-ttu-id="89eb5-123">**Projektant projektu**</span><span class="sxs-lookup"><span data-stu-id="89eb5-123">**Project Designer**</span></span>|<span data-ttu-id="89eb5-124">Publiczny dla wszystkich plików w projekcie</span><span class="sxs-lookup"><span data-stu-id="89eb5-124">Public to all files in the project</span></span>|  
|<span data-ttu-id="89eb5-125">Wiersz polecenia</span><span class="sxs-lookup"><span data-stu-id="89eb5-125">Command line</span></span>|<span data-ttu-id="89eb5-126">Publiczny dla wszystkich plików przesłanych do kompilatora wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="89eb5-126">Public to all files passed to the command-line compiler</span></span>|  
|<span data-ttu-id="89eb5-127">`#Const`Instrukcja w kodzie</span><span class="sxs-lookup"><span data-stu-id="89eb5-127">`#Const` statement in code</span></span>|<span data-ttu-id="89eb5-128">Prywatny do pliku, w którym jest zadeklarowany</span><span class="sxs-lookup"><span data-stu-id="89eb5-128">Private to the file in which it is declared</span></span>|  
  
|<span data-ttu-id="89eb5-129">Aby ustawić stałe w projektancie projektu</span><span class="sxs-lookup"><span data-stu-id="89eb5-129">To set constants in the Project Designer</span></span>|  
|---|  
|<span data-ttu-id="89eb5-130">-Przed utworzeniem pliku wykonywalnego Ustaw stałe w **projektancie projektu** , wykonując kroki opisane w temacie [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties).</span><span class="sxs-lookup"><span data-stu-id="89eb5-130">-   Before creating your executable file, set constants in the **Project Designer** by following the steps provided in [Managing Project and Solution Properties](/visualstudio/ide/managing-project-and-solution-properties).</span></span>|  
  
|<span data-ttu-id="89eb5-131">Aby ustawić stałe w wierszu polecenia</span><span class="sxs-lookup"><span data-stu-id="89eb5-131">To set constants at the command line</span></span>|  
|---|  
|<span data-ttu-id="89eb5-132">-Użyj **/d** przełącznika, aby wprowadzić stałe kompilacji warunkowej, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="89eb5-132">-   Use the **/d** switch to enter conditional compilation constants, as in the following example:</span></span><br />     `vbc MyProj.vb /d:conFrenchVersion=–1:conANSI=0`<br />     <span data-ttu-id="89eb5-133">Między przełącznikiem **/d** i pierwszą stałą nie jest wymagane żadne miejsce.</span><span class="sxs-lookup"><span data-stu-id="89eb5-133">No space is required between the **/d** switch and the first constant.</span></span> <span data-ttu-id="89eb5-134">Aby uzyskać więcej informacji, zobacz [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md).</span><span class="sxs-lookup"><span data-stu-id="89eb5-134">For more information, see [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md).</span></span><br />     <span data-ttu-id="89eb5-135">Deklaracje wiersza polecenia przesłaniają deklaracje wprowadzone w **projektancie projektu**, ale nie są wymazywane.</span><span class="sxs-lookup"><span data-stu-id="89eb5-135">Command-line declarations override declarations entered in the **Project Designer**, but do not erase them.</span></span> <span data-ttu-id="89eb5-136">Argumenty ustawione w **projektancie projektu** obowiązują dla kolejnych kompilacji.</span><span class="sxs-lookup"><span data-stu-id="89eb5-136">Arguments set in **Project Designer** remain in effect for subsequent compilations.</span></span><br />     <span data-ttu-id="89eb5-137">Podczas pisania stałych w samym kodzie nie istnieją ścisłe reguły dotyczące ich umieszczania, ponieważ ich zakresem jest cały moduł, w którym są one zadeklarowane.</span><span class="sxs-lookup"><span data-stu-id="89eb5-137">When writing constants in the code itself, there are no strict rules as to their placement, since their scope is the entire module in which they are declared.</span></span>|  
  
|<span data-ttu-id="89eb5-138">Aby ustawić stałe w kodzie</span><span class="sxs-lookup"><span data-stu-id="89eb5-138">To set constants in your code</span></span>|  
|---|  
|<span data-ttu-id="89eb5-139">— Umieść stałe w bloku deklaracji modułu, w którym są używane.</span><span class="sxs-lookup"><span data-stu-id="89eb5-139">-   Place the constants in the declaration block of the module in which they are used.</span></span> <span data-ttu-id="89eb5-140">Dzięki temu kod jest zorganizowany i łatwiejszy do czytania.</span><span class="sxs-lookup"><span data-stu-id="89eb5-140">This helps keep your code organized and easier to read.</span></span>|  
  
## <a name="related-topics"></a><span data-ttu-id="89eb5-141">Tematy pokrewne</span><span class="sxs-lookup"><span data-stu-id="89eb5-141">Related Topics</span></span>  
  
|<span data-ttu-id="89eb5-142">Tytuł</span><span class="sxs-lookup"><span data-stu-id="89eb5-142">Title</span></span>|<span data-ttu-id="89eb5-143">Opis</span><span class="sxs-lookup"><span data-stu-id="89eb5-143">Description</span></span>|  
|---|---|  
|[<span data-ttu-id="89eb5-144">Konwencje dotyczące struktury programów i kodu</span><span class="sxs-lookup"><span data-stu-id="89eb5-144">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)|<span data-ttu-id="89eb5-145">Zawiera sugestie ułatwiające odczytywanie i konserwowanie kodu.</span><span class="sxs-lookup"><span data-stu-id="89eb5-145">Provides suggestions for making your code easy to read and maintain.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="89eb5-146">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="89eb5-146">Reference</span></span>  
 [<span data-ttu-id="89eb5-147">#Const, dyrektywa</span><span class="sxs-lookup"><span data-stu-id="89eb5-147">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)  
  
 [<span data-ttu-id="89eb5-148">#If...Then...#Else, dyrektywy</span><span class="sxs-lookup"><span data-stu-id="89eb5-148">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
  
 [<span data-ttu-id="89eb5-149">/define (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="89eb5-149">/define (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/define.md)
