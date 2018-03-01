---
title: "Konfigurowanie obsługi protokołu WS-Atomic Transaction"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WS-AT protocol [WCF], configuring WS-Atomic Transaction
ms.assetid: cb9f1c9c-1439-4172-b9bc-b01c3e09ac48
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 922b2048a262e722a11ee77c41e96dddec411326
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="configuring-ws-atomic-transaction-support"></a>Konfigurowanie obsługi protokołu WS-Atomic Transaction
W tym temacie opisano, jak można skonfigurować obsługę protokołu WS-AtomicTransaction (WS-AT) za pomocą narzędzia konfiguracji WS-AT.  
  
## <a name="using-the-ws-at-configuration-utility"></a>Za pomocą narzędzia konfiguracji WS-AT.  
 Narzędzia konfiguracji WS-AT (wsatConfig.exe) służy do konfigurowania ustawień usługi WS-AT. Aby włączyć usługę protokołu WS-AT, należy użyć narzędzia konfiguracji konfiguruje HTTPS port dla protokołu WS-AT, powiąż certyfikat X.509 z portem HTTPS i skonfigurować certyfikaty partnera upoważnionego przez określenie nazwy podmiotu certyfikatu lub odciski palców. Narzędzie konfiguracji umożliwia wybranie trybu śledzenia i wychodzące domyślny zestaw i maksymalny limit czasu przychodzących transakcji.  
  
 Dostępne funkcje to narzędzie przy użyciu przystawki strony właściwości programu Microsoft Management Console (MMC), w konsoli zarządzania usług składowych lub z poziomu okna wiersza polecenia. Konfigurowanie obsługi protokołu WS-AT na komputerze lokalnym przy użyciu okna wiersza polecenia; Skonfiguruj ustawienia na komputerach lokalnych i zdalnych za pomocą przystawki programu MMC.  
  
 W oknie wiersza polecenia są dostępne w lokalizacji instalacji zestawu Windows SDK "%WINDIR%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation".  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Narzędzie wiersza polecenia, zobacz [narzędzia konfiguracji WS-AtomicTransaction (wsatConfig.exe)](../../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md).  
  
 Jeśli używasz [!INCLUDE[wxp](../../../../includes/wxp-md.md)] lub [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], uzyskać dostęp do przystawki programu MMC, przechodząc do **usługi składnik/narzędzia panelu/administracyjne kontroli**, klikając prawym przyciskiem myszy **Mój komputer**, i Wybieranie **właściwości**. To jest tej samej lokalizacji, w którym można skonfigurować MSDTC Microsoft Distributed Transaction Coordinator (). Opcje dostępne dla konfiguracji są pogrupowane w obszarze **WS-AT** kartę. Jeśli używasz systemu Windows Vista lub [!INCLUDE[lserver](../../../../includes/lserver-md.md)], przystawki programu MMC można znaleźć, klikając **Start** przycisk i wprowadzając `dcomcnfg.exe` w **wyszukiwania** pole. Po otwarciu programu MMC, przejdź do **Moje Computer\Distributed transakcji Coordinator\Local DTC** węzeł, kliknij prawym przyciskiem myszy i wybierz **właściwości**. Opcje dostępne dla konfiguracji są pogrupowane w obszarze **WS-AT** kartę.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Zobacz przystawki [przystawki MMC konfiguracji WS-AtomicTransaction](../../../../docs/framework/wcf/ws-atomictransaction-configuration-mmc-snap-in.md).  
  
 Aby włączyć narzędzia interfejsu użytkownika, najpierw należy zarejestrować pliku WsatUI.dll, znajdującym się w następującej ścieżce  
  
 %ProgramFiles%\Microsoft SDKs\Windows\v6.0\Bin  
  
 Aby zarejestrować produkt, uruchom następujące polecenie z poziomu okna wiersza polecenia:  
  
 `regasm.exe /codebase WsatUI.dll`  
  
## <a name="enabling-ws-at"></a>Włączanie usługi WS-AT.  
 Aby włączyć usługę protokołu WS-AT wewnątrz usługi MSDTC przy użyciu portu 443 i certyfikat X.509 z kluczem prywatnym, który został zainstalowany w magazynie komputera lokalnego, należy użyć narzędzia wsatConfig.exe przy użyciu następującego polecenia.  
  
 `WsatConfig.exe –network:enable –port:8443 –endpointCert:<machine|"Issuer\SubjectName"> -accountsCerts:<thumbprint|"Issuer\SubjectName"> -restart`  
  
 Zastąp odpowiednich parametrów mających wartości odpowiednich dla danego środowiska.  
  
 Aby wyłączyć usługę protokołu WS-AT wewnątrz usługi MSDTC, należy użyć narzędzia wsatConfig.exe przy użyciu następującego polecenia.  
  
 `WsatConfig.exe –network:disable -restart`  
  
