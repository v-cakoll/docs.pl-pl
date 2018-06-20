---
title: Konfiguracja serwera proxy
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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 6cf25d3d7dcde963f06729794716b75dffdb64ae
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2018
ms.locfileid: "36207368"
---
# <a name="proxy-configuration"></a><span data-ttu-id="a7c9a-102">Konfiguracja serwera proxy</span><span class="sxs-lookup"><span data-stu-id="a7c9a-102">Proxy Configuration</span></span>
<span data-ttu-id="a7c9a-103">Serwer proxy obsługuje żądania klientów dotyczące zasobów.</span><span class="sxs-lookup"><span data-stu-id="a7c9a-103">A proxy server handles client requests for resources.</span></span> <span data-ttu-id="a7c9a-104">Serwer proxy można zwrócić żądanych zasobów z pamięci podręcznej lub przesyła żądanie do serwera, na którym znajduje się zasób.</span><span class="sxs-lookup"><span data-stu-id="a7c9a-104">A proxy can return a requested resource from its cache or forward the request to the server where the resource resides.</span></span> <span data-ttu-id="a7c9a-105">Serwery proxy może zwiększyć wydajność sieci dzięki zmniejszeniu liczby żądań wysyłanych do serwerów zdalnych.</span><span class="sxs-lookup"><span data-stu-id="a7c9a-105">Proxies can improve network performance by reducing the number of requests sent to remote servers.</span></span> <span data-ttu-id="a7c9a-106">Serwery proxy można również ograniczyć dostęp do zasobów.</span><span class="sxs-lookup"><span data-stu-id="a7c9a-106">Proxies can also be used to restrict access to resources.</span></span>  
  
## <a name="adaptive-proxies"></a><span data-ttu-id="a7c9a-107">Adaptacyjną serwerów proxy</span><span class="sxs-lookup"><span data-stu-id="a7c9a-107">Adaptive Proxies</span></span>  
 <span data-ttu-id="a7c9a-108">W programie .NET Framework, serwery proxy są dostępne w dwóch odmian: adaptacyjną i statyczne.</span><span class="sxs-lookup"><span data-stu-id="a7c9a-108">In the .NET Framework, proxies come in two varieties: adaptive and static.</span></span> <span data-ttu-id="a7c9a-109">Serwery proxy adaptacyjną ich ustawienia, po zmianie konfiguracji sieci.</span><span class="sxs-lookup"><span data-stu-id="a7c9a-109">Adaptive proxies adjust their settings when the network configuration changes.</span></span> <span data-ttu-id="a7c9a-110">Na przykład jeśli użytkownik komputera przenośnego uruchamia połączenie telefoniczne, adaptacyjną serwera proxy będzie rozpoznawać tej zmiany, odnajdywania i uruchamiania jego nowy skrypt konfiguracji i dostosować jego ustawienia odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="a7c9a-110">For example, if a laptop user starts a dialup network connection, an adaptive proxy would recognize this change, discover and run its new configuration script, and adjust its settings appropriately.</span></span>  
  
 <span data-ttu-id="a7c9a-111">Adaptacyjną serwery proxy są skonfigurowane za pomocą skryptu konfiguracji (zobacz [automatycznego wykrywania Proxy](../../../docs/framework/network-programming/automatic-proxy-detection.md)).</span><span class="sxs-lookup"><span data-stu-id="a7c9a-111">Adaptive proxies are configured by a configuration script (see [Automatic Proxy Detection](../../../docs/framework/network-programming/automatic-proxy-detection.md)).</span></span> <span data-ttu-id="a7c9a-112">Skrypt generuje zestaw protokołów aplikacji i serwer proxy dla każdego protokołu.</span><span class="sxs-lookup"><span data-stu-id="a7c9a-112">The script generates a set of application protocols and a proxy for each protocol.</span></span>  
  
 <span data-ttu-id="a7c9a-113">Zmiany w środowisku sieciowym może wymagać używane nowy zestaw serwerów proxy w systemie.</span><span class="sxs-lookup"><span data-stu-id="a7c9a-113">Changes in the network environment may require that the system use a new set of proxies.</span></span> <span data-ttu-id="a7c9a-114">Jeśli połączenie sieciowe ulegnie awarii lub nowego połączenia sieciowego jest zainicjowany, system musi odnaleźć Źródło odpowiedni skrypt konfiguracji w nowym środowisku i uruchom nowy skrypt.</span><span class="sxs-lookup"><span data-stu-id="a7c9a-114">If a network connection goes down or a new network connection is initialized, the system must discover the appropriate source of the configuration script in the new environment and run the new script.</span></span>  
  
 <span data-ttu-id="a7c9a-115">Można użyć `usesystemdefault` atrybutu [ `<proxy>` ](../configure-apps/file-schema/network/proxy-element-network-settings.md) elementu w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a7c9a-115">You can use the `usesystemdefault` attribute of the [`<proxy>`](../configure-apps/file-schema/network/proxy-element-network-settings.md) element in your configuration file.</span></span> <span data-ttu-id="a7c9a-116">`usesystemdefault` Atrybut kontrolki, czy ustawienia serwera proxy statyczne (adres serwera proxy, listy obejścia i obejście na lokalnym) są odczytywane z ustawień serwera proxy programu Internet Explorer dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a7c9a-116">The `usesystemdefault` attribute controls whether the static proxy settings (proxy address, bypass list, and bypass on local) should be read from the Internet Explorer proxy settings for the user.</span></span> <span data-ttu-id="a7c9a-117">Jeśli ta wartość jest równa `true`, zostaną użyte ustawienia statycznych serwera proxy w programie Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="a7c9a-117">If this value is set to `true`, the static proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="a7c9a-118">Jeśli ta wartość jest `false` lub nie jest ustawiona, ustawienia serwera proxy statycznych może być określony w konfiguracji i zastąpią ustawienia serwera proxy programu Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="a7c9a-118">If this value is `false` or not set, the static proxy settings can be specified in the configuration and will override the Internet Explorer proxy settings.</span></span> <span data-ttu-id="a7c9a-119">Ta wartość musi również mieć ustawioną `false` lub nie ustawiono dla adaptacyjną proxy włączenia.</span><span class="sxs-lookup"><span data-stu-id="a7c9a-119">This value must also be set to `false` or not set for adaptive proxies to be enabled.</span></span>  
  
 <span data-ttu-id="a7c9a-120">Poniższy przykład przedstawia konfiguracji typowych adaptacyjną serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="a7c9a-120">The following example shows a typical adaptive proxy configuration.</span></span>  
  
