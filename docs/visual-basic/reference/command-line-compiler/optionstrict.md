---
title: -optionstrict
ms.date: 07/20/2015
f1_keywords:
- -optionstrict
helpviewer_keywords:
- -optionstrict compiler option [Visual Basic]
- optionstrict compiler option [Visual Basic]
- /optionstrict compiler option [Visual Basic]
ms.assetid: c7b10086-0fa4-49db-b3c8-4ae0db5957da
ms.openlocfilehash: 469e22aef9d746fc55e04ba884d17d60d8baa85a
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583074"
---
# <a name="-optionstrict"></a><span data-ttu-id="58ca3-102">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="58ca3-102">-optionstrict</span></span>

<span data-ttu-id="58ca3-103">Wymusza ścisłą semantykę typu w celu ograniczenia niejawnych konwersji typów.</span><span class="sxs-lookup"><span data-stu-id="58ca3-103">Enforces strict type semantics to restrict implicit type conversions.</span></span>

## <a name="syntax"></a><span data-ttu-id="58ca3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="58ca3-104">Syntax</span></span>

```console
-optionstrict[+ | -]
-optionstrict[:custom]
```

## <a name="arguments"></a><span data-ttu-id="58ca3-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="58ca3-105">Arguments</span></span>

<span data-ttu-id="58ca3-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="58ca3-106">`+` &#124; `-`</span></span>  
<span data-ttu-id="58ca3-107">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="58ca3-107">Optional.</span></span> <span data-ttu-id="58ca3-108">Opcja `-optionstrict+` ogranicza niejawną konwersję typu.</span><span class="sxs-lookup"><span data-stu-id="58ca3-108">The `-optionstrict+` option restricts implicit type conversion.</span></span> <span data-ttu-id="58ca3-109">Wartość domyślna dla tej opcji to `-optionstrict-`.</span><span class="sxs-lookup"><span data-stu-id="58ca3-109">The default for this option is `-optionstrict-`.</span></span> <span data-ttu-id="58ca3-110">Opcja `-optionstrict+` jest taka sama jak `-optionstrict`.</span><span class="sxs-lookup"><span data-stu-id="58ca3-110">The `-optionstrict+` option is the same as `-optionstrict`.</span></span> <span data-ttu-id="58ca3-111">Można użyć obu typów jako nieograniczającej semantyki typu.</span><span class="sxs-lookup"><span data-stu-id="58ca3-111">You can use both for permissive type semantics.</span></span>

`custom`  
<span data-ttu-id="58ca3-112">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="58ca3-112">Required.</span></span> <span data-ttu-id="58ca3-113">Ostrzegaj w przypadku nieprzestrzegania ścisłej semantyki języka.</span><span class="sxs-lookup"><span data-stu-id="58ca3-113">Warn when strict language semantics are not respected.</span></span>

## <a name="remarks"></a><span data-ttu-id="58ca3-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="58ca3-114">Remarks</span></span>

<span data-ttu-id="58ca3-115">Gdy `-optionstrict+`, tylko rozszerzone konwersje typów mogą być wykonywane niejawnie.</span><span class="sxs-lookup"><span data-stu-id="58ca3-115">When `-optionstrict+` is in effect, only widening type conversions can be made implicitly.</span></span> <span data-ttu-id="58ca3-116">Niejawne konwersje typów, takie jak przypisanie obiektu typu `Decimal` do obiektu typu Integer, są raportowane jako błędy.</span><span class="sxs-lookup"><span data-stu-id="58ca3-116">Implicit narrowing type conversions, such as assigning a `Decimal` type object to an integer type object, are reported as errors.</span></span>

<span data-ttu-id="58ca3-117">Aby wygenerować ostrzeżenia dla niejawnych konwersji typów zawężających, użyj `-optionstrict:custom`.</span><span class="sxs-lookup"><span data-stu-id="58ca3-117">To generate warnings for implicit narrowing type conversions, use `-optionstrict:custom`.</span></span> <span data-ttu-id="58ca3-118">Użyj `-nowarn:numberlist` do ignorowania określonych ostrzeżeń i `-warnaserror:numberlist` do traktowania określonych ostrzeżeń jako błędów.</span><span class="sxs-lookup"><span data-stu-id="58ca3-118">Use `-nowarn:numberlist` to ignore particular warnings and `-warnaserror:numberlist` to treat particular warnings as errors.</span></span>

### <a name="to-set--optionstrict-in-the-visual-studio-ide"></a><span data-ttu-id="58ca3-119">Aby ustawić-optionstrict w środowisku IDE programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="58ca3-119">To set -optionstrict in the Visual Studio IDE</span></span>

1. <span data-ttu-id="58ca3-120">Zaznaczono projekt w **Eksplorator rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="58ca3-120">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="58ca3-121">W menu **projekt** kliknij polecenie **właściwości.**</span><span class="sxs-lookup"><span data-stu-id="58ca3-121">On the **Project** menu, click **Properties.**</span></span>

2. <span data-ttu-id="58ca3-122">Kliknij kartę **kompilacja** .</span><span class="sxs-lookup"><span data-stu-id="58ca3-122">Click the **Compile** tab.</span></span>

3. <span data-ttu-id="58ca3-123">Zmodyfikuj wartość w polu **Option Strict** .</span><span class="sxs-lookup"><span data-stu-id="58ca3-123">Modify the value in the **Option Strict** box.</span></span>

### <a name="to-set--optionstrict-programmatically"></a><span data-ttu-id="58ca3-124">Aby programowo ustawić — optionstrict</span><span class="sxs-lookup"><span data-stu-id="58ca3-124">To set -optionstrict programmatically</span></span>

<span data-ttu-id="58ca3-125">Zobacz [Option Strict, instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="58ca3-125">See [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>

## <a name="example"></a><span data-ttu-id="58ca3-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="58ca3-126">Example</span></span>

<span data-ttu-id="58ca3-127">Poniższy kod kompiluje `Test.vb` przy użyciu semantyki typu Strict.</span><span class="sxs-lookup"><span data-stu-id="58ca3-127">The following code compiles `Test.vb` using strict type semantics.</span></span>

```console
vbc -optionstrict+ test.vb
```

## <a name="see-also"></a><span data-ttu-id="58ca3-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="58ca3-128">See also</span></span>

- [<span data-ttu-id="58ca3-129">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="58ca3-129">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="58ca3-130">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="58ca3-130">-optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="58ca3-131">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="58ca3-131">-optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [<span data-ttu-id="58ca3-132">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="58ca3-132">-optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="58ca3-133">-nowarn</span><span class="sxs-lookup"><span data-stu-id="58ca3-133">-nowarn</span></span>](../../../visual-basic/reference/command-line-compiler/nowarn.md)
- [<span data-ttu-id="58ca3-134">-warnaserror — (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="58ca3-134">-warnaserror (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/warnaserror.md)
- [<span data-ttu-id="58ca3-135">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="58ca3-135">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="58ca3-136">Option Strict, instrukcja</span><span class="sxs-lookup"><span data-stu-id="58ca3-136">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="58ca3-137">Domyślne ustawienia programu Visual Basic, Projekty, Opcje — okno dialogowe</span><span class="sxs-lookup"><span data-stu-id="58ca3-137">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