## <a name="configuring-trust-between-two-machines"></a>Konfigurowanie relacji zaufania między dwoma komputerami  
 Usługa protokołu WS-AT wymaga administratora jawnie zezwolić indywidualnych kont na uczestniczenie w transakcjach rozproszonych. Jeśli jesteś administratorem dwa komputery, można skonfigurować zarówno maszyny do ustanawiania relacji wzajemnego zaufania wymiana certyfikatów między komputerami prawidłowego zestawu, ich instalowania w magazynach certyfikatów odpowiednich i przy użyciu Narzędzie wsatConfig.exe można dodać certyfikatu do każdej maszyny do drugiego lista autoryzowanych uczestnika certyfikatów. Ten krok jest niezbędny do wykonania transakcji rozproszonych między dwoma komputerami za pomocą usługi WS-AT.  
  
 W poniższym przykładzie przedstawiono kroki, aby ustanowić zaufanie między dwoma komputerami, A i B.  
  
### <a name="creating-and-exporting-certificates"></a>Tworzenie i eksportowanie certyfikatów  
 Ta procedura wymaga przystawki MMC certyfikatów. Przystawka jest możliwy Otwieranie menu Start/uruchamiania, wpisując "mmc" w odpowiednim polu i naciśnięcie przycisku OK. Następnie w **Console1** okna, przejdź do **plik lub Dodaj-Usuń** przystawkę, kliknij przycisk Dodaj, a następnie wybierz pozycję **certyfikaty** z **dostępne autonomiczny Konsola** listy. Na koniec wybierz **konto komputera** do zarządzania i kliknij przycisk **OK**. **Certyfikaty** węzeł jest dostępny w przystawce konsoli.  
  
 Już musi posiadać wymaganych certyfikatów, aby ustanowić zaufanie. Aby dowiedzieć się, jak utworzyć i zainstalować nowe certyfikaty przed następujące czynności, zobacz [porady: tworzenie i instalacja tymczasowego certyfikaty klienta WCF podczas rozwoju](http://go.microsoft.com/fwlink/?LinkId=158925).  
  
1.  Na komputerze A przy użyciu przystawki MMC Certyfikaty importowania istniejącego certyfikatu (certA) do LocalMachine\MY (węzeł osobiste) i magazynu LocalMachine\ROOT (węzeł urzędu certyfikacji zaufanym certyfikatem głównym). Aby zaimportować certyfikat do określonego węzła, kliknij prawym przyciskiem myszy węzeł, a następnie wybierz pozycję **wszystkie zadania/Import**.  
  
2.  Na komputerze B, za pomocą przystawki certyfikatów konsoli MMC utworzyć lub uzyskać certB certyfikatu z kluczem prywatnym i zaimportuj go do LocalMachine\MY (węzeł osobiste) i magazynu LocalMachine\ROOT (węzeł urzędu certyfikacji zaufanym certyfikatem głównym).  
  
3.  Eksportuj do pliku klucza publicznego w certA, jeśli to nie wykonano już.  
  
4.  Eksportuj do pliku klucza publicznego w certB, jeśli to nie wykonano już.  
  
### <a name="establishing-mutual-trust-between-machines"></a>Ustanawianie relacji wzajemnego zaufania między maszyny  
  
1.  Na komputerze A należy zaimportować plik reprezentację certB do magazynów LocalMachine\MY i LocalMachine\ROOT. To deklaruje tej maszynie certB relacji zaufania, aby komunikować się z nim.  
  
2.  Na komputerze B należy zaimportować plik w certA do magazynów LocalMachine\MY i LocalMachine\ROOT. Oznacza to, czy maszyna B certA zaufania do komunikowania się z nim.  
  
 Po wykonaniu tych czynności relacja zaufania została ustanowiona między dwoma komputerami, i można je skonfigurować do komunikowania się ze sobą za pomocą usługi WS-AT.  
  
### <a name="configuring-msdtc-to-use-certificates"></a>Konfigurowanie usługi MSDTC, aby korzystać z certyfikatów  
 Ponieważ Usługa protokołu WS-AT działa jako klient i serwer, musi zarówno nasłuchiwania przychodzących połączeń i inicjowania połączeń wychodzących. W związku z tym należy skonfigurować usługi MSDTC, dzięki czemu bez informacji o certyfikacie używanym do komunikacji z zewnętrznymi i certyfikatów, które można autoryzować akceptując komunikacji przychodzącej.  
  
 Można to skonfigurować za pomocą przystawki MMC usługi WS-AT. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]to narzędzie, zobacz [przystawki MMC konfiguracji WS-AtomicTransaction](../../../../docs/framework/wcf/ws-atomictransaction-configuration-mmc-snap-in.md) tematu. W poniższych krokach opisano sposób ustanowić zaufanie między dwa komputery z systemem usługi MSDTC.  
  
