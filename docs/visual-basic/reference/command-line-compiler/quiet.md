---
title: -quiet
ms.date: 07/20/2015
f1_keywords:
- -quiet
- quiet
helpviewer_keywords:
- -quiet compiler option [Visual Basic]
- /quiet compiler option [Visual Basic]
- quiet compiler option [Visual Basic]
ms.assetid: 5d77fa23-4c50-4708-8535-649912b098e8
ms.openlocfilehash: a22773e2e37eb60ab6f1e88305266f41764311e7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788849"
---
# <a name="-quiet"></a><span data-ttu-id="ae047-102">-quiet</span><span class="sxs-lookup"><span data-stu-id="ae047-102">-quiet</span></span>

<span data-ttu-id="ae047-103">Kompilator uniemożliwia wyświetlanie kodu dotyczące składni błędów i ostrzeżeń.</span><span class="sxs-lookup"><span data-stu-id="ae047-103">Prevents the compiler from displaying code for syntax-related errors and warnings.</span></span>

## <a name="syntax"></a><span data-ttu-id="ae047-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ae047-104">Syntax</span></span>

```
-quiet
```

## <a name="remarks"></a><span data-ttu-id="ae047-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ae047-105">Remarks</span></span>

<span data-ttu-id="ae047-106">Domyślnie `-quiet` nie jest włączone.</span><span class="sxs-lookup"><span data-stu-id="ae047-106">By default, `-quiet` is not in effect.</span></span> <span data-ttu-id="ae047-107">Gdy kompilator zgłosi błąd związany z składni lub ostrzeżenie, również generuje wiersza z kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="ae047-107">When the compiler reports a syntax-related error or warning, it also outputs the line from source code.</span></span> <span data-ttu-id="ae047-108">W przypadku aplikacji, które przeanalizować dane wyjściowe kompilatora może być bardziej wygodne do kompilatora w danych wyjściowych tylko tekst diagnostyki.</span><span class="sxs-lookup"><span data-stu-id="ae047-108">For applications that parse compiler output, it may be more convenient for the compiler to output only the text of the diagnostic.</span></span>

<span data-ttu-id="ae047-109">W poniższym przykładzie `Module1` generuje błąd, który zawiera kod źródłowy, gdy kompilowany bez `-quiet`.</span><span class="sxs-lookup"><span data-stu-id="ae047-109">In the following example, `Module1` outputs an error that includes source code when compiled without `-quiet`.</span></span>

```vb
Module Module1
    Sub Main()
        x()
    End Sub
End Module
```

<span data-ttu-id="ae047-110">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="ae047-110">Output:</span></span>

```console
C:\projects\vb2.vb(3) : error BC30451: 'x' is not declared. It may be inaccessible due to its protection level.

        x()
        ~
```

<span data-ttu-id="ae047-111">Skompilowany przy użyciu `-quiet`, kompilator generuje jedynie następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="ae047-111">Compiled with `-quiet`, the compiler outputs only the following:</span></span>

```
E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.
```

> [!NOTE]
> <span data-ttu-id="ae047-112">`-quiet` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="ae047-112">The `-quiet` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="ae047-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="ae047-113">Example</span></span>

<span data-ttu-id="ae047-114">Poniższy kod kompiluje `T2.vb` i nie zawiera kod dla diagnostyki kompilatora dotyczące składni:</span><span class="sxs-lookup"><span data-stu-id="ae047-114">The following code compiles `T2.vb` and does not display code for syntax-related compiler diagnostics:</span></span>

```
vbc -quiet t2.vb
```

## <a name="see-also"></a><span data-ttu-id="ae047-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ae047-115">See also</span></span>

- [<span data-ttu-id="ae047-116">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ae047-116">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="ae047-117">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="ae047-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
