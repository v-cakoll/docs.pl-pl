---
title: -optioncompare
ms.date: 07/20/2015
f1_keywords:
- /optioncompare
- -optioncompare
helpviewer_keywords:
- optioncompare compiler option [Visual Basic]
- -optioncompare compiler option [Visual Basic]
- /optioncompare compiler option [Visual Basic]
ms.assetid: 7237b766-b44d-4cc5-9a3c-885348a7d9e4
ms.openlocfilehash: ed9adc7cddd9eb204937b9819e4eeff176821e95
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400564"
---
# <a name="-optioncompare"></a><span data-ttu-id="c52e9-102">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="c52e9-102">-optioncompare</span></span>

<span data-ttu-id="c52e9-103">Określa sposób, w jaki są wykonywane porównania ciągów.</span><span class="sxs-lookup"><span data-stu-id="c52e9-103">Specifies how string comparisons are made.</span></span>

## <a name="syntax"></a><span data-ttu-id="c52e9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c52e9-104">Syntax</span></span>

```console
-optioncompare:{binary | text}
```

## <a name="remarks"></a><span data-ttu-id="c52e9-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c52e9-105">Remarks</span></span>

<span data-ttu-id="c52e9-106">Możesz określić `-optioncompare` jedną z dwóch form: `-optioncompare:binary` , aby użyć porównań ciągów binarnych i `-optioncompare:text` użyć porównania ciągów tekstowych.</span><span class="sxs-lookup"><span data-stu-id="c52e9-106">You can specify `-optioncompare` in one of two forms: `-optioncompare:binary` to use binary string comparisons, and `-optioncompare:text` to use text string comparisons.</span></span> <span data-ttu-id="c52e9-107">Domyślnie kompilator używa programu `-optioncompare:binary` .</span><span class="sxs-lookup"><span data-stu-id="c52e9-107">By default, the compiler uses `-optioncompare:binary`.</span></span>

<span data-ttu-id="c52e9-108">W systemie Microsoft Windows bieżąca strona kodowa Określa binarny porządek sortowania.</span><span class="sxs-lookup"><span data-stu-id="c52e9-108">In Microsoft Windows, the current code page determines the binary sort order.</span></span> <span data-ttu-id="c52e9-109">Typowa binarna kolejność sortowania jest następująca:</span><span class="sxs-lookup"><span data-stu-id="c52e9-109">A typical binary sort order is as follows:</span></span>

`A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`

<span data-ttu-id="c52e9-110">Porównania ciągów tekstowych są oparte na kolejności sortowania tekstu bez uwzględniania wielkości liter, która zależy od ustawień regionalnych systemu.</span><span class="sxs-lookup"><span data-stu-id="c52e9-110">Text-based string comparisons are based on a case-insensitive text sort order determined by your system's locale.</span></span> <span data-ttu-id="c52e9-111">Typowy porządek sortowania tekstu jest następujący:</span><span class="sxs-lookup"><span data-stu-id="c52e9-111">A typical text sort order is as follows:</span></span>

`(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`

### <a name="to-set--optioncompare-in-the-visual-studio-ide"></a><span data-ttu-id="c52e9-112">Aby ustawić-optioncompare w środowisku IDE programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c52e9-112">To set -optioncompare in the Visual Studio IDE</span></span>

1. <span data-ttu-id="c52e9-113">Zaznaczono projekt w **Eksplorator rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="c52e9-113">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="c52e9-114">W menu **projekt** kliknij polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="c52e9-114">On the **Project** menu, click **Properties**.</span></span>

2. <span data-ttu-id="c52e9-115">Kliknij kartę **kompilacja** .</span><span class="sxs-lookup"><span data-stu-id="c52e9-115">Click the **Compile** tab.</span></span>

3. <span data-ttu-id="c52e9-116">Zmodyfikuj wartość w polu **PORÓWNAJ opcję** .</span><span class="sxs-lookup"><span data-stu-id="c52e9-116">Modify the value in the **Option Compare** box.</span></span>

### <a name="to-set--optioncompare-programmatically"></a><span data-ttu-id="c52e9-117">Aby programowo ustawić — optioncompare</span><span class="sxs-lookup"><span data-stu-id="c52e9-117">To set -optioncompare programmatically</span></span>

<span data-ttu-id="c52e9-118">Zobacz [Option Compare instrukcji](../../language-reference/statements/option-compare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="c52e9-118">See [Option Compare Statement](../../language-reference/statements/option-compare-statement.md).</span></span>

## <a name="example"></a><span data-ttu-id="c52e9-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="c52e9-119">Example</span></span>

<span data-ttu-id="c52e9-120">Poniższy kod kompiluje `ProjFile.vb` i używa porównywania ciągów binarnych.</span><span class="sxs-lookup"><span data-stu-id="c52e9-120">The following code compiles `ProjFile.vb` and uses binary string comparisons.</span></span>

```console
vbc -optioncompare:binary projFile.vb
```

## <a name="see-also"></a><span data-ttu-id="c52e9-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c52e9-121">See also</span></span>

- [<span data-ttu-id="c52e9-122">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c52e9-122">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="c52e9-123">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="c52e9-123">-optionexplicit</span></span>](optionexplicit.md)
- [<span data-ttu-id="c52e9-124">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="c52e9-124">-optionstrict</span></span>](optionstrict.md)
- [<span data-ttu-id="c52e9-125">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="c52e9-125">-optioninfer</span></span>](optioninfer.md)
- [<span data-ttu-id="c52e9-126">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="c52e9-126">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="c52e9-127">Option Compare — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="c52e9-127">Option Compare Statement</span></span>](../../language-reference/statements/option-compare-statement.md)
- [<span data-ttu-id="c52e9-128">Domyślne ustawienia programu Visual Basic, Projekty, Opcje — okno dialogowe</span><span class="sxs-lookup"><span data-stu-id="c52e9-128">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
