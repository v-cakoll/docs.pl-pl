---
title: Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: a5848ffd-3eb5-432d-812e-bd948ccb6bca
ms.openlocfilehash: 954ec04d2ef1ca7667b4f75a8a6652010b5dbd33
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121618"
---
# <a name="one-time-setup-procedure-for-the-windows-communication-foundation-samples"></a>Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation

Większość przykładów programu Windows Communication Foundation (WCF) jest hostowana w internetowych usługach informacyjnych (IIS) i uruchamiana ze wspólnego katalogu wirtualnego. Ta jednorazowa procedura konfiguracji tworzy folder na dysku; dodaje również katalog wirtualny do usług IIS o nazwie **ServiceModelSamples**.

Katalog wirtualny **ServiceModelSamples** służy do tworzenia i uruchamiania wszystkich przykładów korzystających z usługi hostowanej przez usługi IIS. Jest to jedyny katalog wirtualny, który jest wymagany do uruchomienia próbek. Tworzenie próbki zastąpi wszystkie wcześniej wdrożone usługi w tym katalogu wirtualnym; tylko ostatnio zbudowany próbka zostanie wdrożona i będzie dostępna w tym katalogu wirtualnym.

> [!NOTE]
> Należy uruchomić wszystkie polecenia w ramach lokalnego konta administratora. Jeśli używasz systemu Windows 7, Windows Vista lub Windows Server 2008 R2, należy również uruchomić wiersz polecenia z podwyższonymi uprawnieniami. W tym celu kliknij prawym przyciskiem myszy ikonę wiersza polecenia, a następnie kliknij polecenie **Uruchom jako administrator**. Wszystkie polecenia w tym temacie muszą być uruchamiane w wierszu polecenia, który ma odpowiednie ustawienia ścieżki.  Najprostszym sposobem, aby upewnić się, że jest to za pomocą wiersza polecenia programu Visual Studio. Aby otworzyć ten monit, kliknij przycisk **Start**, wybierz **pozycję Wszystkie programy**, przewiń w dół do programu Visual Studio **2010**, wybierz polecenie **Narzędzia programu Visual Studio**, kliknij prawym przyciskiem myszy wiersz polecenia programu Visual Studio **(2010),** a następnie kliknij polecenie **Uruchom jako administrator**. Jeśli masz zainstalowaną jedną z wersji programu Visual Studio Express, ten wiersz polecenia jest niedostępny i do ścieżki systemowej należy dodać "C:\Windows\Microsoft.Net\Framework\v4.0".

### <a name="one-time-setup-procedure-for-wcf-samples"></a>Procedura jednorazowej konfiguracji próbek WCF

1. Upewnij się, że ASP.NET jest skonfigurowany. Aby uzyskać więcej informacji na temat konfigurowania ASP.NET, zobacz [Instrukcje hostingu usług informacyjnych w Internecie](internet-information-service-hosting-instructions.md).

2. Upewnij się, że jest zainstalowany program .NET Framework 4. Wyszukiwanie następującego katalogu w wersji 4.0 (lub nowszej): **\Windows\Microsoft.NET\Framework**

3. Upewnij się, że masz zainstalowany program Visual Studio 2012 lub nowszy lub system operacyjny to Windows Server 2008 SP2 lub nowszy.

4. Uruchom następujące polecenia. Aby uzyskać więcej informacji o tym, dlaczego te polecenia muszą być uruchamiane, zobacz [Usługa hostowana usług IIS kończy się niepowodzeniem](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752252(v=vs.90)).

    > [!WARNING]
    > Jeśli program IIS zostanie ponownie zainstalowany, należy ponownie uruchomić następujące polecenia.

    ```console
    "%WINDIR%\Microsoft.Net\Framework\v4.0.30319\aspnet_regiis" –i –enable
    "%WINDIR%\Microsoft.Net\Framework\v4.0.30319\ServiceModelReg.exe" -r
    ```

    > [!WARNING]
    > Uruchomienie polecenia `aspnet_regiis –i –enable` spowoduje, że domyślna pula aplikacji będzie uruchamiana przy użyciu programu .NET Framework 4, co może powodować problemy ze zgodnością innych aplikacji na tym samym komputerze.

5. Postępuj zgodnie z [instrukcjami zapory,](firewall-instructions.md) aby włączyć porty używane przez przykłady.

6. Sprawdź, czy w katalogu \<domyślnym nie ma następujących katalogów domyślnych: InstallDrive>:**\WF_WCF_Samples**. Jeśli próbki zostały wcześniej zainstalowane, jest to katalog domyślny.

7. Jeśli próbki nie są zainstalowane, zainstaluj je z [przykładów Programu Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla programu .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459).

