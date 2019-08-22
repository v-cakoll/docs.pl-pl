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
# <a name="socket-element-network-settings"></a><span data-ttu-id="b0a3c-102">\<Socket > — element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="b0a3c-102">\<socket> Element (Network Settings)</span></span>
<span data-ttu-id="b0a3c-103">Określa, czy operacje gniazda używają portów zakończenia.</span><span class="sxs-lookup"><span data-stu-id="b0a3c-103">Specifies whether socket operations use completion ports.</span></span>  
  
 <span data-ttu-id="b0a3c-104">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="b0a3c-104">\<configuration></span></span>  
<span data-ttu-id="b0a3c-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="b0a3c-105">\<system.net></span></span>  
<span data-ttu-id="b0a3c-106">\<settings></span><span class="sxs-lookup"><span data-stu-id="b0a3c-106">\<settings></span></span>  
<span data-ttu-id="b0a3c-107">\<> gniazda</span><span class="sxs-lookup"><span data-stu-id="b0a3c-107">\<socket></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0a3c-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="b0a3c-108">Syntax</span></span>  
  
```xml  
<socket  
  alwaysUseCompletionPortsForConnect="true|false"  
  alwaysUseCompletionPortsForAccept="true|false"  
  ipProtectionLevel="EdgeRestricted|Restricted|Unrestricted|Unspecified"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b0a3c-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b0a3c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b0a3c-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b0a3c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b0a3c-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b0a3c-111">Attributes</span></span>  
  
|<span data-ttu-id="b0a3c-112">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="b0a3c-112">**Attribute**</span></span>|<span data-ttu-id="b0a3c-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="b0a3c-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`alwaysUseCompletionPortsForAccept`|<span data-ttu-id="b0a3c-114">Wskazuje, czy gniazdo ma zawsze używać portów zakończenia dla wywołań metod akceptowania.</span><span class="sxs-lookup"><span data-stu-id="b0a3c-114">Indicates whether the socket should always use completion ports for Accept method calls.</span></span> <span data-ttu-id="b0a3c-115">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="b0a3c-115">The default value is `false`.</span></span>|  
|`alwaysUseCompletionPortsForConnect`|<span data-ttu-id="b0a3c-116">Wskazuje, czy gniazdo ma zawsze używać portów zakończenia dla wywołań metod Connect.</span><span class="sxs-lookup"><span data-stu-id="b0a3c-116">Indicates whether the socket should always use completion ports for Connect method calls.</span></span> <span data-ttu-id="b0a3c-117">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="b0a3c-117">The default value is `false`.</span></span>|  
|`ipProtectionLevel`|<span data-ttu-id="b0a3c-118">Określa wartość domyślną <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> dla gniazda.</span><span class="sxs-lookup"><span data-stu-id="b0a3c-118">Specifies the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> to use for a socket.</span></span> <span data-ttu-id="b0a3c-119">Wartość domyślna zależy od wersji systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="b0a3c-119">The default value depends on the version of Windows.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b0a3c-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b0a3c-120">Child Elements</span></span>  
 <span data-ttu-id="b0a3c-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="b0a3c-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b0a3c-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b0a3c-122">Parent Elements</span></span>  
  
|<span data-ttu-id="b0a3c-123">**Element**</span><span class="sxs-lookup"><span data-stu-id="b0a3c-123">**Element**</span></span>|<span data-ttu-id="b0a3c-124">**Opis**</span><span class="sxs-lookup"><span data-stu-id="b0a3c-124">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="b0a3c-125">Ustawienia</span><span class="sxs-lookup"><span data-stu-id="b0a3c-125">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="b0a3c-126">Konfiguruje podstawowe opcje sieci dla <xref:System.Net> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="b0a3c-126">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b0a3c-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b0a3c-127">Remarks</span></span>  
 <span data-ttu-id="b0a3c-128">Atrybuty `alwaysUseCompletionPortsForAccept` <xref:System.Net.Sockets?displayProperty=nameWithType>i `alwaysUseCompletionPortsForConnect` służą do określania domyślnego zachowania dotyczącego używania portów zakończenia przez klasy w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="b0a3c-128">The `alwaysUseCompletionPortsForAccept` and `alwaysUseCompletionPortsForConnect` attributes are used to specify the default behavior regarding the use of completion ports by the classes in the <xref:System.Net.Sockets?displayProperty=nameWithType>.namespace.</span></span> <span data-ttu-id="b0a3c-129">Porty uzupełniania są zalecane w przypadku aplikacji serwera o wysokiej wydajności.</span><span class="sxs-lookup"><span data-stu-id="b0a3c-129">Completion ports are recommended for high performance server applications.</span></span>  
  
 <span data-ttu-id="b0a3c-130">Wartość domyślna dla `alwaysUseCompletionPortsForAccept` atrybutów i `alwaysUseCompletionPortsForConnect` jest równa **false**.</span><span class="sxs-lookup"><span data-stu-id="b0a3c-130">The default value for the `alwaysUseCompletionPortsForAccept` and `alwaysUseCompletionPortsForConnect` attributes is **false**.</span></span>  
  
 <span data-ttu-id="b0a3c-131">Można <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A> użyć, aby pobrać bieżącą wartość `alwaysUseCompletionPortsForAccept` atrybutu z odpowiednich plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="b0a3c-131">The <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A> can be used to get the current value of the `alwaysUseCompletionPortsForAccept` attribute from applicable configuration files.</span></span> <span data-ttu-id="b0a3c-132">Można <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A> użyć, aby pobrać bieżącą wartość `alwaysUseCompletionPortsForConnect` atrybutu z odpowiednich plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="b0a3c-132">The <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A> can be used to get the current value of the `alwaysUseCompletionPortsForConnect` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="b0a3c-133">Ten `ipProtectionLevel` atrybut określa wartość domyślną <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> do użycia w gnieździe.</span><span class="sxs-lookup"><span data-stu-id="b0a3c-133">The `ipProtectionLevel` attribute specifies the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> to use for a socket.</span></span> <span data-ttu-id="b0a3c-134"><xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> Właściwość umożliwia konfigurowanie ograniczenia dla gniazda IPv6 w określonym zakresie, na przykład adresów z tym samym prefiksem lokalnym lub lokalnym.</span><span class="sxs-lookup"><span data-stu-id="b0a3c-134">The <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> property enables configuration of a restriction for an IPv6 socket to a specified scope, such as addresses with the same link local or site local prefix.</span></span> <span data-ttu-id="b0a3c-135">Ta opcja umożliwia aplikacjom nakładanie ograniczeń dostępu w gniazdach IPv6.</span><span class="sxs-lookup"><span data-stu-id="b0a3c-135">This option enables applications to place access restrictions on IPv6 sockets.</span></span> <span data-ttu-id="b0a3c-136">Takie ograniczenia umożliwiają aplikacji działającej w prywatnej sieci LAN, aby po prostu i niezawodnie zabezpieczyć się przed atakami zewnętrznymi.</span><span class="sxs-lookup"><span data-stu-id="b0a3c-136">Such restrictions enable an application running on a private LAN to simply and robustly harden itself against external attacks.</span></span> <span data-ttu-id="b0a3c-137">Ta opcja rozszerza lub zawęża zakres gniazda nasłuchiwania, umożliwiając nieograniczony dostęp z publicznych i prywatnych użytkowników, jeśli jest to konieczne, lub ograniczanie dostępu tylko do tej samej lokacji, zgodnie z wymaganiami.</span><span class="sxs-lookup"><span data-stu-id="b0a3c-137">This option widens or narrows the scope of a listening socket, enabling unrestricted access from public and private users when appropriate, or restricting access only to the same site, as required.</span></span>  
  
 <span data-ttu-id="b0a3c-138">To `ipProtectionLevel` ustawienie atrybutu ma wpływ tylko na początkowy ruch przychodzący:</span><span class="sxs-lookup"><span data-stu-id="b0a3c-138">This `ipProtectionLevel` attribute setting affects only initial incoming traffic:</span></span>  
  
- <span data-ttu-id="b0a3c-139">Serwer TCP nasłuchuje połączeń przychodzących w gnieździe.</span><span class="sxs-lookup"><span data-stu-id="b0a3c-139">A TCP server listening for incoming connections on a socket.</span></span>  
  
- <span data-ttu-id="b0a3c-140">Aplikacja UDP otrzymująca pakiet w gnieździe.</span><span class="sxs-lookup"><span data-stu-id="b0a3c-140">A UDP application receiving a packet on a socket.</span></span>  
  
 <span data-ttu-id="b0a3c-141">To ustawienie konfiguracji nie ma wpływu na już ustanowione połączenia TCP (ruch nie jest ograniczony w obu kierunkach) i nie ma wpływu na aplikację wysyłającą pakiety UDP.</span><span class="sxs-lookup"><span data-stu-id="b0a3c-141">This configuration setting does not affect already established TCP connections (traffic is unrestricted in both directions) and does not affect an application sending UDP packets.</span></span>  
  
 <span data-ttu-id="b0a3c-142">Możliwe wartości `ipProtectionLevel` ustawienia atrybutu odpowiadają zdefiniowanym poziomom ochrony określonym <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> w wyliczeniu w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="b0a3c-142">The possible values for the `ipProtectionLevel` attribute setting correspond with the defined protection levels specified in the <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> enumeration as follows:</span></span>  
  
|<span data-ttu-id="b0a3c-143">**Wartość atrybutu**</span><span class="sxs-lookup"><span data-stu-id="b0a3c-143">**Attribute Value**</span></span>|<span data-ttu-id="b0a3c-144">**Opis**</span><span class="sxs-lookup"><span data-stu-id="b0a3c-144">**Description**</span></span>|  
|-|-|  
|<span data-ttu-id="b0a3c-145">EdgeRestricted</span><span class="sxs-lookup"><span data-stu-id="b0a3c-145">EdgeRestricted</span></span>|<span data-ttu-id="b0a3c-146">Poziom ochrony adresów IP jest ograniczony do krawędzi.</span><span class="sxs-lookup"><span data-stu-id="b0a3c-146">The IP protection level is edge restricted.</span></span> <span data-ttu-id="b0a3c-147">Ta wartość będzie używana przez aplikacje przeznaczone do działania przez Internet.</span><span class="sxs-lookup"><span data-stu-id="b0a3c-147">This value would be used by applications designed to operate across the Internet.</span></span> <span data-ttu-id="b0a3c-148">To ustawienie nie zezwala na przechodzenie translacji adresów sieciowych (NAT) przy użyciu implementacji Teredo systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="b0a3c-148">This setting does not allow Network Address Translation (NAT) traversal using the Windows Teredo implementation.</span></span> <span data-ttu-id="b0a3c-149">Aplikacje te mogą pomijać zapory IPv4, więc aplikacje muszą być wzmocnione przed atakami z Internetu kierowanymi na otwarty port.</span><span class="sxs-lookup"><span data-stu-id="b0a3c-149">These applications may bypass IPv4 firewalls, so applications must be hardened against Internet attacks directed at the opened port.</span></span> <span data-ttu-id="b0a3c-150">W systemach Windows Server 2003 i Windows XP wartość domyślna dla poziomu ochrony IP w gnieździe jest ograniczona do krawędzi.</span><span class="sxs-lookup"><span data-stu-id="b0a3c-150">On Windows Server 2003 and Windows XP, the default value for the IP Protection level on a socket is edge restricted.</span></span>|  
|<span data-ttu-id="b0a3c-151">Podlega</span><span class="sxs-lookup"><span data-stu-id="b0a3c-151">Restricted</span></span>|<span data-ttu-id="b0a3c-152">Poziom ochrony adresów IP jest ograniczony.</span><span class="sxs-lookup"><span data-stu-id="b0a3c-152">The IP protection level is restricted.</span></span> <span data-ttu-id="b0a3c-153">Ta wartość będzie używana przez aplikacje intranetowe, które nie implementują scenariuszy internetowych.</span><span class="sxs-lookup"><span data-stu-id="b0a3c-153">This value would be used by intranet applications that do not implement Internet scenarios.</span></span> <span data-ttu-id="b0a3c-154">Te aplikacje zazwyczaj nie są przetestowane ani nie są zaostrzone przed atakami w stylu Internetu.</span><span class="sxs-lookup"><span data-stu-id="b0a3c-154">These applications are generally not tested or hardened against Internet-style attacks.</span></span> <span data-ttu-id="b0a3c-155">To ustawienie ograniczy odbieranie ruchu tylko do połączenia lokalnego.</span><span class="sxs-lookup"><span data-stu-id="b0a3c-155">This setting will limit the received traffic to link-local only.</span></span>|  
|<span data-ttu-id="b0a3c-156">Nieograniczone</span><span class="sxs-lookup"><span data-stu-id="b0a3c-156">Unrestricted</span></span>|<span data-ttu-id="b0a3c-157">Poziom ochrony adresów IP nie jest ograniczony.</span><span class="sxs-lookup"><span data-stu-id="b0a3c-157">The IP protection level is unrestricted.</span></span> <span data-ttu-id="b0a3c-158">Ta wartość będzie używana przez aplikacje przeznaczone do działania przez Internet, w tym aplikacje korzystające z możliwości przechodzenia do translatora adresów sieciowych IPv6 wbudowanych w system Windows (na przykład Teredo).</span><span class="sxs-lookup"><span data-stu-id="b0a3c-158">This value would be used by applications designed to operate across the Internet, including applications taking advantage of IPv6 NAT traversal capabilities built into Windows (Teredo, for example).</span></span> <span data-ttu-id="b0a3c-159">Aplikacje te mogą pomijać zapory IPv4, więc aplikacje muszą być wzmocnione przed atakami z Internetu kierowanymi na otwarty port.</span><span class="sxs-lookup"><span data-stu-id="b0a3c-159">These applications may bypass IPv4 firewalls, so applications must be hardened against Internet attacks directed at the opened port.</span></span> <span data-ttu-id="b0a3c-160">W systemach Windows Server 2008 R2 i Windows Vista wartość domyślna dla poziomu ochrony adresów IP w gnieździe jest nieograniczona.</span><span class="sxs-lookup"><span data-stu-id="b0a3c-160">On Windows Server 2008 R2 and Windows Vista, the default value for the IP Protection level on a socket is unrestricted.</span></span>|  
|<span data-ttu-id="b0a3c-161">Nieokreślony</span><span class="sxs-lookup"><span data-stu-id="b0a3c-161">Unspecified</span></span>|<span data-ttu-id="b0a3c-162">Nie określono poziomu ochrony adresów IP.</span><span class="sxs-lookup"><span data-stu-id="b0a3c-162">The IP protection level is unspecified.</span></span> <span data-ttu-id="b0a3c-163">W systemach Windows 7 i Windows Server 2008 R2 nie określono wartości domyślnej dla poziomu ochrony adresów IP w gnieździe.</span><span class="sxs-lookup"><span data-stu-id="b0a3c-163">On Windows 7 and Windows Server 2008 R2, the default value for the IP Protection level on a socket is unspecified.</span></span>|  
  
 <span data-ttu-id="b0a3c-164">Wartość domyślna dla `ipProtectionLevel` atrybutu jest nieokreślona.</span><span class="sxs-lookup"><span data-stu-id="b0a3c-164">The default value for the `ipProtectionLevel` attribute is **Unspecified**.</span></span>  
  
 <span data-ttu-id="b0a3c-165">Właściwość może służyć do uzyskiwania bieżącej wartości `ipProtectionLevel` atrybutu z odpowiednich plików konfiguracji. <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A></span><span class="sxs-lookup"><span data-stu-id="b0a3c-165">The <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> property can be used to get the current value of the `ipProtectionLevel` attribute from applicable configuration files.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="b0a3c-166">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="b0a3c-166">Configuration Files</span></span>  
 <span data-ttu-id="b0a3c-167">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="b0a3c-167">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0a3c-168">Przykład</span><span class="sxs-lookup"><span data-stu-id="b0a3c-168">Example</span></span>  
 <span data-ttu-id="b0a3c-169">Poniższy przykład pokazuje, jak określić, że powinny być używane porty zakończenia oraz że wartość domyślna <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> powinna być bez ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="b0a3c-169">The following example shows how to specify that completion ports should be used and that the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> should be unrestricted.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b0a3c-170">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b0a3c-170">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SocketElement?displayProperty=nameWithType>
- <xref:System.Net.Sockets?displayProperty=nameWithType>
- <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SocketOptionName.IPProtectionLevel?displayProperty=nameWithType>
- [<span data-ttu-id="b0a3c-171">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="b0a3c-171">Network Settings Schema</span></span>](index.md)
