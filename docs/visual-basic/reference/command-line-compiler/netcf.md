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
ms.openlocfilehash: b64c55b73a9c835ded0d7c81ff36329b8d6a8bc9
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586539"
---
# <a name="-netcf"></a><span data-ttu-id="15039-102">-netcf</span><span class="sxs-lookup"><span data-stu-id="15039-102">-netcf</span></span>

<span data-ttu-id="15039-103">Ustawia kompilatora z docelowym [!INCLUDE[Compact](~/includes/compact-md.md)].</span><span class="sxs-lookup"><span data-stu-id="15039-103">Sets the compiler to target the [!INCLUDE[Compact](~/includes/compact-md.md)].</span></span>

## <a name="syntax"></a><span data-ttu-id="15039-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="15039-104">Syntax</span></span>

```
-netcf
```

## <a name="remarks"></a><span data-ttu-id="15039-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="15039-105">Remarks</span></span>

<span data-ttu-id="15039-106">`-netcf` Opcji powoduje, że kompilator języka Visual Basic do obiektu docelowego [!INCLUDE[Compact](~/includes/compact-md.md)] zamiast pełny program .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="15039-106">The `-netcf` option causes the Visual Basic compiler to target the [!INCLUDE[Compact](~/includes/compact-md.md)] rather than the full .NET Framework.</span></span> <span data-ttu-id="15039-107">Funkcje języka, które są dostępne tylko w pełny program .NET Framework jest wyłączone.</span><span class="sxs-lookup"><span data-stu-id="15039-107">Language functionality that is present only in the full .NET Framework is disabled.</span></span>

<span data-ttu-id="15039-108">`-netcf` Opcja jest przeznaczona do użycia z [- sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md).</span><span class="sxs-lookup"><span data-stu-id="15039-108">The `-netcf` option is designed to be used with [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md).</span></span> <span data-ttu-id="15039-109">Funkcje języka, wyłączona przez `-netcf` są te same funkcje języka, nie znajduje się w nim docelowych i związanych z `-sdkpath`.</span><span class="sxs-lookup"><span data-stu-id="15039-109">The language features disabled by `-netcf` are the same language features not present in the files targeted with `-sdkpath`.</span></span>

> [!NOTE]
> <span data-ttu-id="15039-110">`-netcf` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="15039-110">The `-netcf` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span> <span data-ttu-id="15039-111">`-netcf` Ustawiono opcję po załadowaniu projektu urządzenia języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="15039-111">The `-netcf` option is set when a Visual Basic device project is loaded.</span></span>

<span data-ttu-id="15039-112">`-netcf` Opcji zmienia się następujące funkcje języka:</span><span class="sxs-lookup"><span data-stu-id="15039-112">The `-netcf` option changes the following language features:</span></span>

- <span data-ttu-id="15039-113">[Zakończenia \<— słowo kluczowe > instrukcji](../../../visual-basic/language-reference/statements/end-keyword-statement.md) słowo kluczowe, które kończy wykonania programu, jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="15039-113">The [End \<keyword> Statement](../../../visual-basic/language-reference/statements/end-keyword-statement.md) keyword, which terminates execution of a program, is disabled.</span></span> <span data-ttu-id="15039-114">Następujący program kompiluje i uruchamia bez `-netcf` , ale nie powiedzie się w czasie kompilacji za pomocą `-netcf`.</span><span class="sxs-lookup"><span data-stu-id="15039-114">The following program compiles and runs without `-netcf` but fails at compile time with `-netcf`.</span></span>

  [!code-vb[VbVbalrCompiler#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/netcf.vb#34)]

- <span data-ttu-id="15039-115">Późne powiązania wszystkich formularzach jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="15039-115">Late binding, in all forms, is disabled.</span></span> <span data-ttu-id="15039-116">Błędy czasu kompilacji są generowane, gdy zostaną napotkane rozpoznawanym scenariuszy późnego wiązania.</span><span class="sxs-lookup"><span data-stu-id="15039-116">Compile-time errors are generated when recognized late-binding scenarios are encountered.</span></span> <span data-ttu-id="15039-117">Następujący program kompiluje i uruchamia bez `-netcf` , ale nie powiedzie się w czasie kompilacji za pomocą `-netcf`.</span><span class="sxs-lookup"><span data-stu-id="15039-117">The following program compiles and runs without `-netcf` but fails at compile time with `-netcf`.</span></span>

  [!code-vb[VbVbalrCompiler#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#35)]

- <span data-ttu-id="15039-118">[Automatycznie](../../../visual-basic/language-reference/modifiers/auto.md), [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md), i [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) Modyfikatory są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="15039-118">The [Auto](../../../visual-basic/language-reference/modifiers/auto.md), [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md), and [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) modifiers are disabled.</span></span> <span data-ttu-id="15039-119">Składnia [instrukcji Declare](../../../visual-basic/language-reference/statements/declare-statement.md) instrukcji został też zmodyfikowany do `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`.</span><span class="sxs-lookup"><span data-stu-id="15039-119">The syntax of the [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) statement is also modified to `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`.</span></span> <span data-ttu-id="15039-120">Poniższy kod ilustruje efekt `-netcf` podczas kompilacji.</span><span class="sxs-lookup"><span data-stu-id="15039-120">The following code shows the effect of `-netcf` on a compilation.</span></span>

  [!code-vb[VbVbalrCompiler#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#36)]

- <span data-ttu-id="15039-121">Przy użyciu słów kluczowych Visual Basic 6.0, które zostały usunięte z Visual Basic generuje inny błąd podczas `-netcf` jest używany.</span><span class="sxs-lookup"><span data-stu-id="15039-121">Using Visual Basic 6.0 keywords that were removed from Visual Basic generates a different error when `-netcf` is used.</span></span> <span data-ttu-id="15039-122">Ma to wpływ na komunikaty o błędach dla następujących słów kluczowych:</span><span class="sxs-lookup"><span data-stu-id="15039-122">This affects the error messages for the following keywords:</span></span>

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

## <a name="example"></a><span data-ttu-id="15039-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="15039-123">Example</span></span>

<span data-ttu-id="15039-124">Poniższy kod kompiluje `Myfile.vb` z [!INCLUDE[Compact](~/includes/compact-md.md)], przy użyciu wersji biblioteki mscorlib.dll i Microsoft.VisualBasic.dll znajduje się w katalogu instalacji domyślnej z [!INCLUDE[Compact](~/includes/compact-md.md)] na dysku C.</span><span class="sxs-lookup"><span data-stu-id="15039-124">The following code compiles `Myfile.vb` with the [!INCLUDE[Compact](~/includes/compact-md.md)], using the versions of mscorlib.dll and Microsoft.VisualBasic.dll found in the default installation directory of the [!INCLUDE[Compact](~/includes/compact-md.md)] on the C drive.</span></span> <span data-ttu-id="15039-125">Zazwyczaj używasz najnowszej wersji [!INCLUDE[Compact](~/includes/compact-md.md)].</span><span class="sxs-lookup"><span data-stu-id="15039-125">Typically, you would use the most recent version of the [!INCLUDE[Compact](~/includes/compact-md.md)].</span></span>

```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb
```

## <a name="see-also"></a><span data-ttu-id="15039-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="15039-126">See also</span></span>

- [<span data-ttu-id="15039-127">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="15039-127">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="15039-128">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="15039-128">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="15039-129">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="15039-129">-sdkpath</span></span>](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
