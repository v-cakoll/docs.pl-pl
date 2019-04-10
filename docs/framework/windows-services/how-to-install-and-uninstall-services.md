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
# <a name="how-to-install-and-uninstall-windows-services"></a>Instrukcje: Instalowanie i odinstalowywanie usług Windows
Jeśli opracowujesz usługi Windows za pomocą programu .NET Framework, można szybko zainstalować usługi app service przy użyciu [ *InstallUtil.exe* ](../tools/installutil-exe-installer-tool.md) narzędzie wiersza polecenia. Deweloperzy, którzy mają być wersji usług Windows, które użytkownicy mogą instalować i odinstalowywać należy używać programu InstallShield. Aby uzyskać więcej informacji, zobacz [Utwórz pakiet Instalatora (systemu Windows Windows client)](https://docs.microsoft.com/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-client).
  
> [!WARNING]
>  Jeśli chcesz odinstalować usługę z komputera, nie wykonaj kroki opisane w tym artykule. Zamiast tego należy sprawdzić, które pakiety programu lub oprogramowania zainstalowane usługi, a następnie wybierz **aplikacje** w ustawieniach w celu odinstalowania tego programu. Należy pamiętać, że wiele usług są integralną częścią Windows; Jeśli je usuniesz, może spowodować niestabilność systemu.  
  
 Aby skorzystać z instrukcji w tym artykule, należy najpierw dodać Instalatora usługi do usługi Windows. Aby uzyskać więcej informacji, zobacz [instruktażu: Tworzenie aplikacji usługi Windows](../windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).  
  
 Projekty usługi Windows nie można uruchomić bezpośrednio ze środowiska projektowego programu Visual Studio, naciskając klawisz F5. Zanim będzie można uruchomić projektu, należy zainstalować usługę w projekcie.  
  
> [!TIP]
>  Możesz użyć **Eksploratora serwera** Aby sprawdzić, czy zostały zainstalowane lub odinstalować usługę. Aby uzyskać więcej informacji, zobacz [sposobie używania Eksploratora serwera w programie Visual Studio](https://support.microsoft.com/help/316649/how-to-use-the-server-explorer-in-visual-studio-net-and-visual-studio).
  
### <a name="install-your-service-manually"></a>Ręcznie zainstalować usługę  
  
1. Z **Start** menu, wybierz opcję **programu Visual Studio \< *wersji* >**  katalogu, a następnie wybierz opcję **wiersz polecenia dla deweloperów dla programu VS \< *wersji*>**.
  
     Pojawi się wiersz polecenia dla deweloperów programu Visual Studio. 
  
2. Dostęp do katalogu, w którym znajduje się plik wykonywalny projektu.  
  
3. Uruchom *InstallUtil.exe* polecenia w pliku wykonywalnego jako parametr wiersza z projektem:  
  
    ```console
    installutil <yourproject>.exe  
    ```  

     Jeśli używasz wiersz polecenia programisty dla programu Visual Studio *InstallUtil.exe* powinny znajdować się w ścieżce systemowej. W przeciwnym razie możesz dodać go do ścieżki lub wywoływać go za pomocą w pełni kwalifikowanej ścieżki. To narzędzie jest instalowane z .NET Framework w *% WINDIR%\Microsoft.NET\Framework[64]\\< framework_version >*.
     
     Na przykład:
     - W przypadku 32-bitowej wersji programu .NET Framework 4 lub 4.5 lub nowszy, jeśli jest katalogu instalacji Windows *C:\Windows*, domyślna ścieżka to *C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*.
     - Dla 64-bitowej wersji programu .NET Framework 4 lub 4.5 lub nowszy, domyślna ścieżka to *C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.
  
### <a name="uninstall-your-service-manually"></a>Ręcznie odinstalować usługę  
  
1. Z **Start** menu, wybierz opcję **programu Visual Studio \< *wersji* >**  katalogu, a następnie wybierz opcję **wiersz polecenia dla deweloperów dla programu VS \< *wersji*>**.
  
     Pojawi się wiersz polecenia dla deweloperów programu Visual Studio.  
  
2. Uruchom *InstallUtil.exe* w wierszu polecenia z danymi wyjściowymi projektu jako parametr:  
  
    ```console  
    installutil /u <yourproject>.exe  
    ```  
  
3. Po usunięciu pliku wykonywalnego dla usługi usługi znajdować się w rejestrze. Jeśli tak jest rzeczywiście, użyj polecenia [sc delete](/windows-server/administration/windows-commands/sc-delete) można usunąć wpisu usługi z rejestru.  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do aplikacji usług Windows](../windows-services/introduction-to-windows-service-applications.md)
- [Instrukcje: Tworzenie usług Windows](../windows-services/how-to-create-windows-services.md)
- [Instrukcje: Dodawanie instalatorów od aplikacji usług](../windows-services/how-to-add-installers-to-your-service-application.md)
- [Installutil.exe (Narzędzie Instalatora)](../tools/installutil-exe-installer-tool.md)
