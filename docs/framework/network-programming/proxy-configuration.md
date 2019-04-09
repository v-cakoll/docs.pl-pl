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
ms.openlocfilehash: c6b3808a2d73070cc07b31eb0fca7ca9d6af8cdb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59200548"
---
# <a name="proxy-configuration"></a><span data-ttu-id="4a815-102">Konfiguracja serwera proxy</span><span class="sxs-lookup"><span data-stu-id="4a815-102">Proxy Configuration</span></span>
<span data-ttu-id="4a815-103">Serwer proxy obsługuje żądania klienta dla zasobów.</span><span class="sxs-lookup"><span data-stu-id="4a815-103">A proxy server handles client requests for resources.</span></span> <span data-ttu-id="4a815-104">Serwer proxy można zwrócić żądany zasób z pamięci podręcznej lub przekazywać żądania do serwera, na którym znajduje się zasób.</span><span class="sxs-lookup"><span data-stu-id="4a815-104">A proxy can return a requested resource from its cache or forward the request to the server where the resource resides.</span></span> <span data-ttu-id="4a815-105">Serwery proxy może poprawić wydajność sieci dzięki zmniejszeniu liczby żądań wysyłanych do serwerów zdalnych.</span><span class="sxs-lookup"><span data-stu-id="4a815-105">Proxies can improve network performance by reducing the number of requests sent to remote servers.</span></span> <span data-ttu-id="4a815-106">Serwery proxy można również ograniczyć dostęp do zasobów.</span><span class="sxs-lookup"><span data-stu-id="4a815-106">Proxies can also be used to restrict access to resources.</span></span>  
  
## <a name="adaptive-proxies"></a><span data-ttu-id="4a815-107">Funkcje adaptacyjnego sterowania serwerów proxy</span><span class="sxs-lookup"><span data-stu-id="4a815-107">Adaptive Proxies</span></span>  
 <span data-ttu-id="4a815-108">W .NET Framework, serwery proxy dostępne w dwóch odmianach: adaptacyjne i statycznych.</span><span class="sxs-lookup"><span data-stu-id="4a815-108">In the .NET Framework, proxies come in two varieties: adaptive and static.</span></span> <span data-ttu-id="4a815-109">Serwery proxy adaptacyjne dostosować ich ustawienia, po zmianie konfiguracji sieci.</span><span class="sxs-lookup"><span data-stu-id="4a815-109">Adaptive proxies adjust their settings when the network configuration changes.</span></span> <span data-ttu-id="4a815-110">Na przykład, jeśli użytkownik komputera przenośnego uruchamia sieci połączenia telefonicznego, adaptacyjnej serwera proxy będzie rozpoznać tę zmianę, odnajdywanie Uruchom skrypt konfiguracji, na nowych i dostosować jego ustawienia odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="4a815-110">For example, if a laptop user starts a dialup network connection, an adaptive proxy would recognize this change, discover and run its new configuration script, and adjust its settings appropriately.</span></span>  
  
 <span data-ttu-id="4a815-111">Adaptacyjne serwery proxy są skonfigurowane przy użyciu skryptu konfiguracji (zobacz [automatyczne wykrywanie serwera Proxy](../../../docs/framework/network-programming/automatic-proxy-detection.md)).</span><span class="sxs-lookup"><span data-stu-id="4a815-111">Adaptive proxies are configured by a configuration script (see [Automatic Proxy Detection](../../../docs/framework/network-programming/automatic-proxy-detection.md)).</span></span> <span data-ttu-id="4a815-112">Skrypt generuje zestaw protokołów aplikacji i serwera proxy dla każdego protokołu.</span><span class="sxs-lookup"><span data-stu-id="4a815-112">The script generates a set of application protocols and a proxy for each protocol.</span></span>  
  
 <span data-ttu-id="4a815-113">Zmiany w środowisku sieciowym może wymagać używane w systemie nowy zestaw serwerów proxy.</span><span class="sxs-lookup"><span data-stu-id="4a815-113">Changes in the network environment may require that the system use a new set of proxies.</span></span> <span data-ttu-id="4a815-114">Jeśli połączenie sieciowe ulegnie awarii lub nowego połączenia sieciowego jest inicjowany, system musi odnajdywać właściwe źródło skryptu konfiguracji w nowym środowisku i uruchomić nowy skrypt.</span><span class="sxs-lookup"><span data-stu-id="4a815-114">If a network connection goes down or a new network connection is initialized, the system must discover the appropriate source of the configuration script in the new environment and run the new script.</span></span>  
  
 <span data-ttu-id="4a815-115">Możesz użyć `usesystemdefault` atrybutu [ `<proxy>` ](../configure-apps/file-schema/network/proxy-element-network-settings.md) elementu w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="4a815-115">You can use the `usesystemdefault` attribute of the [`<proxy>`](../configure-apps/file-schema/network/proxy-element-network-settings.md) element in your configuration file.</span></span> <span data-ttu-id="4a815-116">`usesystemdefault` Atrybutu formanty, czy ustawienia serwera proxy statyczne (adres serwera proxy, listy obejścia i obejście w lokalnych) są odczytywane z ustawień serwera proxy programu Internet Explorer dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4a815-116">The `usesystemdefault` attribute controls whether the static proxy settings (proxy address, bypass list, and bypass on local) should be read from the Internet Explorer proxy settings for the user.</span></span> <span data-ttu-id="4a815-117">Jeśli ta wartość jest równa `true`, zostaną użyte ustawienia proxy statyczne z programu Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="4a815-117">If this value is set to `true`, the static proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="4a815-118">Jeśli ta wartość jest `false` lub nie został ustawiony, ustawienia serwera proxy statyczne można określić w konfiguracji i spowoduje przesłonięcie ustawień serwera proxy programu Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="4a815-118">If this value is `false` or not set, the static proxy settings can be specified in the configuration and will override the Internet Explorer proxy settings.</span></span> <span data-ttu-id="4a815-119">Ta wartość musi również być równa `false` lub nie jest ustawiona dla adaptacyjne proxy do włączenia.</span><span class="sxs-lookup"><span data-stu-id="4a815-119">This value must also be set to `false` or not set for adaptive proxies to be enabled.</span></span>  
  
 <span data-ttu-id="4a815-120">Poniższy przykład przedstawia konfigurację typowe funkcje adaptacyjnego sterowania serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="4a815-120">The following example shows a typical adaptive proxy configuration.</span></span>  
  