```xml  
<system.net>  
    <defaultProxy>  
      <proxy usesystemdefault="false" />
    </defaultProxy>  
</system.net>  
```  
  
## <a name="static-proxies"></a><span data-ttu-id="a7c9a-121">Statyczne serwerów proxy</span><span class="sxs-lookup"><span data-stu-id="a7c9a-121">Static Proxies</span></span>  
 <span data-ttu-id="a7c9a-122">Statyczne serwery proxy są zazwyczaj konfigurowane jawnie przez aplikację, lub gdy plik konfiguracji jest wywoływany przez aplikację lub systemu.</span><span class="sxs-lookup"><span data-stu-id="a7c9a-122">Static proxies are usually configured explicitly by an application, or when a configuration file is invoked by an application or the system.</span></span> <span data-ttu-id="a7c9a-123">Statyczne serwery proxy są przydatne w sieciach, w których topologii zmienia się rzadko, takich jak komputer stacjonarny podłączone do sieci firmowej.</span><span class="sxs-lookup"><span data-stu-id="a7c9a-123">Static proxies are useful in networks in which the topology changes infrequently, such as a desktop computer connected to a corporate network.</span></span>  
  
 <span data-ttu-id="a7c9a-124">Kilka opcji kontrolować sposób działania statycznych serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="a7c9a-124">Several options control how a static proxy operates.</span></span> <span data-ttu-id="a7c9a-125">Można określić następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="a7c9a-125">You can specify the following:</span></span>  
  
-   <span data-ttu-id="a7c9a-126">Adres serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="a7c9a-126">The address of the proxy.</span></span>  
  
-   <span data-ttu-id="a7c9a-127">Czy należy pominąć serwer proxy dla adresów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="a7c9a-127">Whether the proxy should be bypassed for local addresses.</span></span>  
  
-   <span data-ttu-id="a7c9a-128">Określa, czy można pominąć serwer proxy, zbiór adresów.</span><span class="sxs-lookup"><span data-stu-id="a7c9a-128">Whether the proxy should be bypassed for a set of addresses.</span></span>  
  
 <span data-ttu-id="a7c9a-129">W poniższej tabeli przedstawiono opcje konfiguracji statycznej serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="a7c9a-129">The following table shows the configuration options for a static proxy.</span></span>  
  
