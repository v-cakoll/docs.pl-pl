---
title: -nowin32manifest (opcje kompilatora C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /nowin32manifest
helpviewer_keywords:
- nowin32manifest compiler option [C#]
- -nowin32manifest compiler option [C#]
- /nowin32manifest compiler option [C#]
ms.assetid: 6f06365b-b87b-46a2-b187-b3bfeaf4862d
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1e0d4697e0e14c84c4bc642521cf4f9cdf6a4ed6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="nowin32manifest-c-compiler-options"></a><span data-ttu-id="dd84f-102">/nowin32manifest (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="dd84f-102">/nowin32manifest (C# Compiler Options)</span></span>
<span data-ttu-id="dd84f-103">Użyj **/nowin32manifest** opcję, aby poinstruować kompilatora nie do osadzania manifestu żadnych aplikacji w pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="dd84f-103">Use the **/nowin32manifest** option to instruct the compiler not to embed any application manifest into the executable file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd84f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dd84f-104">Syntax</span></span>  
  
```console  
/nowin32manifest  
```  
  
## <a name="remarks"></a><span data-ttu-id="dd84f-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dd84f-105">Remarks</span></span>  
 <span data-ttu-id="dd84f-106">Gdy ta opcja jest używana, aplikacja podlegać wirtualizacji w systemie Windows Vista dopiero po podaniu manifest aplikacji w pliku zasobów Win32 lub w późniejszym kroku kompilacji.</span><span class="sxs-lookup"><span data-stu-id="dd84f-106">When this option is used, the application will be subject to virtualization on Windows Vista unless you provide an application manifest in a Win32 Resource file or during a later build step.</span></span>  
  
 <span data-ttu-id="dd84f-107">W programie Visual Studio, ustaw tę opcję **aplikacji właściwości** strony, wybierając **Utwórz aplikację bez manifestu** opcji **manifestu** listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="dd84f-107">In Visual Studio, set this option in the **Application Property** page by selecting the **Create Application Without a Manifest** option in the **Manifest** drop down list.</span></span> <span data-ttu-id="dd84f-108">Aby uzyskać więcej informacji, zobacz [strona aplikacji, Projektant projektu (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="dd84f-108">For more information, see [Application Page, Project Designer (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).</span></span>  
  
 <span data-ttu-id="dd84f-109">Aby uzyskać więcej informacji o tworzeniu manifestu, zobacz [/win32manifest (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/win32manifest-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="dd84f-109">For more information about manifest creation, see [/win32manifest (C# Compiler Options)](../../../csharp/language-reference/compiler-options/win32manifest-compiler-option.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd84f-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dd84f-110">See Also</span></span>  
 [<span data-ttu-id="dd84f-111">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="dd84f-111">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="dd84f-112">Zarządzanie właściwościami projektów i rozwiązań</span><span class="sxs-lookup"><span data-stu-id="dd84f-112">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
