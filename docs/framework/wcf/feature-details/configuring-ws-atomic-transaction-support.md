---
title: Konfigurowanie obsługi protokołu WS-Atomic Transaction
ms.date: 03/30/2017
helpviewer_keywords:
- WS-AT protocol [WCF], configuring WS-Atomic Transaction
ms.assetid: cb9f1c9c-1439-4172-b9bc-b01c3e09ac48
ms.openlocfilehash: 2ec4fd65b97808fbf1a8401f5c0913face5835f0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651141"
---
# <a name="configuring-ws-atomic-transaction-support"></a>Konfigurowanie obsługi protokołu WS-Atomic Transaction
W tym temacie opisano sposób konfigurowania obsługi WS-AtomicTransaction (WS-AT) za pomocą narzędzia konfiguracji WS-AT.  
  
## <a name="using-the-ws-at-configuration-utility"></a>Za pomocą narzędzia konfiguracji WS-AT  
 Narzędzie konfiguracji WS-AT (wsatConfig.exe) służy do konfigurowania ustawień WS-AT. Aby włączyć usługi protokołu WS-AT, należy użyć narzędzia konfiguracji można skonfigurować HTTPS port WS-AT, powiąż certyfikat X.509 z portem HTTPS, a także skonfigurować certyfikaty partnera upoważnionego przez określenie nazwy podmiotu certyfikatu lub odciski palców. Narzędzie do konfiguracji umożliwia wybranie trybu śledzenia i wychodzące domyślny zestaw i maksymalne limity czasu transakcji przychodzących.  
  
 Możesz uzyskać dostęp funkcji to narzędzie, za pomocą przystawki strony właściwości programu Microsoft Management Console (MMC), w konsoli zarządzania usług składowych lub z poziomu okna wiersza polecenia. Konfigurowanie obsługi WS-AT na komputerze lokalnym przy użyciu okna wiersza polecenia; Skonfiguruj ustawienia na komputerach lokalnych i zdalnych za pomocą przystawki programu MMC.  
  
 Okno wiersza polecenia są dostępne w lokalizacji instalacji zestawu Windows SDK "%WINDIR%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation".  
  
 Aby uzyskać więcej informacji na temat narzędzia wiersza polecenia, zobacz [WS-AtomicTransaction Configuration Utility (wsatConfig.exe)](../../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md).  
  
 Jeśli używasz [!INCLUDE[wxp](../../../../includes/wxp-md.md)] lub [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], są dostępne w przystawce programu MMC, przechodząc do **usługi narzędzia/składowe w panelu/administracyjne kontroli**, kliknięcie prawym przyciskiem **Mój komputer**, i Wybieranie **właściwości**. Jest to tej samej lokalizacji, w którym można skonfigurować transakcję Koordynator MSDTC (Microsoft Distributed). Opcje dostępne dla konfiguracji są pogrupowane w obszarze **WS-AT** kartę. Jeśli używasz Windows Vista lub [!INCLUDE[lserver](../../../../includes/lserver-md.md)], przystawki programu MMC można znaleźć, klikając pozycję **Start** przycisk, a następnie wprowadzenie `dcomcnfg.exe` w **wyszukiwania** pole. Po otwarciu programu MMC, przejdź do **Moje Computer\Distributed transakcji Coordinator\Local DTC** węzła, kliknij prawym przyciskiem myszy i wybierz **właściwości**. Opcje dostępne dla konfiguracji są pogrupowane w obszarze **WS-AT** kartę.  
  
 Aby uzyskać więcej informacji na temat przystawki, zobacz [przystawki MMC konfiguracji WS-AtomicTransaction](../../../../docs/framework/wcf/ws-atomictransaction-configuration-mmc-snap-in.md).  
  
 Aby włączyć interfejs użytkownika narzędzia, najpierw musisz się zarejestrować plik WsatUI.dll znajduje się w następującej ścieżce  
  
 %PROGRAMFILES%\Microsoft SDKs\Windows\v6.0\Bin  
  
 Aby zarejestrować produkt, uruchom następujące polecenie z poziomu okna wiersza polecenia:  
  
 `regasm.exe /codebase WsatUI.dll`  
  
## <a name="enabling-ws-at"></a>Włączanie WS-AT  
 Aby włączyć usługi protokołu WS-AT wewnątrz usługi MSDTC przy użyciu portu 443 i certyfikatu X.509 przy użyciu klucza prywatnego, który został zainstalowany w magazynie komputera lokalnego, należy użyć narzędzia wsatConfig.exe za pomocą następującego polecenia.  
  
 `WsatConfig.exe –network:enable –port:8443 –endpointCert:<machine|"Issuer\SubjectName"> -accountsCerts:<thumbprint|"Issuer\SubjectName"> -restart`  
  
 Zastąp odpowiednie parametry przy użyciu wartości odpowiednich dla danego środowiska.  
  
 Aby wyłączyć usługę protokołu WS-AT wewnątrz usługi MSDTC, narzędzie wsatConfig.exe za pomocą następującego polecenia.  
  
 `WsatConfig.exe –network:disable -restart`  
  
