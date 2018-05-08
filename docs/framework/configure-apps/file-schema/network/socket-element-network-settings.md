---
title: '&lt;gniazda&gt; elementu (ustawienia sieciowe)'
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
manager: markl
ms.openlocfilehash: 995a89dd67664fd6a408f88f20f6837d2dbaaad4
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltsocketgt-element-network-settings"></a>&lt;gniazda&gt; elementu (ustawienia sieciowe)
Określa, czy operacje gniazda używać portów.  
  
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
|`ipProtectionLevel`|Określa domyślny <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> dla gniazda. Wartość domyślna zależy od wersji systemu Windows.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[Ustawienia](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|Służy do konfigurowania opcji sieci podstawowej dla <xref:System.Net> przestrzeni nazw.|  
  
## <a name="remarks"></a>Uwagi  
 `alwaysUseCompletionPortsForAccept` i `alwaysUseCompletionPortsForConnect` atrybuty służą do określania domyślnego zachowania dotyczące wykorzystania portów przez klasy w <xref:System.Net.Sockets?displayProperty=nameWithType>.namespace. Porty zakończenia są zalecane dla aplikacji serwera wysokiej wydajności.  
  
 Wartość domyślna dla `alwaysUseCompletionPortsForAccept` i `alwaysUseCompletionPortsForConnect` atrybutów jest **false**.  
  
 <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A> Można pobrać wartości bieżącego `alwaysUseCompletionPortsForAccept` atrybutu z plików zastosowania konfiguracji. <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A> Można pobrać wartości bieżącego `alwaysUseCompletionPortsForConnect` atrybutu z plików zastosowania konfiguracji.  
  
 `ipProtectionLevel` Atrybut określa domyślny <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> dla gniazda. <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> Właściwości umożliwia konfigurację ograniczeń dla gniazda IPv6 do określonego zakresu, takie jak adresy o tej samej link lokalnego lub lokacji lokalnej prefiks. Ta opcja umożliwia aplikacjom ograniczają dostęp do protokołu IPv6 sockets. Takie ograniczenia Włącz aplikacji uruchomionej w prywatnej sieci LAN po prostu i niezawodnie zabezpieczyć się przed atakami zewnętrznych. Ta opcja rozszerzenie lub znajduje się w zakresie zakres nasłuchiwania gniazda, włączanie nieograniczony dostęp z publicznych i prywatnych użytkowników, gdy jest to konieczne, lub ograniczać dostęp tylko do tej samej lokacji, zgodnie z wymaganiami.  
  
 To `ipProtectionLevel` atrybutu ustawienie ma wpływ tylko na początkowy ruch przychodzący:  
  
-   Serwer protokołu TCP nasłuchuje przychodzących połączeń dla gniazda.  
  
-   Aplikacja UDP, odbierania pakietów dla gniazda.  
  
 To ustawienie konfiguracji nie ma wpływu na już istniejących połączeń TCP (ruch nieograniczony w obu kierunkach) i nie wpływa na aplikację wysyłania pakietów UDP.  
  
 Możliwe wartości `ipProtectionLevel` ustawienie atrybutu odpowiadają poziomów ochrony zdefiniowanych określone w <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> wyliczenia w następujący sposób:  
  
|**Wartość atrybutu**|**Opis**|  
|-|-|  
|EdgeRestricted|Poziom ochrony IP jest ograniczone krawędzi. Ta wartość może być używane przez aplikacje, przeznaczonych do pracy w Internecie. To ustawienie umożliwia przechodzenie translacji adresów sieciowych (NAT) przy użyciu implementacji protokołu Teredo systemu Windows. Te aplikacje mogą obejścia zapory IPv4, więc aplikacji musi być wzmocnione zabezpieczenia przed atakami Internet skierowane do otwartego portu. W systemie Windows Server 2003 i Windows XP wartością domyślną dla poziomu ochrony IP na gnieździe jest ograniczone krawędzi.|  
|Ograniczone|Poziom ochrony IP jest ograniczone. Ta wartość będzie używana przez aplikacji intranetowych, które nie implementują scenariuszy Internetu. Te aplikacje są zazwyczaj nie badane lub wzmocnione zabezpieczenia przed atakami stylu Internet. To ustawienie powoduje ograniczenie odebrany ruch do link-local.|  
|Bez ograniczeń|Poziom ochrony IP jest nieograniczony. Ta wartość będzie służyć przez aplikacje przeznaczone do pracy w Internecie, w tym aplikacje wykorzystać możliwości przechodzenie IPv6 translatora adresów Sieciowych w systemie Windows (na przykład Teredo). Te aplikacje mogą obejścia zapory IPv4, więc aplikacji musi być wzmocnione zabezpieczenia przed atakami Internet skierowane do otwartego portu. W systemie Windows Server 2008 R2 i Windows Vista wartością domyślną dla poziomu ochrony IP na gnieździe jest nieograniczony.|  
|Nieokreślony|Poziom ochrony IP jest nieokreślony. W systemie Windows 7 i Windows Server 2008 R2 wartością domyślną dla poziomu ochrony IP na gnieździe jest nieokreślony.|  
  
 Wartość domyślna dla `ipProtectionLevel` atrybutu **nieokreślony**.  
  
 <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> Właściwości można pobrać wartości bieżącego `ipProtectionLevel` atrybutu z plików zastosowania konfiguracji.  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Ten element może być użyty w pliku konfiguracji aplikacji lub pliku konfiguracji komputera (Machine.config).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak określić, że używane portów, a wartość domyślna <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> powinny być nieograniczone.  
  
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
