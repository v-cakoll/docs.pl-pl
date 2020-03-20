---
title: Wyprowadzanie z elementu WebRequest
ms.date: 03/30/2017
helpviewer_keywords:
- WebRequest class, pluggable protocols
- protocol-specific request handler
- sending data, pluggable protocols
- pluggable protocols, class criteria
- Internet, pluggable protocols
- receiving data, pluggable protocols
- protocols, pluggable
ms.assetid: 9810c177-973e-43d7-823c-14960bd625ea
ms.openlocfilehash: 6bee864f8d24076d16f226c29d61801e856739d9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048599"
---
# <a name="deriving-from-webrequest"></a>Wyprowadzanie z elementu WebRequest
Klasa <xref:System.Net.WebRequest> jest abstrakcyjną klasą podstawową, która udostępnia podstawowe metody i właściwości tworzenia programu obsługi żądań specyficznych dla protokołu, który pasuje do modelu protokołu .NET Framework pluggable protocol. Aplikacje korzystające z klasy **WebRequest** mogą żądać danych przy użyciu dowolnego obsługiwanego protokołu bez konieczności określania używanego protokołu.  
  
 Muszą być spełnione dwa kryteria, aby klasa specyficzne dla protokołu była używana jako protokół <xref:System.Net.IWebRequestCreate> pluggable: Klasa <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> musi implementować interfejs i musi zarejestrować się przy użyciu metody. Klasa musi zastąpić wszystkie metody abstrakcyjne i właściwości **WebRequest,** aby zapewnić interfejs pluggable.  
  
 **WebRequest** wystąpienia są przeznaczone do jednorazowego użytku; jeśli chcesz złożyć kolejne żądanie, utwórz nowy **WebRequest**. **WebRequest** obsługuje <xref:System.Runtime.Serialization.ISerializable> interfejs, aby umożliwić deweloperom serializacji **szablonu WebRequest,** a następnie zrekonstruować szablon dla dodatkowych żądań.  
  
## <a name="iwebrequest-create-method"></a>Metoda tworzenia iWebRequest  
 Metoda <xref:System.Net.IWebRequestCreate.Create%2A> jest odpowiedzialna za inicjowanie nowego wystąpienia klasy specyficznej dla protokołu. Po utworzeniu nowego <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> **WebRequest,** metoda pasuje do żądanego identyfikatora URI z prefiksami URI zarejestrowanymi za pomocą **metody RegisterPrefix.** Create **Create** Metoda właściwego protokołu specyficznego elementa podrzędnego musi zwracać zainicjowane wystąpienie elementa podrzędnego zdolnego do wykonywania standardowej transakcji żądania/odpowiedzi dla protokołu bez konieczności modyfikowanego pola specyficznego dla protokołu.  
  
## <a name="connectiongroupname-property"></a>Właściwość ConnectionGroupName  
 Właściwość <xref:System.Net.WebRequest.ConnectionGroupName%2A> jest używana do nazwy grupy połączeń z zasobem, dzięki czemu można nawiązywać wiele żądań za pośrednictwem jednego połączenia. Aby zaimplementować udostępnianie połączeń, należy użyć specyficznej dla protokołu metody buforowania i przypisywania połączeń. Na przykład podana <xref:System.Net.ServicePointManager> klasa implementuje <xref:System.Net.HttpWebRequest> udostępnianie połączenia dla klasy. **Klasa ServicePointManager** <xref:System.Net.ServicePoint> tworzy, który zapewnia połączenie z określonym serwerem dla każdej grupy połączeń.  
  
## <a name="contentlength-property"></a>Właściwość ContentLength  
 Właściwość <xref:System.Net.WebRequest.ContentLength%2A> określa liczbę bajtów danych, które będą wysyłane do serwera podczas przekazywania danych.  
  
 Zazwyczaj <xref:System.Net.WebRequest.Method%2A> właściwość musi być ustawiona, aby wskazać, że przekazywanie odbywa się, gdy **ContentLength** właściwość jest ustawiona na wartość większą niż zero.  
  
## <a name="contenttype-property"></a>Właściwość ContentType  
 Właściwość <xref:System.Net.WebRequest.ContentType%2A> zawiera wszelkie specjalne informacje, które protokół wymaga wysłania do serwera w celu zidentyfikowania typu zawartości, które wysyłasz. Zazwyczaj jest to typ zawartości MIME wszystkich przesłanych danych.  
  
