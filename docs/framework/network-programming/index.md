---
title: Programowanie dla sieci w .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- Networking
- Internet
- Internet, .NET Framework Internet services
- Network Resources
ms.assetid: 8d455610-67a0-4fa8-a62f-7747064a9256
ms.openlocfilehash: 1e7f0123ab07fd4e83eea957b72bf79eeeecef2b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74204691"
---
# <a name="network-programming-in-the-net-framework"></a>Programowanie dla sieci w .NET Framework
Środowisko Microsoft .NET Framework oferuje warstwowe, rozszerzalne i zarządzane wdrożenia usług internetowych, które można szybko i łatwo zintegrować ze swoimi aplikacjami. Aplikacje sieciowe mogą za pomocą podłączanych protokołów automatycznie wykorzystywać nowe protokoły internetowe albo za pośrednictwem zarządzanej implementacji interfejsu gniazd systemu Windows współpracować z siecią na poziomie gniazd.  
  
## <a name="in-this-section"></a>W tej sekcji  

 [Wprowadzenie protokołów podłączanych](introducing-pluggable-protocols.md)  
 Opis sposobów uzyskiwania dostępu do zasobu internetowego bez względu na protokół dostępu, którego wymaga zasób.  
  
 [Żądanie danych](requesting-data.md)  
 Wyjaśnienie, jak za pomocą podłączanych protokołów przekazywać i pobierać dane z zasobów internetowych.  
  
 [Programowanie protokołów podłączanych](programming-pluggable-protocols.md)  
 Wyjaśnienie, jak utworzyć pochodne klasy specyficzne dla protokołów w celu zaimplementowania podłączanych protokołów.  
  
 [Korzystanie z protokołów aplikacji](using-application-protocols.md)  
 Opis zasad programowania aplikacji wykorzystujących protokoły sieciowe, takie jak TCP, UDP i HTTP.  
  
 [Protokół internetowy w wersji 6](internet-protocol-version-6.md)  
 Opis zalet protokołu Internet Protocol w wersji 6 (IPv6) w porównaniu z obecną wersją pakietu Internet Protocol (IPv4), a także mechanizmów adresowania, routingu i automatycznej konfiguracji w protokole IPv6 oraz sposobów włączania i wyłączania protokołu.  
  
 [Konfigurowanie aplikacji internetowych](configuring-internet-applications.md)  
 Wyjaśnienie zasad konfigurowania aplikacji internetowych za pomocą plików konfiguracyjnych środowiska .NET Framework.  
  
 [Śledzenie sieci w .NET Framework](network-tracing.md)  
 Wyjaśnienie, jak za pomocą mechanizmu śledzenia sieci uzyskiwać informacje o wywołaniach metod i ruchu sieciowym generowanym przez zarządzaną aplikację.  
  
 [Zarządzanie pamięcią podręczną dla aplikacji sieciowych](cache-management-for-network-applications.md)  
 W tym artykule opisano sposób korzystania <xref:System.Net.WebClient?displayProperty=nameWithType> <xref:System.Net.WebRequest?displayProperty=nameWithType>z <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> buforowania dla aplikacji korzystających z programu , i klas.  
  
 [Zabezpieczenia w programowaniu sieciowym](security-in-network-programming.md)  
 Opis używania standardowych technik zabezpieczania i uwierzytelniania w Internecie.  
  
 [Najlepsze rozwiązania dotyczące klas System.Net](best-practices-for-system-net-classes.md)  
 Porady i wskazówki dotyczące optymalnego wykorzystania możliwości aplikacji internetowych.  
  
 [Dostęp do Internetu za pośrednictwem serwera proxy](accessing-the-internet-through-a-proxy.md)  
 Opis konfigurowania serwerów proxy.  
  
 [NetworkInformation](networkinformation.md)  
 W tym artykule opisano sposób zbierania informacji o zdarzeniach sieciowych, zmianach, statystykach i <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType> właściwościach, a także wyjaśniono, jak ustalić, czy host zdalny jest osiągalny przy użyciu klasy.  
  
 [Zmiany w przestrzeni nazw System.Uri w wersji 2.0](changes-to-the-system-uri-namespace-in-version-2-0.md)  
 W tym artykule <xref:System.Uri?displayProperty=nameWithType> opisano kilka zmian wprowadzonych do klasy w wersji 2.0, aby naprawić niepoprawne zachowanie, zwiększyć użyteczność i zwiększyć bezpieczeństwo.  
  
 [Obsługa identyfikatorów zasobów międzynarodowych w System.Uri](international-resource-identifier-support-in-system-uri.md)  
 Opisuje ulepszenia <xref:System.Uri?displayProperty=nameWithType> klasy w wersji 3.5, 3.0 z sp1 i 2.0 z sp1 dla międzynarodowego identyfikatora zasobów (IRI) i internationalized Domain Name (IDN) pomocy technicznej.  
  
 [Ulepszenia wydajności gniazda w wersji 3.5](socket-performance-enhancements-in-version-3-5.md)  
 W tym artykule opisano <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> zestaw ulepszeń do klasy w wersji 3.5, 3.0 SP1 i 2.0 SP1, które zapewniają alternatywny wzorzec asynchroniczne, które mogą być używane przez wyspecjalizowane aplikacje gniazd o wysokiej wydajności.  
  
 [Protokół PNRP](peer-name-resolution-protocol.md)  
 Opis mechanizmu dodanego w wersji 3.5 do obsługi protokołu PNRP (Peer Name Resolution Protocol), bezserwerowego i dynamicznego rejestrowania nazw oraz protokołu rozpoznawania nazw. Te nowe funkcje są <xref:System.Net.PeerToPeer?displayProperty=nameWithType> obsługiwane przez obszar nazw.  
  
 [Współpraca równorzędna](peer-to-peer-collaboration.md)  
 Opis mechanizmu dodanego w wersji 3.5 do obsługi współpracy między równorzędnymi urządzeniami w oparciu o protokół PNRP. Te nowe funkcje są <xref:System.Net.PeerToPeer.Collaboration?displayProperty=nameWithType> obsługiwane przez obszar nazw.  
  
 [Zmiany w uwierzytelnianiu NTLM dla HttpWebRequest w wersji 3.5 z dodatkiem SP1](changes-to-ntlm-authentication-for-httpwebrequest-in-version-3-5-sp1.md)  
 W tym artykule opisano zmiany zabezpieczeń wprowadzone w dodatku SP1 w <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> <xref:System.Net.HttpListener?displayProperty=nameWithType>wersji <xref:System.Net.Security.NegotiateStream?displayProperty=nameWithType>3.5, które wpływają na sposób obsługi zintegrowanego uwierzytelniania systemu Windows przez program , i powiązane klasy w System.Net obszarze nazw.  
  
 [Zintegrowane uwierzytelnianie systemu Windows z ochroną rozszerzoną](integrated-windows-authentication-with-extended-protection.md)  
 W tym artykule opisano ulepszenia rozszerzonej ochrony, które <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> <xref:System.Net.HttpListener?displayProperty=nameWithType>wpływają <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> <xref:System.Net.Security.SslStream?displayProperty=nameWithType>na <xref:System.Net.Security.NegotiateStream?displayProperty=nameWithType>sposób obsługi zintegrowanego uwierzytelniania systemu Windows przez , , , i powiązane klasy w <xref:System.Net?displayProperty=nameWithType> powiązanych przestrzeniach nazw.  
  
 [Przechodzenie translatora adresów sieciowych przy użyciu protokołu IPv6 i Teredo](nat-traversal-using-ipv6-and-teredo.md)  
 Opisuje ulepszenia dodane <xref:System.Net?displayProperty=nameWithType>do <xref:System.Net.NetworkInformation?displayProperty=nameWithType>, <xref:System.Net.Sockets?displayProperty=nameWithType> i przestrzeni nazw do obsługi przechodzenia na nat przy użyciu IPv6 i Teredo.  
  
 [Izolacja sieci dla aplikacji ze sklepu Windows Store](network-isolation-for-windows-store-apps.md)  
 W tym artykule opisano wpływ <xref:System.Net> <xref:System.Net.Http>izolacji <xref:System.Net.Http.Headers> sieci, gdy klasy w programie , i przestrzenie nazw są używane w aplikacjach ze Sklepu Windows 8.x.  
  
 [Przykłady programowania sieciowego](network-programming-samples.md)  
 Łącza do przykładów programowania sieciowego do <xref:System.Net> <xref:System.Net.Cache>pobrania, które używają <xref:System.Net.Security> <xref:System.Net.Sockets> klas w , , <xref:System.Net.Configuration> <xref:System.Net.Mail>, <xref:System.Net.Mime>, <xref:System.Net.NetworkInformation> <xref:System.Net.PeerToPeer>, , , , , przestrzenie nazw.  
  
