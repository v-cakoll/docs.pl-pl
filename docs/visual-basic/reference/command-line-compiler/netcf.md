---
title: -netcf
ms.date: 03/13/2018
f1_keywords:
- /netcf
- -netcf
helpviewer_keywords:
- -netcf compiler option [Visual Basic]
- netcf compiler option [Visual Basic]
- /netcf compiler option [Visual Basic]
ms.assetid: db7cfa59-c315-401c-a59b-0daf355343d6
ms.openlocfilehash: 7f14ce07a2928f4dbffd3aa57f8cdd514b75694c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716714"
---
# <a name="-netcf"></a><span data-ttu-id="e6e11-102">-netcf</span><span class="sxs-lookup"><span data-stu-id="e6e11-102">-netcf</span></span>

<span data-ttu-id="e6e11-103">Ustawia kompilator jako docelowy .NET Compact Framework.</span><span class="sxs-lookup"><span data-stu-id="e6e11-103">Sets the compiler to target the .NET Compact Framework.</span></span>

## <a name="syntax"></a><span data-ttu-id="e6e11-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e6e11-104">Syntax</span></span>

```console
-netcf
```

## <a name="remarks"></a><span data-ttu-id="e6e11-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e6e11-105">Remarks</span></span>

<span data-ttu-id="e6e11-106">Opcja `-netcf` powoduje, że kompilator Visual Basic ma kierować .NET Compact Framework, a nie pełną .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e6e11-106">The `-netcf` option causes the Visual Basic compiler to target the .NET Compact Framework rather than the full .NET Framework.</span></span> <span data-ttu-id="e6e11-107">Funkcja języka, która jest obecna tylko w pełnej .NET Framework jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="e6e11-107">Language functionality that is present only in the full .NET Framework is disabled.</span></span>

<span data-ttu-id="e6e11-108">Opcja `-netcf` jest przeznaczona do użycia z opcją [-SdkPath](../../../visual-basic/reference/command-line-compiler/sdkpath.md).</span><span class="sxs-lookup"><span data-stu-id="e6e11-108">The `-netcf` option is designed to be used with [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md).</span></span> <span data-ttu-id="e6e11-109">Funkcje języka wyłączone przez `-netcf` są tymi samymi funkcjami językowymi, które nie są obecne w plikach przeznaczonych dla `-sdkpath`.</span><span class="sxs-lookup"><span data-stu-id="e6e11-109">The language features disabled by `-netcf` are the same language features not present in the files targeted with `-sdkpath`.</span></span>

> [!NOTE]
> <span data-ttu-id="e6e11-110">Opcja `-netcf` nie jest dostępna w środowisku deweloperskim programu Visual Studio; jest on dostępny tylko w przypadku kompilowania z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="e6e11-110">The `-netcf` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span> <span data-ttu-id="e6e11-111">Opcja `-netcf` jest ustawiana podczas ładowania projektu urządzenia Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e6e11-111">The `-netcf` option is set when a Visual Basic device project is loaded.</span></span>

<span data-ttu-id="e6e11-112">Opcja `-netcf` zmienia następujące funkcje języka:</span><span class="sxs-lookup"><span data-stu-id="e6e11-112">The `-netcf` option changes the following language features:</span></span>

