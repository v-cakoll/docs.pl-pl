---
title: -utf8output
ms.date: 07/20/2015
helpviewer_keywords:
- -utf8output compiler option [Visual Basic]
- utf8output compiler option [Visual Basic]
- /utf8output compiler option [Visual Basic]
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
ms.openlocfilehash: 0a16cdc535de5ed0619bf080bb4637449b11cfef
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403060"
---
# <a name="-utf8output-visual-basic"></a><span data-ttu-id="0539d-102">-utf8output — (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0539d-102">-utf8output (Visual Basic)</span></span>
<span data-ttu-id="0539d-103">Wyświetla dane wyjściowe kompilatora przy użyciu kodowania UTF-8.</span><span class="sxs-lookup"><span data-stu-id="0539d-103">Displays compiler output using UTF-8 encoding.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0539d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0539d-104">Syntax</span></span>  
  
```console  
-utf8output[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="0539d-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="0539d-105">Arguments</span></span>  
 <span data-ttu-id="0539d-106">`+`&#124;`-`</span><span class="sxs-lookup"><span data-stu-id="0539d-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="0539d-107">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="0539d-107">Optional.</span></span> <span data-ttu-id="0539d-108">Wartość domyślna dla tej opcji to `-utf8output-` , co oznacza, że wyjście kompilatora nie używa kodowania UTF-8.</span><span class="sxs-lookup"><span data-stu-id="0539d-108">The default for this option is `-utf8output-`, which means compiler output does not use UTF-8 encoding.</span></span> <span data-ttu-id="0539d-109">Określanie `-utf8output` jest takie samo jak określanie `-utf8output+` .</span><span class="sxs-lookup"><span data-stu-id="0539d-109">Specifying `-utf8output` is the same as specifying `-utf8output+`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0539d-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0539d-110">Remarks</span></span>  
 <span data-ttu-id="0539d-111">W niektórych konfiguracjach międzynarodowych dane wyjściowe kompilatora nie mogą być prawidłowo wyświetlane w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="0539d-111">In some international configurations, compiler output cannot be displayed correctly in the console.</span></span> <span data-ttu-id="0539d-112">W takich sytuacjach należy używać `-utf8output` i przekierować dane wyjściowe kompilatora do pliku.</span><span class="sxs-lookup"><span data-stu-id="0539d-112">In such situations, use `-utf8output` and redirect compiler output to a file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0539d-113">`-utf8output`Opcja jest niedostępna w środowisku deweloperskim programu Visual Studio. jest ona dostępna tylko podczas kompilowania z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="0539d-113">The `-utf8output` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0539d-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="0539d-114">Example</span></span>  
 <span data-ttu-id="0539d-115">Poniższy kod kompiluje `In.vb` i kieruje kompilator do wyświetlania danych wyjściowych przy użyciu kodowania UTF-8.</span><span class="sxs-lookup"><span data-stu-id="0539d-115">The following code compiles `In.vb` and directs the compiler to display output using UTF-8 encoding.</span></span>  
  
```console  
vbc -utf8output in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="0539d-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0539d-116">See also</span></span>

- [<span data-ttu-id="0539d-117">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0539d-117">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="0539d-118">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="0539d-118">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
