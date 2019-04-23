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
ms.openlocfilehash: 656a21a7b8801a2c3b72b25531705576fcf047cd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59295760"
---
# <a name="automatic-proxy-detection"></a>Automatyczne wykrywanie serwera proxy
Automatyczne wykrywanie serwera proxy jest procesem, za pomocą którego serwer proxy sieci Web jest identyfikowane przez system i używane do wysyłania żądania w imieniu klienta. Ta funkcja jest również znana jako funkcja autowykrywania serwera Proxy sieci Web (WPAD). Gdy automatyczne wykrywanie serwera proxy jest włączone, system próbuje zlokalizować skryptu konfiguracji serwera proxy, która jest odpowiedzialna za zwrócenie zestaw serwerów proxy, które mogą być używane dla żądania. Jeśli zostanie znaleziony skryptu konfiguracji serwera proxy, skrypt pobrany, skompilowany i uruchom na komputerze lokalnym, jeśli informacje o serwerze proxy, strumienia żądania lub odpowiedzi jest uzyskiwany na żądanie, który używa <xref:System.Net.WebProxy> wystąpienia.  
  
 Automatyczne wykrywanie serwera proxy odbywa się przez <xref:System.Net.WebProxy> klasy i mogą stosować ustawienia na poziomie żądania, ustawienia w plikach konfiguracji i ustawień określonych w programie Internet Explorer **sieci lokalnej (LAN)** okno dialogowe.  
  
> [!NOTE]
>  Możesz wyświetlić programu Internet Explorer **ustawienia sieci lokalnej (LAN)** okno dialogowe, wybierając **narzędzia** z menu głównego w programie Internet Explorer, a następnie wybierając pozycję **Opcje internetowe**. Następnie wybierz pozycję **połączeń** kartę, a następnie kliknij przycisk **ustawienia sieci LAN**.  
  
 Gdy jest włączone automatyczne wykrywanie serwera proxy, <xref:System.Net.WebProxy> klasy próbuje zlokalizować skryptu konfiguracji serwera proxy w następujący sposób:  
  
1. WinINet `InternetQueryOption` funkcja jest używana do lokalizowania skryptu konfiguracji serwera proxy ostatnio wykrytych przez program Internet Explorer.  
  
2. Jeśli skrypt nie jest umieszczony <xref:System.Net.WebProxy> klasa używa DHCP Dynamic Host Configuration Protocol (), aby zlokalizować scenariusza. Serwer DHCP może odpowiadać za pomocą lokalizacji (nazwa hosta), skryptu lub pełny adres URL skryptu.  
  
3. Jeśli DHCP nie wskazuje hosta WPAD, DNS zostaje przesłane zapytanie do hosta za pomocą WPAD jako jego nazwę lub alias.  
  
4. Ta lokalizacja jest używana, jeśli host nie zostanie zidentyfikowany, lokalizacja skryptu konfiguracji serwera proxy jest określony przez ustawienia Internet Explorer w sieci LAN lub pliku konfiguracji.  
  
> [!NOTE]
>  Aplikacje działające jako usługi NT lub w ramach programu ASP.NET Użyj ustawień serwera proxy programu Internet Explorer (jeśli jest dostępny) użytkownika, które powinny być przekazywane wywołującemu. Te ustawienia mogą być dostępne dla wszystkich aplikacji usługi.  
  
 Serwery proxy są skonfigurowane na podstawie wstępnie zdefiniowane na połączenie. Identyfikator jest element w oknie dialogowym połączenia sieciowe i może być urządzeniem sieci fizycznej (modem lub karta Ethernet) lub interfejsu wirtualnego (np. połączenia sieci VPN, uruchamiania przez urządzenie sieciowe). Gdy identyfikator ulegnie zmianie (na przykład połączenia bezprzewodowego zmiany punktu dostępu lub sieci VPN jest włączona), algorytm wykrywania serwera proxy jest uruchamiany ponownie.  
  
 Domyślnie ustawienia serwera proxy programu Internet Explorer są używane do wykrywania serwera proxy. Jeśli aplikacja jest uruchomiona w ramach konta nieinterakcyjnych (bez wygodny sposób, aby skonfigurować ustawienia serwera proxy programu Internet Explorer) lub jeśli chcesz używać ustawień serwera proxy są inne niż ustawienia programu Internet Explorer, można skonfigurować serwer proxy, tworząc plik konfiguracji o [ \<defaultProxy >, Element (ustawienia sieci)](../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md) i [ \<proxy >, Element (ustawienia sieci)](../../../docs/framework/configure-apps/file-schema/network/proxy-element-network-settings.md) elementy zdefiniowane.  
  
 Dla żądań, które tworzysz, możesz wyłączyć automatyczne wykrywanie serwera proxy na poziomie żądania przy użyciu wartości null <xref:System.Net.WebRequest.Proxy%2A> z żądaniem, jak pokazano w poniższym przykładzie kodu.  
  
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
  
 Żądania, które nie mają serwer proxy przy użyciu domenę aplikacji domyślny serwer proxy, który jest dostępny w <xref:System.Net.WebRequest.DefaultWebProxy%2A> właściwości.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Net.WebProxy>
- <xref:System.Net.WebRequest>
- [\<przestrzeni nazw system.Net >, Element (ustawienia sieci)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)
