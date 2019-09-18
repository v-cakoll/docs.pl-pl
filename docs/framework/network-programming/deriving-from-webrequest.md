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
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048599"
---
# <a name="deriving-from-webrequest"></a>Wyprowadzanie z elementu WebRequest
<xref:System.Net.WebRequest> Klasa jest abstrakcyjną klasą bazową, która udostępnia podstawowe metody i właściwości służące do tworzenia obsługi żądań specyficznych dla protokołu, które pasują do .NET Framework modelu protokołów podłączanych. Aplikacje korzystające z klasy **WebRequest** mogą żądać danych przy użyciu dowolnego obsługiwanego protokołu bez konieczności określania używanego protokołu.  
  
 Aby klasa specyficzna dla protokołu mogła być używana jako podłączany protokół, muszą być spełnione dwa kryteria: Klasa musi implementować <xref:System.Net.IWebRequestCreate> interfejs i musi być zarejestrowana <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> przy użyciu metody. Klasa musi zastąpić wszystkie metody abstrakcyjne i właściwości elementu **WebRequest** w celu zapewnienia podłączanego interfejsu.  
  
 Wystąpienia **WebRequest** są przeznaczone do jednorazowego użytku; Jeśli chcesz wykonać kolejne żądanie, Utwórz nowe **żądanie**sieci Web. Usługa **WebRequest** obsługuje <xref:System.Runtime.Serialization.ISerializable> interfejs, aby umożliwić deweloperom serializację serializacji **żądania WebRequest** , a następnie odtworzyć szablon pod kątem dodatkowych żądań.  
  
## <a name="iwebrequest-create-method"></a>IWebRequest — metoda tworzenia  
 <xref:System.Net.IWebRequestCreate.Create%2A> Metoda jest odpowiedzialna za Inicjowanie nowego wystąpienia klasy specyficznej dla protokołu. Po utworzeniu <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> nowego **żądania WebRequest** Metoda dopasowuje żądany identyfikator URI przy użyciu prefiksów URI zarejestrowanych przy użyciu metody **RegisterPrefix** . Metoda **Create** odpowiedniego elementu zależnego od protokołu musi zwracać zainicjowane wystąpienie elementu podrzędnego, które może przetworzyć standardową transakcję żądania/odpowiedzi dla protokołu bez modyfikowania żadnych pól specyficznych dla protokołu .  
  
## <a name="connectiongroupname-property"></a>ConnectionGroupName Property  
 <xref:System.Net.WebRequest.ConnectionGroupName%2A> Właściwość służy do nadania nazwy grupie połączeń z zasobem, dzięki czemu można wykonać wiele żądań za pośrednictwem jednego połączenia. Aby zaimplementować udostępnianie połączenia, należy zastosować specyficzną dla protokołu metodę buforowania i przypisywania połączeń. Na przykład podaną <xref:System.Net.ServicePointManager> klasę implementuje Udostępnianie połączenia <xref:System.Net.HttpWebRequest> dla klasy. Klasa **ServicePointManager** tworzy <xref:System.Net.ServicePoint> , która zapewnia połączenie z określonym serwerem dla każdej grupy połączeń.  
  
## <a name="contentlength-property"></a>Właściwość ContentLength  
 <xref:System.Net.WebRequest.ContentLength%2A> Właściwość określa liczbę bajtów danych, które zostaną wysłane do serwera podczas przekazywania danych.  
  
 Zazwyczaj właściwość musi być ustawiona, aby wskazać, że odbywa się przekazywanie, gdy właściwość ContentLength jest ustawiona na wartość większą od zera. <xref:System.Net.WebRequest.Method%2A>  
  
## <a name="contenttype-property"></a>ContentType — Właściwość  
 <xref:System.Net.WebRequest.ContentType%2A> Właściwość zawiera wszelkie specjalne informacje, które są wymagane do wysłania przez protokół do serwera w celu zidentyfikowania typu wysyłanej zawartości. Zwykle jest to typ zawartości MIME dla przekazanych danych.  
  
## <a name="credentials-property"></a>Właściwość poświadczeń  
 <xref:System.Net.WebRequest.Credentials%2A> Właściwość zawiera informacje, które są konieczne do uwierzytelnienia żądania na serwerze. Należy zaimplementować szczegóły procesu uwierzytelniania dla używanego protokołu. <xref:System.Net.AuthenticationManager> Klasa jest odpowiedzialna za uwierzytelnianie żądań i dostarczanie tokenu uwierzytelniania. Klasa, która dostarcza poświadczenia używane przez protokół, musi implementować <xref:System.Net.ICredentials> interfejs.  
  
