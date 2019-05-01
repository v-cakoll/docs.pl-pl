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
ms.openlocfilehash: 0a319ba4259e66ed9a37aa2de9e97d2335b78663
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61784049"
---
# <a name="option-explicit-statement-visual-basic"></a><span data-ttu-id="2ec2d-102">Option Explicit — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2ec2d-102">Option Explicit Statement (Visual Basic)</span></span>
<span data-ttu-id="2ec2d-103">Wymusza jawnej deklaracji wszystkich zmiennych w pliku lub zezwala na niejawne deklaracje zmiennych.</span><span class="sxs-lookup"><span data-stu-id="2ec2d-103">Forces explicit declaration of all variables in a file, or allows implicit declarations of variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ec2d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2ec2d-104">Syntax</span></span>  
  
```  
Option Explicit { On | Off }  
```  
  
## <a name="parts"></a><span data-ttu-id="2ec2d-105">Części</span><span class="sxs-lookup"><span data-stu-id="2ec2d-105">Parts</span></span>  
 `On`  
 <span data-ttu-id="2ec2d-106">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="2ec2d-106">Optional.</span></span> <span data-ttu-id="2ec2d-107">Włącza `Option Explicit` sprawdzania.</span><span class="sxs-lookup"><span data-stu-id="2ec2d-107">Enables `Option Explicit` checking.</span></span> <span data-ttu-id="2ec2d-108">Jeśli `On` lub `Off` nie zostanie określony, wartością domyślną jest `On`.</span><span class="sxs-lookup"><span data-stu-id="2ec2d-108">If `On` or `Off` is not specified, the default is `On`.</span></span>  
  
 `Off`  
 <span data-ttu-id="2ec2d-109">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="2ec2d-109">Optional.</span></span> <span data-ttu-id="2ec2d-110">Wyłącza `Option Explicit` sprawdzania.</span><span class="sxs-lookup"><span data-stu-id="2ec2d-110">Disables `Option Explicit` checking.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ec2d-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2ec2d-111">Remarks</span></span>  
 <span data-ttu-id="2ec2d-112">Gdy `Option Explicit On` lub `Option Explicit` pojawia się w pliku, należy jawnie deklarować wszystkie zmienne, za pomocą `Dim` lub `ReDim` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="2ec2d-112">When `Option Explicit On` or `Option Explicit` appears in a file, you must explicitly declare all variables by using the `Dim` or `ReDim` statements.</span></span> <span data-ttu-id="2ec2d-113">Jeśli zostanie podjęta próba użycia nazwy zmiennej niezadeklarowany, wystąpi błąd w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="2ec2d-113">If you try to use an undeclared variable name, an error occurs at compile time.</span></span> <span data-ttu-id="2ec2d-114">`Option Explicit Off` Instrukcji umożliwia niejawne deklaracji zmiennych.</span><span class="sxs-lookup"><span data-stu-id="2ec2d-114">The `Option Explicit Off` statement allows implicit declaration of variables.</span></span>  
  
 <span data-ttu-id="2ec2d-115">Jeśli używane, `Option Explicit` instrukcja musi znajdować się w pliku przed wszystkimi innymi instrukcjami kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="2ec2d-115">If used, the `Option Explicit` statement must appear in a file before any other source code statements.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2ec2d-116">Ustawienie `Option Explicit` do `Off` zwykle nie jest dobrym rozwiązaniem.</span><span class="sxs-lookup"><span data-stu-id="2ec2d-116">Setting `Option Explicit` to `Off` is generally not a good practice.</span></span> <span data-ttu-id="2ec2d-117">Można błędnego wpisania nazwy zmiennej w przynajmniej jednej lokalizacji, co mogłoby spowodować nieoczekiwane wyniki, gdy program jest uruchamiany.</span><span class="sxs-lookup"><span data-stu-id="2ec2d-117">You could misspell a variable name in one or more locations, which would cause unexpected results when the program is run.</span></span>  
  
## <a name="when-an-option-explicit-statement-is-not-present"></a><span data-ttu-id="2ec2d-118">Jeśli nie jest obecny Option Explicit — instrukcja</span><span class="sxs-lookup"><span data-stu-id="2ec2d-118">When an Option Explicit Statement Is Not Present</span></span>  
 <span data-ttu-id="2ec2d-119">Jeśli kod źródłowy nie zawiera `Option Explicit` instrukcji **Option Explicit** ustawienie [strona kompilowania, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) jest używany.</span><span class="sxs-lookup"><span data-stu-id="2ec2d-119">If the source code does not contain an `Option Explicit` statement, the **Option Explicit** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="2ec2d-120">Jeśli jest używany kompilator w wierszu polecenia, [/optionexplicit —](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) — opcja kompilatora jest używany.</span><span class="sxs-lookup"><span data-stu-id="2ec2d-120">If the command-line compiler is used, the [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) compiler option is used.</span></span>  
  
