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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047356"
---
# <a name="proxy-configuration"></a>Konfiguracja serwera proxy
Serwer proxy obsługuje żądania klientów dotyczące zasobów. Serwer proxy może zwrócić żądany zasób z pamięci podręcznej lub przesłać je dalej do serwera, na którym znajduje się zasób. Serwery proxy mogą zwiększyć wydajność sieci, zmniejszając liczbę żądań wysyłanych do serwerów zdalnych. Serwery proxy mogą być również używane do ograniczania dostępu do zasobów.  
  
## <a name="adaptive-proxies"></a>Adaptacyjne serwery proxy  
 W .NET Framework serwery proxy są dostępne w dwóch odmianach: adaptacyjnej i statycznej. Adaptacyjne serwery proxy dostosowują swoje ustawienia po zmianie konfiguracji sieci. Na przykład jeśli użytkownik komputera przenośnego uruchamia połączenie telefoniczne z siecią, adaptacyjny serwer proxy rozpozna tę zmianę, odnajdzie i uruchomi nowy skrypt konfiguracyjny oraz odpowiednio dostosuje jego ustawienia.  
  
 Adaptacyjne serwery proxy są konfigurowane za pomocą skryptu konfiguracyjnego (patrz [Automatyczne wykrywanie serwera proxy).](automatic-proxy-detection.md) Skrypt generuje zestaw protokołów aplikacji i serwer proxy dla każdego protokołu.  
  
 Zmiany w środowisku sieciowym mogą wymagać, aby system używał nowego zestawu serwerów proxy. Jeśli połączenie sieciowe ustępuje lub zostanie zainicjowane nowe połączenie sieciowe, system musi odnajdować odpowiednie źródło skryptu konfiguracyjnego w nowym środowisku i uruchomić nowy skrypt.  
  
 Można użyć `usesystemdefault` atrybutu [`<proxy>`](../configure-apps/file-schema/network/proxy-element-network-settings.md) elementu w pliku konfiguracji. Atrybut `usesystemdefault` określa, czy statyczne ustawienia serwera proxy (adres serwera proxy, lista pomijania i obejście na lokalnym) powinny być odczytywane z ustawień serwera proxy programu Internet Explorer dla użytkownika. Jeśli ta wartość `true`jest ustawiona na , zostaną użyte statyczne ustawienia serwera proxy z programu Internet Explorer. Jeśli ta `false` wartość jest lub nie jest ustawiona, statyczne ustawienia serwera proxy można określić w konfiguracji i zastąpią ustawienia serwera proxy programu Internet Explorer. Wartość ta musi być `false` również ustawiona na lub nie ustawiona dla serwerów proxy adaptacyjnych, które mają być włączone.  
  
 W poniższym przykładzie przedstawiono typową adaptacyjną konfigurację serwera proxy.  
  
```xml  
<system.net>  
    <defaultProxy>  
      <proxy usesystemdefault="false" />
    </defaultProxy>  
</system.net>  
```  
  
## <a name="static-proxies"></a>Statyczne serwery proxy  
 Statyczne serwery proxy są zwykle konfigurowane jawnie przez aplikację lub gdy plik konfiguracyjny jest wywoływany przez aplikację lub system. Statyczne serwery proxy są przydatne w sieciach, w których topologia zmienia się rzadko, na przykład komputer stacjonarny podłączony do sieci firmowej.  
  
 Kilka opcji kontroluje sposób działania statycznego serwera proxy. Można określić następujące elementy:  
  
- Adres serwera proxy.  
  
- Czy serwer proxy powinien zostać pominięty dla adresów lokalnych.  
  
- Czy serwer proxy powinien zostać pominięty dla zestawu adresów.  
  
 W poniższej tabeli przedstawiono opcje konfiguracji statycznego serwera proxy.  
  
|Ustawienie atrybutu, właściwości lub pliku konfiguracyjnego|Opis|  
|--------------------------------------------------------|-----------------|  
|`proxyaddress` lub <xref:System.Net.WebProxy.Address>|Adres serwera proxy do użycia.|  
|`bypassonlocal` lub <xref:System.Net.WebProxy.BypassProxyOnLocal>|Określa, czy serwer proxy jest pomijany dla adresów lokalnych.|  
|`bypasslist` lub <xref:System.Net.WebProxy.BypassArrayList>|W tym artykule opisano, z wyrażeniami regularnymi, zestaw adresów, które pomijają serwer proxy.|  
|`usesystemdefault`|Określa, czy statyczne ustawienia serwera proxy (adres serwera proxy, lista pomijania i pomijanie na lokalnym) powinny być odczytywane z ustawień serwera proxy programu Internet Explorer dla użytkownika. Jeśli ta wartość `true`jest ustawiona na , zostaną użyte statyczne ustawienia serwera proxy z programu Internet Explorer. W programie .NET Framework 2.0, `true`gdy ta wartość jest ustawiona na , ustawienia serwera proxy programu Internet Explorer nie są zastępowane przez inne ustawienia serwera proxy w pliku konfiguracyjnym. W programie .NET Framework 1.1 ustawienia serwera proxy programu Internet Explorer można zastąpić innymi ustawieniami serwera proxy w pliku konfiguracyjnym.<br /><br /> Jeśli ta `false` wartość jest lub nie jest ustawiona, wówczas statyczne ustawienia serwera proxy można określić w konfiguracji i zastąpić ustawienia serwera proxy programu Internet Explorer. Wartość ta musi być `false` również ustawiona na lub nie ustawiona dla serwerów proxy adaptacyjnych, które mają być włączone.|  
  
 W poniższym przykładzie przedstawiono typową konfigurację statycznego serwera proxy.  
  
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
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Net.WebProxy>
- <xref:System.Net.GlobalProxySelection>
- [Automatyczne wykrywanie serwera proxy](automatic-proxy-detection.md)