## <a name="headers-property"></a>Heads — Właściwość  
 <xref:System.Net.WebRequest.Headers%2A> Właściwość zawiera arbitralną kolekcję par nazwa/wartość metadanych skojarzonych z żądaniem. Wszystkie metadane potrzebne przez protokół, które mogą być wyrażone jako para nazwa/wartość, mogą być zawarte we właściwości **Heads** . Zazwyczaj te informacje muszą być ustawione przed wywołaniem <xref:System.Net.WebRequest.GetRequestStream%2A> lub <xref:System.Net.WebRequest.GetResponse%2A> metodami; po wykonaniu żądania metadane są uznawane za tylko do odczytu.  
  
 Nie jest wymagane używanie właściwości **Headers** do używania metadanych nagłówka. Metadane specyficzne dla protokołu mogą być uwidocznione jako właściwości; na przykład <xref:System.Net.HttpWebRequest.UserAgent%2A?displayProperty=nameWithType> Właściwość uwidacznia nagłówek HTTP **User-Agent** . Po udostępnieniu metadanych nagłówka jako właściwości nie należy zezwalać na ustawienie tej samej właściwości przy użyciu właściwości **Heads** .  
  
## <a name="method-property"></a>Właściwość metody  
 <xref:System.Net.WebRequest.Method%2A> Właściwość zawiera zlecenie lub akcję, którą żądanie żąda serwera do wykonania. Wartość domyślna właściwości **Metoda** musi umożliwiać standardowe działanie żądania/odpowiedzi bez konieczności ustawiania właściwości specyficznych dla protokołu. Na przykład <xref:System.Net.HttpWebResponse.Method%2A> Metoda przyjmuje wartość domyślną Get, która żąda zasobu z serwera sieci Web i zwraca odpowiedź.  
  
 Zazwyczaj Właściwość **ContentLength** musi być ustawiona na wartość większą od zera, gdy właściwość **metody** jest ustawiona na czasownik lub akcję, która wskazuje, że odbywa się przekazywanie.  
  
## <a name="preauthenticate-property"></a>Właściwość preuwierzytelniana  
 Aplikacje ustawiają <xref:System.Net.WebRequest.PreAuthenticate%2A> właściwość, aby wskazać, że informacje o uwierzytelnianiu powinny być wysyłane z żądaniem początkowym, a nie w oczekiwaniu na wyzwanie uwierzytelniania. Właściwość preauthentication ma znaczenie tylko w **przypadku, gdy** protokół obsługuje poświadczenia uwierzytelniania wysyłane z żądaniem początkowym.  
  
## <a name="proxy-property"></a>Właściwość serwera proxy  
 <xref:System.Net.WebRequest.Proxy%2A> Właściwość<xref:System.Net.IWebProxy> zawiera interfejs, który jest używany w celu uzyskania dostępu do żądanego zasobu. Właściwość **proxy** ma znaczenie tylko wtedy, gdy protokół obsługuje żądania proxy. Należy ustawić domyślny serwer proxy, jeśli jest wymagany przez protokół.  
  
 W niektórych środowiskach, takich jak za zaporą firmową, do korzystania z serwera proxy może być wymagany protokół. W takim przypadku należy zaimplementować interfejs **IWebProxy** , aby utworzyć klasę proxy, która będzie działała na potrzeby protokołu.  
  
## <a name="requesturi-property"></a>Właściwość RequestUri  
 Właściwość zawiera identyfikator URI, który został przesłany do metody **WebRequest. Create.** <xref:System.Net.WebRequest.RequestUri%2A> Jest on tylko do odczytu i nie można go zmienić po utworzeniu **żądania WebRequest** . Jeśli protokół obsługuje przekierowywanie, odpowiedź może pochodzić z zasobu identyfikowanego przy użyciu innego identyfikatora URI. Jeśli musisz zapewnić dostęp do identyfikatora URI, który odpowiedział, musisz podać dodatkową właściwość zawierającą ten identyfikator URI.  
  
## <a name="timeout-property"></a>Właściwość Timeout  
 <xref:System.Net.WebRequest.Timeout%2A> Właściwość zawiera czas oczekiwania (w milisekundach), po upływie którego żądanie przekroczy limit czasu i zgłosi wyjątek. **Limit czasu** ma zastosowanie tylko do żądań synchronicznych <xref:System.Net.WebRequest.GetResponse%2A> wykonanych przy użyciu metody; <xref:System.Net.WebRequest.Abort%2A> żądania asynchroniczne muszą używać metody, aby anulować oczekujące żądanie.  
  
 Ustawienie właściwości **timeout** ma znaczenie tylko wtedy, gdy klasa specyficzna dla protokołu implementuje proces przekroczenia limitu czasu.  
  