```xml  
<system.net>  
    <defaultProxy>  
      <proxy usesystemdefault="false" />
    </defaultProxy>  
</system.net>  
```  
  
## <a name="static-proxies"></a><span data-ttu-id="4a815-121">Serwery proxy statyczne</span><span class="sxs-lookup"><span data-stu-id="4a815-121">Static Proxies</span></span>  
 <span data-ttu-id="4a815-122">Statycznego serwerów proxy są zwykle skonfigurowane jawnie przez aplikację, lub gdy plik konfiguracji jest wywoływany przez aplikację lub system.</span><span class="sxs-lookup"><span data-stu-id="4a815-122">Static proxies are usually configured explicitly by an application, or when a configuration file is invoked by an application or the system.</span></span> <span data-ttu-id="4a815-123">Statyczne serwery proxy są przydatne w sieciach, w których topologii zmieniają się rzadko, takich jak komputery pulpitu podłączone do sieci firmowej.</span><span class="sxs-lookup"><span data-stu-id="4a815-123">Static proxies are useful in networks in which the topology changes infrequently, such as a desktop computer connected to a corporate network.</span></span>  
  
 <span data-ttu-id="4a815-124">Kilka opcji kontroli, jak działa serwer proxy statyczne.</span><span class="sxs-lookup"><span data-stu-id="4a815-124">Several options control how a static proxy operates.</span></span> <span data-ttu-id="4a815-125">Należy określić następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="4a815-125">You can specify the following:</span></span>  
  
-   <span data-ttu-id="4a815-126">Adres serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="4a815-126">The address of the proxy.</span></span>  
  
-   <span data-ttu-id="4a815-127">Czy można pominąć serwer proxy, dla adresów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="4a815-127">Whether the proxy should be bypassed for local addresses.</span></span>  
  
-   <span data-ttu-id="4a815-128">Czy można pominąć serwer proxy, zbiór adresów.</span><span class="sxs-lookup"><span data-stu-id="4a815-128">Whether the proxy should be bypassed for a set of addresses.</span></span>  
  
 <span data-ttu-id="4a815-129">W poniższej tabeli przedstawiono opcje konfiguracji statycznej serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="4a815-129">The following table shows the configuration options for a static proxy.</span></span>  
  
