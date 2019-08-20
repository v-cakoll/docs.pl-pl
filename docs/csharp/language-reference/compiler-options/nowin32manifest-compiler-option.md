---
title: -nowin32manifest (C# opcje kompilatora)
ms.date: 07/20/2015
f1_keywords:
- /nowin32manifest
helpviewer_keywords:
- nowin32manifest compiler option [C#]
- -nowin32manifest compiler option [C#]
- /nowin32manifest compiler option [C#]
ms.assetid: 6f06365b-b87b-46a2-b187-b3bfeaf4862d
ms.openlocfilehash: 8820410bfdbce2f9986605f37af4d14957471126
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602714"
---
# <a name="-nowin32manifest-c-compiler-options"></a><span data-ttu-id="a0e59-102">-nowin32manifest (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="a0e59-102">-nowin32manifest (C# Compiler Options)</span></span>
<span data-ttu-id="a0e59-103">Użyj opcji **-nowin32manifest** , aby nakazać kompilatorowi nie osadzenie żadnego manifestu aplikacji w pliku wykonywalnym.</span><span class="sxs-lookup"><span data-stu-id="a0e59-103">Use the **-nowin32manifest** option to instruct the compiler not to embed any application manifest into the executable file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0e59-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a0e59-104">Syntax</span></span>  
  
```console  
-nowin32manifest  
```  
  
## <a name="remarks"></a><span data-ttu-id="a0e59-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a0e59-105">Remarks</span></span>  
 <span data-ttu-id="a0e59-106">Gdy ta opcja jest używana, aplikacja będzie podlegać wirtualizacji w systemie Windows Vista, o ile nie podajesz manifestu aplikacji w pliku zasobów Win32 lub w późniejszym kroku kompilacji.</span><span class="sxs-lookup"><span data-stu-id="a0e59-106">When this option is used, the application will be subject to virtualization on Windows Vista unless you provide an application manifest in a Win32 Resource file or during a later build step.</span></span>  
  
 <span data-ttu-id="a0e59-107">W programie Visual Studio Ustaw tę opcję na stronie **właściwości aplikacji** , wybierając opcję **Utwórz aplikację bez manifestu** na liście rozwijanej **manifestu** .</span><span class="sxs-lookup"><span data-stu-id="a0e59-107">In Visual Studio, set this option in the **Application Property** page by selecting the **Create Application Without a Manifest** option in the **Manifest** drop down list.</span></span> <span data-ttu-id="a0e59-108">Aby uzyskać więcej informacji, zobacz [Strona aplikacji, Projektant projektuC#()](/visualstudio/ide/reference/application-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="a0e59-108">For more information, see [Application Page, Project Designer (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).</span></span>  
  
 <span data-ttu-id="a0e59-109">Aby uzyskać więcej informacji na temat tworzenia manifestu, zobacz [-C# WIN32MANIFEST (opcje kompilatora)](./win32manifest-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="a0e59-109">For more information about manifest creation, see [-win32manifest (C# Compiler Options)](./win32manifest-compiler-option.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0e59-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a0e59-110">See also</span></span>

- [<span data-ttu-id="a0e59-111">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="a0e59-111">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="a0e59-112">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="a0e59-112">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
