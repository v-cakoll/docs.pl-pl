---
title: Option Explicit — Instrukcja (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 3a2d81b1441052c132e4739dfe6045f8c3a026d4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604604"
---
# <a name="option-explicit-statement-visual-basic"></a><span data-ttu-id="c2316-102">Option Explicit — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c2316-102">Option Explicit Statement (Visual Basic)</span></span>
<span data-ttu-id="c2316-103">Wymusza jawnej deklaracji wszystkich zmiennych w pliku lub zezwala na niejawne deklaracji zmiennych.</span><span class="sxs-lookup"><span data-stu-id="c2316-103">Forces explicit declaration of all variables in a file, or allows implicit declarations of variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2316-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c2316-104">Syntax</span></span>  
  
```  
Option Explicit { On | Off }  
```  
  
## <a name="parts"></a><span data-ttu-id="c2316-105">Części</span><span class="sxs-lookup"><span data-stu-id="c2316-105">Parts</span></span>  
 `On`  
 <span data-ttu-id="c2316-106">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="c2316-106">Optional.</span></span> <span data-ttu-id="c2316-107">Włącza `Option Explicit` sprawdzania.</span><span class="sxs-lookup"><span data-stu-id="c2316-107">Enables `Option Explicit` checking.</span></span> <span data-ttu-id="c2316-108">Jeśli `On` lub `Off` nie zostanie określony, wartością domyślną jest `On`.</span><span class="sxs-lookup"><span data-stu-id="c2316-108">If `On` or `Off` is not specified, the default is `On`.</span></span>  
  
 `Off`  
 <span data-ttu-id="c2316-109">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="c2316-109">Optional.</span></span> <span data-ttu-id="c2316-110">Wyłącza `Option Explicit` sprawdzania.</span><span class="sxs-lookup"><span data-stu-id="c2316-110">Disables `Option Explicit` checking.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c2316-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c2316-111">Remarks</span></span>  
 <span data-ttu-id="c2316-112">Gdy `Option Explicit On` lub `Option Explicit` pojawia się w pliku, musisz jawnie zadeklarować wszystkie zmienne przy użyciu `Dim` lub `ReDim` instrukcje.</span><span class="sxs-lookup"><span data-stu-id="c2316-112">When `Option Explicit On` or `Option Explicit` appears in a file, you must explicitly declare all variables by using the `Dim` or `ReDim` statements.</span></span> <span data-ttu-id="c2316-113">Jeśli spróbujesz użyć niezadeklarowanego nazwę zmiennej, wystąpi błąd w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="c2316-113">If you try to use an undeclared variable name, an error occurs at compile time.</span></span> <span data-ttu-id="c2316-114">`Option Explicit Off` Instrukcji zezwala na niejawne deklaracji zmiennych.</span><span class="sxs-lookup"><span data-stu-id="c2316-114">The `Option Explicit Off` statement allows implicit declaration of variables.</span></span>  
  
 <span data-ttu-id="c2316-115">Jeśli używana, `Option Explicit` instrukcji musi występować w pliku przed wszystkimi innymi instrukcjami kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="c2316-115">If used, the `Option Explicit` statement must appear in a file before any other source code statements.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c2316-116">Ustawienie `Option Explicit` do `Off` zwykle nie jest dobrym rozwiązaniem.</span><span class="sxs-lookup"><span data-stu-id="c2316-116">Setting `Option Explicit` to `Off` is generally not a good practice.</span></span> <span data-ttu-id="c2316-117">Można wpiszesz nazwę zmiennej w przynajmniej jednej lokalizacji, co może spowodować nieoczekiwane wyniki, gdy program jest uruchamiany.</span><span class="sxs-lookup"><span data-stu-id="c2316-117">You could misspell a variable name in one or more locations, which would cause unexpected results when the program is run.</span></span>  
  
## <a name="when-an-option-explicit-statement-is-not-present"></a><span data-ttu-id="c2316-118">Jeśli nie jest obecny Option Explicit — instrukcja</span><span class="sxs-lookup"><span data-stu-id="c2316-118">When an Option Explicit Statement Is Not Present</span></span>  
 <span data-ttu-id="c2316-119">Jeśli kod źródłowy nie zawiera `Option Explicit` instrukcji, **Option Explicit** ustawienie [strona kompilowania, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) jest używany.</span><span class="sxs-lookup"><span data-stu-id="c2316-119">If the source code does not contain an `Option Explicit` statement, the **Option Explicit** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="c2316-120">Jeśli używana jest kompilatora wiersza polecenia, [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) — opcja kompilatora jest używany.</span><span class="sxs-lookup"><span data-stu-id="c2316-120">If the command-line compiler is used, the [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) compiler option is used.</span></span>  
  
#### <a name="to-set-option-explicit-in-the-ide"></a><span data-ttu-id="c2316-121">Aby ustawić Option Explicit w środowisku IDE</span><span class="sxs-lookup"><span data-stu-id="c2316-121">To set Option Explicit in the IDE</span></span>  
  
1.  <span data-ttu-id="c2316-122">W **Eksploratora rozwiązań**, wybierz projekt.</span><span class="sxs-lookup"><span data-stu-id="c2316-122">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="c2316-123">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="c2316-123">On the **Project** menu, click **Properties**.</span></span>  
  
2.  <span data-ttu-id="c2316-124">Kliknij przycisk **skompilować** kartę.</span><span class="sxs-lookup"><span data-stu-id="c2316-124">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="c2316-125">Ustaw wartość **Option Explicit** pole.</span><span class="sxs-lookup"><span data-stu-id="c2316-125">Set the value in the **Option Explicit** box.</span></span>  
  
 <span data-ttu-id="c2316-126">Podczas tworzenia nowego projektu **Option Explicit** ustawienie **skompilować** ustawiono kartę **Option Explicit** ustawienie **VB domyślne**okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="c2316-126">When you create a new project, the **Option Explicit** setting on the **Compile** tab is set to the **Option Explicit** setting in the **VB Defaults** dialog box.</span></span> <span data-ttu-id="c2316-127">Aby uzyskać dostęp do **domyślne VB** okna dialogowego, na **narzędzia** menu, kliknij przycisk **opcje**.</span><span class="sxs-lookup"><span data-stu-id="c2316-127">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="c2316-128">W **opcje** okna dialogowego rozwiń **projekty i rozwiązania**, a następnie kliknij przycisk **domyślne VB**.</span><span class="sxs-lookup"><span data-stu-id="c2316-128">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="c2316-129">Ustawieniem domyślnym początkowej w **domyślne VB** jest `On`.</span><span class="sxs-lookup"><span data-stu-id="c2316-129">The initial default setting in **VB Defaults** is `On`.</span></span>  
  
#### <a name="to-set-option-explicit-on-the-command-line"></a><span data-ttu-id="c2316-130">Aby ustawić Option Explicit w wierszu polecenia</span><span class="sxs-lookup"><span data-stu-id="c2316-130">To set Option Explicit on the command line</span></span>  
  
-   <span data-ttu-id="c2316-131">Obejmują [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) w — opcja kompilatora **vbc** polecenia.</span><span class="sxs-lookup"><span data-stu-id="c2316-131">Include the [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2316-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="c2316-132">Example</span></span>  
 <span data-ttu-id="c2316-133">W poniższym przykładzie użyto `Option Explicit` instrukcji, aby wymusić jawnej deklaracji wszystkich zmiennych.</span><span class="sxs-lookup"><span data-stu-id="c2316-133">The following example uses the `Option Explicit` statement to force explicit declaration of all variables.</span></span> <span data-ttu-id="c2316-134">Podjęto próbę użycia niezadeklarowanej zmiennej powoduje błąd w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="c2316-134">Attempting to use an undeclared variable causes an error at compile time.</span></span>  
  
 [!code-vb[VbVbalrStatements#47](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-explicit-statement_1.vb)]  
  
 [!code-vb[VbVbalrStatements#48](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-explicit-statement_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="c2316-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c2316-135">See Also</span></span>  
 [<span data-ttu-id="c2316-136">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="c2316-136">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="c2316-137">ReDim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="c2316-137">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)  
 [<span data-ttu-id="c2316-138">Option Compare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="c2316-138">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [<span data-ttu-id="c2316-139">Option Strict, instrukcja</span><span class="sxs-lookup"><span data-stu-id="c2316-139">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="c2316-140">/optioncompare</span><span class="sxs-lookup"><span data-stu-id="c2316-140">/optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [<span data-ttu-id="c2316-141">/optionexplicit</span><span class="sxs-lookup"><span data-stu-id="c2316-141">/optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [<span data-ttu-id="c2316-142">/optionstrict</span><span class="sxs-lookup"><span data-stu-id="c2316-142">/optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [<span data-ttu-id="c2316-143">Okno dialogowe Opcje domyślne, projektów, Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c2316-143">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