## <a name="credentials-property"></a>Właściwość poświadczenia  
 Właściwość <xref:System.Net.WebRequest.Credentials%2A> zawiera informacje potrzebne do uwierzytelnienia żądania z serwerem. Należy zaimplementować szczegóły procesu uwierzytelniania protokołu. Klasa <xref:System.Net.AuthenticationManager> jest odpowiedzialna za uwierzytelnianie żądań i dostarczanie tokenu uwierzytelniania. Klasa, która zawiera poświadczenia używane przez protokół <xref:System.Net.ICredentials> musi implementować interfejs.  
  
## <a name="headers-property"></a>Właściwość nagłówków  
 Właściwość <xref:System.Net.WebRequest.Headers%2A> zawiera dowolną kolekcję pary nazw/wartości metadanych skojarzonych z żądaniem. Wszystkie metadane wymagane przez protokół, które mogą być wyrażone jako para nazwa/wartość mogą być zawarte w **Headers** właściwości. Zazwyczaj te informacje muszą być <xref:System.Net.WebRequest.GetRequestStream%2A> ustawione <xref:System.Net.WebRequest.GetResponse%2A> przed wywołaniem lub metody; po zdaniu żądania metadane są uznawane za tylko do odczytu.  
  
 Nie musisz używać właściwości **Nagłówki** do używania metadanych nagłówka. Metadane specyficzne dla protokołu mogą być udostępniane jako właściwości; na przykład <xref:System.Net.HttpWebRequest.UserAgent%2A?displayProperty=nameWithType> właściwość udostępnia nagłówek HTTP **agenta użytkownika.** Podczas uwidaczniania metadanych nagłówka jako właściwości, nie należy zezwalać na tę samą właściwość, aby ustawić przy użyciu **headers** właściwości.  
  
## <a name="method-property"></a>Właściwość metody  
 Właściwość <xref:System.Net.WebRequest.Method%2A> zawiera zlecenie lub akcję, która żądać prosi serwer do wykonania. Wartość domyślna dla **Method** właściwość musi włączyć akcję żądania/odpowiedzi standardowej bez konieczności ustawiania żadnych właściwości specyficznych dla protokołu. Na przykład <xref:System.Net.HttpWebResponse.Method%2A> metoda domyślnie GET, który żąda zasobu z serwera sieci Web i zwraca odpowiedź.  
  
 Zazwyczaj **ContentLength** właściwość musi być ustawiona na wartość większą niż zero, gdy **Method** właściwość jest ustawiona na zlecenie lub akcji, która wskazuje, że przekazywanie ma miejsce.  
  
## <a name="preauthenticate-property"></a>Właściwość preauthenticate  
 Aplikacje <xref:System.Net.WebRequest.PreAuthenticate%2A> ustawić właściwość, aby wskazać, że informacje o uwierzytelnianiu powinny być wysyłane z początkowego żądania, a nie czeka na wyzwanie uwierzytelniania. **Właściwość PreAuthenticate** ma znaczenie tylko wtedy, gdy protokół obsługuje poświadczenia uwierzytelniania wysyłane z żądaniem początkowym.  
  
## <a name="proxy-property"></a>Właściwość serwera proxy  
 Właściwość <xref:System.Net.WebRequest.Proxy%2A> zawiera <xref:System.Net.IWebProxy> interfejs, który jest używany do uzyskiwania dostępu do żądanego zasobu. Właściwość **serwera proxy** ma znaczenie tylko wtedy, gdy protokół obsługuje proxied żądań. Należy ustawić domyślny serwer proxy, jeśli jest wymagany przez protokół.  
  
 W niektórych środowiskach, takich jak za zaporą firmową, protokół może być wymagany do użycia serwera proxy. W takim przypadku należy zaimplementować interfejs **IWebProxy,** aby utworzyć klasę proxy, która będzie działać dla protokołu.  
  
## <a name="requesturi-property"></a>Właściwość RequestUri  
 Właściwość <xref:System.Net.WebRequest.RequestUri%2A> zawiera identyfikator URI, który został przekazany do **WebRequest.Create** metody. Jest tylko do odczytu i nie można go zmienić po utworzeniu **WebRequest.** Jeśli protokół obsługuje przekierowanie, odpowiedź może pochodzić z zasobu zidentyfikowanego przez inny identyfikator URI. Jeśli musisz zapewnić dostęp do identyfikatora URI, który odpowiedział, należy podać dodatkową właściwość zawierającą ten identyfikator URI.  
  
