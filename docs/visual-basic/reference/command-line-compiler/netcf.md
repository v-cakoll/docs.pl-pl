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
ms.openlocfilehash: 028fa148d0e5622648a5fdfff1789c3d0bfde057
ms.sourcegitcommit: 4c41ec195caf03d98b7900007c3c8e24eba20d34
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/20/2019
ms.locfileid: "67268280"
---
# <a name="-netcf"></a><span data-ttu-id="ee470-102">-netcf</span><span class="sxs-lookup"><span data-stu-id="ee470-102">-netcf</span></span>

<span data-ttu-id="ee470-103">Ustawia kompilatora pod kątem platformy .NET Compact Framework.</span><span class="sxs-lookup"><span data-stu-id="ee470-103">Sets the compiler to target the .NET Compact Framework.</span></span>

## <a name="syntax"></a><span data-ttu-id="ee470-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ee470-104">Syntax</span></span>

```
-netcf
```

## <a name="remarks"></a><span data-ttu-id="ee470-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ee470-105">Remarks</span></span>

<span data-ttu-id="ee470-106">`-netcf` Opcji powoduje, że kompilator języka Visual Basic pod kątem platformy .NET Compact Framework, a nie pełny program .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ee470-106">The `-netcf` option causes the Visual Basic compiler to target the .NET Compact Framework rather than the full .NET Framework.</span></span> <span data-ttu-id="ee470-107">Funkcje języka, które są dostępne tylko w pełny program .NET Framework jest wyłączone.</span><span class="sxs-lookup"><span data-stu-id="ee470-107">Language functionality that is present only in the full .NET Framework is disabled.</span></span>

<span data-ttu-id="ee470-108">`-netcf` Opcja jest przeznaczona do użycia z [- sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md).</span><span class="sxs-lookup"><span data-stu-id="ee470-108">The `-netcf` option is designed to be used with [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md).</span></span> <span data-ttu-id="ee470-109">Funkcje języka, wyłączona przez `-netcf` są te same funkcje języka, nie znajduje się w nim docelowych i związanych z `-sdkpath`.</span><span class="sxs-lookup"><span data-stu-id="ee470-109">The language features disabled by `-netcf` are the same language features not present in the files targeted with `-sdkpath`.</span></span>

> [!NOTE]
> <span data-ttu-id="ee470-110">`-netcf` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="ee470-110">The `-netcf` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span> <span data-ttu-id="ee470-111">`-netcf` Ustawiono opcję po załadowaniu projektu urządzenia języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ee470-111">The `-netcf` option is set when a Visual Basic device project is loaded.</span></span>

<span data-ttu-id="ee470-112">`-netcf` Opcji zmienia się następujące funkcje języka:</span><span class="sxs-lookup"><span data-stu-id="ee470-112">The `-netcf` option changes the following language features:</span></span>

- <span data-ttu-id="ee470-113">[Zakończenia \<— słowo kluczowe > instrukcji](../../../visual-basic/language-reference/statements/end-keyword-statement.md) słowo kluczowe, które kończy wykonania programu, jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="ee470-113">The [End \<keyword> Statement](../../../visual-basic/language-reference/statements/end-keyword-statement.md) keyword, which terminates execution of a program, is disabled.</span></span> <span data-ttu-id="ee470-114">Następujący program kompiluje i uruchamia bez `-netcf` , ale nie powiedzie się w czasie kompilacji za pomocą `-netcf`.</span><span class="sxs-lookup"><span data-stu-id="ee470-114">The following program compiles and runs without `-netcf` but fails at compile time with `-netcf`.</span></span>

  [!code-vb[VbVbalrCompiler#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/netcf.vb#34)]

- <span data-ttu-id="ee470-115">Późne powiązania wszystkich formularzach jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="ee470-115">Late binding, in all forms, is disabled.</span></span> <span data-ttu-id="ee470-116">Błędy czasu kompilacji są generowane, gdy zostaną napotkane rozpoznawanym scenariuszy późnego wiązania.</span><span class="sxs-lookup"><span data-stu-id="ee470-116">Compile-time errors are generated when recognized late-binding scenarios are encountered.</span></span> <span data-ttu-id="ee470-117">Następujący program kompiluje i uruchamia bez `-netcf` , ale nie powiedzie się w czasie kompilacji za pomocą `-netcf`.</span><span class="sxs-lookup"><span data-stu-id="ee470-117">The following program compiles and runs without `-netcf` but fails at compile time with `-netcf`.</span></span>

  [!code-vb[VbVbalrCompiler#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#35)]

- <span data-ttu-id="ee470-118">[Automatycznie](../../../visual-basic/language-reference/modifiers/auto.md), [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md), i [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) Modyfikatory są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="ee470-118">The [Auto](../../../visual-basic/language-reference/modifiers/auto.md), [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md), and [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) modifiers are disabled.</span></span> <span data-ttu-id="ee470-119">Składnia [instrukcji Declare](../../../visual-basic/language-reference/statements/declare-statement.md) instrukcji został też zmodyfikowany do `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`.</span><span class="sxs-lookup"><span data-stu-id="ee470-119">The syntax of the [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) statement is also modified to `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`.</span></span> <span data-ttu-id="ee470-120">Poniższy kod ilustruje efekt `-netcf` podczas kompilacji.</span><span class="sxs-lookup"><span data-stu-id="ee470-120">The following code shows the effect of `-netcf` on a compilation.</span></span>

  [!code-vb[VbVbalrCompiler#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#36)]

- <span data-ttu-id="ee470-121">Przy użyciu słów kluczowych Visual Basic 6.0, które zostały usunięte z Visual Basic generuje inny błąd podczas `-netcf` jest używany.</span><span class="sxs-lookup"><span data-stu-id="ee470-121">Using Visual Basic 6.0 keywords that were removed from Visual Basic generates a different error when `-netcf` is used.</span></span> <span data-ttu-id="ee470-122">Ma to wpływ na komunikaty o błędach dla następujących słów kluczowych:</span><span class="sxs-lookup"><span data-stu-id="ee470-122">This affects the error messages for the following keywords:</span></span>

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

## <a name="example"></a><span data-ttu-id="ee470-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="ee470-123">Example</span></span>

<span data-ttu-id="ee470-124">Poniższy kod kompiluje `Myfile.vb` przy użyciu platformy .NET Compact Framework przy użyciu wersji biblioteki mscorlib.dll i Microsoft.VisualBasic.dll znajduje się w katalogu instalacji domyślnej .NET Compact Framework, na dysku C.</span><span class="sxs-lookup"><span data-stu-id="ee470-124">The following code compiles `Myfile.vb` with the .NET Compact Framework, using the versions of mscorlib.dll and Microsoft.VisualBasic.dll found in the default installation directory of the .NET Compact Framework on the C drive.</span></span> <span data-ttu-id="ee470-125">Zazwyczaj należy użyć najnowszej wersji platformy .NET Compact Framework.</span><span class="sxs-lookup"><span data-stu-id="ee470-125">Typically, you would use the most recent version of the .NET Compact Framework.</span></span>

```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb
```

## <a name="see-also"></a><span data-ttu-id="ee470-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ee470-126">See also</span></span>

- [<span data-ttu-id="ee470-127">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ee470-127">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="ee470-128">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="ee470-128">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="ee470-129">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="ee470-129">-sdkpath</span></span>](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
