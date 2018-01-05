---
title: Konfiguracja serwera proxy
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 41f7cfe76acfb4b6bbf66207685935c190a51901
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="proxy-configuration"></a><span data-ttu-id="13c3f-102">Konfiguracja serwera proxy</span><span class="sxs-lookup"><span data-stu-id="13c3f-102">Proxy Configuration</span></span>
<span data-ttu-id="13c3f-103">Serwer proxy obsługuje żądania klientów dotyczące zasobów.</span><span class="sxs-lookup"><span data-stu-id="13c3f-103">A proxy server handles client requests for resources.</span></span> <span data-ttu-id="13c3f-104">Serwer proxy można zwrócić żądanych zasobów z pamięci podręcznej lub przesyła żądanie do serwera, na którym znajduje się zasób.</span><span class="sxs-lookup"><span data-stu-id="13c3f-104">A proxy can return a requested resource from its cache or forward the request to the server where the resource resides.</span></span> <span data-ttu-id="13c3f-105">Serwery proxy może zwiększyć wydajność sieci dzięki zmniejszeniu liczby żądań wysyłanych do serwerów zdalnych.</span><span class="sxs-lookup"><span data-stu-id="13c3f-105">Proxies can improve network performance by reducing the number of requests sent to remote servers.</span></span> <span data-ttu-id="13c3f-106">Serwery proxy można również ograniczyć dostęp do zasobów.</span><span class="sxs-lookup"><span data-stu-id="13c3f-106">Proxies can also be used to restrict access to resources.</span></span>  
  
## <a name="adaptive-proxies"></a><span data-ttu-id="13c3f-107">Adaptacyjną serwerów proxy</span><span class="sxs-lookup"><span data-stu-id="13c3f-107">Adaptive Proxies</span></span>  
 <span data-ttu-id="13c3f-108">W programie .NET Framework, serwery proxy są dostępne w dwóch odmian: adaptacyjną i statyczne.</span><span class="sxs-lookup"><span data-stu-id="13c3f-108">In the .NET Framework, proxies come in two varieties: adaptive and static.</span></span> <span data-ttu-id="13c3f-109">Serwery proxy adaptacyjną ich ustawienia, po zmianie konfiguracji sieci.</span><span class="sxs-lookup"><span data-stu-id="13c3f-109">Adaptive proxies adjust their settings when the network configuration changes.</span></span> <span data-ttu-id="13c3f-110">Na przykład jeśli użytkownik komputera przenośnego uruchamia połączenie telefoniczne, adaptacyjną serwera proxy będzie rozpoznawać tej zmiany, odnajdywania i uruchamiania jego nowy skrypt konfiguracji i dostosować jego ustawienia odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="13c3f-110">For example, if a laptop user starts a dialup network connection, an adaptive proxy would recognize this change, discover and run its new configuration script, and adjust its settings appropriately.</span></span>  
  
 <span data-ttu-id="13c3f-111">Adaptacyjną serwery proxy są skonfigurowane za pomocą skryptu konfiguracji (zobacz [automatycznego wykrywania Proxy](../../../docs/framework/network-programming/automatic-proxy-detection.md)).</span><span class="sxs-lookup"><span data-stu-id="13c3f-111">Adaptive proxies are configured by a configuration script (see [Automatic Proxy Detection](../../../docs/framework/network-programming/automatic-proxy-detection.md)).</span></span> <span data-ttu-id="13c3f-112">Skrypt generuje zestaw protokołów aplikacji i serwer proxy dla każdego protokołu.</span><span class="sxs-lookup"><span data-stu-id="13c3f-112">The script generates a set of application protocols and a proxy for each protocol.</span></span>  
  
 <span data-ttu-id="13c3f-113">Kilka opcji kontrolować sposób uruchamiania skryptu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="13c3f-113">Several options control how the configuration script is run.</span></span> <span data-ttu-id="13c3f-114">Można określić następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="13c3f-114">You can specify the following:</span></span>  
  
-   <span data-ttu-id="13c3f-115">Jak często skryptu konfiguracji jest pobierane i uruchom.</span><span class="sxs-lookup"><span data-stu-id="13c3f-115">How often the configuration script is downloaded and run.</span></span>  
  
