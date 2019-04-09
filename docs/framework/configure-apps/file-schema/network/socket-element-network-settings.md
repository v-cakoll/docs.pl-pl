---
title: <socket> Element (ustawienia sieci)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/socket
- http://schemas.microsoft.com/.NetConfiguration/v2.0#socket
helpviewer_keywords:
- <socket> element
- socket element
ms.assetid: 366c634c-7d16-478f-aedf-053eda94a1a0
ms.openlocfilehash: 82bfe3b6e3107ff787716657dbf0b31dcadde911
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59160163"
---
# <a name="socket-element-network-settings"></a><span data-ttu-id="bba3b-102">\<gniazda >, Element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="bba3b-102">\<socket> Element (Network Settings)</span></span>
<span data-ttu-id="bba3b-103">Określa, czy operacje gniazda używają portów.</span><span class="sxs-lookup"><span data-stu-id="bba3b-103">Specifies whether socket operations use completion ports.</span></span>  
  
 <span data-ttu-id="bba3b-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="bba3b-104">\<configuration></span></span>  
<span data-ttu-id="bba3b-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="bba3b-105">\<system.net></span></span>  
<span data-ttu-id="bba3b-106">\<settings></span><span class="sxs-lookup"><span data-stu-id="bba3b-106">\<settings></span></span>  
<span data-ttu-id="bba3b-107">\<socket></span><span class="sxs-lookup"><span data-stu-id="bba3b-107">\<socket></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bba3b-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="bba3b-108">Syntax</span></span>  
  
