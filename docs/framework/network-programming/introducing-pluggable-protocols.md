---
title: Wprowadzenie podłączany protokołów
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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: ef674855d1b9d6538e08ea2bb95f1f63e602d61d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33396393"
---
# <a name="introducing-pluggable-protocols"></a>Wprowadzenie podłączany protokołów
Microsoft .NET Framework udostępnia implementację warstwowych, rozszerzalne i zarządzanych usług internetowych, które można zintegrować szybko i łatwo aplikacji. Dostęp do Internetu klas w <xref:System.Net> i <xref:System.Net.Sockets> przestrzeni nazw może służyć do wdrożenia aplikacji opartych na sieci Web, a internetowy.  
  
## <a name="internet-applications"></a>Aplikacje internetowe  
 Aplikacje internetowe można podzielić na dwa rodzaje szeroko: aplikacje klienckie, które żądają informacji i serwera aplikacji, które odpowiadają na żądania informacje od klientów. Klasycznym aplikacji klient serwer Internet jest sieci World Wide Web, w których użytkownicy korzystają z przeglądarki, aby dostęp do dokumentów i innych danych przechowywanych na serwerach sieci Web na całym świecie.  
  
 Aplikacje nie są ograniczone do tylko jednej z tych ról; na przykład serwer znanych aplikacji warstwy środkowej odpowiada na żądania od klientów na żądanie danych z innego serwera, w tym przypadku działa jako zarówno serwer, jak i klienta.  
  
 Aplikacja kliencka żąda, określając żądanego zasobu internetowego i protokół komunikacyjny na potrzeby żądań i odpowiedzi. W razie potrzeby klient także wszelkich dodatkowych danych wymaganych do wykonania żądania, takie jak lokalizacja lub uwierzytelniania informacje dotyczące serwera proxy (nazwa użytkownika, hasło i tak dalej). Gdy żądanie został utworzony, żądania mogą być wysyłane do serwera.  
  
## <a name="identifying-resources"></a>Identyfikowanie zasobów  
 .NET Framework używana jednolity identyfikator zasobów (URI) żądany protokół zasobów i komunikacja z Internetem. Identyfikator URI, który składa się z co najmniej trzech oraz, ewentualnie, cztery fragmenty: identyfikator schematu, która identyfikuje protokół komunikacji dla żądań i odpowiedzi; Identyfikator serwera, który składa się z nazwy hosta systemu nazw domen (DNS, Domain Name System) lub adres TCP, który unikatowo identyfikuje serwera w Internecie. Identyfikator ścieżki, która lokalizuje żądane informacje na serwerze; i ciągu zapytania opcjonalne i przekazuje informacje z klienta do serwera. Na przykład identyfikator URI "http://www.contoso.com/whatsnew.aspx?date=today" składa się z identyfikatora schematu "http", identyfikator serwera "www.contoso.com", ścieżka "/ whatsnew.aspx" i ciągu zapytania "? Data = dzisiaj".  
  
 Po otrzymaniu żądania i przetworzyć odpowiedzi serwera, zwraca odpowiedź do aplikacji klienckiej. Odpowiedź zawiera dodatkowe informacje, takie jak typ zawartości (nieprzetworzone tekst lub danych XML, na przykład).  
  
