---
title: Konfiguracja serwera proxy
description: Dowiedz się, jak skonfigurować adaptacyjne i statyczne serwery proxy. Konfiguracja serwera proxy kontroluje sposób, w jaki serwer proxy obsługuje żądania klientów dotyczące zasobów.
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
ms.openlocfilehash: d1c8b69223ab470d505d9f8007bc01b29fdc66b8
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502213"
---
# <a name="proxy-configuration"></a><span data-ttu-id="e931e-104">Konfiguracja serwera proxy</span><span class="sxs-lookup"><span data-stu-id="e931e-104">Proxy Configuration</span></span>
<span data-ttu-id="e931e-105">Serwer proxy obsługuje żądania klientów dotyczące zasobów.</span><span class="sxs-lookup"><span data-stu-id="e931e-105">A proxy server handles client requests for resources.</span></span> <span data-ttu-id="e931e-106">Serwer proxy może zwrócić żądany zasób z jego pamięci podręcznej lub przesłać żądanie do serwera, na którym znajduje się zasób.</span><span class="sxs-lookup"><span data-stu-id="e931e-106">A proxy can return a requested resource from its cache or forward the request to the server where the resource resides.</span></span> <span data-ttu-id="e931e-107">Serwery proxy mogą zwiększyć wydajność sieci, zmniejszając liczbę żądań wysyłanych do serwerów zdalnych.</span><span class="sxs-lookup"><span data-stu-id="e931e-107">Proxies can improve network performance by reducing the number of requests sent to remote servers.</span></span> <span data-ttu-id="e931e-108">Serwery proxy mogą być również używane do ograniczania dostępu do zasobów.</span><span class="sxs-lookup"><span data-stu-id="e931e-108">Proxies can also be used to restrict access to resources.</span></span>  
  
## <a name="adaptive-proxies"></a><span data-ttu-id="e931e-109">Adaptacyjne serwery proxy</span><span class="sxs-lookup"><span data-stu-id="e931e-109">Adaptive Proxies</span></span>  
 <span data-ttu-id="e931e-110">W .NET Framework serwery proxy są dostępne w dwóch odmianach: adaptacyjne i statyczne.</span><span class="sxs-lookup"><span data-stu-id="e931e-110">In the .NET Framework, proxies come in two varieties: adaptive and static.</span></span> <span data-ttu-id="e931e-111">Adaptacyjne serwery proxy dostosowują swoje ustawienia w przypadku zmiany konfiguracji sieci.</span><span class="sxs-lookup"><span data-stu-id="e931e-111">Adaptive proxies adjust their settings when the network configuration changes.</span></span> <span data-ttu-id="e931e-112">Na przykład, jeśli użytkownik laptop uruchamia połączenie sieciowe telefoniczne, adaptacyjny serwer proxy rozpozna tę zmianę, odnajduje i uruchamia nowy skrypt konfiguracji i odpowiednio dostosowuje jego ustawienia.</span><span class="sxs-lookup"><span data-stu-id="e931e-112">For example, if a laptop user starts a dialup network connection, an adaptive proxy would recognize this change, discover and run its new configuration script, and adjust its settings appropriately.</span></span>  
  
 <span data-ttu-id="e931e-113">Adaptacyjne serwery proxy są konfigurowane przez skrypt konfiguracji (zobacz [Automatyczne wykrywanie serwera proxy](automatic-proxy-detection.md)).</span><span class="sxs-lookup"><span data-stu-id="e931e-113">Adaptive proxies are configured by a configuration script (see [Automatic Proxy Detection](automatic-proxy-detection.md)).</span></span> <span data-ttu-id="e931e-114">Skrypt generuje zestaw protokołów aplikacji i serwer proxy dla każdego protokołu.</span><span class="sxs-lookup"><span data-stu-id="e931e-114">The script generates a set of application protocols and a proxy for each protocol.</span></span>  
  
 <span data-ttu-id="e931e-115">Zmiany w środowisku sieciowym mogą wymagać, aby system używał nowego zestawu serwerów proxy.</span><span class="sxs-lookup"><span data-stu-id="e931e-115">Changes in the network environment may require that the system use a new set of proxies.</span></span> <span data-ttu-id="e931e-116">Jeśli połączenie sieciowe ulegnie awarii lub zostanie zainicjowane nowe połączenie sieciowe, system musi wykryć odpowiednie źródło skryptu konfiguracji w nowym środowisku i uruchomić nowy skrypt.</span><span class="sxs-lookup"><span data-stu-id="e931e-116">If a network connection goes down or a new network connection is initialized, the system must discover the appropriate source of the configuration script in the new environment and run the new script.</span></span>  
  
 <span data-ttu-id="e931e-117">Możesz użyć `usesystemdefault` atrybutu [`<proxy>`](../configure-apps/file-schema/network/proxy-element-network-settings.md) elementu w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e931e-117">You can use the `usesystemdefault` attribute of the [`<proxy>`](../configure-apps/file-schema/network/proxy-element-network-settings.md) element in your configuration file.</span></span> <span data-ttu-id="e931e-118">Ten `usesystemdefault` atrybut określa, czy ustawienia statycznego serwera proxy (adres serwera proxy, Lista pomijania i obejście dla lokalnego) powinny zostać odczytane z ustawień serwera proxy programu Internet Explorer dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e931e-118">The `usesystemdefault` attribute controls whether the static proxy settings (proxy address, bypass list, and bypass on local) should be read from the Internet Explorer proxy settings for the user.</span></span> <span data-ttu-id="e931e-119">Jeśli ta wartość jest ustawiona na `true` , zostaną użyte ustawienia statycznego serwera proxy z programu Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="e931e-119">If this value is set to `true`, the static proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="e931e-120">Jeśli ta wartość jest `false` lub nie jest ustawiona, statyczne ustawienia serwera proxy mogą być określone w konfiguracji i zastąpią ustawienia serwera proxy programu Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="e931e-120">If this value is `false` or not set, the static proxy settings can be specified in the configuration and will override the Internet Explorer proxy settings.</span></span> <span data-ttu-id="e931e-121">Ta wartość musi być również ustawiona na `false` lub nie ustawiona dla adaptacyjnych serwerów proxy, aby można ją było włączyć.</span><span class="sxs-lookup"><span data-stu-id="e931e-121">This value must also be set to `false` or not set for adaptive proxies to be enabled.</span></span>  
  
 <span data-ttu-id="e931e-122">Poniższy przykład przedstawia typową adaptacyjną konfigurację serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="e931e-122">The following example shows a typical adaptive proxy configuration.</span></span>  
  
