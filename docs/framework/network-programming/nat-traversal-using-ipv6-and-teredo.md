---
title: Przechodzenie translatora adresów Sieciowych przy użyciu protokołu IPv6 i Teredo
ms.date: 03/30/2017
ms.assetid: 568cd245-3300-49ef-a995-d81bf845d961
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 7ee219f8ecb3103e5f9676498b09f290d6e7be8d
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48581943"
---
# <a name="nat-traversal-using-ipv6-and-teredo"></a>Przechodzenie translatora adresów Sieciowych przy użyciu protokołu IPv6 i Teredo
Wprowadzono ulepszenia, które umożliwiają przechodzenie translacji adresów sieciowych (NAT). Te zmiany są skonstruowane do użycia przy użyciu protokołu IPv6 i Teredo, ale są one również zastosowanie do innych adresów IP, tunelowanie technologii. Te ulepszenia wpływają na klas w <xref:System.Net> i pokrewnych przestrzeniach nazw.  
  
 Te zmiany mogą wpływać na klienta i serwera aplikacji, które planujesz używać tunelowania technologii adresu IP.  
  
 Zmiany, które umożliwiają przechodzenie translatora adresów Sieciowych są dostępne tylko dla aplikacji przy użyciu platformy .NET Framework w wersji 4. Te funkcje nie są dostępne we wcześniejszych wersjach programu .NET Framework.  
  
## <a name="overview"></a>Omówienie  
 Protokołu internetowego w wersji 4 (IPv4) adres IPv4 są zdefiniowane jako 32 bity długości. W rezultacie protokołu IPv4 obsługuje około 4 miliardy unikatowych adresów IP (2 ^ 32). Jako liczba komputerów i urządzeń sieciowych w Internecie, rozwinięty w 1990s granice przestrzeni adresów IPv4 stał się widoczny.  
  
 Jeden z kilku technik używanej do rozszerzania okres istnienia IPv4 został wdrażania translatora adresów Sieciowych, aby zezwolić na jeden unikatowy publiczny adres IP do reprezentowania dużej liczby prywatny adres IP adresów (prywatny Intranet). Prywatne adresy IP za urządzeniem NAT udostępnianie jednego publicznego adresu IPv4. Urządzenie NAT może być dedykowanym urządzeniem sprzętowym (niedrogie punkt dostępu bezprzewodowego i routera, na przykład) lub komputera z uruchomioną usługą w celu zapewnienia translatora adresów sieciowych. Urządzenie lub usługa dla tego publicznego adresu IP dokonuje translacji pakietów sieciowych adresów IP między publicznym Internetem a prywatny Intranet.  
  
 Ten schemat działa dobrze w przypadku aplikacji klienckich działających na prywatnym intranetem, które wysyłają żądania z innymi adresami IP (zazwyczaj serwery) w Internecie. Urządzenie NAT lub serwer można pozostawić mapowanie żądań klientów to gdy odpowiedź jest zwracana wie, gdzie wysyłać odpowiedzi. Jednak ten schemat stwarza problemy dla aplikacji uruchamianych w prywatnym intranecie za urządzeniem NAT, które do świadczenia usług, nasłuchiwania pakietów oraz reagować. Jest to szczególnie w przypadku aplikacji peer-to-peer.  
  
 Protokół IPv6 określa adres IPv4 jako długości 128 bitów. W rezultacie IPv6 obsługuje bardzo duża przestrzeń adresów IP 3.2 x 10 ^ 38 unikatowych adresów (2 ^ 128). Przy użyciu przestrzeni adresowej o takim rozmiarze jest możliwe dla każdego urządzenia połączone z Internetem, otrzyma unikatowy adres. Ale występują problemy. Większość świecie nadal jest używany tylko protokół IPv4. W szczególności wiele routery i punktów dostępu bezprzewodowego używanych przez małe firmy, organizacje i gospodarstw domowych nie obsługują protokołu IPv6. Ponadto niektórzy usługodawcy internetowi, które pełnią Ci klienci nie obsługują albo nie skonfigurowano obsługę protokołu IPv6.  
  
 Kilka technologie przejściowe IPv6 zostały opracowane w celu adresy w tunelu IPv6 w pakiecie IPv4. Te technologie obejmują usługi 6to4 protokołu ISATAP, i tunele protokołu Teredo, zapewniające przypisywania adresów i hosta do automatycznego tunelowania ruchu IPv6 emisji pojedynczej Jeśli hosty IPv6 musi przechodzić przez IP4 sieci w celu dostępu do innych sieci IPv6. Pakiety IPv6 są wysyłane tunelowane jako pakiety protokołu IPv4. Kilka technik tunelowania są używane przez urządzenie NAT zezwalających na Przechodzenie translatora adresów Sieciowych dla adresów IPv6.  
  
 Protokół Teredo jest jednym z technologie przejściowe IPv6, które udostępnia łączność IPv6 w sieci IPv4. Protokół Teredo jest udokumentowany w dokumencie RFC 4380 opublikowane przez Internet Engineering Task Force (IETF). Windows XP z dodatkiem SP2 oraz później zapewnić wsparcie dla wirtualnej karty sieciowej protokołu Teredo, co może zapewnić publiczny adres IPv6 w zakresie 2001: 0:: / 32. Ten adres IPv6 może służyć do nasłuchiwania połączeń przychodzących z Internetu i mogą otrzymywać klientom włączony protokół IPv6, które chcą nawiązać połączenie z usługą nasłuchiwania. To powoduje zwolnienie aplikacji z konieczności martwienia się o adres komputera za urządzeniem NAT, ponieważ aplikacja może po prostu nawiązać z nim przy użyciu jego adresu IPv6 klientów Teredo.  
  
