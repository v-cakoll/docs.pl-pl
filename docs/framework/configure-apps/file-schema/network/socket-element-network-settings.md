---
title: '&lt;gniazda&gt; elementu (ustawienia sieciowe)'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/socket
- http://schemas.microsoft.com/.NetConfiguration/v2.0#socket
helpviewer_keywords:
- <socket> element
- socket element
ms.assetid: 366c634c-7d16-478f-aedf-053eda94a1a0
caps.latest.revision: "21"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 3d1adc163e889a0de6ad27347c8f122ac26d3524
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltsocketgt-element-network-settings"></a><span data-ttu-id="c8b95-102">&lt;gniazda&gt; elementu (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="c8b95-102">&lt;socket&gt; Element (Network Settings)</span></span>
<span data-ttu-id="c8b95-103">Określa, czy operacje gniazda używać portów.</span><span class="sxs-lookup"><span data-stu-id="c8b95-103">Specifies whether socket operations use completion ports.</span></span>  
  
 <span data-ttu-id="c8b95-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="c8b95-104">\<configuration></span></span>  
<span data-ttu-id="c8b95-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="c8b95-105">\<system.net></span></span>  
<span data-ttu-id="c8b95-106">\<Ustawienia ></span><span class="sxs-lookup"><span data-stu-id="c8b95-106">\<settings></span></span>  
<span data-ttu-id="c8b95-107">\<gniazda ></span><span class="sxs-lookup"><span data-stu-id="c8b95-107">\<socket></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8b95-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="c8b95-108">Syntax</span></span>  
  
