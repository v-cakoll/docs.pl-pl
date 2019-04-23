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
ms.openlocfilehash: 25d7b0e8b8b98d68a0fb4a3cadab3d9f3e8747bd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59146149"
---
# <a name="introducing-pluggable-protocols"></a>Wprowadzenie protokołów podłączanych
Microsoft .NET Framework oferuje warstwowe, rozszerzalne i zarządzane wdrożenia usług internetowych, które można zintegrować szybkie i łatwe w swoich aplikacjach. Dostęp do Internetu klas w <xref:System.Net> i <xref:System.Net.Sockets> przestrzeni nazw może służyć do wdrożenia aplikacji opartych na sieci Web i oparty na Internecie.  
  
## <a name="internet-applications"></a>Aplikacje internetowe  
 Aplikacje internetowe można ogólnie podzielić na dwa rodzaje: aplikacje klienckie, które żądać informacji i serwera aplikacji, które odpowiadają na żądania informacji od klientów. Klasyczne aplikacja klient / serwer Internet jest World Wide Web, w których użytkownicy korzystają z przeglądarki pod kątem dostęp do dokumentów i innych — dane przechowywane na serwerach sieci Web na całym świecie.  
  
 Aplikacje nie są ograniczone do tylko jednej z tych ról; na przykład serwer znanych aplikacji warstwy środkowej odpowiada na żądania klientów przez żądanie danych z innego serwera, w tym przypadku działa ona jako serwera i klienta.  
  
 Aplikacja kliencka wysyła żądanie, identyfikując żądanego zasobu internetowego i protokół komunikacyjny na potrzeby żądań i odpowiedzi. Jeśli to konieczne, klient także wszelkie dodatkowe dane wymagane do ukończenia żądania, takie jak lokalizacja lub uwierzytelniania informacje o serwerze proxy (nazwa użytkownika, hasło i tak dalej). Gdy żądanie jest sformułowany, żądanie może wysłane do serwera.  
  
## <a name="identifying-resources"></a>Identyfikowanie zasobów  
 .NET Framework używa jednolity identyfikator zasobów (URI), aby zidentyfikować żądanego zasobu i komunikacji protokołu internetowego. Identyfikator URI, który składa się z co najmniej trzech oraz, ewentualnie czterech i fragmenty: identyfikator schemat, który identyfikuje protokołu komunikacji do żądania i odpowiedzi; Identyfikator serwera, który składa się z nazwy hosta systemu nazw domen (DNS, Domain Name System) lub adres protokołu TCP, który unikatowo identyfikuje serwer, na Internecie. Identyfikator ścieżki, która lokalizuje wymagane informacje, na serwerze; i parametry opcjonalne zapytanie, które przekazuje informacje z klienta do serwera. Na przykład identyfikator URI `http://www.contoso.com/whatsnew.aspx?date=today` składa się z identyfikatorem schematu `http`, identyfikator serwera `www.contoso.com`, ścieżka `/whatsnew.aspx`i ciągu zapytania `?date=today`.  
  
 Po otrzymaniu żądania serwer i przetworzyć odpowiedzi, zwraca odpowiedź do aplikacji klienckiej. Odpowiedź zawiera dodatkowe informacje, takie jak typ zawartości (nieprzetworzony tekst lub dane XML, na przykład).  
  
