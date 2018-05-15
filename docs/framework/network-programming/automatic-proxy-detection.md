---
title: Wykrywanie serwera Proxy
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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: acb14d8785a01d98d56233b8eb942f9bc4675f63
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="automatic-proxy-detection"></a><span data-ttu-id="f7e54-102">Wykrywanie serwera Proxy</span><span class="sxs-lookup"><span data-stu-id="f7e54-102">Automatic Proxy Detection</span></span>
<span data-ttu-id="f7e54-103">Wykrywanie serwera proxy jest procesem, za pomocą którego serwer proxy sieci Web jest identyfikowane przez system i używane do wysyłania żądania w imieniu klienta.</span><span class="sxs-lookup"><span data-stu-id="f7e54-103">Automatic proxy detection is a process by which a Web proxy server is identified by the system and used to send requests on behalf of the client.</span></span> <span data-ttu-id="f7e54-104">Ta funkcja jest nazywana autowykrywania serwera Proxy sieci Web (WPAD).</span><span class="sxs-lookup"><span data-stu-id="f7e54-104">This feature is also known as Web Proxy Auto-Discovery (WPAD).</span></span> <span data-ttu-id="f7e54-105">Gdy wykrywanie serwera proxy jest włączone, system próbuje zlokalizować skrypt konfiguracji serwera proxy, który jest odpowiedzialny za zwrócenie zestaw serwerów proxy, które mogą być używane dla żądania.</span><span class="sxs-lookup"><span data-stu-id="f7e54-105">When automatic proxy detection is enabled, the system attempts to locate a proxy configuration script that is responsible for returning the set of proxies that can be used for the request.</span></span> <span data-ttu-id="f7e54-106">Jeśli skrypt konfiguracji serwera proxy zostanie znaleziony, skrypt pobrany, skompilowany i uruchom na komputerze lokalnym, jeśli informacje o serwerze proxy, strumień żądań lub odpowiedzi jest uzyskiwany dla żądania, która używa <xref:System.Net.WebProxy> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="f7e54-106">If the proxy configuration script is found, the script is downloaded, compiled, and run on the local computer when proxy information, the request stream, or the response is obtained for a request that uses a <xref:System.Net.WebProxy> instance.</span></span>  
  
 <span data-ttu-id="f7e54-107">Wykrywanie serwera proxy jest wykonywane przez <xref:System.Net.WebProxy> klasy i można stosować ustawienia na poziomie żądania, ustawień w plikach konfiguracji i ustawienia określone przy użyciu programu Internet Explorer **sieci lokalnej (LAN)** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="f7e54-107">Automatic proxy detection is performed by the <xref:System.Net.WebProxy> class and can employ request-level settings, settings in configuration files, and settings specified using the Internet Explorer **Local Area Network (LAN)** dialog box.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f7e54-108">Można wyświetlić programu Internet Explorer **ustawienia sieci lokalnej (LAN)** okno dialogowe, wybierając **narzędzia** z menu głównego w programie Internet Explorer, a następnie wybierając **Opcje internetowe**.</span><span class="sxs-lookup"><span data-stu-id="f7e54-108">You can display the Internet Explorer **Local Area Network (LAN) Settings** dialog box by selecting **Tools** from the Internet Explorer main menu and then selecting **Internet Options**.</span></span> <span data-ttu-id="f7e54-109">Następnie wybierz pozycję **połączeń** , a następnie kliknij pozycję **ustawienia sieci LAN**.</span><span class="sxs-lookup"><span data-stu-id="f7e54-109">Next, select the **Connections** tab, and click **LAN Settings**.</span></span>  
  
 <span data-ttu-id="f7e54-110">Po włączeniu serwera proxy automatycznego wykrywania <xref:System.Net.WebProxy> klasa próbuje zlokalizować skrypt konfiguracji serwera proxy w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="f7e54-110">When automatic proxy detection is enabled, the <xref:System.Net.WebProxy> class attempts to locate the proxy configuration script as follows:</span></span>  
  
1.  <span data-ttu-id="f7e54-111">WinINet `InternetQueryOption` funkcja jest używana do lokalizowania ostatnio wykrytych przez program Internet Explorer skryptu konfiguracji serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="f7e54-111">The WinINet `InternetQueryOption` function is used to locate the proxy configuration script most recently detected by Internet Explorer.</span></span>  
  
2.  <span data-ttu-id="f7e54-112">Jeśli skrypt nie jest umieszczony <xref:System.Net.WebProxy> klasa korzysta z konfiguracji protokołu DHCP (Dynamic Host) można znaleźć skryptu.</span><span class="sxs-lookup"><span data-stu-id="f7e54-112">If the script is not located, the <xref:System.Net.WebProxy> class uses the Dynamic Host Configuration Protocol (DHCP) to locate the script.</span></span> <span data-ttu-id="f7e54-113">Serwer DHCP może odpowiadać lokalizacji (nazwa hosta) za pomocą skryptu lub do pełnego adresu URL skryptu.</span><span class="sxs-lookup"><span data-stu-id="f7e54-113">The DHCP server can respond either with the location (host name) of the script or with the full URL for the script.</span></span>  
  
