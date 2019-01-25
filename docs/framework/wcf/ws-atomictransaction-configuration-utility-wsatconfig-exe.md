---
title: Narzędzie do konfiguracji elementu WS-AtomicTransaction (wsatConfig.exe)
ms.date: 03/30/2017
ms.assetid: 1c56cf98-3963-46d5-a4e1-482deae58c58
ms.openlocfilehash: b4c2bb2d9c81b6ab3afc783d1188de7664e01566
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54741421"
---
# <a name="ws-atomictransaction-configuration-utility-wsatconfigexe"></a>Narzędzie do konfiguracji elementu WS-AtomicTransaction (wsatConfig.exe)
Narzędzie konfiguracji WS-AtomicTransaction służy do konfigurowania podstawowych ustawień pomocy technicznej WS-AtomicTransaction.  
  
## <a name="syntax"></a>Składnia  
  
```  
wsatConfig [Options]  
```  
  
## <a name="remarks"></a>Uwagi  
 To narzędzie wiersza polecenia mogą służyć do skonfigurowania podstawowych ustawień WS-AT tylko na lokalnej maszynie. Jeśli musisz skonfigurować ustawienia na komputerach lokalnych i zdalnych, powinien używasz przystawki programu MMC zgodnie z opisem w [Konfigurowanie obsługi protokołu WS-Atomic Transaction](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md).  
  
 Narzędzie wiersza polecenia można znaleźć w lokalizacji instalacji zestawu Windows SDK, w szczególności  
  
 %SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\wsatConfig.exe  
  
 Jeśli używasz [!INCLUDE[wxp](../../../includes/wxp-md.md)] lub [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], musisz pobrać aktualizację przed uruchomieniem WsatConfig.exe. Aby uzyskać więcej informacji na temat tej aktualizacji, zobacz [aktualizacji Commerce Server 2007 (KB912817)](https://go.microsoft.com/fwlink/?LinkId=95340) i [dostępności z Windows XP modelu COM + poprawki pakietu zbiorczego pakietu 13](https://go.microsoft.com/fwlink/?LinkId=95341).  
  
 W poniższej tabeli przedstawiono opcje, które mogą być używane z narzędzia konfiguracji WS-AtomicTransaction (wsatConfig.exe).  
  
> [!NOTE]
>  Po ustawieniu certyfikatu SSL dla wybranego portu jest zastąpienie oryginalnego certyfikatu SSL skojarzonych z tego portu, jeśli taka istnieje.  
  
|Opcje|Opis|  
|-------------|-----------------|  
|-kont:\<konto >|Określa rozdzielaną przecinkami listę kont, które mogą uczestniczyć w WS-AtomicTransaction. Ważność tych kont nie jest zaznaczone.|  
|-accountsCerts:\<thumb>&#124;"Issuer\SubjectName",>|Określa rozdzielaną przecinkami listę certyfikatów, które mogą uczestniczyć w WS-AtomicTransaction. Certyfikaty są wskazywane przez odcisk palca lub parę Issuer\SubjectName. Użyj {EMPTY} dla nazwy podmiotu, jeśli jest on pusty.|  
|-endpointCert:<machine&#124;\<thumb>&#124;"Issuer\SubjectName">|Używa certyfikatu komputera lub inny certyfikat lokalny punkt końcowy określonego przez odcisk palca lub parę Issuer\SubjectName. Używa {EMPTY} dla nazwy podmiotu, jeśli jest on pusty.|  
|-maxTimeout:\<sec>|Określa maksymalny limit czasu w sekundach. Prawidłowe wartości to od 0 do 3600.|  
|-network:\<enable&#124;disable>|Włącza lub wyłącza obsługę sieci WS-AtomicTransaction.|  
|-port:\<portNum >|Nastavuje HTTPS port dla WS-AtomicTransaction.<br /><br /> Jeśli została już włączona zapora, przed uruchomieniem tego narzędzia, numer portu jest automatycznie rejestrowane na liście wyjątków. Jeśli Zapora jest wyłączona, przed uruchomieniem tego narzędzia, żadne dodatkowe zostaną skonfigurowane dotyczące zapory.<br /><br /> Po skonfigurowaniu WS-AT zostanie włączona zapora, należy ponownie uruchomić to narzędzie i podaj numer portu, przy użyciu tego parametru. Jeśli wyłączysz zapory po skonfigurowaniu WS-AT w dalszym ciągu działać bez dodatkowych danych wejściowych.|  
|-timeout:\<s >|Określa domyślny limit czasu w sekundach. Prawidłowe wartości to od 1 do 3600.|  
|-traceActivity:\<enable&#124;disable>|Włącza lub wyłącza śledzenie zdarzeń działania.|  
|-traceLevel:\<Off&#124;Error&#124;Critical&#124;Warning&#124;Information&#124; Verbose&#124;All>}|Określa poziom śledzenia.|  
|-tracePII:\<enable&#124;disable>|Włącza lub wyłącza śledzenie identyfikowalne dane osobowe.|  
|-traceProp:\<enable&#124;disable>|Włącza lub wyłącza śledzenie zdarzeń propagacji.|  
|-restart|Ponownie uruchamia MSDTC, aby wykonać natychmiastową aktywację zmiany. Jeśli nie zostanie określony, zmiany wprowadzone po ponownym uruchomieniu usługi MSDTC.|  
|-show|Wyświetla bieżące ustawienia protokołu WS-AtomicTransaction.|  
|-SerwerWirtualny:\<SerwerWirtualny >|Określa nazwę klastra usługi DTC zasobów.|  
  
## <a name="see-also"></a>Zobacz także
- [Używanie elementu WS-AtomicTransaction](../../../docs/framework/wcf/feature-details/using-ws-atomictransaction.md)
- [Konfigurowanie obsługi protokołu WS-Atomic Transaction](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md)
