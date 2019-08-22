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
ms.openlocfilehash: aa455945b839ada4100138d5bdf9fc239376e5cb
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663985"
---
# <a name="socket-element-network-settings"></a>\<Socket > — element (Ustawienia sieci)
Określa, czy operacje gniazda używają portów zakończenia.  
  
 \<> konfiguracji  
\<system.net>  
\<settings>  
\<> gniazda  
  
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
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[Ustawienia](settings-element-network-settings.md)|Konfiguruje podstawowe opcje sieci dla <xref:System.Net> przestrzeni nazw.|  
  
## <a name="remarks"></a>Uwagi  
 Atrybuty `alwaysUseCompletionPortsForAccept` <xref:System.Net.Sockets?displayProperty=nameWithType>i `alwaysUseCompletionPortsForConnect` służą do określania domyślnego zachowania dotyczącego używania portów zakończenia przez klasy w przestrzeni nazw. Porty uzupełniania są zalecane w przypadku aplikacji serwera o wysokiej wydajności.  
  
 Wartość domyślna dla `alwaysUseCompletionPortsForAccept` atrybutów i `alwaysUseCompletionPortsForConnect` jest równa **false**.  
  
 Można <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A> użyć, aby pobrać bieżącą wartość `alwaysUseCompletionPortsForAccept` atrybutu z odpowiednich plików konfiguracji. Można <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A> użyć, aby pobrać bieżącą wartość `alwaysUseCompletionPortsForConnect` atrybutu z odpowiednich plików konfiguracji.  
  
 Ten `ipProtectionLevel` atrybut określa wartość domyślną <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> do użycia w gnieździe. <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> Właściwość umożliwia konfigurowanie ograniczenia dla gniazda IPv6 w określonym zakresie, na przykład adresów z tym samym prefiksem lokalnym lub lokalnym. Ta opcja umożliwia aplikacjom nakładanie ograniczeń dostępu w gniazdach IPv6. Takie ograniczenia umożliwiają aplikacji działającej w prywatnej sieci LAN, aby po prostu i niezawodnie zabezpieczyć się przed atakami zewnętrznymi. Ta opcja rozszerza lub zawęża zakres gniazda nasłuchiwania, umożliwiając nieograniczony dostęp z publicznych i prywatnych użytkowników, jeśli jest to konieczne, lub ograniczanie dostępu tylko do tej samej lokacji, zgodnie z wymaganiami.  
  
 To `ipProtectionLevel` ustawienie atrybutu ma wpływ tylko na początkowy ruch przychodzący:  
  
- Serwer TCP nasłuchuje połączeń przychodzących w gnieździe.  
  
- Aplikacja UDP otrzymująca pakiet w gnieździe.  
  
 To ustawienie konfiguracji nie ma wpływu na już ustanowione połączenia TCP (ruch nie jest ograniczony w obu kierunkach) i nie ma wpływu na aplikację wysyłającą pakiety UDP.  
  
 Możliwe wartości `ipProtectionLevel` ustawienia atrybutu odpowiadają zdefiniowanym poziomom ochrony określonym <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> w wyliczeniu w następujący sposób:  
  
|**Wartość atrybutu**|**Opis**|  
|-|-|  
|EdgeRestricted|Poziom ochrony adresów IP jest ograniczony do krawędzi. Ta wartość będzie używana przez aplikacje przeznaczone do działania przez Internet. To ustawienie nie zezwala na przechodzenie translacji adresów sieciowych (NAT) przy użyciu implementacji Teredo systemu Windows. Aplikacje te mogą pomijać zapory IPv4, więc aplikacje muszą być wzmocnione przed atakami z Internetu kierowanymi na otwarty port. W systemach Windows Server 2003 i Windows XP wartość domyślna dla poziomu ochrony IP w gnieździe jest ograniczona do krawędzi.|  
|Podlega|Poziom ochrony adresów IP jest ograniczony. Ta wartość będzie używana przez aplikacje intranetowe, które nie implementują scenariuszy internetowych. Te aplikacje zazwyczaj nie są przetestowane ani nie są zaostrzone przed atakami w stylu Internetu. To ustawienie ograniczy odbieranie ruchu tylko do połączenia lokalnego.|  
|Nieograniczone|Poziom ochrony adresów IP nie jest ograniczony. Ta wartość będzie używana przez aplikacje przeznaczone do działania przez Internet, w tym aplikacje korzystające z możliwości przechodzenia do translatora adresów sieciowych IPv6 wbudowanych w system Windows (na przykład Teredo). Aplikacje te mogą pomijać zapory IPv4, więc aplikacje muszą być wzmocnione przed atakami z Internetu kierowanymi na otwarty port. W systemach Windows Server 2008 R2 i Windows Vista wartość domyślna dla poziomu ochrony adresów IP w gnieździe jest nieograniczona.|  
|Nieokreślony|Nie określono poziomu ochrony adresów IP. W systemach Windows 7 i Windows Server 2008 R2 nie określono wartości domyślnej dla poziomu ochrony adresów IP w gnieździe.|  
  
 Wartość domyślna dla `ipProtectionLevel` atrybutu jest nieokreślona.  
  
 Właściwość może służyć do uzyskiwania bieżącej wartości `ipProtectionLevel` atrybutu z odpowiednich plików konfiguracji. <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A>  
  
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
