---
title: Przystawka programu MMC do konfigurowania elementu WS-AtomicTransaction
ms.date: 03/30/2017
ms.assetid: 23592973-1d51-44cc-b887-bf8b0d801e9e
ms.openlocfilehash: 04380a2a30aba85efb98ee8f9e24d0a6223a18a3
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320329"
---
# <a name="ws-atomictransaction-configuration-mmc-snap-in"></a>Przystawka programu MMC do konfigurowania elementu WS-AtomicTransaction
Przystawka programu MMC Konfiguracja protokołu WS-AtomicTransaction służy do konfigurowania części ustawień protokołu WS-AtomicTransaction na maszynach lokalnych i zdalnych.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli używasz [!INCLUDE[wxp](../../../includes/wxp-md.md)] lub [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], przystawka MMC można znaleźć, przechodząc do **Panelu sterowania/narzędzia administracyjne/Składniki usługi/** , klikając prawym przyciskiem myszy pozycję **mój komputer**, a następnie wybierając polecenie **Właściwości**. Jest to ta sama lokalizacja, w której można skonfigurować usługę MSDTC. Opcje dostępne dla konfiguracji są pogrupowane pod kartą **WS-AT** .  
  
 W przypadku korzystania z systemu Windows Vista lub [!INCLUDE[lserver](../../../includes/lserver-md.md)] można znaleźć przystawkę programu MMC, klikając przycisk **Start** i wpisując ciąg w `dcomcnfg.exe` w polu **wyszukiwania** . Po otwarciu programu MMC przejdź do węzła **My Computer\Distributed Transaction COORDINATOR\LOCAL DTC** , kliknij prawym przyciskiem myszy i wybierz pozycję **Właściwości**. Opcje dostępne dla konfiguracji są pogrupowane pod kartą **WS-AT** .  
  
 Poprzednie kroki służą do uruchomienia przystawki do konfigurowania komputera lokalnego. Aby skonfigurować maszynę zdalną, należy zlokalizować nazwę maszyny zdalnej w **Panelu sterowania/narzędzia administracyjne/usługi składowe/** , a następnie wykonać podobne czynności, jeśli jest uruchomiony program [!INCLUDE[wxp](../../../includes/wxp-md.md)] lub [!INCLUDE[ws2003](../../../includes/ws2003-md.md)]. W przypadku korzystania z systemu Windows Vista lub [!INCLUDE[lserver](../../../includes/lserver-md.md)] wykonaj poprzednie kroki dla systemu Vista i [!INCLUDE[lserver](../../../includes/lserver-md.md)], ale Użyj węzła **usługi Distributed Transaction Coordinator\Local DTC** w węźle komputera zdalnego.  
  
 Aby użyć interfejsu użytkownika dostarczonego przez narzędzie, należy zarejestrować plik WsatUI. dll, który znajduje się w następującej ścieżce:  
  
 **%PROGRAMFILES%\Microsoft SDKs\Windows\v6.0\Bin\WsatUI.dll**  
  
 Rejestrację można wykonać za pomocą następującego polecenia.  
  
```console
regasm.exe /codebase WsatUI.dll  
```  
  
 Za pomocą tego narzędzia można modyfikować podstawowe ustawienia protokołu WS-AtomicTransaction. Można na przykład włączyć i wyłączyć obsługę protokołu WS-AtomicTransaction, skonfigurować porty HTTP dla usługi WS-AT, powiązać certyfikat protokołu SSL z portem HTTP, skonfigurować certyfikaty przez określenie nazw podmiotów certyfikatów, wybrać tryb śledzenia i ustawić domyślne i maksymalne limity czasu.  
  
 Jeśli musisz skonfigurować obsługę protokołu WS-AtomicTransaction tylko na komputerze lokalnym, możesz użyć wersji wiersza polecenia tego narzędzia. Aby uzyskać więcej informacji na temat narzędzia wiersza polecenia, zobacz temat [Narzędzie konfiguracji protokołu WS-AtomicTransaction (wsatConfig. exe)](ws-atomictransaction-configuration-utility-wsatconfig-exe.md) .  
  
 Należy pamiętać, że zarówno przystawka programu MMC, jak i narzędzie wiersza polecenia nie obsługują konfigurowania wszystkich ustawień usługi WS-AT. Te ustawienia można edytować tylko poprzez bezpośrednie Modyfikowanie rejestru. Aby uzyskać więcej informacji na temat tych ustawień rejestru, zobacz [Konfigurowanie obsługi transakcji WS-AT](./feature-details/configuring-ws-atomic-transaction-support.md).  
  
### <a name="user-interface-description"></a>Opis interfejsu użytkownika  
 **Włącz obsługę sieci WS-Bioatom transakcji**:  
  
 Przełączenie tego pola wyboru włącza lub wyłącza wszystkie składniki graficznego interfejsu użytkownika w tej przystawce.  
  
 Przed zaznaczeniem tego pola wyboru upewnij się, że dostęp do usługi Network DTC jest włączony przy użyciu komunikacji przychodzącej lub wychodzącej. Tę wartość można zweryfikować na karcie **zabezpieczenia** w przystawce MSDTC.  
  
#### <a name="network-group-box"></a>Pole grupy sieciowej  
 W grupie sieci można określić port HTTPS i dodatkowe ustawienia zabezpieczeń, takie jak szyfrowanie SSL. Ta grupa jest wyłączona (wyszarzona), jeśli transakcje sieci usługi DTC nie są włączone.  
  
 **Port HTTPS**  
  
 Jest to wartość portu HTTPS używanego w usłudze WS-AT. Wartość musi być liczbą z zakresu 1-65535 (tak, aby reprezentować prawidłowy port). Zmiana portu HTTP modyfikuje konfigurację usługi HTTP, co oznacza, że poprzednio używany adres usługi WS-AT jest wydawany, a nowy adres usługi WS-AT jest rejestrowany w oparciu o nowy port. Ponadto nowo wybrany port jest szyfrowany przy użyciu aktualnie wybranego certyfikatu na potrzeby szyfrowania SSL.  
  
> [!NOTE]
> Jeśli Zapora została już włączona przed uruchomieniem tego narzędzia, port zostanie automatycznie zarejestrowany na liście wyjątków. Jeśli Zapora jest wyłączona przed uruchomieniem tego narzędzia, dla zapory nic nie skonfigurowano.  
  
 Jeśli Zapora zostanie włączona po skonfigurowaniu usługi WS-AT, należy ponownie uruchomić to narzędzie i podać numer portu przy użyciu tego parametru. Wyłączenie zapory po skonfigurowaniu usługi WS-AT kontynuuje pracę bez dodatkowych danych wejściowych.  
  
 **Certyfikat punktu końcowego**  
  
 Kliknięcie przycisku **Wybierz** spowoduje wyświetlenie listy z aktualnie dostępnymi certyfikatami na komputerze lokalnym, umożliwiając użytkownikowi wybranie certyfikatu, którego można użyć do szyfrowania SSL. Certyfikaty muszą mieć klucz prywatny. W przeciwnym razie zostanie wyświetlony komunikat o błędzie.  
  
> [!NOTE]
> Po ustawieniu certyfikatu protokołu SSL dla wybranego portu zastępowany jest oryginalny certyfikat SSL skojarzony z tym portem, jeśli taki istnieje.  
  
 **Autoryzowane konta**  
  
 Kliknięcie przycisku **Wybierz** wywołuje edytor listy Access Control systemu Windows, w którym można określić użytkownika lub grupę, która może uczestniczyć w transakcjach WS-Atom, zaznaczając pole **Zezwalaj** lub **Odmów** w obszarze **uczestnictwo** . Grupa uprawnień.  
  
 **Autoryzowane certyfikaty**  
  
 Kliknięcie przycisku **Wybierz** spowoduje wyświetlenie listy aktualnie dostępnych certyfikatów w LocalMachine. Następnie możesz wybrać, które tożsamości certyfikatów mogą uczestniczyć w transakcjach WS-AT.  
  
#### <a name="timeout-group-box"></a>Pole grupy limitów czasu  
 Pole grupy **limit czasu** umożliwia określenie domyślnego i maksymalnego limitu czasu dla transakcji WS-AT. Prawidłowa wartość limitu czasu wychodzącego wynosi od 1 do 3600. Prawidłowa wartość limitu czasu dla ruchu przychodzącego to od 0 do 3600.  
  
#### <a name="tracing-and-logging-group-box"></a>Śledzenie i rejestrowanie pola grupy  
 Pole **śledzenie i Grupa rejestrowania** umożliwia skonfigurowanie żądanego poziomu śledzenia i rejestrowania.  
  
 Kliknięcie przycisku **Opcje** powoduje wywołanie strony, na której można określić dodatkowe ustawienia.  
  
 Pole kombinacja **poziomu śledzenia** umożliwia wybranie dowolnej prawidłowej wartości wyliczenia <xref:System.Diagnostics.TraceLevel>. Możesz również użyć pól wyboru, aby określić, czy chcesz przeprowadzić śledzenie działań, propagację działań czy zbierać informacje osobiste.  
  
 Możesz również określić sesje rejestrowania w polu Grupa **sesji rejestrowania** .  
  
> [!NOTE]
> Gdy inny odbiorca śledzenia korzysta z dostawcy śledzenia WS-AT, nie można utworzyć nowej sesji rejestrowania dla zdarzeń śledzenia. Każda próba skonfigurowania rejestrowania w tym czasie powoduje, że w komunikacie o błędzie "nie można włączyć dostawcy. Kod błędu: 1 ".  
  
 Aby uzyskać więcej informacji na temat śledzenia i rejestrowania, zobacz [administrowanie i Diagnostyka](./diagnostics/index.md).  
  
## <a name="see-also"></a>Zobacz także

- [Konfigurowanie obsługi protokołu WS-Atomic Transaction](./feature-details/configuring-ws-atomic-transaction-support.md)
- [Narzędzie do konfiguracji elementu WS-AtomicTransaction (wsatConfig.exe)](ws-atomictransaction-configuration-utility-wsatconfig-exe.md)
- [Administracja i diagnostyka](./diagnostics/index.md)
