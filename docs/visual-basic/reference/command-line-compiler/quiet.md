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
ms.openlocfilehash: f894ed6a778e026ffd3976a63fe3b677eb6a9557
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400529"
---
# <a name="-quiet"></a><span data-ttu-id="acb67-102">-quiet</span><span class="sxs-lookup"><span data-stu-id="acb67-102">-quiet</span></span>

<span data-ttu-id="acb67-103">Zapobiega wyświetlaniu przez kompilator kodu dla błędów i ostrzeżeń związanych z składnią.</span><span class="sxs-lookup"><span data-stu-id="acb67-103">Prevents the compiler from displaying code for syntax-related errors and warnings.</span></span>

## <a name="syntax"></a><span data-ttu-id="acb67-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="acb67-104">Syntax</span></span>

```console
-quiet
```

## <a name="remarks"></a><span data-ttu-id="acb67-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="acb67-105">Remarks</span></span>

<span data-ttu-id="acb67-106">Domyślnie program `-quiet` nie działa.</span><span class="sxs-lookup"><span data-stu-id="acb67-106">By default, `-quiet` is not in effect.</span></span> <span data-ttu-id="acb67-107">Gdy kompilator zgłosi błąd lub ostrzeżenie związane z składnią, wyprowadza również wiersz z kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="acb67-107">When the compiler reports a syntax-related error or warning, it also outputs the line from source code.</span></span> <span data-ttu-id="acb67-108">W przypadku aplikacji, które analizują dane wyjściowe kompilatora, może być wygodniejszy, aby kompilator wyprowadził tylko tekst diagnostyki.</span><span class="sxs-lookup"><span data-stu-id="acb67-108">For applications that parse compiler output, it may be more convenient for the compiler to output only the text of the diagnostic.</span></span>

<span data-ttu-id="acb67-109">W poniższym przykładzie `Module1` generuje błąd, który zawiera kod źródłowy, gdy jest kompilowany bez `-quiet` .</span><span class="sxs-lookup"><span data-stu-id="acb67-109">In the following example, `Module1` outputs an error that includes source code when compiled without `-quiet`.</span></span>

```vb
Module Module1
    Sub Main()
        x()
    End Sub
End Module
```

<span data-ttu-id="acb67-110">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="acb67-110">Output:</span></span>

```console
C:\projects\vb2.vb(3) : error BC30451: 'x' is not declared. It may be inaccessible due to its protection level.

        x()
        ~
```

<span data-ttu-id="acb67-111">Skompilowany przy użyciu `-quiet` , kompilator wyprowadza tylko następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="acb67-111">Compiled with `-quiet`, the compiler outputs only the following:</span></span>

```console
E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.
```

> [!NOTE]
> <span data-ttu-id="acb67-112">`-quiet`Opcja jest niedostępna w środowisku deweloperskim programu Visual Studio. jest ona dostępna tylko podczas kompilowania z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="acb67-112">The `-quiet` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="acb67-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="acb67-113">Example</span></span>

<span data-ttu-id="acb67-114">Poniższy kod kompiluje `T2.vb` i nie wyświetla kodu dla diagnostyki kompilatora powiązanego z składnią:</span><span class="sxs-lookup"><span data-stu-id="acb67-114">The following code compiles `T2.vb` and does not display code for syntax-related compiler diagnostics:</span></span>

```console
vbc -quiet t2.vb
```

## <a name="see-also"></a><span data-ttu-id="acb67-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="acb67-115">See also</span></span>

- [<span data-ttu-id="acb67-116">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="acb67-116">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="acb67-117">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="acb67-117">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
