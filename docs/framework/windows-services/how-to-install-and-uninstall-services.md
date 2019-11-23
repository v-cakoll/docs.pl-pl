---
title: 'Instrukcje: Instalowanie i odinstalowywanie usług systemu Windows'
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
ms.openlocfilehash: 38fc0172b5f97561d69fe495237e95597d7b9727
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003132"
---
# <a name="how-to-install-and-uninstall-windows-services"></a>Instrukcje: Instalowanie i odinstalowywanie usług systemu Windows

Jeśli tworzysz usługę systemu Windows przy użyciu .NET Framework, możesz szybko zainstalować swoją aplikację usługi przy użyciu narzędzia wiersza polecenia [*Installutil. exe*](../tools/installutil-exe-installer-tool.md) lub [programu PowerShell](/powershell/scripting/overview). Deweloperzy, którzy chcą zwolnić usługę systemu Windows, którą użytkownicy mogą instalować i odinstalowywać, powinni używać InstallShield. Aby uzyskać więcej informacji, zobacz [Tworzenie pakietu Instalatora (klient systemu Windows)](https://docs.microsoft.com/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-client).

> [!WARNING]
> Jeśli chcesz odinstalować usługę z komputera, nie wykonuj kroków opisanych w tym artykule. Zamiast tego Sprawdź, który program lub pakiet oprogramowania zainstalował usługę, a następnie wybierz pozycję **aplikacje** w ustawieniach, aby odinstalować ten program. Należy zauważyć, że wiele usług jest integralną częścią systemu Windows; po ich usunięciu może wystąpić niestabilność systemu.

Aby wykonać kroki opisane w tym artykule, należy najpierw dodać Instalatora usługi do usługi systemu Windows. Aby uzyskać więcej informacji, zobacz [Przewodnik: Tworzenie aplikacji usługi systemu Windows](../windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).

Nie można uruchamiać projektów usług systemu Windows bezpośrednio ze środowiska programistycznego programu Visual Studio, naciskając klawisz F5. Aby można było uruchomić projekt, należy zainstalować usługę w projekcie.

> [!TIP]
> Możesz użyć **Eksplorator serwera** , aby sprawdzić, czy usługa została zainstalowana lub odinstalowana. Aby uzyskać więcej informacji, zobacz [jak używać Eksplorator serwera w programie Visual Studio](https://support.microsoft.com/help/316649/how-to-use-the-server-explorer-in-visual-studio-net-and-visual-studio).

### <a name="install-your-service-manually-using-installutilexe-utility"></a>Ręczne instalowanie usługi za pomocą narzędzia InstallUtil. exe

1. Z menu **Start** wybierz pozycję **Visual Studio \<*wersja*>** directory, a następnie wybierz pozycję **wiersz polecenia dla deweloperów dla programu vs \<*Version*>** .

     Zostanie wyświetlony wiersz polecenia dla deweloperów dla programu Visual Studio.

2. Uzyskaj dostęp do katalogu, w którym znajduje się skompilowany plik wykonywalny projektu.

3. Uruchom program *Installutil. exe* z wiersza polecenia z plikiem wykonywalnym projektu jako parametrem:

    ```console
    installutil <yourproject>.exe
    ```

     Jeśli używasz wiersz polecenia dla deweloperów dla programu Visual Studio, *Installutil. exe* powinien znajdować się na ścieżce systemowej. W przeciwnym razie możesz dodać go do ścieżki lub użyć w pełni kwalifikowanej ścieżki, aby wywołać ją. To narzędzie jest instalowane z .NET Framework w *%windir%\Microsoft.NET\Framework [64]\\< framework_version\>* .

     Na przykład:
     - W przypadku 32-bitowej wersji .NET Framework 4 lub 4,5 lub nowszej, jeśli katalog instalacyjny systemu Windows to *C:\Windows*, domyślną ścieżką jest *C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*.
     - W przypadku 64-bitowej wersji .NET Framework 4 lub 4,5 lub nowszej ścieżka domyślna to *C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.

### <a name="uninstall-your-service-manually-using-installutilexe-utility"></a>Ręczne odinstalowywanie usługi za pomocą narzędzia InstallUtil. exe

1. Z menu **Start** wybierz pozycję **Visual Studio \<*wersja*>** directory, a następnie wybierz pozycję **wiersz polecenia dla deweloperów dla programu vs \<*Version*>** .

     Zostanie wyświetlony wiersz polecenia dla deweloperów dla programu Visual Studio.

2. Uruchom program *Installutil. exe* z wiersza polecenia z danymi wyjściowymi projektu jako parametr:

    ```console
    installutil /u <yourproject>.exe
    ```

3. Po usunięciu pliku wykonywalnego usługi może być on nadal obecny w rejestrze. W takim przypadku należy użyć polecenia [SC Delete](/windows-server/administration/windows-commands/sc-delete) , aby usunąć wpis usługi z rejestru.

### <a name="install-your-service-manually-using-powershell"></a>Ręczne instalowanie usługi przy użyciu programu PowerShell

1. Z menu **Start** wybierz pozycję katalog programu **Windows PowerShell** , a następnie wybierz pozycję **Windows PowerShell**.

2. Uzyskaj dostęp do katalogu, w którym znajduje się skompilowany plik wykonywalny projektu.

3. Uruchom polecenie cmdlet [**New-Service**](/powershell/module/microsoft.powershell.management/new-service) z danymi wyjściowymi projektu i nazwą usługi jako parametry:

    ```powershell
    New-Service -Name "YourServiceName" -BinaryPathName <yourproject>.exe
    ```

### <a name="uninstall-your-service-manually-using-powershell"></a>Ręczne odinstalowywanie usługi przy użyciu programu PowerShell

1. Z menu **Start** wybierz pozycję katalog programu **Windows PowerShell** , a następnie wybierz pozycję **Windows PowerShell**.

2. Uruchom polecenie cmdlet [**Remove-Service**](/powershell/module/microsoft.powershell.management/remove-service) z nazwą usługi jako parametr:

    ```powershell
    Remove-Service -Name "YourServiceName"
    ```

3. Po usunięciu pliku wykonywalnego usługi może być on nadal obecny w rejestrze. W takim przypadku należy użyć polecenia [SC Delete](/windows-server/administration/windows-commands/sc-delete) , aby usunąć wpis usługi z rejestru.

    ```powershell
    sc.exe delete "YourServiceName"
    ```

## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do aplikacji usług systemu Windows](../windows-services/introduction-to-windows-service-applications.md)
- [Instrukcje: tworzenie usług systemu Windows](../windows-services/how-to-create-windows-services.md)
- [Instrukcje: Dodawanie instalatorów do aplikacji usługi](../windows-services/how-to-add-installers-to-your-service-application.md)
- [Installutil. exe (Narzędzie instalatora)](../tools/installutil-exe-installer-tool.md)