## <a name="requests-and-responses-in-the-net-framework"></a>Żądania i odpowiedzi w programie .NET Framework  
 .NET Framework używa określonej klasy, aby zapewnić trzy informacje wymagane do dostępu do zasobów w Internecie za pośrednictwem modelu żądań/odpowiedzi: <xref:System.Uri> klasy, która zawiera identyfikator URI zasobu internetowego szukamy; <xref:System.Net.WebRequest>klasy, która zawiera żądanie dla zasobu. i <xref:System.Net.WebResponse> klasy, która oferuje kontener dla przychodzącą odpowiedź.  
  
 Tworzenie aplikacji klienckich `WebRequest` wystąpień, przekazując identyfikator URI zasobu sieciowego do <xref:System.Net.WebRequest.Create%2A> metody. Ta metoda statyczna tworzy `WebRequest` dla określonego protokołu, takich jak HTTP. `WebRequest` Zwracanym zapewnia dostęp do właściwości, które kontrolują zarówno żądania do serwera i dostęp do strumienia danych, która jest wysyłana, gdy żądanie jest wysyłane. <xref:System.Net.WebRequest.GetResponse%2A> Metody `WebRequest` wysyła żądanie od aplikacji klienckiej na serwerze, który został zidentyfikowany w identyfikatorze URI. W przypadkach, w których mogą być opóźnione odpowiedzi, żądanie może zostać wykonane z asynchronicznie za pomocą <xref:System.Net.WebRequest.BeginGetResponse%2A> metody **WebRequest**, a odpowiedzi mogą być zwracane w późniejszym czasie przy użyciu <xref:System.Net.WebRequest.EndGetResponse%2A> metody.  
  
 **Metody GetResponse** i **EndGetResponse** metody zwracają **elementu WebResponse** , który zapewnia dostęp do danych zwróconych przez serwer. Ponieważ podano te dane do aplikacji żądającej jako strumień przez <xref:System.Net.WebResponse.GetResponseStream%2A> metody może służyć w aplikacji, gdziekolwiek są używane ze strumieni danych.  
  
 **WebRequest** i **elementu WebResponse** klasy stanowią podstawę podłączanych protokołów — implementacja usługi sieciowe umożliwia tworzenie aplikacji korzystających z zasobów internetowych bez martwienia się o określonych szczegółach protokół, który korzysta z każdego zasobu. Zależne kategorie **WebRequest** są zarejestrowane w usłudze **WebRequest** klasy do zarządzania szczegółami dokonywania rzeczywiste połączenia z zasobami internetowymi.  
  
 Na przykład <xref:System.Net.HttpWebRequest> klasa zarządza szczegóły dotyczące nawiązywania połączenia z zasobem internetowym za pośrednictwem protokołu HTTP. Domyślnie gdy **WebRequest.Create** metoda napotka identyfikator URI, który rozpoczyna się od "http:" lub "https:" (identyfikatorów protokołu HTTP i bezpiecznego protokołu HTTP), **WebRequest** zwracanym może służyć jako lub może być rzutowanie typu, aby **HttpWebRequest** uzyskiwania dostępu do właściwości specyficznych dla protokołu. W większości przypadków **WebRequest** zawiera wszystkie informacje niezbędne dla żądania.  
  
 Dowolny protokół, który może być reprezentowany jako transakcja żądania/odpowiedzi mogą być używane w **WebRequest**. Utworzeniu klasy pochodnej klasy związane z Protokołem z **WebRequest** i **elementu WebResponse** , a następnie zarejestruj je do użycia przez aplikację przy użyciu statycznych <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> metody.  
  
 Gdy autoryzacja żądania internetowe klienta jest wymagany, <xref:System.Net.WebRequest.Credentials%2A> właściwość **WebRequest** dostarcza niezbędnych poświadczeń. Te poświadczenia można parę proste nazwy i hasła dla podstawowego HTTP lub uwierzytelniania szyfrowanego lub nazwa/hasło/domenę ustawić podczas uwierzytelniania NTLM i Kerberos. Jeden zestaw poświadczeń mogą być przechowywane w <xref:System.Net.NetworkCredential> wystąpienie lub wiele zestawów mogą być przechowywane w systemie <xref:System.Net.CredentialCache> wystąpienia. **CredentialCache** używa identyfikatora URI żądania i schematu uwierzytelniania serwer obsługuje, aby określić, które poświadczenia do wysyłania do serwera.  
  
## <a name="simple-requests-with-webclient"></a>Proste żądania z WebClient  
 Dla aplikacji, które muszą stosować prostego żądania zasobów internetowych <xref:System.Net.WebClient> klasa udostępnia typowe metody przekazywanie danych do lub pobranie danych z serwera internetowego. **Usługa WebClient** opiera się na **WebRequest** klasy w celu zapewnienia dostępu do zasobów internetowych; w związku z tym, **WebClient** klasy mogą używać zarejestrowanego podłączanych protokołów.  
  
 Aplikacje, które nie mogą używać modelu żądań/odpowiedzi lub aplikacje, które muszą nasłuchiwanie w sieci, a także wysyłać żądania **System.Net.Sockets** przestrzeń nazw zawiera <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>i <xref:System.Net.Sockets.UdpClient> klasy. Te klasy obsługi szczegóły dotyczące nawiązywania połączeń przy użyciu różnych protokołów transportu i udostępnić połączenia sieciowego do aplikacji jako strumień.  
  
 Deweloperom zapoznać się z interfejsu Windows Sockets lub tych, którzy potrzebują kontroli, dostarczone przez programowania na poziomie gniazd zorientujesz się, że **System.Net.Sockets** klasy spełniania ich potrzeb. **System.Net.Sockets** klasy są punkt przejście z kodu zarządzanego do kodu natywnego w ramach **przestrzeni nazw System.Net** klasy. W większości przypadków **System.Net.Sockets** klasy organizowania danych do ich odpowiedników Windows 32-bitowych, jak również wszystkie kontrole zabezpieczeń wymagane do obsługi.  
  
## <a name="see-also"></a>Zobacz także

- [Programowanie protokołów podłączanych](../../../docs/framework/network-programming/programming-pluggable-protocols.md)
- [Programowanie dla sieci w programie .NET Framework](../../../docs/framework/network-programming/index.md)
- [Przykłady programowania sieciowego](../../../docs/framework/network-programming/network-programming-samples.md)
- [Przykłady kodu usług sieciowych dla platformy .NET w galerii kodu MSDN](https://code.msdn.microsoft.com/Wiki/View.aspx?ProjectName=nclsamples)
