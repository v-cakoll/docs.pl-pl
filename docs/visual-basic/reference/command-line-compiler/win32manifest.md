---
title: -win32manifest (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /win32manifest compiler option [Visual Basic]
- win32manifest compiler option [Visual Basic]
- -win32manifest compiler option [Visual Basic]
ms.assetid: 9e3191b4-90db-41c8-966a-28036fd20005
ms.openlocfilehash: 15fe62457ed11ffcd08a1db3aa8be57080f22869
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59300801"
---
# <a name="-win32manifest-visual-basic"></a><span data-ttu-id="dc183-102">-win32manifest (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dc183-102">-win32manifest (Visual Basic)</span></span>
<span data-ttu-id="dc183-103">Identyfikuje użytkownika aplikacji plik manifestu Win32 osadzanego do projektu przenośnych plików wykonywalnych (PE) pliku.</span><span class="sxs-lookup"><span data-stu-id="dc183-103">Identifies a user-defined Win32 application manifest file to be embedded into a project's portable executable (PE) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc183-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dc183-104">Syntax</span></span>  
  
```  
-win32manifest: fileName  
```  
  
## <a name="arguments"></a><span data-ttu-id="dc183-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="dc183-105">Arguments</span></span>  
  
|<span data-ttu-id="dc183-106">Termin</span><span class="sxs-lookup"><span data-stu-id="dc183-106">Term</span></span>|<span data-ttu-id="dc183-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="dc183-107">Definition</span></span>|  
|---|---|  
|`fileName`|<span data-ttu-id="dc183-108">Ścieżka niestandardowego pliku manifestu.</span><span class="sxs-lookup"><span data-stu-id="dc183-108">The path of the custom manifest file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dc183-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dc183-109">Remarks</span></span>  
 <span data-ttu-id="dc183-110">Domyślnie kompilator języka Visual Basic osadza manifest aplikacji, która określa wymagany poziom wykonywania programu asInvoker.</span><span class="sxs-lookup"><span data-stu-id="dc183-110">By default, the Visual Basic compiler embeds an application manifest that specifies a requested execution level of asInvoker.</span></span> <span data-ttu-id="dc183-111">Tworzy manifest w tym samym folderze, w którym plik wykonywalny został opracowany, zwykle bin\Debug lub bin\Release folderu, gdy używasz programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="dc183-111">It creates the manifest in the same folder in which the executable file is built, typically the bin\Debug or bin\Release folder when you use Visual Studio.</span></span> <span data-ttu-id="dc183-112">Jeśli chcesz podać niestandardowy manifest, na przykład aby określić wymagany poziom wykonywania highestAvailable lub requireAdministrator, należy użyć tę opcję, aby określić nazwę pliku.</span><span class="sxs-lookup"><span data-stu-id="dc183-112">If you want to supply a custom manifest, for example to specify a requested execution level of highestAvailable or requireAdministrator, use this option to specify the name of the file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dc183-113">Ta opcja i [-win32resource —](../../../visual-basic/reference/command-line-compiler/win32resource.md) opcji wzajemnie się wykluczają.</span><span class="sxs-lookup"><span data-stu-id="dc183-113">This option and the [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) option are mutually exclusive.</span></span> <span data-ttu-id="dc183-114">Jeśli spróbujesz użyć obu opcji w tym samym wierszu polecenia, zostanie wyświetlony błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="dc183-114">If you try to use both options in the same command line, you will get a build error.</span></span>  
  
 <span data-ttu-id="dc183-115">Aplikacja, która ma żadna aplikacja manifestu, który określa, że będzie wymagany poziom wykonywania pliku/rejestru wirtualizacji w ramach funkcji kontroli konta użytkownika w Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="dc183-115">An application that has no application manifest that specifies a requested execution level will be subject to file/registry virtualization under the User Account Control feature in Windows Vista.</span></span> <span data-ttu-id="dc183-116">Aby uzyskać więcej informacji na temat wirtualizacji, zobacz [wdrażania ClickOnce w systemie Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span><span class="sxs-lookup"><span data-stu-id="dc183-116">For more information about virtualization, see [ClickOnce Deployment on Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span></span>  
  
 <span data-ttu-id="dc183-117">Twoja aplikacja będzie wirtualizacji, jeśli jest spełniony jeden z następujących warunków:</span><span class="sxs-lookup"><span data-stu-id="dc183-117">Your application will be subject to virtualization if either of the following conditions is true:</span></span>  
  
1. <span data-ttu-id="dc183-118">Możesz użyć `-nowin32manifest` opcji nie są oferowane manifest na późniejszym etapie kompilacji lub jako część pliku Windows zasobów (.res) przy użyciu `-win32resource` opcji.</span><span class="sxs-lookup"><span data-stu-id="dc183-118">You use the `-nowin32manifest` option and you do not provide a manifest in a later build step or as part of a Windows Resource (.res) file by using the `-win32resource` option.</span></span>  
  
2. <span data-ttu-id="dc183-119">Możesz podać niestandardowy manifest, który nie określa wymagany poziom wykonywania.</span><span class="sxs-lookup"><span data-stu-id="dc183-119">You provide a custom manifest that does not specify a requested execution level.</span></span>  
  
 <span data-ttu-id="dc183-120">Visual Studio tworzy domyślny plik .manifest i zapisuje go w katalogach debug i release, wraz z pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="dc183-120">Visual Studio creates a default .manifest file and stores it in the debug and release directories alongside the executable file.</span></span> <span data-ttu-id="dc183-121">Możesz wyświetlić lub edytować plik app.manifest domyślny, klikając **ustawienia funkcji Kontrola konta użytkownika widoku** na **aplikacji** kartę w Projektancie projektu.</span><span class="sxs-lookup"><span data-stu-id="dc183-121">You can view or edit the default app.manifest file by clicking **View UAC Settings** on the **Application** tab in the Project Designer.</span></span> <span data-ttu-id="dc183-122">Aby uzyskać więcej informacji, zobacz [strona aplikacji, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="dc183-122">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
 <span data-ttu-id="dc183-123">Możesz podać w manifeście aplikacji jako niestandardowy krok po kompilacji lub jako część pliku zasobów Win32 przy użyciu `-nowin32manifest` opcji.</span><span class="sxs-lookup"><span data-stu-id="dc183-123">You can provide the application manifest as a custom post-build step or as part of a Win32 resource file by using the `-nowin32manifest` option.</span></span> <span data-ttu-id="dc183-124">Jeśli chcesz, aby aplikacja ma być wirtualizacji plików i rejestru w systemie Windows Vista, należy użyć tej samej opcji.</span><span class="sxs-lookup"><span data-stu-id="dc183-124">Use that same option if you want your application to be subject to file or registry virtualization on Windows Vista.</span></span> <span data-ttu-id="dc183-125">Uniemożliwi to kompilatora od utworzenia i osadzanie manifestu domyślnej w pliku PE.</span><span class="sxs-lookup"><span data-stu-id="dc183-125">This will prevent the compiler from creating and embedding a default manifest in the PE file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc183-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="dc183-126">Example</span></span>  
 <span data-ttu-id="dc183-127">Poniższy kod przedstawia domyślny manifest, kompilator Visual Basic wstawia do PE.</span><span class="sxs-lookup"><span data-stu-id="dc183-127">The following example shows the default manifest that the Visual Basic compiler inserts into a PE.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dc183-128">Kompilator Wstawia nazwę standardowej aplikacji MyApplication.app do manifestu XML.</span><span class="sxs-lookup"><span data-stu-id="dc183-128">The compiler inserts a standard application name MyApplication.app into the manifest XML.</span></span> <span data-ttu-id="dc183-129">To obejście, aby umożliwić aplikacji do uruchamiania w systemie Windows Server 2003 z dodatkiem Service Pack 3.</span><span class="sxs-lookup"><span data-stu-id="dc183-129">This is a workaround to enable applications to run on Windows Server 2003 Service Pack 3.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dc183-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dc183-130">See also</span></span>

- [<span data-ttu-id="dc183-131">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dc183-131">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="dc183-132">-nowin32manifest (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dc183-132">-nowin32manifest (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)
