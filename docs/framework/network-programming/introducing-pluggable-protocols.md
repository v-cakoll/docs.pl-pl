---
title: Wprowadzenie protokołów podłączanych
ms.date: 03/30/2017
helpviewer_keywords:
- data requests, pluggable protocols
- WebRequest class, pluggable protocols
- response to Internet request, pluggable protocols
- URI
- Windows Sockets
- request/response model
- sending data, pluggable protocols
- pluggable protocols
- WebClient class, about WebClient class
- pluggable protocols, about pluggable protocols
- Internet, pluggable protocols
- path identifiers
- Uniform Resource Identifier
- application development [.NET Framework], pluggable protocols
- requesting data from Internet, pluggable protocols
- receiving data, pluggable protocols
- protocols, pluggable
- server identifiers
- scheme identifiers
ms.assetid: 4b48e22d-e4e5-48f0-be80-d549bda97415
ms.openlocfilehash: 72b47b8159f9f6f0dc3a19c5cbf94335507d9e7d
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047861"
---
# <a name="introducing-pluggable-protocols"></a>Wprowadzenie protokołów podłączanych
Platforma Microsoft .NET Framework zawiera warstwową, rozszerzalną i zarządzaną implementację usług internetowych, którą można szybko i łatwo zintegrować z aplikacjami. Klasy dostępu do Internetu w <xref:System.Net> przestrzeniach nazw i <xref:System.Net.Sockets> mogą służyć do implementowania aplikacji opartych na sieci Web i Internecie.  
  
## <a name="internet-applications"></a>Aplikacje internetowe  
 Aplikacje internetowe można podzielić na dwa rodzaje: aplikacje klienckie, które żądają informacji i aplikacji serwerowych, które reagują na żądania informacji od klientów. Klasyczna aplikacja internetowa klienta — serwer to World Wide Web, w którym ludzie mogą uzyskiwać dostęp do dokumentów i innych danych przechowywanych na serwerach sieci Web na całym świecie.  
  
 Aplikacje nie są ograniczone tylko do jednej z tych ról; na przykład znany serwer aplikacji warstwy środkowej reaguje na żądania od klientów żądając danych z innego serwera, w takim przypadku działa zarówno jako serwer, jak i klient.  
  
 Aplikacja kliencka wysyła żądanie, identyfikując żądany zasób internetowy i protokół komunikacyjny do użycia na potrzeby żądania i odpowiedzi. W razie potrzeby klient zapewnia również wszelkie dodatkowe dane wymagane do ukończenia żądania, takie jak lokalizacja serwera proxy lub informacje o uwierzytelnianiu (nazwa użytkownika, hasło itp.). Po utworzeniu żądania można wysłać żądanie do serwera.  
  
## <a name="identifying-resources"></a>Identyfikowanie zasobów  
 .NET Framework używa Uniform Resource Identifier (URI) do identyfikowania żądanego zasobu internetowego i protokołu komunikacyjnego. Identyfikator URI składa się z co najmniej trzech i prawdopodobnie czterech fragmentów: Identyfikator schematu, który identyfikuje protokół komunikacji dla żądania i odpowiedzi; Identyfikator serwera, który składa się z nazwy hosta systemu nazw domen (DNS) lub adresu TCP, który jednoznacznie identyfikuje serwer w Internecie; Identyfikator ścieżki, który lokalizuje żądane informacje na serwerze; i opcjonalny ciąg zapytania, który przekazuje informacje z klienta do serwera. Na przykład identyfikator URI `http://www.contoso.com/whatsnew.aspx?date=today` składa się z identyfikatora `http`schematu, identyfikatora `www.contoso.com`serwera, ścieżki `/whatsnew.aspx`i ciągu `?date=today`zapytania.  
  
 Gdy serwer odebrał żądanie i przetworzył odpowiedź, zwróci odpowiedź do aplikacji klienckiej. Odpowiedź zawiera dodatkowe informacje, takie jak typ zawartości (na przykład nieprzetworzony tekst lub dane XML).  
  
