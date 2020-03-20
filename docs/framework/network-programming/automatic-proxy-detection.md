---
title: Automatyczne wykrywanie serwera proxy
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
ms.openlocfilehash: 4c5bc9e0efb39032d388d141e8bccf3e520ebd45
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180899"
---
# <a name="automatic-proxy-detection"></a><span data-ttu-id="d743f-102">Automatyczne wykrywanie serwera proxy</span><span class="sxs-lookup"><span data-stu-id="d743f-102">Automatic Proxy Detection</span></span>
<span data-ttu-id="d743f-103">Automatyczne wykrywanie serwera proxy jest procesem, w którym serwer proxy sieci Web jest identyfikowany przez system i używany do wysyłania żądań w imieniu klienta.</span><span class="sxs-lookup"><span data-stu-id="d743f-103">Automatic proxy detection is a process by which a Web proxy server is identified by the system and used to send requests on behalf of the client.</span></span> <span data-ttu-id="d743f-104">Ta funkcja jest również znana jako Auto-Discovery serwera proxy sieci Web (WPAD).</span><span class="sxs-lookup"><span data-stu-id="d743f-104">This feature is also known as Web Proxy Auto-Discovery (WPAD).</span></span> <span data-ttu-id="d743f-105">Gdy automatyczne wykrywanie serwera proxy jest włączone, system próbuje zlokalizować skrypt konfiguracji serwera proxy, który jest odpowiedzialny za zwracanie zestawu serwerów proxy, które mogą być używane dla żądania.</span><span class="sxs-lookup"><span data-stu-id="d743f-105">When automatic proxy detection is enabled, the system attempts to locate a proxy configuration script that is responsible for returning the set of proxies that can be used for the request.</span></span> <span data-ttu-id="d743f-106">Jeśli zostanie znaleziony skrypt konfiguracji serwera proxy, skrypt jest pobierany, kompilowany i uruchamiany na komputerze lokalnym, gdy informacje <xref:System.Net.WebProxy> o serwerze proxy, strumień żądania lub odpowiedź jest uzyskiwana dla żądania, które używa wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="d743f-106">If the proxy configuration script is found, the script is downloaded, compiled, and run on the local computer when proxy information, the request stream, or the response is obtained for a request that uses a <xref:System.Net.WebProxy> instance.</span></span>  
  
 <span data-ttu-id="d743f-107">Automatyczne wykrywanie serwera <xref:System.Net.WebProxy> proxy jest wykonywane przez klasę i może stosować ustawienia na poziomie żądania, ustawienia w plikach konfiguracyjnych i ustawienia określone za pomocą okna dialogowego Sieć lokalna programu Internet Explorer **(LAN).**</span><span class="sxs-lookup"><span data-stu-id="d743f-107">Automatic proxy detection is performed by the <xref:System.Net.WebProxy> class and can employ request-level settings, settings in configuration files, and settings specified using the Internet Explorer **Local Area Network (LAN)** dialog box.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d743f-108">Okno dialogowe Ustawienia sieci lokalnej programu Internet Explorer **(LAN),** wybierając polecenie **Narzędzia** z menu głównego programu Internet Explorer, a następnie wybierając pozycję **Opcje internetowe**.</span><span class="sxs-lookup"><span data-stu-id="d743f-108">You can display the Internet Explorer **Local Area Network (LAN) Settings** dialog box by selecting **Tools** from the Internet Explorer main menu and then selecting **Internet Options**.</span></span> <span data-ttu-id="d743f-109">Następnie wybierz kartę **Połączenia** i kliknij pozycję **Ustawienia sieci LAN**.</span><span class="sxs-lookup"><span data-stu-id="d743f-109">Next, select the **Connections** tab, and click **LAN Settings**.</span></span>  
  
 <span data-ttu-id="d743f-110">Gdy automatyczne wykrywanie serwera <xref:System.Net.WebProxy> proxy jest włączone, klasa próbuje zlokalizować skrypt konfiguracji serwera proxy w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="d743f-110">When automatic proxy detection is enabled, the <xref:System.Net.WebProxy> class attempts to locate the proxy configuration script as follows:</span></span>  
  
1. <span data-ttu-id="d743f-111">Funkcja WinINet `InternetQueryOption` służy do lokalizowania skryptu konfiguracji serwera proxy ostatnio wykrytego przez program Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="d743f-111">The WinINet `InternetQueryOption` function is used to locate the proxy configuration script most recently detected by Internet Explorer.</span></span>  
  
2. <span data-ttu-id="d743f-112">Jeśli skrypt nie znajduje <xref:System.Net.WebProxy> się, klasa używa protokołu DHCP (Dynamic Host Configuration Protocol) do zlokalizowania skryptu.</span><span class="sxs-lookup"><span data-stu-id="d743f-112">If the script is not located, the <xref:System.Net.WebProxy> class uses the Dynamic Host Configuration Protocol (DHCP) to locate the script.</span></span> <span data-ttu-id="d743f-113">Serwer DHCP może odpowiedzieć lokalizacją (nazwą hosta) skryptu lub pełnym adresem URL skryptu.</span><span class="sxs-lookup"><span data-stu-id="d743f-113">The DHCP server can respond either with the location (host name) of the script or with the full URL for the script.</span></span>  
  
