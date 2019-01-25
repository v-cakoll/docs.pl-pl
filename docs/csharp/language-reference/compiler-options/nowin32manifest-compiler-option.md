---
title: -nowin32manifest (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /nowin32manifest
helpviewer_keywords:
- nowin32manifest compiler option [C#]
- -nowin32manifest compiler option [C#]
- /nowin32manifest compiler option [C#]
ms.assetid: 6f06365b-b87b-46a2-b187-b3bfeaf4862d
ms.openlocfilehash: 357bc0dbe261a5d55b958fa0e8256920f050356d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54516866"
---
# <a name="-nowin32manifest-c-compiler-options"></a><span data-ttu-id="596d4-102">-nowin32manifest (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="596d4-102">-nowin32manifest (C# Compiler Options)</span></span>
<span data-ttu-id="596d4-103">Użyj **-nowin32manifest** opcję, aby poinstruować kompilator, nie można osadzić manifest dowolnej aplikacji w pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="596d4-103">Use the **-nowin32manifest** option to instruct the compiler not to embed any application manifest into the executable file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="596d4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="596d4-104">Syntax</span></span>  
  
```console  
-nowin32manifest  
```  
  
## <a name="remarks"></a><span data-ttu-id="596d4-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="596d4-105">Remarks</span></span>  
 <span data-ttu-id="596d4-106">Gdy ta opcja jest używana, aplikacja będzie wirtualizacji w systemie Windows Vista, chyba że zapewniasz manifest aplikacji w pliku zasobów Win32 lub w późniejszym kroku kompilacji.</span><span class="sxs-lookup"><span data-stu-id="596d4-106">When this option is used, the application will be subject to virtualization on Windows Vista unless you provide an application manifest in a Win32 Resource file or during a later build step.</span></span>  
  
 <span data-ttu-id="596d4-107">W programie Visual Studio, należy ustawić tę opcję w **właściwość aplikacji** strony, wybierając **tworzenie aplikacji bez manifestu** opcji **manifestu** listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="596d4-107">In Visual Studio, set this option in the **Application Property** page by selecting the **Create Application Without a Manifest** option in the **Manifest** drop down list.</span></span> <span data-ttu-id="596d4-108">Aby uzyskać więcej informacji, zobacz [strona aplikacji, Projektant projektu (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="596d4-108">For more information, see [Application Page, Project Designer (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).</span></span>  
  
 <span data-ttu-id="596d4-109">Aby uzyskać więcej informacji o tworzeniu manifestu, zobacz [-win32manifest (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/win32manifest-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="596d4-109">For more information about manifest creation, see [-win32manifest (C# Compiler Options)](../../../csharp/language-reference/compiler-options/win32manifest-compiler-option.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="596d4-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="596d4-110">See also</span></span>

- [<span data-ttu-id="596d4-111">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="596d4-111">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="596d4-112">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="596d4-112">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
