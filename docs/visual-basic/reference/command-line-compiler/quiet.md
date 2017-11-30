---
title: /quiet
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- /quiet
- quiet
helpviewer_keywords:
- -quiet compiler option [Visual Basic]
- /quiet compiler option [Visual Basic]
- quiet compiler option [Visual Basic]
ms.assetid: 5d77fa23-4c50-4708-8535-649912b098e8
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3b816cadb9d805d57a14e9b5df553654dd8167af
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="quiet"></a><span data-ttu-id="64761-102">/quiet</span><span class="sxs-lookup"><span data-stu-id="64761-102">/quiet</span></span>
<span data-ttu-id="64761-103">Uniemożliwia wyświetlanie kodu dotyczące składni błędów i ostrzeżeń kompilatora.</span><span class="sxs-lookup"><span data-stu-id="64761-103">Prevents the compiler from displaying code for syntax-related errors and warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64761-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="64761-104">Syntax</span></span>  
  
```  
/quiet  
```  
  
## <a name="remarks"></a><span data-ttu-id="64761-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="64761-105">Remarks</span></span>  
 <span data-ttu-id="64761-106">Domyślnie `/quiet` nie jest włączone.</span><span class="sxs-lookup"><span data-stu-id="64761-106">By default, `/quiet` is not in effect.</span></span> <span data-ttu-id="64761-107">Kiedy kompilator zgłasza błąd związany z składni lub ostrzeżenie, generuje także wiersza z kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="64761-107">When the compiler reports a syntax-related error or warning, it also outputs the line from source code.</span></span> <span data-ttu-id="64761-108">Dla aplikacji, które przeanalizować dane wyjściowe kompilatora może być wygodniejsze kompilator, aby uzyskać tylko tekst diagnostyki.</span><span class="sxs-lookup"><span data-stu-id="64761-108">For applications that parse compiler output, it may be more convenient for the compiler to output only the text of the diagnostic.</span></span>  
  
 <span data-ttu-id="64761-109">W poniższym przykładzie `Module1` generuje błąd, który zawiera kod źródłowy, gdy kompilowany bez `/quiet`.</span><span class="sxs-lookup"><span data-stu-id="64761-109">In the following example, `Module1` outputs an error that includes source code when compiled without `/quiet`.</span></span>  
  
```  
Module Module1  
    Sub Main()  
        x()  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="64761-110">Dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="64761-110">Output:</span></span>  
  
 `E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.`  
  
 `x`  
  
 `~`  
  
 <span data-ttu-id="64761-111">Skompilowane z `/quiet`, kompilator generuje jedynie następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="64761-111">Compiled with `/quiet`, the compiler outputs only the following:</span></span>  
  
 `E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.`  
  
> [!NOTE]
>  <span data-ttu-id="64761-112">`/quiet` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="64761-112">The `/quiet` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64761-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="64761-113">Example</span></span>  
 <span data-ttu-id="64761-114">Poniższy kod kompiluje `T2.vb` i nie zawiera kodu dla diagnostyki kompilatora dotyczące składni:</span><span class="sxs-lookup"><span data-stu-id="64761-114">The following code compiles `T2.vb` and does not display code for syntax-related compiler diagnostics:</span></span>  
  
```  
vbc /quiet t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="64761-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="64761-115">See Also</span></span>  
 [<span data-ttu-id="64761-116">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="64761-116">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="64761-117">Kompilacja przykładów — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="64761-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