|<span data-ttu-id="a7c9a-130">Ustawienie pliku atrybutu, właściwość lub konfiguracji</span><span class="sxs-lookup"><span data-stu-id="a7c9a-130">Attribute, property, or configuration file setting</span></span>|<span data-ttu-id="a7c9a-131">Opis</span><span class="sxs-lookup"><span data-stu-id="a7c9a-131">Description</span></span>|  
|--------------------------------------------------------|-----------------|  
|<span data-ttu-id="a7c9a-132">`proxyaddress` lub <xref:System.Net.WebProxy.Address></span><span class="sxs-lookup"><span data-stu-id="a7c9a-132">`proxyaddress` or <xref:System.Net.WebProxy.Address></span></span>|<span data-ttu-id="a7c9a-133">Adres serwera proxy do użycia.</span><span class="sxs-lookup"><span data-stu-id="a7c9a-133">The address of the proxy to use.</span></span>|  
|<span data-ttu-id="a7c9a-134">`bypassonlocal` lub <xref:System.Net.WebProxy.BypassProxyOnLocal></span><span class="sxs-lookup"><span data-stu-id="a7c9a-134">`bypassonlocal` or <xref:System.Net.WebProxy.BypassProxyOnLocal></span></span>|<span data-ttu-id="a7c9a-135">Określa, czy serwer proxy jest pomijana dla adresów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="a7c9a-135">Controls whether the proxy is bypassed for local addresses.</span></span>|  
|<span data-ttu-id="a7c9a-136">`bypasslist` lub <xref:System.Net.WebProxy.BypassArrayList></span><span class="sxs-lookup"><span data-stu-id="a7c9a-136">`bypasslist` or <xref:System.Net.WebProxy.BypassArrayList></span></span>|<span data-ttu-id="a7c9a-137">Opisuje za pomocą wyrażeń regularnych, zestaw adresów, które pominąć serwer proxy.</span><span class="sxs-lookup"><span data-stu-id="a7c9a-137">Describes, with regular expressions, a set of addresses that bypass the proxy.</span></span>|  
|`usesystemdefault`|<span data-ttu-id="a7c9a-138">Określa, czy ustawienia serwera proxy statyczne (adres serwera proxy, listy obejścia i obejście na lokalnym) są odczytywane z ustawień serwera proxy programu Internet Explorer dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a7c9a-138">Controls whether the static proxy settings (proxy address, bypass list, and bypass on local) should be read from the Internet Explorer proxy settings for the user.</span></span> <span data-ttu-id="a7c9a-139">Jeśli ta wartość jest równa `true`, zostaną użyte ustawienia statycznych serwera proxy w programie Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="a7c9a-139">If this value is set to `true`, then the static proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="a7c9a-140">.NET Framework 2.0, gdy ta wartość jest równa `true`, ustawienia serwera proxy programu Internet Explorer nie zostały zastąpione przez inne ustawienia serwera proxy w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a7c9a-140">On .NET Framework 2.0 when this value is set to `true`, the Internet Explorer proxy settings are not overridden by other proxy settings in the configuration file.</span></span> <span data-ttu-id="a7c9a-141">W programie .NET Framework 1.1 ustawienia serwera proxy programu Internet Explorer, może zostać przesłonięta przez inne ustawienia serwera proxy w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a7c9a-141">On .NET Framework 1.1, the Internet Explorer proxy settings can be overridden by other proxy settings in the configuration file.</span></span><br /><br /> <span data-ttu-id="a7c9a-142">Jeśli ta wartość jest `false` lub nie został ustawiony, następnie statyczne ustawienia serwera proxy może być określony w konfiguracji i zastąpią ustawienia serwera proxy programu Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="a7c9a-142">If this value is `false` or not set, then the static proxy settings can be specified in the configuration and will override the Internet Explorer proxy settings.</span></span> <span data-ttu-id="a7c9a-143">Ta wartość musi również mieć ustawioną `false` lub nie ustawiono dla adaptacyjną proxy włączenia.</span><span class="sxs-lookup"><span data-stu-id="a7c9a-143">This value must also be set to `false` or not set for adaptive proxies to be enabled.</span></span>|  
  
 <span data-ttu-id="a7c9a-144">Poniższy przykład przedstawia konfiguracji typowych statycznych serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="a7c9a-144">The following example shows a typical static proxy configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a7c9a-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a7c9a-145">See Also</span></span>  
 <xref:System.Net.WebProxy>  
 <xref:System.Net.GlobalProxySelection>  
 [<span data-ttu-id="a7c9a-146">Automatyczne wykrywanie serwera proxy</span><span class="sxs-lookup"><span data-stu-id="a7c9a-146">Automatic Proxy Detection</span></span>](../../../docs/framework/network-programming/automatic-proxy-detection.md)
