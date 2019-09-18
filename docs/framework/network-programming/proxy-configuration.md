---
title: Konfiguracja serwera proxy
ms.date: 06/18/2018
helpviewer_keywords:
- Networking
- adaptive proxies
- static proxies
- Network Resources
- Internet, proxy configuration
- proxies
- network, proxy configuration
- proxies, configuring
ms.assetid: 353c0a8b-4cee-44f6-8e65-60e286743df9
ms.openlocfilehash: 1fbfe25b90e810ff96924a2341582ff3f5ee5e5d
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047356"
---
# <a name="proxy-configuration"></a>Konfiguracja serwera proxy
Serwer proxy obsługuje żądania klientów dotyczące zasobów. Serwer proxy może zwrócić żądany zasób z jego pamięci podręcznej lub przesłać żądanie do serwera, na którym znajduje się zasób. Serwery proxy mogą zwiększyć wydajność sieci, zmniejszając liczbę żądań wysyłanych do serwerów zdalnych. Serwery proxy mogą być również używane do ograniczania dostępu do zasobów.  
  
## <a name="adaptive-proxies"></a>Adaptacyjne serwery proxy  
 W .NET Framework serwery proxy są dostępne w dwóch odmianach: adaptacyjne i statyczne. Adaptacyjne serwery proxy dostosowują swoje ustawienia w przypadku zmiany konfiguracji sieci. Na przykład, jeśli użytkownik laptop uruchamia połączenie sieciowe telefoniczne, adaptacyjny serwer proxy rozpozna tę zmianę, odnajduje i uruchamia nowy skrypt konfiguracji i odpowiednio dostosowuje jego ustawienia.  
  
 Adaptacyjne serwery proxy są konfigurowane przez skrypt konfiguracji (zobacz [Automatyczne wykrywanie serwera proxy](automatic-proxy-detection.md)). Skrypt generuje zestaw protokołów aplikacji i serwer proxy dla każdego protokołu.  
  
 Zmiany w środowisku sieciowym mogą wymagać, aby system używał nowego zestawu serwerów proxy. Jeśli połączenie sieciowe ulegnie awarii lub zostanie zainicjowane nowe połączenie sieciowe, system musi wykryć odpowiednie źródło skryptu konfiguracji w nowym środowisku i uruchomić nowy skrypt.  
  
 Możesz użyć `usesystemdefault` atrybutu [`<proxy>`](../configure-apps/file-schema/network/proxy-element-network-settings.md) elementu w pliku konfiguracji. Ten `usesystemdefault` atrybut określa, czy ustawienia statycznego serwera proxy (adres serwera proxy, Lista pomijania i obejście dla lokalnego) powinny zostać odczytane z ustawień serwera proxy programu Internet Explorer dla użytkownika. Jeśli ta wartość jest ustawiona na `true`, zostaną użyte ustawienia statycznego serwera proxy z programu Internet Explorer. Jeśli ta wartość jest `false` lub nie jest ustawiona, statyczne ustawienia serwera proxy mogą być określone w konfiguracji i zastąpią ustawienia serwera proxy programu Internet Explorer. Ta wartość musi być również ustawiona na `false` lub nie ustawiona dla adaptacyjnych serwerów proxy, aby można ją było włączyć.  
  
 Poniższy przykład przedstawia typową adaptacyjną konfigurację serwera proxy.  
  
```xml  
<system.net>  
    <defaultProxy>  
      <proxy usesystemdefault="false" />
    </defaultProxy>  
</system.net>  
```  
  
## <a name="static-proxies"></a>Statyczne serwery proxy  
 Statyczne serwery proxy są zwykle konfigurowane jawnie przez aplikację lub gdy plik konfiguracji jest wywoływany przez aplikację lub system. Statyczne serwery proxy są przydatne w sieciach, w których topologia zmienia się rzadko, na przykład na komputerze stacjonarnym podłączonym do sieci firmowej.  
  
 Niektóre opcje kontrolują sposób działania statycznego serwera proxy. Można określić następujące elementy:  
  
- Adres serwera proxy.  
  
- Czy serwer proxy powinien być pomijany dla adresów lokalnych.  
  
- Czy serwer proxy powinien być pomijany dla zbioru adresów.  
  
 W poniższej tabeli przedstawiono opcje konfiguracji dla statycznego serwera proxy.  
  
|Ustawienie atrybutu, właściwości lub pliku konfiguracji|Opis|  
|--------------------------------------------------------|-----------------|  
|`proxyaddress` lub <xref:System.Net.WebProxy.Address>|Adres serwera proxy, który ma być używany.|  
|`bypassonlocal` lub <xref:System.Net.WebProxy.BypassProxyOnLocal>|Określa, czy serwer proxy jest pomijany dla adresów lokalnych.|  
|`bypasslist` lub <xref:System.Net.WebProxy.BypassArrayList>|Opisuje, w wyrażeniach regularnych, zestaw adresów, które pomijają serwer proxy.|  
|`usesystemdefault`|Określa, czy ustawienia statycznego serwera proxy (adres serwera proxy, Lista pomijania i obejście dla lokalnego) powinny zostać odczytane z ustawień serwera proxy programu Internet Explorer dla użytkownika. Jeśli ta wartość jest ustawiona na `true`, zostaną użyte ustawienia statycznego serwera proxy z programu Internet Explorer. W .NET Framework 2,0, gdy ta wartość jest ustawiona `true`na, ustawienia serwera proxy programu Internet Explorer nie są zastępowane przez inne ustawienia serwera proxy w pliku konfiguracji. W .NET Framework 1,1 ustawienia serwera proxy programu Internet Explorer mogą być przesłonięte przez inne ustawienia serwera proxy w pliku konfiguracji.<br /><br /> Jeśli ta wartość jest `false` lub nie jest ustawiona, statyczne ustawienia serwera proxy mogą być określone w konfiguracji i zastąpią ustawienia serwera proxy programu Internet Explorer. Ta wartość musi być również ustawiona na `false` lub nie ustawiona dla adaptacyjnych serwerów proxy, aby można ją było włączyć.|  
  
 Poniższy przykład przedstawia typową konfigurację statycznego serwera proxy.  
  
```xml  
<system.net>  
    <defaultProxy>  
        <proxy  proxyaddress="http://proxy.contoso.com:3128"  
                bypassonlocal="true"  
        />  
        <bypasslist>  
            <add address="[a-z]+.blueyonderairlines.com$" />  
        </bypasslist>  
    </defaultProxy>  
</system.net>  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Net.WebProxy>
- <xref:System.Net.GlobalProxySelection>
- [Automatyczne wykrywanie serwera proxy](automatic-proxy-detection.md)
