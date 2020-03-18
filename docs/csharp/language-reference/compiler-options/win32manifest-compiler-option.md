---
title: -win32manifest (Opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /win32manifest
helpviewer_keywords:
- /win32manifest compiler option [C#]
- win32manifest compiler option [C#]
- -win32manifest compiler option [C#]
ms.assetid: 9460ea1b-6c9f-44b8-8f73-301b30a01de1
ms.openlocfilehash: 24677b145974af03e6ddcac1b9bab5907ab70c7b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69924675"
---
# <a name="-win32manifest-c-compiler-options"></a><span data-ttu-id="2d5b2-102">-win32manifest (Opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="2d5b2-102">-win32manifest (C# Compiler Options)</span></span>
<span data-ttu-id="2d5b2-103">Użyj opcji **-win32manifest,** aby określić zdefiniowany przez użytkownika plik manifestu aplikacji Win32, który ma być osadzony w przenośnym pliku wykonywalnym projektu (PE).</span><span class="sxs-lookup"><span data-stu-id="2d5b2-103">Use the **-win32manifest** option to specify a user-defined Win32 application manifest file to be embedded into a project's portable executable (PE) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d5b2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2d5b2-104">Syntax</span></span>  
  
```console  
-win32manifest: filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="2d5b2-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="2d5b2-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="2d5b2-106">Nazwa i lokalizacja pliku manifestu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="2d5b2-106">The name and location of the custom manifest file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d5b2-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2d5b2-107">Remarks</span></span>  
 <span data-ttu-id="2d5b2-108">Domyślnie kompilator języka Visual C# osadza manifest aplikacji, który określa żądany poziom wykonania "asInvoker".</span><span class="sxs-lookup"><span data-stu-id="2d5b2-108">By default, the Visual C# compiler embeds an application manifest that specifies a requested execution level of "asInvoker."</span></span> <span data-ttu-id="2d5b2-109">Tworzy manifest w tym samym folderze, w którym jest zbudowany plik wykonywalny, zazwyczaj bin\Debug lub bin\Release folderu podczas korzystania z programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2d5b2-109">It creates the manifest in the same folder in which the executable is built, typically the bin\Debug or bin\Release folder when you use Visual Studio.</span></span> <span data-ttu-id="2d5b2-110">Jeśli chcesz podać manifest niestandardowy, na przykład, aby określić żądany poziom wykonania "highestAvailable" lub "requireAdministrator", użyj tej opcji, aby określić nazwę pliku.</span><span class="sxs-lookup"><span data-stu-id="2d5b2-110">If you want to supply a custom manifest, for example to specify a requested execution level of "highestAvailable" or "requireAdministrator," use this option to specify the name of the file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2d5b2-111">Ta opcja i [-win32res (Opcje kompilatora C#)](./win32res-compiler-option.md) są wzajemnie się wykluczają.</span><span class="sxs-lookup"><span data-stu-id="2d5b2-111">This option and the [-win32res (C# Compiler Options)](./win32res-compiler-option.md) option are mutually exclusive.</span></span> <span data-ttu-id="2d5b2-112">Jeśli spróbujesz użyć obu opcji w tym samym wierszu polecenia pojawi się błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="2d5b2-112">If you try to use both options in the same command line you will get a build error.</span></span>  
  
 <span data-ttu-id="2d5b2-113">Aplikacja, która nie ma manifestu aplikacji, który określa żądany poziom wykonania będzie podlegać wirtualizacji pliku/rejestru w ramach funkcji Kontrola konta użytkownika w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="2d5b2-113">An application that has no application manifest that specifies a requested execution level will be subject to file/registry virtualization under the User Account Control feature in Windows.</span></span> <span data-ttu-id="2d5b2-114">Aby uzyskać więcej informacji, zobacz [Kontrola konta użytkownika](/windows/access-protection/user-account-control/user-account-control-overview).</span><span class="sxs-lookup"><span data-stu-id="2d5b2-114">For more information, see [User Account Control](/windows/access-protection/user-account-control/user-account-control-overview).</span></span>  
  
 <span data-ttu-id="2d5b2-115">Aplikacja będzie podlegać wirtualizacji, jeśli którykolwiek z tych warunków jest spełniony:</span><span class="sxs-lookup"><span data-stu-id="2d5b2-115">Your application will be subject to virtualization if either of these conditions is true:</span></span>  
  
- <span data-ttu-id="2d5b2-116">Użyj opcji **-nowin32manifest** i nie udostępniasz manifestu w późniejszym kroku kompilacji lub jako część pliku Windows Resource (.res) przy użyciu opcji **-win32res.**</span><span class="sxs-lookup"><span data-stu-id="2d5b2-116">You use the **-nowin32manifest** option and you do not provide a manifest in a later build step or as part of a Windows Resource (.res) file by using the **-win32res** option.</span></span>  
  
- <span data-ttu-id="2d5b2-117">Należy podać manifest niestandardowy, który nie określa żądanego poziomu wykonania.</span><span class="sxs-lookup"><span data-stu-id="2d5b2-117">You provide a custom manifest that does not specify a requested execution level.</span></span>  
  
 <span data-ttu-id="2d5b2-118">Visual Studio tworzy domyślny plik manifestu i przechowuje go w katalogach debugowania i wydania obok pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="2d5b2-118">Visual Studio creates a default .manifest file and stores it in the debug and release directories alongside the executable file.</span></span> <span data-ttu-id="2d5b2-119">Manifest niestandardowy można dodać, tworząc go w dowolnym edytorze tekstu, a następnie dodając plik do projektu.</span><span class="sxs-lookup"><span data-stu-id="2d5b2-119">You can add a custom manifest by creating one in any text editor and then adding the file to the project.</span></span> <span data-ttu-id="2d5b2-120">Alternatywnie można kliknąć prawym przyciskiem myszy ikonę **projektu** w **Eksploratorze rozwiązań,** kliknąć polecenie **Dodaj nowy element**, a następnie kliknąć polecenie Plik **manifestu aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="2d5b2-120">Alternatively, you can right-click the **Project** icon in **Solution Explorer**, click **Add New Item**, and then click **Application Manifest File**.</span></span> <span data-ttu-id="2d5b2-121">Po dodaniu nowego lub istniejącego pliku manifestu pojawi się on na liście rozwijanej **Manifest.**</span><span class="sxs-lookup"><span data-stu-id="2d5b2-121">After you have added your new or existing manifest file, it will appear in the **Manifest** drop down list.</span></span> <span data-ttu-id="2d5b2-122">Aby uzyskać więcej informacji, zobacz [Strona aplikacji, Projektant projektu (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="2d5b2-122">For more information, see [Application Page, Project Designer (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).</span></span>  
  
 <span data-ttu-id="2d5b2-123">Manifest aplikacji można podać jako niestandardowy krok po kompilacji lub jako część pliku zasobów Win32 przy użyciu opcji [-nowin32manifest (C# Compiler Options).](./nowin32manifest-compiler-option.md)</span><span class="sxs-lookup"><span data-stu-id="2d5b2-123">You can provide the application manifest as a custom post-build step or as part of a Win32 resource file by using the [-nowin32manifest (C# Compiler Options)](./nowin32manifest-compiler-option.md) option.</span></span> <span data-ttu-id="2d5b2-124">Użyj tej samej opcji, jeśli chcesz, aby aplikacja podlegała wirtualizacji plików lub rejestru w systemie Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="2d5b2-124">Use that same option if you want your application to be subject to file or registry virtualization on Windows Vista.</span></span> <span data-ttu-id="2d5b2-125">Uniemożliwi to kompilatorowi tworzenie i osadzanie domyślnego manifestu w przenośnym pliku wykonywalnym (PE).</span><span class="sxs-lookup"><span data-stu-id="2d5b2-125">This will prevent the compiler from creating and embedding a default manifest in the portable executable (PE) file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d5b2-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d5b2-126">Example</span></span>  
 <span data-ttu-id="2d5b2-127">W poniższym przykładzie przedstawiono domyślny manifest, który kompilator Visual C# wstawia do programu PE.</span><span class="sxs-lookup"><span data-stu-id="2d5b2-127">The following example shows the default manifest that the Visual C# compiler inserts into a PE.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2d5b2-128">Kompilator wstawia standardową nazwę aplikacji " MyApplication.app " do pliku xml.</span><span class="sxs-lookup"><span data-stu-id="2d5b2-128">The compiler inserts a standard application name " MyApplication.app " into the xml.</span></span> <span data-ttu-id="2d5b2-129">Jest to obejście umożliwiające uruchamianie aplikacji w systemie Windows Server 2003 z dodatkiem Service Pack 3.</span><span class="sxs-lookup"><span data-stu-id="2d5b2-129">This is a workaround to enable applications to run on Windows Server 2003 Service Pack 3.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2d5b2-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d5b2-130">See also</span></span>

- [<span data-ttu-id="2d5b2-131">Opcje kompilatora Języka C#</span><span class="sxs-lookup"><span data-stu-id="2d5b2-131">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="2d5b2-132">-nowin32manifest (Opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="2d5b2-132">-nowin32manifest (C# Compiler Options)</span></span>](./nowin32manifest-compiler-option.md)
- [<span data-ttu-id="2d5b2-133">Zarządzanie właściwościami projektów i rozwiązań</span><span class="sxs-lookup"><span data-stu-id="2d5b2-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
