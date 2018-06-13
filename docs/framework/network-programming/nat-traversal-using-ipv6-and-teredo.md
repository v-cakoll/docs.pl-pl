---
title: Przechodzenie translatora adresów Sieciowych przy użyciu protokołu IPv6 i Teredo
ms.date: 03/30/2017
ms.assetid: 568cd245-3300-49ef-a995-d81bf845d961
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: d2e503bedd908bff18f3c1a8d626d056f22d3f55
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33398121"
---
# <a name="nat-traversal-using-ipv6-and-teredo"></a>Przechodzenie translatora adresów Sieciowych przy użyciu protokołu IPv6 i Teredo
Ulepszenia wprowadzono zapewniają obsługę przechodzenie translacji adresów sieciowych (NAT). Te zmiany są przeznaczone do użytku z protokołu IPv6 i Teredo, ale również dotyczą innych IP tunelowania technologii. Te ulepszenia mają wpływ na klas w <xref:System.Net> i związanych z przestrzeni nazw.  
  
 Te zmiany mogą wpłynąć na klienta i serwera aplikacji, które ma być używana technologii tunelowania IP.  
  
 Zmiany do obsługi przechodzenia translatora adresów Sieciowych są dostępne tylko dla aplikacji za pomocą .NET Framework w wersji 4. Te funkcje nie są dostępne w starszych wersjach programu .NET Framework.  
  
## <a name="overview"></a>Omówienie  
 Internet Protocol w wersji 4 (IPv4) zdefiniowany 32 bitów adresu IPv4. W związku z tym IPv4 obsługuje około 4 miliardy unikatowych adresów IP (2 ^ 32). Jako liczba komputerów i urządzeń sieciowych w Internecie rozwinięty w 1990s limity przestrzeni adresów IPv4 stała się oczywista.  
  
 Jeden z kilku technik umożliwia rozszerzanie przez czas ich istnienia IPv4 został wdrażania translatora adresów Sieciowych, aby umożliwić pojedynczego unikatowy publicznego adresu IP do reprezentowania dużą liczbę prywatnego adresu IP adresów (prywatny Intranet). Prywatnych adresów IP za urządzeniem NAT współużytkować jeden publiczny adres IPv4. Urządzenie NAT może być dedykowanym urządzeniem sprzętowym (niedrogich punkt dostępu bezprzewodowego i router, na przykład) lub komputer z uruchomioną usługą zapewnienie translatora adresów sieciowych. Urządzenie lub usługa dla ten publiczny adres IP tłumaczy IP pakietów sieciowych między publicznej sieci Internet i prywatny Intranet.  
  
 Ten program działa dobrze w przypadku aplikacji klienckich działających w prywatnym intranetem, które wysyłają żądania do innych adresów IP (zwykle serwery) w Internecie. Urządzenie NAT lub serwer można zachować mapowania żądań klientów, gdy odpowiedź jest zwracana wie, który ma zostać wysłana odpowiedź. Jednak ten schemat stwarza problemy dla aplikacji działających w prywatnym intranecie za urządzeniem NAT, które mają być świadczenia usług, nasłuchiwania pakietów i odpowiadać. Jest to szczególnie w przypadku aplikacji peer-to-peer.  
  
 Protokół IPv6 zdefiniowany 128 bitów adresu IPv4. W związku z tym IPv6 obsługuje bardzo dużych przestrzeń adresów IP w wersji 3.2 x 10 ^ 38 unikatowych adresów (2 ^ 128). Się na przestrzeń adresową ten rozmiar jest możliwe dla wszystkich urządzeń, połączony z Internetem, aby mieć unikatowy adres. Ale wystąpiły problemy. Większość świecie nadal używa tylko protokół IPv4. W szczególności nie obsługują wiele punktów dostępu bezprzewodowego, używany przez małe firmy, organizacje i domowych i routery IPv6. Również niektórzy usługodawcy internetowi obsługujących Ci klienci nie obsługują albo nie skonfigurowano obsługę protokołu IPv6.  
  
 Kilka technologie przejściowe IPv6 zostały opracowane na adresy IPv6 tunelu w pakiecie IPv4. Te technologie obejmują usługi 6to4 protokołu ISATAP, a tuneli protokołu Teredo, zapewniających przypisywania adresów i automatyczne tunelowanie host-host ruch IPv6 emisji pojedynczej przechodzenie hostów protokołu IPv6 musi IP4 sieci w celu dostępu do innych sieci IPv6. Tunelowane jako pakietów IPv4 wysyłania pakietów IPv6. Kilka technik tunelowania jest używany przez urządzenie NAT zezwalających na Przechodzenie translatora adresów Sieciowych dla adresów IPv6.  
  
 Protokół Teredo jest jednym z technologie przejściowe IPv6, które oferuje łączności IPv6 w sieciach IPv4. Teredo jest opisane w dokumencie RFC 4380 opublikowane przez Internet Engineering Task Force (IETF). Windows XP z dodatkiem SP2 i nowszym zapewniają obsługę dla wirtualnej karty Teredo, które zapewniają publiczny adres IPv6 w zakresie 2001: 0:: / 32. Ten adres IPv6 może służyć do nasłuchiwania przychodzących połączeń z Internetu i może zostać dostarczona do IPv6 włączone klientów, którzy chcą połączyć się z usługą nasłuchiwania. To powoduje zwolnienie aplikację za pomocą martwiąc się o sposobie adres komputera za urządzeniem NAT, ponieważ aplikacja właśnie można łączyć się przy użyciu jego adresu IPv6 klientów Teredo.  
  