```xml  
<system.net>  
    <defaultProxy>  
      <proxy usesystemdefault="false" />
    </defaultProxy>  
</system.net>  
```  
  
## <a name="static-proxies"></a><span data-ttu-id="e931e-123">Statyczne serwery proxy</span><span class="sxs-lookup"><span data-stu-id="e931e-123">Static Proxies</span></span>  
 <span data-ttu-id="e931e-124">Statyczne serwery proxy są zwykle konfigurowane jawnie przez aplikację lub gdy plik konfiguracji jest wywoływany przez aplikację lub system.</span><span class="sxs-lookup"><span data-stu-id="e931e-124">Static proxies are usually configured explicitly by an application, or when a configuration file is invoked by an application or the system.</span></span> <span data-ttu-id="e931e-125">Statyczne serwery proxy są przydatne w sieciach, w których topologia zmienia się rzadko, na przykład na komputerze stacjonarnym podłączonym do sieci firmowej.</span><span class="sxs-lookup"><span data-stu-id="e931e-125">Static proxies are useful in networks in which the topology changes infrequently, such as a desktop computer connected to a corporate network.</span></span>  
  
 <span data-ttu-id="e931e-126">Niektóre opcje kontrolują sposób działania statycznego serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="e931e-126">Several options control how a static proxy operates.</span></span> <span data-ttu-id="e931e-127">Można określić następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="e931e-127">You can specify the following:</span></span>  
  
- <span data-ttu-id="e931e-128">Adres serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="e931e-128">The address of the proxy.</span></span>  
  
- <span data-ttu-id="e931e-129">Czy serwer proxy powinien być pomijany dla adresów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="e931e-129">Whether the proxy should be bypassed for local addresses.</span></span>  
  
- <span data-ttu-id="e931e-130">Czy serwer proxy powinien być pomijany dla zbioru adresów.</span><span class="sxs-lookup"><span data-stu-id="e931e-130">Whether the proxy should be bypassed for a set of addresses.</span></span>  
  
 <span data-ttu-id="e931e-131">W poniższej tabeli przedstawiono opcje konfiguracji dla statycznego serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="e931e-131">The following table shows the configuration options for a static proxy.</span></span>  
  
