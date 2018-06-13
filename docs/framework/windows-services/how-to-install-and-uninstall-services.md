---
title: 'Porady: instalowanie i odinstalowywanie usług'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, deploying
- services, uninstalling
- services, installing
- installing Windows Services
- uninstalling applications, Windows Services
- installation, Windows Services
- uninstalling Windows Services
- installutil.exe tool
ms.assetid: c89c5169-f567-4305-9d62-db31a1de5481
author: ghogen
manager: douge
ms.openlocfilehash: 0d42a37b2e84c310569666771ded38e5feca3608
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33513142"
---
# <a name="how-to-install-and-uninstall-services"></a><span data-ttu-id="c7397-102">Porady: instalowanie i odinstalowywanie usług</span><span class="sxs-lookup"><span data-stu-id="c7397-102">How to: Install and Uninstall Services</span></span>
<span data-ttu-id="c7397-103">Jeśli projektujesz usługi systemu Windows przy użyciu programu .NET Framework, można zainstalować za pomocą narzędzia wiersza polecenia o nazwie InstallUtil.exe szybko aplikacji usługi.</span><span class="sxs-lookup"><span data-stu-id="c7397-103">If you’re developing a Windows Service by using the .NET Framework, you can quickly install your service application by using a command-line utility called InstallUtil.exe.</span></span> <span data-ttu-id="c7397-104">Jeśli jesteś deweloperem kto chce wersji usługi systemu Windows, czy użytkownicy mogą instalować i odinstalowywać możesz użyć InstallShield.</span><span class="sxs-lookup"><span data-stu-id="c7397-104">If you’re a developer who wants to release a Windows Service that users can install and uninstall  you should use InstallShield.</span></span> <span data-ttu-id="c7397-105">Zobacz [wdrożenia Instalatora Windows](http://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0).</span><span class="sxs-lookup"><span data-stu-id="c7397-105">See [Windows Installer Deployment](http://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="c7397-106">Jeśli chcesz odinstalować usługi z komputera, nie należy wykonać czynności opisane w tym artykule.</span><span class="sxs-lookup"><span data-stu-id="c7397-106">If you want to uninstall a service from your computer, don’t follow the steps in this article.</span></span> <span data-ttu-id="c7397-107">Zamiast tego należy sprawdzić, które pakiety programu lub oprogramowanie instalowane usługi, a następnie wybierz **Dodaj lub usuń programy** w Panelu sterowania, aby odinstalować ten program.</span><span class="sxs-lookup"><span data-stu-id="c7397-107">Instead, find out which program or software package installed the service, and then choose **Add/Remove Programs** in Control Panel to uninstall that program.</span></span> <span data-ttu-id="c7397-108">Należy pamiętać, że wiele usług są integralną częścią systemu Windows; Jeśli je usuniesz, może spowodować niestabilność systemu.</span><span class="sxs-lookup"><span data-stu-id="c7397-108">Note that many services are integral parts of Windows; if you remove them, you might cause system instability.</span></span>  
  
 <span data-ttu-id="c7397-109">Aby skorzystać z instrukcji w tym artykule, należy najpierw dodać Instalatora usługi z usługą systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="c7397-109">In order to use the steps in this article, you first need to add a service installer to your Windows Service.</span></span> <span data-ttu-id="c7397-110">Zobacz [wskazówki: tworzenie okien aplikacji w Projektancie składników usługi](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span><span class="sxs-lookup"><span data-stu-id="c7397-110">See [Walkthrough: Creating a Windows Service Application in the Component Designer](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span></span>  
  
 <span data-ttu-id="c7397-111">Projekty usługi systemu Windows nie można uruchomić bezpośrednio ze środowiska projektowego Visual Studio, naciskając klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="c7397-111">Windows Service projects cannot be run directly from the Visual Studio development environment by pressing F5.</span></span> <span data-ttu-id="c7397-112">To dlatego musi być zainstalowana usługa w projekcie, można było uruchomić projekt.</span><span class="sxs-lookup"><span data-stu-id="c7397-112">This is because the service in the project must be installed before you can run the project.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="c7397-113">Możesz uruchomić **Eksploratora serwera** i sprawdź, czy usługa została zainstalowana lub odinstalowana.</span><span class="sxs-lookup"><span data-stu-id="c7397-113">You can launch **Server Explorer** and verify that your service has been installed or uninstalled.</span></span> <span data-ttu-id="c7397-114">Aby uzyskać więcej informacji, zobacz porady: dostęp i zainicjować Eksploratora bazy danych Eksploratora serwera.</span><span class="sxs-lookup"><span data-stu-id="c7397-114">For more information, see How to: Access and Initialize Server Explorer-Database Explorer.</span></span>  
  
### <a name="to-install-your-service-manually"></a><span data-ttu-id="c7397-115">Aby ręcznie zainstalować usługi</span><span class="sxs-lookup"><span data-stu-id="c7397-115">To install your service manually</span></span>  
  
1.  <span data-ttu-id="c7397-116">W systemie Windows **Start** menu lub **Start** ekranu, wybierz **programu Visual Studio** , **programu Visual Studio Tools**, **Developer Wiersz polecenia**.</span><span class="sxs-lookup"><span data-stu-id="c7397-116">On the Windows **Start** menu or **Start** screen, choose **Visual Studio** , **Visual Studio Tools**, **Developer Command Prompt**.</span></span>  
  
     <span data-ttu-id="c7397-117">Zostanie wyświetlony wiersz polecenia programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c7397-117">A Visual Studio command prompt appears.</span></span>  
  
2.  <span data-ttu-id="c7397-118">Uzyskanie dostępu do katalogu, w którym znajduje się plik wykonywalny skompilowanych projektu.</span><span class="sxs-lookup"><span data-stu-id="c7397-118">Access the directory where your project's compiled executable file is located.</span></span>  
  
3.  <span data-ttu-id="c7397-119">Uruchom InstallUtil.exe z wiersza polecenia z pliku wykonywalnego projektu jako parametr:</span><span class="sxs-lookup"><span data-stu-id="c7397-119">Run InstallUtil.exe from the command prompt with your project's executable as a parameter:</span></span>  
  
    ```  
    installutil <yourproject>.exe  
    ```  
  
     <span data-ttu-id="c7397-120">Jeśli używasz wiersza polecenia programu Visual Studio InstallUtil.exe powinna znajdować się na ścieżce systemowej.</span><span class="sxs-lookup"><span data-stu-id="c7397-120">If you’re using the Visual Studio command prompt, InstallUtil.exe should be on the system path.</span></span> <span data-ttu-id="c7397-121">Jeśli nie, dodaj go do ścieżki lub użyj w pełni kwalifikowana, aby go wywołać.</span><span class="sxs-lookup"><span data-stu-id="c7397-121">If not, you can add it to the path, or use the fully qualified path to invoke it.</span></span> <span data-ttu-id="c7397-122">To narzędzie jest zainstalowany w środowisku .NET Framework, a jego ścieżka jest `%WINDIR%\Microsoft.NET\Framework[64]\<framework_version>`.</span><span class="sxs-lookup"><span data-stu-id="c7397-122">This tool is installed with the .NET Framework, and its path is `%WINDIR%\Microsoft.NET\Framework[64]\<framework_version>`.</span></span> <span data-ttu-id="c7397-123">Na przykład w przypadku 32-bitowej wersji programu .NET Framework 4 lub 4.5. \*, jeśli katalog instalacyjny systemu Windows jest C:\Windows, ścieżka jest `C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe`.</span><span class="sxs-lookup"><span data-stu-id="c7397-123">For example, for the 32-bit version of the .NET Framework 4 or 4.5.\*, if your Windows installation directory is C:\Windows, the path is `C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe`.</span></span> <span data-ttu-id="c7397-124">W 64-bitowej wersji programu .NET Framework 4 lub 4.5. \*, domyślna ścieżka to `C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe`.</span><span class="sxs-lookup"><span data-stu-id="c7397-124">For the 64-bit version of the .NET Framework 4 or 4.5.\*, the default path is `C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe`.</span></span>  
  
### <a name="to-uninstall-your-service-manually"></a><span data-ttu-id="c7397-125">Aby ręcznie odinstalować usługi</span><span class="sxs-lookup"><span data-stu-id="c7397-125">To uninstall your service manually</span></span>  
  
1.  <span data-ttu-id="c7397-126">W systemie Windows **Start** menu lub **Start** ekranu, wybierz **programu Visual Studio**, **programu Visual Studio Tools**, **Developer Wiersz polecenia**.</span><span class="sxs-lookup"><span data-stu-id="c7397-126">On the Windows **Start** menu or **Start** screen, choose **Visual Studio**, **Visual Studio Tools**, **Developer Command Prompt**.</span></span>  
  
     <span data-ttu-id="c7397-127">Zostanie wyświetlony wiersz polecenia programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c7397-127">A Visual Studio command prompt appears.</span></span>  
  
2.  <span data-ttu-id="c7397-128">Uruchom InstallUtil.exe z wiersza polecenia z danych wyjściowych projektu jako parametr:</span><span class="sxs-lookup"><span data-stu-id="c7397-128">Run InstallUtil.exe from the command prompt with your project's output as a parameter:</span></span>  
  
    ```  
    installutil /u <yourproject>.exe  
    ```  
  
3.  <span data-ttu-id="c7397-129">Czasami po usunięciu pliku wykonywalnego usługi usługa może nadal być znajdujący się w rejestrze.</span><span class="sxs-lookup"><span data-stu-id="c7397-129">Sometimes, after the executable for a service is deleted, the service might still be present in the registry.</span></span> <span data-ttu-id="c7397-130">W takim przypadku polecenie [sc delete](http://technet.microsoft.com/library/cc742045.aspx) Aby usunąć wpis dla usługi z rejestru.</span><span class="sxs-lookup"><span data-stu-id="c7397-130">In that case, use the command [sc delete](http://technet.microsoft.com/library/cc742045.aspx) to remove the entry for the service from the registry.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7397-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c7397-131">See Also</span></span>  
 [<span data-ttu-id="c7397-132">Wprowadzenie do aplikacji usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="c7397-132">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [<span data-ttu-id="c7397-133">Instrukcje: tworzenie usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="c7397-133">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 [<span data-ttu-id="c7397-134">Instrukcje: dodawanie instalatorów od aplikacji usług</span><span class="sxs-lookup"><span data-stu-id="c7397-134">How to: Add Installers to Your Service Application</span></span>](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [<span data-ttu-id="c7397-135">Installutil.exe (narzędzie instalatora)</span><span class="sxs-lookup"><span data-stu-id="c7397-135">Installutil.exe (Installer Tool)</span></span>](../../../docs/framework/tools/installutil-exe-installer-tool.md)
