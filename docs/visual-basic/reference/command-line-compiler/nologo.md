---
title: -nologo (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
ms.openlocfilehash: bb64a468f67745b80b47b42c4fac18852279035d
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005426"
---
# <a name="-nologo-visual-basic"></a><span data-ttu-id="95f60-102">-nologo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="95f60-102">-nologo (Visual Basic)</span></span>
<span data-ttu-id="95f60-103">Pomija wyświetlanie transparentu praw autorskich i komunikatów informacyjnych podczas kompilacji.</span><span class="sxs-lookup"><span data-stu-id="95f60-103">Suppresses display of the copyright banner and informational messages during compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95f60-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="95f60-104">Syntax</span></span>  
  
```console  
-nologo  
```  
  
## <a name="remarks"></a><span data-ttu-id="95f60-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="95f60-105">Remarks</span></span>  
 <span data-ttu-id="95f60-106">W przypadku określenia `-nologo` kompilator nie będzie wyświetlał transparentu praw autorskich.</span><span class="sxs-lookup"><span data-stu-id="95f60-106">If you specify `-nologo`, the compiler does not display a copyright banner.</span></span> <span data-ttu-id="95f60-107">Domyślnie `-nologo` nie jest włączona.</span><span class="sxs-lookup"><span data-stu-id="95f60-107">By default, `-nologo` is not in effect.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="95f60-108">Opcja `-nologo` nie jest dostępna w środowisku deweloperskim programu Visual Studio. jest on dostępny tylko w przypadku kompilowania z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="95f60-108">The `-nologo` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95f60-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="95f60-109">Example</span></span>  
 <span data-ttu-id="95f60-110">Poniższy kod kompiluje `T2.vb` i nie wyświetla transparentu praw autorskich.</span><span class="sxs-lookup"><span data-stu-id="95f60-110">The following code compiles `T2.vb` and does not display a copyright banner.</span></span>  
  
```console
vbc -nologo t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="95f60-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="95f60-111">See also</span></span>

- [<span data-ttu-id="95f60-112">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="95f60-112">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="95f60-113">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="95f60-113">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