-   <span data-ttu-id="13c3f-116">Jak długo czekać na pobieranie skryptu.</span><span class="sxs-lookup"><span data-stu-id="13c3f-116">How long to wait for the script to download.</span></span>  
  
-   <span data-ttu-id="13c3f-117">Które poświadczeń systemu należy używać dostępu do serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="13c3f-117">Which credentials your system should use to access the proxy.</span></span>  
  
-   <span data-ttu-id="13c3f-118">Które poświadczeń systemu powinna być używana do pobrania skryptu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="13c3f-118">Which credentials your system should use to download the configuration script.</span></span>  
  
 <span data-ttu-id="13c3f-119">Zmiany w środowisku sieciowym może wymagać używane nowy zestaw serwerów proxy w systemie.</span><span class="sxs-lookup"><span data-stu-id="13c3f-119">Changes in the network environment may require that the system use a new set of proxies.</span></span> <span data-ttu-id="13c3f-120">Jeśli połączenie sieciowe ulegnie awarii lub nowego połączenia sieciowego jest zainicjowany, system musi odnaleźć Źródło odpowiedni skrypt konfiguracji w nowym środowisku i uruchom nowy skrypt.</span><span class="sxs-lookup"><span data-stu-id="13c3f-120">If a network connection goes down or a new network connection is initialized, the system must discover the appropriate source of the configuration script in the new environment and run the new script.</span></span>  
  
 <span data-ttu-id="13c3f-121">W poniższej tabeli przedstawiono opcje konfiguracji dla serwera proxy adaptacyjną.</span><span class="sxs-lookup"><span data-stu-id="13c3f-121">The following table shows configuration options for an adaptive proxy.</span></span>  
  
|<span data-ttu-id="13c3f-122">Ustawienie pliku atrybutu, właściwość lub konfiguracji</span><span class="sxs-lookup"><span data-stu-id="13c3f-122">Attribute, property, or configuration file setting</span></span>|<span data-ttu-id="13c3f-123">Opis</span><span class="sxs-lookup"><span data-stu-id="13c3f-123">Description</span></span>|  
|--------------------------------------------------------|-----------------|  
|`scriptDownloadInterval`|<span data-ttu-id="13c3f-124">Czas w sekundach między pobraniami skryptu.</span><span class="sxs-lookup"><span data-stu-id="13c3f-124">Elapsed time in seconds between script downloads.</span></span>|  
|`scriptDownloadTimeout`|<span data-ttu-id="13c3f-125">Czas oczekiwania (w sekundach) dla skryptu do pobrania.</span><span class="sxs-lookup"><span data-stu-id="13c3f-125">Time to wait (in seconds) for the script to download.</span></span>|  
|<span data-ttu-id="13c3f-126">`useDefaultCredentials`lub<xref:System.Net.WebProxy.UseDefaultCredentials></span><span class="sxs-lookup"><span data-stu-id="13c3f-126">`useDefaultCredentials` or <xref:System.Net.WebProxy.UseDefaultCredentials></span></span>|<span data-ttu-id="13c3f-127">Określa, czy system używa sieci domyślne poświadczenia dostępu do serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="13c3f-127">Controls whether the system uses the default network credentials to access a proxy.</span></span>|  
|`useDefaultCredentialForScriptDownload`|<span data-ttu-id="13c3f-128">Określa, czy system używa poświadczeń domyślnych w sieci można pobrać skryptu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="13c3f-128">Controls whether the system uses the default network credentials to download the configuration script.</span></span>|  
|`usesystemdefaults`|<span data-ttu-id="13c3f-129">Określa, czy ustawienia serwera proxy statyczne (adres serwera proxy, listy obejścia i obejście na lokalnym) są odczytywane z ustawień serwera proxy programu Internet Explorer dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="13c3f-129">Controls whether the static proxy settings (proxy address, bypass list, and bypass on local) should be read from the Internet Explorer proxy settings for the user.</span></span> <span data-ttu-id="13c3f-130">Jeśli ta wartość jest równa "true", a następnie ustawienia serwera proxy statyczne z programu Internet Explorer będzie używany.</span><span class="sxs-lookup"><span data-stu-id="13c3f-130">If this value is set to "true", then the static proxy settings from Internet Explorer will be used.</span></span><br /><br /> <span data-ttu-id="13c3f-131">Jeśli ta wartość wynosi "false" lub nie zestawu, a następnie ustawienia serwera proxy statycznych może być określony w konfiguracji i zastąpią ustawienia serwera proxy programu Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="13c3f-131">If this value is "false" or not set, then the static proxy settings can be specified in the configuration and will override the Internet Explorer proxy settings.</span></span> <span data-ttu-id="13c3f-132">Ta wartość również musi mieć ustawioną "wartość false" lub nie została ustawiona dla adaptacyjną proxy włączenia.</span><span class="sxs-lookup"><span data-stu-id="13c3f-132">This value must also be set to "false" or not set for adaptive proxies to be enabled.</span></span>|  
  
 <span data-ttu-id="13c3f-133">Poniższy przykład przedstawia konfiguracji typowych adaptacyjną serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="13c3f-133">The following example shows a typical adaptive proxy configuration.</span></span>  
  
