---
title: -nologo (Visual Basic)
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8e5eb9db7af861a8439b47adb8f5e515331fae6e
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
---
# <a name="-nologo-visual-basic"></a><span data-ttu-id="3e9f1-102">-nologo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3e9f1-102">-nologo (Visual Basic)</span></span>
<span data-ttu-id="3e9f1-103">Pomija wyświetlanie banera praw autorskich i komunikaty informacyjne podczas kompilacji.</span><span class="sxs-lookup"><span data-stu-id="3e9f1-103">Suppresses display of the copyright banner and informational messages during compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e9f1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3e9f1-104">Syntax</span></span>  
  
```  
-nologo  
```  
  
## <a name="remarks"></a><span data-ttu-id="3e9f1-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3e9f1-105">Remarks</span></span>  
 <span data-ttu-id="3e9f1-106">Jeśli określisz `-nologo`, kompilator nie wyświetla transparentu o prawach autorskich.</span><span class="sxs-lookup"><span data-stu-id="3e9f1-106">If you specify `-nologo`, the compiler does not display a copyright banner.</span></span> <span data-ttu-id="3e9f1-107">Domyślnie `-nologo` nie jest włączone.</span><span class="sxs-lookup"><span data-stu-id="3e9f1-107">By default, `-nologo` is not in effect.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3e9f1-108">`-nologo` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="3e9f1-108">The `-nologo` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e9f1-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="3e9f1-109">Example</span></span>  
 <span data-ttu-id="3e9f1-110">Poniższy kod kompiluje `T2.vb` i nie wyświetla transparentu o prawach autorskich.</span><span class="sxs-lookup"><span data-stu-id="3e9f1-110">The following code compiles `T2.vb` and does not display a copyright banner.</span></span>  
  
```console
vbc -nologo t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="3e9f1-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3e9f1-111">See Also</span></span>  
 [<span data-ttu-id="3e9f1-112">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3e9f1-112">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="3e9f1-113">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="3e9f1-113">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
