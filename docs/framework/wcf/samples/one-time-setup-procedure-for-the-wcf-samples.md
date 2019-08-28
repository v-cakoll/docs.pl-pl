---
title: Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: a5848ffd-3eb5-432d-812e-bd948ccb6bca
ms.openlocfilehash: 4fe77455c26393455c66c24c74691a335ad8cb1b
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70039179"
---
# <a name="one-time-setup-procedure-for-the-windows-communication-foundation-samples"></a>Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation

Większość przykładów Windows Communication Foundation (WCF) znajduje się w Internet Information Services (IIS) i uruchamiana ze wspólnego katalogu wirtualnego. Ta procedura konfiguracji jednorazowej tworzy folder na dysku; dodaje również katalog wirtualny do usług IIS o nazwie **servicemodelsamples**.

Katalog wirtualny **servicemodelsamples** służy do kompilowania i uruchamiania wszystkich przykładów korzystających z usługi hostowanej przez usługi IIS. Jest to jedyny katalog wirtualny, który jest wymagany do uruchomienia przykładów. Utworzenie przykładu spowoduje zastąpienie wszystkich wcześniej wdrożonych usług w tym katalogu wirtualnym; tylko ostatnio skompilowany przykład zostanie wdrożony i będzie dostępny w tym katalogu wirtualnym.

> [!NOTE]
> Należy uruchomić wszystkie polecenia w ramach konta administratora lokalnego. W przypadku korzystania z systemu Windows 7 [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)]lub Windows Server 2008 R2 należy również uruchomić wiersz polecenia z podwyższonym poziomem uprawnień. Aby to zrobić, kliknij prawym przyciskiem myszy ikonę wiersza polecenia, a następnie kliknij polecenie **Uruchom jako administrator**. Wszystkie polecenia w tym temacie muszą być uruchamiane w wierszu polecenia, który ma odpowiednie ustawienia ścieżki.  Najprostszym sposobem upewnienia się, że jest to przy użyciu wiersza polecenia programu Visual Studio. Aby otworzyć ten monit, kliknij przycisk **Start**, wybierz pozycję **Wszystkie programy**, przewiń w dół do **programu Visual Studio 2010**, wybierz pozycję **Visual Studio Tools**, kliknij prawym przyciskiem myszy pozycję **wiersz polecenia programu Visual Studio (2010)** , a następnie kliknij polecenie **Uruchom jako administrator.** . Jeśli masz zainstalowaną jedną z następujących wersji Visual Studio Express, ten wiersz polecenia nie jest dostępny i trzeba będzie dodać "C:\Windows\Microsoft.Net\Framework\v4.0" do ścieżki systemowej.

### <a name="one-time-setup-procedure-for-wcf-samples"></a>Procedura konfiguracji jednorazowej dla przykładów WCF

1. Upewnij się, że ASP.NET został skonfigurowany. Aby uzyskać więcej informacji na temat sposobu konfigurowania usługi ASP.NET, zobacz [instrukcje hostingu internetowych usług informacyjnych](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md).

2. Upewnij się [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] , że jest zainstalowany. Wyszukaj w następującym katalogu dla wersji v 4.0 (lub nowszej): **\Windows\Microsoft.NET\Framework**