## <a name="abort-method"></a>Abort — Metoda  
 <xref:System.Net.WebRequest.Abort%2A> Metoda anuluje oczekujące asynchroniczne żądanie do serwera. Po anulowaniu żądania wywołanie metody **GetResponse**, **BeginGetResponse**, **EndGetResponse**, **GetRequestStream**, **BeginGetRequestStream**lub **EndGetRequestStream** spowoduje zgłoszenie elementu <xref:System.Net.WebException> Właściwość ustawiona na <xref:System.Net.WebExceptionStatus>. <xref:System.Net.WebException.Status%2A>  
  
## <a name="begingetrequeststream-and-endgetrequeststream-methods"></a>Metody BeginGetRequestStream i EndGetRequestStream  
 <xref:System.Net.WebRequest.BeginGetRequestStream%2A> Metoda uruchamia asynchroniczne żądanie dla strumienia, który jest używany do przekazywania danych na serwer. <xref:System.Net.WebRequest.EndGetRequestStream%2A> Metoda kończy asynchroniczne żądanie i zwraca żądany strumień. Te metody implementują metodę **GetRequestStream** przy użyciu standardowego wzorca asynchronicznego .NET Framework.  
  
## <a name="begingetresponse-and-endgetresponse-methods"></a>Metody BeginGetResponse i EndGetResponse  
 <xref:System.Net.WebRequest.BeginGetResponse%2A> Metoda uruchamia asynchroniczne żądanie do serwera. <xref:System.Net.WebRequest.EndGetResponse%2A> Metoda kończy asynchroniczne żądanie i zwraca żądaną odpowiedź. Te metody implementują metodę **GetResponse** przy użyciu wzorca asynchronicznego .NET Framework standardowego.  
  
## <a name="getrequeststream-method"></a>GetRequestStream, Metoda  
 <xref:System.Net.WebRequest.GetRequestStream%2A> Metoda zwraca strumień, który jest używany do zapisywania danych na żądanym serwerze. Zwrócony strumień powinien być strumieniem tylko do zapisu, który nie poszukuje; jest ona przeznaczona do jednokierunkowego strumienia danych, które są zapisywane na serwerze. Strumień zwraca wartość false dla <xref:System.IO.Stream.CanRead%2A> <xref:System.IO.Stream.CanWrite%2A> właściwości i <xref:System.IO.Stream.CanSeek%2A> i ma wartość true dla właściwości.  
  
 Metoda **GetRequestStream** zazwyczaj otwiera połączenie z serwerem i, przed zwróceniem strumienia, wysyła informacje nagłówka, które wskazują, że dane są wysyłane do serwera. Ponieważ **GetRequestStream** rozpoczyna żądanie, ustawienie właściwości **nagłówka** lub właściwości **ContentLength** zazwyczaj nie jest dozwolone po wywołaniu **GetRequestStream**.  
  
## <a name="getresponse-method"></a>GetResponse — metoda  
 Metoda zwraca specyficzny dla protokołu element podrzędny <xref:System.Net.WebResponse> klasy, która reprezentuje odpowiedź z serwera. <xref:System.Net.WebRequest.GetResponse%2A> O ile żądanie zostało już zainicjowane przez metodę **GetRequestStream** , Metoda **GetResponse** tworzy połączenie z zasobem identyfikowanym przez **RequestUri**, wysyła informacje nagłówka wskazujące typ tworzonego żądania , a następnie otrzymuje odpowiedź z zasobu.  
  
 Po wywołaniu metody **GetResponse** wszystkie właściwości należy traktować jako tylko do odczytu. Wystąpienia **WebRequest** są przeznaczone do jednorazowego użytku; Jeśli chcesz wykonać kolejne żądanie, należy utworzyć nowe **żądanie WebRequest**.  
  
 Metoda **GetResponse** jest odpowiedzialna za utworzenie odpowiedniego elementu podrzędnego **WebResponse** w celu przechowywania odpowiedzi przychodzącej.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Net.WebRequest>
- <xref:System.Net.HttpWebRequest>
- <xref:System.Net.FileWebRequest>
- [Programowanie protokołów podłączanych](programming-pluggable-protocols.md)
- [Wyprowadzanie z elementu WebResponse](deriving-from-webresponse.md)
