---
title: Przechodzenie translatora adresów sieciowych przy użyciu protokołu IPv6 i Teredo
ms.date: 03/30/2017
ms.assetid: 568cd245-3300-49ef-a995-d81bf845d961
ms.openlocfilehash: f617dc8912091576727b90da1e9efb9ebd5f9bda
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "61642181"
---
# <a name="nat-traversal-using-ipv6-and-teredo"></a>Przechodzenie translatora adresów sieciowych przy użyciu protokołu IPv6 i Teredo
Wprowadzono ulepszenia, które zapewniają obsługę przechodzenia translacji adresów sieciowych (NAT). Zmiany te są przeznaczone do użytku z IPv6 i Teredo, ale mają również zastosowanie do innych technologii tunelowania IP. Te ulepszenia wpływają na <xref:System.Net> klasy w i powiązanych przestrzeni nazw.  
  
 Zmiany te mogą mieć wpływ na aplikacje klienckie i serwerowe, które planują używać technologii tunelowania IP.  
  
 Zmiany do obsługi przechodzenia NAT są dostępne tylko dla aplikacji korzystających z programu .NET Framework w wersji 4. Te funkcje nie są dostępne we wcześniejszych wersjach programu .NET Framework.  
  
## <a name="overview"></a>Omówienie  
 Protokół internetowy w wersji 4 (IPv4) zdefiniował adres IPv4 jako 32 bity. W rezultacie protokół IPv4 obsługuje około 4 miliardów unikatowych adresów IP (2^32). Wraz ze wzrostem liczby komputerów i urządzeń sieciowych w Internecie w latach 90., granice przestrzeni adresowej IPv4 stały się widoczne.  
  
 Jedną z kilku technik używanych w celu przedłużenia okresu istnienia protokołu IPv4 było wdrożenie translatora adresów sieciowych w celu umożliwienia pojedynczego unikatowego publicznego adresu IP reprezentującego dużą liczbę prywatnych adresów IP (prywatny intranet). Prywatne adresy IP za urządzeniem NAT współużytkuje pojedynczy publiczny adres IPv4. Urządzenie NAT może być dedykowanym urządzeniem sprzętowym (na przykład niedrogim punktem dostępu bezprzewodowego i routerem) lub komputerem z usługą zapewniającą translatora adresów sieciowych. Urządzenie lub usługa dla tego publicznego adresu IP tłumaczy pakiety sieciOWE IP między publicznym Internetem a prywatnym intranetem.  
  
 Ten schemat działa dobrze w przypadku aplikacji klienckich uruchomionych w prywatnym intranecie, które wysyłają żądania do innych adresów IP (zwykle serwerów) w Internecie. Urządzenie lub serwer NAT można zachować mapowanie żądań klienta, więc po zwróceniu odpowiedzi wie, gdzie wysłać odpowiedź. Ale ten schemat stwarza problemy dla aplikacji działających w prywatnym intranecie za urządzeniem NAT, które chcą świadczyć usługi, nasłuchiwać pakietów i odpowiadać. Dotyczy to w szczególności aplikacji równorzędnych.  
  
 Protokół IPv6 zdefiniował adres IPv4 o długości 128 bitów. W rezultacie protokół IPv6 obsługuje bardzo dużą przestrzeń adresów IP o unikatowych adresach 3,2 x 10^38 (2^128). Dzięki przestrzeni adresowej tej wielkości, możliwe jest, aby każde urządzenie podłączone do Internetu otrzymało unikalny adres. Ale są problemy. Większość świata nadal używa tylko IPv4. W szczególności wiele istniejących routerów i punktów dostępu bezprzewodowego używanych przez małe firmy, organizacje i gospodarstwa domowe nie obsługuje IPv6. Również niektórzy dostawcy usług internetowych, którzy obsługują tych klientów, nie obsługują lub nie skonfigurowali obsługi iPv6.  
  
 Opracowano kilka technologii przejścia IPv6 do tunelowania adresów IPv6 w pakiecie IPv4. Technologie te obejmują tunele 6to4, ISATAP i Teredo, które zapewniają przypisanie adresów i automatyczne tunelowanie hosta dla ruchu IPv6 emisji pojedynczej, gdy hosty IPv6 muszą przechodzić przez sieci IP4, aby dotrzeć do innych sieci IPv6. Pakiety IPv6 są wysyłane tunelowane jako pakiety IPv4. Dostępnych jest kilka technik tunelowania, które umożliwiają przechodzenie na łat dla adresów IPv6 za pośrednictwem urządzenia NAT.  
  
 Teredo jest jedną z technologii przejścia IPv6, która zapewnia łączność IPv6 do sieci IPv4. Teredo jest udokumentowany w RFC 4380 opublikowanym przez Internet Engineering Task Force (IETF). Dodatek SP2 dla systemu Windows XP i nowszych zapewniają obsługę wirtualnej karty Teredo, która może zapewnić publiczny adres IPv6 w zakresie 2001:0::/32. Ten adres IPv6 może służyć do nasłuchiwania połączeń przychodzących z Internetu i może być dostarczony klientom obsługującym protokół IPv6, którzy chcą połączyć się z usługą nasłuchiwania. Zwalnia to aplikację od martwienia się o to, jak rozwiązać komputer za urządzeniem NAT, ponieważ aplikacja może po prostu połączyć się z nią za pomocą adresu IPv6 Teredo.  
  
