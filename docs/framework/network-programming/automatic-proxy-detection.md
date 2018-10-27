---
title: Automatyczne wykrywanie serwera Proxy
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- automatic proxy detections
- Web Proxy Auto-Discovery
- Web proxy
- detecting proxies automatically
- WebProxy class, automatic proxy detections
- proxies, automatically detecting
- network
- WPAD (Web Proxy Auto-Discovery)
ms.assetid: fcd9c3bd-93de-4c92-8ff3-837327ad18de
ms.openlocfilehash: 3a59347c3fcd72f68ee2ae07ccc638ec43021a3b
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188511"
---
# <a name="automatic-proxy-detection"></a><span data-ttu-id="14da1-102">Automatyczne wykrywanie serwera Proxy</span><span class="sxs-lookup"><span data-stu-id="14da1-102">Automatic Proxy Detection</span></span>
<span data-ttu-id="14da1-103">Automatyczne wykrywanie serwera proxy jest procesem, za pomocą którego serwer proxy sieci Web jest identyfikowane przez system i używane do wysyłania żądania w imieniu klienta.</span><span class="sxs-lookup"><span data-stu-id="14da1-103">Automatic proxy detection is a process by which a Web proxy server is identified by the system and used to send requests on behalf of the client.</span></span> <span data-ttu-id="14da1-104">Ta funkcja jest również znana jako funkcja autowykrywania serwera Proxy sieci Web (WPAD).</span><span class="sxs-lookup"><span data-stu-id="14da1-104">This feature is also known as Web Proxy Auto-Discovery (WPAD).</span></span> <span data-ttu-id="14da1-105">Gdy automatyczne wykrywanie serwera proxy jest włączone, system próbuje zlokalizować skryptu konfiguracji serwera proxy, która jest odpowiedzialna za zwrócenie zestaw serwerów proxy, które mogą być używane dla żądania.</span><span class="sxs-lookup"><span data-stu-id="14da1-105">When automatic proxy detection is enabled, the system attempts to locate a proxy configuration script that is responsible for returning the set of proxies that can be used for the request.</span></span> <span data-ttu-id="14da1-106">Jeśli zostanie znaleziony skryptu konfiguracji serwera proxy, skrypt pobrany, skompilowany i uruchom na komputerze lokalnym, jeśli informacje o serwerze proxy, strumienia żądania lub odpowiedzi jest uzyskiwany na żądanie, który używa <xref:System.Net.WebProxy> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="14da1-106">If the proxy configuration script is found, the script is downloaded, compiled, and run on the local computer when proxy information, the request stream, or the response is obtained for a request that uses a <xref:System.Net.WebProxy> instance.</span></span>  
  
 <span data-ttu-id="14da1-107">Automatyczne wykrywanie serwera proxy odbywa się przez <xref:System.Net.WebProxy> klasy i mogą stosować ustawienia na poziomie żądania, ustawienia w plikach konfiguracji i ustawień określonych w programie Internet Explorer **sieci lokalnej (LAN)** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="14da1-107">Automatic proxy detection is performed by the <xref:System.Net.WebProxy> class and can employ request-level settings, settings in configuration files, and settings specified using the Internet Explorer **Local Area Network (LAN)** dialog box.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="14da1-108">Możesz wyświetlić programu Internet Explorer **ustawienia sieci lokalnej (LAN)** okno dialogowe, wybierając **narzędzia** z menu głównego w programie Internet Explorer, a następnie wybierając pozycję **Opcje internetowe**.</span><span class="sxs-lookup"><span data-stu-id="14da1-108">You can display the Internet Explorer **Local Area Network (LAN) Settings** dialog box by selecting **Tools** from the Internet Explorer main menu and then selecting **Internet Options**.</span></span> <span data-ttu-id="14da1-109">Następnie wybierz pozycję **połączeń** kartę, a następnie kliknij przycisk **ustawienia sieci LAN**.</span><span class="sxs-lookup"><span data-stu-id="14da1-109">Next, select the **Connections** tab, and click **LAN Settings**.</span></span>  
  
 <span data-ttu-id="14da1-110">Gdy jest włączone automatyczne wykrywanie serwera proxy, <xref:System.Net.WebProxy> klasy próbuje zlokalizować skryptu konfiguracji serwera proxy w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="14da1-110">When automatic proxy detection is enabled, the <xref:System.Net.WebProxy> class attempts to locate the proxy configuration script as follows:</span></span>  
  
1.  <span data-ttu-id="14da1-111">WinINet `InternetQueryOption` funkcja jest używana do lokalizowania skryptu konfiguracji serwera proxy ostatnio wykrytych przez program Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="14da1-111">The WinINet `InternetQueryOption` function is used to locate the proxy configuration script most recently detected by Internet Explorer.</span></span>  
  
2.  <span data-ttu-id="14da1-112">Jeśli skrypt nie jest umieszczony <xref:System.Net.WebProxy> klasa używa DHCP Dynamic Host Configuration Protocol (), aby zlokalizować scenariusza.</span><span class="sxs-lookup"><span data-stu-id="14da1-112">If the script is not located, the <xref:System.Net.WebProxy> class uses the Dynamic Host Configuration Protocol (DHCP) to locate the script.</span></span> <span data-ttu-id="14da1-113">Serwer DHCP może odpowiadać za pomocą lokalizacji (nazwa hosta), skryptu lub pełny adres URL skryptu.</span><span class="sxs-lookup"><span data-stu-id="14da1-113">The DHCP server can respond either with the location (host name) of the script or with the full URL for the script.</span></span>  
  
