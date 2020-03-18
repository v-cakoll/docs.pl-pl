---
title: -nowin32manifest (Opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /nowin32manifest
helpviewer_keywords:
- nowin32manifest compiler option [C#]
- -nowin32manifest compiler option [C#]
- /nowin32manifest compiler option [C#]
ms.assetid: 6f06365b-b87b-46a2-b187-b3bfeaf4862d
ms.openlocfilehash: 8820410bfdbce2f9986605f37af4d14957471126
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69602714"
---
# <a name="-nowin32manifest-c-compiler-options"></a><span data-ttu-id="2555b-102">-nowin32manifest (Opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="2555b-102">-nowin32manifest (C# Compiler Options)</span></span>
<span data-ttu-id="2555b-103">Użyj opcji **-nowin32manifest,** aby poinstruować kompilator, aby nie osadzał żadnego manifestu aplikacji w pliku wykonywalnym.</span><span class="sxs-lookup"><span data-stu-id="2555b-103">Use the **-nowin32manifest** option to instruct the compiler not to embed any application manifest into the executable file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2555b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2555b-104">Syntax</span></span>  
  
```console  
-nowin32manifest  
```  
  
## <a name="remarks"></a><span data-ttu-id="2555b-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2555b-105">Remarks</span></span>  
 <span data-ttu-id="2555b-106">Gdy ta opcja jest używana, aplikacja będzie podlegać wirtualizacji w systemie Windows Vista, chyba że podasz manifest aplikacji w pliku zasobu Win32 lub podczas późniejszego kroku kompilacji.</span><span class="sxs-lookup"><span data-stu-id="2555b-106">When this option is used, the application will be subject to virtualization on Windows Vista unless you provide an application manifest in a Win32 Resource file or during a later build step.</span></span>  
  
 <span data-ttu-id="2555b-107">W programie Visual Studio ustaw tę opcję na stronie **Właściwości aplikacji,** wybierając opcję **Utwórz aplikację bez manifestu** na liście rozwijanej **Manifest.**</span><span class="sxs-lookup"><span data-stu-id="2555b-107">In Visual Studio, set this option in the **Application Property** page by selecting the **Create Application Without a Manifest** option in the **Manifest** drop down list.</span></span> <span data-ttu-id="2555b-108">Aby uzyskać więcej informacji, zobacz [Strona aplikacji, Projektant projektu (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="2555b-108">For more information, see [Application Page, Project Designer (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).</span></span>  
  
 <span data-ttu-id="2555b-109">Aby uzyskać więcej informacji na temat tworzenia manifestu, zobacz [-win32manifest (Opcje kompilatora C#)](./win32manifest-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="2555b-109">For more information about manifest creation, see [-win32manifest (C# Compiler Options)](./win32manifest-compiler-option.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2555b-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2555b-110">See also</span></span>

- [<span data-ttu-id="2555b-111">Opcje kompilatora Języka C#</span><span class="sxs-lookup"><span data-stu-id="2555b-111">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="2555b-112">Zarządzanie właściwościami projektów i rozwiązań</span><span class="sxs-lookup"><span data-stu-id="2555b-112">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