## <a name="requests-and-responses-in-the-net-framework"></a>Żądania i odpowiedzi w .NET Framework  
 .NET Framework używa określonych klas w celu zapewnienia trzech informacji wymaganych do uzyskania dostępu do zasobów internetowych za pośrednictwem modelu żądania/odpowiedzi: <xref:System.Uri> Klasa, która zawiera identyfikator URI poszukiwanego zasobu internetowego; <xref:System.Net.WebRequest>Klasa, która zawiera żądanie dla zasobu; <xref:System.Net.WebResponse> i Klasa, która dostarcza kontener dla odpowiedzi przychodzącej.  
  
 Aplikacje klienckie tworzą `WebRequest` wystąpienia przez przekazanie identyfikatora URI zasobu sieciowego <xref:System.Net.WebRequest.Create%2A> do metody. Ta metoda statyczna tworzy `WebRequest` dla określonego protokołu, takich jak http. Zwracana `WebRequest` wartość zapewnia dostęp do właściwości kontrolujących zarówno żądanie do serwera, jak i dostęp do strumienia danych, który jest wysyłany podczas żądania. <xref:System.Net.WebRequest.GetResponse%2A> Metoda`WebRequest` wysyłania żądania z aplikacji klienckiej do serwera zidentyfikowanego w identyfikatorze URI. W przypadkach, w których odpowiedź może być opóźniona, żądanie może być wykonywane asynchronicznie przy <xref:System.Net.WebRequest.BeginGetResponse%2A> użyciu metody w **webżądaniu**, a odpowiedź może zostać zwrócona w <xref:System.Net.WebRequest.EndGetResponse%2A> późniejszym czasie za pomocą metody.  
  
 Metody **GetResponse** i **EndGetResponse** zwracają **WebResponse** , który zapewnia dostęp do danych zwróconych przez serwer. Ponieważ te dane są dostarczane do żądającej aplikacji jako strumień przez <xref:System.Net.WebResponse.GetResponseStream%2A> metodę, może być używana w aplikacji, w której są używane strumienie danych.  
  
 Klasy **WebRequest** i **WebResponse** stanowią podstawę protokołów podłączanych — implementację usług sieciowych, która umożliwia tworzenie aplikacji, które korzystają z zasobów internetowych bez obaw o szczegółowe informacje dotyczące Protokół, który jest wykorzystywany przez każdy z zasobów. Klasy podrzędne elementu **WebRequest** są rejestrowane za pomocą klasy **WebRequest** w celu zarządzania szczegółami tworzenia rzeczywistych połączeń z zasobami internetowymi.  
  
 Przykładowo <xref:System.Net.HttpWebRequest> Klasa zarządza informacjami o łączeniu się z zasobem internetowym przy użyciu protokołu HTTP. Domyślnie, gdy metoda **WebRequest. Create** napotyka identyfikator URI zaczynający się od ciągu "http:" lub "https:" (identyfikatory protokołu dla protokołu HTTP i Secure HTTP), zwracane **żądanie WebRequest** może być używane jako lub może być rzutowanie do  **HttpWebRequest** uzyskać dostęp do właściwości specyficznych dla protokołu. W większości przypadków **żądanie WebRequest** zawiera wszystkie informacje niezbędne do wykonania żądania.  
  
 Każdy protokół, który może być reprezentowany jako transakcja żądania/odpowiedzi, może być używany w **żądaniu WebRequest**. Klasy specyficzne dla protokołu można utworzyć z **żądań WebRequest** i **WebResponse** , a następnie zarejestrować je do użytku przez aplikację z metodą statyczną <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> .  
  
 Gdy wymagane jest autoryzacja klienta dla żądań internetowych, <xref:System.Net.WebRequest.Credentials%2A> Właściwość **żądania WebRequest** dostarcza niezbędne poświadczenia. Mogą to być proste pary nazw i haseł dla podstawowego uwierzytelniania HTTP lub szyfrowanego, a także nazwa/hasło/domena ustawiona na potrzeby uwierzytelniania NTLM lub Kerberos. Jeden zestaw poświadczeń może być przechowywany w <xref:System.Net.NetworkCredential> wystąpieniu lub wiele zestawów może być przechowywanych jednocześnie <xref:System.Net.CredentialCache> w wystąpieniu. **CredentialCache** używa identyfikatora URI żądania oraz schematu uwierzytelniania obsługiwanego przez serwer, aby określić, które poświadczenia należy wysłać do serwera.  
  
## <a name="simple-requests-with-webclient"></a>Proste żądania z klientem WebClient  
 W przypadku aplikacji, które muszą wykonywać proste żądania dotyczące zasobów internetowych, <xref:System.Net.WebClient> Klasa zawiera typowe metody przekazywania danych do lub pobierania danych z serwera internetowego. **Klient WebClient** korzysta z klasy **żądania WebRequest** w celu zapewnienia dostępu do zasobów internetowych. w związku z tym Klasa **WebClient** może korzystać z dowolnego zarejestrowanego protokołu podłączanego.  
  
 W przypadku aplikacji, które nie mogą korzystać z modelu żądania/odpowiedzi, lub dla aplikacji, które muszą nasłuchiwać w sieci, a także żądania wysłania, przestrzeń nazw **System .NET. Sockets** zawiera <xref:System.Net.Sockets.TcpClient>klasy, <xref:System.Net.Sockets.TcpListener>i <xref:System.Net.Sockets.UdpClient> . Te klasy obsługują Szczegóły tworzenia połączeń przy użyciu różnych protokołów transportu i uwidaczniają połączenie sieciowe z aplikacją jako strumień.  
  
 Deweloperzy znający interfejs Windows Sockets lub osoby potrzebujące kontroli zapewnianej przez Programowanie na poziomie gniazda znajdą, że klasy **System .NET. Sockets** spełnią ich potrzeby. Klasy **System .NET. Sockets** to punkt przejścia z kodu zarządzanego do natywnego w klasach **System.NET** . W większości przypadków klasy **System .NET. Sockets** są organizowane jako odpowiedniki systemu Windows 32-bitowe, a także do obsługi wszelkich niezbędnych kontroli zabezpieczeń.  
  
## <a name="see-also"></a>Zobacz także

- [Programowanie protokołów podłączanych](programming-pluggable-protocols.md)
- [Programowanie dla sieci w programie .NET Framework](index.md)
- [Przykłady programowania sieciowego](network-programming-samples.md)