#### <a name="to-set-option-explicit-in-the-ide"></a><span data-ttu-id="2ec2d-121">Aby ustawić Option Explicit w środowisku IDE</span><span class="sxs-lookup"><span data-stu-id="2ec2d-121">To set Option Explicit in the IDE</span></span>  
  
1. <span data-ttu-id="2ec2d-122">W **Eksploratora rozwiązań**, wybierz projekt.</span><span class="sxs-lookup"><span data-stu-id="2ec2d-122">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="2ec2d-123">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="2ec2d-123">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="2ec2d-124">Kliknij przycisk **skompilować** kartę.</span><span class="sxs-lookup"><span data-stu-id="2ec2d-124">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="2ec2d-125">Ustaw wartość w **Option Explicit** pole.</span><span class="sxs-lookup"><span data-stu-id="2ec2d-125">Set the value in the **Option Explicit** box.</span></span>  
  
 <span data-ttu-id="2ec2d-126">Podczas tworzenia nowego projektu **Option Explicit** ustawienie **skompilować** karta jest ustawiona na **Option Explicit** ustawienie w **VB domyślnie**okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="2ec2d-126">When you create a new project, the **Option Explicit** setting on the **Compile** tab is set to the **Option Explicit** setting in the **VB Defaults** dialog box.</span></span> <span data-ttu-id="2ec2d-127">Aby uzyskać dostęp do **ustawienia domyślne VB** dialogowym **narzędzia** menu, kliknij przycisk **opcje**.</span><span class="sxs-lookup"><span data-stu-id="2ec2d-127">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="2ec2d-128">W **opcje** okna dialogowego rozwiń **projekty i rozwiązania**, a następnie kliknij przycisk **ustawienia domyślne VB**.</span><span class="sxs-lookup"><span data-stu-id="2ec2d-128">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="2ec2d-129">Ustawieniem domyślnym początkowej w **ustawienia domyślne VB** jest `On`.</span><span class="sxs-lookup"><span data-stu-id="2ec2d-129">The initial default setting in **VB Defaults** is `On`.</span></span>  
  
#### <a name="to-set-option-explicit-on-the-command-line"></a><span data-ttu-id="2ec2d-130">Aby ustawić Option Explicit, w wierszu polecenia</span><span class="sxs-lookup"><span data-stu-id="2ec2d-130">To set Option Explicit on the command line</span></span>  
  
- <span data-ttu-id="2ec2d-131">Obejmują [/optionexplicit —](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) w — opcja kompilatora **vbc** polecenia.</span><span class="sxs-lookup"><span data-stu-id="2ec2d-131">Include the [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ec2d-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="2ec2d-132">Example</span></span>  
 <span data-ttu-id="2ec2d-133">W poniższym przykładzie użyto `Option Explicit` instrukcję, aby wymusić jawnej deklaracji wszystkich zmiennych.</span><span class="sxs-lookup"><span data-stu-id="2ec2d-133">The following example uses the `Option Explicit` statement to force explicit declaration of all variables.</span></span> <span data-ttu-id="2ec2d-134">Podjęto próbę użycia niezadeklarowana zmienna powoduje błąd w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="2ec2d-134">Attempting to use an undeclared variable causes an error at compile time.</span></span>  
  
 [!code-vb[VbVbalrStatements#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#47)]  
  
 [!code-vb[VbVbalrStatements#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#48)]  
  
## <a name="see-also"></a><span data-ttu-id="2ec2d-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2ec2d-135">See also</span></span>

- [<span data-ttu-id="2ec2d-136">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2ec2d-136">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="2ec2d-137">ReDim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2ec2d-137">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)
- [<span data-ttu-id="2ec2d-138">Option Compare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2ec2d-138">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [<span data-ttu-id="2ec2d-139">Option Strict, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2ec2d-139">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="2ec2d-140">/optioncompare</span><span class="sxs-lookup"><span data-stu-id="2ec2d-140">/optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="2ec2d-141">/optionexplicit</span><span class="sxs-lookup"><span data-stu-id="2ec2d-141">/optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [<span data-ttu-id="2ec2d-142">/optionstrict</span><span class="sxs-lookup"><span data-stu-id="2ec2d-142">/optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [<span data-ttu-id="2ec2d-143">Domyślne ustawienia programu Visual Basic, Projekty, Opcje — okno dialogowe</span><span class="sxs-lookup"><span data-stu-id="2ec2d-143">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
