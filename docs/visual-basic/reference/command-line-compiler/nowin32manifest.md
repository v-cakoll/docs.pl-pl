---
title: -nowin32manifest
ms.date: 03/13/2018
helpviewer_keywords:
- /nowin32manifest compiler option [Visual Basic]
- nowin32manifest compiler option [Visual Basic]
- -nowin32manifest compiler option [Visual Basic]
ms.assetid: c0528aae-83b3-4425-99f0-19448e9843e3
ms.openlocfilehash: d9323cd541eaf611551de90e58a181f6915fad89
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397457"
---
# <a name="-nowin32manifest-visual-basic"></a><span data-ttu-id="41489-102">-nowin32manifest (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="41489-102">-nowin32manifest (Visual Basic)</span></span>
<span data-ttu-id="41489-103">Instruuje kompilator, aby nie osadzał żadnego manifestu aplikacji w pliku wykonywalnym.</span><span class="sxs-lookup"><span data-stu-id="41489-103">Instructs the compiler not to embed any application manifest into the executable file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41489-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="41489-104">Syntax</span></span>  
  
```console  
-nowin32manifest  
```  
  
## <a name="remarks"></a><span data-ttu-id="41489-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="41489-105">Remarks</span></span>  
 <span data-ttu-id="41489-106">Gdy ta opcja jest używana, aplikacja będzie podlegać wirtualizacji w systemie Windows Vista, o ile nie podajesz manifestu aplikacji w pliku zasobów Win32 lub w późniejszym kroku kompilacji.</span><span class="sxs-lookup"><span data-stu-id="41489-106">When this option is used, the application will be subject to virtualization on Windows Vista unless you provide an application manifest in a Win32 Resource file or during a later build step.</span></span> <span data-ttu-id="41489-107">Aby uzyskać więcej informacji na temat wirtualizacji, zobacz [wdrażanie ClickOnce w systemie Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span><span class="sxs-lookup"><span data-stu-id="41489-107">For more information about virtualization, see [ClickOnce Deployment on Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span></span>  
  
 <span data-ttu-id="41489-108">Aby uzyskać więcej informacji na temat tworzenia manifestu, zobacz [-WIN32MANIFEST (Visual Basic)](win32manifest.md).</span><span class="sxs-lookup"><span data-stu-id="41489-108">For more information about manifest creation, see [-win32manifest (Visual Basic)](win32manifest.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41489-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="41489-109">See also</span></span>

- [<span data-ttu-id="41489-110">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="41489-110">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="41489-111">Strona aplikacji, Projektant projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="41489-111">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