```xml  
<system.net>  
    <defaultProxy>  
      <proxy  scriptDownloadInterval="600"  
              scriptDownloadTimeout="30"  
              useDefaultCredentials="true"  
              usesystemdefaults="true"  
      />  
    </defaultProxy>  
</system.net>  
```  
  
## <a name="static-proxies"></a><span data-ttu-id="13c3f-134">Statyczne serwerów proxy</span><span class="sxs-lookup"><span data-stu-id="13c3f-134">Static Proxies</span></span>  
 <span data-ttu-id="13c3f-135">Statyczne serwery proxy są zazwyczaj konfigurowane jawnie przez aplikację, lub gdy plik konfiguracji jest wywoływany przez aplikację lub systemu.</span><span class="sxs-lookup"><span data-stu-id="13c3f-135">Static proxies are usually configured explicitly by an application, or when a configuration file is invoked by an application or the system.</span></span> <span data-ttu-id="13c3f-136">Statyczne serwery proxy są przydatne w sieciach, w których topologii zmienia się rzadko, takich jak komputer stacjonarny podłączone do sieci firmowej.</span><span class="sxs-lookup"><span data-stu-id="13c3f-136">Static proxies are useful in networks in which the topology changes infrequently, such as a desktop computer connected to a corporate network.</span></span>  
  
 <span data-ttu-id="13c3f-137">Kilka opcji kontrolować sposób działania statycznych serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="13c3f-137">Several options control how a static proxy operates.</span></span> <span data-ttu-id="13c3f-138">Można określić następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="13c3f-138">You can specify the following:</span></span>  
  
-   <span data-ttu-id="13c3f-139">Adres serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="13c3f-139">The address of the proxy.</span></span>  
  
-   <span data-ttu-id="13c3f-140">Czy należy pominąć serwer proxy dla adresów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="13c3f-140">Whether the proxy should be bypassed for local addresses.</span></span>  
  
-   <span data-ttu-id="13c3f-141">Określa, czy można pominąć serwer proxy, zbiór adresów.</span><span class="sxs-lookup"><span data-stu-id="13c3f-141">Whether the proxy should be bypassed for a set of addresses.</span></span>  
  
 <span data-ttu-id="13c3f-142">W poniższej tabeli przedstawiono opcje konfiguracji statycznej serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="13c3f-142">The following table shows the configuration options for a static proxy.</span></span>  
  
