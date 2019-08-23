---
title: -verbose
ms.date: 03/13/2018
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
ms.openlocfilehash: 5b3899462af7c4aa8e0f77377a8d7485975f9867
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937259"
---
# <a name="-verbose"></a><span data-ttu-id="63735-102">-verbose</span><span class="sxs-lookup"><span data-stu-id="63735-102">-verbose</span></span>
<span data-ttu-id="63735-103">Powoduje, że kompilator tworzy pełny stan i komunikaty o błędach.</span><span class="sxs-lookup"><span data-stu-id="63735-103">Causes the compiler to produce verbose status and error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63735-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="63735-104">Syntax</span></span>  
  
```  
-verbose[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="63735-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="63735-105">Arguments</span></span>  
 <span data-ttu-id="63735-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="63735-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="63735-107">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="63735-107">Optional.</span></span> <span data-ttu-id="63735-108">Określanie `-verbose` jest takie samo jak określanie `-verbose+`, co powoduje, że kompilator emituje pełne komunikaty.</span><span class="sxs-lookup"><span data-stu-id="63735-108">Specifying `-verbose` is the same as specifying `-verbose+`, which causes the compiler to emit verbose messages.</span></span> <span data-ttu-id="63735-109">Wartość domyślna dla tej opcji to `-verbose-`.</span><span class="sxs-lookup"><span data-stu-id="63735-109">The default for this option is `-verbose-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="63735-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="63735-110">Remarks</span></span>  
 <span data-ttu-id="63735-111">`-verbose` Opcja wyświetla informacje o całkowitej liczbie błędów wydanych przez kompilator, raporty, które zestawy są ładowane przez moduł, i wyświetla pliki, które są obecnie kompilowane.</span><span class="sxs-lookup"><span data-stu-id="63735-111">The `-verbose` option displays information about the total number of errors issued by the compiler, reports which assemblies are being loaded by a module, and displays which files are currently being compiled.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="63735-112">`-verbose` Opcja jest niedostępna w środowisku deweloperskim programu Visual Studio. jest ona dostępna tylko podczas kompilowania z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="63735-112">The `-verbose` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="63735-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="63735-113">Example</span></span>  
 <span data-ttu-id="63735-114">Poniższy kod kompiluje `In.vb` i kieruje kompilator, aby wyświetlić pełne informacje o stanie.</span><span class="sxs-lookup"><span data-stu-id="63735-114">The following code compiles `In.vb` and directs the compiler to display verbose status information.</span></span>  
  
```console  
vbc -verbose in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="63735-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="63735-115">See also</span></span>

- [<span data-ttu-id="63735-116">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="63735-116">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="63735-117">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="63735-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
