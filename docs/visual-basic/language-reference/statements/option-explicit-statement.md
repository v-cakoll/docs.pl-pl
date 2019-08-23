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
ms.openlocfilehash: c027964d185d7f69c0a56a4386bedc2d8f9d2eac
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912336"
---
# <a name="option-explicit-statement-visual-basic"></a><span data-ttu-id="4c29f-102">Option Explicit — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4c29f-102">Option Explicit Statement (Visual Basic)</span></span>
<span data-ttu-id="4c29f-103">Wymusza jawną deklarację wszystkich zmiennych w pliku lub zezwala na niejawne deklaracje zmiennych.</span><span class="sxs-lookup"><span data-stu-id="4c29f-103">Forces explicit declaration of all variables in a file, or allows implicit declarations of variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c29f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4c29f-104">Syntax</span></span>  
  
```  
Option Explicit { On | Off }  
```  
  
## <a name="parts"></a><span data-ttu-id="4c29f-105">Części</span><span class="sxs-lookup"><span data-stu-id="4c29f-105">Parts</span></span>  
 `On`  
 <span data-ttu-id="4c29f-106">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="4c29f-106">Optional.</span></span> <span data-ttu-id="4c29f-107">Włącza `Option Explicit` sprawdzanie.</span><span class="sxs-lookup"><span data-stu-id="4c29f-107">Enables `Option Explicit` checking.</span></span> <span data-ttu-id="4c29f-108">Jeśli `On` `On`lub `Off` nie jest określony, wartość domyślna to.</span><span class="sxs-lookup"><span data-stu-id="4c29f-108">If `On` or `Off` is not specified, the default is `On`.</span></span>  
  
 `Off`  
 <span data-ttu-id="4c29f-109">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="4c29f-109">Optional.</span></span> <span data-ttu-id="4c29f-110">Wyłącza `Option Explicit` sprawdzanie.</span><span class="sxs-lookup"><span data-stu-id="4c29f-110">Disables `Option Explicit` checking.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4c29f-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4c29f-111">Remarks</span></span>  
 <span data-ttu-id="4c29f-112">Gdy `Option Explicit On` `Dim` `ReDim` lub `Option Explicit` pojawia się w pliku, należy jawnie zadeklarować wszystkie zmienne przy użyciu instrukcji or.</span><span class="sxs-lookup"><span data-stu-id="4c29f-112">When `Option Explicit On` or `Option Explicit` appears in a file, you must explicitly declare all variables by using the `Dim` or `ReDim` statements.</span></span> <span data-ttu-id="4c29f-113">Jeśli spróbujesz użyć niezadeklarowanej nazwy zmiennej, wystąpi błąd w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="4c29f-113">If you try to use an undeclared variable name, an error occurs at compile time.</span></span> <span data-ttu-id="4c29f-114">`Option Explicit Off` Instrukcja umożliwia niejawną deklarację zmiennych.</span><span class="sxs-lookup"><span data-stu-id="4c29f-114">The `Option Explicit Off` statement allows implicit declaration of variables.</span></span>  
  
 <span data-ttu-id="4c29f-115">Jeśli jest `Option Explicit` używana, instrukcja musi pojawić się w pliku przed innymi instrukcjami kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="4c29f-115">If used, the `Option Explicit` statement must appear in a file before any other source code statements.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4c29f-116">Ustawienie `Option Explicit` na`Off` ogół nie jest dobrym sposobem.</span><span class="sxs-lookup"><span data-stu-id="4c29f-116">Setting `Option Explicit` to `Off` is generally not a good practice.</span></span> <span data-ttu-id="4c29f-117">W co najmniej jednej lokalizacji można wypróbować nazwę zmiennej, co spowodowałoby nieoczekiwane wyniki, gdy program zostanie uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="4c29f-117">You could misspell a variable name in one or more locations, which would cause unexpected results when the program is run.</span></span>  
  
## <a name="when-an-option-explicit-statement-is-not-present"></a><span data-ttu-id="4c29f-118">Gdy nie ma instrukcji Option Explicit</span><span class="sxs-lookup"><span data-stu-id="4c29f-118">When an Option Explicit Statement Is Not Present</span></span>  
 <span data-ttu-id="4c29f-119">Jeśli kod źródłowy nie zawiera `Option Explicit` instrukcji, zostanie użyta **opcja jawne** ustawienie na [stronie kompilowania, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) .</span><span class="sxs-lookup"><span data-stu-id="4c29f-119">If the source code does not contain an `Option Explicit` statement, the **Option Explicit** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="4c29f-120">Jeśli używany jest kompilator wiersza polecenia, opcja kompilatora [/optionexplicit —](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) jest używana.</span><span class="sxs-lookup"><span data-stu-id="4c29f-120">If the command-line compiler is used, the [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) compiler option is used.</span></span>  
  