## <a name="timeout-property"></a>Właściwość limit czasu  
 Właściwość <xref:System.Net.WebRequest.Timeout%2A> zawiera czas, w milisekundach, aby czekać przed upłyniem czasu żądania i zgłasza wyjątek. **Limit czasu** ma zastosowanie tylko do synchronicznych żądań wykonanych za <xref:System.Net.WebRequest.GetResponse%2A> pomocą metody; asynchroniczne żądania należy <xref:System.Net.WebRequest.Abort%2A> użyć metody, aby anulować oczekujące żądanie.  
  
 Ustawienie **Timeout** właściwość ma znaczenie tylko wtedy, gdy klasa specyficzne dla protokołu implementuje proces limitu czasu.  
  
## <a name="abort-method"></a>Abort — Metoda  
 Metoda <xref:System.Net.WebRequest.Abort%2A> anuluje oczekujące żądanie asynchroniczne do serwera. Po anulowaniu żądania **wywołanie GetResponse**, **BeginGetResponse**, **EndGetResponse**, **GetRequestStream**, **BeginGetRequestStream** <xref:System.Net.WebException> lub <xref:System.Net.WebException.Status%2A> **EndGetRequestStream** spowoduje wrzucenie a z właściwością ustawioną na <xref:System.Net.WebExceptionStatus>.  
  
## <a name="begingetrequeststream-and-endgetrequeststream-methods"></a>Metody BeginGetRequestStream i EndGetRequestStream  
 Metoda <xref:System.Net.WebRequest.BeginGetRequestStream%2A> uruchamia asynchroniczne żądanie dla strumienia, który jest używany do przekazywania danych na serwer. Metoda <xref:System.Net.WebRequest.EndGetRequestStream%2A> kończy żądanie asynchroniczne i zwraca żądany strumień. Te metody implementują **GetRequestStream** metody przy użyciu standardowego wzorca asynchronicznym .NET Framework.  
  
## <a name="begingetresponse-and-endgetresponse-methods"></a>Metody BeginGetResponse i EndGetResponse  
 Metoda <xref:System.Net.WebRequest.BeginGetResponse%2A> uruchamia żądanie asynchroniczne do serwera. Metoda <xref:System.Net.WebRequest.EndGetResponse%2A> kończy żądanie asynchroniczne i zwraca żądaną odpowiedź. Te metody implementują **GetResponse** metody przy użyciu standardowego wzorca asynchroniczne .NET Framework.  
  
## <a name="getrequeststream-method"></a>Metoda GetRequestStream  
 Metoda <xref:System.Net.WebRequest.GetRequestStream%2A> zwraca strumień, który jest używany do zapisywania danych na żądanym serwerze. Strumień zwrócony powinien być strumień tylko do zapisu, który nie szuka; jest przeznaczony jako strumień jednokierunkowy danych, który jest zapisywany na serwerze. Strumień zwraca false <xref:System.IO.Stream.CanRead%2A> dla <xref:System.IO.Stream.CanSeek%2A> i właściwości i <xref:System.IO.Stream.CanWrite%2A> true dla właściwości.  
  
 **GetRequestStream** Metoda zazwyczaj otwiera połączenie z serwerem i przed zwróceniem strumienia, wysyła informacje nagłówka, który wskazuje, że dane są wysyłane do serwera. Ponieważ **GetRequestStream** rozpoczyna żądanie, ustawienie żadnych właściwości **nagłówka** lub **ContentLength** właściwość jest zazwyczaj niedozwolone po wywołaniu **GetRequestStream**.  
  
## <a name="getresponse-method"></a>Metoda GetResponse  
 Metoda <xref:System.Net.WebRequest.GetResponse%2A> zwraca element podrzędny specyficzne <xref:System.Net.WebResponse> dla protokołu klasy, która reprezentuje odpowiedź z serwera. Chyba że żądanie zostało już zainicjowane przez **GetRequestStream** metody, **GetResponse** metoda tworzy połączenie z zasobem identyfikowane przez **RequestUri**, wysyła informacje nagłówka wskazując typ żądania, a następnie odbiera odpowiedź z zasobu.  
  
 Po **wywołaniu GetResponse** metoda, wszystkie właściwości powinny być traktowane tylko do odczytu. **WebRequest** wystąpienia są przeznaczone do jednorazowego użytku; jeśli chcesz złożyć kolejne żądanie, należy utworzyć nowy **WebRequest**.  
  
 **Metoda GetResponse** jest odpowiedzialna za tworzenie odpowiedniego elementa podrzędnego **WebResponse,** który zawiera odpowiedź przychodzącą.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Net.WebRequest>
- <xref:System.Net.HttpWebRequest>
- <xref:System.Net.FileWebRequest>
- [Programowanie protokołów podłączanych](programming-pluggable-protocols.md)
- [Wyprowadzanie z elementu WebResponse](deriving-from-webresponse.md)
