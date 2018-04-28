---
title: -win32manifest (opcje kompilatora C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /win32manifest
helpviewer_keywords:
- /win32manifest compiler option [C#]
- win32manifest compiler option [C#]
- -win32manifest compiler option [C#]
ms.assetid: 9460ea1b-6c9f-44b8-8f73-301b30a01de1
caps.latest.revision: 13
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8631477f7067870ca1d8a62513489cdbbbe43f33
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="-win32manifest-c-compiler-options"></a><span data-ttu-id="bc3e9-102">-win32manifest (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="bc3e9-102">-win32manifest (C# Compiler Options)</span></span>
<span data-ttu-id="bc3e9-103">Użyj **-win32manifest** opcję, aby określić użytkownika aplikacji plik manifestu Win32 do osadzenia pliku przenośny plik wykonywalny (PE) projektu.</span><span class="sxs-lookup"><span data-stu-id="bc3e9-103">Use the **-win32manifest** option to specify a user-defined Win32 application manifest file to be embedded into a project's portable executable (PE) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc3e9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bc3e9-104">Syntax</span></span>  
  
```console  
-win32manifest: filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="bc3e9-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="bc3e9-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="bc3e9-106">Nazwę i lokalizację niestandardowego pliku manifestu.</span><span class="sxs-lookup"><span data-stu-id="bc3e9-106">The name and location of the custom manifest file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bc3e9-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bc3e9-107">Remarks</span></span>  
 <span data-ttu-id="bc3e9-108">Domyślnie kompilator Visual C# osadza manifest aplikacji, która określa wymagany poziom wykonywania elementu "asInvoker".</span><span class="sxs-lookup"><span data-stu-id="bc3e9-108">By default, the Visual C# compiler embeds an application manifest that specifies a requested execution level of "asInvoker."</span></span> <span data-ttu-id="bc3e9-109">W tym samym folderze, w którym plik wykonywalny jest wbudowana, zwykle folderu bin\Debug lub bin\Release, gdy używasz programu Visual Studio tworzy plik manifestu.</span><span class="sxs-lookup"><span data-stu-id="bc3e9-109">It creates the manifest in the same folder in which the executable is built, typically the bin\Debug or bin\Release folder when you use Visual Studio.</span></span> <span data-ttu-id="bc3e9-110">Jeśli chcesz podać niestandardowy manifest, na przykład określić wymagany poziom wykonywania "highestAvailable" lub "requireAdministrator", ta opcja umożliwia Określ nazwę pliku.</span><span class="sxs-lookup"><span data-stu-id="bc3e9-110">If you want to supply a custom manifest, for example to specify a requested execution level of "highestAvailable" or "requireAdministrator," use this option to specify the name of the file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bc3e9-111">Ta opcja i [-win32res (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) opcji wzajemnie się wykluczają.</span><span class="sxs-lookup"><span data-stu-id="bc3e9-111">This option and the [-win32res (C# Compiler Options)](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) option are mutually exclusive.</span></span> <span data-ttu-id="bc3e9-112">Jeśli spróbujesz użyć obu opcji, w tym samym wierszu polecenia wystąpi błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="bc3e9-112">If you try to use both options in the same command line you will get a build error.</span></span>  
  
 <span data-ttu-id="bc3e9-113">Aplikacja, która nie ma aplikacji manifestu, który określa wymagany poziom wykonywania podlegają wirtualizacji plików/rejestru w funkcji Kontrola konta użytkownika w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="bc3e9-113">An application that has no application manifest that specifies a requested execution level will be subject to file/registry virtualization under the User Account Control feature in Windows.</span></span> <span data-ttu-id="bc3e9-114">Aby uzyskać więcej informacji, zobacz [Kontrola konta użytkownika](/windows/access-protection/user-account-control/user-account-control-overview).</span><span class="sxs-lookup"><span data-stu-id="bc3e9-114">For more information, see [User Account Control](/windows/access-protection/user-account-control/user-account-control-overview).</span></span>  
  
 <span data-ttu-id="bc3e9-115">Aplikacji będą podlegać wirtualizacji, jeśli jest spełniony jeden z następujących warunków:</span><span class="sxs-lookup"><span data-stu-id="bc3e9-115">Your application will be subject to virtualization if either of these conditions is true:</span></span>  
  
-   <span data-ttu-id="bc3e9-116">Możesz użyć **-nowin32manifest** opcja i nie udostępniają manifestu w kolejnym kroku kompilacji lub jako część pliku zasobów systemu Windows (.res) przy użyciu **-win32res** opcji.</span><span class="sxs-lookup"><span data-stu-id="bc3e9-116">You use the **-nowin32manifest** option and you do not provide a manifest in a later build step or as part of a Windows Resource (.res) file by using the **-win32res** option.</span></span>  
  
-   <span data-ttu-id="bc3e9-117">Musisz podać niestandardowy manifest, która nie określa wymagany poziom wykonywania.</span><span class="sxs-lookup"><span data-stu-id="bc3e9-117">You provide a custom manifest that does not specify a requested execution level.</span></span>  
  
 <span data-ttu-id="bc3e9-118">Visual Studio tworzy domyślny plik .manifest i zapisuje go w katalogach debug i release obok pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="bc3e9-118">Visual Studio creates a default .manifest file and stores it in the debug and release directories alongside the executable file.</span></span> <span data-ttu-id="bc3e9-119">Aby dodać niestandardowy manifest, tworząc go w edytorze tekstu, a następnie dodanie go do projektu.</span><span class="sxs-lookup"><span data-stu-id="bc3e9-119">You can add a custom manifest by creating one in any text editor and then adding the file to the project.</span></span> <span data-ttu-id="bc3e9-120">Alternatywnie możesz kliknąć prawym przyciskiem myszy **projektu** ikonę w **Eksploratora rozwiązań**, kliknij przycisk **Dodaj nowy element**, a następnie kliknij przycisk **plikumanifestuaplikacji**.</span><span class="sxs-lookup"><span data-stu-id="bc3e9-120">Alternatively, you can right-click the **Project** icon in **Solution Explorer**, click **Add New Item**, and then click **Application Manifest File**.</span></span> <span data-ttu-id="bc3e9-121">Po dodaniu nowego lub istniejącego pliku manifestu, zostanie wyświetlony na **manifestu** listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="bc3e9-121">After you have added your new or existing manifest file, it will appear in the **Manifest** drop down list.</span></span> <span data-ttu-id="bc3e9-122">Aby uzyskać więcej informacji, zobacz [strona aplikacji, Projektant projektu (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="bc3e9-122">For more information, see [Application Page, Project Designer (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).</span></span>  
  
 <span data-ttu-id="bc3e9-123">Możesz podać manifest aplikacji jako niestandardowy krok kompilacji po lub w ramach plik zasobów Win32 za pomocą [-nowin32manifest (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md) opcji.</span><span class="sxs-lookup"><span data-stu-id="bc3e9-123">You can provide the application manifest as a custom post-build step or as part of a Win32 resource file by using the [-nowin32manifest (C# Compiler Options)](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md) option.</span></span> <span data-ttu-id="bc3e9-124">Tej samej opcji należy użyć, jeśli aplikacja ma być może ulec plików lub rejestrze wirtualizacji w systemie Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="bc3e9-124">Use that same option if you want your application to be subject to file or registry virtualization on Windows Vista.</span></span> <span data-ttu-id="bc3e9-125">Uniemożliwi to kompilatora tworzenie i osadzanie manifestu domyślne w przenośny plik wykonywalny (PE).</span><span class="sxs-lookup"><span data-stu-id="bc3e9-125">This will prevent the compiler from creating and embedding a default manifest in the portable executable (PE) file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc3e9-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="bc3e9-126">Example</span></span>  
 <span data-ttu-id="bc3e9-127">W poniższym przykładzie przedstawiono manifest domyślny, że kompilator Visual C# wstawia do PE.</span><span class="sxs-lookup"><span data-stu-id="bc3e9-127">The following example shows the default manifest that the Visual C# compiler inserts into a PE.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bc3e9-128">Kompilator Wstawia nazwę standardowej aplikacji "MyApplication.app" do pliku xml.</span><span class="sxs-lookup"><span data-stu-id="bc3e9-128">The compiler inserts a standard application name " MyApplication.app " into the xml.</span></span> <span data-ttu-id="bc3e9-129">To obejście, aby umożliwić aplikacji do uruchamiania w systemie Windows Server 2003 Service Pack 3.</span><span class="sxs-lookup"><span data-stu-id="bc3e9-129">This is a workaround to enable applications to run on Windows Server 2003 Service Pack 3.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bc3e9-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bc3e9-130">See Also</span></span>  
 [<span data-ttu-id="bc3e9-131">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="bc3e9-131">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="bc3e9-132">-nowin32manifest (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="bc3e9-132">-nowin32manifest (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md)  
 [<span data-ttu-id="bc3e9-133">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="bc3e9-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
