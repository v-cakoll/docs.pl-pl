---
title: Konfigurowanie obsługi protokołu WS-Atomic Transaction
ms.date: 03/30/2017
helpviewer_keywords:
- WS-AT protocol [WCF], configuring WS-Atomic Transaction
ms.assetid: cb9f1c9c-1439-4172-b9bc-b01c3e09ac48
ms.openlocfilehash: d396ccdaca81eab74de5e20d7ba7a9a00acbf7a6
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597478"
---
# <a name="configure-ws-atomic-transaction-support"></a>Konfigurowanie obsługi transakcji WS-AT

W tym temacie opisano, jak można skonfigurować obsługę protokołu WS-AtomicTransaction (WS-AT) przy użyciu narzędzia konfiguracji WS-AT.

## <a name="use-the-ws-at-configuration-utility"></a>Korzystanie z narzędzia konfiguracji WS-AT

Narzędzie konfiguracji WS-AT (wsatConfig. exe) służy do konfigurowania ustawień usługi WS-AT. Aby włączyć usługę protokołu WS-AT, należy użyć narzędzia konfiguracji, aby skonfigurować port HTTPS dla usługi WS-AT, powiązać certyfikat X. 509 z portem HTTPS i skonfigurować autoryzowane certyfikaty partnerów przez określenie nazw podmiotu certyfikatu lub odcisków palców. Narzędzie konfiguracji umożliwia również wybranie trybu śledzenia i ustawienie domyślnych limitów czasu transakcji przychodzących i maksymalnych.

Dostęp do funkcji tego narzędzia można uzyskać za pomocą przystawki Strona właściwości programu Microsoft Management Console (MMC) w konsoli zarządzania usługami składowych lub z okna wiersza polecenia. Skonfiguruj obsługę WS-AT na komputerze lokalnym za pomocą okna wiersza polecenia. Skonfiguruj ustawienia na maszynach lokalnych i zdalnych przy użyciu przystawki programu MMC.

Dostęp do okna wiersza polecenia można uzyskać w lokalizacji instalacji Windows SDK "%WINDIR%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation".

Aby uzyskać więcej informacji na temat narzędzia wiersza polecenia, zobacz [Narzędzie konfiguracji protokołu WS-AtomicTransaction (wsatConfig. exe)](../ws-atomictransaction-configuration-utility-wsatconfig-exe.md).

Jeśli korzystasz z systemu Windows XP lub Windows Server 2003, możesz uzyskać dostęp do przystawki programu MMC, przechodząc do **Panelu sterowania/narzędzia administracyjne/usługi składowe**, klikając prawym przyciskiem myszy pozycję **mój komputer**, a następnie wybierając polecenie **Właściwości**. Jest to ta sama lokalizacja, w której można skonfigurować usługę Microsoft Distributed Transaction Coordinator (MSDTC). Opcje dostępne dla konfiguracji są pogrupowane pod kartą **WS-AT** . W przypadku korzystania z systemu Windows Vista lub Windows Server 2008 przystawka MMC można znaleźć, klikając przycisk **Start** i wprowadzając `dcomcnfg.exe` w polu **wyszukiwania** . Po otwarciu programu MMC przejdź do węzła **My Computer\Distributed Transaction COORDINATOR\LOCAL DTC** , kliknij prawym przyciskiem myszy i wybierz pozycję **Właściwości**. Opcje dostępne dla konfiguracji są pogrupowane pod kartą **WS-AT** .

Aby uzyskać więcej informacji o przystawce, zobacz [Przystawka programu MMC Konfiguracja protokołu WS-AtomicTransaction](../ws-atomictransaction-configuration-mmc-snap-in.md).

Aby włączyć interfejs użytkownika narzędzia, należy najpierw zarejestrować plik WsatUI. dll znajdujący się w następującej ścieżce

%PROGRAMFILES%\Microsoft SDKs\Windows\v6.0\Bin

Aby zarejestrować produkt, wykonaj następujące polecenie w oknie wiersza polecenia:

`regasm.exe /codebase WsatUI.dll`

## <a name="enable-ws-at"></a>Włącz usługę WS-AT

Aby włączyć usługę protokołu WS-AT w usłudze MSDTC przy użyciu portu 443 i certyfikatu X. 509 z kluczem prywatnym, który został zainstalowany w magazynie komputera lokalnego, należy użyć narzędzia wsatConfig. exe z następującym poleceniem.

`WsatConfig.exe –network:enable –port:8443 –endpointCert:<machine|"Issuer\SubjectName"> -accountsCerts:<thumbprint|"Issuer\SubjectName"> -restart`

Zamień odpowiednie parametry na wartości odpowiednie dla danego środowiska.

Aby wyłączyć usługę protokołu WS-AT w usłudze MSDTC, należy użyć narzędzia wsatConfig. exe z następującym poleceniem.