```xml  
<socket  
  alwaysUseCompletionPortsForConnect="true|false"  
  alwaysUseCompletionPortsForAccept="true|false"  
  ipProtectionLevel="EdgeRestricted|Restricted|Unrestricted|Unspecified"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c8b95-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c8b95-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c8b95-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c8b95-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c8b95-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c8b95-111">Attributes</span></span>  
  
|<span data-ttu-id="c8b95-112">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="c8b95-112">**Attribute**</span></span>|<span data-ttu-id="c8b95-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="c8b95-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`alwaysUseCompletionPortsForAccept`|<span data-ttu-id="c8b95-114">Wskazuje, czy gniazda zawsze należy używać portów dla wywołań metod Accept.</span><span class="sxs-lookup"><span data-stu-id="c8b95-114">Indicates whether the socket should always use completion ports for Accept method calls.</span></span> <span data-ttu-id="c8b95-115">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="c8b95-115">The default value is `false`.</span></span>|  
|`alwaysUseCompletionPortsForConnect`|<span data-ttu-id="c8b95-116">Wskazuje, czy gniazda zawsze należy używać portów dla wywołania metody Connect.</span><span class="sxs-lookup"><span data-stu-id="c8b95-116">Indicates whether the socket should always use completion ports for Connect method calls.</span></span> <span data-ttu-id="c8b95-117">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="c8b95-117">The default value is `false`.</span></span>|  
|`ipProtectionLevel`|<span data-ttu-id="c8b95-118">Określa domyślny <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> dla gniazda.</span><span class="sxs-lookup"><span data-stu-id="c8b95-118">Specifies the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> to use for a socket.</span></span> <span data-ttu-id="c8b95-119">Wartość domyślna zależy od wersji systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="c8b95-119">The default value depends on the version of Windows.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c8b95-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c8b95-120">Child Elements</span></span>  
 <span data-ttu-id="c8b95-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="c8b95-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c8b95-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c8b95-122">Parent Elements</span></span>  
  
|<span data-ttu-id="c8b95-123">**Element**</span><span class="sxs-lookup"><span data-stu-id="c8b95-123">**Element**</span></span>|<span data-ttu-id="c8b95-124">**Opis**</span><span class="sxs-lookup"><span data-stu-id="c8b95-124">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="c8b95-125">Ustawienia</span><span class="sxs-lookup"><span data-stu-id="c8b95-125">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="c8b95-126">Służy do konfigurowania opcji sieci podstawowej dla <xref:System.Net> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="c8b95-126">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c8b95-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c8b95-127">Remarks</span></span>  
 <span data-ttu-id="c8b95-128">`alwaysUseCompletionPortsForAccept` i `alwaysUseCompletionPortsForConnect` atrybuty służą do określania domyślnego zachowania dotyczące wykorzystania portów przez klasy w <xref:System.Net.Sockets?displayProperty=nameWithType>.namespace.</span><span class="sxs-lookup"><span data-stu-id="c8b95-128">The `alwaysUseCompletionPortsForAccept` and `alwaysUseCompletionPortsForConnect` attributes are used to specify the default behavior regarding the use of completion ports by the classes in the <xref:System.Net.Sockets?displayProperty=nameWithType>.namespace.</span></span> <span data-ttu-id="c8b95-129">Porty zakończenia są zalecane dla aplikacji serwera wysokiej wydajności.</span><span class="sxs-lookup"><span data-stu-id="c8b95-129">Completion ports are recommended for high performance server applications.</span></span>  
  
 <span data-ttu-id="c8b95-130">Wartość domyślna dla `alwaysUseCompletionPortsForAccept` i `alwaysUseCompletionPortsForConnect` atrybutów jest **false**.</span><span class="sxs-lookup"><span data-stu-id="c8b95-130">The default value for the `alwaysUseCompletionPortsForAccept` and `alwaysUseCompletionPortsForConnect` attributes is **false**.</span></span>  
  
 <span data-ttu-id="c8b95-131"><xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A> Można pobrać wartości bieżącego `alwaysUseCompletionPortsForAccept` atrybutu z plików zastosowania konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c8b95-131">The <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A> can be used to get the current value of the `alwaysUseCompletionPortsForAccept` attribute from applicable configuration files.</span></span> <span data-ttu-id="c8b95-132"><xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A> Można pobrać wartości bieżącego `alwaysUseCompletionPortsForConnect` atrybutu z plików zastosowania konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c8b95-132">The <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A> can be used to get the current value of the `alwaysUseCompletionPortsForConnect` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="c8b95-133">`ipProtectionLevel` Atrybut określa domyślny <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> dla gniazda.</span><span class="sxs-lookup"><span data-stu-id="c8b95-133">The `ipProtectionLevel` attribute specifies the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> to use for a socket.</span></span> <span data-ttu-id="c8b95-134"><xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> Właściwości umożliwia konfigurację ograniczeń dla gniazda IPv6 do określonego zakresu, takie jak adresy o tej samej link lokalnego lub lokacji lokalnej prefiks.</span><span class="sxs-lookup"><span data-stu-id="c8b95-134">The <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> property enables configuration of a restriction for an IPv6 socket to a specified scope, such as addresses with the same link local or site local prefix.</span></span> <span data-ttu-id="c8b95-135">Ta opcja umożliwia aplikacjom ograniczają dostęp do protokołu IPv6 sockets.</span><span class="sxs-lookup"><span data-stu-id="c8b95-135">This option enables applications to place access restrictions on IPv6 sockets.</span></span> <span data-ttu-id="c8b95-136">Takie ograniczenia Włącz aplikacji uruchomionej w prywatnej sieci LAN po prostu i niezawodnie zabezpieczyć się przed atakami zewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="c8b95-136">Such restrictions enable an application running on a private LAN to simply and robustly harden itself against external attacks.</span></span> <span data-ttu-id="c8b95-137">Ta opcja rozszerzenie lub znajduje się w zakresie zakres nasłuchiwania gniazda, włączanie nieograniczony dostęp z publicznych i prywatnych użytkowników, gdy jest to konieczne, lub ograniczać dostęp tylko do tej samej lokacji, zgodnie z wymaganiami.</span><span class="sxs-lookup"><span data-stu-id="c8b95-137">This option widens or narrows the scope of a listening socket, enabling unrestricted access from public and private users when appropriate, or restricting access only to the same site, as required.</span></span>  
  
 <span data-ttu-id="c8b95-138">To `ipProtectionLevel` atrybutu ustawienie ma wpływ tylko na początkowy ruch przychodzący:</span><span class="sxs-lookup"><span data-stu-id="c8b95-138">This `ipProtectionLevel` attribute setting affects only initial incoming traffic:</span></span>  
  
-   <span data-ttu-id="c8b95-139">Serwer protokołu TCP nasłuchuje przychodzących połączeń dla gniazda.</span><span class="sxs-lookup"><span data-stu-id="c8b95-139">A TCP server listening for incoming connections on a socket.</span></span>  
  
-   <span data-ttu-id="c8b95-140">Aplikacja UDP, odbierania pakietów dla gniazda.</span><span class="sxs-lookup"><span data-stu-id="c8b95-140">A UDP application receiving a packet on a socket.</span></span>  
  
 <span data-ttu-id="c8b95-141">To ustawienie konfiguracji nie ma wpływu na już istniejących połączeń TCP (ruch nieograniczony w obu kierunkach) i nie wpływa na aplikację wysyłania pakietów UDP.</span><span class="sxs-lookup"><span data-stu-id="c8b95-141">This configuration setting does not affect already established TCP connections (traffic is unrestricted in both directions) and does not affect an application sending UDP packets.</span></span>  
  
 <span data-ttu-id="c8b95-142">Możliwe wartości `ipProtectionLevel` ustawienie atrybutu odpowiadają poziomów ochrony zdefiniowanych określone w <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> wyliczenia w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="c8b95-142">The possible values for the `ipProtectionLevel` attribute setting correspond with the defined protection levels specified in the <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> enumeration as follows:</span></span>  
  
|<span data-ttu-id="c8b95-143">**Wartość atrybutu**</span><span class="sxs-lookup"><span data-stu-id="c8b95-143">**Attribute Value**</span></span>|<span data-ttu-id="c8b95-144">**Opis**</span><span class="sxs-lookup"><span data-stu-id="c8b95-144">**Description**</span></span>|  
|-|-|  
|<span data-ttu-id="c8b95-145">EdgeRestricted</span><span class="sxs-lookup"><span data-stu-id="c8b95-145">EdgeRestricted</span></span>|<span data-ttu-id="c8b95-146">Poziom ochrony IP jest ograniczone krawędzi.</span><span class="sxs-lookup"><span data-stu-id="c8b95-146">The IP protection level is edge restricted.</span></span> <span data-ttu-id="c8b95-147">Ta wartość może być używane przez aplikacje, przeznaczonych do pracy w Internecie.</span><span class="sxs-lookup"><span data-stu-id="c8b95-147">This value would be used by applications designed to operate across the Internet.</span></span> <span data-ttu-id="c8b95-148">To ustawienie umożliwia przechodzenie translacji adresów sieciowych (NAT) przy użyciu implementacji protokołu Teredo systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="c8b95-148">This setting does not allow Network Address Translation (NAT) traversal using the Windows Teredo implementation.</span></span> <span data-ttu-id="c8b95-149">Te aplikacje mogą obejścia zapory IPv4, więc aplikacji musi być wzmocnione zabezpieczenia przed atakami Internet skierowane do otwartego portu.</span><span class="sxs-lookup"><span data-stu-id="c8b95-149">These applications may bypass IPv4 firewalls, so applications must be hardened against Internet attacks directed at the opened port.</span></span> <span data-ttu-id="c8b95-150">W systemie Windows Server 2003 i Windows XP wartością domyślną dla poziomu ochrony IP na gnieździe jest ograniczone krawędzi.</span><span class="sxs-lookup"><span data-stu-id="c8b95-150">On Windows Server 2003 and Windows XP, the default value for the IP Protection level on a socket is edge restricted.</span></span>|  
|<span data-ttu-id="c8b95-151">Ograniczone</span><span class="sxs-lookup"><span data-stu-id="c8b95-151">Restricted</span></span>|<span data-ttu-id="c8b95-152">Poziom ochrony IP jest ograniczone.</span><span class="sxs-lookup"><span data-stu-id="c8b95-152">The IP protection level is restricted.</span></span> <span data-ttu-id="c8b95-153">Ta wartość będzie używana przez aplikacji intranetowych, które nie implementują scenariuszy Internetu.</span><span class="sxs-lookup"><span data-stu-id="c8b95-153">This value would be used by intranet applications that do not implement Internet scenarios.</span></span> <span data-ttu-id="c8b95-154">Te aplikacje są zazwyczaj nie badane lub wzmocnione zabezpieczenia przed atakami stylu Internet.</span><span class="sxs-lookup"><span data-stu-id="c8b95-154">These applications are generally not tested or hardened against Internet-style attacks.</span></span> <span data-ttu-id="c8b95-155">To ustawienie powoduje ograniczenie odebrany ruch do link-local.</span><span class="sxs-lookup"><span data-stu-id="c8b95-155">This setting will limit the received traffic to link-local only.</span></span>|  
|<span data-ttu-id="c8b95-156">Bez ograniczeń</span><span class="sxs-lookup"><span data-stu-id="c8b95-156">Unrestricted</span></span>|<span data-ttu-id="c8b95-157">Poziom ochrony IP jest nieograniczony.</span><span class="sxs-lookup"><span data-stu-id="c8b95-157">The IP protection level is unrestricted.</span></span> <span data-ttu-id="c8b95-158">Ta wartość będzie służyć przez aplikacje przeznaczone do pracy w Internecie, w tym aplikacje wykorzystać możliwości przechodzenie IPv6 translatora adresów Sieciowych w systemie Windows (na przykład Teredo).</span><span class="sxs-lookup"><span data-stu-id="c8b95-158">This value would be used by applications designed to operate across the Internet, including applications taking advantage of IPv6 NAT traversal capabilities built into Windows (Teredo, for example).</span></span> <span data-ttu-id="c8b95-159">Te aplikacje mogą obejścia zapory IPv4, więc aplikacji musi być wzmocnione zabezpieczenia przed atakami Internet skierowane do otwartego portu.</span><span class="sxs-lookup"><span data-stu-id="c8b95-159">These applications may bypass IPv4 firewalls, so applications must be hardened against Internet attacks directed at the opened port.</span></span> <span data-ttu-id="c8b95-160">W systemie Windows Server 2008 R2 i Windows Vista wartością domyślną dla poziomu ochrony IP na gnieździe jest nieograniczony.</span><span class="sxs-lookup"><span data-stu-id="c8b95-160">On Windows Server 2008 R2 and Windows Vista, the default value for the IP Protection level on a socket is unrestricted.</span></span>|  
|<span data-ttu-id="c8b95-161">Nieokreślony</span><span class="sxs-lookup"><span data-stu-id="c8b95-161">Unspecified</span></span>|<span data-ttu-id="c8b95-162">Poziom ochrony IP jest nieokreślony.</span><span class="sxs-lookup"><span data-stu-id="c8b95-162">The IP protection level is unspecified.</span></span> <span data-ttu-id="c8b95-163">W systemie Windows 7 i Windows Server 2008 R2 wartością domyślną dla poziomu ochrony IP na gnieździe jest nieokreślony.</span><span class="sxs-lookup"><span data-stu-id="c8b95-163">On Windows 7 and Windows Server 2008 R2, the default value for the IP Protection level on a socket is unspecified.</span></span>|  
  
 <span data-ttu-id="c8b95-164">Wartość domyślna dla `ipProtectionLevel` atrybutu **nieokreślony**.</span><span class="sxs-lookup"><span data-stu-id="c8b95-164">The default value for the `ipProtectionLevel` attribute is **Unspecified**.</span></span>  
  
 <span data-ttu-id="c8b95-165"><xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> Właściwości można pobrać wartości bieżącego `ipProtectionLevel` atrybutu z plików zastosowania konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c8b95-165">The <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> property can be used to get the current value of the `ipProtectionLevel` attribute from applicable configuration files.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="c8b95-166">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="c8b95-166">Configuration Files</span></span>  
 <span data-ttu-id="c8b95-167">Ten element może być użyty w pliku konfiguracji aplikacji lub pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="c8b95-167">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8b95-168">Przykład</span><span class="sxs-lookup"><span data-stu-id="c8b95-168">Example</span></span>  
 <span data-ttu-id="c8b95-169">W poniższym przykładzie pokazano, jak określić, że używane portów, a wartość domyślna <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> powinny być nieograniczone.</span><span class="sxs-lookup"><span data-stu-id="c8b95-169">The following example shows how to specify that completion ports should be used and that the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> should be unrestricted.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c8b95-170">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c8b95-170">See Also</span></span>  
 <xref:System.Net?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SocketElement?displayProperty=nameWithType>  
 <xref:System.Net.Sockets?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.SocketOptionName.IPProtectionLevel?displayProperty=nameWithType>  
 [<span data-ttu-id="c8b95-171">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="c8b95-171">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