## <a name="requests-and-responses-in-the-net-framework"></a>Żądania i odpowiedzi w programie .NET Framework  
 .NET Framework używa określonej klasy, aby zapewnić trzy informacje wymagane do dostępu do zasobów Internetu za pośrednictwem modelu żądanie/odpowiedź: <xref:System.Uri> klasy, która zawiera identyfikator URI zasobu internetowego szukamy; <xref:System.Net.WebRequest>klasy, która zawiera żądanie dla zasobu. i <xref:System.Net.WebResponse> klasy, która udostępnia kontener dla przychodzących odpowiedzi.  
  
 Tworzenie aplikacji klienckich `WebRequest` wystąpień przez przekazanie identyfikatora URI zasobu sieci, aby <xref:System.Net.WebRequest.Create%2A> metody. Ta metoda statyczna tworzy `WebRequest` dla określonego protokołu, takich jak HTTP. `WebRequest` Który jest zwracany zapewnia dostęp do właściwości sterujące zarówno żądanie do serwera i dostęp do strumienia danych, który jest wysyłany, gdy żądanie. <xref:System.Net.WebRequest.GetResponse%2A> Metoda `WebRequest` wysyła żądanie od aplikacji klienta na serwerze określone w identyfikatorze URI. W przypadkach, w których mogą być opóźnione odpowiedzi, żądanie będzie możliwe asynchronicznie za pomocą <xref:System.Net.WebRequest.BeginGetResponse%2A> metoda **WebRequest**, i może być zwracany odpowiedzi na nowsze przy użyciu czasu <xref:System.Net.WebRequest.EndGetResponse%2A> metody.  
  
 **GetResponse** i **EndGetResponse** metody zwracają **WebResponse** , który zapewnia dostęp do danych zwróconych przez serwer. Ponieważ dane te są udostępniane z aplikacją wysyłającą żądania jako strumień przez <xref:System.Net.WebResponse.GetResponseStream%2A> metody, można w aplikacji, gdziekolwiek strumienie danych są używane.  
  
 **WebRequest** i **WebResponse** klasy stanowią podstawę podłączany protokołów — implementację usług sieciowych, która umożliwia tworzenie aplikacji korzystających z zasobów w Internecie bez obaw o określonych szczegółach protokół, który wykorzystuje każdego zasobu. Klasy podrzędne **WebRequest** są zarejestrowane w usłudze **WebRequest** klasy do zarządzania szczegóły rzeczywistych połączeń z zasobami internetowymi.  
  
 Na przykład <xref:System.Net.HttpWebRequest> klasa zarządza szczegóły nawiązywania połączenia z zasobem internetowym przy użyciu protokołu HTTP. Domyślnie podczas **WebRequest.Create** metody napotka identyfikator URI, który rozpoczyna się od ciągu "http:" lub "https:" (identyfikatorów protokołu HTTP i bezpiecznego protokołu HTTP), **WebRequest** który jest zwracany, mogą być używane jako lub jego rzutowanie typu do **HttpWebRequest** do dostępu do właściwości specyficzne dla protokołu. W większości przypadków **WebRequest** zawiera wszystkie informacje niezbędne do tworzenia żądania.  
  
 Każdego protokołu, który może być reprezentowany jako transakcji żądania/odpowiedzi mogą być używane w **WebRequest**. Mogą dziedziczyć klasy specyficzne dla protokołu z **WebRequest** i **WebResponse** , a następnie zarejestruj je do użycia przez aplikację z statycznych <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> metody.  
  
 Gdy jest wymagana, klient autoryzacja dla żądań internetowych <xref:System.Net.WebRequest.Credentials%2A> właściwość **WebRequest** dostarcza niezbędnych poświadczeń. Te poświadczenia można parę proste nazwy i hasła dla podstawowego HTTP lub uwierzytelniania szyfrowanego lub ustawić nazwa/hasło/domeny do uwierzytelniania NTLM lub Kerberos. Jeden zestaw poświadczeń mogą być przechowywane w <xref:System.Net.NetworkCredential> wystąpienia lub wiele zestawów mogą być przechowywane jednocześnie w <xref:System.Net.CredentialCache> wystąpienia. **CredentialCache** używa identyfikatora URI żądania i schemat uwierzytelniania serwera obsługującego Aby określić poświadczenia do wysyłania do serwera.  
  
## <a name="simple-requests-with-webclient"></a>Proste żądania z WebClient  
 Dla aplikacji, które należy podjąć prostego żądania zasobów internetowych <xref:System.Net.WebClient> klasa udostępnia typowe metody przekazywanie danych do lub pobierania danych z serwera internetowego. **WebClient** zależy od **WebRequest** klasy w celu zapewnienia dostępu do zasobów Internetu; w związku z tym **WebClient** klasy mogą używać żadnych zarejestrowanych protokołu podłączanej.  
  
 Dla aplikacji, które nie używają modelu żądań i odpowiedzi lub aplikacji wymagających nasłuchiwanie w sieci, jak również wysyłać żądania **System.Net.Sockets** przestrzeń nazw zawiera <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>i <xref:System.Net.Sockets.UdpClient> klasy. Te klasy obsługi szczegóły połączeń przy użyciu różnych protokołów transportowych i ujawnia połączenie sieciowe z aplikacji jako strumień.  
  
 Deweloperzy zapoznać się z interfejsu Windows Sockets lub osoby, które wymagają kontroli podał programowanie na poziomie gniazda zostanie ustalone, które **System.Net.Sockets** klas konkretnych potrzeb. **System.Net.Sockets** klasy są punkt przejście z kodu zarządzanego do kodu macierzystego w **System.Net** klasy. W większości przypadków **System.Net.Sockets** klasy organizowania danych do ich odpowiedniki 32-bitowego, jak również kontroli zabezpieczeń wymaganymi do obsługi.  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie protokołów podłączanych](../../../docs/framework/network-programming/programming-pluggable-protocols.md)  
 [Programowanie dla sieci w programie .NET Framework](../../../docs/framework/network-programming/index.md)  
 [Przykłady programowania sieciowego](../../../docs/framework/network-programming/network-programming-samples.md)  
 [Przykłady sieci dla platformy .NET w galerii kodu MSDN](http://code.msdn.microsoft.com/Wiki/View.aspx?ProjectName=nclsamples)