1.  Skonfiguruj ustawienia maszyny A. Wybierz certA "Certyfikatu punktu końcowego". Wybierz certB "Autoryzowany certyfikatów".  
  
2.  Skonfiguruj ustawienia maszyny B. Wybierz certB "Certyfikatu punktu końcowego". Wybierz certA "Autoryzowany certyfikatów".  
  
> [!NOTE]
>  Jeśli na jednym komputerze wysyła komunikat do innego komputera, nadawca próbuje Sprawdź, czy nazwa podmiotu certyfikatu adresata i nazwę adresata odpowiadają. Jeśli nie są zgodne, niepowodzenia weryfikacji certyfikatu i nie może komunikować się dwie maszyny.  
>   
>  Dla komputera przyłączonego do domeny nazwa jest w pełni kwalifikowaną nazwę domeny. Domyślnie nazwa komputera w grupie roboczej jest nazwa NetBIOS komputera. Jednak nazwa mogą również obejmować sufiks systemu nazw domen (DNS, Domain Name System), jeśli jest dostępny dla połączenia jest używany podczas komunikacji między dwoma komputerami.  
>   
>  W przypadku zmiany nazwy maszyny, na przykład gdy komputera grupy roboczej jest dołączany do domeny, należy ponowne wystawienie certyfikatów lub ręcznie skonfigurować sufiksów DNS.  
  
## <a name="security"></a>Zabezpieczenia  
 Ponieważ niektóre ustawienia związane z usługi MSDTC i WS-AT są przechowywane w rejestrze HKLM\Software\Microsoft\MSDTC i HKLM\Software\Microsoft\WSAT, odpowiednio, upewnij się, że te klucze rejestru są chronione tak, aby tylko administratorzy mogą pisać do nich. W narzędziu Edytora rejestru, kliknij prawym przyciskiem myszy klucz chcesz zabezpieczyć i wybierz **uprawnienia** można ustawić kontroli dostępu. Jest niezwykle ważny do zapewnienia bezpieczeństwa i integralności systemu to ważne, że klucze są tylko do odczytu dla użytkowników z niskim poziomem uprawnień.  
  
 Podczas wdrażania usługi MSDTC, administrator musi upewnij się, że wszelkie wymiany danych usługi MSDTC jest bezpieczna. W przypadku wdrożenia grupy roboczej izolować transakcyjne infrastruktury przed złośliwymi użytkownikami; w ramach wdrożenia klastra należy zabezpieczyć rejestru klastra.  
  
## <a name="tracing"></a>Śledzenie  
 Zintegrowana usługa obsługuje protokół WS-AT, transakcji określonych śledzenia może być włączony i zarządzane za pośrednictwem [przystawki MMC konfiguracji WS-AtomicTransaction](../../../../docs/framework/wcf/ws-atomictransaction-configuration-mmc-snap-in.md) narzędzia.  Dane śledzenia mogą zawierać dane, wskazujący, że otrzymał podczas rejestracji zostanie przeprowadzona dla określonej transakcji czasu transakcji osiągnie stanu terminali wynik każdego rejestracji transakcji. Wszystkie ślady można wyświetlić przy użyciu [narzędzia podglądu śledzenia usług (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) narzędzia.  
  
 Usługa protokołu WS-AT obsługuje również zintegrowanego śledzenia ServiceModel przez sesję śledzenia funkcji ETW. Zapewnia to bardziej szczegółowe, specyficzne dla komunikacji śladów oprócz istniejących śledzeniach transakcji.  Aby włączyć te dodatkowe dane śledzenia, wykonaj następujące kroki  
  
1.  Otwórz **Start/Uruchom** menu, w polu wejściowym wpisz "regedit" i wybierz **OK**.  
  
2.  W **Edytora rejestru**, przejdź do folderu w lewym okienku Hkey_Local_Machine\SOFTWARE\Microsoft\WSAT\3.0\  
  
3.  Kliknij prawym przyciskiem myszy `ServiceModelDiagnosticTracing` wartość w okienku po prawej stronie, a następnie wybierz **Modyfikuj**.  
  
4.  W **dane wartości** pole wprowadzania, wpisz jedno z następujących prawidłowych wartości określa poziom śledzenia, aby umożliwić.  
  
-   0: wyłączanie  
  
-   1: krytyczne  
  
-   3: błąd. Jest to wartość domyślna  
  
-   7: ostrzeżenie  
  
-   15: informacje  
  
-   31: pełne  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzie do konfiguracji elementu WS-AtomicTransaction (wsatConfig.exe)](../../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)  
 [Przystawka programu MMC do konfigurowania elementu WS-AtomicTransaction](../../../../docs/framework/wcf/ws-atomictransaction-configuration-mmc-snap-in.md)
