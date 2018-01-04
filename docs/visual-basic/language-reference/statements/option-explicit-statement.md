---
title: "Option Explicit — Instrukcja (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Explicit
- vb.OptionExplicit
helpviewer_keywords:
- declaring variables [Visual Basic], explicit
- forced variable declaration in Option Explicit statement [Visual Basic]
- Explicit keyword
- explicit variable declaration
- Option Explicit statement [Visual Basic]
ms.assetid: e82ac1ad-2cd3-49b2-b985-8bcf016f3fcc
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f3d4c9cd3310e0ec3943c4e2b5e28be5b9a393db
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="option-explicit-statement-visual-basic"></a><span data-ttu-id="e9bb7-102">Option Explicit — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e9bb7-102">Option Explicit Statement (Visual Basic)</span></span>
<span data-ttu-id="e9bb7-103">Wymusza jawnej deklaracji wszystkich zmiennych w pliku lub zezwala na niejawne deklaracji zmiennych.</span><span class="sxs-lookup"><span data-stu-id="e9bb7-103">Forces explicit declaration of all variables in a file, or allows implicit declarations of variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9bb7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e9bb7-104">Syntax</span></span>  
  
```  
Option Explicit { On | Off }  
```  
  
## <a name="parts"></a><span data-ttu-id="e9bb7-105">Części</span><span class="sxs-lookup"><span data-stu-id="e9bb7-105">Parts</span></span>  
 `On`  
 <span data-ttu-id="e9bb7-106">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="e9bb7-106">Optional.</span></span> <span data-ttu-id="e9bb7-107">Włącza `Option Explicit` sprawdzania.</span><span class="sxs-lookup"><span data-stu-id="e9bb7-107">Enables `Option Explicit` checking.</span></span> <span data-ttu-id="e9bb7-108">Jeśli `On` lub `Off` nie zostanie określony, wartością domyślną jest `On`.</span><span class="sxs-lookup"><span data-stu-id="e9bb7-108">If `On` or `Off` is not specified, the default is `On`.</span></span>  
  
 `Off`  
 <span data-ttu-id="e9bb7-109">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="e9bb7-109">Optional.</span></span> <span data-ttu-id="e9bb7-110">Wyłącza `Option Explicit` sprawdzania.</span><span class="sxs-lookup"><span data-stu-id="e9bb7-110">Disables `Option Explicit` checking.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9bb7-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e9bb7-111">Remarks</span></span>  
 <span data-ttu-id="e9bb7-112">Gdy `Option Explicit On` lub `Option Explicit` pojawia się w pliku, musisz jawnie zadeklarować wszystkie zmienne przy użyciu `Dim` lub `ReDim` instrukcje.</span><span class="sxs-lookup"><span data-stu-id="e9bb7-112">When `Option Explicit On` or `Option Explicit` appears in a file, you must explicitly declare all variables by using the `Dim` or `ReDim` statements.</span></span> <span data-ttu-id="e9bb7-113">Jeśli spróbujesz użyć niezadeklarowanego nazwę zmiennej, wystąpi błąd w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e9bb7-113">If you try to use an undeclared variable name, an error occurs at compile time.</span></span> <span data-ttu-id="e9bb7-114">`Option Explicit Off` Instrukcji zezwala na niejawne deklaracji zmiennych.</span><span class="sxs-lookup"><span data-stu-id="e9bb7-114">The `Option Explicit Off` statement allows implicit declaration of variables.</span></span>  
  
 <span data-ttu-id="e9bb7-115">Jeśli używana, `Option Explicit` instrukcji musi występować w pliku przed wszystkimi innymi instrukcjami kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="e9bb7-115">If used, the `Option Explicit` statement must appear in a file before any other source code statements.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e9bb7-116">Ustawienie `Option Explicit` do `Off` zwykle nie jest dobrym rozwiązaniem.</span><span class="sxs-lookup"><span data-stu-id="e9bb7-116">Setting `Option Explicit` to `Off` is generally not a good practice.</span></span> <span data-ttu-id="e9bb7-117">Można wpiszesz nazwę zmiennej w przynajmniej jednej lokalizacji, co może spowodować nieoczekiwane wyniki, gdy program jest uruchamiany.</span><span class="sxs-lookup"><span data-stu-id="e9bb7-117">You could misspell a variable name in one or more locations, which would cause unexpected results when the program is run.</span></span>  
  
## <a name="when-an-option-explicit-statement-is-not-present"></a><span data-ttu-id="e9bb7-118">Jeśli nie jest obecny Option Explicit — instrukcja</span><span class="sxs-lookup"><span data-stu-id="e9bb7-118">When an Option Explicit Statement Is Not Present</span></span>  
 <span data-ttu-id="e9bb7-119">Jeśli kod źródłowy nie zawiera `Option Explicit` instrukcji, **Option Explicit** ustawienie [strona kompilowania, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) jest używany.</span><span class="sxs-lookup"><span data-stu-id="e9bb7-119">If the source code does not contain an `Option Explicit` statement, the **Option Explicit** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="e9bb7-120">Jeśli używana jest kompilatora wiersza polecenia, [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) — opcja kompilatora jest używany.</span><span class="sxs-lookup"><span data-stu-id="e9bb7-120">If the command-line compiler is used, the [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) compiler option is used.</span></span>  
  
