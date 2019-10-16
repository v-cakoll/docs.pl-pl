---
title: Narzędzie do konfiguracji elementu WS-AtomicTransaction (wsatConfig.exe)
ms.date: 03/30/2017
ms.assetid: 1c56cf98-3963-46d5-a4e1-482deae58c58
ms.openlocfilehash: 5333c9c5caad502ce925fe4a45a039c553812ba6
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320197"
---
# <a name="ws-atomictransaction-configuration-utility-wsatconfigexe"></a>Narzędzie do konfiguracji elementu WS-AtomicTransaction (wsatConfig.exe)
Narzędzie konfiguracji protokołu WS-AtomicTransaction służy do konfigurowania podstawowych ustawień obsługi WS-AtomicTransaction.  
  
## <a name="syntax"></a>Składnia  
  
```  
wsatConfig [Options]  
```  
  
## <a name="remarks"></a>Uwagi  
 Za pomocą tego narzędzia wiersza polecenia można skonfigurować podstawowe ustawienia usługi WS-AT tylko na komputerze lokalnym. Jeśli konieczne jest skonfigurowanie ustawień na maszynach lokalnych i zdalnych, należy użyć przystawki programu MMC zgodnie z opisem w temacie [Konfigurowanie obsługi transakcji WS-AT](./feature-details/configuring-ws-atomic-transaction-support.md).  
  
 Narzędzie wiersza polecenia można znaleźć w lokalizacji instalacji Windows SDK, w tym,  
  
 %SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\wsatConfig.exe  
  
 Jeśli używasz [!INCLUDE[wxp](../../../includes/wxp-md.md)] lub [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], musisz pobrać aktualizację przed uruchomieniem programu WsatConfig. exe. Aby uzyskać więcej informacji o tej aktualizacji, zobacz [Update for Commerce Server 2007 (KB912817)](https://go.microsoft.com/fwlink/?LinkId=95340) i [dostępność pakietu zbiorczego poprawek dla systemu Windows XP com+](https://go.microsoft.com/fwlink/?LinkId=95341).  
  
 W poniższej tabeli przedstawiono opcje, które mogą być używane z narzędziem konfiguracji protokołu WS-AtomicTransaction (wsatConfig. exe).  
  
> [!NOTE]
> Po ustawieniu certyfikatu protokołu SSL dla wybranego portu zastępowany jest oryginalny certyfikat SSL skojarzony z tym portem, jeśli taki istnieje.  
  
|Opcje|Opis|  
|-------------|-----------------|  
|-accounts: \<account, >|Określa rozdzieloną przecinkami listę kont, które mogą uczestniczyć w usłudze WS-AtomicTransaction. Ważność tych kont nie jest sprawdzana.|  
|-accountsCerts: \<thumb >&#124;"Issuer\SubjectName", >|Określa rozdzieloną przecinkami listę certyfikatów, które mogą uczestniczyć w usłudze WS-AtomicTransaction. Certyfikaty są wskazywane przez odcisk palca lub parę Issuer\SubjectName. Użyj {EMPTY} dla nazwy podmiotu, jeśli jest pusta.|  
|-endpointCert: < Machine&#124;\<thumb >&#124;"Issuer\SubjectName" >|Używa certyfikatu komputera lub innego lokalnego certyfikatu punktu końcowego określonego za pomocą odcisku palca lub pary Issuer\SubjectName. Używa elementu {EMPTY} dla nazwy podmiotu, jeśli jest pusta.|  
|-maxTimeout: \<sec >|Określa maksymalny limit czasu w sekundach. Prawidłowe wartości to od 0 do 3600.|  
|-Sieć: @no__t&#124;wyłączyć >|Włącza lub wyłącza obsługę sieci WS-AtomicTransaction.|  
|-Port: \<portNum >|Ustawia port HTTPS dla protokołu WS-AtomicTransaction.<br /><br /> Jeśli Zapora została już włączona przed uruchomieniem tego narzędzia, port zostanie automatycznie zarejestrowany na liście wyjątków. Jeśli Zapora jest wyłączona przed uruchomieniem tego narzędzia, dla zapory nic nie skonfigurowano.<br /><br /> W przypadku włączenia zapory po skonfigurowaniu usługi WS-AT należy ponownie uruchomić to narzędzie i podać numer portu przy użyciu tego parametru. Jeśli po skonfigurowaniu Zapora zostanie wyłączona, Usługa WS-AT będzie nadal działała bez dodatkowych danych wejściowych.|  
|-timeout: \<sec >|Określa domyślny limit czasu (w sekundach). Prawidłowe wartości to od 1 do 3600.|  
|-traced: \<enable&#124;Disable >|Włącza lub wyłącza śledzenie zdarzeń działania.|  
|-traceLevel: \<Off&#124;błędu&#124;krytyczne&#124;informacje&#124;o&#124; ostrzeżeniu&#124;wszystkie >}|Określa poziom śledzenia.|  
|-tracePII: \<enable&#124;Disable >|Włącza lub wyłącza śledzenie informacji umożliwiających identyfikację użytkownika.|  
|-traceProp: \<enable&#124;Disable >|Włącza lub wyłącza śledzenie zdarzeń propagacji.|  
|-Uruchom ponownie|Uruchamia ponownie usługę MSDTC, aby natychmiast aktywować zmiany. Jeśli ta wartość nie zostanie określona, zmiany zaczną obowiązywać po ponownym uruchomieniu usługi MSDTC.|  
|-Pokaż|Wyświetla bieżące ustawienia protokołu WS-AtomicTransaction.|  
|-virtualServer: \<virtualServer >|Określa nazwę klastra zasobów usługi DTC.|  
  
## <a name="see-also"></a>Zobacz także

- [Używanie elementu WS-AtomicTransaction](./feature-details/using-ws-atomictransaction.md)
- [Konfigurowanie obsługi protokołu WS-Atomic Transaction](./feature-details/configuring-ws-atomic-transaction-support.md)