#### <a name="to-set-option-explicit-in-the-ide"></a><span data-ttu-id="4c29f-121">Aby ustawić opcję jawną w środowisku IDE</span><span class="sxs-lookup"><span data-stu-id="4c29f-121">To set Option Explicit in the IDE</span></span>  
  
1. <span data-ttu-id="4c29f-122">W **Eksplorator rozwiązań**wybierz projekt.</span><span class="sxs-lookup"><span data-stu-id="4c29f-122">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="4c29f-123">W menu **projekt** kliknij polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="4c29f-123">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="4c29f-124">Kliknij kartę **kompilacja** .</span><span class="sxs-lookup"><span data-stu-id="4c29f-124">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="4c29f-125">Ustaw wartość w polu **opcja jawna** .</span><span class="sxs-lookup"><span data-stu-id="4c29f-125">Set the value in the **Option Explicit** box.</span></span>  
  
 <span data-ttu-id="4c29f-126">Podczas tworzenia nowego projektu **opcja ustawienie jawne** na karcie kompilowania jest ustawiona na wartość ustawienie **jawne** w oknie dialogowym **Ustawienia domyślne języka vb** .</span><span class="sxs-lookup"><span data-stu-id="4c29f-126">When you create a new project, the **Option Explicit** setting on the **Compile** tab is set to the **Option Explicit** setting in the **VB Defaults** dialog box.</span></span> <span data-ttu-id="4c29f-127">Aby uzyskać dostęp do okna dialogowego **Ustawienia domyślne VB** , w menu **Narzędzia** kliknij polecenie **Opcje**.</span><span class="sxs-lookup"><span data-stu-id="4c29f-127">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="4c29f-128">W oknie dialogowym **Opcje** rozwiń węzeł **projekty i rozwiązania**, a następnie kliknij pozycję **Ustawienia domyślne w języku VB**.</span><span class="sxs-lookup"><span data-stu-id="4c29f-128">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="4c29f-129">Początkowe domyślne ustawienie w **języku VB** domyślnie ma `On`wartość.</span><span class="sxs-lookup"><span data-stu-id="4c29f-129">The initial default setting in **VB Defaults** is `On`.</span></span>  
  
#### <a name="to-set-option-explicit-on-the-command-line"></a><span data-ttu-id="4c29f-130">Aby ustawić opcję jawną w wierszu polecenia</span><span class="sxs-lookup"><span data-stu-id="4c29f-130">To set Option Explicit on the command line</span></span>  
  
- <span data-ttu-id="4c29f-131">Dołącz opcję kompilatora [/optionexplicit —](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) do polecenia **VBC** .</span><span class="sxs-lookup"><span data-stu-id="4c29f-131">Include the [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c29f-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="4c29f-132">Example</span></span>  
 <span data-ttu-id="4c29f-133">Poniższy przykład używa instrukcji, `Option Explicit` aby wymusić jawną deklarację wszystkich zmiennych.</span><span class="sxs-lookup"><span data-stu-id="4c29f-133">The following example uses the `Option Explicit` statement to force explicit declaration of all variables.</span></span> <span data-ttu-id="4c29f-134">Próba użycia niezadeklarowanej zmiennej powoduje błąd w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="4c29f-134">Attempting to use an undeclared variable causes an error at compile time.</span></span>  
  
 [!code-vb[VbVbalrStatements#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#47)]  
  
 [!code-vb[VbVbalrStatements#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#48)]  
  
## <a name="see-also"></a><span data-ttu-id="4c29f-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4c29f-135">See also</span></span>

- [<span data-ttu-id="4c29f-136">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="4c29f-136">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="4c29f-137">ReDim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="4c29f-137">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)
- [<span data-ttu-id="4c29f-138">Option Compare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="4c29f-138">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [<span data-ttu-id="4c29f-139">Option Strict, instrukcja</span><span class="sxs-lookup"><span data-stu-id="4c29f-139">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="4c29f-140">/optioncompare</span><span class="sxs-lookup"><span data-stu-id="4c29f-140">/optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="4c29f-141">/optionexplicit</span><span class="sxs-lookup"><span data-stu-id="4c29f-141">/optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [<span data-ttu-id="4c29f-142">/optionstrict</span><span class="sxs-lookup"><span data-stu-id="4c29f-142">/optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [<span data-ttu-id="4c29f-143">Domyślne ustawienia programu Visual Basic, Projekty, Opcje — okno dialogowe</span><span class="sxs-lookup"><span data-stu-id="4c29f-143">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