## <a name="enhancements-to-support-nat-traversal-and-teredo"></a>Ulepszenia do obsługi NAT Traversal i Teredo  
 Ulepszenia są dodawane <xref:System.Net> <xref:System.Net.NetworkInformation>do <xref:System.Net.Sockets> , i przestrzeni nazw do obsługi przechodzenia na nat przy użyciu IPv6 i Teredo.  
  
 Kilka metod są <xref:System.Net.NetworkInformation.IPGlobalProperties?displayProperty=nameWithType> dodawane do klasy, aby uzyskać listę adresów IP emisji pojedynczej na hoście. Metoda <xref:System.Net.NetworkInformation.IPGlobalProperties.BeginGetUnicastAddresses%2A> rozpoczyna asynchroniczne żądanie, aby pobrać stabilną tabelę adresów IP emisji pojedynczej na komputerze lokalnym. Metoda <xref:System.Net.NetworkInformation.IPGlobalProperties.EndGetUnicastAddresses%2A> kończy oczekujące żądanie asynchroniczne, aby pobrać stabilną tabelę adresów IP emisji pojedynczej na komputerze lokalnym. Metoda <xref:System.Net.NetworkInformation.IPGlobalProperties.GetUnicastAddresses%2A> jest synchroniczne żądanie, aby pobrać stabilną tabelę adresów IP emisji pojedynczej na komputerze lokalnym, czekając, aż tabela adresów ustabilizuje się w razie potrzeby.  
  
 Właściwość <xref:System.Net.IPAddress.IsIPv6Teredo%2A?displayProperty=nameWithType> może służyć do <xref:System.Net.IPAddress> określenia, czy jest adres IPv6 Teredo.  
  
 Za pomocą <xref:System.Net.NetworkInformation.IPGlobalProperties> tych nowych metod <xref:System.Net.IPAddress.IsIPv6Teredo%2A> klasy w połączeniu z właściwości umożliwia aplikacji łatwo znaleźć adres Teredo. Aplikacja zwykle musi znać lokalny adres Teredo tylko wtedy, gdy przekazuje te informacje do aplikacji zdalnych. Na przykład aplikacja peer-to-peer może wysłać wszystkie swoje adresy IPv6 do serwera kojarzeń, który następnie można przekazać je do innych elementów równorzędnych, aby włączyć komunikację bezpośrednią.  
  
 Aplikacja powinna zwykle ustawić swoją usługę <xref:System.Net.IPAddress.IPv6Any?displayProperty=nameWithType> nasłuchiwania, aby nasłuchiwać, a nie na lokalnym adresie Teredo. Jeśli więc klient zdalny lub element równorzędny ma bezpośrednią trasę IPv6 do hosta usługi nasłuchiwania, klient lub element równorzędny może łączyć się bezpośrednio przy użyciu protokołu IPv6 i nie musi używać Teredo do tunelowania pakietów.  
  
 W przypadku aplikacji <xref:System.Net.Sockets.TcpListener?displayProperty=nameWithType> TCP <xref:System.Net.Sockets.TcpListener.AllowNatTraversal%2A> klasa ma metodę włączania przechodzenia na nat. Dla aplikacji UDP <xref:System.Net.Sockets.UdpClient?displayProperty=nameWithType> klasa <xref:System.Net.Sockets.UdpClient.AllowNatTraversal%2A> ma metodę, aby włączyć przechodzenie na nat.  
  
 W przypadku aplikacji, które używają <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> i powiązanych klas, <xref:System.Net.Sockets.Socket.GetSocketOption%2A> i <xref:System.Net.Sockets.Socket.SetSocketOption%2A> metody mogą być używane z opcją <xref:System.Net.Sockets.SocketOptionName.IPProtectionLevel?displayProperty=nameWithType> gniazda do kwerendy, włączyć lub wyłączyć przechodzenie nat.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Net.IPAddress.IsIPv6Teredo%2A?displayProperty=nameWithType>
- <xref:System.Net.NetworkInformation.IPGlobalProperties.BeginGetUnicastAddresses%2A?displayProperty=nameWithType>
- <xref:System.Net.NetworkInformation.IPGlobalProperties.EndGetUnicastAddresses%2A?displayProperty=nameWithType>
- <xref:System.Net.NetworkInformation.IPGlobalProperties.GetUnicastAddresses%2A?displayProperty=nameWithType>
- <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>
- <xref:System.Net.Sockets.Socket.SetIPProtectionLevel%2A?displayProperty=nameWithType>
- <xref:System.Net.Sockets.TcpListener.AllowNatTraversal%2A?displayProperty=nameWithType>
- <xref:System.Net.Sockets.UdpClient.AllowNatTraversal%2A?displayProperty=nameWithType>