- <span data-ttu-id="e6e11-113">Słowo kluczowe [End \<słowo kluczowe > instrukcji](../../../visual-basic/language-reference/statements/end-keyword-statement.md) , które kończy wykonywanie programu, jest wyłączone.</span><span class="sxs-lookup"><span data-stu-id="e6e11-113">The [End \<keyword> Statement](../../../visual-basic/language-reference/statements/end-keyword-statement.md) keyword, which terminates execution of a program, is disabled.</span></span> <span data-ttu-id="e6e11-114">Następujący program kompiluje i uruchamia się bez `-netcf`, ale kończy się niepowodzeniem w czasie kompilacji z `-netcf`.</span><span class="sxs-lookup"><span data-stu-id="e6e11-114">The following program compiles and runs without `-netcf` but fails at compile time with `-netcf`.</span></span>

  [!code-vb[VbVbalrCompiler#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/netcf.vb#34)]

- <span data-ttu-id="e6e11-115">Późne wiązanie w obszarze wszystkie formularze jest wyłączone.</span><span class="sxs-lookup"><span data-stu-id="e6e11-115">Late binding, in all forms, is disabled.</span></span> <span data-ttu-id="e6e11-116">Błędy czasu kompilacji są generowane po napotkaniu rozpoznanych scenariuszy późnego wiązania.</span><span class="sxs-lookup"><span data-stu-id="e6e11-116">Compile-time errors are generated when recognized late-binding scenarios are encountered.</span></span> <span data-ttu-id="e6e11-117">Następujący program kompiluje i uruchamia się bez `-netcf`, ale kończy się niepowodzeniem w czasie kompilacji z `-netcf`.</span><span class="sxs-lookup"><span data-stu-id="e6e11-117">The following program compiles and runs without `-netcf` but fails at compile time with `-netcf`.</span></span>

  [!code-vb[VbVbalrCompiler#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#35)]

- <span data-ttu-id="e6e11-118">Modyfikatory [Auto,](../../../visual-basic/language-reference/modifiers/auto.md) [ANSI](../../../visual-basic/language-reference/modifiers/ansi.md)i [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="e6e11-118">The [Auto](../../../visual-basic/language-reference/modifiers/auto.md), [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md), and [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) modifiers are disabled.</span></span> <span data-ttu-id="e6e11-119">Składnia [instrukcji DECLARE](../../../visual-basic/language-reference/statements/declare-statement.md) jest również modyfikowana do `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`.</span><span class="sxs-lookup"><span data-stu-id="e6e11-119">The syntax of the [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) is also modified to `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`.</span></span> <span data-ttu-id="e6e11-120">Poniższy kod ilustruje wpływ `-netcf` na kompilację.</span><span class="sxs-lookup"><span data-stu-id="e6e11-120">The following code shows the effect of `-netcf` on a compilation.</span></span>

  [!code-vb[VbVbalrCompiler#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#36)]

- <span data-ttu-id="e6e11-121">Używanie Visual Basic 6,0 słów kluczowych, które zostały usunięte z Visual Basic generuje inny błąd, gdy `-netcf` jest używany.</span><span class="sxs-lookup"><span data-stu-id="e6e11-121">Using Visual Basic 6.0 keywords that were removed from Visual Basic generates a different error when `-netcf` is used.</span></span> <span data-ttu-id="e6e11-122">Ma to wpływ na komunikaty o błędach dla następujących słów kluczowych:</span><span class="sxs-lookup"><span data-stu-id="e6e11-122">This affects the error messages for the following keywords:</span></span>

  - `Open`

  - `Close`

  - `Put`

  - `Print`

  - `Write`

  - `Input`

  - `Lock`

  - `Unlock`

  - `Seek`

  - `Width`

  - `Name`

  - `FreeFile`

  - `EOF`

  - `Loc`

  - `LOF`

  - `Line`

## <a name="example"></a><span data-ttu-id="e6e11-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="e6e11-123">Example</span></span>

<span data-ttu-id="e6e11-124">Poniższy kod kompiluje `Myfile.vb` z .NET Compact Framework przy użyciu wersji plików mscorlib. dll i Microsoft. VisualBasic. dll znajdujących się w domyślnym katalogu instalacyjnym .NET Compact Framework na dysku C.</span><span class="sxs-lookup"><span data-stu-id="e6e11-124">The following code compiles `Myfile.vb` with the .NET Compact Framework, using the versions of mscorlib.dll and Microsoft.VisualBasic.dll found in the default installation directory of the .NET Compact Framework on the C drive.</span></span> <span data-ttu-id="e6e11-125">Zazwyczaj należy użyć najnowszej wersji .NET Compact Framework.</span><span class="sxs-lookup"><span data-stu-id="e6e11-125">Typically, you would use the most recent version of the .NET Compact Framework.</span></span>

```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb
```

## <a name="see-also"></a><span data-ttu-id="e6e11-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e6e11-126">See also</span></span>

- [<span data-ttu-id="e6e11-127">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e6e11-127">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="e6e11-128">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="e6e11-128">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="e6e11-129">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="e6e11-129">-sdkpath</span></span>](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
