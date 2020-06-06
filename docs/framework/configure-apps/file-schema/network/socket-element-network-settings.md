---
title: <socket>, element (ustawienia sieci)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/socket
- http://schemas.microsoft.com/.NetConfiguration/v2.0#socket
helpviewer_keywords:
- <socket> element
- socket element
ms.assetid: 366c634c-7d16-478f-aedf-053eda94a1a0
ms.openlocfilehash: 0e2b369eccfbc658a790ef61a961315a88361669
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "74089089"
---
# <a name="socket-element-network-settings"></a>\<socket>, element (ustawienia sieci)
Określa, czy operacje gniazda używają portów zakończenia.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<socket>**

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
|`alwaysUseCompletionPortsForAccept`|Wskazuje, czy gniazdo ma zawsze używać portów zakończenia dla wywołań metod akceptowania. Wartość domyślna to `false`.|  
|`alwaysUseCompletionPortsForConnect`|Wskazuje, czy gniazdo ma zawsze używać portów zakończenia dla wywołań metod Connect. Wartość domyślna to `false`.|  
|`ipProtectionLevel`|Określa wartość domyślną <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> dla gniazda. Wartość domyślna zależy od wersji systemu Windows.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Postaci**|**Opis**|  
|-----------------|---------------------|  
|[ustawienia](settings-element-network-settings.md)|Konfiguruje podstawowe opcje sieci dla <xref:System.Net> przestrzeni nazw.|  
  
## <a name="remarks"></a>Uwagi  
 `alwaysUseCompletionPortsForAccept`Atrybuty i służą `alwaysUseCompletionPortsForConnect` do określania domyślnego zachowania dotyczącego używania portów zakończenia przez klasy w <xref:System.Net.Sockets?displayProperty=nameWithType> przestrzeni nazw. Porty uzupełniania są zalecane w przypadku aplikacji serwera o wysokiej wydajności.  
  
 Wartość domyślna dla `alwaysUseCompletionPortsForAccept` atrybutów i jest równa `alwaysUseCompletionPortsForConnect` **false**.  
  
 <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A>Można użyć, aby pobrać bieżącą wartość `alwaysUseCompletionPortsForAccept` atrybutu z odpowiednich plików konfiguracji. <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A>Można użyć, aby pobrać bieżącą wartość `alwaysUseCompletionPortsForConnect` atrybutu z odpowiednich plików konfiguracji.  
  
 Ten `ipProtectionLevel` atrybut określa wartość domyślną <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> do użycia w gnieździe. <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A>Właściwość umożliwia konfigurowanie ograniczenia dla gniazda IPv6 w określonym zakresie, na przykład adresów z tym samym prefiksem lokalnym lub lokalnym. Ta opcja umożliwia aplikacjom nakładanie ograniczeń dostępu w gniazdach IPv6. Takie ograniczenia umożliwiają aplikacji działającej w prywatnej sieci LAN, aby po prostu i niezawodnie zabezpieczyć się przed atakami zewnętrznymi. Ta opcja rozszerza lub zawęża zakres gniazda nasłuchiwania, umożliwiając nieograniczony dostęp z publicznych i prywatnych użytkowników, jeśli jest to konieczne, lub ograniczanie dostępu tylko do tej samej lokacji, zgodnie z wymaganiami.  
  
 To `ipProtectionLevel` ustawienie atrybutu ma wpływ tylko na początkowy ruch przychodzący:  
  
- Serwer TCP nasłuchuje połączeń przychodzących w gnieździe.  
  
- Aplikacja UDP otrzymująca pakiet w gnieździe.  
  
 To ustawienie konfiguracji nie ma wpływu na już ustanowione połączenia TCP (ruch nie jest ograniczony w obu kierunkach) i nie ma wpływu na aplikację wysyłającą pakiety UDP.  
  
 Możliwe wartości `ipProtectionLevel` ustawienia atrybutu odpowiadają zdefiniowanym poziomom ochrony określonym w <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> wyliczeniu w następujący sposób:  
  
|**Wartość atrybutu**|**Opis**|  
|-|-|  
|EdgeRestricted|Poziom ochrony adresów IP jest ograniczony do krawędzi. Ta wartość będzie używana przez aplikacje przeznaczone do działania przez Internet. To ustawienie nie zezwala na przechodzenie translacji adresów sieciowych (NAT) przy użyciu implementacji Teredo systemu Windows. Aplikacje te mogą pomijać zapory IPv4, więc aplikacje muszą być wzmocnione przed atakami z Internetu kierowanymi na otwarty port. W systemach Windows Server 2003 i Windows XP wartość domyślna dla poziomu ochrony IP w gnieździe jest ograniczona do krawędzi.|  
|Z ograniczeniami|Poziom ochrony adresów IP jest ograniczony. Ta wartość będzie używana przez aplikacje intranetowe, które nie implementują scenariuszy internetowych. Te aplikacje zazwyczaj nie są przetestowane ani nie są zaostrzone przed atakami w stylu Internetu. To ustawienie ograniczy odbieranie ruchu tylko do połączenia lokalnego.|  
|Bez ograniczeń|Poziom ochrony adresów IP nie jest ograniczony. Ta wartość będzie używana przez aplikacje przeznaczone do działania przez Internet, w tym aplikacje korzystające z możliwości przechodzenia do translatora adresów sieciowych IPv6 wbudowanych w system Windows (na przykład Teredo). Aplikacje te mogą pomijać zapory IPv4, więc aplikacje muszą być wzmocnione przed atakami z Internetu kierowanymi na otwarty port. W systemach Windows Server 2008 R2 i Windows Vista wartość domyślna dla poziomu ochrony adresów IP w gnieździe jest nieograniczona.|  
|Nie określono|Nie określono poziomu ochrony adresów IP. W systemach Windows 7 i Windows Server 2008 R2 nie określono wartości domyślnej dla poziomu ochrony adresów IP w gnieździe.|  
  
 Wartość domyślna dla `ipProtectionLevel` atrybutu jest **nieokreślona**.  
  
 <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A>Właściwość może służyć do uzyskiwania bieżącej wartości `ipProtectionLevel` atrybutu z odpowiednich plików konfiguracji.  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak określić, że powinny być używane porty zakończenia oraz że wartość domyślna <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> powinna być bez ograniczeń.  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Net?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SocketElement?displayProperty=nameWithType>
- <xref:System.Net.Sockets?displayProperty=nameWithType>
- <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SocketOptionName.IPProtectionLevel?displayProperty=nameWithType>
- [Schemat ustawień sieci](index.md)
