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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047861"
---
# <a name="introducing-pluggable-protocols"></a>Wprowadzenie protokołów podłączanych
Program Microsoft .NET Framework udostępnia warstwową, rozszerzalną i zarządzaną implementację usług internetowych, które można szybko i łatwo zintegrować z aplikacjami. Klasy dostępu do <xref:System.Net> Internetu <xref:System.Net.Sockets> w obszarach nazw i mogą być używane do implementowania aplikacji opartych na sieci Web i internetowych.  
  
## <a name="internet-applications"></a>Aplikacje internetowe  
 Aplikacje internetowe można podzielić na dwa rodzaje: aplikacje klienckie, które żądają informacji i aplikacje serwera, które odpowiadają na żądania informacji od klientów. Klasyczna aplikacja klient-serwer internetowy to sieć World Wide Web, w której użytkownicy korzystają z przeglądarek w celu uzyskiwania dostępu do dokumentów i innych danych przechowywanych na serwerach sieci Web na całym świecie.  
  
 Aplikacje nie są ograniczone tylko do jednej z tych ról; na przykład znany serwer aplikacji warstwy środkowej odpowiada na żądania od klientów, żądając danych od innego serwera, w którym to przypadku działa zarówno jako serwer, jak i klient.  
  
 Aplikacja kliencka składa żądanie, identyfikując żądany zasób internetowy i protokół komunikacyjny do użycia dla żądania i odpowiedzi. W razie potrzeby klient udostępnia również wszelkie dodatkowe dane wymagane do wykonania żądania, takie jak lokalizacja serwera proxy lub informacje uwierzytelniania (nazwa użytkownika, hasło itd.). Po utworzeniu żądania żądanie może zostać wysłane do serwera.  
  
## <a name="identifying-resources"></a>Identyfikowanie zasobów  
 Program .NET Framework używa jednolitego identyfikatora zasobów (URI) do identyfikowania żądanego zasobu internetowego i protokołu komunikacyjnego. Identyfikator URI składa się z co najmniej trzech, a być może czterech fragmentów: identyfikatora schematu, który identyfikuje protokół komunikacyjny dla żądania i odpowiedzi; identyfikator serwera, który składa się z nazwy hosta dns (Domain Name System) lub adresu TCP, który jednoznacznie identyfikuje serwer w Internecie; identyfikator ścieżki, który lokalizuje żądane informacje na serwerze; i opcjonalny ciąg zapytania, który przekazuje informacje z klienta do serwera. Na przykład identyfikator `http://www.contoso.com/whatsnew.aspx?date=today` URI składa się `http`z identyfikatora `www.contoso.com`schematu, identyfikatora serwera, ścieżki `/whatsnew.aspx`i ciągu `?date=today`zapytania .  
  
 Po odebraniu żądania przez serwer i przetworzyniu odpowiedzi zwraca odpowiedź do aplikacji klienckiej. Odpowiedź zawiera dodatkowe informacje, takie jak typ zawartości (na przykład tekst nieprzetworzony lub dane XML).  
  
