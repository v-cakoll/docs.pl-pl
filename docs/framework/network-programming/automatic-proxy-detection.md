---
title: Automatyczne wykrywanie serwera proxy
description: Informacje o automatycznym wykrywaniu serwera proxy, gdzie system identyfikuje serwer proxy sieci Web i używa go do wysyłania żądań w imieniu klienta.
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
ms.openlocfilehash: dbd5d7fa671ae5ec3b7dc00205f0c9d8381bb3ce
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502703"
---
# <a name="automatic-proxy-detection"></a>Automatyczne wykrywanie serwera proxy
Automatyczne wykrywanie serwera proxy to proces, za pomocą którego serwer proxy sieci Web jest identyfikowany przez system i używany do wysyłania żądań w imieniu klienta. Ta funkcja jest nazywana również autowykrywaniem serwera proxy sieci Web (WPAD). Gdy automatyczne wykrywanie serwera proxy jest włączone, system próbuje zlokalizować skrypt konfiguracji serwera proxy, który jest odpowiedzialny za zwracanie zestawu serwerów proxy, których można użyć dla żądania. Jeśli zostanie znaleziony skrypt konfiguracji serwera proxy, skrypt zostanie pobrany, skompilowany i uruchomiony na komputerze lokalnym, gdy informacje o serwerze proxy, strumieniu żądania lub odpowiedzi zostaną uzyskane dla żądania, które używa <xref:System.Net.WebProxy> wystąpienia.  
  
 Automatyczne wykrywanie serwera proxy jest wykonywane przez <xref:System.Net.WebProxy> klasę i może korzystać z ustawień na poziomie żądania, ustawień w plikach konfiguracji i ustawień określonych przy użyciu okna dialogowego **sieci lokalnej (LAN)** programu Internet Explorer.  
  
> [!NOTE]
> Możesz wyświetlić okno dialogowe **Ustawienia sieci lokalnej (LAN)** programu Internet Explorer, wybierając pozycję **Narzędzia** z menu głównego programu Internet Explorer, a następnie wybierając pozycję **Opcje internetowe**. Następnie wybierz kartę **połączenia** , a następnie kliknij pozycję **Ustawienia sieci LAN**.  
  
 Gdy automatyczne wykrywanie serwera proxy jest włączone, <xref:System.Net.WebProxy> Klasa próbuje zlokalizować skrypt konfiguracji serwera proxy w następujący sposób:  
  
1. Funkcja WinINet `InternetQueryOption` służy do lokalizowania ostatnio wykrytego skryptu konfiguracji serwera proxy przez program Internet Explorer.  
  
2. Jeśli skrypt nie znajduje się, <xref:System.Net.WebProxy> Klasa używa Dynamic Host Configuration Protocol (DHCP) do lokalizowania skryptu. Serwer DHCP może odpowiedzieć na lokalizację (nazwę hosta) skryptu lub z pełnym adresem URL dla skryptu.  
  
3. Jeśli usługa DHCP nie zidentyfikuje hosta WPAD, do usługi DNS jest wysyłane zapytanie dla hosta z usługą WPAD jako jego nazwy lub aliasu.  
  
4. Jeśli host nie zostanie zidentyfikowany i lokalizacja skryptu konfiguracji serwera proxy jest określona przez ustawienia sieci LAN programu Internet Explorer lub plik konfiguracji, Ta lokalizacja jest używana.  
  
> [!NOTE]
> Aplikacje działające jako usługa NT lub jako część ASP.NET używają ustawień serwera proxy programu Internet Explorer (jeśli są dostępne) dla użytkownika wywołującego. Te ustawienia mogą być niedostępne dla wszystkich aplikacji usługi.  
  
 Serwery proxy są konfigurowane na podstawie Connectoid. Connectoid to element w oknie dialogowym połączenia sieciowego, który może być fizycznym urządzeniem sieciowym (modemem lub kartą sieci Ethernet) lub interfejsem wirtualnym (na przykład połączeniem sieci VPN działającym przez urządzenie sieciowe). Gdy Connectoid zmiany (na przykład połączenie bezprzewodowe zmienia punkt dostępu lub sieć VPN jest włączona), algorytm wykrywania serwera proxy jest uruchamiany ponownie.  
  
 Domyślnie ustawienia serwera proxy programu Internet Explorer są używane do wykrywania serwera proxy. Jeśli aplikacja działa w ramach konta nieinterakcyjnego (bez wygodnego sposobu konfigurowania ustawień serwera proxy programu IE) lub jeśli chcesz użyć ustawień serwera proxy innych niż ustawienia programu IE, możesz skonfigurować serwer proxy, tworząc plik konfiguracji z [ \<defaultProxy> elementem (Ustawienia sieci)](../configure-apps/file-schema/network/defaultproxy-element-network-settings.md) i [ \<proxy> element (Ustawienia sieci)](../configure-apps/file-schema/network/proxy-element-network-settings.md) zdefiniowane.  
  
 W przypadku żądań, które tworzysz, można wyłączyć automatyczne wykrywanie serwera proxy na poziomie żądania przy użyciu wartości null <xref:System.Net.WebRequest.Proxy%2A> z żądaniem, jak pokazano w poniższym przykładzie kodu.  
  
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
  
 Żądania, które nie mają serwera proxy, używają domyślnego serwera proxy domeny aplikacji, który jest dostępny we <xref:System.Net.WebRequest.DefaultWebProxy%2A> właściwości.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Net.WebProxy>
- <xref:System.Net.WebRequest>
- [\<system.Net>— Element (Ustawienia sieci)](../configure-apps/file-schema/network/system-net-element-network-settings.md)