3. Jeśli nie zainstalowano programu Visual Studio 2012 i system operacyjny nie jest systemem Windows Server 2008 z dodatkiem SP2 lub nowszym, należy zainstalować [poprawkę 251798](https://go.microsoft.com/fwlink/?LinkId=184693).

4. Uruchom następujące polecenia. Aby uzyskać więcej informacji na temat tego, dlaczego te polecenia muszą być uruchamiane, zobacz [usługa hostowana usług IIS kończy się niepowodzeniem](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752252(v=vs.90)).

    > [!WARNING]
    > Po ponownym zainstalowaniu usług IIS należy ponownie uruchomić następujące polecenia.

    ```
    "%WINDIR%\Microsoft.Net\Framework\v4.0.30319\aspnet_regiis" –i –enable
    "%WINDIR%\Microsoft.Net\Framework\v4.0.30319\ServiceModelReg.exe" -r
    ```

    > [!WARNING]
    > Uruchomienie polecenia `aspnet_regiis –i –enable` spowoduje [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], że zostanie uruchomiona domyślna pula aplikacji, co może spowodować problemy z niezgodnością dla innych aplikacji na tym samym komputerze.

5. Postępuj zgodnie z [instrukcjami zapory](../../../../docs/framework/wcf/samples/firewall-instructions.md) dotyczącymi włączania portów używanych przez przykłady.

6. Wyszukaj następujący katalog domyślny: \<InstallDrive >: **\WF_WCF_Samples**. Jeśli wcześniej zainstalowano przykłady, jest to katalog domyślny.

7. Jeśli przykłady nie są zainstalowane, zainstaluj je z lokalizacji pobierania próbek dla wizualizacji [ C# ](https://go.microsoft.com/fwlink/?LinkId=190939) lub [Visual Basic](https://go.microsoft.com/fwlink/?LinkID=193373).

8. Po zainstalowaniu przykładów przejdź do: \<InstallDrive>: **\WF_WCF_Samples\WCF\Setup\\**

9. Uruchom plik wsadowy **Setupvroot. bat** . Wykonywane są następujące czynności:

    - Katalog wirtualny jest tworzony w usługach IIS o nazwie ServiceModelSamples.

    - Nowe katalogi dysku są tworzone o nazwie%SystemDrive%\Inetpub\wwwroot\ServiceModelSamples i%SystemDrive%\Inetpub\wwwroot\ServiceModelSamples\bin.

    Jeśli wolisz ręcznie skonfigurować te katalogi, zobacz [instrukcje dotyczące instalacji katalogu wirtualnego](../../../../docs/framework/wcf/samples/virtual-directory-setup-instructions.md). Aby przywrócić wszystkie zmiany dokonane w tym kroku, uruchom cleanupvroot. bat po zakończeniu przy użyciu przykładów.

    > [!NOTE]
    > Tę procedurę należy wykonać tylko raz na komputerze, chyba że cleanupvroot. bat jest uruchomiony.

10. Musisz przyznać uprawnienia do modyfikowania%SystemDrive%\inetpub\wwwroot na koncie, w ramach którego tworzysz przykłady i użytkownika usługi sieciowej. Podczas kompilowania niektóre przykłady hostowane w sieci Web mogą próbować skopiować skompilowane pliki binarne do wcześniej wymienionej lokalizacji, a jeśli nie ustawisz odpowiednich uprawnień, kompilacja zostanie przerwana. Alternatywnie można pozostawić odpowiednie uprawnienia, a następnie uruchomić wiersz polecenia zestawu SDK lub wiersz polecenia programu Visual Studio (2012) jako administrator lub skompilować przykłady w programie Visual Studio 2012, również uruchomić jako administrator.

    > [!NOTE]
    > Jeśli ten krok nie zostanie ukończony, wszystkie przykłady hostowane przez usługi IIS zakończą się niepowodzeniem podczas kompilowania. Upewnij się, że uprawnienia zostały prawidłowo ustawione, lub Uruchom wiersz polecenia zestawu SDK i wiersz polecenia programu Visual Studio (2012) jako administrator.

11. Utwórz katalog C:\LOGS na komputerze; Niektóre przykłady mogą oczekiwać. Upewnij się, że odpowiednie konto ma przyznany dostęp do zapisu dla tego folderu. W przypadku systemów Windows [!INCLUDE[wv](../../../../includes/wv-md.md)]7,, i Windows Server 2008 R2 to konto jest **usługą sieciową**. W [!INCLUDE[lserver](../../../../includes/lserver-md.md)]przypadku systemu konto to NT AUTHORITY\NETWORK Service. Dla [!INCLUDE[wxp](../../../../includes/wxp-md.md)] i[!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], konto jest ASPNET.

12. Uruchom plik Setupcerttool. bat. Ten plik znajduje się w \<folderze InstallPath > \WF_WCF_Samples\WCF\Setup\.  Ten skrypt wykona następujące zadania:

    - Utwórz narzędzie FindPrivateKey.

    - Utwórz katalog o nazwie%ProgramFiles%\ServiceModelSampleTools.

    - Skopiuj nowe narzędzie FindPrivateKey do tego katalogu.

    To narzędzie jest wymagane przez przykłady, które używają certyfikatów i są hostowane w usługach IIS.

    > [!NOTE]
    > Ze względów bezpieczeństwa Pamiętaj, aby usunąć definicję katalogu wirtualnego i uprawnienia przyznane w powyższych krokach konfiguracji, uruchamiając plik wsadowy o nazwie cleanupvroot. bat po zakończeniu korzystania z przykładów.

13. Przykłady, które są samodzielne (niehostowane w usługach IIS), wymagają uprawnień do rejestrowania adresów HTTP na komputerze do nasłuchiwania. Uprawnienie do rezerwacji przestrzeni nazw protokołu HTTP pochodzi z konta użytkownika używanego do uruchomienia przykładu. Domyślnie konta administratorów mają uprawnienia do rejestrowania dowolnego adresu HTTP. Kontom innym niż administrator należy nadać uprawnienia do przestrzeni nazw HTTP używanych przez przykłady. Więcej informacji o sposobie konfigurowania rezerwacji przestrzeni nazw znajduje się w temacie [Konfigurowanie protokołów HTTP i https](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md).

14. Niektóre przykłady wymagają usługi kolejkowania komunikatów. Instrukcje instalacji znajdują się w temacie [Instalowanie usługi kolejkowania komunikatów (MSMQ)](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md) .

    > [!NOTE]
    > Upewnij się, że usługa MSMQ została uruchomiona przed uruchomieniem dowolnych przykładów, które wymagają usługi kolejkowania komunikatów.

15. Niektóre przykłady wymagają certyfikatów. Zobacz [instrukcje instalacji certyfikatu serwera Internet Information Services (IIS)](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).
