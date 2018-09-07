---
title: Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: a5848ffd-3eb5-432d-812e-bd948ccb6bca
ms.openlocfilehash: 3c3c5934cbbc7dd68f03d888aa0594f9ff61c225
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44063858"
---
# <a name="one-time-setup-procedure-for-the-windows-communication-foundation-samples"></a>Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation
Większość przykładów Windows Communication Foundation (WCF) są hostowane w Internet Information Services (IIS) i uruchamiane z wspólnego katalogu wirtualnego. Ta procedura konfiguracji jednorazowej tworzy folder z dysku. dodaje także katalog wirtualny usług IIS o nazwie **ServiceModelSamples**.  
  
 **ServiceModelSamples** katalog wirtualny jest używany do tworzenia i uruchamiania wszystkie przykłady, które przy użyciu usługi hostowanych przez usługi IIS. Jest to jedyny wirtualny katalogu, który jest wymagany do uruchamiania przykładów. Budowanie przykładu spowoduje zastąpienie dowolnego wcześniej wdrożonej usługi na ten katalog wirtualny; tylko najbardziej niedawno utworzonych przykładowych będą wdrożone i dostępne w tym katalogu wirtualnego.  
  
> [!NOTE]
>  Należy uruchomić wszystkie polecenia przy użyciu konta administratora lokalnego. Jeśli używasz Windows 7, [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)], lub Windows Server 2008 R2, należy również uruchomić wiersz polecenia z podwyższonym poziomem uprawnień. Aby to zrobić, kliknij prawym przyciskiem myszy ikonę wiersza polecenia, a następnie kliknij przycisk **Uruchom jako administrator**. Wszystkie polecenia w tym temacie, należy uruchomić polecenie w wierszu polecenia, który zawiera ustawienia odpowiednią ścieżkę.  Najprostszym sposobem, aby upewnić się, to jest przy użyciu wiersza polecenia programu Visual Studio. Aby otworzyć ten monit, kliknij przycisk **Start**, wybierz opcję **wszystkie programy**, przewiń w dół do **programu Visual Studio 2010**, wybierz opcję **Visual Studio Tools**, Kliknij prawym przyciskiem myszy **wiersza polecenia programu Visual Studio (2010)**, a następnie kliknij przycisk **Uruchom jako administrator**. Jeśli masz zainstalowany wersji programu Visual Studio Express, ten wiersz polecenia nie jest dostępna, i trzeba będzie dodać "C:\Windows\Microsoft.Net\Framework\v4.0" do ścieżki systemowej.  
  
### <a name="one-time-setup-procedure-for-wcf-samples"></a>Procedura konfiguracji jednorazowej dla przykładów programu WCF  
  
1.  Upewnij się, że [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] jest skonfigurowany. Aby uzyskać więcej informacji na temat sposobu konfigurowania [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], zobacz [informacji usługi instrukcje dotyczące hostowania internetowej](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md).  
  
2.  Upewnij się, że [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] jest zainstalowany. Wyszukaj następujący katalog dla wersji 4.0 (lub nowszy): **\Windows\Microsoft.NET\Framework**  
  