|<span data-ttu-id="13c3f-143">Ustawienie pliku atrybutu, właściwość lub konfiguracji</span><span class="sxs-lookup"><span data-stu-id="13c3f-143">Attribute, property, or configuration file setting</span></span>|<span data-ttu-id="13c3f-144">Opis</span><span class="sxs-lookup"><span data-stu-id="13c3f-144">Description</span></span>|  
|--------------------------------------------------------|-----------------|  
|<span data-ttu-id="13c3f-145">`proxyaddress`lub<xref:System.Net.WebProxy.Address></span><span class="sxs-lookup"><span data-stu-id="13c3f-145">`proxyaddress` or <xref:System.Net.WebProxy.Address></span></span>|<span data-ttu-id="13c3f-146">Adres serwera proxy do użycia.</span><span class="sxs-lookup"><span data-stu-id="13c3f-146">The address of the proxy to use.</span></span>|  
|<span data-ttu-id="13c3f-147">`bypassonlocal`lub<xref:System.Net.WebProxy.BypassProxyOnLocal></span><span class="sxs-lookup"><span data-stu-id="13c3f-147">`bypassonlocal` or <xref:System.Net.WebProxy.BypassProxyOnLocal></span></span>|<span data-ttu-id="13c3f-148">Określa, czy serwer proxy jest pomijana dla adresów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="13c3f-148">Controls whether the proxy is bypassed for local addresses.</span></span>|  
|<span data-ttu-id="13c3f-149">`bypasslist`lub<xref:System.Net.WebProxy.BypassArrayList></span><span class="sxs-lookup"><span data-stu-id="13c3f-149">`bypasslist` or <xref:System.Net.WebProxy.BypassArrayList></span></span>|<span data-ttu-id="13c3f-150">Opisuje za pomocą wyrażeń regularnych, zestaw adresów, które pominąć serwer proxy.</span><span class="sxs-lookup"><span data-stu-id="13c3f-150">Describes, with regular expressions, a set of addresses that bypass the proxy.</span></span>|  
|`usesystemdefaults`|<span data-ttu-id="13c3f-151">Określa, czy ustawienia serwera proxy statyczne (adres serwera proxy, listy obejścia i obejście na lokalnym) są odczytywane z ustawień serwera proxy programu Internet Explorer dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="13c3f-151">Controls whether the static proxy settings (proxy address, bypass list, and bypass on local) should be read from the Internet Explorer proxy settings for the user.</span></span> <span data-ttu-id="13c3f-152">Jeśli ta wartość jest równa "true", a następnie ustawienia serwera proxy statyczne z programu Internet Explorer będzie używany.</span><span class="sxs-lookup"><span data-stu-id="13c3f-152">If this value is set to "true", then the static proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="13c3f-153">.NET Framework 2.0, gdy ta wartość jest równa "true", ustawienia serwera proxy programu Internet Explorer ustawienia nie są zastępowane przez inne ustawienia serwera proxy w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="13c3f-153">On .NET Framework 2.0 when this value is set to "true", the Internet Explorer proxy settings are not overridden by other proxy settings in the configuration file.</span></span> <span data-ttu-id="13c3f-154">W programie .NET Framework 1.1 ustawienia serwera proxy programu Internet Explorer, może zostać przesłonięta przez inne ustawienia serwera proxy w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="13c3f-154">On .NET Framework 1.1, the Internet Explorer proxy settings can be overridden by other proxy settings in the configuration file.</span></span><br /><br /> <span data-ttu-id="13c3f-155">Jeśli ta wartość wynosi "false" lub nie zestawu, a następnie ustawienia serwera proxy statycznych może być określony w konfiguracji i zastąpią ustawienia serwera proxy programu Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="13c3f-155">If this value is "false" or not set, then the static proxy settings can be specified in the configuration and will override the Internet Explorer proxy settings.</span></span> <span data-ttu-id="13c3f-156">Ta wartość również musi mieć ustawioną "wartość false" lub nie została ustawiona dla adaptacyjną proxy włączenia.</span><span class="sxs-lookup"><span data-stu-id="13c3f-156">This value must also be set to "false" or not set for adaptive proxies to be enabled.</span></span>|  
  
 <span data-ttu-id="13c3f-157">Poniższy przykład przedstawia konfiguracji typowych statycznych serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="13c3f-157">The following example shows a typical static proxy configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="13c3f-158">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="13c3f-158">See Also</span></span>  
 <xref:System.Net.WebProxy>  
 <xref:System.Net.GlobalProxySelection>  
 [<span data-ttu-id="13c3f-159">Automatyczne wykrywanie serwera proxy</span><span class="sxs-lookup"><span data-stu-id="13c3f-159">Automatic Proxy Detection</span></span>](../../../docs/framework/network-programming/automatic-proxy-detection.md)
