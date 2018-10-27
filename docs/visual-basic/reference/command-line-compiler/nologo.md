---
title: -nologo (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
ms.openlocfilehash: 21c708ef632cc0ed923713cd49e22d44848b4db3
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50037285"
---
# <a name="-nologo-visual-basic"></a><span data-ttu-id="918b3-102">-nologo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="918b3-102">-nologo (Visual Basic)</span></span>
<span data-ttu-id="918b3-103">Pomija wyświetlanie transparentu praw autorskich i komunikaty informacyjne, podczas kompilacji.</span><span class="sxs-lookup"><span data-stu-id="918b3-103">Suppresses display of the copyright banner and informational messages during compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="918b3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="918b3-104">Syntax</span></span>  
  
```  
-nologo  
```  
  
## <a name="remarks"></a><span data-ttu-id="918b3-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="918b3-105">Remarks</span></span>  
 <span data-ttu-id="918b3-106">Jeśli określisz `-nologo`, kompilator nie wyświetla transparentu praw autorskich.</span><span class="sxs-lookup"><span data-stu-id="918b3-106">If you specify `-nologo`, the compiler does not display a copyright banner.</span></span> <span data-ttu-id="918b3-107">Domyślnie `-nologo` nie jest włączone.</span><span class="sxs-lookup"><span data-stu-id="918b3-107">By default, `-nologo` is not in effect.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="918b3-108">`-nologo` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="918b3-108">The `-nologo` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="918b3-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="918b3-109">Example</span></span>  
 <span data-ttu-id="918b3-110">Poniższy kod kompiluje `T2.vb` i nie wyświetla transparentu praw autorskich.</span><span class="sxs-lookup"><span data-stu-id="918b3-110">The following code compiles `T2.vb` and does not display a copyright banner.</span></span>  
  
```console
vbc -nologo t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="918b3-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="918b3-111">See Also</span></span>  
 [<span data-ttu-id="918b3-112">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="918b3-112">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="918b3-113">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="918b3-113">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
