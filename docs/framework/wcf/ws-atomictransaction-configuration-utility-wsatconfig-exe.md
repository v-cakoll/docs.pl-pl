---
title: Narzędzie do konfiguracji elementu WS-AtomicTransaction (wsatConfig.exe)
ms.date: 03/30/2017
ms.assetid: 1c56cf98-3963-46d5-a4e1-482deae58c58
ms.openlocfilehash: 31b2b3cf16857bf08a4f8d09f47f80d9b34a53b8
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43871994"
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
  
 Foundation\wsatConfig.exe komunikacji %systemroot%\Microsoft.Net\Framework\v3.0\Windows  
  
 Jeśli używasz [!INCLUDE[wxp](../../../includes/wxp-md.md)] lub [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], musisz pobrać aktualizację przed uruchomieniem WsatConfig.exe. Aby uzyskać więcej informacji na temat tej aktualizacji, zobacz [aktualizacji Commerce Server 2007 (KB912817)](https://go.microsoft.com/fwlink/?LinkId=95340) i [dostępności z Windows XP modelu COM + poprawki pakietu zbiorczego pakietu 13](https://go.microsoft.com/fwlink/?LinkId=95341).  
  
 W poniższej tabeli przedstawiono opcje, które mogą być używane z narzędzia konfiguracji WS-AtomicTransaction (wsatConfig.exe).  
  
> [!NOTE]
>  Po ustawieniu certyfikatu SSL dla wybranego portu jest zastąpienie oryginalnego certyfikatu SSL skojarzonych z tego portu, jeśli taka istnieje.  
  
|Opcje|Opis|  
|-------------|-----------------|  
|-kont:\<konto >|Określa rozdzielaną przecinkami listę kont, które mogą uczestniczyć w WS-AtomicTransaction. Ważność tych kont nie jest zaznaczone.|  
|-accountsCerts:\<thumb >&#124;"Issuer\SubjectName" >|Określa rozdzielaną przecinkami listę certyfikatów, które mogą uczestniczyć w WS-AtomicTransaction. Certyfikaty są wskazywane przez odcisk palca lub parę Issuer\SubjectName. Użyj {EMPTY} dla nazwy podmiotu, jeśli jest on pusty.|  
|-endpointCert: < maszyny&#124;\<thumb >&#124;"Issuer\SubjectName" >|Używa certyfikatu komputera lub inny certyfikat lokalny punkt końcowy określonego przez odcisk palca lub parę Issuer\SubjectName. Używa {EMPTY} dla nazwy podmiotu, jeśli jest on pusty.|  
|-maxTimeout:\<s >|Określa maksymalny limit czasu w sekundach. Prawidłowe wartości to od 0 do 3600.|  
|-sieci:\<Włącz&#124;wyłączyć >|Włącza lub wyłącza obsługę sieci WS-AtomicTransaction.|  
|-port:\<portNum >|Nastavuje HTTPS port dla WS-AtomicTransaction.<br /><br /> Jeśli została już włączona zapora, przed uruchomieniem tego narzędzia, numer portu jest automatycznie rejestrowane na liście wyjątków. Jeśli Zapora jest wyłączona, przed uruchomieniem tego narzędzia, żadne dodatkowe zostaną skonfigurowane dotyczące zapory.<br /><br /> Po skonfigurowaniu WS-AT zostanie włączona zapora, należy ponownie uruchomić to narzędzie i podaj numer portu, przy użyciu tego parametru. Jeśli wyłączysz zapory po skonfigurowaniu WS-AT w dalszym ciągu działać bez dodatkowych danych wejściowych.|  
|-timeout:\<s >|Określa domyślny limit czasu w sekundach. Prawidłowe wartości to od 1 do 3600.|  
|-traceActivity:\<Włącz&#124;wyłączyć >|Włącza lub wyłącza śledzenie zdarzeń działania.|  
|-traceLevel:\<poza&#124;błąd&#124;krytyczne&#124;ostrzeżenie&#124;informacji&#124; pełne&#124;wszystkich >}|Określa poziom śledzenia.|  
|-tracePII:\<Włącz&#124;wyłączyć >|Włącza lub wyłącza śledzenie identyfikowalne dane osobowe.|  
|-traceProp:\<Włącz&#124;wyłączyć >|Włącza lub wyłącza śledzenie zdarzeń propagacji.|  
|-Uruchom ponownie|Ponownie uruchamia MSDTC, aby wykonać natychmiastową aktywację zmiany. Jeśli nie zostanie określony, zmiany wprowadzone po ponownym uruchomieniu usługi MSDTC.|  
|— pokazać|Wyświetla bieżące ustawienia protokołu WS-AtomicTransaction.|  
|-SerwerWirtualny:\<SerwerWirtualny >|Określa nazwę klastra usługi DTC zasobów.|  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie elementu WS-AtomicTransaction](../../../docs/framework/wcf/feature-details/using-ws-atomictransaction.md)  
 [Konfigurowanie obsługi protokołu WS-Atomic Transaction](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md)
