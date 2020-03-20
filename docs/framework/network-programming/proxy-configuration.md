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
ms.openlocfilehash: 1fbfe25b90e810ff96924a2341582ff3f5ee5e5d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047356"
---
# <a name="proxy-configuration"></a><span data-ttu-id="5204c-102">Konfiguracja serwera proxy</span><span class="sxs-lookup"><span data-stu-id="5204c-102">Proxy Configuration</span></span>
<span data-ttu-id="5204c-103">Serwer proxy obsługuje żądania klientów dotyczące zasobów.</span><span class="sxs-lookup"><span data-stu-id="5204c-103">A proxy server handles client requests for resources.</span></span> <span data-ttu-id="5204c-104">Serwer proxy może zwrócić żądany zasób z pamięci podręcznej lub przesłać je dalej do serwera, na którym znajduje się zasób.</span><span class="sxs-lookup"><span data-stu-id="5204c-104">A proxy can return a requested resource from its cache or forward the request to the server where the resource resides.</span></span> <span data-ttu-id="5204c-105">Serwery proxy mogą zwiększyć wydajność sieci, zmniejszając liczbę żądań wysyłanych do serwerów zdalnych.</span><span class="sxs-lookup"><span data-stu-id="5204c-105">Proxies can improve network performance by reducing the number of requests sent to remote servers.</span></span> <span data-ttu-id="5204c-106">Serwery proxy mogą być również używane do ograniczania dostępu do zasobów.</span><span class="sxs-lookup"><span data-stu-id="5204c-106">Proxies can also be used to restrict access to resources.</span></span>  
  
## <a name="adaptive-proxies"></a><span data-ttu-id="5204c-107">Adaptacyjne serwery proxy</span><span class="sxs-lookup"><span data-stu-id="5204c-107">Adaptive Proxies</span></span>  
 <span data-ttu-id="5204c-108">W .NET Framework serwery proxy są dostępne w dwóch odmianach: adaptacyjnej i statycznej.</span><span class="sxs-lookup"><span data-stu-id="5204c-108">In the .NET Framework, proxies come in two varieties: adaptive and static.</span></span> <span data-ttu-id="5204c-109">Adaptacyjne serwery proxy dostosowują swoje ustawienia po zmianie konfiguracji sieci.</span><span class="sxs-lookup"><span data-stu-id="5204c-109">Adaptive proxies adjust their settings when the network configuration changes.</span></span> <span data-ttu-id="5204c-110">Na przykład jeśli użytkownik komputera przenośnego uruchamia połączenie telefoniczne z siecią, adaptacyjny serwer proxy rozpozna tę zmianę, odnajdzie i uruchomi nowy skrypt konfiguracyjny oraz odpowiednio dostosuje jego ustawienia.</span><span class="sxs-lookup"><span data-stu-id="5204c-110">For example, if a laptop user starts a dialup network connection, an adaptive proxy would recognize this change, discover and run its new configuration script, and adjust its settings appropriately.</span></span>  
  
 <span data-ttu-id="5204c-111">Adaptacyjne serwery proxy są konfigurowane za pomocą skryptu konfiguracyjnego (patrz [Automatyczne wykrywanie serwera proxy).](automatic-proxy-detection.md)</span><span class="sxs-lookup"><span data-stu-id="5204c-111">Adaptive proxies are configured by a configuration script (see [Automatic Proxy Detection](automatic-proxy-detection.md)).</span></span> <span data-ttu-id="5204c-112">Skrypt generuje zestaw protokołów aplikacji i serwer proxy dla każdego protokołu.</span><span class="sxs-lookup"><span data-stu-id="5204c-112">The script generates a set of application protocols and a proxy for each protocol.</span></span>  
  
 <span data-ttu-id="5204c-113">Zmiany w środowisku sieciowym mogą wymagać, aby system używał nowego zestawu serwerów proxy.</span><span class="sxs-lookup"><span data-stu-id="5204c-113">Changes in the network environment may require that the system use a new set of proxies.</span></span> <span data-ttu-id="5204c-114">Jeśli połączenie sieciowe ustępuje lub zostanie zainicjowane nowe połączenie sieciowe, system musi odnajdować odpowiednie źródło skryptu konfiguracyjnego w nowym środowisku i uruchomić nowy skrypt.</span><span class="sxs-lookup"><span data-stu-id="5204c-114">If a network connection goes down or a new network connection is initialized, the system must discover the appropriate source of the configuration script in the new environment and run the new script.</span></span>  
  
 <span data-ttu-id="5204c-115">Można użyć `usesystemdefault` atrybutu [`<proxy>`](../configure-apps/file-schema/network/proxy-element-network-settings.md) elementu w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="5204c-115">You can use the `usesystemdefault` attribute of the [`<proxy>`](../configure-apps/file-schema/network/proxy-element-network-settings.md) element in your configuration file.</span></span> <span data-ttu-id="5204c-116">Atrybut `usesystemdefault` określa, czy statyczne ustawienia serwera proxy (adres serwera proxy, lista pomijania i obejście na lokalnym) powinny być odczytywane z ustawień serwera proxy programu Internet Explorer dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5204c-116">The `usesystemdefault` attribute controls whether the static proxy settings (proxy address, bypass list, and bypass on local) should be read from the Internet Explorer proxy settings for the user.</span></span> <span data-ttu-id="5204c-117">Jeśli ta wartość `true`jest ustawiona na , zostaną użyte statyczne ustawienia serwera proxy z programu Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="5204c-117">If this value is set to `true`, the static proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="5204c-118">Jeśli ta `false` wartość jest lub nie jest ustawiona, statyczne ustawienia serwera proxy można określić w konfiguracji i zastąpią ustawienia serwera proxy programu Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="5204c-118">If this value is `false` or not set, the static proxy settings can be specified in the configuration and will override the Internet Explorer proxy settings.</span></span> <span data-ttu-id="5204c-119">Wartość ta musi być `false` również ustawiona na lub nie ustawiona dla serwerów proxy adaptacyjnych, które mają być włączone.</span><span class="sxs-lookup"><span data-stu-id="5204c-119">This value must also be set to `false` or not set for adaptive proxies to be enabled.</span></span>  
  
 <span data-ttu-id="5204c-120">W poniższym przykładzie przedstawiono typową adaptacyjną konfigurację serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="5204c-120">The following example shows a typical adaptive proxy configuration.</span></span>  
  
