---
title: "Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a5848ffd-3eb5-432d-812e-bd948ccb6bca
caps.latest.revision: "83"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7ffc74fdbec204b798ee93a8ee2c91db992a83cb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="one-time-setup-procedure-for-the-windows-communication-foundation-samples"></a>Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation
Większość [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] próbki są obsługiwane w Internet Information Services (IIS) i uruchom z wspólnego katalogu wirtualnego. Ta procedura konfiguracji jednorazowej tworzy folder z dysku. Dodano również katalog wirtualny usług IIS o nazwie **ServiceModelSamples**.  
  
 **ServiceModelSamples** katalog wirtualny jest używany do tworzenia i uruchamiania wszystkie próbki, które używają usług hostowanych przez usługi IIS. Jest to tylko wirtualnego katalogu, który jest wymagany do uruchamiania przykładów. Tworzenie próbki spowoduje zastąpienie wcześniej wdrożonej usługi z tego katalogu wirtualnego; najbardziej ostatnio wbudowanych próbki będą wdrożone i dostępne w tym katalogu wirtualnego.  
  
> [!NOTE]
>  Należy uruchomić wszystkie polecenia przy użyciu konta administratora lokalnego. Jeśli używasz systemu Windows 7, [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)], lub Windows Server 2008 R2, należy także uruchomić wiersz polecenia z podwyższonym poziomem uprawnień. Aby to zrobić, kliknij prawym przyciskiem myszy ikonę wiersz polecenia, a następnie kliknij przycisk **Uruchom jako administrator**. Wszystkie polecenia w tym temacie należy uruchomić w wierszu polecenia, który zawiera ustawienia odpowiednią ścieżkę.  Najprostszym sposobem zapewnienia to polega na użyciu wiersz polecenia programu Visual Studio. Aby otworzyć ten monit, kliknij przycisk **Start**, wybierz pozycję **wszystkie programy**, przewiń w dół do **programu Visual Studio 2010**, wybierz pozycję **programu Visual Studio Tools**, Kliknij prawym przyciskiem myszy **wiersz polecenia programu Visual Studio (2010)**, a następnie kliknij przycisk **Uruchom jako administrator**. Jeśli jedna z zainstalowanych wersji programu Visual Studio Express, ten wiersz polecenia nie jest dostępna, i należy dodać "C:\Windows\Microsoft.Net\Framework\v4.0" do ścieżki systemowej.  
  
### <a name="one-time-setup-procedure-for-wcf-samples"></a>Procedura konfiguracji jednorazowej dla przykładów WCF  
  
1.  Upewnij się, że [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] jest skonfigurowany. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]jak skonfigurować [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], zobacz [informacji usługi instrukcje dotyczące hostowania internetowej](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md).  
  
2.  Upewnij się, że [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] jest zainstalowany. Wyszukaj następujące do wersji 4.0 (lub nowszej): **\Windows\Microsoft.NET\Framework**  
  
