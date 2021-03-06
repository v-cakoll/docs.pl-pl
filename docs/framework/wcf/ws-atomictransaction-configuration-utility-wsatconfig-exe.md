---
title: Narzędzie do konfiguracji elementu WS-AtomicTransaction (wsatConfig.exe)
ms.date: 03/30/2017
ms.assetid: 1c56cf98-3963-46d5-a4e1-482deae58c58
ms.openlocfilehash: 009be8d4c25fd9db5b2f2df6e75fb046e92f389a
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094725"
---
# <a name="ws-atomictransaction-configuration-utility-wsatconfigexe"></a>Narzędzie do konfiguracji elementu WS-AtomicTransaction (wsatConfig.exe)

Narzędzie konfiguracji protokołu WS-AtomicTransaction służy do konfigurowania podstawowych ustawień obsługi WS-AtomicTransaction.  
  
## <a name="syntax"></a>Składnia  
  
```console  
wsatConfig [Options]  
```  
  
## <a name="remarks"></a>Uwagi  
 Za pomocą tego narzędzia wiersza polecenia można skonfigurować podstawowe ustawienia usługi WS-AT tylko na komputerze lokalnym. Jeśli konieczne jest skonfigurowanie ustawień na maszynach lokalnych i zdalnych, należy użyć przystawki programu MMC zgodnie z opisem w temacie [Konfigurowanie obsługi transakcji WS-AT](./feature-details/configuring-ws-atomic-transaction-support.md).  
  
 Narzędzie wiersza polecenia można znaleźć w lokalizacji instalacji Windows SDK, w tym,  
  
 %SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\wsatConfig.exe  
  
 W przypadku korzystania z systemu Windows XP lub Windows Server 2003, należy pobrać aktualizację przed uruchomieniem programu WsatConfig. exe. Aby uzyskać więcej informacji o tej aktualizacji, zobacz [Aktualizacja dla Windows Communication Foundation (KB912817)](https://www.microsoft.com/download/details.aspx?id=21520).  
  
 W poniższej tabeli przedstawiono opcje, które mogą być używane z narzędziem konfiguracji protokołu WS-AtomicTransaction (wsatConfig. exe).  
  
> [!NOTE]
> Po ustawieniu certyfikatu protokołu SSL dla wybranego portu zastępowany jest oryginalny certyfikat SSL skojarzony z tym portem, jeśli taki istnieje.  
  
|Opcje|Opis|  
|-------------|-----------------|  
|-konta:\<konta, >|Określa rozdzieloną przecinkami listę kont, które mogą uczestniczyć w usłudze WS-AtomicTransaction. Ważność tych kont nie jest sprawdzana.|  
|-accountsCerts:\<kciuk >&#124;"Issuer\SubjectName", >|Określa rozdzieloną przecinkami listę certyfikatów, które mogą uczestniczyć w usłudze WS-AtomicTransaction. Certyfikaty są wskazywane przez odcisk palca lub parę Issuer\SubjectName. Użyj {EMPTY} dla nazwy podmiotu, jeśli jest pusta.|  
|-endpointCert: <&#124;\<>&#124;"Issuer\SubjectName" >|Używa certyfikatu komputera lub innego lokalnego certyfikatu punktu końcowego określonego za pomocą odcisku palca lub pary Issuer\SubjectName. Używa elementu {EMPTY} dla nazwy podmiotu, jeśli jest pusta.|  
|-maxTimeout:\<sek >|Określa maksymalny limit czasu w sekundach. Prawidłowe wartości to od 0 do 3600.|  
|-Sieć:\<Włącz&#124;opcję Wyłącz >|Włącza lub wyłącza obsługę sieci WS-AtomicTransaction.|  
|-Port:\<portNum >|Ustawia port HTTPS dla protokołu WS-AtomicTransaction.<br /><br /> Jeśli Zapora została już włączona przed uruchomieniem tego narzędzia, port zostanie automatycznie zarejestrowany na liście wyjątków. Jeśli Zapora jest wyłączona przed uruchomieniem tego narzędzia, dla zapory nic nie skonfigurowano.<br /><br /> W przypadku włączenia zapory po skonfigurowaniu usługi WS-AT należy ponownie uruchomić to narzędzie i podać numer portu przy użyciu tego parametru. Jeśli po skonfigurowaniu Zapora zostanie wyłączona, Usługa WS-AT będzie nadal działała bez dodatkowych danych wejściowych.|  
|-timeout:\<sek >|Określa domyślny limit czasu (w sekundach). Prawidłowe wartości to od 1 do 3600.|  
|-traced:\<Enable&#124;Disable >|Włącza lub wyłącza śledzenie zdarzeń działania.|  
|-traceLevel:\<wyłączyć&#124;&#124;krytyczne&#124;informacje&#124;&#124; ostrzegawcze&#124;wszystkie >}|Określa poziom śledzenia.|  
|-tracePII:\<Włącz&#124;opcję Disable >|Włącza lub wyłącza śledzenie informacji umożliwiających identyfikację użytkownika.|  
|-traceProp:\<Włącz&#124;opcję Disable >|Włącza lub wyłącza śledzenie zdarzeń propagacji.|  
|-Uruchom ponownie|Uruchamia ponownie usługę MSDTC, aby natychmiast aktywować zmiany. Jeśli ta wartość nie zostanie określona, zmiany zaczną obowiązywać po ponownym uruchomieniu usługi MSDTC.|  
|-Pokaż|Wyświetla bieżące ustawienia protokołu WS-AtomicTransaction.|  
|-virtualServer:\<virtualServer >|Określa nazwę klastra zasobów usługi DTC.|  
  
## <a name="see-also"></a>Zobacz też

- [Używanie elementu WS-AtomicTransaction](./feature-details/using-ws-atomictransaction.md)
- [Konfigurowanie obsługi protokołu WS-Atomic Transaction](./feature-details/configuring-ws-atomic-transaction-support.md)
