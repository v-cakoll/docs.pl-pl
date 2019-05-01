---
title: -nowin32manifest (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /nowin32manifest compiler option [Visual Basic]
- nowin32manifest compiler option [Visual Basic]
- -nowin32manifest compiler option [Visual Basic]
ms.assetid: c0528aae-83b3-4425-99f0-19448e9843e3
ms.openlocfilehash: 2d14da2d0c24f3bd833503c73374d26ee73c5629
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789015"
---
# <a name="-nowin32manifest-visual-basic"></a><span data-ttu-id="6cb6c-102">-nowin32manifest (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6cb6c-102">-nowin32manifest (Visual Basic)</span></span>
<span data-ttu-id="6cb6c-103">Instruuje kompilator, nie można osadzić manifest dowolnej aplikacji w pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="6cb6c-103">Instructs the compiler not to embed any application manifest into the executable file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cb6c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6cb6c-104">Syntax</span></span>  
  
```  
-nowin32manifest  
```  
  
## <a name="remarks"></a><span data-ttu-id="6cb6c-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6cb6c-105">Remarks</span></span>  
 <span data-ttu-id="6cb6c-106">Gdy ta opcja jest używana, aplikacja będzie wirtualizacji w systemie Windows Vista, chyba że zapewniasz manifest aplikacji w pliku zasobów Win32 lub w późniejszym kroku kompilacji.</span><span class="sxs-lookup"><span data-stu-id="6cb6c-106">When this option is used, the application will be subject to virtualization on Windows Vista unless you provide an application manifest in a Win32 Resource file or during a later build step.</span></span> <span data-ttu-id="6cb6c-107">Aby uzyskać więcej informacji na temat wirtualizacji, zobacz [wdrażania ClickOnce w systemie Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span><span class="sxs-lookup"><span data-stu-id="6cb6c-107">For more information about virtualization, see [ClickOnce Deployment on Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span></span>  
  
 <span data-ttu-id="6cb6c-108">Aby uzyskać więcej informacji o tworzeniu manifestu, zobacz [-win32manifest (Visual Basic)](../../../visual-basic/reference/command-line-compiler/win32manifest.md).</span><span class="sxs-lookup"><span data-stu-id="6cb6c-108">For more information about manifest creation, see [-win32manifest (Visual Basic)](../../../visual-basic/reference/command-line-compiler/win32manifest.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cb6c-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6cb6c-109">See also</span></span>

- [<span data-ttu-id="6cb6c-110">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6cb6c-110">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="6cb6c-111">Strona aplikacji, Projektant projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6cb6c-111">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
