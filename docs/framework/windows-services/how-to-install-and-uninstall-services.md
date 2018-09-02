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
ms.openlocfilehash: 9d8e84280b5821f8d8df36694198bd85fb8470d4
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43416911"
---
# <a name="how-to-install-and-uninstall-services"></a>Porady: instalowanie i odinstalowywanie usług
Jeśli opracowujesz usługi Windows za pomocą programu .NET Framework, można szybko zainstalować aplikacji usługi za pomocą narzędzia wiersza polecenia o nazwie InstallUtil.exe. Jeśli jesteś deweloperem kto chce wersji usług Windows, czy użytkownicy mogą zainstalować i możesz odinstalować należy używać programu InstallShield. Zobacz [wdrożenia Instalatora Windows](https://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0).  
  
> [!WARNING]
>  Jeśli chcesz odinstalować usługę z komputera, nie wykonaj kroki opisane w tym artykule. Zamiast tego należy sprawdzić, które pakiety programu lub oprogramowania zainstalowane usługi, a następnie wybierz **Dodaj/Usuń programy** w Panelu sterowania, aby odinstalować ten program. Należy pamiętać, że wiele usług są integralną częścią Windows; Jeśli je usuniesz, może spowodować niestabilność systemu.  
  
 Aby skorzystać z instrukcji w tym artykule, należy najpierw dodać Instalatora usługi do usługi Windows. Zobacz [wskazówki: tworzenie Windows usługi aplikacji w Projektancie składników](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).  
  
 Projekty usługi Windows nie można uruchomić bezpośrednio ze środowiska projektowego programu Visual Studio, naciskając klawisz F5. Jest to spowodowane musi być zainstalowana usługa w projekcie, aby można było uruchomić projekt.  
  
> [!TIP]
>  Możesz uruchomić **Eksploratora serwera** i sprawdź, czy usługi zostały zainstalowane lub odinstalowane. Aby uzyskać więcej informacji, zobacz jak: dostępu oraz inicjowanie Eksploratora bazy danych Eksploratora serwera.  
  
### <a name="to-install-your-service-manually"></a>Aby ręcznie zainstalować usługę  
  
1.  Na Windows **Start** menu lub **Start** ekranu, wybierz **programu Visual Studio** , **Visual Studio Tools**, **dla deweloperów Wiersz polecenia**.  
  
     Pojawi się wiersz polecenia programu Visual Studio.  
  
2.  Dostęp do katalogu, w którym znajduje się plik wykonywalny projektu.  
  
3.  Uruchom InstallUtil.exe z wiersza polecenia przy użyciu pliku wykonywalnego projektu jako parametr:  
  
    ```  
    installutil <yourproject>.exe  
    ```  
  
     Jeśli używasz programu Visual Studio wiersza polecenia InstallUtil.exe powinien być w ścieżce systemowej. Jeśli nie, dodaj go do ścieżki lub wywoływać go za pomocą w pełni kwalifikowanej ścieżki. To narzędzie jest instalowane z .NET Framework i jego ścieżka jest `%WINDIR%\Microsoft.NET\Framework[64]\<framework_version>`. Na przykład w przypadku 32-bitowej wersji programu .NET Framework 4 lub 4.5. *, jeśli katalogu instalacji Windows C:\Windows, ścieżka jest `C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe`. Dla 64-bitowej wersji programu .NET Framework 4 lub 4.5. \*, domyślna ścieżka to `C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe`.  
  
### <a name="to-uninstall-your-service-manually"></a>Aby ręcznie odinstalować usługę  
  
1.  Na Windows **Start** menu lub **Start** ekranu, wybierz **programu Visual Studio**, **Visual Studio Tools**, **dla deweloperów Wiersz polecenia**.  
  
     Pojawi się wiersz polecenia programu Visual Studio.  
  
2.  Uruchom InstallUtil.exe w wierszu polecenia z danymi wyjściowymi projektu jako parametr:  
  
    ```  
    installutil /u <yourproject>.exe  
    ```  
  
3.  Czasami po usunięciu pliku wykonywalnego dla usługi usługi może nadal istnieć w rejestrze. W takim przypadku należy użyć polecenia [sc delete](https://technet.microsoft.com/library/cc742045.aspx) można usunąć wpisu usługi z rejestru.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do aplikacji usług systemu Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [Instrukcje: tworzenie usług systemu Windows](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 [Instrukcje: dodawanie instalatorów od aplikacji usług](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [Installutil.exe (narzędzie instalatora)](../../../docs/framework/tools/installutil-exe-installer-tool.md)
