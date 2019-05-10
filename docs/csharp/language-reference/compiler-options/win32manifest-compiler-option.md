---
title: -win32manifest (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /win32manifest
helpviewer_keywords:
- /win32manifest compiler option [C#]
- win32manifest compiler option [C#]
- -win32manifest compiler option [C#]
ms.assetid: 9460ea1b-6c9f-44b8-8f73-301b30a01de1
ms.openlocfilehash: 4cdab8c818cf3278c829e2486e89be32bb4ba277
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593048"
---
# <a name="-win32manifest-c-compiler-options"></a><span data-ttu-id="f8c3d-102">-win32manifest (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="f8c3d-102">-win32manifest (C# Compiler Options)</span></span>
<span data-ttu-id="f8c3d-103">Użyj **-win32manifest** opcję, aby określić zdefiniowanych przez użytkownika aplikacji plik manifestu Win32 osadzanego do projektu przenośnych plików wykonywalnych (PE) pliku.</span><span class="sxs-lookup"><span data-stu-id="f8c3d-103">Use the **-win32manifest** option to specify a user-defined Win32 application manifest file to be embedded into a project's portable executable (PE) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8c3d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f8c3d-104">Syntax</span></span>  
  
```console  
-win32manifest: filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="f8c3d-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="f8c3d-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="f8c3d-106">Nazwę i lokalizację niestandardowego pliku manifestu.</span><span class="sxs-lookup"><span data-stu-id="f8c3d-106">The name and location of the custom manifest file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f8c3d-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f8c3d-107">Remarks</span></span>  
 <span data-ttu-id="f8c3d-108">Domyślnie kompilator Visual C# osadza manifest aplikacji, która określa wymagany poziom wykonywania programu "asInvoker".</span><span class="sxs-lookup"><span data-stu-id="f8c3d-108">By default, the Visual C# compiler embeds an application manifest that specifies a requested execution level of "asInvoker."</span></span> <span data-ttu-id="f8c3d-109">Tworzy manifest w tym samym folderze, w którym plik wykonywalny został opracowany, zwykle bin\Debug lub bin\Release folderu, gdy używasz programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f8c3d-109">It creates the manifest in the same folder in which the executable is built, typically the bin\Debug or bin\Release folder when you use Visual Studio.</span></span> <span data-ttu-id="f8c3d-110">Jeśli chcesz podać niestandardowy manifest, na przykład aby określić wymagany poziom wykonywania "highestAvailable" lub "requireAdministrator", należy użyć tę opcję, aby określić nazwę pliku.</span><span class="sxs-lookup"><span data-stu-id="f8c3d-110">If you want to supply a custom manifest, for example to specify a requested execution level of "highestAvailable" or "requireAdministrator," use this option to specify the name of the file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f8c3d-111">Ta opcja i [-win32res (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) opcji wzajemnie się wykluczają.</span><span class="sxs-lookup"><span data-stu-id="f8c3d-111">This option and the [-win32res (C# Compiler Options)](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) option are mutually exclusive.</span></span> <span data-ttu-id="f8c3d-112">Jeśli spróbujesz użyć obu opcji w tym samym wierszu polecenia zostanie wyświetlony błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="f8c3d-112">If you try to use both options in the same command line you will get a build error.</span></span>  
  
 <span data-ttu-id="f8c3d-113">Aplikacja, która ma żadna aplikacja manifestu, który określa, że będzie wymagany poziom wykonywania pliku/rejestru wirtualizacji w ramach tej funkcji Kontrola konta użytkownika w programie Windows.</span><span class="sxs-lookup"><span data-stu-id="f8c3d-113">An application that has no application manifest that specifies a requested execution level will be subject to file/registry virtualization under the User Account Control feature in Windows.</span></span> <span data-ttu-id="f8c3d-114">Aby uzyskać więcej informacji, zobacz [Kontrola konta użytkownika](/windows/access-protection/user-account-control/user-account-control-overview).</span><span class="sxs-lookup"><span data-stu-id="f8c3d-114">For more information, see [User Account Control](/windows/access-protection/user-account-control/user-account-control-overview).</span></span>  
  
 <span data-ttu-id="f8c3d-115">Twoja aplikacja będzie wirtualizacji, jeśli jest spełniony jeden z następujących warunków:</span><span class="sxs-lookup"><span data-stu-id="f8c3d-115">Your application will be subject to virtualization if either of these conditions is true:</span></span>  
  
- <span data-ttu-id="f8c3d-116">Możesz użyć **-nowin32manifest** opcji nie są oferowane manifest na późniejszym etapie kompilacji lub jako część pliku Windows zasobów (.res) przy użyciu **-win32res** opcji.</span><span class="sxs-lookup"><span data-stu-id="f8c3d-116">You use the **-nowin32manifest** option and you do not provide a manifest in a later build step or as part of a Windows Resource (.res) file by using the **-win32res** option.</span></span>  
  
- <span data-ttu-id="f8c3d-117">Możesz podać niestandardowy manifest, który nie określa wymagany poziom wykonywania.</span><span class="sxs-lookup"><span data-stu-id="f8c3d-117">You provide a custom manifest that does not specify a requested execution level.</span></span>  
  
 <span data-ttu-id="f8c3d-118">Visual Studio tworzy domyślny plik .manifest i zapisuje go w katalogach debug i release, wraz z pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="f8c3d-118">Visual Studio creates a default .manifest file and stores it in the debug and release directories alongside the executable file.</span></span> <span data-ttu-id="f8c3d-119">Aby dodać niestandardowy manifest, tworząc go w dowolnym edytorze tekstów, a następnie dodanie go do projektu.</span><span class="sxs-lookup"><span data-stu-id="f8c3d-119">You can add a custom manifest by creating one in any text editor and then adding the file to the project.</span></span> <span data-ttu-id="f8c3d-120">Alternatywnie możesz kliknąć prawym przyciskiem myszy **projektu** ikonę **Eksploratora rozwiązań**, kliknij przycisk **Dodaj nowy element**, a następnie kliknij przycisk **Plikmanifestuaplikacji**.</span><span class="sxs-lookup"><span data-stu-id="f8c3d-120">Alternatively, you can right-click the **Project** icon in **Solution Explorer**, click **Add New Item**, and then click **Application Manifest File**.</span></span> <span data-ttu-id="f8c3d-121">Po dodaniu nowego lub istniejącego pliku manifestu, pojawi się na **manifestu** listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="f8c3d-121">After you have added your new or existing manifest file, it will appear in the **Manifest** drop down list.</span></span> <span data-ttu-id="f8c3d-122">Aby uzyskać więcej informacji, zobacz [strona aplikacji, Projektant projektu (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="f8c3d-122">For more information, see [Application Page, Project Designer (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).</span></span>  
  
 <span data-ttu-id="f8c3d-123">Możesz podać w manifeście aplikacji jako niestandardowy krok po kompilacji lub jako część pliku zasobów Win32 przy użyciu [-nowin32manifest (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md) opcji.</span><span class="sxs-lookup"><span data-stu-id="f8c3d-123">You can provide the application manifest as a custom post-build step or as part of a Win32 resource file by using the [-nowin32manifest (C# Compiler Options)](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md) option.</span></span> <span data-ttu-id="f8c3d-124">Jeśli chcesz, aby aplikacja ma być wirtualizacji plików i rejestru w systemie Windows Vista, należy użyć tej samej opcji.</span><span class="sxs-lookup"><span data-stu-id="f8c3d-124">Use that same option if you want your application to be subject to file or registry virtualization on Windows Vista.</span></span> <span data-ttu-id="f8c3d-125">Uniemożliwi to kompilatora od utworzenia i osadzanie domyślny manifest w przenośny plik wykonywalny (PE).</span><span class="sxs-lookup"><span data-stu-id="f8c3d-125">This will prevent the compiler from creating and embedding a default manifest in the portable executable (PE) file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8c3d-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="f8c3d-126">Example</span></span>  
 <span data-ttu-id="f8c3d-127">Poniższy kod przedstawia domyślny manifest, kompilator Visual C#, wstawia w Wykonywalnym.</span><span class="sxs-lookup"><span data-stu-id="f8c3d-127">The following example shows the default manifest that the Visual C# compiler inserts into a PE.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f8c3d-128">Kompilator Wstawia nazwę standardowej aplikacji "MyApplication.app" do pliku xml.</span><span class="sxs-lookup"><span data-stu-id="f8c3d-128">The compiler inserts a standard application name " MyApplication.app " into the xml.</span></span> <span data-ttu-id="f8c3d-129">To obejście, aby umożliwić aplikacji do uruchamiania w systemie Windows Server 2003 z dodatkiem Service Pack 3.</span><span class="sxs-lookup"><span data-stu-id="f8c3d-129">This is a workaround to enable applications to run on Windows Server 2003 Service Pack 3.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f8c3d-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f8c3d-130">See also</span></span>

- [<span data-ttu-id="f8c3d-131">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="f8c3d-131">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="f8c3d-132">-nowin32manifest (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="f8c3d-132">-nowin32manifest (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md)
- [<span data-ttu-id="f8c3d-133">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="f8c3d-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
