---
title: -utf8output (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- -utf8output compiler option [Visual Basic]
- utf8output compiler option [Visual Basic]
- /utf8output compiler option [Visual Basic]
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
ms.openlocfilehash: 75369c3bcb19afbf98bfb80bc3e439f996d2a9d0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796081"
---
# <a name="-utf8output-visual-basic"></a><span data-ttu-id="c36f3-102">-utf8output (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c36f3-102">-utf8output (Visual Basic)</span></span>
<span data-ttu-id="c36f3-103">Kompilator wyświetla dane wyjściowe przy użyciu kodowania UTF-8.</span><span class="sxs-lookup"><span data-stu-id="c36f3-103">Displays compiler output using UTF-8 encoding.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c36f3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c36f3-104">Syntax</span></span>  
  
```  
-utf8output[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="c36f3-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="c36f3-105">Arguments</span></span>  
 <span data-ttu-id="c36f3-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="c36f3-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="c36f3-107">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="c36f3-107">Optional.</span></span> <span data-ttu-id="c36f3-108">Wartość domyślna tej opcji to `-utf8output-`, co oznacza, że dane wyjściowe kompilatora nie używa kodowania UTF-8.</span><span class="sxs-lookup"><span data-stu-id="c36f3-108">The default for this option is `-utf8output-`, which means compiler output does not use UTF-8 encoding.</span></span> <span data-ttu-id="c36f3-109">Określanie `-utf8output` jest taka sama jak określanie `-utf8output+`.</span><span class="sxs-lookup"><span data-stu-id="c36f3-109">Specifying `-utf8output` is the same as specifying `-utf8output+`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c36f3-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c36f3-110">Remarks</span></span>  
 <span data-ttu-id="c36f3-111">W niektórych konfiguracjach międzynarodowe dane wyjściowe kompilatora nie można wyświetlić prawidłowo w konsoli.</span><span class="sxs-lookup"><span data-stu-id="c36f3-111">In some international configurations, compiler output cannot be displayed correctly in the console.</span></span> <span data-ttu-id="c36f3-112">W takich sytuacjach należy użyć `-utf8output` i przekierować dane wyjściowe kompilatora do pliku.</span><span class="sxs-lookup"><span data-stu-id="c36f3-112">In such situations, use `-utf8output` and redirect compiler output to a file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c36f3-113">`-utf8output` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="c36f3-113">The `-utf8output` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c36f3-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="c36f3-114">Example</span></span>  
 <span data-ttu-id="c36f3-115">Poniższy kod kompiluje `In.vb` i instruuje kompilator, aby wyświetlić dane wyjściowe przy użyciu kodowania UTF-8.</span><span class="sxs-lookup"><span data-stu-id="c36f3-115">The following code compiles `In.vb` and directs the compiler to display output using UTF-8 encoding.</span></span>  
  
```console  
vbc -utf8output in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="c36f3-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c36f3-116">See also</span></span>

- [<span data-ttu-id="c36f3-117">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c36f3-117">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="c36f3-118">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="c36f3-118">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
