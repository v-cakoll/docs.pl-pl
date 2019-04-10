---
title: 'Instrukcje: Instalowanie i odinstalowywanie usług Windows'
ms.date: 02/05/2019
helpviewer_keywords:
- Windows Service applications, deploying
- services, uninstalling
- services, installing
- installing Windows Services
- uninstalling applications, apps, Windows services
- installation, Windows services
- uninstalling Windows services
- installutil.exe tool
ms.assetid: c89c5169-f567-4305-9d62-db31a1de5481
author: ghogen
ms.openlocfilehash: 0119fee443aafd1d4215260d2cf42cec9f7eba74
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59308474"
---
# <a name="how-to-install-and-uninstall-windows-services"></a><span data-ttu-id="577bd-102">Instrukcje: Instalowanie i odinstalowywanie usług Windows</span><span class="sxs-lookup"><span data-stu-id="577bd-102">How to: Install and uninstall Windows services</span></span>
<span data-ttu-id="577bd-103">Jeśli opracowujesz usługi Windows za pomocą programu .NET Framework, można szybko zainstalować usługi app service przy użyciu [ *InstallUtil.exe* ](../tools/installutil-exe-installer-tool.md) narzędzie wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="577bd-103">If you’re developing a Windows service with the .NET Framework, you can quickly install your service app by using the [*InstallUtil.exe*](../tools/installutil-exe-installer-tool.md) command-line utility.</span></span> <span data-ttu-id="577bd-104">Deweloperzy, którzy mają być wersji usług Windows, które użytkownicy mogą instalować i odinstalowywać należy używać programu InstallShield.</span><span class="sxs-lookup"><span data-stu-id="577bd-104">Developers who want to release a Windows service that users can install and uninstall should use InstallShield.</span></span> <span data-ttu-id="577bd-105">Aby uzyskać więcej informacji, zobacz [Utwórz pakiet Instalatora (systemu Windows Windows client)](https://docs.microsoft.com/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-client).</span><span class="sxs-lookup"><span data-stu-id="577bd-105">For more information, see [Create an installer package (Windows client)](https://docs.microsoft.com/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-client).</span></span>
  
> [!WARNING]
>  <span data-ttu-id="577bd-106">Jeśli chcesz odinstalować usługę z komputera, nie wykonaj kroki opisane w tym artykule.</span><span class="sxs-lookup"><span data-stu-id="577bd-106">If you want to uninstall a service from your computer, don’t follow the steps in this article.</span></span> <span data-ttu-id="577bd-107">Zamiast tego należy sprawdzić, które pakiety programu lub oprogramowania zainstalowane usługi, a następnie wybierz **aplikacje** w ustawieniach w celu odinstalowania tego programu.</span><span class="sxs-lookup"><span data-stu-id="577bd-107">Instead, find out which program or software package installed the service, and then choose **Apps** in Settings to uninstall that program.</span></span> <span data-ttu-id="577bd-108">Należy pamiętać, że wiele usług są integralną częścią Windows; Jeśli je usuniesz, może spowodować niestabilność systemu.</span><span class="sxs-lookup"><span data-stu-id="577bd-108">Note that many services are integral parts of Windows; if you remove them, you might cause system instability.</span></span>  
  
 <span data-ttu-id="577bd-109">Aby skorzystać z instrukcji w tym artykule, należy najpierw dodać Instalatora usługi do usługi Windows.</span><span class="sxs-lookup"><span data-stu-id="577bd-109">To use the steps in this article, you first need to add a service installer to your Windows service.</span></span> <span data-ttu-id="577bd-110">Aby uzyskać więcej informacji, zobacz [instruktażu: Tworzenie aplikacji usługi Windows](../windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span><span class="sxs-lookup"><span data-stu-id="577bd-110">For more information, see [Walkthrough: Creating a Windows service app](../windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span></span>  
  
 <span data-ttu-id="577bd-111">Projekty usługi Windows nie można uruchomić bezpośrednio ze środowiska projektowego programu Visual Studio, naciskając klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="577bd-111">You can't run Windows service projects directly from the Visual Studio development environment by pressing F5.</span></span> <span data-ttu-id="577bd-112">Zanim będzie można uruchomić projektu, należy zainstalować usługę w projekcie.</span><span class="sxs-lookup"><span data-stu-id="577bd-112">Before you can run the project, you must install the service in the project.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="577bd-113">Możesz użyć **Eksploratora serwera** Aby sprawdzić, czy zostały zainstalowane lub odinstalować usługę.</span><span class="sxs-lookup"><span data-stu-id="577bd-113">You can use **Server Explorer** to verify that you've installed or uninstalled your service.</span></span> <span data-ttu-id="577bd-114">Aby uzyskać więcej informacji, zobacz [sposobie używania Eksploratora serwera w programie Visual Studio](https://support.microsoft.com/help/316649/how-to-use-the-server-explorer-in-visual-studio-net-and-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="577bd-114">For more information, see [How to use Server Explorer in Visual Studio](https://support.microsoft.com/help/316649/how-to-use-the-server-explorer-in-visual-studio-net-and-visual-studio).</span></span>
  
### <a name="install-your-service-manually"></a><span data-ttu-id="577bd-115">Ręcznie zainstalować usługę</span><span class="sxs-lookup"><span data-stu-id="577bd-115">Install your service manually</span></span>  
  
1. <span data-ttu-id="577bd-116">Z **Start** menu, wybierz opcję **programu Visual Studio \< *wersji* >**  katalogu, a następnie wybierz opcję **wiersz polecenia dla deweloperów dla programu VS \< *wersji*>**.</span><span class="sxs-lookup"><span data-stu-id="577bd-116">From the **Start** menu, select the **Visual Studio \<*version*>** directory, then select **Developer Command Prompt for VS \<*version*>**.</span></span>
  
     <span data-ttu-id="577bd-117">Pojawi się wiersz polecenia dla deweloperów programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="577bd-117">The Developer Command Prompt for Visual Studio appears.</span></span> 
  
2. <span data-ttu-id="577bd-118">Dostęp do katalogu, w którym znajduje się plik wykonywalny projektu.</span><span class="sxs-lookup"><span data-stu-id="577bd-118">Access the directory where your project's compiled executable file is located.</span></span>  
  
3. <span data-ttu-id="577bd-119">Uruchom *InstallUtil.exe* polecenia w pliku wykonywalnego jako parametr wiersza z projektem:</span><span class="sxs-lookup"><span data-stu-id="577bd-119">Run *InstallUtil.exe* from the command prompt with your project's executable as a parameter:</span></span>  
  
    ```console
    installutil <yourproject>.exe  
    ```  

     <span data-ttu-id="577bd-120">Jeśli używasz wiersz polecenia programisty dla programu Visual Studio *InstallUtil.exe* powinny znajdować się w ścieżce systemowej.</span><span class="sxs-lookup"><span data-stu-id="577bd-120">If you’re using the Developer Command Prompt for Visual Studio, *InstallUtil.exe* should be on the system path.</span></span> <span data-ttu-id="577bd-121">W przeciwnym razie możesz dodać go do ścieżki lub wywoływać go za pomocą w pełni kwalifikowanej ścieżki.</span><span class="sxs-lookup"><span data-stu-id="577bd-121">Otherwise, you can add it to the path, or use the fully qualified path to invoke it.</span></span> <span data-ttu-id="577bd-122">To narzędzie jest instalowane z .NET Framework w *% WINDIR%\Microsoft.NET\Framework[64]\\< framework_version >*.</span><span class="sxs-lookup"><span data-stu-id="577bd-122">This tool is installed with the .NET Framework in *%WINDIR%\Microsoft.NET\Framework[64]\\<framework_version>*.</span></span>
     
     <span data-ttu-id="577bd-123">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="577bd-123">For example:</span></span>
     - <span data-ttu-id="577bd-124">W przypadku 32-bitowej wersji programu .NET Framework 4 lub 4.5 lub nowszy, jeśli jest katalogu instalacji Windows *C:\Windows*, domyślna ścieżka to *C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*.</span><span class="sxs-lookup"><span data-stu-id="577bd-124">For the 32-bit version of the .NET Framework 4 or 4.5 and later, if your Windows installation directory is *C:\Windows*, the default path is *C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*.</span></span>
     - <span data-ttu-id="577bd-125">Dla 64-bitowej wersji programu .NET Framework 4 lub 4.5 lub nowszy, domyślna ścieżka to *C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.</span><span class="sxs-lookup"><span data-stu-id="577bd-125">For the 64-bit version of the .NET Framework 4 or 4.5 and later, the default path is *C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.</span></span>
  
### <a name="uninstall-your-service-manually"></a><span data-ttu-id="577bd-126">Ręcznie odinstalować usługę</span><span class="sxs-lookup"><span data-stu-id="577bd-126">Uninstall your service manually</span></span>  
  
1. <span data-ttu-id="577bd-127">Z **Start** menu, wybierz opcję **programu Visual Studio \< *wersji* >**  katalogu, a następnie wybierz opcję **wiersz polecenia dla deweloperów dla programu VS \< *wersji*>**.</span><span class="sxs-lookup"><span data-stu-id="577bd-127">From the **Start** menu, select the **Visual Studio \<*version*>** directory, then select **Developer Command Prompt for VS \<*version*>**.</span></span>
  
     <span data-ttu-id="577bd-128">Pojawi się wiersz polecenia dla deweloperów programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="577bd-128">The Developer Command Prompt for Visual Studio appears.</span></span>  
  
2. <span data-ttu-id="577bd-129">Uruchom *InstallUtil.exe* w wierszu polecenia z danymi wyjściowymi projektu jako parametr:</span><span class="sxs-lookup"><span data-stu-id="577bd-129">Run *InstallUtil.exe* from the command prompt with your project's output as a parameter:</span></span>  
  
    ```console  
    installutil /u <yourproject>.exe  
    ```  
  
3. <span data-ttu-id="577bd-130">Po usunięciu pliku wykonywalnego dla usługi usługi znajdować się w rejestrze.</span><span class="sxs-lookup"><span data-stu-id="577bd-130">After the executable for a service is deleted, the service might still be present in the registry.</span></span> <span data-ttu-id="577bd-131">Jeśli tak jest rzeczywiście, użyj polecenia [sc delete](/windows-server/administration/windows-commands/sc-delete) można usunąć wpisu usługi z rejestru.</span><span class="sxs-lookup"><span data-stu-id="577bd-131">If that's the case, use the command [sc delete](/windows-server/administration/windows-commands/sc-delete) to remove the entry for the service from the registry.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="577bd-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="577bd-132">See also</span></span>

- [<span data-ttu-id="577bd-133">Wprowadzenie do aplikacji usług Windows</span><span class="sxs-lookup"><span data-stu-id="577bd-133">Introduction to Windows service applications</span></span>](../windows-services/introduction-to-windows-service-applications.md)
- [<span data-ttu-id="577bd-134">Instrukcje: Tworzenie usług Windows</span><span class="sxs-lookup"><span data-stu-id="577bd-134">How to: Create Windows services</span></span>](../windows-services/how-to-create-windows-services.md)
- [<span data-ttu-id="577bd-135">Instrukcje: Dodawanie instalatorów od aplikacji usług</span><span class="sxs-lookup"><span data-stu-id="577bd-135">How to: Add installers to your service application</span></span>](../windows-services/how-to-add-installers-to-your-service-application.md)
- [<span data-ttu-id="577bd-136">Installutil.exe (Narzędzie Instalatora)</span><span class="sxs-lookup"><span data-stu-id="577bd-136">Installutil.exe (Installer tool)</span></span>](../tools/installutil-exe-installer-tool.md)
