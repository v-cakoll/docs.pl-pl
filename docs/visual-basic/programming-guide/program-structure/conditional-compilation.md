---
title: Kompilacja warunkowa
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], about conditional compilation
- compilation [Visual Basic], conditional
ms.assetid: 9c35e55e-7eee-44fb-a586-dad1f1884848
ms.openlocfilehash: c3eb1eb57b3d76e762ed53edb3b168ad96abec39
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403268"
---
# <a name="conditional-compilation-in-visual-basic"></a><span data-ttu-id="c3231-102">Kompilacja warunkowa w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c3231-102">Conditional Compilation in Visual Basic</span></span>
<span data-ttu-id="c3231-103">W *kompilacji warunkowej*poszczególne bloki kodu w programie są kompilowane wybiórczo, podczas gdy inne są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="c3231-103">In *conditional compilation*, particular blocks of code in a program are compiled selectively while others are ignored.</span></span>  
  
 <span data-ttu-id="c3231-104">Na przykład możesz chcieć napisać instrukcje debugowania, które porównują szybkość różnych podejść do tego samego zadania programistycznego, lub można zlokalizować aplikację dla wielu języków.</span><span class="sxs-lookup"><span data-stu-id="c3231-104">For example, you may want to write debugging statements that compare the speed of different approaches to the same programming task, or you may want to localize an application for multiple languages.</span></span> <span data-ttu-id="c3231-105">Instrukcje kompilacji warunkowej są przeznaczone do uruchamiania w czasie kompilacji, a nie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c3231-105">Conditional compilation statements are designed to run during compile time, not at run time.</span></span>  
  
 <span data-ttu-id="c3231-106">Należy zauważyć, że bloki kodu mają być warunkowo kompilowane z `#If...Then...#Else` dyrektywą.</span><span class="sxs-lookup"><span data-stu-id="c3231-106">You denote blocks of code to be conditionally compiled with the `#If...Then...#Else` directive.</span></span> <span data-ttu-id="c3231-107">Aby na przykład utworzyć wersje językowe języka francuskiego i niemieckiego tej samej aplikacji z tego samego kodu źródłowego, segmenty kodu specyficzne dla platformy można osadzić w `#If...Then` instrukcjach korzystających ze wstępnie zdefiniowanych stałych `FrenchVersion` i `GermanVersion` .</span><span class="sxs-lookup"><span data-stu-id="c3231-107">For example, to create French- and German-language versions of the same application from the same source code, you embed platform-specific code segments in `#If...Then` statements using the predefined constants `FrenchVersion` and `GermanVersion`.</span></span> <span data-ttu-id="c3231-108">W poniższym przykładzie pokazano, jak:</span><span class="sxs-lookup"><span data-stu-id="c3231-108">The following example demonstrates how:</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#5)]  
  
 <span data-ttu-id="c3231-109">Jeśli ustawisz wartość `FrenchVersion` stałej kompilacji warunkowej na `True` w czasie kompilacji, zostanie skompilowany kod warunkowy dla wersji francuskiej.</span><span class="sxs-lookup"><span data-stu-id="c3231-109">If you set the value of the `FrenchVersion` conditional compilation constant to `True` at compile time, the conditional code for the French version is compiled.</span></span> <span data-ttu-id="c3231-110">Jeśli wartość stała jest ustawiona `GermanVersion` na `True` , kompilator używa wersji niemieckiej.</span><span class="sxs-lookup"><span data-stu-id="c3231-110">If you set the value of the `GermanVersion` constant to `True`, the compiler uses the German version.</span></span> <span data-ttu-id="c3231-111">Jeśli żaden z nich nie jest ustawiony na `True` , kod w ostatnim `Else` bloku zostanie uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="c3231-111">If neither is set to `True`, the code in the last `Else` block runs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c3231-112">Funkcja autouzupełniania nie będzie działać podczas edytowania kodu i stosowania dyrektyw warunkowej kompilacji, jeśli kod nie jest częścią bieżącej gałęzi.</span><span class="sxs-lookup"><span data-stu-id="c3231-112">Autocompletion will not function when editing code and using conditional compilation directives if the code is not part of the current branch.</span></span>  
  