8. Po zainstalowaniu przykładów przejdź \<do : InstallDrive>:**\WF_WCF_Samples\WCF\Setup\\ **

9. Uruchom plik wsadowy **Setupvroot.bat.** Wykonywane są następujące kroki:

    - Katalog wirtualny jest tworzony w usługach IIS o nazwie ServiceModelSamples.

    - Nowe katalogi dysków są tworzone o nazwie %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples i %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples\bin.

    Jeśli wolisz ręcznie skonfigurować te katalogi, zobacz [Instrukcje konfiguracji katalogu wirtualnego](virtual-directory-setup-instructions.md). Aby przywrócić wszystkie zmiany wykonane w tym kroku, uruchom cleanupvroot.bat po zakończeniu korzystania z próbek.

    > [!NOTE]
    > Ta procedura musi być wykonana tylko raz na komputerze, chyba że cleanupvroot.bat jest uruchomiony.

10. Należy udzielić uprawnień do modyfikowania dla %SystemDrive%\inetpub\wwwroot do konta, na którym są one budowane próbki i użytkownika usługi sieciowej. Podczas tworzenia niektóre próbki hostowane w sieci Web mogą próbować skopiować skompilowane pliki binarne do wcześniej wymienionej lokalizacji, a jeśli nie ustawiono odpowiednich uprawnień, kompilacja zostanie przerwana. Alternatywnie można pozostawić uprawnienia, ponieważ są one i uruchomić wiersz polecenia SDK lub Visual Studio Command Prompt (2012) jako administrator lub utworzyć przykłady w programie Visual Studio 2012, również uruchomić jako administrator.

    > [!NOTE]
    > Jeśli ten krok nie zostanie ukończony, wszystkie próbki hostowane przez iIS zakończy się niepowodzeniem podczas tworzenia. Upewnij się, że poprawnie ustawisz uprawnienia lub uruchomisz wiersz polecenia zestawu SDK i wiersz polecenia programu Visual Studio (2012) jako administratora.

11. Tworzenie katalogu C:\logs na komputerze; niektóre próbki mogą się tego spodziewać. Upewnij się, że odpowiednie konto ma dostęp do zapisu przyznany temu folderowi. W systemach Windows 7, Windows Vista i Windows Server 2008 R2 to konto to **usługa sieciowa**. W systemie Windows Server 2008 kontem jest nt authority\usługa sieciowa. W systemach Windows XP i Windows Server 2003 kontem jest aspnet.

12. Uruchom plik Setupcerttool.bat. Ten plik znajduje \<się w folderze InstallPath>\WF_WCF_Samples\WCF\Setup\.  Ten skrypt wykona następujące zadania:

    - Tworzenie narzędzia FindPrivateKey.

    - Utwórz katalog o nazwie %ProgramFiles%\ServiceModelSampleTools.

    - Skopiuj nowe narzędzie FindPrivateKey do tego katalogu.

    To narzędzie jest wymagane przez przykłady, które używają certyfikatów i są hostowane w urzędzie IIS.

    > [!NOTE]
    > Ze względów bezpieczeństwa należy pamiętać o usunięciu definicji katalogu wirtualnego i uprawnień przyznanych w powyższych krokach konfiguracji, uruchamiając plik wsadowy o nazwie Cleanupvroot.bat po zakończeniu pracy z próbkami.

13. Przykłady, które są hostowane samodzielnie (nie są hostowane w serwisach IIS) wymagają uprawnień do rejestrowania adresów HTTP na komputerze w celu nasłuchiwania. Uprawnienie do rezerwacji obszaru nazw HTTP pochodzi z konta użytkownika używanego do uruchamiania próbki. Domyślnie konta administratora mają uprawnienia do rejestrowania dowolnego adresu HTTP. Konta niebędące administratorami muszą mieć uprawnienia do obszarów nazw HTTP używanych przez przykłady. Aby uzyskać więcej informacji na temat konfigurowania rezerwacji obszaru nazw, zobacz [Konfigurowanie protokołu HTTP i HTTPS](../feature-details/configuring-http-and-https.md).

14. Niektóre przykłady wymagają usługi kolejkowania wiadomości. Aby uzyskać instrukcje instalacji, zobacz [Instalowanie usługi kolejkowania wiadomości (MSMQ).](installing-message-queuing-msmq.md)

    > [!NOTE]
    > Przed uruchomieniem próbek wymagających usługi kolejkowania wiadomości należy rozpocząć usługę MSMQ.

15. Niektóre przykłady wymagają certyfikatów. Zobacz [Instrukcje instalacji certyfikatów serwera usług informacyjnych (IIS).](iis-server-certificate-installation-instructions.md)
