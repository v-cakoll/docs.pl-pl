---
title: Przystawka programu MMC do konfigurowania elementu WS-AtomicTransaction
ms.date: 03/30/2017
ms.assetid: 23592973-1d51-44cc-b887-bf8b0d801e9e
ms.openlocfilehash: b1d86fa57b31d1f9be12f76c28f9d042e7e28e24
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052563"
---
# <a name="ws-atomictransaction-configuration-mmc-snap-in"></a>Przystawka programu MMC do konfigurowania elementu WS-AtomicTransaction
Przystawki MMC konfiguracji WS-AtomicTransaction służy do konfigurowania część ustawień WS-AtomicTransaction na maszynach lokalnych i zdalnych.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli używasz [!INCLUDE[wxp](../../../includes/wxp-md.md)] lub [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], przystawki programu MMC można znaleźć, przechodząc do **usług składnik narzędzia administracyjne/Panel sterowania /**, kliknąć prawym przyciskiem myszy **Mój komputer**, i Wybieranie **właściwości**. Jest to tej samej lokalizacji, w którym można skonfigurować MSDTC. Opcje dostępne dla konfiguracji są pogrupowane w obszarze **WS-AT** kartę.  
  
 Jeśli używasz Windows Vista lub [!INCLUDE[lserver](../../../includes/lserver-md.md)], przystawki MMC można znaleźć, klikając pozycję **Start** przycisk i wpisując frazę `dcomcnfg.exe` w **wyszukiwania** pole. Po otwarciu programu MMC, przejdź do **Moje Computer\Distributed transakcji Coordinator\Local DTC** węzła, kliknij prawym przyciskiem myszy i wybierz **właściwości**. Opcje dostępne dla konfiguracji są pogrupowane w obszarze **WS-AT** kartę.  
  
 Poprzednie kroki są używane do uruchamiania przystawki do konfigurowania komputera lokalnego. Jeśli chcesz skonfigurować komputer zdalny, należy znaleźć nazwę maszyny zdalnej w **usług składnik narzędzia administracyjne/Panel sterowania /** i wykonać podobne kroki, jeśli używasz [!INCLUDE[wxp](../../../includes/wxp-md.md)] lub [!INCLUDE[ws2003](../../../includes/ws2003-md.md)]. Jeśli używasz Windows Vista lub [!INCLUDE[lserver](../../../includes/lserver-md.md)], wykonaj poprzednie kroki, Vista i [!INCLUDE[lserver](../../../includes/lserver-md.md)], ale **transakcji rozproszonych Coordinator\Local DTC** węzeł w węźle na komputerze zdalnym.  
  
 Aby użyć interfejsu użytkownika dostarczonego przez narzędzie, należy zarejestrować plik WsatUI.dll, który znajduje się w następującej ścieżce,  
  
 **%PROGRAMFILES%\Microsoft SDKs\Windows\v6.0\Bin\WsatUI.dll**  
  
 Rejestracja może odbywać się przez polecenie.  
  
```Output  
regasm.exe /codebase WsatUI.dll  
```  
  
 To narzędzie służy do modyfikowania podstawowych ustawień WS-AtomicTransaction. Na przykład można włączyć i wyłączyć obsługę protokołu WS-AtomicTransaction, konfigurowanie portów HTTP dla WS-AT, powiązania certyfikatu SSL z portem HTTP, skonfiguruj certyfikaty, określając nazwy podmiotu certyfikatu, wybierz tryb śledzenia i ustawić domyślną i maksymalną przekroczeń limitu czasu.  
  
 Jeśli obsługa WS-AtomicTransaction należy skonfigurować tylko na komputerze lokalnym, można użyć tego narzędzia w wersji wiersza polecenia. Aby uzyskać więcej informacji na temat narzędzia wiersza polecenia, zobacz [WS-AtomicTransaction Configuration Utility (wsatConfig.exe)](../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md) tematu.  
  
 Należy pamiętać, że zarówno przystawki MMC i narzędzie wiersza polecenia nie obsługują konfigurowania wszystkie ustawienia WS-AT. Te ustawienia można edytować tylko przez modyfikację rejestru bezpośrednio. Aby uzyskać więcej informacji na temat tych ustawień rejestru, zobacz [Konfigurowanie obsługi protokołu WS-Atomic Transaction](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md).  
  
### <a name="user-interface-description"></a>Opis interfejsu użytkownika  
 **Włącz obsługę sieci protokołu WS-Atomic Transaction**:  
  
 To pole wyboru, przełączając Włącza lub wyłącza wszystkie składniki graficznego interfejsu użytkownika tej przystawki.  
  
 Przed zaznacz to pole wyboru, należy się upewnić, włączenie dostępu do sieci usługi DTC z komunikacji przychodzącej lub wychodzącej i / lub danych. Ta wartość może zostać zweryfikowana w **zabezpieczeń** kartę przystawki usługi MSDTC.  
  
#### <a name="network-group-box"></a>Pole grupy sieci  
 W grupie sieci, można określić HTTPS port i ustawienia zabezpieczeń, takie jak szyfrowanie SSL. Ta grupa jest wyłączona (szary) Jeśli transakcje sieciowe usługi DTC nie są włączone.  
  
 **HTTPS Port**  
  
 Jest to wartość portu HTTPS używane dla WS-AT. Wartość musi być liczbą z zakresu od 1 do 65535 (do reprezentowania prawidłowy port). Zmiana portu HTTP Modyfikuje konfigurację usługi HTTP, co oznacza, że poprzednio używanych adres usługi WS-AT jest zwalniany, a nowy adres usługi WS-AT jest zarejestrowana na podstawie na nowy port. Ponadto nowo wybrany port jest szyfrowany przy użyciu aktualnie wybranego certyfikatu dla szyfrowania SSL.  
  
> [!NOTE]
>  Jeśli już włączono zaporę przed uruchomieniem tego narzędzia, numer portu jest automatycznie rejestrowane na liście wyjątków. Jeśli Zapora jest wyłączona, przed uruchomieniem tego narzędzia, żadne dodatkowe skonfigurowano dotyczące zapory.  
  
 Jeśli Zapora jest włączone po skonfigurowaniu WS-AT, należy ponownie uruchomić to narzędzie i podaj numer portu, przy użyciu tego parametru. Jeśli wyłączysz zapory po skonfigurowaniu WS-AT w dalszym ciągu działać bez dodatkowych danych wejściowych.  
  
 **Certyfikat punktu końcowego**  
  
 Klikając **wybierz** przycisk powoduje wyświetlenie listy dostępnych certyfikatów na komputerze lokalnym, dzięki czemu użytkownik wybrać certyfikat używany do szyfrowania SSL. Certyfikaty muszą mieć klucz prywatny. W przeciwnym razie zostanie wyświetlony komunikat o błędzie.  
  
> [!NOTE]
>  Po ustawieniu certyfikatu SSL dla wybranego portu jest zastąpienie oryginalnego certyfikatu SSL skojarzonych z tego portu, jeśli taka istnieje.  
  
 **Autoryzowanych kont**  
  
 Klikając **wybierz** przycisk wywołuje edytora listy kontroli dostępu Windows, w którym można określić użytkownika lub grupy, które mogą uczestniczyć w transakcjach usługi WS-Atomic, sprawdzając **Zezwalaj** lub **Odmów** pole w **uczestniczyć** grupy uprawnień.  
  
 **Autoryzowane certyfikatów**  
  
 Klikając **wybierz** przycisk powoduje wyświetlenie listy certyfikatów obecnie dostępna na użytkownika na maszynie lokalnej. Następnie możesz wybrać certyfikat tożsamości, które mogą uczestniczyć w transakcjach usługi WS-Atomic.  
  
#### <a name="timeout-group-box"></a>Pole grupy limitu czasu  
 **Limitu czasu** pole grupy umożliwia określenie domyślnego i maksymalny limit czasu dla protokołu WS-Atomic transaction. Nieprawidłowa wartość limitu czasu wychodzących jest od 1 do 3600. Jest prawidłową wartością limitu czasu przychodzących od 0 do 3600.  
  
#### <a name="tracing-and-logging-group-box"></a>Śledzenie i rejestrowanie pole grupy  
 **Śledzenie i rejestrowanie** grupy okno pozwala na skonfigurowanie żądanego śledzenia i poziom rejestrowania.  
  
 Klikając **opcje** przycisk wywołuje strony, w którym można określić dodatkowe ustawienia.  
  
 **Poziom śledzenia** kombinacji pole pozwala wybrać z dowolną prawidłową wartość <xref:System.Diagnostics.TraceLevel> wyliczenia. Można również Użyj pól wyboru, aby określić, czy chcesz przeprowadzić śledzenie aktywności, Propagacja działania lub zbierania danych osobowych użytkownika.  
  
 Można również określić sesji rejestrowania w **rejestrowania sesji** pole grupy.  
  
> [!NOTE]
>  Korzystając z innego konsumenta śledzenia jest dostawca śledzenia WS-AT, nie można utworzyć nowej sesji rejestrowania dla zdarzenia śledzenia. Każda próba Konfigurowanie rejestrowania w tym czasie powoduje komunikat o błędzie "nie można włączyć dostawcy. Kod błędu: 1".  
  
 Aby uzyskać więcej informacji dotyczących śledzenia i rejestrowania, zobacz [Administracja i Diagnostyka](../../../docs/framework/wcf/diagnostics/index.md).  
  
## <a name="see-also"></a>Zobacz także

- [Konfigurowanie obsługi protokołu WS-Atomic Transaction](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md)
- [Narzędzie do konfiguracji elementu WS-AtomicTransaction (wsatConfig.exe)](../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)
- [Administracja i diagnostyka](../../../docs/framework/wcf/diagnostics/index.md)