3.  <span data-ttu-id="14da1-114">Jeśli DHCP nie wskazuje hosta WPAD, DNS zostaje przesłane zapytanie do hosta za pomocą WPAD jako jego nazwę lub alias.</span><span class="sxs-lookup"><span data-stu-id="14da1-114">If DHCP does not identify the WPAD host, DNS is queried for a host with WPAD as its name or alias.</span></span>  
  
4.  <span data-ttu-id="14da1-115">Ta lokalizacja jest używana, jeśli host nie zostanie zidentyfikowany, lokalizacja skryptu konfiguracji serwera proxy jest określony przez ustawienia Internet Explorer w sieci LAN lub pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="14da1-115">If the host is not identified and the location of a proxy configuration script is specified by the Internet Explorer LAN settings or a configuration file, this location is used.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="14da1-116">Aplikacje działające jako usługi NT lub w ramach programu ASP.NET Użyj ustawień serwera proxy programu Internet Explorer (jeśli jest dostępny) użytkownika, które powinny być przekazywane wywołującemu.</span><span class="sxs-lookup"><span data-stu-id="14da1-116">Applications running as an NT Service or as part of ASP.NET use the Internet Explorer proxy server settings (if available) of the invoking user.</span></span> <span data-ttu-id="14da1-117">Te ustawienia mogą być dostępne dla wszystkich aplikacji usługi.</span><span class="sxs-lookup"><span data-stu-id="14da1-117">These settings may not be available for all service applications.</span></span>  
  
 <span data-ttu-id="14da1-118">Serwery proxy są skonfigurowane na podstawie wstępnie zdefiniowane na połączenie.</span><span class="sxs-lookup"><span data-stu-id="14da1-118">Proxies are configured on a per-connectoid basis.</span></span> <span data-ttu-id="14da1-119">Identyfikator jest element w oknie dialogowym połączenia sieciowe i może być urządzeniem sieci fizycznej (modem lub karta Ethernet) lub interfejsu wirtualnego (np. połączenia sieci VPN, uruchamiania przez urządzenie sieciowe).</span><span class="sxs-lookup"><span data-stu-id="14da1-119">A connectoid is an item in the network connection dialog, and can be a physical network device (a modem or Ethernet card) or a virtual interface (such as a VPN connection running over a network device).</span></span> <span data-ttu-id="14da1-120">Gdy identyfikator ulegnie zmianie (na przykład połączenia bezprzewodowego zmiany punktu dostępu lub sieci VPN jest włączona), algorytm wykrywania serwera proxy jest uruchamiany ponownie.</span><span class="sxs-lookup"><span data-stu-id="14da1-120">When a connectoid changes (for example, a wireless connection changes an access point, or a VPN is enabled), the proxy detection algorithm is run again.</span></span>  
  
 <span data-ttu-id="14da1-121">Domyślnie ustawienia serwera proxy programu Internet Explorer są używane do wykrywania serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="14da1-121">By default, the Internet Explorer proxy settings are used to detect the proxy.</span></span> <span data-ttu-id="14da1-122">Jeśli aplikacja jest uruchomiona w ramach konta nieinterakcyjnych (bez wygodny sposób, aby skonfigurować ustawienia serwera proxy programu Internet Explorer) lub jeśli chcesz używać ustawień serwera proxy są inne niż ustawienia programu Internet Explorer, można skonfigurować serwer proxy, tworząc plik konfiguracji o [ \<defaultProxy >, Element (ustawienia sieci)](../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md) i [ \<proxy >, Element (ustawienia sieci)](../../../docs/framework/configure-apps/file-schema/network/proxy-element-network-settings.md) elementy zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="14da1-122">If your application is running under a non-interactive account (without a convenient way to configure IE proxy settings), or if you want to use proxy settings different than the IE settings, you can configure your proxy by creating a configuration file with the [\<defaultProxy> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md) and [\<proxy> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/proxy-element-network-settings.md) elements defined.</span></span>  
  
 <span data-ttu-id="14da1-123">Dla żądań, które tworzysz, możesz wyłączyć automatyczne wykrywanie serwera proxy na poziomie żądania przy użyciu wartości null <xref:System.Net.WebRequest.Proxy%2A> z żądaniem, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="14da1-123">For requests that you create, you can disable automatic proxy detection at the request level by using a null <xref:System.Net.WebRequest.Proxy%2A> with your request, as shown in the following code example.</span></span>  
  
```csharp  
public static void DisableForMyRequest (Uri resource)  
{  
    WebRequest request = WebRequest.Create (resource);  
    request.Proxy = null;  
    WebResponse response = request.GetResponse ();  
}  
```  
  
```vb  
Public Shared Sub DisableForMyRequest(ByVal resource As Uri)  
    Dim request As WebRequest = WebRequest.Create(resource)  
    request.Proxy = Nothing  
    Dim response As WebResponse = request.GetResponse()  
    End Sub   
```  
  
 <span data-ttu-id="14da1-124">Żądania, które nie mają serwer proxy przy użyciu domenę aplikacji domyślny serwer proxy, który jest dostępny w <xref:System.Net.WebRequest.DefaultWebProxy%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="14da1-124">Requests that do not have a proxy use your application domain's default proxy, which is available in the <xref:System.Net.WebRequest.DefaultWebProxy%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14da1-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="14da1-125">See Also</span></span>  
 <xref:System.Net.WebProxy>  
 <xref:System.Net.WebRequest>  
 [<span data-ttu-id="14da1-126">\<przestrzeni nazw system.Net >, Element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="14da1-126">\<system.Net> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)