## <a name="declaring-conditional-compilation-constants"></a><span data-ttu-id="c3231-113">Deklarowanie stałych kompilacji warunkowej</span><span class="sxs-lookup"><span data-stu-id="c3231-113">Declaring Conditional Compilation Constants</span></span>  
 <span data-ttu-id="c3231-114">Stałe kompilacji warunkowej można ustawić na jeden z trzech sposobów:</span><span class="sxs-lookup"><span data-stu-id="c3231-114">You can set conditional compilation constants in one of three ways:</span></span>  
  
- <span data-ttu-id="c3231-115">W **projektancie projektu**</span><span class="sxs-lookup"><span data-stu-id="c3231-115">In the **Project Designer**</span></span>  
  
- <span data-ttu-id="c3231-116">W wierszu polecenia przy użyciu kompilatora wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="c3231-116">At the command line when using the command-line compiler</span></span>  
  
- <span data-ttu-id="c3231-117">W kodzie</span><span class="sxs-lookup"><span data-stu-id="c3231-117">In your code</span></span>  
  
 <span data-ttu-id="c3231-118">Stałe kompilacji warunkowej mają specjalny zakres i nie można uzyskać do niego dostępu z poziomu kodu standardowego.</span><span class="sxs-lookup"><span data-stu-id="c3231-118">Conditional compilation constants have a special scope and cannot be accessed from standard code.</span></span> <span data-ttu-id="c3231-119">Zakres stałej kompilacji warunkowej zależy od sposobu jej ustawienia.</span><span class="sxs-lookup"><span data-stu-id="c3231-119">The scope of a conditional compilation constant is dependent on the way it is set.</span></span> <span data-ttu-id="c3231-120">W poniższej tabeli wymieniono zakres stałych zadeklarowanych przy użyciu każdego z trzech sposobów wymienionych powyżej.</span><span class="sxs-lookup"><span data-stu-id="c3231-120">The following table lists the scope of constants declared using each of the three ways mentioned above.</span></span>  
  
|<span data-ttu-id="c3231-121">Jak stała jest ustawiona</span><span class="sxs-lookup"><span data-stu-id="c3231-121">How constant is set</span></span>|<span data-ttu-id="c3231-122">Zakres stałej</span><span class="sxs-lookup"><span data-stu-id="c3231-122">Scope of constant</span></span>|  
|---|---|  
|<span data-ttu-id="c3231-123">**Projektant projektu**</span><span class="sxs-lookup"><span data-stu-id="c3231-123">**Project Designer**</span></span>|<span data-ttu-id="c3231-124">Publiczny dla wszystkich plików w projekcie</span><span class="sxs-lookup"><span data-stu-id="c3231-124">Public to all files in the project</span></span>|  
|<span data-ttu-id="c3231-125">Wiersz polecenia</span><span class="sxs-lookup"><span data-stu-id="c3231-125">Command line</span></span>|<span data-ttu-id="c3231-126">Publiczny dla wszystkich plików przesłanych do kompilatora wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="c3231-126">Public to all files passed to the command-line compiler</span></span>|  
|<span data-ttu-id="c3231-127">`#Const`Instrukcja w kodzie</span><span class="sxs-lookup"><span data-stu-id="c3231-127">`#Const` statement in code</span></span>|<span data-ttu-id="c3231-128">Prywatny do pliku, w którym jest zadeklarowany</span><span class="sxs-lookup"><span data-stu-id="c3231-128">Private to the file in which it is declared</span></span>|  
  
|<span data-ttu-id="c3231-129">Aby ustawić stałe w projektancie projektu</span><span class="sxs-lookup"><span data-stu-id="c3231-129">To set constants in the Project Designer</span></span>|  
|---|  
|<span data-ttu-id="c3231-130">-Przed utworzeniem pliku wykonywalnego Ustaw stałe w **projektancie projektu** , wykonując kroki opisane w temacie [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties).</span><span class="sxs-lookup"><span data-stu-id="c3231-130">-   Before creating your executable file, set constants in the **Project Designer** by following the steps provided in [Managing Project and Solution Properties](/visualstudio/ide/managing-project-and-solution-properties).</span></span>|  
  
