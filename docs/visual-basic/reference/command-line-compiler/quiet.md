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
ms.openlocfilehash: 6e773c60469e8426956c92a5aa377741ba5af4d3
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005276"
---
# <a name="-quiet"></a><span data-ttu-id="cffa7-102">-quiet</span><span class="sxs-lookup"><span data-stu-id="cffa7-102">-quiet</span></span>

<span data-ttu-id="cffa7-103">Zapobiega wyświetlaniu przez kompilator kodu dla błędów i ostrzeżeń związanych z składnią.</span><span class="sxs-lookup"><span data-stu-id="cffa7-103">Prevents the compiler from displaying code for syntax-related errors and warnings.</span></span>

## <a name="syntax"></a><span data-ttu-id="cffa7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cffa7-104">Syntax</span></span>

```console
-quiet
```

## <a name="remarks"></a><span data-ttu-id="cffa7-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cffa7-105">Remarks</span></span>

<span data-ttu-id="cffa7-106">Domyślnie `-quiet` nie jest włączona.</span><span class="sxs-lookup"><span data-stu-id="cffa7-106">By default, `-quiet` is not in effect.</span></span> <span data-ttu-id="cffa7-107">Gdy kompilator zgłosi błąd lub ostrzeżenie związane z składnią, wyprowadza również wiersz z kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="cffa7-107">When the compiler reports a syntax-related error or warning, it also outputs the line from source code.</span></span> <span data-ttu-id="cffa7-108">W przypadku aplikacji, które analizują dane wyjściowe kompilatora, może być wygodniejszy, aby kompilator wyprowadził tylko tekst diagnostyki.</span><span class="sxs-lookup"><span data-stu-id="cffa7-108">For applications that parse compiler output, it may be more convenient for the compiler to output only the text of the diagnostic.</span></span>

<span data-ttu-id="cffa7-109">W poniższym przykładzie `Module1` wyświetla błąd, który zawiera kod źródłowy podczas kompilowania bez `-quiet`.</span><span class="sxs-lookup"><span data-stu-id="cffa7-109">In the following example, `Module1` outputs an error that includes source code when compiled without `-quiet`.</span></span>

```vb
Module Module1
    Sub Main()
        x()
    End Sub
End Module
```

<span data-ttu-id="cffa7-110">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="cffa7-110">Output:</span></span>

```console
C:\projects\vb2.vb(3) : error BC30451: 'x' is not declared. It may be inaccessible due to its protection level.

        x()
        ~
```

<span data-ttu-id="cffa7-111">Kompilacja z `-quiet`, kompilator generuje tylko następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="cffa7-111">Compiled with `-quiet`, the compiler outputs only the following:</span></span>

```console
E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.
```

> [!NOTE]
> <span data-ttu-id="cffa7-112">Opcja `-quiet` nie jest dostępna w środowisku deweloperskim programu Visual Studio. jest on dostępny tylko w przypadku kompilowania z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="cffa7-112">The `-quiet` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="cffa7-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="cffa7-113">Example</span></span>

<span data-ttu-id="cffa7-114">Poniższy kod kompiluje `T2.vb` i nie wyświetla kodu dla diagnostyki kompilatora powiązanego z składnią:</span><span class="sxs-lookup"><span data-stu-id="cffa7-114">The following code compiles `T2.vb` and does not display code for syntax-related compiler diagnostics:</span></span>

```console
vbc -quiet t2.vb
```

## <a name="see-also"></a><span data-ttu-id="cffa7-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cffa7-115">See also</span></span>

- [<span data-ttu-id="cffa7-116">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cffa7-116">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="cffa7-117">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="cffa7-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
