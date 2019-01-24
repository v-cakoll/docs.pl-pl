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
ms.openlocfilehash: 30b61a662170b87a557a1a2ea094301ba6401742
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54608687"
---
# <a name="proxy-configuration"></a>Konfiguracja serwera proxy
Serwer proxy obsługuje żądania klienta dla zasobów. Serwer proxy można zwrócić żądany zasób z pamięci podręcznej lub przekazywać żądania do serwera, na którym znajduje się zasób. Serwery proxy może poprawić wydajność sieci dzięki zmniejszeniu liczby żądań wysyłanych do serwerów zdalnych. Serwery proxy można również ograniczyć dostęp do zasobów.  
  
## <a name="adaptive-proxies"></a>Funkcje adaptacyjnego sterowania serwerów proxy  
 W .NET Framework, serwery proxy dostępne w dwóch odmianach: adaptacyjne i statycznych. Serwery proxy adaptacyjne dostosować ich ustawienia, po zmianie konfiguracji sieci. Na przykład, jeśli użytkownik komputera przenośnego uruchamia sieci połączenia telefonicznego, adaptacyjnej serwera proxy będzie rozpoznać tę zmianę, odnajdywanie Uruchom skrypt konfiguracji, na nowych i dostosować jego ustawienia odpowiednio.  
  
 Adaptacyjne serwery proxy są skonfigurowane przy użyciu skryptu konfiguracji (zobacz [automatyczne wykrywanie serwera Proxy](../../../docs/framework/network-programming/automatic-proxy-detection.md)). Skrypt generuje zestaw protokołów aplikacji i serwera proxy dla każdego protokołu.  
  
 Zmiany w środowisku sieciowym może wymagać używane w systemie nowy zestaw serwerów proxy. Jeśli połączenie sieciowe ulegnie awarii lub nowego połączenia sieciowego jest inicjowany, system musi odnajdywać właściwe źródło skryptu konfiguracji w nowym środowisku i uruchomić nowy skrypt.  
  
 Możesz użyć `usesystemdefault` atrybutu [ `<proxy>` ](../configure-apps/file-schema/network/proxy-element-network-settings.md) elementu w pliku konfiguracji. `usesystemdefault` Atrybutu formanty, czy ustawienia serwera proxy statyczne (adres serwera proxy, listy obejścia i obejście w lokalnych) są odczytywane z ustawień serwera proxy programu Internet Explorer dla użytkownika. Jeśli ta wartość jest równa `true`, zostaną użyte ustawienia proxy statyczne z programu Internet Explorer. Jeśli ta wartość jest `false` lub nie został ustawiony, ustawienia serwera proxy statyczne można określić w konfiguracji i spowoduje przesłonięcie ustawień serwera proxy programu Internet Explorer. Ta wartość musi również być równa `false` lub nie jest ustawiona dla adaptacyjne proxy do włączenia.  
  
 Poniższy przykład przedstawia konfigurację typowe funkcje adaptacyjnego sterowania serwera proxy.  
  
```xml  
<system.net>  
    <defaultProxy>  
      <proxy usesystemdefault="false" />
    </defaultProxy>  
</system.net>  
```  
  
## <a name="static-proxies"></a>Serwery proxy statyczne  
 Statycznego serwerów proxy są zwykle skonfigurowane jawnie przez aplikację, lub gdy plik konfiguracji jest wywoływany przez aplikację lub system. Statyczne serwery proxy są przydatne w sieciach, w których topologii zmieniają się rzadko, takich jak komputery pulpitu podłączone do sieci firmowej.  
  
 Kilka opcji kontroli, jak działa serwer proxy statyczne. Należy określić następujące informacje:  
  
-   Adres serwera proxy.  
  
-   Czy można pominąć serwer proxy, dla adresów lokalnych.  
  
-   Czy można pominąć serwer proxy, zbiór adresów.  
  
 W poniższej tabeli przedstawiono opcje konfiguracji statycznej serwera proxy.  
  
|Ustawienie pliku atrybutu, właściwość lub konfiguracji|Opis|  
|--------------------------------------------------------|-----------------|  
|`proxyaddress` lub <xref:System.Net.WebProxy.Address>|Adres serwera proxy do użycia.|  
|`bypassonlocal` lub <xref:System.Net.WebProxy.BypassProxyOnLocal>|Określa, czy serwer proxy jest pomijane dla adresów lokalnych.|  
|`bypasslist` lub <xref:System.Net.WebProxy.BypassArrayList>|W tym artykule opisano, za pomocą wyrażeń regularnych zestawu adresów, które pomijają serwer proxy.|  
|`usesystemdefault`|Określa, czy ustawienia proxy statyczne (adres serwera proxy, listę obejść i obejście na lokalny) są odczytywane z ustawień serwera proxy programu Internet Explorer dla użytkownika. Jeśli ta wartość jest równa `true`, a następnie zostaną użyte ustawienia proxy statyczne z programu Internet Explorer. .NET Framework 2.0, gdy ta wartość jest równa `true`, ustawienia serwera proxy programu Internet Explorer nie są zastępowane przez inne ustawienia serwera proxy w pliku konfiguracji. W programie .NET Framework 1.1 ustawienia serwera proxy programu Internet Explorer mogą zostać zastąpione przez inne ustawienia serwera proxy w pliku konfiguracji.<br /><br /> Jeśli ta wartość jest `false` lub nie został ustawiony, następnie statyczne ustawienia serwera proxy może być określony w konfiguracji i spowoduje przesłonięcie ustawień serwera proxy programu Internet Explorer. Ta wartość musi również być równa `false` lub nie jest ustawiona dla adaptacyjne proxy do włączenia.|  
  
 Poniższy przykład pokazuje konfiguracji typowych statyczny serwera proxy.  
  
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
- [Automatyczne wykrywanie serwera proxy](../../../docs/framework/network-programming/automatic-proxy-detection.md)
