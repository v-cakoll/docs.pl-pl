---
title: -verbose
ms.date: 03/13/2018
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
ms.openlocfilehash: e70496b552ced8e07cbe3cde34cda377d94da9f4
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188420"
---
# <a name="-verbose"></a><span data-ttu-id="c58ef-102">-verbose</span><span class="sxs-lookup"><span data-stu-id="c58ef-102">-verbose</span></span>
<span data-ttu-id="c58ef-103">Powoduje, że kompilator generuje pełny stan i komunikaty o błędach.</span><span class="sxs-lookup"><span data-stu-id="c58ef-103">Causes the compiler to produce verbose status and error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c58ef-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c58ef-104">Syntax</span></span>  
  
```  
-verbose[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="c58ef-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="c58ef-105">Arguments</span></span>  
 <span data-ttu-id="c58ef-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="c58ef-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="c58ef-107">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="c58ef-107">Optional.</span></span> <span data-ttu-id="c58ef-108">Określanie `-verbose` jest taka sama jak określanie `-verbose+`, co powoduje, że kompilator będzie pełne komunikaty wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="c58ef-108">Specifying `-verbose` is the same as specifying `-verbose+`, which causes the compiler to emit verbose messages.</span></span> <span data-ttu-id="c58ef-109">Wartość domyślna tej opcji to `-verbose-`.</span><span class="sxs-lookup"><span data-stu-id="c58ef-109">The default for this option is `-verbose-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c58ef-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c58ef-110">Remarks</span></span>  
 <span data-ttu-id="c58ef-111">`-verbose` Opcji wyświetla informacje o całkowitą liczbę wszystkich błędów, które wystawiony przez kompilator, raporty, zestawy, które są ładowane przez moduł i wyświetla pliki, które są aktualnie kompilowana.</span><span class="sxs-lookup"><span data-stu-id="c58ef-111">The `-verbose` option displays information about the total number of errors issued by the compiler, reports which assemblies are being loaded by a module, and displays which files are currently being compiled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c58ef-112">`-verbose` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="c58ef-112">The `-verbose` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c58ef-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="c58ef-113">Example</span></span>  
 <span data-ttu-id="c58ef-114">Poniższy kod kompiluje `In.vb` i instruuje kompilator, aby wyświetlić informacje o stanie pełne.</span><span class="sxs-lookup"><span data-stu-id="c58ef-114">The following code compiles `In.vb` and directs the compiler to display verbose status information.</span></span>  
  
```console  
vbc -verbose in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="c58ef-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c58ef-115">See Also</span></span>  
 [<span data-ttu-id="c58ef-116">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c58ef-116">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="c58ef-117">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="c58ef-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
