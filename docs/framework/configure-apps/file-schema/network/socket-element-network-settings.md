---
title: '&lt;gniazda&gt; — Element (ustawienia sieci)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/socket
- http://schemas.microsoft.com/.NetConfiguration/v2.0#socket
helpviewer_keywords:
- <socket> element
- socket element
ms.assetid: 366c634c-7d16-478f-aedf-053eda94a1a0
author: mcleblanc
ms.author: markl
ms.openlocfilehash: fb057ab75c31edd7bbdaf5d5115cda2802d3b057
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2018
ms.locfileid: "48028294"
---
# <a name="ltsocketgt-element-network-settings"></a>&lt;gniazda&gt; — Element (ustawienia sieci)
Określa, czy operacje gniazda używają portów.  
  
 \<Konfiguracja >  
\<system.net>  
\<Ustawienia >  
\<gniazda >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<socket  
  alwaysUseCompletionPortsForConnect="true|false"  
  alwaysUseCompletionPortsForAccept="true|false"  
  ipProtectionLevel="EdgeRestricted|Restricted|Unrestricted|Unspecified"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|**Atrybut**|**Opis**|  
|-------------------|---------------------|  
|`alwaysUseCompletionPortsForAccept`|Wskazuje, czy gniazda zawsze należy używać portów dla wywołań metod Accept. Wartość domyślna to `false`.|  
|`alwaysUseCompletionPortsForConnect`|Wskazuje, czy gniazda zawsze należy używać portów dla wywołania metody Connect. Wartość domyślna to `false`.|  
|`ipProtectionLevel`|Określa domyślny <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> do użycia dla gniazda. Wartość domyślna zależy od wersji systemu Windows.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[Ustawienia](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|Konfiguruje opcje sieciowe podstawowe dla <xref:System.Net> przestrzeni nazw.|  
  
## <a name="remarks"></a>Uwagi  
 `alwaysUseCompletionPortsForAccept` i `alwaysUseCompletionPortsForConnect` atrybuty są używane do określania domyślne zachowanie dotyczące używania portów przez klasy w <xref:System.Net.Sockets?displayProperty=nameWithType>.namespace. Porty zakończenia są zalecane w przypadku aplikacji serwera o wysokiej wydajności.  
  
 Wartością domyślną dla `alwaysUseCompletionPortsForAccept` i `alwaysUseCompletionPortsForConnect` atrybutów jest **false**.  
  
 <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A> Może służyć do uzyskania bieżącej wartości `alwaysUseCompletionPortsForAccept` atrybut z właściwych plików konfiguracji. <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A> Może służyć do uzyskania bieżącej wartości `alwaysUseCompletionPortsForConnect` atrybut z właściwych plików konfiguracji.  
  
 `ipProtectionLevel` Atrybut określa domyślny <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> do użycia dla gniazda. <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> Właściwość umożliwia skonfigurowanie ograniczeń dla gniazda IPv6 do określonego zakresu, takie jak adresy z takimi samymi link lokalny lub lokacji lokalnej prefiks. Ta opcja umożliwia aplikacjom do ograniczenia dostępu do gniazda IPv6. Takie ograniczenia, Włącz aplikacji uruchomionej w prywatnej sieci lokalnej po prostu i niezawodnie zabezpieczyć się przed atakami zewnętrznych. Ta opcja rozszerza się lub umożliwia zawężenie zakresu nasłuchiwania gniazda, dzięki czemu nieograniczonego dostępu z publicznych i prywatnych użytkowników, gdy jest to konieczne, lub ograniczać dostęp tylko do tej samej lokacji, zgodnie z wymaganiami.  
  
 To `ipProtectionLevel` ustawienie atrybutu ma wpływ tylko na początkowy ruch przychodzący:  
  
-   Serwer protokołu TCP nasłuchuje połączeń przychodzących na gniazdo.  
  
-   Aplikacja UDP, odbierania pakietów dla gniazda.  
  
 To ustawienie konfiguracji nie wpływa na nawiązano już połączenie połączenia protokołu TCP (ruch jest nieograniczony w obu kierunkach) i nie ma wpływu na aplikację, wysyłanie pakietów UDP.  
  
 Możliwe wartości parametru `ipProtectionLevel` ustawienie atrybutu odnoszą się do poziomu ochrony zdefiniowanych określonych w <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> wyliczenia w następujący sposób:  
  
|**Wartość atrybutu**|**Opis**|  
|-|-|  
|EdgeRestricted|Poziom ochrony IP jest edge z ograniczeniami. Ta wartość będzie używana przez aplikacje zaprojektowane do działania w Internecie. To ustawienie umożliwia przechodzenie translacji adresów sieciowych (NAT) przy użyciu implementacji Windows Teredo. Te aplikacje mogą pominąć IPv4 zapory, dzięki czemu aplikacje muszą być wzmocnione zabezpieczenia przed atakami internetowymi, skierowanych do otwartego portu. W systemie Windows Server 2003 i Windows XP wartością domyślną dla poziomu ochrony IP na gniazdo jest edge z ograniczeniami.|  
|z ograniczeniami|Poziom ochrony IP jest ograniczona. Ta wartość będzie używana przez aplikacji intranetowych, które nie implementują scenariuszy Internetu. Te aplikacje zwykle nie są przetestowane lub wzmocnione zabezpieczenia przed atakami internetową. To ustawienie powoduje ograniczenie odebrany ruch link-local.|  
|Bez ograniczeń|Poziom ochrony IP jest nieograniczony. Ta wartość będzie używana przez aplikacje przeznaczone do pracy w Internecie, łącznie z aplikacjami, wykorzystując możliwości Przechodzenie translatora adresów Sieciowych IPv6 do Windows (na przykład Teredo). Te aplikacje mogą pominąć IPv4 zapory, dzięki czemu aplikacje muszą być wzmocnione zabezpieczenia przed atakami internetowymi, skierowanych do otwartego portu. W systemie Windows Server 2008 R2 i Windows Vista wartością domyślną dla poziomu ochrony IP na gniazdo jest nieograniczony.|  
|Nie określono tego parametru|Poziom ochrony IP jest nieokreślony. Windows 7 i Windows Server 2008 R2 wartością domyślną dla poziomu ochrony IP na gniazdo jest nieokreślona.|  
  
 Wartością domyślną dla `ipProtectionLevel` atrybut jest **nieokreślony**.  
  
 <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> Właściwość może służyć do uzyskania bieżącej wartości `ipProtectionLevel` atrybut z właściwych plików konfiguracji.  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Ten element może być użyty w pliku konfiguracji aplikacji lub w pliku konfiguracji komputera (Machine.config).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak określić, że porty zakończenia powinien być używany i czy domyślnie <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> powinny być bez ograniczeń.  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <socket  
        alwaysUseCompletionPortsForAccept="true"  
        alwaysUseCompletionPortsForConnect="true"  
        ipProtectionLevel="Unrestricted"  
       />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Net?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SocketElement?displayProperty=nameWithType>  
 <xref:System.Net.Sockets?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.SocketOptionName.IPProtectionLevel?displayProperty=nameWithType>  
 [Schemat ustawień sieci](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