3. <span data-ttu-id="d743f-114">Jeśli usługa DHCP nie identyfikuje hosta WPAD, usługa DNS jest wyszukiwana w przypadku hosta z programem WPAD jako jego nazwą lub aliasem.</span><span class="sxs-lookup"><span data-stu-id="d743f-114">If DHCP does not identify the WPAD host, DNS is queried for a host with WPAD as its name or alias.</span></span>  
  
4. <span data-ttu-id="d743f-115">Jeśli host nie został zidentyfikowany, a lokalizacja skryptu konfiguracji serwera proxy jest określona przez ustawienia sieci LAN programu Internet Explorer lub plik konfiguracyjny, ta lokalizacja jest używana.</span><span class="sxs-lookup"><span data-stu-id="d743f-115">If the host is not identified and the location of a proxy configuration script is specified by the Internet Explorer LAN settings or a configuration file, this location is used.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d743f-116">Aplikacje działające jako usługa NT lub w ramach ASP.NET używać ustawień serwera proxy programu Internet Explorer (jeśli są dostępne) wywoływanego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d743f-116">Applications running as an NT Service or as part of ASP.NET use the Internet Explorer proxy server settings (if available) of the invoking user.</span></span> <span data-ttu-id="d743f-117">Te ustawienia mogą nie być dostępne dla wszystkich aplikacji serwisowych.</span><span class="sxs-lookup"><span data-stu-id="d743f-117">These settings may not be available for all service applications.</span></span>  
  
 <span data-ttu-id="d743f-118">Serwery proxy są konfigurowane na podstawie na connectoid.</span><span class="sxs-lookup"><span data-stu-id="d743f-118">Proxies are configured on a per-connectoid basis.</span></span> <span data-ttu-id="d743f-119">Connectoid jest elementem w oknie dialogowym połączenia sieciowego i może być fizycznym urządzeniem sieciowym (modem lub kartą Ethernet) lub interfejsem wirtualnym (takim jak połączenie sieci VPN działające za pośrednictwem urządzenia sieciowego).</span><span class="sxs-lookup"><span data-stu-id="d743f-119">A connectoid is an item in the network connection dialog, and can be a physical network device (a modem or Ethernet card) or a virtual interface (such as a VPN connection running over a network device).</span></span> <span data-ttu-id="d743f-120">Po zmianie connectoid (na przykład połączenie bezprzewodowe zmienia punkt dostępu lub vpn jest włączony), algorytm wykrywania serwera proxy jest uruchamiany ponownie.</span><span class="sxs-lookup"><span data-stu-id="d743f-120">When a connectoid changes (for example, a wireless connection changes an access point, or a VPN is enabled), the proxy detection algorithm is run again.</span></span>  
  
 <span data-ttu-id="d743f-121">Domyślnie ustawienia serwera proxy programu Internet Explorer są używane do wykrywania serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="d743f-121">By default, the Internet Explorer proxy settings are used to detect the proxy.</span></span> <span data-ttu-id="d743f-122">Jeśli aplikacja działa na koncie nieinterakcyjnym (bez wygodnego sposobu konfigurowania ustawień serwera proxy IE) lub jeśli chcesz używać ustawień serwera proxy innych niż ustawienia IE, możesz skonfigurować serwer proxy, tworząc plik konfiguracyjny z zdefiniowanymi elementami [ \<defaultProxy> Element (Ustawienia sieciowe)](../configure-apps/file-schema/network/defaultproxy-element-network-settings.md) i [ \<elementem> proxy (Ustawienia sieci).](../configure-apps/file-schema/network/proxy-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="d743f-122">If your application is running under a non-interactive account (without a convenient way to configure IE proxy settings), or if you want to use proxy settings different than the IE settings, you can configure your proxy by creating a configuration file with the [\<defaultProxy> Element (Network Settings)](../configure-apps/file-schema/network/defaultproxy-element-network-settings.md) and [\<proxy> Element (Network Settings)](../configure-apps/file-schema/network/proxy-element-network-settings.md) elements defined.</span></span>  
  
 <span data-ttu-id="d743f-123">W przypadku żądań, które tworzysz, można wyłączyć automatyczne <xref:System.Net.WebRequest.Proxy%2A> wykrywanie serwera proxy na poziomie żądania przy użyciu null z żądaniem, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="d743f-123">For requests that you create, you can disable automatic proxy detection at the request level by using a null <xref:System.Net.WebRequest.Proxy%2A> with your request, as shown in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="d743f-124">Żądania, które nie mają serwera proxy, używają domyślnego serwera <xref:System.Net.WebRequest.DefaultWebProxy%2A> proxy domeny aplikacji, który jest dostępny we właściwości.</span><span class="sxs-lookup"><span data-stu-id="d743f-124">Requests that do not have a proxy use your application domain's default proxy, which is available in the <xref:System.Net.WebRequest.DefaultWebProxy%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d743f-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d743f-125">See also</span></span>

- <xref:System.Net.WebProxy>
- <xref:System.Net.WebRequest>
- [<span data-ttu-id="d743f-126">\<system.Net element> (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="d743f-126">\<system.Net> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/system-net-element-network-settings.md)