```xml  
<system.net>  
    <defaultProxy>  
      <proxy usesystemdefault="false" />
    </defaultProxy>  
</system.net>  
```  
  
## <a name="static-proxies"></a><span data-ttu-id="5204c-121">Statyczne serwery proxy</span><span class="sxs-lookup"><span data-stu-id="5204c-121">Static Proxies</span></span>  
 <span data-ttu-id="5204c-122">Statyczne serwery proxy są zwykle konfigurowane jawnie przez aplikację lub gdy plik konfiguracyjny jest wywoływany przez aplikację lub system.</span><span class="sxs-lookup"><span data-stu-id="5204c-122">Static proxies are usually configured explicitly by an application, or when a configuration file is invoked by an application or the system.</span></span> <span data-ttu-id="5204c-123">Statyczne serwery proxy są przydatne w sieciach, w których topologia zmienia się rzadko, na przykład komputer stacjonarny podłączony do sieci firmowej.</span><span class="sxs-lookup"><span data-stu-id="5204c-123">Static proxies are useful in networks in which the topology changes infrequently, such as a desktop computer connected to a corporate network.</span></span>  
  
 <span data-ttu-id="5204c-124">Kilka opcji kontroluje sposób działania statycznego serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="5204c-124">Several options control how a static proxy operates.</span></span> <span data-ttu-id="5204c-125">Można określić następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="5204c-125">You can specify the following:</span></span>  
  
- <span data-ttu-id="5204c-126">Adres serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="5204c-126">The address of the proxy.</span></span>  
  
- <span data-ttu-id="5204c-127">Czy serwer proxy powinien zostać pominięty dla adresów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="5204c-127">Whether the proxy should be bypassed for local addresses.</span></span>  
  
- <span data-ttu-id="5204c-128">Czy serwer proxy powinien zostać pominięty dla zestawu adresów.</span><span class="sxs-lookup"><span data-stu-id="5204c-128">Whether the proxy should be bypassed for a set of addresses.</span></span>  
  
 <span data-ttu-id="5204c-129">W poniższej tabeli przedstawiono opcje konfiguracji statycznego serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="5204c-129">The following table shows the configuration options for a static proxy.</span></span>  
  