## <a name="requests-and-responses-in-the-net-framework"></a>Żądania i odpowiedzi w ramach .NET Framework  
 .NET Framework używa określonych klas, aby zapewnić trzy informacje wymagane do uzyskania dostępu do <xref:System.Uri> zasobów internetowych za pośrednictwem modelu żądania/odpowiedzi: klasa, która zawiera identyfikator URI zasobu internetowego, którego szukasz; <xref:System.Net.WebRequest> klasa, która zawiera żądanie dla zasobu; i <xref:System.Net.WebResponse> klasy, która zapewnia kontener dla odpowiedzi przychodzącej.  
  
 Aplikacje `WebRequest` klienckie tworzą wystąpienia, przekazując <xref:System.Net.WebRequest.Create%2A> identyfikator URI zasobu sieciowego do metody. Ta metoda statyczna `WebRequest` tworzy dla określonego protokołu, takich jak HTTP. Zwracany `WebRequest` zapewnia dostęp do właściwości, które kontrolują zarówno żądanie do serwera, jak i dostęp do strumienia danych, który jest wysyłany po wysłaniu żądania. Metoda <xref:System.Net.WebRequest.GetResponse%2A> na `WebRequest` wysyła żądanie z aplikacji klienckiej do serwera określonego w identyfikatorze URI. W przypadkach, w których odpowiedź może być opóźnione, żądanie można zrobić <xref:System.Net.WebRequest.BeginGetResponse%2A> asynchronicznie przy użyciu metody na **WebRequest** <xref:System.Net.WebRequest.EndGetResponse%2A> , a odpowiedź może zostać zwrócona w późniejszym czasie przy użyciu metody.  
  
 **Metody GetResponse** i **EndGetResponse** zwracają **WebResponse,** który zapewnia dostęp do danych zwracanych przez serwer. Ponieważ te dane są dostarczane do aplikacji żądającej jako strumień przez <xref:System.Net.WebResponse.GetResponseStream%2A> metodę, może służyć w aplikacji wszędzie tam, gdzie są używane strumienie danych.  
  
 **WebRequest** i **WebResponse** klasy są podstawą protokołów pluggable — implementacja usług sieciowych, która umożliwia tworzenie aplikacji, które korzystają z zasobów internetowych bez martwienia się o szczegółowe szczegóły protokołu, który każdy zasób używa. Klasy podrzędne **WebRequest** są rejestrowane w **Klasie WebRequest,** aby zarządzać szczegółami tworzenia rzeczywistych połączeń z zasobami internetowymi.  
  
 Na przykład <xref:System.Net.HttpWebRequest> klasa zarządza szczegółami łączenia się z zasobem internetowym przy użyciu protokołu HTTP. Domyślnie, gdy **WebRequest.Create** metoda napotka identyfikator URI, który zaczyna się od "http:" lub "https:" (identyfikatory protokołu HTTP i bezpiecznego HTTP), **WebRequest,** który jest zwracany może być używany w stanie jest lub może być typecast do **HttpWebRequest** dostępu do właściwości specyficznych dla protokołu. W większości przypadków **WebRequest** zawiera wszystkie informacje niezbędne do złożenia żądania.  
  
 Każdy protokół, który może być reprezentowany jako transakcja żądania/odpowiedzi, może być używany w **webrequest**. Klasy specyficzne dla protokołu można uzyskać z **WebRequest** i **WebResponse,** a następnie <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> zarejestrować je do użycia przez aplikację za pomocą metody statycznej.  
  
 Gdy wymagana jest autoryzacja klienta <xref:System.Net.WebRequest.Credentials%2A> dla żądań internetowych, właściwość **WebRequest** dostarcza niezbędnych poświadczeń. Te poświadczenia mogą być prostą parą nazwa/hasło dla podstawowego uwierzytelniania HTTP lub szyfrowanego lub ustawioną na nazwę/hasło/domenę dla uwierzytelniania NTLM lub Kerberos. Jeden zestaw poświadczeń <xref:System.Net.NetworkCredential> mogą być przechowywane w wystąpieniu lub <xref:System.Net.CredentialCache> wiele zestawów mogą być przechowywane jednocześnie w wystąpieniu. **CredentialCache** używa identyfikatora URI żądania i schematu uwierzytelniania, który obsługuje serwer, aby określić, które poświadczenia mają być wysyłane do serwera.  
  
## <a name="simple-requests-with-webclient"></a>Proste żądania z WebClient  
 W przypadku aplikacji, które muszą tworzyć <xref:System.Net.WebClient> proste żądania dotyczące zasobów internetowych, klasa zawiera typowe metody przekazywania danych do lub pobierania danych z serwera internetowego. **WebClient** opiera się na **WebRequest** klasy w celu zapewnienia dostępu do zasobów internetowych; w związku z tym **WebClient** klasa może używać dowolnego zarejestrowanego protokołu pluggable.  
  
 W przypadku aplikacji, które nie mogą używać modelu żądania/odpowiedzi lub dla aplikacji, które muszą nasłuchiwać w <xref:System.Net.Sockets.TcpClient> <xref:System.Net.Sockets.TcpListener>sieci, <xref:System.Net.Sockets.UdpClient> a także wysyłać żądania, obszar nazw **System.Net.Sockets** udostępnia , i klasy. Te klasy obsługują szczegóły tworzenia połączeń przy użyciu różnych protokołów transportu i udostępniają połączenie sieciowe do aplikacji jako strumień.  
  
 Deweloperzy zaznajomieni z interfejsem Windows Sockets lub ci, którzy potrzebują kontroli zapewnianej przez programowanie na poziomie gniazda, przekonają się, że klasy **System.Net.Sockets** spełniają ich potrzeby. **Klasy System.Net.Sockets** są punktem przejścia od kodu natywnego z kodu macierzystego w **klasach System.Net.** W większości przypadków **System.Net.Sockets** klasy danych marszałka do ich odpowiedników systemu Windows 32-bitowych, a także obsługi wszelkich niezbędnych kontroli zabezpieczeń.  
  
## <a name="see-also"></a>Zobacz też

- [Programowanie protokołów podłączanych](programming-pluggable-protocols.md)
- [Programowanie dla sieci w programie .NET Framework](index.md)
- [Przykłady programowania sieciowego](network-programming-samples.md)