|<span data-ttu-id="e931e-132">Ustawienie atrybutu, właściwości lub pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="e931e-132">Attribute, property, or configuration file setting</span></span>|<span data-ttu-id="e931e-133">Opis</span><span class="sxs-lookup"><span data-stu-id="e931e-133">Description</span></span>|  
|--------------------------------------------------------|-----------------|  
|<span data-ttu-id="e931e-134">`proxyaddress` lub <xref:System.Net.WebProxy.Address></span><span class="sxs-lookup"><span data-stu-id="e931e-134">`proxyaddress` or <xref:System.Net.WebProxy.Address></span></span>|<span data-ttu-id="e931e-135">Adres serwera proxy, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="e931e-135">The address of the proxy to use.</span></span>|  
|<span data-ttu-id="e931e-136">`bypassonlocal` lub <xref:System.Net.WebProxy.BypassProxyOnLocal></span><span class="sxs-lookup"><span data-stu-id="e931e-136">`bypassonlocal` or <xref:System.Net.WebProxy.BypassProxyOnLocal></span></span>|<span data-ttu-id="e931e-137">Określa, czy serwer proxy jest pomijany dla adresów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="e931e-137">Controls whether the proxy is bypassed for local addresses.</span></span>|  
|<span data-ttu-id="e931e-138">`bypasslist` lub <xref:System.Net.WebProxy.BypassArrayList></span><span class="sxs-lookup"><span data-stu-id="e931e-138">`bypasslist` or <xref:System.Net.WebProxy.BypassArrayList></span></span>|<span data-ttu-id="e931e-139">Opisuje, w wyrażeniach regularnych, zestaw adresów, które pomijają serwer proxy.</span><span class="sxs-lookup"><span data-stu-id="e931e-139">Describes, with regular expressions, a set of addresses that bypass the proxy.</span></span>|  
|`usesystemdefault`|<span data-ttu-id="e931e-140">Określa, czy ustawienia statycznego serwera proxy (adres serwera proxy, Lista pomijania i obejście dla lokalnego) powinny zostać odczytane z ustawień serwera proxy programu Internet Explorer dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e931e-140">Controls whether the static proxy settings (proxy address, bypass list, and bypass on local) should be read from the Internet Explorer proxy settings for the user.</span></span> <span data-ttu-id="e931e-141">Jeśli ta wartość jest ustawiona na `true` , zostaną użyte ustawienia statycznego serwera proxy z programu Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="e931e-141">If this value is set to `true`, then the static proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="e931e-142">W .NET Framework 2,0, gdy ta wartość jest ustawiona na `true` , ustawienia serwera proxy programu Internet Explorer nie są zastępowane przez inne ustawienia serwera proxy w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e931e-142">On .NET Framework 2.0 when this value is set to `true`, the Internet Explorer proxy settings are not overridden by other proxy settings in the configuration file.</span></span> <span data-ttu-id="e931e-143">W .NET Framework 1,1 ustawienia serwera proxy programu Internet Explorer mogą być przesłonięte przez inne ustawienia serwera proxy w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e931e-143">On .NET Framework 1.1, the Internet Explorer proxy settings can be overridden by other proxy settings in the configuration file.</span></span><br /><br /> <span data-ttu-id="e931e-144">Jeśli ta wartość jest `false` lub nie jest ustawiona, statyczne ustawienia serwera proxy mogą być określone w konfiguracji i zastąpią ustawienia serwera proxy programu Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="e931e-144">If this value is `false` or not set, then the static proxy settings can be specified in the configuration and will override the Internet Explorer proxy settings.</span></span> <span data-ttu-id="e931e-145">Ta wartość musi być również ustawiona na `false` lub nie ustawiona dla adaptacyjnych serwerów proxy, aby można ją było włączyć.</span><span class="sxs-lookup"><span data-stu-id="e931e-145">This value must also be set to `false` or not set for adaptive proxies to be enabled.</span></span>|  
  
 <span data-ttu-id="e931e-146">Poniższy przykład przedstawia typową konfigurację statycznego serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="e931e-146">The following example shows a typical static proxy configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e931e-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e931e-147">See also</span></span>

- <xref:System.Net.WebProxy>
- <xref:System.Net.GlobalProxySelection>
- [<span data-ttu-id="e931e-148">Automatyczne wykrywanie serwera proxy</span><span class="sxs-lookup"><span data-stu-id="e931e-148">Automatic Proxy Detection</span></span>](automatic-proxy-detection.md)