|<span data-ttu-id="4a815-130">Ustawienie pliku atrybutu, właściwość lub konfiguracji</span><span class="sxs-lookup"><span data-stu-id="4a815-130">Attribute, property, or configuration file setting</span></span>|<span data-ttu-id="4a815-131">Opis</span><span class="sxs-lookup"><span data-stu-id="4a815-131">Description</span></span>|  
|--------------------------------------------------------|-----------------|  
|`proxyaddress` <span data-ttu-id="4a815-132">lub</span><span class="sxs-lookup"><span data-stu-id="4a815-132">or</span></span> <xref:System.Net.WebProxy.Address>|<span data-ttu-id="4a815-133">Adres serwera proxy do użycia.</span><span class="sxs-lookup"><span data-stu-id="4a815-133">The address of the proxy to use.</span></span>|  
|`bypassonlocal` <span data-ttu-id="4a815-134">lub</span><span class="sxs-lookup"><span data-stu-id="4a815-134">or</span></span> <xref:System.Net.WebProxy.BypassProxyOnLocal>|<span data-ttu-id="4a815-135">Określa, czy serwer proxy jest pomijane dla adresów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="4a815-135">Controls whether the proxy is bypassed for local addresses.</span></span>|  
|`bypasslist` <span data-ttu-id="4a815-136">lub</span><span class="sxs-lookup"><span data-stu-id="4a815-136">or</span></span> <xref:System.Net.WebProxy.BypassArrayList>|<span data-ttu-id="4a815-137">W tym artykule opisano, za pomocą wyrażeń regularnych zestawu adresów, które pomijają serwer proxy.</span><span class="sxs-lookup"><span data-stu-id="4a815-137">Describes, with regular expressions, a set of addresses that bypass the proxy.</span></span>|  
|`usesystemdefault`|<span data-ttu-id="4a815-138">Określa, czy ustawienia proxy statyczne (adres serwera proxy, listę obejść i obejście na lokalny) są odczytywane z ustawień serwera proxy programu Internet Explorer dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4a815-138">Controls whether the static proxy settings (proxy address, bypass list, and bypass on local) should be read from the Internet Explorer proxy settings for the user.</span></span> <span data-ttu-id="4a815-139">Jeśli ta wartość jest równa `true`, a następnie zostaną użyte ustawienia proxy statyczne z programu Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="4a815-139">If this value is set to `true`, then the static proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="4a815-140">.NET Framework 2.0, gdy ta wartość jest równa `true`, ustawienia serwera proxy programu Internet Explorer nie są zastępowane przez inne ustawienia serwera proxy w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="4a815-140">On .NET Framework 2.0 when this value is set to `true`, the Internet Explorer proxy settings are not overridden by other proxy settings in the configuration file.</span></span> <span data-ttu-id="4a815-141">W programie .NET Framework 1.1 ustawienia serwera proxy programu Internet Explorer mogą zostać zastąpione przez inne ustawienia serwera proxy w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="4a815-141">On .NET Framework 1.1, the Internet Explorer proxy settings can be overridden by other proxy settings in the configuration file.</span></span><br /><br /> <span data-ttu-id="4a815-142">Jeśli ta wartość jest `false` lub nie został ustawiony, następnie statyczne ustawienia serwera proxy może być określony w konfiguracji i spowoduje przesłonięcie ustawień serwera proxy programu Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="4a815-142">If this value is `false` or not set, then the static proxy settings can be specified in the configuration and will override the Internet Explorer proxy settings.</span></span> <span data-ttu-id="4a815-143">Ta wartość musi również być równa `false` lub nie jest ustawiona dla adaptacyjne proxy do włączenia.</span><span class="sxs-lookup"><span data-stu-id="4a815-143">This value must also be set to `false` or not set for adaptive proxies to be enabled.</span></span>|  
  
 <span data-ttu-id="4a815-144">Poniższy przykład pokazuje konfiguracji typowych statyczny serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="4a815-144">The following example shows a typical static proxy configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4a815-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4a815-145">See also</span></span>

- <xref:System.Net.WebProxy>
- <xref:System.Net.GlobalProxySelection>
- [<span data-ttu-id="4a815-146">Automatyczne wykrywanie serwera proxy</span><span class="sxs-lookup"><span data-stu-id="4a815-146">Automatic Proxy Detection</span></span>](../../../docs/framework/network-programming/automatic-proxy-detection.md)
