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
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2019
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
  
 [Protokół IPv6](internet-protocol-version-6.md)  
 Opis zalet protokołu Internet Protocol w wersji 6 (IPv6) w porównaniu z obecną wersją pakietu Internet Protocol (IPv4), a także mechanizmów adresowania, routingu i automatycznej konfiguracji w protokole IPv6 oraz sposobów włączania i wyłączania protokołu.  
  
 [Konfigurowanie aplikacji internetowych](configuring-internet-applications.md)  
 Wyjaśnienie zasad konfigurowania aplikacji internetowych za pomocą plików konfiguracyjnych środowiska .NET Framework.  
  
 [Śledzenie sieci w programie .NET Framework](network-tracing.md)  
 Wyjaśnienie, jak za pomocą mechanizmu śledzenia sieci uzyskiwać informacje o wywołaniach metod i ruchu sieciowym generowanym przez zarządzaną aplikację.  
  
 [Zarządzanie pamięcią podręczną dla aplikacji sieciowych](cache-management-for-network-applications.md)  
 Describes how to use caching for applications that use the <xref:System.Net.WebClient?displayProperty=nameWithType>, <xref:System.Net.WebRequest?displayProperty=nameWithType>, and <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> classes.  
  
 [Zabezpieczenia w programowaniu sieciowym](security-in-network-programming.md)  
 Opis używania standardowych technik zabezpieczania i uwierzytelniania w Internecie.  
  
 [Najlepsze rozwiązania dotyczące klas System.Net](best-practices-for-system-net-classes.md)  
 Porady i wskazówki dotyczące optymalnego wykorzystania możliwości aplikacji internetowych.  
  
 [Dostęp do Internetu za pośrednictwem serwera proxy](accessing-the-internet-through-a-proxy.md)  
 Opis konfigurowania serwerów proxy.  
  
 [NetworkInformation](networkinformation.md)  
 Describes how to gather information about network events, changes, statistics, and properties and also explains how to determine whether a remote host is reachable by using the <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType> class.  
  
 [Zmiany w przestrzeni nazw System.Uri w wersji 2.0](changes-to-the-system-uri-namespace-in-version-2-0.md)  
 Describes several changes made to the <xref:System.Uri?displayProperty=nameWithType> class in Version 2.0 to fixed incorrect behavior, enhance usability, and enhance security.  
  
 [Obsługa identyfikatorów zasobów międzynarodowych w System.Uri](international-resource-identifier-support-in-system-uri.md)  
 Describes enhancements to the <xref:System.Uri?displayProperty=nameWithType> class in Version 3.5, 3.0 SP1, and 2.0 SP1 for International Resource Identifier (IRI) and Internationalized Domain Name (IDN) support.  
  
 [Ulepszenia wydajności gniazda w wersji 3.5](socket-performance-enhancements-in-version-3-5.md)  
 Describes a set of enhancements to the <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> class in Version 3.5, 3.0 SP1, and 2.0 SP1 that provide an alternative asynchronous pattern that can be used by specialized high-performance socket applications.  
  
 [Protokół PNRP](peer-name-resolution-protocol.md)  
 Opis mechanizmu dodanego w wersji 3.5 do obsługi protokołu PNRP (Peer Name Resolution Protocol), bezserwerowego i dynamicznego rejestrowania nazw oraz protokołu rozpoznawania nazw. These new features are supported by the <xref:System.Net.PeerToPeer?displayProperty=nameWithType> namespace.  
  
 [Współpraca równorzędna](peer-to-peer-collaboration.md)  
 Opis mechanizmu dodanego w wersji 3.5 do obsługi współpracy między równorzędnymi urządzeniami w oparciu o protokół PNRP. These new features are supported by the <xref:System.Net.PeerToPeer.Collaboration?displayProperty=nameWithType> namespace.  
  
 [Zmiany w uwierzytelnianiu NTLM dla HttpWebRequest w wersji 3.5 z dodatkiem SP1](changes-to-ntlm-authentication-for-httpwebrequest-in-version-3-5-sp1.md)  
 Describes security changes made in Version 3.5 SP1 that affect how integrated Windows authentication is handled by the <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>, <xref:System.Net.HttpListener?displayProperty=nameWithType>, <xref:System.Net.Security.NegotiateStream?displayProperty=nameWithType>, and related classes in the System.Net namespace.  
  
 [Zintegrowane uwierzytelnianie systemu Windows z ochroną rozszerzoną](integrated-windows-authentication-with-extended-protection.md)  
 Describes enhancements for extended protection that affect how integrated Windows authentication is handled by the <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>, <xref:System.Net.HttpListener?displayProperty=nameWithType>, <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>, <xref:System.Net.Security.SslStream?displayProperty=nameWithType>, <xref:System.Net.Security.NegotiateStream?displayProperty=nameWithType>, and related classes in the <xref:System.Net?displayProperty=nameWithType> and related namespaces.  
  
 [Przechodzenie translatora adresów sieciowych przy użyciu protokołu IPv6 i Teredo](nat-traversal-using-ipv6-and-teredo.md)  
 Describes enhancements added to the <xref:System.Net?displayProperty=nameWithType>, <xref:System.Net.NetworkInformation?displayProperty=nameWithType>, and <xref:System.Net.Sockets?displayProperty=nameWithType> namespaces to support NAT traversal using IPv6 and Teredo.  
  
 [Izolacja sieci dla aplikacji ze sklepu Windows Store](network-isolation-for-windows-store-apps.md)  
 Describes the impact of network isolation when classes in the <xref:System.Net>, <xref:System.Net.Http>, and <xref:System.Net.Http.Headers> namespaces are used in Windows 8.x Store apps.  
  
 [Przykłady programowania sieciowego](network-programming-samples.md)  
 Links to downloadable network programming samples that use classes in the <xref:System.Net>, <xref:System.Net.Cache>, <xref:System.Net.Configuration>, <xref:System.Net.Mail>, <xref:System.Net.Mime>, <xref:System.Net.NetworkInformation>, <xref:System.Net.PeerToPeer>, <xref:System.Net.Security>, <xref:System.Net.Sockets> namespaces.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Net?displayProperty=nameWithType>  
 Prosty interfejs programistyczny dla wielu protokołów używanych obecnie w sieciach. The <xref:System.Net.WebRequest?displayProperty=nameWithType> and <xref:System.Net.WebResponse?displayProperty=nameWithType> classes in this namespace are the basis for pluggable protocols.  
  
 <xref:System.Net.Cache?displayProperty=nameWithType>  
 Defines the types and enumerations used to define cache policies for resources obtained using the <xref:System.Net.WebRequest?displayProperty=nameWithType> and <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> classes.  
  
 <xref:System.Net.Configuration?displayProperty=nameWithType>  
 Klasy, za pomocą których aplikacje programistycznie uzyskują dostęp i aktualizują ustawienia konfiguracyjne w przestrzeni nazw System.Net.  
  
 <xref:System.Net.Http?displayProperty=nameWithType>  
 Klasy tworzące interfejs programistyczny dla nowoczesnych aplikacji wykorzystujących protokół HTTP.  
  
 <xref:System.Net.Http.Headers?displayProperty=nameWithType>  
 Provides support for collections of HTTP headers used by the <xref:System.Net.Http?displayProperty=nameWithType> namespace  
  
 <xref:System.Net.Mail?displayProperty=nameWithType>  
 Klasy do redagowania i wysyłania poczty przy użyciu protokołu SMTP.  
  
 <xref:System.Net.Mime?displayProperty=nameWithType>  
 Defines types that are used to represent Multipurpose Internet Mail Exchange (MIME) headers used by classes in the <xref:System.Net.Mail?displayProperty=nameWithType> namespace.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Transport Layer Security (TLS) best practices with .NET Framework](tls.md)
- [Programowanie dla sieci — tematy z instrukcjami](network-programming-how-to-topics.md)
- [Przykłady programowania sieciowego](network-programming-samples.md)
- [HttpClient Sample](https://code.msdn.microsoft.com/windowsapps/HttpClient-sample-55700664)