3.  Jeśli [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] nie jest zainstalowany, a system operacyjny nie jest system Windows Server 2008 z dodatkiem SP2 lub nowszej, zainstaluj [251798 poprawkę](https://go.microsoft.com/fwlink/?LinkId=184693).  
  
4.  Uruchom następujące polecenia. Aby uzyskać więcej informacji na temat Dlaczego należy uruchomić następujące polecenia, zobacz [IIS hostowanej usługi nie powiedzie się](https://msdn.microsoft.com/library/ee5499fc-1b10-4cda-a9b1-13dba70f05f8).  
  
    > [!WARNING]
    >  W przypadku ponownej instalacji usług IIS następujące polecenia należy ponownie uruchomić.  
  
    ```  
    "%WINDIR%\Microsoft.Net\Framework\v4.0.30319\aspnet_regiis" –i –enable  
    "%WINDIR%\Microsoft.Net\Framework\v4.0.30319\ServiceModelReg.exe" -r  
    ```  
  
    > [!WARNING]
    >  Uruchomienie polecenia `aspnet_regiis –i –enable` spowoduje, że pula aplikacji domyślnej uruchamiania, za pomocą [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], który może tworzyć problemy z brakiem zgodności dla innych aplikacji na tym samym komputerze.  
  
5.  Postępuj zgodnie z [instrukcje dotyczące zapory](../../../../docs/framework/wcf/samples/firewall-instructions.md) włączania portów używanych przez próbki.  
  
6.  Wyszukaj następujący katalog domyślny: \<InstallDrive >:**\WF_WCF_Samples**. Jeśli przykłady zostały wcześniej zainstalowane, to jest katalog domyślny.  
  
7.  Jeśli nie są zainstalowane przykłady, zainstaluj je z lokalizacji pobierania próbek [Visual C#](https://go.microsoft.com/fwlink/?LinkId=190939) lub [języka Visual Basic](https://go.microsoft.com/fwlink/?LinkID=193373).  
  
8.  Po zainstalowaniu próbki, przejdź do: \<InstallDrive >:**\WF_WCF_Samples\WCF\Setup\\**  
  
9. Uruchom **Setupvroot.bat** pliku wsadowego. Są wykonywane następujące czynności:  
  
    -   Katalog wirtualny jest tworzony w usługach IIS o nazwie ServiceModelSamples.  
  
    -   Nowe katalogi dysku są tworzone o nazwie %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples i % SystemDrive%\Inetpub\wwwroot\ServiceModelSamples\bin.  
  
     Jeśli wolisz skonfigurować te katalogi ręcznie, zobacz [instrukcje dotyczące konfigurowania katalogów wirtualnych](../../../../docs/framework/wcf/samples/virtual-directory-setup-instructions.md). Aby cofnąć wszystkie zmiany wykonane w tym kroku, należy uruchomić cleanupvroot.bat po zakończeniu korzystania z przykładami.  
  
    > [!NOTE]
    >  Ta procedura odbywa się tylko raz na komputerze, chyba że uruchomieniu cleanupvroot.bat.  
  
10. Należy przyznać uprawnienia do modyfikowania dla %SystemDrive%\inetpub\wwwroot do konta, w którym tworzysz, przykłady i użytkownik Usługa sieciowa. Podczas tworzenia, przykłady hostowanych w sieci Web może próbować skopiuj skompilowane pliki binarne do lokalizacji, które wspomniano wcześniej, a jeśli nie zostały ustawione odpowiednie uprawnienia, kompilacja zostanie przerwana. Alternatywnie możesz zostawić uprawnienia, i uruchom wiersz polecenia zestawu SDK lub wiersza polecenia programu Visual Studio (2012) jako Administrator, lub utworzyć próbek [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]również Uruchom jako Administrator.  
  
    > [!NOTE]
    >  Jeśli ten krok nie zostanie zakończona, wszystkie przykłady hostowanych przez usługi IIS zakończy się niepowodzeniem podczas kompilowania. Upewnij się, czy poprawnie ustawić uprawnienia, lub uruchom wiersz polecenia zestawu SDK i programu Visual Studio Command Prompt (2012) jako Administrator.  
  
11. Utwórz katalog C:\logs na komputerze. Przykłady może być oczekiwany go. Upewnij się, że odpowiednie konto ma zapisu udzielono dostępu do tego folderu. Windows 7 [!INCLUDE[wv](../../../../includes/wv-md.md)], a system Windows Server 2008 R2, to konto jest **Usługa sieciowa**. Aby uzyskać [!INCLUDE[lserver](../../../../includes/lserver-md.md)], konto jest NT Authority\Network Service. Aby uzyskać [!INCLUDE[wxp](../../../../includes/wxp-md.md)] i [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], konto jest ASPNET.  
  
12. Uruchom plik Setupcerttool.bat. Ten plik znajduje się w \<InstallPath > \WF_WCF_Samples\WCF\Setup\ folderu.  Ten skrypt będzie wykonywać następujące zadania:  
  
    -   Narzędzie FindPrivateKey kompilacji.  
  
    -   Utwórz katalog o nazwie % ProgramFiles%\ServiceModelSampleTools.  
  
    -   Skopiuj nowe narzędzie FindPrivateKey do tego katalogu.  
  
     To narzędzie jest wymagana przez przykładów, które używają certyfikatów i są hostowane w usługach IIS.  
  
    > [!NOTE]
    >  Ze względów bezpieczeństwa należy pamiętać o usunięciu definicji katalogu wirtualnego i uprawnienia udzielone w ramach kroków konfiguracji powyżej, uruchamiając plik wsadowy o nazwie Cleanupvroot.bat po zakończeniu pracy z próbek.  
  
13. Przykłady, które są może być samodzielnie hostowane (nie hostowane w usługach IIS) wymagają uprawnień, aby zarejestrować adresy HTTP na komputerze w celu nasłuchiwania. Uprawnienia dla rezerwacji przestrzeni nazw protokołu HTTP, pochodzi z konta użytkownika używanego do uruchomienia przykładu. Domyślnie administrator konta mają uprawnienia do rejestrowania dowolny adres HTTP. Konta administratorów inne niż muszą mieć uprawnienie do przestrzeni nazw protokołu HTTP, które posługują się z przykładami. Aby uzyskać więcej informacji o sposobie konfigurowania rezerwacji przestrzeni nazw, zobacz [Konfigurowanie protokołów HTTP i HTTPS](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md).  
  
14. Niektóre przykłady wymagają usługi kolejkowania komunikatów. Zobacz [instalowanie komunikatów usługi kolejkowania wiadomości (MSMQ)](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md) instrukcje dotyczące instalacji.  
  
    > [!NOTE]
    >  Upewnij się, uruchom usługę MSMQ, przed uruchomieniem żadnych przykładów, które wymagają usługi kolejkowania komunikatów.  
  
15. Niektóre przykłady wymagają certyfikatów. Zobacz [internetowych usług informacyjnych (IIS) serwera certyfikatów — instrukcje dotyczące instalacji](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).  
  
## <a name="see-also"></a>Zobacz też