3.  Jeśli [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] nie jest zainstalowany, i systemu operacyjnego nie jest systemu Windows Server 2008 z dodatkiem SP2 lub nowszym, zainstaluj [251798 poprawkę](http://go.microsoft.com/fwlink/?LinkId=184693).  
  
4.  Uruchom następujące polecenia. Aby uzyskać więcej informacji na temat Dlaczego należy uruchamiać tych poleceń, zobacz [IIS hostowanej usługi nie powiedzie się](http://msdn.microsoft.com/en-us/ee5499fc-1b10-4cda-a9b1-13dba70f05f8).  
  
    > [!WARNING]
    >  Przypadku ponownej instalacji usług IIS należy ponownie uruchomić następujące polecenia.  
  
    ```  
    "%WINDIR%\Microsoft.Net\Framework\v4.0.30319\aspnet_regiis" –i –enable  
    "%WINDIR%\Microsoft.Net\Framework\v4.0.30319\ServiceModelReg.exe" -r  
    ```  
  
    > [!WARNING]
    >  Uruchomienie polecenia `aspnet_regiis –i –enable` będzie uruchamiało domyślnej puli aplikacji przy użyciu [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], który może powodować problemy z niezgodnością inne aplikacje na tym samym komputerze.  
  
5.  Postępuj zgodnie z [instrukcje dotyczące zapory](../../../../docs/framework/wcf/samples/firewall-instructions.md) umożliwiających porty używane przez próbek.  
  
6.  Sprawdź, czy następujące domyślny katalog: \<InstallDrive >:**\WF_WCF_Samples**. Jeśli wcześniej zostały zainstalowane przykłady, jest domyślnym katalogiem.  
  
7.  Jeśli nie są zainstalowane przykłady, zainstaluj je z lokalizacji pobierania próbek [Visual C#](http://go.microsoft.com/fwlink/?LinkId=190939) lub [Visual Basic](http://go.microsoft.com/fwlink/?LinkID=193373).  
  
8.  Po zainstalowaniu próbek, przejdź do: \<InstallDrive >:**\WF_WCF_Samples\WCF\Setup\\**  
  
9. Uruchom **Setupvroot.bat** pliku wsadowego. Są wykonywane następujące czynności:  
  
    -   W usługach IIS o nazwie ServiceModelSamples jest tworzony katalog wirtualny.  
  
    -   Nowe katalogi dysku są tworzone nazwane %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples i % SystemDrive%\Inetpub\wwwroot\ServiceModelSamples\bin.  
  
     Jeśli wolisz skonfigurować te katalogi ręcznie, zobacz [instrukcje dotyczące konfigurowania katalogów wirtualnych](../../../../docs/framework/wcf/samples/virtual-directory-setup-instructions.md). Aby przywrócić wszystkie zmiany wykonane w tym kroku, należy uruchomić cleanupvroot.bat po zakończeniu za pomocą próbek.  
  
    > [!NOTE]
    >  Ta procedura odbywa się tylko raz na komputerze, o ile nie jest uruchamiane cleanupvroot.bat.  
  
10. Należy udzielić uprawnień do modyfikowania dla %SystemDrive%\inetpub\wwwroot do konta, pod którym tworzysz przykłady i użytkownika usługi sieciowej. Podczas kompilowania, niektóre przykłady hostowanych w sieci Web może próba skopiowania plików binarnych skompilowanych wymienione wcześniej lokalizacji, a jeśli nie zostały ustawione odpowiednie uprawnienia, kompilacja zostanie przerwana. Alternatywnie możesz pozostawić uprawnień i uruchom wiersz polecenia zestawu SDK lub wiersz polecenia programu Visual Studio (2012) jako Administrator, lub utworzyć próbek [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]również Uruchom jako Administrator.  
  
    > [!NOTE]
    >  Jeśli ten krok nie jest ukończona, wszystkie próbki hostowanych przez usługi IIS zakończy się niepowodzeniem podczas kompilowania. Upewnij się, poprawnie ustawić uprawnienia lub uruchom wiersz polecenia SDK i wiersz polecenia programu Visual Studio (2012) jako Administrator.  
  
11. Utwórz katalog C:\logs na komputerze. Niektóre przykłady może być oczekiwano go. Upewnij się, że odpowiednie konto ma zapisu udzielono dostępu do tego folderu. W systemie Windows 7 [!INCLUDE[wv](../../../../includes/wv-md.md)], i Windows Server 2008 R2, to konto jest **usługi sieciowej**. Aby uzyskać [!INCLUDE[lserver](../../../../includes/lserver-md.md)], konto jest NT Authority\Network Service. Aby uzyskać [!INCLUDE[wxp](../../../../includes/wxp-md.md)] i [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], konto jest ASPNET.  
  
12. Uruchom plik Setupcerttool.bat. Ten plik znajduje się w \<InstallPath > \WF_WCF_Samples\WCF\Setup\ folderu.  Ten skrypt będzie wykonywać następujące zadania:  
  
    -   Narzędzie FindPrivateKey kompilacji.  
  
    -   Utwórz katalog o nazwie % ProgramFiles%\ServiceModelSampleTools.  
  
    -   Skopiuj nowe narzędzie FindPrivateKey do tego katalogu.  
  
     To narzędzie jest wymagany przez przykłady, które korzystają z certyfikatów i są hostowane w usługach IIS.  
  
    > [!NOTE]
    >  Ze względów bezpieczeństwa Pamiętaj, aby usunąć katalog wirtualny definicji i uprawnienia w ramach kroków konfiguracji powyżej, uruchamiając plik wsadowy o nazwie Cleanupvroot.bat po zakończeniu próbek.  
  
13. Przykłady, które znajdują się własnym (nie obsługiwany w usługach IIS) wymagają uprawnień, aby zarejestrować adresy HTTP na komputerze w celu nasłuchiwania. Uprawnienie do rezerwacji przestrzeni nazw protokołu HTTP, pochodzi z konto użytkownika używane do uruchomienia przykładu. Domyślnie konto administratora mają uprawnienia do rejestrowania dowolny adres HTTP. Konta administratorów inne niż musi mieć uprawnienie dla przestrzeni nazw protokołu HTTP używanego przez próbek. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]jak skonfigurować rezerwacji przestrzeni nazw, zobacz [Konfigurowanie protokołów HTTP i HTTPS](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md).  
  
14. Niektóre przykłady wymagają usługi kolejkowania komunikatów. Zobacz [usługi kolejkowania komunikatów instalowanie (MSMQ)](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md) instrukcje instalacji.  
  
    > [!NOTE]
    >  Upewnij się, uruchomić usługę MSMQ, przed uruchomieniem żadnych przykładów, które wymagają usługi kolejkowania komunikatów.  
  
15. Niektóre przykłady wymagają certyfikatów. Zobacz [internetowych usług informacyjnych (IIS) instrukcje dotyczące instalacji certyfikatu dla serwera](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).  
  
## <a name="see-also"></a>Zobacz też