`WsatConfig.exe –network:disable -restart`

## <a name="configure-trust-between-two-machines"></a>Skonfiguruj relację zaufania między dwoma komputerami

Usługa protokołu WS-AT wymaga, aby administrator jawnie autoryzuje poszczególne konta do udziału w transakcjach rozproszonych. Jeśli jesteś administratorem dwóch maszyn, możesz skonfigurować oba komputery w celu ustanowienia relacji wzajemnego zaufania przez wymianę odpowiedniego zestawu certyfikatów między maszynami, zainstalowanie ich w odpowiednich magazynach certyfikatów i użycie narzędzia wsatConfig. exe do dodania certyfikatu każdej maszyny do listy autoryzowanych certyfikatów uczestników. Ten krok jest niezbędny do wykonania transakcji rozproszonych między dwoma maszynami przy użyciu usługi WS-AT.

W poniższym przykładzie przedstawiono kroki, aby ustanowić relację zaufania między dwoma komputerami, a i B.

### <a name="create-and-export-certificates"></a>Tworzenie i eksportowanie certyfikatów

Ta procedura wymaga przystawki Certyfikaty programu MMC. Dostęp do przystawki można uzyskać, otwierając menu Start/Run, wpisując "MMC" w polu wejściowym i naciskając przycisk OK. Następnie w oknie **Console1** przejdź do **pliku/Dodaj/Usuń** przystawkę, kliknij przycisk Dodaj, a następnie wybierz pozycję **Certyfikaty** z listy **dostępne autonomiczne przystawki** . Na koniec wybierz pozycję **konto komputera** , aby zarządzać, a następnie kliknij przycisk **OK**. W konsoli przystawki zostanie wyświetlony węzeł **Certyfikaty** .