```xml  
<socket  
  alwaysUseCompletionPortsForConnect="true|false"  
  alwaysUseCompletionPortsForAccept="true|false"  
  ipProtectionLevel="EdgeRestricted|Restricted|Unrestricted|Unspecified"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bba3b-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="bba3b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="bba3b-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="bba3b-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bba3b-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="bba3b-111">Attributes</span></span>  
  
|**<span data-ttu-id="bba3b-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="bba3b-112">Attribute</span></span>**|**<span data-ttu-id="bba3b-113">Opis</span><span class="sxs-lookup"><span data-stu-id="bba3b-113">Description</span></span>**|  
|-------------------|---------------------|  
|`alwaysUseCompletionPortsForAccept`|<span data-ttu-id="bba3b-114">Wskazuje, czy gniazda zawsze należy używać portów dla wywołań metod Accept.</span><span class="sxs-lookup"><span data-stu-id="bba3b-114">Indicates whether the socket should always use completion ports for Accept method calls.</span></span> <span data-ttu-id="bba3b-115">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="bba3b-115">The default value is `false`.</span></span>|  
|`alwaysUseCompletionPortsForConnect`|<span data-ttu-id="bba3b-116">Wskazuje, czy gniazda zawsze należy używać portów dla wywołania metody Connect.</span><span class="sxs-lookup"><span data-stu-id="bba3b-116">Indicates whether the socket should always use completion ports for Connect method calls.</span></span> <span data-ttu-id="bba3b-117">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="bba3b-117">The default value is `false`.</span></span>|  
|`ipProtectionLevel`|<span data-ttu-id="bba3b-118">Określa domyślny <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> do użycia dla gniazda.</span><span class="sxs-lookup"><span data-stu-id="bba3b-118">Specifies the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> to use for a socket.</span></span> <span data-ttu-id="bba3b-119">Wartość domyślna zależy od wersji systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="bba3b-119">The default value depends on the version of Windows.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bba3b-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="bba3b-120">Child Elements</span></span>  
 <span data-ttu-id="bba3b-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="bba3b-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bba3b-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="bba3b-122">Parent Elements</span></span>  
  
|**<span data-ttu-id="bba3b-123">Element</span><span class="sxs-lookup"><span data-stu-id="bba3b-123">Element</span></span>**|**<span data-ttu-id="bba3b-124">Opis</span><span class="sxs-lookup"><span data-stu-id="bba3b-124">Description</span></span>**|  
|-----------------|---------------------|  
|[<span data-ttu-id="bba3b-125">ustawienia</span><span class="sxs-lookup"><span data-stu-id="bba3b-125">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="bba3b-126">Konfiguruje opcje sieciowe podstawowe dla <xref:System.Net> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="bba3b-126">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bba3b-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bba3b-127">Remarks</span></span>  
 <span data-ttu-id="bba3b-128">`alwaysUseCompletionPortsForAccept` i `alwaysUseCompletionPortsForConnect` atrybuty są używane do określania domyślne zachowanie dotyczące używania portów przez klasy w <xref:System.Net.Sockets?displayProperty=nameWithType>.namespace.</span><span class="sxs-lookup"><span data-stu-id="bba3b-128">The `alwaysUseCompletionPortsForAccept` and `alwaysUseCompletionPortsForConnect` attributes are used to specify the default behavior regarding the use of completion ports by the classes in the <xref:System.Net.Sockets?displayProperty=nameWithType>.namespace.</span></span> <span data-ttu-id="bba3b-129">Porty zakończenia są zalecane w przypadku aplikacji serwera o wysokiej wydajności.</span><span class="sxs-lookup"><span data-stu-id="bba3b-129">Completion ports are recommended for high performance server applications.</span></span>  
  
 <span data-ttu-id="bba3b-130">Wartością domyślną dla `alwaysUseCompletionPortsForAccept` i `alwaysUseCompletionPortsForConnect` atrybutów jest **false**.</span><span class="sxs-lookup"><span data-stu-id="bba3b-130">The default value for the `alwaysUseCompletionPortsForAccept` and `alwaysUseCompletionPortsForConnect` attributes is **false**.</span></span>  
  
 <span data-ttu-id="bba3b-131"><xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A> Może służyć do uzyskania bieżącej wartości `alwaysUseCompletionPortsForAccept` atrybut z właściwych plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="bba3b-131">The <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A> can be used to get the current value of the `alwaysUseCompletionPortsForAccept` attribute from applicable configuration files.</span></span> <span data-ttu-id="bba3b-132"><xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A> Może służyć do uzyskania bieżącej wartości `alwaysUseCompletionPortsForConnect` atrybut z właściwych plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="bba3b-132">The <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A> can be used to get the current value of the `alwaysUseCompletionPortsForConnect` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="bba3b-133">`ipProtectionLevel` Atrybut określa domyślny <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> do użycia dla gniazda.</span><span class="sxs-lookup"><span data-stu-id="bba3b-133">The `ipProtectionLevel` attribute specifies the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> to use for a socket.</span></span> <span data-ttu-id="bba3b-134"><xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> Właściwość umożliwia skonfigurowanie ograniczeń dla gniazda IPv6 do określonego zakresu, takie jak adresy z takimi samymi link lokalny lub lokacji lokalnej prefiks.</span><span class="sxs-lookup"><span data-stu-id="bba3b-134">The <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> property enables configuration of a restriction for an IPv6 socket to a specified scope, such as addresses with the same link local or site local prefix.</span></span> <span data-ttu-id="bba3b-135">Ta opcja umożliwia aplikacjom do ograniczenia dostępu do gniazda IPv6.</span><span class="sxs-lookup"><span data-stu-id="bba3b-135">This option enables applications to place access restrictions on IPv6 sockets.</span></span> <span data-ttu-id="bba3b-136">Takie ograniczenia, Włącz aplikacji uruchomionej w prywatnej sieci lokalnej po prostu i niezawodnie zabezpieczyć się przed atakami zewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="bba3b-136">Such restrictions enable an application running on a private LAN to simply and robustly harden itself against external attacks.</span></span> <span data-ttu-id="bba3b-137">Ta opcja rozszerza się lub umożliwia zawężenie zakresu nasłuchiwania gniazda, dzięki czemu nieograniczonego dostępu z publicznych i prywatnych użytkowników, gdy jest to konieczne, lub ograniczać dostęp tylko do tej samej lokacji, zgodnie z wymaganiami.</span><span class="sxs-lookup"><span data-stu-id="bba3b-137">This option widens or narrows the scope of a listening socket, enabling unrestricted access from public and private users when appropriate, or restricting access only to the same site, as required.</span></span>  
  
 <span data-ttu-id="bba3b-138">To `ipProtectionLevel` ustawienie atrybutu ma wpływ tylko na początkowy ruch przychodzący:</span><span class="sxs-lookup"><span data-stu-id="bba3b-138">This `ipProtectionLevel` attribute setting affects only initial incoming traffic:</span></span>  
  
-   <span data-ttu-id="bba3b-139">Serwer protokołu TCP nasłuchuje połączeń przychodzących na gniazdo.</span><span class="sxs-lookup"><span data-stu-id="bba3b-139">A TCP server listening for incoming connections on a socket.</span></span>  
  
-   <span data-ttu-id="bba3b-140">Aplikacja UDP, odbierania pakietów dla gniazda.</span><span class="sxs-lookup"><span data-stu-id="bba3b-140">A UDP application receiving a packet on a socket.</span></span>  
  
 <span data-ttu-id="bba3b-141">To ustawienie konfiguracji nie wpływa na nawiązano już połączenie połączenia protokołu TCP (ruch jest nieograniczony w obu kierunkach) i nie ma wpływu na aplikację, wysyłanie pakietów UDP.</span><span class="sxs-lookup"><span data-stu-id="bba3b-141">This configuration setting does not affect already established TCP connections (traffic is unrestricted in both directions) and does not affect an application sending UDP packets.</span></span>  
  
 <span data-ttu-id="bba3b-142">Możliwe wartości parametru `ipProtectionLevel` ustawienie atrybutu odnoszą się do poziomu ochrony zdefiniowanych określonych w <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> wyliczenia w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="bba3b-142">The possible values for the `ipProtectionLevel` attribute setting correspond with the defined protection levels specified in the <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> enumeration as follows:</span></span>  
  
|**<span data-ttu-id="bba3b-143">Wartość atrybutu</span><span class="sxs-lookup"><span data-stu-id="bba3b-143">Attribute Value</span></span>**|**<span data-ttu-id="bba3b-144">Opis</span><span class="sxs-lookup"><span data-stu-id="bba3b-144">Description</span></span>**|  
|-|-|  
|<span data-ttu-id="bba3b-145">EdgeRestricted</span><span class="sxs-lookup"><span data-stu-id="bba3b-145">EdgeRestricted</span></span>|<span data-ttu-id="bba3b-146">Poziom ochrony IP jest edge z ograniczeniami.</span><span class="sxs-lookup"><span data-stu-id="bba3b-146">The IP protection level is edge restricted.</span></span> <span data-ttu-id="bba3b-147">Ta wartość będzie używana przez aplikacje zaprojektowane do działania w Internecie.</span><span class="sxs-lookup"><span data-stu-id="bba3b-147">This value would be used by applications designed to operate across the Internet.</span></span> <span data-ttu-id="bba3b-148">To ustawienie umożliwia przechodzenie translacji adresów sieciowych (NAT) przy użyciu implementacji Windows Teredo.</span><span class="sxs-lookup"><span data-stu-id="bba3b-148">This setting does not allow Network Address Translation (NAT) traversal using the Windows Teredo implementation.</span></span> <span data-ttu-id="bba3b-149">Te aplikacje mogą pominąć IPv4 zapory, dzięki czemu aplikacje muszą być wzmocnione zabezpieczenia przed atakami internetowymi, skierowanych do otwartego portu.</span><span class="sxs-lookup"><span data-stu-id="bba3b-149">These applications may bypass IPv4 firewalls, so applications must be hardened against Internet attacks directed at the opened port.</span></span> <span data-ttu-id="bba3b-150">W systemie Windows Server 2003 i Windows XP wartością domyślną dla poziomu ochrony IP na gniazdo jest edge z ograniczeniami.</span><span class="sxs-lookup"><span data-stu-id="bba3b-150">On Windows Server 2003 and Windows XP, the default value for the IP Protection level on a socket is edge restricted.</span></span>|  
|<span data-ttu-id="bba3b-151">z ograniczeniami</span><span class="sxs-lookup"><span data-stu-id="bba3b-151">Restricted</span></span>|<span data-ttu-id="bba3b-152">Poziom ochrony IP jest ograniczona.</span><span class="sxs-lookup"><span data-stu-id="bba3b-152">The IP protection level is restricted.</span></span> <span data-ttu-id="bba3b-153">Ta wartość będzie używana przez aplikacji intranetowych, które nie implementują scenariuszy Internetu.</span><span class="sxs-lookup"><span data-stu-id="bba3b-153">This value would be used by intranet applications that do not implement Internet scenarios.</span></span> <span data-ttu-id="bba3b-154">Te aplikacje zwykle nie są przetestowane lub wzmocnione zabezpieczenia przed atakami internetową.</span><span class="sxs-lookup"><span data-stu-id="bba3b-154">These applications are generally not tested or hardened against Internet-style attacks.</span></span> <span data-ttu-id="bba3b-155">To ustawienie powoduje ograniczenie odebrany ruch link-local.</span><span class="sxs-lookup"><span data-stu-id="bba3b-155">This setting will limit the received traffic to link-local only.</span></span>|  
|<span data-ttu-id="bba3b-156">Bez ograniczeń</span><span class="sxs-lookup"><span data-stu-id="bba3b-156">Unrestricted</span></span>|<span data-ttu-id="bba3b-157">Poziom ochrony IP jest nieograniczony.</span><span class="sxs-lookup"><span data-stu-id="bba3b-157">The IP protection level is unrestricted.</span></span> <span data-ttu-id="bba3b-158">Ta wartość będzie używana przez aplikacje przeznaczone do pracy w Internecie, łącznie z aplikacjami, wykorzystując możliwości Przechodzenie translatora adresów Sieciowych IPv6 do Windows (na przykład Teredo).</span><span class="sxs-lookup"><span data-stu-id="bba3b-158">This value would be used by applications designed to operate across the Internet, including applications taking advantage of IPv6 NAT traversal capabilities built into Windows (Teredo, for example).</span></span> <span data-ttu-id="bba3b-159">Te aplikacje mogą pominąć IPv4 zapory, dzięki czemu aplikacje muszą być wzmocnione zabezpieczenia przed atakami internetowymi, skierowanych do otwartego portu.</span><span class="sxs-lookup"><span data-stu-id="bba3b-159">These applications may bypass IPv4 firewalls, so applications must be hardened against Internet attacks directed at the opened port.</span></span> <span data-ttu-id="bba3b-160">W systemie Windows Server 2008 R2 i Windows Vista wartością domyślną dla poziomu ochrony IP na gniazdo jest nieograniczony.</span><span class="sxs-lookup"><span data-stu-id="bba3b-160">On Windows Server 2008 R2 and Windows Vista, the default value for the IP Protection level on a socket is unrestricted.</span></span>|  
|<span data-ttu-id="bba3b-161">Nie określono tego parametru</span><span class="sxs-lookup"><span data-stu-id="bba3b-161">Unspecified</span></span>|<span data-ttu-id="bba3b-162">Poziom ochrony IP jest nieokreślony.</span><span class="sxs-lookup"><span data-stu-id="bba3b-162">The IP protection level is unspecified.</span></span> <span data-ttu-id="bba3b-163">Windows 7 i Windows Server 2008 R2 wartością domyślną dla poziomu ochrony IP na gniazdo jest nieokreślona.</span><span class="sxs-lookup"><span data-stu-id="bba3b-163">On Windows 7 and Windows Server 2008 R2, the default value for the IP Protection level on a socket is unspecified.</span></span>|  
  
 <span data-ttu-id="bba3b-164">Wartością domyślną dla `ipProtectionLevel` atrybut jest **nieokreślony**.</span><span class="sxs-lookup"><span data-stu-id="bba3b-164">The default value for the `ipProtectionLevel` attribute is **Unspecified**.</span></span>  
  
 <span data-ttu-id="bba3b-165"><xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> Właściwość może służyć do uzyskania bieżącej wartości `ipProtectionLevel` atrybut z właściwych plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="bba3b-165">The <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> property can be used to get the current value of the `ipProtectionLevel` attribute from applicable configuration files.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="bba3b-166">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="bba3b-166">Configuration Files</span></span>  
 <span data-ttu-id="bba3b-167">Ten element może być użyty w pliku konfiguracji aplikacji lub w pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="bba3b-167">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bba3b-168">Przykład</span><span class="sxs-lookup"><span data-stu-id="bba3b-168">Example</span></span>  
 <span data-ttu-id="bba3b-169">W poniższym przykładzie pokazano, jak określić, że porty zakończenia powinien być używany i czy domyślnie <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> powinny być bez ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="bba3b-169">The following example shows how to specify that completion ports should be used and that the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> should be unrestricted.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bba3b-170">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bba3b-170">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SocketElement?displayProperty=nameWithType>
- <xref:System.Net.Sockets?displayProperty=nameWithType>
- <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SocketOptionName.IPProtectionLevel?displayProperty=nameWithType>
- [<span data-ttu-id="bba3b-171">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="bba3b-171">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
