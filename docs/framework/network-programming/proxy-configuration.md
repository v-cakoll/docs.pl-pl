---
title: Konfiguracja serwera proxy
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: b543097d0fc85c502bd36f22225958f9239ccd71
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="proxy-configuration"></a>Konfiguracja serwera proxy
Serwer proxy obsługuje żądania klientów dotyczące zasobów. Serwer proxy można zwrócić żądanych zasobów z pamięci podręcznej lub przesyła żądanie do serwera, na którym znajduje się zasób. Serwery proxy może zwiększyć wydajność sieci dzięki zmniejszeniu liczby żądań wysyłanych do serwerów zdalnych. Serwery proxy można również ograniczyć dostęp do zasobów.  
  
## <a name="adaptive-proxies"></a>Adaptacyjną serwerów proxy  
 W programie .NET Framework, serwery proxy są dostępne w dwóch odmian: adaptacyjną i statyczne. Serwery proxy adaptacyjną ich ustawienia, po zmianie konfiguracji sieci. Na przykład jeśli użytkownik komputera przenośnego uruchamia połączenie telefoniczne, adaptacyjną serwera proxy będzie rozpoznawać tej zmiany, odnajdywania i uruchamiania jego nowy skrypt konfiguracji i dostosować jego ustawienia odpowiednio.  
  
 Adaptacyjną serwery proxy są skonfigurowane za pomocą skryptu konfiguracji (zobacz [automatycznego wykrywania Proxy](../../../docs/framework/network-programming/automatic-proxy-detection.md)). Skrypt generuje zestaw protokołów aplikacji i serwer proxy dla każdego protokołu.  
  
 Kilka opcji kontrolować sposób uruchamiania skryptu konfiguracji. Można określić następujące czynności:  
  
-   Jak często skryptu konfiguracji jest pobierane i uruchom.  
  
-   Jak długo czekać na pobieranie skryptu.  
  
-   Które poświadczeń systemu należy używać dostępu do serwera proxy.  
  
-   Które poświadczeń systemu powinna być używana do pobrania skryptu konfiguracji.  
  
 Zmiany w środowisku sieciowym może wymagać używane nowy zestaw serwerów proxy w systemie. Jeśli połączenie sieciowe ulegnie awarii lub nowego połączenia sieciowego jest zainicjowany, system musi odnaleźć Źródło odpowiedni skrypt konfiguracji w nowym środowisku i uruchom nowy skrypt.  
  
 W poniższej tabeli przedstawiono opcje konfiguracji dla serwera proxy adaptacyjną.  
  
|Ustawienie pliku atrybutu, właściwość lub konfiguracji|Opis|  
|--------------------------------------------------------|-----------------|  
|`scriptDownloadInterval`|Czas w sekundach między pobraniami skryptu.|  
|`scriptDownloadTimeout`|Czas oczekiwania (w sekundach) dla skryptu do pobrania.|  
|`useDefaultCredentials`lub<xref:System.Net.WebProxy.UseDefaultCredentials>|Określa, czy system używa sieci domyślne poświadczenia dostępu do serwera proxy.|  
|`useDefaultCredentialForScriptDownload`|Określa, czy system używa poświadczeń domyślnych w sieci można pobrać skryptu konfiguracji.|  
|`usesystemdefaults`|Określa, czy ustawienia serwera proxy statyczne (adres serwera proxy, listy obejścia i obejście na lokalnym) są odczytywane z ustawień serwera proxy programu Internet Explorer dla użytkownika. Jeśli ta wartość jest równa "true", a następnie ustawienia serwera proxy statyczne z programu Internet Explorer będzie używany.<br /><br /> Jeśli ta wartość wynosi "false" lub nie zestawu, a następnie ustawienia serwera proxy statycznych może być określony w konfiguracji i zastąpią ustawienia serwera proxy programu Internet Explorer. Ta wartość również musi mieć ustawioną "wartość false" lub nie została ustawiona dla adaptacyjną proxy włączenia.|  
  
 Poniższy przykład przedstawia konfiguracji typowych adaptacyjną serwera proxy.  
  
```xml  
<system.net>  
    <defaultProxy>  
      <proxy  scriptDownloadInterval="600"  
              scriptDownloadTimeout="30"  
              useDefaultCredentials="true"  
              usesystemdefaults="true"  
      />  
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
|`proxyaddress`lub<xref:System.Net.WebProxy.Address>|Adres serwera proxy do użycia.|  
|`bypassonlocal`lub<xref:System.Net.WebProxy.BypassProxyOnLocal>|Określa, czy serwer proxy jest pomijana dla adresów lokalnych.|  
|`bypasslist`lub<xref:System.Net.WebProxy.BypassArrayList>|Opisuje za pomocą wyrażeń regularnych, zestaw adresów, które pominąć serwer proxy.|  
|`usesystemdefaults`|Określa, czy ustawienia serwera proxy statyczne (adres serwera proxy, listy obejścia i obejście na lokalnym) są odczytywane z ustawień serwera proxy programu Internet Explorer dla użytkownika. Jeśli ta wartość jest równa "true", a następnie ustawienia serwera proxy statyczne z programu Internet Explorer będzie używany. .NET Framework 2.0, gdy ta wartość jest równa "true", ustawienia serwera proxy programu Internet Explorer ustawienia nie są zastępowane przez inne ustawienia serwera proxy w pliku konfiguracji. W programie .NET Framework 1.1 ustawienia serwera proxy programu Internet Explorer, może zostać przesłonięta przez inne ustawienia serwera proxy w pliku konfiguracji.<br /><br /> Jeśli ta wartość wynosi "false" lub nie zestawu, a następnie ustawienia serwera proxy statycznych może być określony w konfiguracji i zastąpią ustawienia serwera proxy programu Internet Explorer. Ta wartość również musi mieć ustawioną "wartość false" lub nie została ustawiona dla adaptacyjną proxy włączenia.|  
  
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
 [Wykrywanie serwera Proxy](../../../docs/framework/network-programming/automatic-proxy-detection.md)