## <a name="enhancements-to-support-nat-traversal-and-teredo"></a>Ulepszenia obsługi przechodzenia translatora adresów Sieciowych i Teredo  
 Rozszerzenia są dodawane do <xref:System.Net>, <xref:System.Net.NetworkInformation>, i <xref:System.Net.Sockets> obszarów nazw do obsługi przechodzenia translatora adresów Sieciowych przy użyciu protokołu IPv6 i Teredo.  
  
 Kilka metod są dodawane do <xref:System.Net.NetworkInformation.IPGlobalProperties?displayProperty=nameWithType> klasy w celu uzyskania adresów IP na liście emisji pojedynczej na hoście. <xref:System.Net.NetworkInformation.IPGlobalProperties.BeginGetUnicastAddresses%2A> Metoda rozpoczyna żądanie asynchroniczne można pobrać tabeli adresów IP stabilna emisji pojedynczej na komputerze lokalnym. <xref:System.Net.NetworkInformation.IPGlobalProperties.EndGetUnicastAddresses%2A> Metoda kończy się oczekujące żądania asynchronicznego można pobrać tabeli adresów IP stabilna emisji pojedynczej na komputerze lokalnym. <xref:System.Net.NetworkInformation.IPGlobalProperties.GetUnicastAddresses%2A> Metoda jest żądań synchronicznych można pobrać tabeli adresów IP stabilna emisji pojedynczej na komputerze lokalnym, czekając na tabeli Adres stabilizuje się, jeśli to konieczne.  
  
 <xref:System.Net.IPAddress.IsIPv6Teredo%2A?displayProperty=nameWithType> Właściwości może służyć do określenia, czy <xref:System.Net.IPAddress> jest adresem IPv6 klientów Teredo.  
  
 Korzystanie z tych nowych <xref:System.Net.NetworkInformation.IPGlobalProperties> metody w połączeniu z klasy <xref:System.Net.IPAddress.IsIPv6Teredo%2A> właściwości umożliwia aplikacji łatwo znaleźć adresu Teredo. Aplikacji zwykle tylko trzeba określić lokalny adres protokołu Teredo, jeśli komunikuje się te informacje do zdalnej aplikacji. Na przykład aplikacja peer-to-peer może wysyłać, wszystkie jego adresy IPv6 do serwera matchmaking, który można następnie prześlij je dalej do innych użytkowników równorzędnymi użytkownikami, aby umożliwić bezpośrednią komunikację.  
  
 Aplikacja zwykle należy ustawić jej nasłuchiwania usługi do nasłuchiwania <xref:System.Net.IPAddress.IPv6Any?displayProperty=nameWithType> , a nie dla adresu lokalnego Teredo. Dlatego jeśli klienta zdalnego lub elementu równorzędnego bezpośrednie trasy IPv6 do hosta usługi nasłuchiwania, klienta lub elementu równorzędnego można połączyć się bezpośrednio przy użyciu protokołu IPv6 i nie trzeba używać protokołu Teredo pakietów tunelu.  
  
 W przypadku aplikacji TCP <xref:System.Net.Sockets.TcpListener?displayProperty=nameWithType> klasa ma <xref:System.Net.Sockets.TcpListener.AllowNatTraversal%2A> metodę, aby włączyć Przechodzenie translatora adresów Sieciowych. W przypadku aplikacji UDP <xref:System.Net.Sockets.UdpClient?displayProperty=nameWithType> klasa ma <xref:System.Net.Sockets.UdpClient.AllowNatTraversal%2A> metodę, aby włączyć Przechodzenie translatora adresów Sieciowych.  
  
 Dla aplikacji używających <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> i klas pokrewnych <xref:System.Net.Sockets.Socket.GetSocketOption%2A> i <xref:System.Net.Sockets.Socket.SetSocketOption%2A> metody mogą być używane z <xref:System.Net.Sockets.SocketOptionName.IPProtectionLevel?displayProperty=nameWithType> gniazda zapytania, włączyć lub wyłączyć przechodzenia translatora adresów Sieciowych.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Net.IPAddress.IsIPv6Teredo%2A?displayProperty=nameWithType>  
 <xref:System.Net.NetworkInformation.IPGlobalProperties.BeginGetUnicastAddresses%2A?displayProperty=nameWithType>  
 <xref:System.Net.NetworkInformation.IPGlobalProperties.EndGetUnicastAddresses%2A?displayProperty=nameWithType>  
 <xref:System.Net.NetworkInformation.IPGlobalProperties.GetUnicastAddresses%2A?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.Socket.SetIPProtectionLevel%2A?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.TcpListener.AllowNatTraversal%2A?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.UdpClient.AllowNatTraversal%2A?displayProperty=nameWithType>