## <a name="reference"></a>Dokumentacja  
 <xref:System.Net?displayProperty=nameWithType>  
 Prosty interfejs programistyczny dla wielu protokołów używanych obecnie w sieciach. I <xref:System.Net.WebRequest?displayProperty=nameWithType> <xref:System.Net.WebResponse?displayProperty=nameWithType> klasy w tej przestrzeni nazw są podstawą dla protokołów pluggable.  
  
 <xref:System.Net.Cache?displayProperty=nameWithType>  
 Definiuje typy i wyliczenia używane do definiowania <xref:System.Net.WebRequest?displayProperty=nameWithType> zasad <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> pamięci podręcznej dla zasobów uzyskanych przy użyciu i klas.  
  
 <xref:System.Net.Configuration?displayProperty=nameWithType>  
 Klasy, za pomocą których aplikacje programistycznie uzyskują dostęp i aktualizują ustawienia konfiguracyjne w przestrzeni nazw System.Net.  
  
 <xref:System.Net.Http?displayProperty=nameWithType>  
 Klasy tworzące interfejs programistyczny dla nowoczesnych aplikacji wykorzystujących protokół HTTP.  
  
 <xref:System.Net.Http.Headers?displayProperty=nameWithType>  
 Zapewnia obsługę kolekcji nagłówków HTTP <xref:System.Net.Http?displayProperty=nameWithType> używanych przez obszar nazw  
  
 <xref:System.Net.Mail?displayProperty=nameWithType>  
 Klasy do redagowania i wysyłania poczty przy użyciu protokołu SMTP.  
  
 <xref:System.Net.Mime?displayProperty=nameWithType>  
 Definiuje typy, które są używane do reprezentowania nagłówków MIME (Multipurpose Internet Mail Exchange) używanych przez klasy w obszarze <xref:System.Net.Mail?displayProperty=nameWithType> nazw.  
  
 <xref:System.Net.NetworkInformation?displayProperty=nameWithType>  
 Klasy umożliwiające programistyczne gromadzenie informacji o zdarzeniach, zmianach, statystykach i właściwościach sieci.  
  
 <xref:System.Net.PeerToPeer?displayProperty=nameWithType>  
 Umożliwia zarządzaną implementację protokołu PNRP (Peer Name Resolution Protocol) dla programistów.  
  
 <xref:System.Net.PeerToPeer.Collaboration?displayProperty=nameWithType>  
 Umożliwia zarządzaną implementację interfejsu współpracy elementów równorzędnych dla programistów.  
  
 <xref:System.Net.Security?displayProperty=nameWithType>  
 Klasy zapewniające strumienie sieciowe umożliwiające bezpieczną komunikację między hostami.  
  
 <xref:System.Net.Sockets?displayProperty=nameWithType>  
 Umożliwia zarządzaną implementację interfejsu Windows Sockets (Winsock) dla programistów, którzy muszą wprowadzić mechanizm kontroli dostępu do sieci.  
  
 <xref:System.Net.WebSockets?displayProperty=nameWithType>  
 Umożliwia zarządzaną implementację interfejsu WebSocket dla programistów.  
  
 <xref:System.Uri?displayProperty=nameWithType>  
 Umożliwia reprezentowanie obiektów za pomocą jednolitych identyfikatorów zasobów (URI) oraz łatwy dostęp do elementów identyfikatorów URI.  
  
 <xref:System.Security.Authentication.ExtendedProtection?displayProperty=nameWithType>  
 Umożliwia obsługę uwierzytelniania przy użyciu mechanizmu rozszerzonej ochrony aplikacji.  
  
 <xref:System.Security.Authentication.ExtendedProtection.Configuration?displayProperty=nameWithType>  
 Umożliwia konfigurowanie uwierzytelniania przy użyciu mechanizmu rozszerzonej ochrony aplikacji.  
  
## <a name="see-also"></a>Zobacz też

- [Najważniejsze wskazówki dotyczące zabezpieczeń warstwy transportu (TLS) w ramach platformy .NET Framework](tls.md)
- [Programowanie dla sieci — tematy z instrukcjami](network-programming-how-to-topics.md)
- [Przykłady programowania sieciowego](network-programming-samples.md)
- [Przykład httpclient](https://code.msdn.microsoft.com/windowsapps/HttpClient-sample-55700664)
