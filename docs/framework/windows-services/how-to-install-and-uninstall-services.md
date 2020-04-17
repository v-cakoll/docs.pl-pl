---
title: 'Jak: Instalowanie i odinstalowywanie usług systemu Windows'
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
ms.openlocfilehash: 8937ef8b4007253b06444e59b292395084e4df2f
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607922"
---
# <a name="how-to-install-and-uninstall-windows-services"></a>Jak: Instalowanie i odinstalowywanie usług systemu Windows

Jeśli tworzysz usługę systemu Windows za pomocą programu .NET Framework, możesz szybko zainstalować aplikację usługi za pomocą narzędzia wiersza polecenia [*InstallUtil.exe*](../tools/installutil-exe-installer-tool.md) lub [programu PowerShell](/powershell/scripting/overview). Deweloperzy, którzy chcą zwolnić usługę systemu Windows, którą użytkownicy mogą zainstalować i odinstalować, powinni używać InstallShield. Aby uzyskać więcej informacji, zobacz [Tworzenie pakietu instalacyjnego (pulpit systemu Windows)](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).

> [!WARNING]
> Jeśli chcesz odinstalować usługę z komputera, nie postępuj zgodnie z instrukcjami w tym artykule. Zamiast tego dowiedz się, który program lub pakiet oprogramowania zainstalował usługę, a następnie wybierz pozycję **Aplikacje** w ustawieniach, aby odinstalować ten program. Należy zauważyć, że wiele usług są integralną częścią systemu Windows; Jeśli je usuniesz, może to spowodować niestabilność systemu.

Aby wykonać czynności opisane w tym artykule, należy najpierw dodać instalatora usługi do usługi systemu Windows. Aby uzyskać więcej informacji, zobacz [Przewodnik: Tworzenie aplikacji usługi systemu Windows](../windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).

Nie można uruchomić projektów usługi systemu Windows bezpośrednio ze środowiska programistycznego programu Visual Studio, naciskając klawisz F5. Przed uruchomieniem projektu należy zainstalować usługę w projekcie.

> [!TIP]
> Za pomocą **Eksploratora serwera** można sprawdzić, czy usługa została zainstalowana lub odinstalowana. Aby uzyskać więcej informacji, zobacz [Jak używać Eksploratora serwera w programie Visual Studio](https://support.microsoft.com/help/316649/how-to-use-the-server-explorer-in-visual-studio-net-and-visual-studio).

### <a name="install-your-service-manually-using-installutilexe-utility"></a>Instalowanie usługi ręcznie przy użyciu narzędzia InstallUtil.exe

1. Z menu **Start** wybierz katalog ** \< *wersji* > programu Visual Studio,** a następnie wybierz pozycję **Wiersz polecenia dewelopera dla \< *wersji*>programu VS**.

     Zostanie wyświetlony wiersz polecenia dewelopera dla programu Visual Studio.

2. Dostęp do katalogu, w którym znajduje się skompilowany plik wykonywalny projektu.

3. Uruchom *installUtil.exe* z wiersza polecenia z plikiem wykonywalnym projektu jako parametrem:

    ```console
    installutil <yourproject>.exe
    ```

     Jeśli używasz wiersza polecenia dewelopera dla programu Visual Studio, *InstallUtil.exe* powinien znajdować się na ścieżce systemowej. W przeciwnym razie można dodać go do ścieżki lub użyć w pełni kwalifikowanej ścieżki, aby ją wywołać. To narzędzie jest instalowane z programem .NET Framework w *%WINDIR%\Microsoft.NET\Framework[64]\\<framework_version\>*.

     Przykład:
     - W przypadku 32-bitowej wersji programu .NET Framework 4 lub 4.5 lub nowszej, jeśli katalogiem instalacyjnym systemu Windows jest *C:\Windows,* domyślną ścieżką jest *C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*.
     - W przypadku 64-bitowej wersji programu .NET Framework 4 lub 4.5 lub nowszej domyślną ścieżką jest *C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.

### <a name="uninstall-your-service-manually-using-installutilexe-utility"></a>Odinstaluj usługę ręcznie za pomocą narzędzia InstallUtil.exe

1. Z menu **Start** wybierz katalog ** \< *wersji* > programu Visual Studio,** a następnie wybierz pozycję **Wiersz polecenia dewelopera dla \< *wersji*>programu VS**.

     Zostanie wyświetlony wiersz polecenia dewelopera dla programu Visual Studio.

2. Uruchom *installUtil.exe* z wiersza polecenia z wyjściem projektu jako parametrem:

    ```console
    installutil /u <yourproject>.exe
    ```

3. Po usunięciu pliku wykonywalnego dla usługi usługa może nadal znajdować się w rejestrze. Jeśli tak jest, użyj polecenia [sc delete,](/windows-server/administration/windows-commands/sc-delete) aby usunąć wpis usługi z rejestru.

### <a name="install-your-service-manually-using-powershell"></a>Instalowanie usługi ręcznie przy użyciu programu PowerShell

1. Z menu **Start** wybierz katalog **programu Windows PowerShell,** a następnie wybierz pozycję **Windows PowerShell**.

2. Dostęp do katalogu, w którym znajduje się skompilowany plik wykonywalny projektu.

3. Uruchom polecenie cmdlet [**Nowej Usługi**](/powershell/module/microsoft.powershell.management/new-service) z wyjściem projektu i nazwą usługi jako parametrami:

    ```powershell
    New-Service -Name "YourServiceName" -BinaryPathName <yourproject>.exe
    ```

### <a name="uninstall-your-service-manually-using-powershell"></a>Ręczne odinstalowywanie usługi przy użyciu programu PowerShell

1. Z menu **Start** wybierz katalog **programu Windows PowerShell,** a następnie wybierz pozycję **Windows PowerShell**.

2. Uruchom polecenie cmdlet [**Remove-Service**](/powershell/module/microsoft.powershell.management/remove-service) z nazwą usługi jako parametrem:

    ```powershell
    Remove-Service -Name "YourServiceName"
    ```

3. Po usunięciu pliku wykonywalnego dla usługi usługa może nadal znajdować się w rejestrze. Jeśli tak jest, użyj polecenia [sc delete,](/windows-server/administration/windows-commands/sc-delete) aby usunąć wpis usługi z rejestru.

    ```powershell
    sc.exe delete "YourServiceName"
    ```

## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do aplikacji serwisowych systemu Windows](../windows-services/introduction-to-windows-service-applications.md)
- [Jak: Tworzenie usług systemu Windows](../windows-services/how-to-create-windows-services.md)
- [Jak: Dodawanie instalatorów do aplikacji usługi](../windows-services/how-to-add-installers-to-your-service-application.md)
- [Installutil.exe (Narzędzie instalatora)](../tools/installutil-exe-installer-tool.md)
