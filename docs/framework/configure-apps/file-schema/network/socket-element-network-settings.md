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
# <a name="socket-element-network-settings"></a><span data-ttu-id="6778a-102">\<socket>, element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="6778a-102">\<socket> Element (Network Settings)</span></span>
<span data-ttu-id="6778a-103">Określa, czy operacje gniazda używają portów zakończenia.</span><span class="sxs-lookup"><span data-stu-id="6778a-103">Specifies whether socket operations use completion ports.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<socket>**

## <a name="syntax"></a><span data-ttu-id="6778a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6778a-104">Syntax</span></span>  
  
```xml  
<socket  
  alwaysUseCompletionPortsForConnect="true|false"  
  alwaysUseCompletionPortsForAccept="true|false"  
  ipProtectionLevel="EdgeRestricted|Restricted|Unrestricted|Unspecified"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6778a-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6778a-105">Attributes and Elements</span></span>  
 <span data-ttu-id="6778a-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6778a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6778a-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6778a-107">Attributes</span></span>  
  
|<span data-ttu-id="6778a-108">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="6778a-108">**Attribute**</span></span>|<span data-ttu-id="6778a-109">**Opis**</span><span class="sxs-lookup"><span data-stu-id="6778a-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`alwaysUseCompletionPortsForAccept`|<span data-ttu-id="6778a-110">Wskazuje, czy gniazdo ma zawsze używać portów zakończenia dla wywołań metod akceptowania.</span><span class="sxs-lookup"><span data-stu-id="6778a-110">Indicates whether the socket should always use completion ports for Accept method calls.</span></span> <span data-ttu-id="6778a-111">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="6778a-111">The default value is `false`.</span></span>|  
|`alwaysUseCompletionPortsForConnect`|<span data-ttu-id="6778a-112">Wskazuje, czy gniazdo ma zawsze używać portów zakończenia dla wywołań metod Connect.</span><span class="sxs-lookup"><span data-stu-id="6778a-112">Indicates whether the socket should always use completion ports for Connect method calls.</span></span> <span data-ttu-id="6778a-113">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="6778a-113">The default value is `false`.</span></span>|  
|`ipProtectionLevel`|<span data-ttu-id="6778a-114">Określa wartość domyślną <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> dla gniazda.</span><span class="sxs-lookup"><span data-stu-id="6778a-114">Specifies the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> to use for a socket.</span></span> <span data-ttu-id="6778a-115">Wartość domyślna zależy od wersji systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="6778a-115">The default value depends on the version of Windows.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6778a-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6778a-116">Child Elements</span></span>  
 <span data-ttu-id="6778a-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="6778a-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6778a-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6778a-118">Parent Elements</span></span>  
  
|<span data-ttu-id="6778a-119">**Postaci**</span><span class="sxs-lookup"><span data-stu-id="6778a-119">**Element**</span></span>|<span data-ttu-id="6778a-120">**Opis**</span><span class="sxs-lookup"><span data-stu-id="6778a-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="6778a-121">ustawienia</span><span class="sxs-lookup"><span data-stu-id="6778a-121">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="6778a-122">Konfiguruje podstawowe opcje sieci dla <xref:System.Net> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="6778a-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6778a-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6778a-123">Remarks</span></span>  
 <span data-ttu-id="6778a-124">`alwaysUseCompletionPortsForAccept`Atrybuty i służą `alwaysUseCompletionPortsForConnect` do określania domyślnego zachowania dotyczącego używania portów zakończenia przez klasy w <xref:System.Net.Sockets?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="6778a-124">The `alwaysUseCompletionPortsForAccept` and `alwaysUseCompletionPortsForConnect` attributes are used to specify the default behavior regarding the use of completion ports by the classes in the <xref:System.Net.Sockets?displayProperty=nameWithType>.namespace.</span></span> <span data-ttu-id="6778a-125">Porty uzupełniania są zalecane w przypadku aplikacji serwera o wysokiej wydajności.</span><span class="sxs-lookup"><span data-stu-id="6778a-125">Completion ports are recommended for high performance server applications.</span></span>  
  
 <span data-ttu-id="6778a-126">Wartość domyślna dla `alwaysUseCompletionPortsForAccept` atrybutów i jest równa `alwaysUseCompletionPortsForConnect` **false**.</span><span class="sxs-lookup"><span data-stu-id="6778a-126">The default value for the `alwaysUseCompletionPortsForAccept` and `alwaysUseCompletionPortsForConnect` attributes is **false**.</span></span>  
  
 <span data-ttu-id="6778a-127"><xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A>Można użyć, aby pobrać bieżącą wartość `alwaysUseCompletionPortsForAccept` atrybutu z odpowiednich plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6778a-127">The <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A> can be used to get the current value of the `alwaysUseCompletionPortsForAccept` attribute from applicable configuration files.</span></span> <span data-ttu-id="6778a-128"><xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A>Można użyć, aby pobrać bieżącą wartość `alwaysUseCompletionPortsForConnect` atrybutu z odpowiednich plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6778a-128">The <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A> can be used to get the current value of the `alwaysUseCompletionPortsForConnect` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="6778a-129">Ten `ipProtectionLevel` atrybut określa wartość domyślną <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> do użycia w gnieździe.</span><span class="sxs-lookup"><span data-stu-id="6778a-129">The `ipProtectionLevel` attribute specifies the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> to use for a socket.</span></span> <span data-ttu-id="6778a-130"><xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A>Właściwość umożliwia konfigurowanie ograniczenia dla gniazda IPv6 w określonym zakresie, na przykład adresów z tym samym prefiksem lokalnym lub lokalnym.</span><span class="sxs-lookup"><span data-stu-id="6778a-130">The <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> property enables configuration of a restriction for an IPv6 socket to a specified scope, such as addresses with the same link local or site local prefix.</span></span> <span data-ttu-id="6778a-131">Ta opcja umożliwia aplikacjom nakładanie ograniczeń dostępu w gniazdach IPv6.</span><span class="sxs-lookup"><span data-stu-id="6778a-131">This option enables applications to place access restrictions on IPv6 sockets.</span></span> <span data-ttu-id="6778a-132">Takie ograniczenia umożliwiają aplikacji działającej w prywatnej sieci LAN, aby po prostu i niezawodnie zabezpieczyć się przed atakami zewnętrznymi.</span><span class="sxs-lookup"><span data-stu-id="6778a-132">Such restrictions enable an application running on a private LAN to simply and robustly harden itself against external attacks.</span></span> <span data-ttu-id="6778a-133">Ta opcja rozszerza lub zawęża zakres gniazda nasłuchiwania, umożliwiając nieograniczony dostęp z publicznych i prywatnych użytkowników, jeśli jest to konieczne, lub ograniczanie dostępu tylko do tej samej lokacji, zgodnie z wymaganiami.</span><span class="sxs-lookup"><span data-stu-id="6778a-133">This option widens or narrows the scope of a listening socket, enabling unrestricted access from public and private users when appropriate, or restricting access only to the same site, as required.</span></span>  
  
 <span data-ttu-id="6778a-134">To `ipProtectionLevel` ustawienie atrybutu ma wpływ tylko na początkowy ruch przychodzący:</span><span class="sxs-lookup"><span data-stu-id="6778a-134">This `ipProtectionLevel` attribute setting affects only initial incoming traffic:</span></span>  
  
- <span data-ttu-id="6778a-135">Serwer TCP nasłuchuje połączeń przychodzących w gnieździe.</span><span class="sxs-lookup"><span data-stu-id="6778a-135">A TCP server listening for incoming connections on a socket.</span></span>  
  
- <span data-ttu-id="6778a-136">Aplikacja UDP otrzymująca pakiet w gnieździe.</span><span class="sxs-lookup"><span data-stu-id="6778a-136">A UDP application receiving a packet on a socket.</span></span>  
  
 <span data-ttu-id="6778a-137">To ustawienie konfiguracji nie ma wpływu na już ustanowione połączenia TCP (ruch nie jest ograniczony w obu kierunkach) i nie ma wpływu na aplikację wysyłającą pakiety UDP.</span><span class="sxs-lookup"><span data-stu-id="6778a-137">This configuration setting does not affect already established TCP connections (traffic is unrestricted in both directions) and does not affect an application sending UDP packets.</span></span>  
  
 <span data-ttu-id="6778a-138">Możliwe wartości `ipProtectionLevel` ustawienia atrybutu odpowiadają zdefiniowanym poziomom ochrony określonym w <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> wyliczeniu w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="6778a-138">The possible values for the `ipProtectionLevel` attribute setting correspond with the defined protection levels specified in the <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> enumeration as follows:</span></span>  
  
|<span data-ttu-id="6778a-139">**Wartość atrybutu**</span><span class="sxs-lookup"><span data-stu-id="6778a-139">**Attribute Value**</span></span>|<span data-ttu-id="6778a-140">**Opis**</span><span class="sxs-lookup"><span data-stu-id="6778a-140">**Description**</span></span>|  
|-|-|  
|<span data-ttu-id="6778a-141">EdgeRestricted</span><span class="sxs-lookup"><span data-stu-id="6778a-141">EdgeRestricted</span></span>|<span data-ttu-id="6778a-142">Poziom ochrony adresów IP jest ograniczony do krawędzi.</span><span class="sxs-lookup"><span data-stu-id="6778a-142">The IP protection level is edge restricted.</span></span> <span data-ttu-id="6778a-143">Ta wartość będzie używana przez aplikacje przeznaczone do działania przez Internet.</span><span class="sxs-lookup"><span data-stu-id="6778a-143">This value would be used by applications designed to operate across the Internet.</span></span> <span data-ttu-id="6778a-144">To ustawienie nie zezwala na przechodzenie translacji adresów sieciowych (NAT) przy użyciu implementacji Teredo systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="6778a-144">This setting does not allow Network Address Translation (NAT) traversal using the Windows Teredo implementation.</span></span> <span data-ttu-id="6778a-145">Aplikacje te mogą pomijać zapory IPv4, więc aplikacje muszą być wzmocnione przed atakami z Internetu kierowanymi na otwarty port.</span><span class="sxs-lookup"><span data-stu-id="6778a-145">These applications may bypass IPv4 firewalls, so applications must be hardened against Internet attacks directed at the opened port.</span></span> <span data-ttu-id="6778a-146">W systemach Windows Server 2003 i Windows XP wartość domyślna dla poziomu ochrony IP w gnieździe jest ograniczona do krawędzi.</span><span class="sxs-lookup"><span data-stu-id="6778a-146">On Windows Server 2003 and Windows XP, the default value for the IP Protection level on a socket is edge restricted.</span></span>|  
|<span data-ttu-id="6778a-147">Z ograniczeniami</span><span class="sxs-lookup"><span data-stu-id="6778a-147">Restricted</span></span>|<span data-ttu-id="6778a-148">Poziom ochrony adresów IP jest ograniczony.</span><span class="sxs-lookup"><span data-stu-id="6778a-148">The IP protection level is restricted.</span></span> <span data-ttu-id="6778a-149">Ta wartość będzie używana przez aplikacje intranetowe, które nie implementują scenariuszy internetowych.</span><span class="sxs-lookup"><span data-stu-id="6778a-149">This value would be used by intranet applications that do not implement Internet scenarios.</span></span> <span data-ttu-id="6778a-150">Te aplikacje zazwyczaj nie są przetestowane ani nie są zaostrzone przed atakami w stylu Internetu.</span><span class="sxs-lookup"><span data-stu-id="6778a-150">These applications are generally not tested or hardened against Internet-style attacks.</span></span> <span data-ttu-id="6778a-151">To ustawienie ograniczy odbieranie ruchu tylko do połączenia lokalnego.</span><span class="sxs-lookup"><span data-stu-id="6778a-151">This setting will limit the received traffic to link-local only.</span></span>|  
|<span data-ttu-id="6778a-152">Bez ograniczeń</span><span class="sxs-lookup"><span data-stu-id="6778a-152">Unrestricted</span></span>|<span data-ttu-id="6778a-153">Poziom ochrony adresów IP nie jest ograniczony.</span><span class="sxs-lookup"><span data-stu-id="6778a-153">The IP protection level is unrestricted.</span></span> <span data-ttu-id="6778a-154">Ta wartość będzie używana przez aplikacje przeznaczone do działania przez Internet, w tym aplikacje korzystające z możliwości przechodzenia do translatora adresów sieciowych IPv6 wbudowanych w system Windows (na przykład Teredo).</span><span class="sxs-lookup"><span data-stu-id="6778a-154">This value would be used by applications designed to operate across the Internet, including applications taking advantage of IPv6 NAT traversal capabilities built into Windows (Teredo, for example).</span></span> <span data-ttu-id="6778a-155">Aplikacje te mogą pomijać zapory IPv4, więc aplikacje muszą być wzmocnione przed atakami z Internetu kierowanymi na otwarty port.</span><span class="sxs-lookup"><span data-stu-id="6778a-155">These applications may bypass IPv4 firewalls, so applications must be hardened against Internet attacks directed at the opened port.</span></span> <span data-ttu-id="6778a-156">W systemach Windows Server 2008 R2 i Windows Vista wartość domyślna dla poziomu ochrony adresów IP w gnieździe jest nieograniczona.</span><span class="sxs-lookup"><span data-stu-id="6778a-156">On Windows Server 2008 R2 and Windows Vista, the default value for the IP Protection level on a socket is unrestricted.</span></span>|  
|<span data-ttu-id="6778a-157">Nie określono</span><span class="sxs-lookup"><span data-stu-id="6778a-157">Unspecified</span></span>|<span data-ttu-id="6778a-158">Nie określono poziomu ochrony adresów IP.</span><span class="sxs-lookup"><span data-stu-id="6778a-158">The IP protection level is unspecified.</span></span> <span data-ttu-id="6778a-159">W systemach Windows 7 i Windows Server 2008 R2 nie określono wartości domyślnej dla poziomu ochrony adresów IP w gnieździe.</span><span class="sxs-lookup"><span data-stu-id="6778a-159">On Windows 7 and Windows Server 2008 R2, the default value for the IP Protection level on a socket is unspecified.</span></span>|  
  
 <span data-ttu-id="6778a-160">Wartość domyślna dla `ipProtectionLevel` atrybutu jest **nieokreślona**.</span><span class="sxs-lookup"><span data-stu-id="6778a-160">The default value for the `ipProtectionLevel` attribute is **Unspecified**.</span></span>  
  
 <span data-ttu-id="6778a-161"><xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A>Właściwość może służyć do uzyskiwania bieżącej wartości `ipProtectionLevel` atrybutu z odpowiednich plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6778a-161">The <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> property can be used to get the current value of the `ipProtectionLevel` attribute from applicable configuration files.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="6778a-162">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="6778a-162">Configuration Files</span></span>  
 <span data-ttu-id="6778a-163">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="6778a-163">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6778a-164">Przykład</span><span class="sxs-lookup"><span data-stu-id="6778a-164">Example</span></span>  
 <span data-ttu-id="6778a-165">Poniższy przykład pokazuje, jak określić, że powinny być używane porty zakończenia oraz że wartość domyślna <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> powinna być bez ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="6778a-165">The following example shows how to specify that completion ports should be used and that the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> should be unrestricted.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6778a-166">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6778a-166">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SocketElement?displayProperty=nameWithType>
- <xref:System.Net.Sockets?displayProperty=nameWithType>
- <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SocketOptionName.IPProtectionLevel?displayProperty=nameWithType>
- [<span data-ttu-id="6778a-167">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="6778a-167">Network Settings Schema</span></span>](index.md)
