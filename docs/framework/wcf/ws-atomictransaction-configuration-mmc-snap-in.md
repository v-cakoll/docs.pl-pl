---
title: Przystawka programu MMC do konfigurowania elementu WS-AtomicTransaction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 23592973-1d51-44cc-b887-bf8b0d801e9e
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 73db4b201aba6e07891803aa86c56403f135f863
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ws-atomictransaction-configuration-mmc-snap-in"></a>Przystawka programu MMC do konfigurowania elementu WS-AtomicTransaction
Przystawka programu MMC konfiguracji WS-AtomicTransaction służy do konfigurowania część ustawień protokołu WS-AtomicTransaction na komputerach lokalnych i zdalnych.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli używasz [!INCLUDE[wxp](../../../includes/wxp-md.md)] lub [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], przystawki programu MMC można znaleźć przechodząc do **usług składnik narzędzia administracyjne/Panel sterowania /**, klikając prawym przyciskiem myszy **Mój komputer**, i Wybieranie **właściwości**. To jest tej samej lokalizacji, w którym można skonfigurować usługi MSDTC. Opcje dostępne dla konfiguracji są pogrupowane w obszarze **WS-AT** kartę.  
  
 Jeśli używasz systemu Windows Vista lub [!INCLUDE[lserver](../../../includes/lserver-md.md)], przystawki programu MMC można znaleźć, klikając **Start** przycisk, a następnie wpisując w `dcomcnfg.exe` w **wyszukiwania** pole. Po otwarciu programu MMC, przejdź do **Moje Computer\Distributed transakcji Coordinator\Local DTC** węzeł, kliknij prawym przyciskiem myszy i wybierz **właściwości**. Opcje dostępne dla konfiguracji są pogrupowane w obszarze **WS-AT** kartę.  
  
 Poprzednie kroki są używane do uruchamiania przystawki do konfigurowania komputera lokalnego. Jeśli chcesz skonfigurować komputer zdalny, należy zlokalizować nazwy maszyny zdalnej w **usług składnik narzędzia administracyjne/Panel sterowania /**i wykonywać podobne kroki, jeśli używasz [!INCLUDE[wxp](../../../includes/wxp-md.md)] lub [!INCLUDE[ws2003](../../../includes/ws2003-md.md)]. Jeśli używasz systemu Windows Vista lub [!INCLUDE[lserver](../../../includes/lserver-md.md)], wykonaj poprzednie kroki dla Vista i [!INCLUDE[lserver](../../../includes/lserver-md.md)], ale użyj **transakcji rozproszonych Coordinator\Local DTC** węzeł w węźle na komputerze zdalnym.  
  
 Aby korzystać z interfejsu użytkownika dostarczanych przez narzędzie, należy zarejestrować plik WsatUI.dll, który znajduje się w następującej ścieżce,  
  
 **%ProgramFiles%\Microsoft SDKs\Windows\v6.0\Bin\WsatUI.dll**  
  
 Rejestracja może odbywać się za pomocą następującego polecenia.  
  
```Output  
regasm.exe /codebase WsatUI.dll  
```  
  
 Za pomocą tego narzędzia, aby zmodyfikować ustawienia protokołu WS-AtomicTransaction podstawowe. Na przykład możesz można włączyć i wyłączyć obsługę protokołu WS-AtomicTransaction konfigurowania portów HTTP WS-AT, powiązania certyfikatu SSL z portem HTTP, konfigurowanie certyfikatów przez określenie nazwy podmiotu certyfikatu, wybierz tryb śledzenia i ustawić domyślne i maksymalna liczba przekroczeń limitu czasu.  
  
 Jeśli należy skonfigurować obsługę protokołu WS-AtomicTransaction tylko na komputerze lokalnym, można użyć wersji to narzędzie wiersza polecenia. [!INCLUDE[crabout](../../../includes/crabout-md.md)]Narzędzie wiersza polecenia, zobacz [narzędzia konfiguracji WS-AtomicTransaction (wsatConfig.exe)](../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md) tematu.  
  
 Należy pamiętać, że zarówno przystawki programu MMC i narzędzie wiersza polecenia nie obsługują konfigurowania wszystkich ustawień protokołu WS-AT. Te ustawienia można edytować tylko przez modyfikację rejestru bezpośrednio. [!INCLUDE[crabout](../../../includes/crabout-md.md)]te ustawienia rejestru, zobacz [Konfigurowanie obsługi protokołu WS-AT transakcji](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md).  
  
### <a name="user-interface-description"></a>Opis interfejsu użytkownika  
 **Włącz obsługę sieci WS-Atomic Transaction**:  
  
 Przełączanie tego pola wyboru włącza lub wyłącza wszystkie składniki graficznego interfejsu użytkownika dla tej przystawki.  
  
 Przed zaznacz to pole wyboru użytkownik powinien upewnić się, włączenia usługi Network DTC Access komunikacji przychodzącej lub wychodzącej lub oba. Tę wartość można sprawdzić w **zabezpieczeń** kartę przystawki usługi MSDTC.  
  
#### <a name="network-group-box"></a>Pole grupy sieci  
 W grupie sieciowych można określić HTTPS port i ustawienia dodatkowe zabezpieczenia, takie jak szyfrowania SSL. Ta grupa jest wyłączone (szary) Jeśli transakcji sieci usługi DTC nie są włączone.  
  
 **HTTPS Port**  
  
 Jest to wartość portu HTTPS używane dla protokołu WS-AT. Wartość musi być liczbą z zakresu od 1 do 65535 (do reprezentowania prawidłowy port). Zmiana portu HTTP Modyfikuje konfigurację usługi HTTP, co oznacza, że wcześniej używanych adres usługi WS-AT zostanie zwolniony i nowego adresu usługi WS-AT jest zarejestrowana na podstawie na nowy port. Ponadto nowo wybrany port jest szyfrowany przy aktualnie wybranego certyfikatu do szyfrowania SSL.  
  
> [!NOTE]
>  Jeśli Zapora jest jeszcze włączone, przed uruchomieniem tego narzędzia, numer portu jest automatycznie rejestrowane na liście wyjątków. Jeśli Zapora jest wyłączone przed uruchomieniem tego narzędzia, żadne dodatkowe skonfigurowano dotyczące zapory.  
  
 Jeśli Zapora jest włączone po skonfigurowaniu usługi WS-AT, należy ponownie uruchomić to narzędzie i podaj numer portu, za pomocą tego parametru. Wyłączenie zapory po skonfigurowaniu, WS-AT w dalszym ciągu działać bez dodatkowych danych wejściowych.  
  
 **Certyfikat punktu końcowego**  
  
 Kliknięcie przycisku **wybierz** przycisk Wyświetla listę dostępnych certyfikatów na komputerze lokalnym, co pozwala użytkownikowi na wybranie certyfikatu, który może być używany do szyfrowania SSL. Certyfikaty musi mieć klucz prywatny. W przeciwnym razie zostanie wyświetlony komunikat o błędzie.  
  
> [!NOTE]
>  Po ustawieniu certyfikatu SSL dla wybranego portu możesz zastąpić oryginalny certyfikat SSL skojarzony z tego portu, jeśli taka istnieje.  
  
 **Autoryzowanych kont**  
  
 Kliknięcie przycisku **wybierz** przycisk wywołuje edytora listy kontroli dostępu do systemu Windows, w którym można określić użytkownika lub grupy, które mogą uczestniczyć w transakcji protokołu WS-AT sprawdzając **Zezwalaj** lub **Odmów** polu **uczestniczyć** grupy uprawnień.  
  
 **Autoryzowany certyfikatów**  
  
 Kliknięcie przycisku **wybierz** przycisku zostanie wyświetlona lista aktualnie dostępnych certyfikatów na LocalMachine. Następnie możesz wybrać tożsamości certyfikatów, które są dozwolone na uczestniczenie w transakcjach protokołu WS-AT.  
  
#### <a name="timeout-group-box"></a>Pole grupy limitu czasu  
 **Limitu czasu** pole grupy służy do określenia domyślnej i maksymalny limit czasu dla protokołu WS-Atomic transaction. Nieprawidłowa wartość Limit czasu operacji wychodzących jest zakresu od 1 do 3600. Nieprawidłowa wartość Limit czasu operacji przychodzących jest zakresu od 0 do 3600.  
  
#### <a name="tracing-and-logging-group-box"></a>Śledzenie i rejestrowanie pola grupy  
 **Śledzenie i rejestrowanie** grupy pole umożliwia skonfigurowanie żądanego śledzenia i poziom rejestrowania.  
  
 Kliknięcie przycisku **opcje** przycisk wywołuje strony, w którym można określić dodatkowe ustawienia.  
  
 **Poziom śledzenia** kombinacja pole pozwala wybrać od dowolnej wartości prawidłowe <xref:System.Diagnostics.TraceLevel> wyliczenia. Aby określić, czy chcesz wykonać czynność śledzenia propagacji działania lub zbierać dane osobowe umożliwia także pola wyboru.  
  
 Można również określić sesji rejestrowania w **rejestrowania sesji** pole grupy.  
  
> [!NOTE]
>  Korzystając z innego klienta śledzenia jest dostawca śledzenia WS-AT, nie można utworzyć nowej sesji rejestrowania śledzenia zdarzeń. Aby skonfigurować rejestrowanie w tym czasie wszystkie próby wyniki w komunikacie o błędzie "nie można włączyć dostawcy. Kod błędu: 1".  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]Śledzenie i rejestrowanie, zobacz [Administracja i Diagnostyka](../../../docs/framework/wcf/diagnostics/index.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie obsługi protokołu WS-Atomic Transaction](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md)  
 [Narzędzie do konfiguracji elementu WS-AtomicTransaction (wsatConfig.exe)](../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)  
 [Administracja i diagnostyka](../../../docs/framework/wcf/diagnostics/index.md)
