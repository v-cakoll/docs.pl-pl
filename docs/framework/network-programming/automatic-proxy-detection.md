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
# <a name="automatic-proxy-detection"></a>Wykrywanie serwera Proxy
Wykrywanie serwera proxy jest procesem, za pomocą którego serwer proxy sieci Web jest identyfikowane przez system i używane do wysyłania żądania w imieniu klienta. Ta funkcja jest nazywana autowykrywania serwera Proxy sieci Web (WPAD). Gdy wykrywanie serwera proxy jest włączone, system próbuje zlokalizować skrypt konfiguracji serwera proxy, który jest odpowiedzialny za zwrócenie zestaw serwerów proxy, które mogą być używane dla żądania. Jeśli skrypt konfiguracji serwera proxy zostanie znaleziony, skrypt pobrany, skompilowany i uruchom na komputerze lokalnym, jeśli informacje o serwerze proxy, strumień żądań lub odpowiedzi jest uzyskiwany dla żądania, która używa <xref:System.Net.WebProxy> wystąpienia.  
  
 Wykrywanie serwera proxy jest wykonywane przez <xref:System.Net.WebProxy> klasy i można stosować ustawienia na poziomie żądania, ustawień w plikach konfiguracji i ustawienia określone przy użyciu programu Internet Explorer **sieci lokalnej (LAN)** okno dialogowe.  
  
> [!NOTE]
>  Można wyświetlić programu Internet Explorer **ustawienia sieci lokalnej (LAN)** okno dialogowe, wybierając **narzędzia** z menu głównego w programie Internet Explorer, a następnie wybierając **Opcje internetowe**. Następnie wybierz pozycję **połączeń** , a następnie kliknij pozycję **ustawienia sieci LAN**.  
  
 Po włączeniu serwera proxy automatycznego wykrywania <xref:System.Net.WebProxy> klasa próbuje zlokalizować skrypt konfiguracji serwera proxy w następujący sposób:  
  
1.  WinINet `InternetQueryOption` funkcja jest używana do lokalizowania ostatnio wykrytych przez program Internet Explorer skryptu konfiguracji serwera proxy.  
  
2.  Jeśli skrypt nie jest umieszczony <xref:System.Net.WebProxy> klasa korzysta z konfiguracji protokołu DHCP (Dynamic Host) można znaleźć skryptu. Serwer DHCP może odpowiadać lokalizacji (nazwa hosta) za pomocą skryptu lub do pełnego adresu URL skryptu.  
  
3.  Jeśli DHCP nie będzie rozpoznawał hosta WPAD, DNS zostanie zapytany o hoście WPAD, jako jego nazwę lub alias.  
  
4.  Jeśli nie określono hosta i lokalizacja skryptu konfiguracji serwera proxy jest określony przez ustawienia sieci LAN programu Internet Explorer lub plik konfiguracji, ta lokalizacja jest używana.  
  
> [!NOTE]
>  Aplikacje uruchomione jako usługi NT lub w ramach programu ASP.NET Użyj ustawień serwera proxy programu Internet Explorer (jeśli jest dostępny) wywoływanie użytkownika. Te ustawienia mogą nie być dostępne dla wszystkich aplikacji usługi.  
  
 Serwery proxy są skonfigurowane na podstawie wstępnie zdefiniowane na połączenie. Identyfikator elementu w oknie dialogowym połączenia sieciowe i może być urządzenie sieci fizycznej (modemu lub karty sieciowej Ethernet) lub interfejsu wirtualnego (na przykład uruchomiony za pośrednictwem urządzenia sieciowego połączenia sieci VPN). Podczas zmiany identyfikator (na przykład połączenia bezprzewodowego zmiany włączono punkt dostępu lub sieci VPN), ponownie uruchom algorytmu wykrywania serwera proxy.  
  
 Domyślnie ustawienia serwera proxy programu Internet Explorer są używane do wykrywania serwera proxy. Jeśli aplikacja jest uruchomiona na koncie podejścia nieinterakcyjnego (bez wygodny sposób, aby skonfigurować ustawienia serwera proxy programu Internet Explorer) lub jeśli chcesz użyć ustawień serwera proxy jest inne niż ustawienia programu Internet Explorer, tworząc plik konfiguracji z możnaskonfigurowaćserwerproxy[ \<defaultProxy — > elementu (ustawienia sieciowe)](../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md) i [ \<proxy > elementu (ustawienia sieciowe)](../../../docs/framework/configure-apps/file-schema/network/proxy-element-network-settings.md) elementy zdefiniowane.  
  
 Żądań, które możesz utworzyć, można wyłączyć wykrywanie serwera proxy na poziomie żądania za pomocą wartości null <xref:System.Net.WebRequest.Proxy%2A> z żądaniem, jak pokazano w poniższym przykładzie kodu.  
  
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
  
 Żądania bez serwera proxy przy użyciu domenę aplikacji domyślny serwer proxy, który jest dostępny w <xref:System.Net.WebRequest.DefaultWebProxy%2A> właściwości.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Net.WebProxy>  
 <xref:System.Net.WebRequest>  
 [\<system.Net > (ustawienia sieciowe) — Element](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)
