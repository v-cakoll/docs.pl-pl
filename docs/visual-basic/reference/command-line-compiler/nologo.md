---
title: -nologo (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
ms.openlocfilehash: c1824e4a086ecdd4b6a776bd6894f6e003d02867
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58822560"
---
# <a name="-nologo-visual-basic"></a><span data-ttu-id="3e079-102">-nologo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3e079-102">-nologo (Visual Basic)</span></span>
<span data-ttu-id="3e079-103">Pomija wyświetlanie transparentu praw autorskich i komunikaty informacyjne, podczas kompilacji.</span><span class="sxs-lookup"><span data-stu-id="3e079-103">Suppresses display of the copyright banner and informational messages during compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e079-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3e079-104">Syntax</span></span>  
  
```  
-nologo  
```  
  
## <a name="remarks"></a><span data-ttu-id="3e079-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3e079-105">Remarks</span></span>  
 <span data-ttu-id="3e079-106">Jeśli określisz `-nologo`, kompilator nie wyświetla transparentu praw autorskich.</span><span class="sxs-lookup"><span data-stu-id="3e079-106">If you specify `-nologo`, the compiler does not display a copyright banner.</span></span> <span data-ttu-id="3e079-107">Domyślnie `-nologo` nie jest włączone.</span><span class="sxs-lookup"><span data-stu-id="3e079-107">By default, `-nologo` is not in effect.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3e079-108">`-nologo` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="3e079-108">The `-nologo` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e079-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="3e079-109">Example</span></span>  
 <span data-ttu-id="3e079-110">Poniższy kod kompiluje `T2.vb` i nie wyświetla transparentu praw autorskich.</span><span class="sxs-lookup"><span data-stu-id="3e079-110">The following code compiles `T2.vb` and does not display a copyright banner.</span></span>  
  
```console
vbc -nologo t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="3e079-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3e079-111">See also</span></span>

- [<span data-ttu-id="3e079-112">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3e079-112">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="3e079-113">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="3e079-113">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
