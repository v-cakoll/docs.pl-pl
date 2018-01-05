---
title: "Porady: instalowanie i odinstalowywanie usług"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "19"
author: ghogen
ms.author: ghogen
manager: douge
ms.workload: dotnet
ms.openlocfilehash: bf767813f965b2c52a5061f74bbf2fab4572791b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-install-and-uninstall-services"></a>Porady: instalowanie i odinstalowywanie usług
Jeśli projektujesz usługi systemu Windows przy użyciu programu .NET Framework, można zainstalować za pomocą narzędzia wiersza polecenia o nazwie InstallUtil.exe szybko aplikacji usługi. Jeśli jesteś deweloperem kto chce wersji usługi systemu Windows, czy użytkownicy mogą instalować i odinstalowywać możesz użyć InstallShield. Zobacz [wdrożenia Instalatora Windows](http://msdn.microsoft.com/en-us/121be21b-b916-43e2-8f10-8b080516d2a0).  
  
> [!WARNING]
>  Jeśli chcesz odinstalować usługi z komputera, nie należy wykonać czynności opisane w tym artykule. Zamiast tego należy sprawdzić, które pakiety programu lub oprogramowanie instalowane usługi, a następnie wybierz **Dodaj lub usuń programy** w Panelu sterowania, aby odinstalować ten program. Należy pamiętać, że wiele usług są integralną częścią systemu Windows; Jeśli je usuniesz, może spowodować niestabilność systemu.  
  
 Aby skorzystać z instrukcji w tym artykule, należy najpierw dodać Instalatora usługi z usługą systemu Windows. Zobacz [wskazówki: tworzenie okien aplikacji w Projektancie składników usługi](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).  
  
 Projekty usługi systemu Windows nie można uruchomić bezpośrednio ze środowiska projektowego Visual Studio, naciskając klawisz F5. To dlatego musi być zainstalowana usługa w projekcie, można było uruchomić projekt.  
  
> [!TIP]
>  Możesz uruchomić **Eksploratora serwera** i sprawdź, czy usługa została zainstalowana lub odinstalowana. Aby uzyskać więcej informacji, zobacz porady: dostęp i zainicjować Eksploratora bazy danych Eksploratora serwera.  
  
### <a name="to-install-your-service-manually"></a>Aby ręcznie zainstalować usługi  
  
1.  W systemie Windows **Start** menu lub **Start** ekranu, wybierz **programu Visual Studio** , **programu Visual Studio Tools**, **Developer Wiersz polecenia**.  
  
     Zostanie wyświetlony wiersz polecenia programu Visual Studio.  
  
2.  Uzyskanie dostępu do katalogu, w którym znajduje się plik wykonywalny skompilowanych projektu.  
  
3.  Uruchom InstallUtil.exe z wiersza polecenia z pliku wykonywalnego projektu jako parametr:  
  
    ```  
    installutil <yourproject>.exe  
    ```  
  
     Jeśli używasz wiersza polecenia programu Visual Studio InstallUtil.exe powinna znajdować się na ścieżce systemowej. Jeśli nie, dodaj go do ścieżki lub użyj w pełni kwalifikowana, aby go wywołać. To narzędzie jest zainstalowany w środowisku .NET Framework, a jego ścieżka jest `%WINDIR%\Microsoft.NET\Framework[64]\<framework_version>`. Na przykład w przypadku 32-bitowej wersji programu .NET Framework 4 lub 4.5. *, jeśli katalog instalacyjny systemu Windows jest C:\Windows, ścieżka jest `C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe`. W 64-bitowej wersji programu .NET Framework 4 lub 4.5. \*, domyślna ścieżka to `C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe`.  
  
### <a name="to-uninstall-your-service-manually"></a>Aby ręcznie odinstalować usługi  
  
1.  W systemie Windows **Start** menu lub **Start** ekranu, wybierz **programu Visual Studio**, **programu Visual Studio Tools**, **Developer Wiersz polecenia**.  
  
     Zostanie wyświetlony wiersz polecenia programu Visual Studio.  
  
2.  Uruchom InstallUtil.exe z wiersza polecenia z danych wyjściowych projektu jako parametr:  
  
    ```  
    installutil /u <yourproject>.exe  
    ```  
  
3.  Czasami po usunięciu pliku wykonywalnego usługi usługa może nadal być znajdujący się w rejestrze. W takim przypadku polecenie [sc delete](http://technet.microsoft.com/library/cc742045.aspx) Aby usunąć wpis dla usługi z rejestru.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do aplikacji usług systemu Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [Instrukcje: tworzenie usług systemu Windows](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 [Instrukcje: dodawanie instalatorów od aplikacji usług](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [Installutil.exe (narzędzie instalatora)](../../../docs/framework/tools/installutil-exe-installer-tool.md)