#### <a name="to-set-option-explicit-in-the-ide"></a><span data-ttu-id="e9bb7-121">Aby ustawić Option Explicit w środowisku IDE</span><span class="sxs-lookup"><span data-stu-id="e9bb7-121">To set Option Explicit in the IDE</span></span>  
  
1.  <span data-ttu-id="e9bb7-122">W **Eksploratora rozwiązań**, wybierz projekt.</span><span class="sxs-lookup"><span data-stu-id="e9bb7-122">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="e9bb7-123">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="e9bb7-123">On the **Project** menu, click **Properties**.</span></span>  
  
2.  <span data-ttu-id="e9bb7-124">Kliknij przycisk **skompilować** kartę.</span><span class="sxs-lookup"><span data-stu-id="e9bb7-124">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="e9bb7-125">Ustaw wartość **Option Explicit** pole.</span><span class="sxs-lookup"><span data-stu-id="e9bb7-125">Set the value in the **Option Explicit** box.</span></span>  
  
 <span data-ttu-id="e9bb7-126">Podczas tworzenia nowego projektu **Option Explicit** ustawienie **skompilować** ustawiono kartę **Option Explicit** ustawienie **VB domyślne**okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="e9bb7-126">When you create a new project, the **Option Explicit** setting on the **Compile** tab is set to the **Option Explicit** setting in the **VB Defaults** dialog box.</span></span> <span data-ttu-id="e9bb7-127">Aby uzyskać dostęp do **domyślne VB** okna dialogowego, na **narzędzia** menu, kliknij przycisk **opcje**.</span><span class="sxs-lookup"><span data-stu-id="e9bb7-127">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="e9bb7-128">W **opcje** okna dialogowego rozwiń **projekty i rozwiązania**, a następnie kliknij przycisk **domyślne VB**.</span><span class="sxs-lookup"><span data-stu-id="e9bb7-128">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="e9bb7-129">Ustawieniem domyślnym początkowej w **domyślne VB** jest `On`.</span><span class="sxs-lookup"><span data-stu-id="e9bb7-129">The initial default setting in **VB Defaults** is `On`.</span></span>  
  
#### <a name="to-set-option-explicit-on-the-command-line"></a><span data-ttu-id="e9bb7-130">Aby ustawić Option Explicit w wierszu polecenia</span><span class="sxs-lookup"><span data-stu-id="e9bb7-130">To set Option Explicit on the command line</span></span>  
  
-   <span data-ttu-id="e9bb7-131">Obejmują [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) w — opcja kompilatora **vbc** polecenia.</span><span class="sxs-lookup"><span data-stu-id="e9bb7-131">Include the [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9bb7-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9bb7-132">Example</span></span>  
 <span data-ttu-id="e9bb7-133">W poniższym przykładzie użyto `Option Explicit` instrukcji, aby wymusić jawnej deklaracji wszystkich zmiennych.</span><span class="sxs-lookup"><span data-stu-id="e9bb7-133">The following example uses the `Option Explicit` statement to force explicit declaration of all variables.</span></span> <span data-ttu-id="e9bb7-134">Podjęto próbę użycia niezadeklarowanej zmiennej powoduje błąd w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e9bb7-134">Attempting to use an undeclared variable causes an error at compile time.</span></span>  
  
 [!code-vb[VbVbalrStatements#47](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-explicit-statement_1.vb)]  
  
 [!code-vb[VbVbalrStatements#48](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-explicit-statement_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="e9bb7-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9bb7-135">See Also</span></span>  
 [<span data-ttu-id="e9bb7-136">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="e9bb7-136">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="e9bb7-137">ReDim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="e9bb7-137">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)  
 [<span data-ttu-id="e9bb7-138">Option Compare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="e9bb7-138">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [<span data-ttu-id="e9bb7-139">Option Strict, instrukcja</span><span class="sxs-lookup"><span data-stu-id="e9bb7-139">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="e9bb7-140">/optioncompare</span><span class="sxs-lookup"><span data-stu-id="e9bb7-140">/optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [<span data-ttu-id="e9bb7-141">/optionexplicit</span><span class="sxs-lookup"><span data-stu-id="e9bb7-141">/optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [<span data-ttu-id="e9bb7-142">/optionstrict</span><span class="sxs-lookup"><span data-stu-id="e9bb7-142">/optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [<span data-ttu-id="e9bb7-143">Okno dialogowe Opcje domyślne, projektów, Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e9bb7-143">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