## <a name="enhancements-to-support-nat-traversal-and-teredo"></a>Ulepszenia obsługi Przechodzenie translatora adresów Sieciowych i Teredo  
 Ulepszenia są dodawane do <xref:System.Net>, <xref:System.Net.NetworkInformation>, i <xref:System.Net.Sockets> przestrzenie nazw do obsługi Przechodzenie translatora adresów Sieciowych przy użyciu protokołu IPv6 i Teredo.  
  
 Kilka metod są dodawane do <xref:System.Net.NetworkInformation.IPGlobalProperties?displayProperty=nameWithType> klasy w celu uzyskania adresów IP listę emisji pojedynczej na hoście. <xref:System.Net.NetworkInformation.IPGlobalProperties.BeginGetUnicastAddresses%2A> Metoda rozpoczyna żądania asynchronicznego, można pobrać tabeli adresów IP emisji pojedynczej stabilna na komputerze lokalnym. <xref:System.Net.NetworkInformation.IPGlobalProperties.EndGetUnicastAddresses%2A> Metoda kończy się oczekującego żądania asynchronicznego, można pobrać tabeli adresów IP emisji pojedynczej stabilna na komputerze lokalnym. <xref:System.Net.NetworkInformation.IPGlobalProperties.GetUnicastAddresses%2A> Metodą jest synchroniczne żądanie pobrania tabeli adresów IP emisji pojedynczej stabilna na komputerze lokalnym, czekając na tabelę adresów stabilizuje się, jeśli to konieczne.  
  
 <xref:System.Net.IPAddress.IsIPv6Teredo%2A?displayProperty=nameWithType> Właściwość może służyć do określenia, czy <xref:System.Net.IPAddress> jest adresem IPv6 klientów Teredo.  
  
 Korzystanie z tych nowych <xref:System.Net.NetworkInformation.IPGlobalProperties> metody w połączeniu z klasy <xref:System.Net.IPAddress.IsIPv6Teredo%2A> właściwość umożliwia aplikacji łatwo znaleźć adresu Teredo. Aplikacja wymaga zwykle jedynie znać lokalnego adresu Teredo, jeśli komunikuje się te informacje do zdalnych aplikacji. Na przykład aplikacji peer-to-peer może wysyłać, wszystkie jego adresy IPv6 do serwera matchmaking, który można następnie prześlij je dalej do innych osób prowadzi komunikację równorzędną, aby włączyć bezpośrednią komunikację.  
  
 Aplikacja zazwyczaj należy ustawić jego service nasłuchiwania do nasłuchiwania <xref:System.Net.IPAddress.IPv6Any?displayProperty=nameWithType> , a nie na lokalnym adresem Teredo. Dlatego jeśli klientów zdalnych lub elementów równorzędnych ma bezpośredni trasa IPv6 do hosta service nasłuchiwania, klienta lub równorzędnym można połączyć się bezpośrednio przy użyciu protokołu IPv6 i nie trzeba używać protokołu Teredo pakietów tunelu.  
  
 W przypadku aplikacji TCP <xref:System.Net.Sockets.TcpListener?displayProperty=nameWithType> klasa ma <xref:System.Net.Sockets.TcpListener.AllowNatTraversal%2A> metodę, aby włączyć Przechodzenie translatora adresów Sieciowych. W przypadku aplikacji UDP <xref:System.Net.Sockets.UdpClient?displayProperty=nameWithType> klasa ma <xref:System.Net.Sockets.UdpClient.AllowNatTraversal%2A> metodę, aby włączyć Przechodzenie translatora adresów Sieciowych.  
  
 W przypadku aplikacji, które używają <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> i powiązanymi klasami <xref:System.Net.Sockets.Socket.GetSocketOption%2A> i <xref:System.Net.Sockets.Socket.SetSocketOption%2A> metody mogą być używane z <xref:System.Net.Sockets.SocketOptionName.IPProtectionLevel?displayProperty=nameWithType> gniazda opcję, aby zbadać, włączyć lub wyłączyć Przechodzenie translatora adresów Sieciowych.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Net.IPAddress.IsIPv6Teredo%2A?displayProperty=nameWithType>  
 <xref:System.Net.NetworkInformation.IPGlobalProperties.BeginGetUnicastAddresses%2A?displayProperty=nameWithType>  
 <xref:System.Net.NetworkInformation.IPGlobalProperties.EndGetUnicastAddresses%2A?displayProperty=nameWithType>  
 <xref:System.Net.NetworkInformation.IPGlobalProperties.GetUnicastAddresses%2A?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.Socket.SetIPProtectionLevel%2A?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.TcpListener.AllowNatTraversal%2A?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.UdpClient.AllowNatTraversal%2A?displayProperty=nameWithType>
