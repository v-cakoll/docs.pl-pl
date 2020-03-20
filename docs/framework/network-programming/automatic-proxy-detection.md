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
# <a name="automatic-proxy-detection"></a>Automatyczne wykrywanie serwera proxy
Automatyczne wykrywanie serwera proxy jest procesem, w którym serwer proxy sieci Web jest identyfikowany przez system i używany do wysyłania żądań w imieniu klienta. Ta funkcja jest również znana jako Auto-Discovery serwera proxy sieci Web (WPAD). Gdy automatyczne wykrywanie serwera proxy jest włączone, system próbuje zlokalizować skrypt konfiguracji serwera proxy, który jest odpowiedzialny za zwracanie zestawu serwerów proxy, które mogą być używane dla żądania. Jeśli zostanie znaleziony skrypt konfiguracji serwera proxy, skrypt jest pobierany, kompilowany i uruchamiany na komputerze lokalnym, gdy informacje <xref:System.Net.WebProxy> o serwerze proxy, strumień żądania lub odpowiedź jest uzyskiwana dla żądania, które używa wystąpienia.  
  
 Automatyczne wykrywanie serwera <xref:System.Net.WebProxy> proxy jest wykonywane przez klasę i może stosować ustawienia na poziomie żądania, ustawienia w plikach konfiguracyjnych i ustawienia określone za pomocą okna dialogowego Sieć lokalna programu Internet Explorer **(LAN).**  
  
> [!NOTE]
> Okno dialogowe Ustawienia sieci lokalnej programu Internet Explorer **(LAN),** wybierając polecenie **Narzędzia** z menu głównego programu Internet Explorer, a następnie wybierając pozycję **Opcje internetowe**. Następnie wybierz kartę **Połączenia** i kliknij pozycję **Ustawienia sieci LAN**.  
  
 Gdy automatyczne wykrywanie serwera <xref:System.Net.WebProxy> proxy jest włączone, klasa próbuje zlokalizować skrypt konfiguracji serwera proxy w następujący sposób:  
  
1. Funkcja WinINet `InternetQueryOption` służy do lokalizowania skryptu konfiguracji serwera proxy ostatnio wykrytego przez program Internet Explorer.  
  
2. Jeśli skrypt nie znajduje <xref:System.Net.WebProxy> się, klasa używa protokołu DHCP (Dynamic Host Configuration Protocol) do zlokalizowania skryptu. Serwer DHCP może odpowiedzieć lokalizacją (nazwą hosta) skryptu lub pełnym adresem URL skryptu.  
  
3. Jeśli usługa DHCP nie identyfikuje hosta WPAD, usługa DNS jest wyszukiwana w przypadku hosta z programem WPAD jako jego nazwą lub aliasem.  
  
4. Jeśli host nie został zidentyfikowany, a lokalizacja skryptu konfiguracji serwera proxy jest określona przez ustawienia sieci LAN programu Internet Explorer lub plik konfiguracyjny, ta lokalizacja jest używana.  
  
> [!NOTE]
> Aplikacje działające jako usługa NT lub w ramach ASP.NET używać ustawień serwera proxy programu Internet Explorer (jeśli są dostępne) wywoływanego użytkownika. Te ustawienia mogą nie być dostępne dla wszystkich aplikacji serwisowych.  
  
 Serwery proxy są konfigurowane na podstawie na connectoid. Connectoid jest elementem w oknie dialogowym połączenia sieciowego i może być fizycznym urządzeniem sieciowym (modem lub kartą Ethernet) lub interfejsem wirtualnym (takim jak połączenie sieci VPN działające za pośrednictwem urządzenia sieciowego). Po zmianie connectoid (na przykład połączenie bezprzewodowe zmienia punkt dostępu lub vpn jest włączony), algorytm wykrywania serwera proxy jest uruchamiany ponownie.  
  
 Domyślnie ustawienia serwera proxy programu Internet Explorer są używane do wykrywania serwera proxy. Jeśli aplikacja działa na koncie nieinterakcyjnym (bez wygodnego sposobu konfigurowania ustawień serwera proxy IE) lub jeśli chcesz używać ustawień serwera proxy innych niż ustawienia IE, możesz skonfigurować serwer proxy, tworząc plik konfiguracyjny z zdefiniowanymi elementami [ \<defaultProxy> Element (Ustawienia sieciowe)](../configure-apps/file-schema/network/defaultproxy-element-network-settings.md) i [ \<elementem> proxy (Ustawienia sieci).](../configure-apps/file-schema/network/proxy-element-network-settings.md)  
  
 W przypadku żądań, które tworzysz, można wyłączyć automatyczne <xref:System.Net.WebRequest.Proxy%2A> wykrywanie serwera proxy na poziomie żądania przy użyciu null z żądaniem, jak pokazano w poniższym przykładzie kodu.  
  
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
  
 Żądania, które nie mają serwera proxy, używają domyślnego serwera <xref:System.Net.WebRequest.DefaultWebProxy%2A> proxy domeny aplikacji, który jest dostępny we właściwości.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Net.WebProxy>
- <xref:System.Net.WebRequest>
- [\<system.Net element> (ustawienia sieciowe)](../configure-apps/file-schema/network/system-net-element-network-settings.md)
