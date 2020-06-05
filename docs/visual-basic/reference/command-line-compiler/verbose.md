---
title: -verbose
ms.date: 03/13/2018
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
ms.openlocfilehash: 405b557568a736de3ddc3b51e265261222613131
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403034"
---
# <a name="-verbose"></a><span data-ttu-id="09763-102">-verbose</span><span class="sxs-lookup"><span data-stu-id="09763-102">-verbose</span></span>
<span data-ttu-id="09763-103">Powoduje, że kompilator tworzy pełny stan i komunikaty o błędach.</span><span class="sxs-lookup"><span data-stu-id="09763-103">Causes the compiler to produce verbose status and error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09763-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="09763-104">Syntax</span></span>  
  
```console  
-verbose[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="09763-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="09763-105">Arguments</span></span>  
 <span data-ttu-id="09763-106">`+`&#124;`-`</span><span class="sxs-lookup"><span data-stu-id="09763-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="09763-107">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="09763-107">Optional.</span></span> <span data-ttu-id="09763-108">Określanie `-verbose` jest takie samo jak określanie `-verbose+` , co powoduje, że kompilator emituje pełne komunikaty.</span><span class="sxs-lookup"><span data-stu-id="09763-108">Specifying `-verbose` is the same as specifying `-verbose+`, which causes the compiler to emit verbose messages.</span></span> <span data-ttu-id="09763-109">Wartość domyślna dla tej opcji to `-verbose-` .</span><span class="sxs-lookup"><span data-stu-id="09763-109">The default for this option is `-verbose-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="09763-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="09763-110">Remarks</span></span>  
 <span data-ttu-id="09763-111">`-verbose`Opcja wyświetla informacje o całkowitej liczbie błędów wydanych przez kompilator, raporty, które zestawy są ładowane przez moduł, i wyświetla pliki, które są obecnie kompilowane.</span><span class="sxs-lookup"><span data-stu-id="09763-111">The `-verbose` option displays information about the total number of errors issued by the compiler, reports which assemblies are being loaded by a module, and displays which files are currently being compiled.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="09763-112">`-verbose`Opcja jest niedostępna w środowisku deweloperskim programu Visual Studio. jest ona dostępna tylko podczas kompilowania z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="09763-112">The `-verbose` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="09763-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="09763-113">Example</span></span>  
 <span data-ttu-id="09763-114">Poniższy kod kompiluje `In.vb` i kieruje kompilator, aby wyświetlić pełne informacje o stanie.</span><span class="sxs-lookup"><span data-stu-id="09763-114">The following code compiles `In.vb` and directs the compiler to display verbose status information.</span></span>  
  
```console  
vbc -verbose in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="09763-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="09763-115">See also</span></span>

- [<span data-ttu-id="09763-116">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="09763-116">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="09763-117">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="09763-117">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
