---
title: Narzędzie do konfiguracji elementu WS-AtomicTransaction (wsatConfig.exe)
ms.date: 03/30/2017
ms.assetid: 1c56cf98-3963-46d5-a4e1-482deae58c58
ms.openlocfilehash: ef2f34a6700d72c01977ea449041669a88c35e6f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33506270"
---
# <a name="ws-atomictransaction-configuration-utility-wsatconfigexe"></a>Narzędzie do konfiguracji elementu WS-AtomicTransaction (wsatConfig.exe)
Narzędzia konfiguracji WS-AtomicTransaction służy do konfigurowania podstawowych ustawień obsługi protokołu WS-AtomicTransaction.  
  
## <a name="syntax"></a>Składnia  
  
```  
wsatConfig [Options]  
```  
  
## <a name="remarks"></a>Uwagi  
 To narzędzie wiersza polecenia może służyć do konfigurowania podstawowych ustawień protokołu WS-AT w tylko komputer lokalny. Jeśli należy skonfigurować ustawienia na komputerach lokalnych i zdalnych, możesz użyć przystawki programu MMC zgodnie z opisem w [Konfigurowanie obsługi protokołu WS-AT transakcji](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md).  
  
 Narzędzia wiersza polecenia znajduje się w lokalizacji instalacji zestawu Windows SDK, w szczególności  
  
 %SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Foundation\wsatConfig.exe komunikacji  
  
 Jeśli używasz [!INCLUDE[wxp](../../../includes/wxp-md.md)] lub [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], należy pobrać aktualizacji przed uruchomieniem WsatConfig.exe. Aby uzyskać więcej informacji na temat tej aktualizacji, zobacz [aktualizacji dla Commerce Server 2007 (KB912817)](http://go.microsoft.com/fwlink/?LinkId=95340) i [dostępności z systemu Windows XP COM + poprawki pakietu zbiorczego pakietu 13](http://go.microsoft.com/fwlink/?LinkId=95341).  
  
 W poniższej tabeli przedstawiono opcje, które mogą być używane z narzędzia konfiguracji WS-AtomicTransaction (wsatConfig.exe).  
  
> [!NOTE]
>  Po ustawieniu certyfikatu SSL dla wybranego portu możesz zastąpić oryginalny certyfikat SSL skojarzony z tego portu, jeśli taka istnieje.  
  
|Opcje|Opis|  
|-------------|-----------------|  
|-kont:\<konta >|Określa rozdzielaną przecinkami listę kont, które mogą uczestniczyć w WS-AtomicTransaction. Ważność tych kont nie jest zaznaczone.|  
|-accountsCerts:\<thumb >&#124;"Issuer\SubjectName" >|Określa rozdzielaną przecinkami listę certyfikatów, które mogą uczestniczyć w WS-AtomicTransaction. Certyfikaty są wskazane przez odcisk palca lub parę Issuer\SubjectName. Użyj wartości {EMPTY} dla nazwy podmiotu, jeśli jest pusty.|  
|-endpointCert: < maszyny&#124;\<thumb >&#124;"Issuer\SubjectName" >|Używa certyfikatu komputera lub innego lokalnego certyfikatu punktu końcowego określonego przez odcisk palca lub parę Issuer\SubjectName. Używa {EMPTY} jako nazwę podmiotu, jeśli jest pusty.|  
|-maxTimeout:\<s >|Określa maksymalny limit czasu w sekundach. Prawidłowe wartości to od 0 do 3600.|  
|— sieć:\<włączyć&#124;wyłączyć >|Włącza lub wyłącza obsługę sieci WS-AtomicTransaction.|  
|— port:\<portNum >|Ustawia HTTPS port dla protokołu WS-AtomicTransaction.<br /><br /> Jeśli została już włączona zapora, przed uruchomieniem tego narzędzia, numer portu jest automatycznie rejestrowane na liście wyjątków. Jeśli Zapora jest wyłączone przed uruchomieniem tego narzędzia, żadne dodatkowe skonfigurowano dotyczące zapory.<br /><br /> Po skonfigurowaniu usługi WS-AT zostanie włączona zapora, należy ponownie uruchomić to narzędzie i podaj numer portu, za pomocą tego parametru. Wyłączenie zapory po skonfigurowaniu, WS-AT w dalszym ciągu działać bez dodatkowych danych wejściowych.|  
|-timeout:\<s >|Określa domyślny limit czasu w sekundach. Prawidłowe są wartości z zakresu od 1 do 3600.|  
|-traceActivity:\<włączyć&#124;wyłączyć >|Włącza lub wyłącza śledzenie zdarzeń aktywności.|  
|-traceLevel:\<poza&#124;błąd&#124;krytyczne&#124;ostrzeżenie&#124;informacji&#124; pełne&#124;wszystkie >}|Określa poziom śledzenia.|  
|-tracePII:\<włączyć&#124;wyłączyć >|Włącza lub wyłącza śledzenie informacji umożliwiających identyfikację użytkownika.|  
|-traceProp:\<włączyć&#124;wyłączyć >|Włącza lub wyłącza śledzenie zdarzeń propagacji.|  
|— ponowne uruchomienie|Ponownie uruchamia usługę MSDTC w celu aktywowania zmian natychmiast. Jeśli nie zostanie określony, zmiany zaczynają obowiązywać po ponownym uruchomieniu usługi MSDTC.|  
|— Pokaż|Wyświetla bieżące ustawienia protokołu WS-AtomicTransaction.|  
|-SerwerWirtualny:\<SerwerWirtualny >|Określa nazwę klastra zasobu DTC.|  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie elementu WS-AtomicTransaction](../../../docs/framework/wcf/feature-details/using-ws-atomictransaction.md)  
 [Konfigurowanie obsługi protokołu WS-Atomic Transaction](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md)