|<span data-ttu-id="c3231-131">Aby ustawić stałe w wierszu polecenia</span><span class="sxs-lookup"><span data-stu-id="c3231-131">To set constants at the command line</span></span>|  
|---|  
|<span data-ttu-id="c3231-132">— Użyj przełącznika **-d** , aby wprowadzić stałe kompilacji warunkowej, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="c3231-132">-   Use the **-d** switch to enter conditional compilation constants, as in the following example:</span></span><br />     `vbc MyProj.vb /d:conFrenchVersion=–1:conANSI=0`<br />     <span data-ttu-id="c3231-133">Między przełącznikiem **-d** i pierwszą stałą nie jest wymagane miejsce.</span><span class="sxs-lookup"><span data-stu-id="c3231-133">No space is required between the **-d** switch and the first constant.</span></span> <span data-ttu-id="c3231-134">Aby uzyskać więcej informacji, zobacz [-define (Visual Basic)](../../reference/command-line-compiler/define.md).</span><span class="sxs-lookup"><span data-stu-id="c3231-134">For more information, see [-define (Visual Basic)](../../reference/command-line-compiler/define.md).</span></span><br />     <span data-ttu-id="c3231-135">Deklaracje wiersza polecenia przesłaniają deklaracje wprowadzone w **projektancie projektu**, ale nie są wymazywane.</span><span class="sxs-lookup"><span data-stu-id="c3231-135">Command-line declarations override declarations entered in the **Project Designer**, but do not erase them.</span></span> <span data-ttu-id="c3231-136">Argumenty ustawione w **projektancie projektu** obowiązują dla kolejnych kompilacji.</span><span class="sxs-lookup"><span data-stu-id="c3231-136">Arguments set in **Project Designer** remain in effect for subsequent compilations.</span></span><br />     <span data-ttu-id="c3231-137">Podczas pisania stałych w samym kodzie nie istnieją ścisłe reguły dotyczące ich umieszczania, ponieważ ich zakresem jest cały moduł, w którym są one zadeklarowane.</span><span class="sxs-lookup"><span data-stu-id="c3231-137">When writing constants in the code itself, there are no strict rules as to their placement, since their scope is the entire module in which they are declared.</span></span>|  
  
|<span data-ttu-id="c3231-138">Aby ustawić stałe w kodzie</span><span class="sxs-lookup"><span data-stu-id="c3231-138">To set constants in your code</span></span>|  
|---|  
|<span data-ttu-id="c3231-139">— Umieść stałe w bloku deklaracji modułu, w którym są używane.</span><span class="sxs-lookup"><span data-stu-id="c3231-139">-   Place the constants in the declaration block of the module in which they are used.</span></span> <span data-ttu-id="c3231-140">Dzięki temu kod jest zorganizowany i łatwiejszy do czytania.</span><span class="sxs-lookup"><span data-stu-id="c3231-140">This helps keep your code organized and easier to read.</span></span>|  
  
## <a name="related-topics"></a><span data-ttu-id="c3231-141">Tematy pokrewne</span><span class="sxs-lookup"><span data-stu-id="c3231-141">Related Topics</span></span>  
  
|<span data-ttu-id="c3231-142">Tytuł</span><span class="sxs-lookup"><span data-stu-id="c3231-142">Title</span></span>|<span data-ttu-id="c3231-143">Opis</span><span class="sxs-lookup"><span data-stu-id="c3231-143">Description</span></span>|  
|---|---|  
|[<span data-ttu-id="c3231-144">Struktura programu i konwencje związane z kodem</span><span class="sxs-lookup"><span data-stu-id="c3231-144">Program Structure and Code Conventions</span></span>](program-structure-and-code-conventions.md)|<span data-ttu-id="c3231-145">Zawiera sugestie ułatwiające odczytywanie i konserwowanie kodu.</span><span class="sxs-lookup"><span data-stu-id="c3231-145">Provides suggestions for making your code easy to read and maintain.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="c3231-146">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="c3231-146">Reference</span></span>  
 [<span data-ttu-id="c3231-147">#Const — dyrektywa</span><span class="sxs-lookup"><span data-stu-id="c3231-147">#Const Directive</span></span>](../../language-reference/directives/const-directive.md)  
  
 [<span data-ttu-id="c3231-148">#If... Then... #Else — dyrektywy</span><span class="sxs-lookup"><span data-stu-id="c3231-148">#If...Then...#Else Directives</span></span>](../../language-reference/directives/if-then-else-directives.md)  
  
 [<span data-ttu-id="c3231-149">-Definiuj (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c3231-149">-define (Visual Basic)</span></span>](../../reference/command-line-compiler/define.md)
