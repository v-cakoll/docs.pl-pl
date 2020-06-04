---
title: -nologo
ms.date: 03/13/2018
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
ms.openlocfilehash: d1307603ebc06b4eb4c3786f1cd2fb432c0cf636
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360465"
---
# <a name="-nologo-visual-basic"></a><span data-ttu-id="c74c9-102">-nologo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c74c9-102">-nologo (Visual Basic)</span></span>
<span data-ttu-id="c74c9-103">Pomija wyświetlanie transparentu praw autorskich i komunikatów informacyjnych podczas kompilacji.</span><span class="sxs-lookup"><span data-stu-id="c74c9-103">Suppresses display of the copyright banner and informational messages during compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c74c9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c74c9-104">Syntax</span></span>  
  
```console  
-nologo  
```  
  
## <a name="remarks"></a><span data-ttu-id="c74c9-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c74c9-105">Remarks</span></span>  
 <span data-ttu-id="c74c9-106">Jeśli określisz `-nologo` , kompilator nie wyświetli transparentu praw autorskich.</span><span class="sxs-lookup"><span data-stu-id="c74c9-106">If you specify `-nologo`, the compiler does not display a copyright banner.</span></span> <span data-ttu-id="c74c9-107">Domyślnie program `-nologo` nie działa.</span><span class="sxs-lookup"><span data-stu-id="c74c9-107">By default, `-nologo` is not in effect.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c74c9-108">`-nologo`Opcja jest niedostępna w środowisku deweloperskim programu Visual Studio. jest ona dostępna tylko podczas kompilowania z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="c74c9-108">The `-nologo` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c74c9-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="c74c9-109">Example</span></span>  
 <span data-ttu-id="c74c9-110">Poniższy kod kompiluje `T2.vb` i nie wyświetla transparentu praw autorskich.</span><span class="sxs-lookup"><span data-stu-id="c74c9-110">The following code compiles `T2.vb` and does not display a copyright banner.</span></span>  
  
```console
vbc -nologo t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="c74c9-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c74c9-111">See also</span></span>

- [<span data-ttu-id="c74c9-112">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c74c9-112">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="c74c9-113">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="c74c9-113">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