3.  <span data-ttu-id="f7e54-114">Jeśli DHCP nie będzie rozpoznawał hosta WPAD, DNS zostanie zapytany o hoście WPAD, jako jego nazwę lub alias.</span><span class="sxs-lookup"><span data-stu-id="f7e54-114">If DHCP does not identify the WPAD host, DNS is queried for a host with WPAD as its name or alias.</span></span>  
  
4.  <span data-ttu-id="f7e54-115">Jeśli nie określono hosta i lokalizacja skryptu konfiguracji serwera proxy jest określony przez ustawienia sieci LAN programu Internet Explorer lub plik konfiguracji, ta lokalizacja jest używana.</span><span class="sxs-lookup"><span data-stu-id="f7e54-115">If the host is not identified and the location of a proxy configuration script is specified by the Internet Explorer LAN settings or a configuration file, this location is used.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f7e54-116">Aplikacje uruchomione jako usługi NT lub w ramach programu ASP.NET Użyj ustawień serwera proxy programu Internet Explorer (jeśli jest dostępny) wywoływanie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f7e54-116">Applications running as an NT Service or as part of ASP.NET use the Internet Explorer proxy server settings (if available) of the invoking user.</span></span> <span data-ttu-id="f7e54-117">Te ustawienia mogą nie być dostępne dla wszystkich aplikacji usługi.</span><span class="sxs-lookup"><span data-stu-id="f7e54-117">These settings may not be available for all service applications.</span></span>  
  
 <span data-ttu-id="f7e54-118">Serwery proxy są skonfigurowane na podstawie wstępnie zdefiniowane na połączenie.</span><span class="sxs-lookup"><span data-stu-id="f7e54-118">Proxies are configured on a per-connectoid basis.</span></span> <span data-ttu-id="f7e54-119">Identyfikator elementu w oknie dialogowym połączenia sieciowe i może być urządzenie sieci fizycznej (modemu lub karty sieciowej Ethernet) lub interfejsu wirtualnego (na przykład uruchomiony za pośrednictwem urządzenia sieciowego połączenia sieci VPN).</span><span class="sxs-lookup"><span data-stu-id="f7e54-119">A connectoid is an item in the network connection dialog, and can be a physical network device (a modem or Ethernet card) or a virtual interface (such as a VPN connection running over a network device).</span></span> <span data-ttu-id="f7e54-120">Podczas zmiany identyfikator (na przykład połączenia bezprzewodowego zmiany włączono punkt dostępu lub sieci VPN), ponownie uruchom algorytmu wykrywania serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="f7e54-120">When a connectoid changes (for example, a wireless connection changes an access point, or a VPN is enabled), the proxy detection algorithm is run again.</span></span>  
  
 <span data-ttu-id="f7e54-121">Domyślnie ustawienia serwera proxy programu Internet Explorer są używane do wykrywania serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="f7e54-121">By default, the Internet Explorer proxy settings are used to detect the proxy.</span></span> <span data-ttu-id="f7e54-122">Jeśli aplikacja jest uruchomiona na koncie podejścia nieinterakcyjnego (bez wygodny sposób, aby skonfigurować ustawienia serwera proxy programu Internet Explorer) lub jeśli chcesz użyć ustawień serwera proxy jest inne niż ustawienia programu Internet Explorer, tworząc plik konfiguracji z możnaskonfigurowaćserwerproxy[ \<defaultProxy — > elementu (ustawienia sieciowe)](../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md) i [ \<proxy > elementu (ustawienia sieciowe)](../../../docs/framework/configure-apps/file-schema/network/proxy-element-network-settings.md) elementy zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="f7e54-122">If your application is running under a non-interactive account (without a convenient way to configure IE proxy settings), or if you want to use proxy settings different than the IE settings, you can configure your proxy by creating a configuration file with the [\<defaultProxy> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md) and [\<proxy> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/proxy-element-network-settings.md) elements defined.</span></span>  
  
 <span data-ttu-id="f7e54-123">Żądań, które możesz utworzyć, można wyłączyć wykrywanie serwera proxy na poziomie żądania za pomocą wartości null <xref:System.Net.WebRequest.Proxy%2A> z żądaniem, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="f7e54-123">For requests that you create, you can disable automatic proxy detection at the request level by using a null <xref:System.Net.WebRequest.Proxy%2A> with your request, as shown in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="f7e54-124">Żądania bez serwera proxy przy użyciu domenę aplikacji domyślny serwer proxy, który jest dostępny w <xref:System.Net.WebRequest.DefaultWebProxy%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="f7e54-124">Requests that do not have a proxy use your application domain's default proxy, which is available in the <xref:System.Net.WebRequest.DefaultWebProxy%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7e54-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f7e54-125">See Also</span></span>  
 <xref:System.Net.WebProxy>  
 <xref:System.Net.WebRequest>  
 [<span data-ttu-id="f7e54-126">\<system.Net > (ustawienia sieciowe) — Element</span><span class="sxs-lookup"><span data-stu-id="f7e54-126">\<system.Net> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)