|<span data-ttu-id="5204c-130">Ustawienie atrybutu, właściwości lub pliku konfiguracyjnego</span><span class="sxs-lookup"><span data-stu-id="5204c-130">Attribute, property, or configuration file setting</span></span>|<span data-ttu-id="5204c-131">Opis</span><span class="sxs-lookup"><span data-stu-id="5204c-131">Description</span></span>|  
|--------------------------------------------------------|-----------------|  
|<span data-ttu-id="5204c-132">`proxyaddress` lub <xref:System.Net.WebProxy.Address></span><span class="sxs-lookup"><span data-stu-id="5204c-132">`proxyaddress` or <xref:System.Net.WebProxy.Address></span></span>|<span data-ttu-id="5204c-133">Adres serwera proxy do użycia.</span><span class="sxs-lookup"><span data-stu-id="5204c-133">The address of the proxy to use.</span></span>|  
|<span data-ttu-id="5204c-134">`bypassonlocal` lub <xref:System.Net.WebProxy.BypassProxyOnLocal></span><span class="sxs-lookup"><span data-stu-id="5204c-134">`bypassonlocal` or <xref:System.Net.WebProxy.BypassProxyOnLocal></span></span>|<span data-ttu-id="5204c-135">Określa, czy serwer proxy jest pomijany dla adresów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="5204c-135">Controls whether the proxy is bypassed for local addresses.</span></span>|  
|<span data-ttu-id="5204c-136">`bypasslist` lub <xref:System.Net.WebProxy.BypassArrayList></span><span class="sxs-lookup"><span data-stu-id="5204c-136">`bypasslist` or <xref:System.Net.WebProxy.BypassArrayList></span></span>|<span data-ttu-id="5204c-137">W tym artykule opisano, z wyrażeniami regularnymi, zestaw adresów, które pomijają serwer proxy.</span><span class="sxs-lookup"><span data-stu-id="5204c-137">Describes, with regular expressions, a set of addresses that bypass the proxy.</span></span>|  
|`usesystemdefault`|<span data-ttu-id="5204c-138">Określa, czy statyczne ustawienia serwera proxy (adres serwera proxy, lista pomijania i pomijanie na lokalnym) powinny być odczytywane z ustawień serwera proxy programu Internet Explorer dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5204c-138">Controls whether the static proxy settings (proxy address, bypass list, and bypass on local) should be read from the Internet Explorer proxy settings for the user.</span></span> <span data-ttu-id="5204c-139">Jeśli ta wartość `true`jest ustawiona na , zostaną użyte statyczne ustawienia serwera proxy z programu Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="5204c-139">If this value is set to `true`, then the static proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="5204c-140">W programie .NET Framework 2.0, `true`gdy ta wartość jest ustawiona na , ustawienia serwera proxy programu Internet Explorer nie są zastępowane przez inne ustawienia serwera proxy w pliku konfiguracyjnym.</span><span class="sxs-lookup"><span data-stu-id="5204c-140">On .NET Framework 2.0 when this value is set to `true`, the Internet Explorer proxy settings are not overridden by other proxy settings in the configuration file.</span></span> <span data-ttu-id="5204c-141">W programie .NET Framework 1.1 ustawienia serwera proxy programu Internet Explorer można zastąpić innymi ustawieniami serwera proxy w pliku konfiguracyjnym.</span><span class="sxs-lookup"><span data-stu-id="5204c-141">On .NET Framework 1.1, the Internet Explorer proxy settings can be overridden by other proxy settings in the configuration file.</span></span><br /><br /> <span data-ttu-id="5204c-142">Jeśli ta `false` wartość jest lub nie jest ustawiona, wówczas statyczne ustawienia serwera proxy można określić w konfiguracji i zastąpić ustawienia serwera proxy programu Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="5204c-142">If this value is `false` or not set, then the static proxy settings can be specified in the configuration and will override the Internet Explorer proxy settings.</span></span> <span data-ttu-id="5204c-143">Wartość ta musi być `false` również ustawiona na lub nie ustawiona dla serwerów proxy adaptacyjnych, które mają być włączone.</span><span class="sxs-lookup"><span data-stu-id="5204c-143">This value must also be set to `false` or not set for adaptive proxies to be enabled.</span></span>|  
  
 <span data-ttu-id="5204c-144">W poniższym przykładzie przedstawiono typową konfigurację statycznego serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="5204c-144">The following example shows a typical static proxy configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5204c-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5204c-145">See also</span></span>

- <xref:System.Net.WebProxy>
- <xref:System.Net.GlobalProxySelection>
- [<span data-ttu-id="5204c-146">Automatyczne wykrywanie serwera proxy</span><span class="sxs-lookup"><span data-stu-id="5204c-146">Automatic Proxy Detection</span></span>](automatic-proxy-detection.md)
