---
title: -win32manifest
ms.date: 03/13/2018
helpviewer_keywords:
- /win32manifest compiler option [Visual Basic]
- win32manifest compiler option [Visual Basic]
- -win32manifest compiler option [Visual Basic]
ms.assetid: 9e3191b4-90db-41c8-966a-28036fd20005
ms.openlocfilehash: cef1e6c19e7fdd6fc9f42c8fc36008314ea80a80
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349132"
---
# <a name="-win32manifest-visual-basic"></a><span data-ttu-id="cbb37-102">-WIN32MANIFEST (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cbb37-102">-win32manifest (Visual Basic)</span></span>
<span data-ttu-id="cbb37-103">Identyfikuje zdefiniowany przez użytkownika plik manifestu aplikacji Win32, który ma zostać osadzony w przenośnym pliku wykonywalnym (PE) projektu.</span><span class="sxs-lookup"><span data-stu-id="cbb37-103">Identifies a user-defined Win32 application manifest file to be embedded into a project's portable executable (PE) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbb37-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cbb37-104">Syntax</span></span>  
  
```console  
-win32manifest: fileName  
```  
  
## <a name="arguments"></a><span data-ttu-id="cbb37-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="cbb37-105">Arguments</span></span>  
  
|<span data-ttu-id="cbb37-106">Termin</span><span class="sxs-lookup"><span data-stu-id="cbb37-106">Term</span></span>|<span data-ttu-id="cbb37-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="cbb37-107">Definition</span></span>|  
|---|---|  
|`fileName`|<span data-ttu-id="cbb37-108">Ścieżka pliku manifestu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="cbb37-108">The path of the custom manifest file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cbb37-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cbb37-109">Remarks</span></span>  
 <span data-ttu-id="cbb37-110">Domyślnie kompilator Visual Basic osadza manifest aplikacji, który określa żądany poziom wykonywania jako źródło.</span><span class="sxs-lookup"><span data-stu-id="cbb37-110">By default, the Visual Basic compiler embeds an application manifest that specifies a requested execution level of asInvoker.</span></span> <span data-ttu-id="cbb37-111">Tworzy manifest w tym samym folderze, w którym plik wykonywalny jest kompilowany, zazwyczaj folder bin\Debug lub bin\Release w przypadku korzystania z programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cbb37-111">It creates the manifest in the same folder in which the executable file is built, typically the bin\Debug or bin\Release folder when you use Visual Studio.</span></span> <span data-ttu-id="cbb37-112">Jeśli chcesz podać niestandardowy manifest, na przykład aby określić żądany poziom wykonywania najwyższe dostępne lub wymaga administratora, Użyj tej opcji, aby określić nazwę pliku.</span><span class="sxs-lookup"><span data-stu-id="cbb37-112">If you want to supply a custom manifest, for example to specify a requested execution level of highestAvailable or requireAdministrator, use this option to specify the name of the file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cbb37-113">Ta opcja i opcja [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) wykluczają się wzajemnie.</span><span class="sxs-lookup"><span data-stu-id="cbb37-113">This option and the [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) option are mutually exclusive.</span></span> <span data-ttu-id="cbb37-114">Jeśli spróbujesz użyć obu opcji w tym samym wierszu polecenia, zostanie wyświetlony błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="cbb37-114">If you try to use both options in the same command line, you will get a build error.</span></span>  
  
 <span data-ttu-id="cbb37-115">Aplikacja, która nie ma manifestu aplikacji, która określa żądany poziom wykonania, będzie podlegała wirtualizacji plików/rejestru w ramach funkcji kontroli konta użytkownika w systemie Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="cbb37-115">An application that has no application manifest that specifies a requested execution level will be subject to file/registry virtualization under the User Account Control feature in Windows Vista.</span></span> <span data-ttu-id="cbb37-116">Aby uzyskać więcej informacji na temat wirtualizacji, zobacz [wdrażanie ClickOnce w systemie Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span><span class="sxs-lookup"><span data-stu-id="cbb37-116">For more information about virtualization, see [ClickOnce Deployment on Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span></span>  
  
 <span data-ttu-id="cbb37-117">Aplikacja będzie podlegać wirtualizacji, jeśli spełniony jest jeden z następujących warunków:</span><span class="sxs-lookup"><span data-stu-id="cbb37-117">Your application will be subject to virtualization if either of the following conditions is true:</span></span>  
  
1. <span data-ttu-id="cbb37-118">Użyj `-nowin32manifest` opcji i nie udostępniaj manifestu w późniejszym kroku kompilacji lub jako część pliku zasobów systemu Windows (. res) przy użyciu `-win32resource` opcji.</span><span class="sxs-lookup"><span data-stu-id="cbb37-118">You use the `-nowin32manifest` option and you do not provide a manifest in a later build step or as part of a Windows Resource (.res) file by using the `-win32resource` option.</span></span>  
  
2. <span data-ttu-id="cbb37-119">Należy podać niestandardowy manifest, który nie określa żądanego poziomu wykonania.</span><span class="sxs-lookup"><span data-stu-id="cbb37-119">You provide a custom manifest that does not specify a requested execution level.</span></span>  
  
 <span data-ttu-id="cbb37-120">Program Visual Studio tworzy domyślny plik. manifest i zapisuje go w katalogach debugowania i wydań obok pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="cbb37-120">Visual Studio creates a default .manifest file and stores it in the debug and release directories alongside the executable file.</span></span> <span data-ttu-id="cbb37-121">Możesz wyświetlić lub edytować domyślny plik aplikacji. manifest, klikając pozycję **Wyświetl ustawienia kontroli konta użytkownika** na karcie **aplikacja** w projektancie projektu.</span><span class="sxs-lookup"><span data-stu-id="cbb37-121">You can view or edit the default app.manifest file by clicking **View UAC Settings** on the **Application** tab in the Project Designer.</span></span> <span data-ttu-id="cbb37-122">Aby uzyskać więcej informacji, zobacz [Strona aplikacji, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="cbb37-122">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
 <span data-ttu-id="cbb37-123">Można dostarczyć manifest aplikacji jako niestandardowy krok po kompilacji lub jako część pliku zasobów Win32 przy użyciu `-nowin32manifest` opcji.</span><span class="sxs-lookup"><span data-stu-id="cbb37-123">You can provide the application manifest as a custom post-build step or as part of a Win32 resource file by using the `-nowin32manifest` option.</span></span> <span data-ttu-id="cbb37-124">Użyj tej samej opcji, jeśli chcesz, aby aplikacja podlegała wirtualizacji plików lub rejestru w systemie Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="cbb37-124">Use that same option if you want your application to be subject to file or registry virtualization on Windows Vista.</span></span> <span data-ttu-id="cbb37-125">Uniemożliwi to kompilatorowi utworzenie i osadzenie domyślnego manifestu w pliku PE.</span><span class="sxs-lookup"><span data-stu-id="cbb37-125">This will prevent the compiler from creating and embedding a default manifest in the PE file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cbb37-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="cbb37-126">Example</span></span>  
 <span data-ttu-id="cbb37-127">Poniższy przykład pokazuje domyślny manifest, który kompilator Visual Basic wstawia do PE.</span><span class="sxs-lookup"><span data-stu-id="cbb37-127">The following example shows the default manifest that the Visual Basic compiler inserts into a PE.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cbb37-128">Kompilator wstawia standardową nazwę aplikacji aplikacja. app do manifestu XML.</span><span class="sxs-lookup"><span data-stu-id="cbb37-128">The compiler inserts a standard application name MyApplication.app into the manifest XML.</span></span> <span data-ttu-id="cbb37-129">Jest to obejście, aby umożliwić uruchamianie aplikacji w systemie Windows Server 2003 z dodatkiem Service Pack 3.</span><span class="sxs-lookup"><span data-stu-id="cbb37-129">This is a workaround to enable applications to run on Windows Server 2003 Service Pack 3.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cbb37-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cbb37-130">See also</span></span>

- [<span data-ttu-id="cbb37-131">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cbb37-131">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="cbb37-132">-nowin32manifest (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cbb37-132">-nowin32manifest (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)