Musisz mieć już wymagane certyfikaty, aby ustanowić relację zaufania. Aby dowiedzieć się, jak tworzyć i instalować nowe certyfikaty przed wykonaniem poniższych kroków, zobacz [How to: Create i Install Temporary Client Certificates in WCF podczas tworzenia](https://docs.microsoft.com/previous-versions/msp-n-p/ff650751(v=pandp.10)).

1. Na maszynie A, za pomocą przystawki Certyfikaty programu MMC, zaimportuj istniejący certyfikat (certyfikat) do LocalMachine\MY (węzeł prywatny) i magazyn LocalMachine\ROOT (węzeł zaufanego głównego urzędu certyfikacji). Aby zaimportować certyfikat do określonego węzła, kliknij prawym przyciskiem myszy węzeł i wybierz polecenie **wszystkie zadania/Importuj**.

2. Na komputerze B, za pomocą przystawki Certyfikaty programu MMC, Utwórz lub uzyskaj certyfikat certB z kluczem prywatnym i zaimportuj go do magazynu LocalMachine\MY (osobiste) i LocalMachine\ROOT (węzeł zaufanego głównego urzędu certyfikacji).

3. Wyeksportuj klucz publiczny certyfikatu do pliku, jeśli nie został on jeszcze wykonany.

4. Wyeksportuj klucz publiczny certB do pliku, jeśli nie został on jeszcze wykonany.

### <a name="establish-mutual-trust-between-machines"></a>Ustanów wzajemne zaufanie między maszynami

1. Na maszynie A zaimportuj reprezentację certB do magazynów LocalMachine\MY i LocalMachine\ROOT. Deklaruje, że maszyna A ufa certB do komunikacji z nią.

2. Na komputerze B Zaimportuj plik certyfikatu do magazynów LocalMachine\MY i LocalMachine\ROOT. Oznacza to, że komputer B ufa certyfikatowi w celu komunikowania się z nim.

Po wykonaniu tych kroków zaufanie jest nawiązywane między tymi dwoma komputerami i można je skonfigurować w taki sposób, aby komunikować się ze sobą przy użyciu usługi WS-AT.

### <a name="configure-msdtc-to-use-certificates"></a>Konfigurowanie usługi MSDTC do używania certyfikatów

Ponieważ usługa protokołu WS-AT działa zarówno jako klient, jak i serwer, musi nasłuchiwać połączeń przychodzących i inicjować połączenia wychodzące. W związku z tym należy skonfigurować usługę MSDTC, aby znać certyfikat używany podczas komunikacji z podmiotami zewnętrznymi oraz certyfikaty, które mają być autoryzowane przy akceptowaniu komunikacji przychodzącej.

Można to skonfigurować za pomocą przystawki MMC WS-AT. Aby uzyskać więcej informacji na temat tego narzędzia, zobacz temat [Przystawka programu MMC Konfiguracja protokołu WS-AtomicTransaction](../ws-atomictransaction-configuration-mmc-snap-in.md) . W poniższych krokach opisano, jak ustanowić relację zaufania między dwoma komputerami z uruchomioną usługą MSDTC.

1. Skonfiguruj ustawienia maszyny A. W obszarze "certyfikat punktu końcowego" Wybierz pozycję certyfikat a. W polu "autoryzowane certyfikaty" Wybierz pozycję certB.

2. Skonfiguruj ustawienia maszyny B. W obszarze "certyfikat punktu końcowego" Wybierz pozycję certB. W polu "autoryzowane certyfikaty" Wybierz certyfikat.

> [!NOTE]
> Gdy jeden komputer wysyła komunikat do innej maszyny, nadawca podejmuje próbę sprawdzenia, czy nazwa podmiotu certyfikatu odbiorcy i nazwa komputera adresata są zgodne. Jeśli nie są zgodne, weryfikacja certyfikatu kończy się niepowodzeniem, a dwa komputery nie mogą się komunikować.
>
> W przypadku komputera przyłączonego do domeny nazwa jest w pełni kwalifikowaną nazwą domeny. Domyślnie nazwa komputera w grupie roboczej to nazwa NetBIOS komputera. Jednak nazwa może również zawierać sufiks DNS (Domain Name System), jeśli istnieje dla połączenia używanego między tymi dwoma komputerami.
>
> W przypadku zmiany nazwy komputera, na przykład gdy komputer grupy roboczej jest przyłączony do domeny, należy ponownie wydać certyfikaty lub ręcznie skonfigurować sufiksy DNS.

## <a name="security"></a>Zabezpieczenia

Ponieważ niektóre ustawienia dotyczące usługi MSDTC i WS-AT są przechowywane w rejestrze w HKLM\Software\Microsoft\MSDTC i HKLM\Software\Microsoft\WSAT, upewnij się, że te klucze rejestru są zabezpieczone, tak aby tylko Administratorzy mogli zapisywać w nich. W narzędziu Edytor rejestru kliknij prawym przyciskiem myszy klucz, który chcesz zabezpieczyć, a następnie wybierz pozycję **uprawnienie** , aby ustawić odpowiednią kontrolę dostępu. Kluczową kwestią bezpieczeństwa i integralności systemu jest to, że ważne klucze są tylko do odczytu dla użytkowników z niskimi uprawnieniami.

Podczas wdrażania usługi MSDTC administrator musi upewnić się, że wszystkie wymiany danych usługi MSDTC są bezpieczne. W przypadku wdrożenia grupy roboczej należy odizolować infrastrukturę transakcyjną od złośliwych użytkowników. w przypadku wdrożenia klastra Zabezpiecz rejestr klastra.

## <a name="tracing"></a>Śledzenie

Usługa protokołu WS-AT obsługuje zintegrowane, specyficzne dla transakcji śledzenie, które może być włączone i zarządzane za pomocą narzędzia [MMC konfiguracja usługi WS-AtomicTransaction](../ws-atomictransaction-configuration-mmc-snap-in.md) . Ślady mogą zawierać dane wskazujące czas rejestracji dla konkretnej transakcji, czas, w którym transakcja osiągnie swój stan, a także otrzymać wyniki każdej rejestracji transakcji. Wszystkie ślady można wyświetlić za pomocą narzędzia [Podgląd śledzenia usług (SvcTraceViewer. exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) .

Usługa protokołu WS-AT obsługuje również zintegrowane śledzenie ServiceModel przez sesję śledzenia ETW. Zawiera bardziej szczegółowe dane śledzenia dotyczące komunikacji oprócz istniejących śladów transakcji.  Aby włączyć te dodatkowe ślady, wykonaj następujące kroki

1. Otwórz menu **Start/Run** , w polu wejściowym wpisz ciąg "regedit" i wybierz polecenie **OK**.

2. W **Edytorze rejestru**przejdź do następującego folderu w lewym okienku, Hkey_Local_Machine \software\microsoft\wsat\3.0\

3. Kliknij prawym przyciskiem myszy `ServiceModelDiagnosticTracing` wartość w prawym okienku, a następnie wybierz polecenie **Modyfikuj**.

4. W polu wejściowym **dane wartości** Wprowadź jedną z następujących prawidłowych wartości, aby określić poziom śledzenia, który ma zostać włączony.

- 0: wyłączone

- 1: krytyczne

- 3: błąd. Jest to wartość domyślna

- 7: Ostrzeżenie

- 15: informacje

- 31: pełne

## <a name="see-also"></a>Zobacz też

- [Narzędzie do konfiguracji elementu WS-AtomicTransaction (wsatConfig.exe)](../ws-atomictransaction-configuration-utility-wsatconfig-exe.md)
- [Przystawka programu MMC do konfigurowania elementu WS-AtomicTransaction](../ws-atomictransaction-configuration-mmc-snap-in.md)