## <a name="configuring-trust-between-two-machines"></a>Konfigurowanie relacji zaufania między dwiema maszynami  
 Usługa protokołu WS-AT wymaga, aby administrator jawnie autoryzować indywidualnych kont na uczestniczenie w transakcjach rozproszonych. Jeśli jesteś administratorem dla dwóch maszyn, można skonfigurować zarówno maszyn do ustanawiania relacji wzajemnego zaufania wymiana właściwy zestaw certyfikatów między maszynami, instalując je w magazynach certyfikatów odpowiednich oraz korzystając Narzędzie wsatConfig.exe można dodać certyfikatu do każdej maszyny do drugiej strony listy autoryzowanych uczestnika certyfikatów. Ten krok jest niezbędny do wykonania transakcji rozproszonych między dwiema maszynami przy użyciu WS-AT.  
  
 W poniższym przykładzie przedstawiono kroki, aby ustanowić zaufanie między dwiema maszynami, A i B.  
  
### <a name="creating-and-exporting-certificates"></a>Tworzenie i eksportowanie certyfikatów  
 Ta procedura wymaga przystawki MMC certyfikatów. Przystawka jest możliwy, otwierając menu Start/wykonywania, wpisując "programu mmc" w polu wejściowym i naciśnięcie przycisku OK. Następnie w **Console1** okna, przejdź do **pliku/Dodaj-Usuń** przystawkę, kliknij przycisk Dodaj, a następnie wybierz **certyfikaty** z **dostępne autonomiczny Konsola** listy. Na koniec wybierz pozycję **konto komputera** do zarządzania, a następnie kliknij przycisk **OK**. **Certyfikaty** węzeł jest dostępny w konsoli przystawki.  
  
 Musisz już posiadać wymaganych certyfikatów, aby ustanowić zaufanie. Aby dowiedzieć się, jak utworzyć i zainstalować nowe certyfikaty przed następujące czynności, zobacz [jak: Tworzenie i instalowanie certyfikatów tymczasowych klienta programu WCF podczas tworzenia](https://go.microsoft.com/fwlink/?LinkId=158925).  
  
1. Na komputerze A przy użyciu przystawki MMC Certyfikaty importowania istniejącego certyfikatu (certA) LocalMachine\MY (węzeł osobiste) i Magazyn LocalMachine\ROOT (węzeł urząd certyfikacji zaufany główny urząd certyfikacji). Aby zaimportować certyfikat do określonego węzła, kliknij prawym przyciskiem myszy węzeł, a następnie wybierz **wszystkie zadania/Import**.  
  
2. Na komputerze B, za pomocą przystawki MMC certyfikatów utworzyć lub uzyskać certB certyfikatu z kluczem prywatnym i zaimportuj go do LocalMachine\MY (węzeł osobiste) i magazynem LocalMachine\ROOT (węzeł urząd certyfikacji zaufany główny urząd certyfikacji).  
  
3. Eksportuj do pliku klucza publicznego firmy certA, jeśli nie zostało to zrobione już.  
  
4. Eksportuj do pliku klucza publicznego firmy certB, jeśli nie zostało to zrobione już.  
  
### <a name="establishing-mutual-trust-between-machines"></a>Ustanawianie wzajemnego zaufania między maszynami  
  
1. Na komputerze A należy zaimportować plik reprezentacja certB do LocalMachine\MY i LocalMachine\ROOT magazynów. To deklaruje maszyny certB relacji zaufania, aby komunikować się z nim.  
  
2. Na komputerze B należy zaimportować plik certA firmy do LocalMachine\MY i LocalMachine\ROOT magazynów. Oznacza to tego komputera B certA zaufania do komunikowania się z nim.  
  
 Po wykonaniu tych kroków, zaufanie jest ustanawiane między dwoma komputerami, a następnie takie grupy można skonfigurować do komunikowania się ze sobą przy użyciu WS-AT.  
  
### <a name="configuring-msdtc-to-use-certificates"></a>Konfigurowanie usługi MSDTC, aby korzystać z certyfikatów  
 Ponieważ Usługa protokołu WS-AT pełni funkcję zarówno klient, jak i serwera, musi zarówno nasłuchiwania przychodzących połączeń i inicjują połączenia wychodzące. W związku z tym należy skonfigurować usługi MSDTC, tak aby wie o certyfikacie używanym podczas komunikowania się z zewnętrznymi i o certyfikatach, aby autoryzować akceptując przychodzącą komunikację.  
  
 Można to skonfigurować za pomocą przystawki programu MMC WS-AT. Aby uzyskać więcej informacji o tym narzędziu, zobacz [przystawki MMC konfiguracji WS-AtomicTransaction](../../../../docs/framework/wcf/ws-atomictransaction-configuration-mmc-snap-in.md) tematu. Poniżej opisano sposób ustanowić zaufanie między dwa komputery z systemem usługi MSDTC.  
  
1. Konfigurowanie ustawień maszyny A. Jako "Certyfikat punktu końcowego" Wybierz certA. W przypadku "Autoryzacji certyfikatów" Wybierz certB.  
  
2. Konfigurowanie ustawień maszyny B. Jako "Certyfikat punktu końcowego" Wybierz certB. W przypadku "Autoryzacji certyfikatów" Wybierz certA.  
  
> [!NOTE]
>  Po jednej maszynie wysyła wiadomość do innego komputera, nadawca próbuje Sprawdź, czy nazwa podmiotu certyfikatu adresata i nazwę adresata odpowiadają. Jeśli nie są zgodne, weryfikacja certyfikatu nie powiedzie się i dwóch maszyn nie mogą komunikować się.  
>   
>  Dla maszyny, przyłączone do domeny nazwa jest w pełni kwalifikowaną nazwę domeny. Domyślnie nazwa maszyny w grupie roboczej jest nazwą NetBIOS komputera. Jednak nazwa może również zawierać sufiks systemu nazw domen (DNS, Domain Name System), jeśli jest obecna dla połączenia używane między dwoma komputerami.  
>   
>  Jeśli nazwa komputera zmieni się, na przykład, gdy maszyną grupy roboczej zostanie przyłączony do domeny, musisz ponownego wystawienia certyfikatów lub ręcznie skonfigurować sufiksy DNS.  
  
## <a name="security"></a>Zabezpieczenia  
 Ponieważ niektóre ustawienia związane z MSDTC i WS-AT są przechowywane w rejestrze HKLM\Software\Microsoft\MSDTC i HKLM\Software\Microsoft\WSAT, odpowiednio, upewnij się, że te klucze rejestru są zabezpieczone, aby tylko administratorzy mogą pisać dla nich. W narzędziu Edytora rejestru, kliknij prawym przyciskiem myszy klucz, aby zabezpieczyć, a następnie wybierz pozycję **uprawnienie** można ustawić kontroli dostępu. Ma zasadnicze znaczenie bezpieczeństwa i integralności systemu to ważne, że klucze są tylko do odczytu dla użytkowników z niskim poziomem uprawnień.  
  
 Podczas wdrażania usługi MSDTC, administrator musi zapewnić, że wszelkie wymiany danych MSDTC jest bezpieczne. W przypadku wdrożenia w grupie roboczej izolowania transakcyjnych infrastruktury ze strony złośliwych użytkowników; w przypadku wdrożenia klastra zabezpieczenia rejestru klastra.  
  
## <a name="tracing"></a>Śledzenie  
 Usługa obsługuje protokół WS-AT zintegrowane transakcji, określonych śledzenie można włączyć i zarządzać nim za pośrednictwem [przystawki MMC konfiguracji WS-AtomicTransaction](../../../../docs/framework/wcf/ws-atomictransaction-configuration-mmc-snap-in.md) narzędzia.  Ślady mogą zawierać dane, wskazujący, że otrzymał podczas rejestracji zostanie przeprowadzona dla określonej transakcji czasu transakcji osiągnie swój stan końcowy, wynik każdej rejestracji transakcji. Wszystkie ślady mogą być wyświetlane za pomocą [narzędzie śledzenia usług (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) narzędzia.  
  
 Usługa protokołu WS-AT obsługuje także zintegrowane śledzenie elementu ServiceModel za pośrednictwem sesji śledzenia zdarzeń systemu Windows. Zapewnia to bardziej szczegółowe, dotyczące komunikacji ślady oprócz istniejących śledzeniach transakcji.  Aby włączyć te dodatkowe dane śledzenia, wykonaj następujące kroki  
  
1. Otwórz **uruchomienia/Start** menu, w polu wejściowym wpisz "regedit" i wybierz **OK**.  
  
2. W **Edytora rejestru**, przejdź do następującego folderu w okienku po lewej stronie Hkey_Local_Machine\SOFTWARE\Microsoft\WSAT\3.0\  
  
3. Kliknij prawym przyciskiem myszy `ServiceModelDiagnosticTracing` wartość w okienku po prawej stronie, a następnie wybierz pozycję **Modyfikuj**.  
  
4. W **dane wartości** pole wprowadzania, wprowadź jedną z poniższych prawidłowych wartości, aby określić poziom śledzenia, aby włączyć.  
  
- 0: wyłączone  
  
- 1: krytyczne  
  
- 3: błąd. Jest to wartość domyślna  
  
- 7: ostrzeżenie  
  
- 15: informacji  
  
- 31: pełne  
  
## <a name="see-also"></a>Zobacz także

- [Narzędzie do konfiguracji elementu WS-AtomicTransaction (wsatConfig.exe)](../../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)
- [Przystawka programu MMC do konfigurowania elementu WS-AtomicTransaction](../../../../docs/framework/wcf/ws-atomictransaction-configuration-mmc-snap-in.md)
