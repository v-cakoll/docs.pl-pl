---
title: -nologo (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
ms.openlocfilehash: 07e1718554b158635b9d8b04958834e804e1fe9f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964378"
---
# <a name="-nologo-visual-basic"></a><span data-ttu-id="fe6b7-102">-nologo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fe6b7-102">-nologo (Visual Basic)</span></span>
<span data-ttu-id="fe6b7-103">Pomija wyświetlanie transparentu praw autorskich i komunikatów informacyjnych podczas kompilacji.</span><span class="sxs-lookup"><span data-stu-id="fe6b7-103">Suppresses display of the copyright banner and informational messages during compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe6b7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fe6b7-104">Syntax</span></span>  
  
```  
-nologo  
```  
  
## <a name="remarks"></a><span data-ttu-id="fe6b7-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fe6b7-105">Remarks</span></span>  
 <span data-ttu-id="fe6b7-106">Jeśli określisz `-nologo`, kompilator nie wyświetli transparentu praw autorskich.</span><span class="sxs-lookup"><span data-stu-id="fe6b7-106">If you specify `-nologo`, the compiler does not display a copyright banner.</span></span> <span data-ttu-id="fe6b7-107">Domyślnie program `-nologo` nie działa.</span><span class="sxs-lookup"><span data-stu-id="fe6b7-107">By default, `-nologo` is not in effect.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fe6b7-108">`-nologo` Opcja jest niedostępna w środowisku deweloperskim programu Visual Studio. jest ona dostępna tylko podczas kompilowania z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="fe6b7-108">The `-nologo` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fe6b7-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="fe6b7-109">Example</span></span>  
 <span data-ttu-id="fe6b7-110">Poniższy kod kompiluje `T2.vb` i nie wyświetla transparentu praw autorskich.</span><span class="sxs-lookup"><span data-stu-id="fe6b7-110">The following code compiles `T2.vb` and does not display a copyright banner.</span></span>  
  
```console
vbc -nologo t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="fe6b7-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fe6b7-111">See also</span></span>

- [<span data-ttu-id="fe6b7-112">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fe6b7-112">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="fe6b7-113">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="fe6b7-113">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
