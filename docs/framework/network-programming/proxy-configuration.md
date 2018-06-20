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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 6cf25d3d7dcde963f06729794716b75dffdb64ae
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2018
ms.locfileid: "36207368"
---
# <a name="proxy-configuration"></a>Konfiguracja serwera proxy
Serwer proxy obsługuje żądania klientów dotyczące zasobów. Serwer proxy można zwrócić żądanych zasobów z pamięci podręcznej lub przesyła żądanie do serwera, na którym znajduje się zasób. Serwery proxy może zwiększyć wydajność sieci dzięki zmniejszeniu liczby żądań wysyłanych do serwerów zdalnych. Serwery proxy można również ograniczyć dostęp do zasobów.  
  
## <a name="adaptive-proxies"></a>Adaptacyjną serwerów proxy  
 W programie .NET Framework, serwery proxy są dostępne w dwóch odmian: adaptacyjną i statyczne. Serwery proxy adaptacyjną ich ustawienia, po zmianie konfiguracji sieci. Na przykład jeśli użytkownik komputera przenośnego uruchamia połączenie telefoniczne, adaptacyjną serwera proxy będzie rozpoznawać tej zmiany, odnajdywania i uruchamiania jego nowy skrypt konfiguracji i dostosować jego ustawienia odpowiednio.  
  
 Adaptacyjną serwery proxy są skonfigurowane za pomocą skryptu konfiguracji (zobacz [automatycznego wykrywania Proxy](../../../docs/framework/network-programming/automatic-proxy-detection.md)). Skrypt generuje zestaw protokołów aplikacji i serwer proxy dla każdego protokołu.  
  
 Zmiany w środowisku sieciowym może wymagać używane nowy zestaw serwerów proxy w systemie. Jeśli połączenie sieciowe ulegnie awarii lub nowego połączenia sieciowego jest zainicjowany, system musi odnaleźć Źródło odpowiedni skrypt konfiguracji w nowym środowisku i uruchom nowy skrypt.  
  
 Można użyć `usesystemdefault` atrybutu [ `<proxy>` ](../configure-apps/file-schema/network/proxy-element-network-settings.md) elementu w pliku konfiguracji. `usesystemdefault` Atrybut kontrolki, czy ustawienia serwera proxy statyczne (adres serwera proxy, listy obejścia i obejście na lokalnym) są odczytywane z ustawień serwera proxy programu Internet Explorer dla użytkownika. Jeśli ta wartość jest równa `true`, zostaną użyte ustawienia statycznych serwera proxy w programie Internet Explorer. Jeśli ta wartość jest `false` lub nie jest ustawiona, ustawienia serwera proxy statycznych może być określony w konfiguracji i zastąpią ustawienia serwera proxy programu Internet Explorer. Ta wartość musi również mieć ustawioną `false` lub nie ustawiono dla adaptacyjną proxy włączenia.  
  
 Poniższy przykład przedstawia konfiguracji typowych adaptacyjną serwera proxy.  
  
```xml  
<system.net>  
    <defaultProxy>  
      <proxy usesystemdefault="false" />
    </defaultProxy>  
</system.net>  
```  
  
## <a name="static-proxies"></a>Statyczne serwerów proxy  
 Statyczne serwery proxy są zazwyczaj konfigurowane jawnie przez aplikację, lub gdy plik konfiguracji jest wywoływany przez aplikację lub systemu. Statyczne serwery proxy są przydatne w sieciach, w których topologii zmienia się rzadko, takich jak komputer stacjonarny podłączone do sieci firmowej.  
  
 Kilka opcji kontrolować sposób działania statycznych serwera proxy. Można określić następujące czynności:  
  
-   Adres serwera proxy.  
  
-   Czy należy pominąć serwer proxy dla adresów lokalnych.  
  
-   Określa, czy można pominąć serwer proxy, zbiór adresów.  
  
 W poniższej tabeli przedstawiono opcje konfiguracji statycznej serwera proxy.  
  
|Ustawienie pliku atrybutu, właściwość lub konfiguracji|Opis|  
|--------------------------------------------------------|-----------------|  
|`proxyaddress` lub <xref:System.Net.WebProxy.Address>|Adres serwera proxy do użycia.|  
|`bypassonlocal` lub <xref:System.Net.WebProxy.BypassProxyOnLocal>|Określa, czy serwer proxy jest pomijana dla adresów lokalnych.|  
|`bypasslist` lub <xref:System.Net.WebProxy.BypassArrayList>|Opisuje za pomocą wyrażeń regularnych, zestaw adresów, które pominąć serwer proxy.|  
|`usesystemdefault`|Określa, czy ustawienia serwera proxy statyczne (adres serwera proxy, listy obejścia i obejście na lokalnym) są odczytywane z ustawień serwera proxy programu Internet Explorer dla użytkownika. Jeśli ta wartość jest równa `true`, zostaną użyte ustawienia statycznych serwera proxy w programie Internet Explorer. .NET Framework 2.0, gdy ta wartość jest równa `true`, ustawienia serwera proxy programu Internet Explorer nie zostały zastąpione przez inne ustawienia serwera proxy w pliku konfiguracji. W programie .NET Framework 1.1 ustawienia serwera proxy programu Internet Explorer, może zostać przesłonięta przez inne ustawienia serwera proxy w pliku konfiguracji.<br /><br /> Jeśli ta wartość jest `false` lub nie został ustawiony, następnie statyczne ustawienia serwera proxy może być określony w konfiguracji i zastąpią ustawienia serwera proxy programu Internet Explorer. Ta wartość musi również mieć ustawioną `false` lub nie ustawiono dla adaptacyjną proxy włączenia.|  
  
 Poniższy przykład przedstawia konfiguracji typowych statycznych serwera proxy.  
  
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
 <xref:System.Net.WebProxy>  
 <xref:System.Net.GlobalProxySelection>  
 [Automatyczne wykrywanie serwera proxy](../../../docs/framework/network-programming/automatic-proxy-detection.md)
