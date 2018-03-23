---
title: -win32manifest (Visual Basic)
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /win32manifest compiler option [Visual Basic]
- win32manifest compiler option [Visual Basic]
- -win32manifest compiler option [Visual Basic]
ms.assetid: 9e3191b4-90db-41c8-966a-28036fd20005
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 79b51117197f28cec21671eea4dd7b7f2f1cc306
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
---
# <a name="-win32manifest-visual-basic"></a><span data-ttu-id="cae38-102">-win32manifest (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cae38-102">-win32manifest (Visual Basic)</span></span>
<span data-ttu-id="cae38-103">Identyfikuje użytkownika aplikacji plik manifestu Win32 do osadzenia pliku przenośny plik wykonywalny (PE) projektu.</span><span class="sxs-lookup"><span data-stu-id="cae38-103">Identifies a user-defined Win32 application manifest file to be embedded into a project's portable executable (PE) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cae38-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cae38-104">Syntax</span></span>  
  
```  
-win32manifest: fileName  
```  
  
## <a name="arguments"></a><span data-ttu-id="cae38-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="cae38-105">Arguments</span></span>  
  
|<span data-ttu-id="cae38-106">Termin</span><span class="sxs-lookup"><span data-stu-id="cae38-106">Term</span></span>|<span data-ttu-id="cae38-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="cae38-107">Definition</span></span>|  
|---|---|  
|`fileName`|<span data-ttu-id="cae38-108">Ścieżka niestandardowego pliku manifestu.</span><span class="sxs-lookup"><span data-stu-id="cae38-108">The path of the custom manifest file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cae38-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cae38-109">Remarks</span></span>  
 <span data-ttu-id="cae38-110">Domyślnie kompilator Visual Basic osadza manifest aplikacji, która określa poziom wykonywania żądany asInvoker.</span><span class="sxs-lookup"><span data-stu-id="cae38-110">By default, the Visual Basic compiler embeds an application manifest that specifies a requested execution level of asInvoker.</span></span> <span data-ttu-id="cae38-111">W tym samym folderze, w którym plik wykonywalny jest wbudowana, zwykle folderu bin\Debug lub bin\Release, gdy używasz programu Visual Studio tworzy plik manifestu.</span><span class="sxs-lookup"><span data-stu-id="cae38-111">It creates the manifest in the same folder in which the executable file is built, typically the bin\Debug or bin\Release folder when you use Visual Studio.</span></span> <span data-ttu-id="cae38-112">Jeśli chcesz podać niestandardowy manifest, na przykład określić wymagany poziom wykonywania highestAvailable lub requireAdministrator, ta opcja umożliwia Określ nazwę pliku.</span><span class="sxs-lookup"><span data-stu-id="cae38-112">If you want to supply a custom manifest, for example to specify a requested execution level of highestAvailable or requireAdministrator, use this option to specify the name of the file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cae38-113">Ta opcja i [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) opcji wzajemnie się wykluczają.</span><span class="sxs-lookup"><span data-stu-id="cae38-113">This option and the [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) option are mutually exclusive.</span></span> <span data-ttu-id="cae38-114">Jeśli spróbujesz użyć obu opcji, w tym samym wierszu polecenia, wystąpi błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="cae38-114">If you try to use both options in the same command line, you will get a build error.</span></span>  
  
 <span data-ttu-id="cae38-115">Aplikacja, która nie ma aplikacji manifestu, który określa wymagany poziom wykonywania podlegają wirtualizacji plików/rejestru w funkcji Kontrola konta użytkownika w systemie Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="cae38-115">An application that has no application manifest that specifies a requested execution level will be subject to file/registry virtualization under the User Account Control feature in Windows Vista.</span></span> <span data-ttu-id="cae38-116">Aby uzyskać więcej informacji o wirtualizacji, zobacz [wdrażania ClickOnce w systemie Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span><span class="sxs-lookup"><span data-stu-id="cae38-116">For more information about virtualization, see [ClickOnce Deployment on Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span></span>  
  
 <span data-ttu-id="cae38-117">Aplikacji będą podlegać wirtualizacji, jeśli jest spełniony jeden z następujących warunków:</span><span class="sxs-lookup"><span data-stu-id="cae38-117">Your application will be subject to virtualization if either of the following conditions is true:</span></span>  
  
1.  <span data-ttu-id="cae38-118">Możesz użyć `-nowin32manifest` opcja i nie udostępniają manifestu w kolejnym kroku kompilacji lub jako część pliku zasobów systemu Windows (.res) przy użyciu `-win32resource` opcji.</span><span class="sxs-lookup"><span data-stu-id="cae38-118">You use the `-nowin32manifest` option and you do not provide a manifest in a later build step or as part of a Windows Resource (.res) file by using the `-win32resource` option.</span></span>  
  
2.  <span data-ttu-id="cae38-119">Musisz podać niestandardowy manifest, która nie określa wymagany poziom wykonywania.</span><span class="sxs-lookup"><span data-stu-id="cae38-119">You provide a custom manifest that does not specify a requested execution level.</span></span>  
  
 [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]<span data-ttu-id="cae38-120"> tworzy domyślny plik .manifest i zapisuje go w katalogach debug i release obok pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="cae38-120"> creates a default .manifest file and stores it in the debug and release directories alongside the executable file.</span></span> <span data-ttu-id="cae38-121">Umożliwia wyświetlenie i edytowanie pliku app.manifest domyślny, klikając **ustawienia kontroli konta użytkownika widoku** na **aplikacji** kartę w Projektancie projektu.</span><span class="sxs-lookup"><span data-stu-id="cae38-121">You can view or edit the default app.manifest file by clicking **View UAC Settings** on the **Application** tab in the Project Designer.</span></span> <span data-ttu-id="cae38-122">Aby uzyskać więcej informacji, zobacz [strona aplikacji, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="cae38-122">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
 <span data-ttu-id="cae38-123">Możesz podać manifest aplikacji jako niestandardowy krok kompilacji po lub w ramach plik zasobów Win32 przy użyciu `-nowin32manifest` opcji.</span><span class="sxs-lookup"><span data-stu-id="cae38-123">You can provide the application manifest as a custom post-build step or as part of a Win32 resource file by using the `-nowin32manifest` option.</span></span> <span data-ttu-id="cae38-124">Tej samej opcji należy użyć, jeśli aplikacja ma być może ulec plików lub rejestrze wirtualizacji w systemie Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="cae38-124">Use that same option if you want your application to be subject to file or registry virtualization on Windows Vista.</span></span> <span data-ttu-id="cae38-125">Uniemożliwi to kompilatora tworzenie i osadzanie manifestu domyślnej w pliku PE.</span><span class="sxs-lookup"><span data-stu-id="cae38-125">This will prevent the compiler from creating and embedding a default manifest in the PE file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cae38-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="cae38-126">Example</span></span>  
 <span data-ttu-id="cae38-127">W poniższym przykładzie przedstawiono manifest domyślny, że kompilator Visual Basic wstawia do PE.</span><span class="sxs-lookup"><span data-stu-id="cae38-127">The following example shows the default manifest that the Visual Basic compiler inserts into a PE.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cae38-128">Nazwa standardowa aplikacji MyApplication.app zostanie wstawiona do manifestu XML.</span><span class="sxs-lookup"><span data-stu-id="cae38-128">The compiler inserts a standard application name MyApplication.app into the manifest XML.</span></span> <span data-ttu-id="cae38-129">To obejście, aby umożliwić aplikacji do uruchamiania w systemie Windows Server 2003 Service Pack 3.</span><span class="sxs-lookup"><span data-stu-id="cae38-129">This is a workaround to enable applications to run on Windows Server 2003 Service Pack 3.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
  <assemblyIdentity version="1.0.0.0" name="MyApplication.app"/>  
  <trustInfo xmlns="urn:schemas-microsoft-com:asm.v2">  
    <security>  
      <requestedPrivileges xmlns="urn:schemas-microsoft-com:asm.v3">  
        <requestedExecutionLevel level="asInvoker"/>  
      </requestedPrivileges>  
    </security>  
  </trustInfo>  
</assembly>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cae38-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cae38-130">See Also</span></span>  
 [<span data-ttu-id="cae38-131">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cae38-131">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="cae38-132">-nowin32manifest (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cae38-132">-nowin32manifest (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)
