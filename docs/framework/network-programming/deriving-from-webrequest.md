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
ms.openlocfilehash: e8e7c1d2943dcbfa8d9faa0b2e53bae57c767101
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59216488"
---
# <a name="deriving-from-webrequest"></a>Wyprowadzanie z elementu WebRequest
<xref:System.Net.WebRequest> Klasa jest abstrakcyjna klasa bazowa, który zawiera podstawowe metody i właściwości dla tworzenia program obsługi żądania związane z protokołem, który pasuje do modelu podłączanego protokołu .NET Framework. Aplikacje, które używają **WebRequest** klasy mogą żądać danych za pomocą dowolnego obsługiwanego protokołu bez konieczności, aby określić protokół używany.  
  
 W kolejności dla klasy związane z protokołem ma być używany jako protokół podłączania, muszą być spełnione dwa kryteria: Klasa musi implementować <xref:System.Net.IWebRequestCreate> interfejsu który należy zarejestrować <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> metody. Klasy należy zastąpić wszystkie metody abstrakcyjne i właściwości **WebRequest** podłączanych interfejs.  
  
 **WebRequest** wystąpień są przeznaczone do jednorazowego użytku; Jeśli chcesz wprowadzić inne żądanie, Utwórz nowe **WebRequest**. **WebRequest** obsługuje <xref:System.Runtime.Serialization.ISerializable> interfejsu, aby umożliwić programistom serializacji szablonu **WebRequest** i następnie odtworzenie szablonu dla dodatkowych żądań.  
  
## <a name="iwebrequest-create-method"></a>Metody Create, IWebRequest  
 <xref:System.Net.IWebRequestCreate.Create%2A> Metody jest odpowiedzialny za inicjowanie nowe wystąpienie klasy specyficzne dla protokołu. Gdy nowy **WebRequest** utworzeniu <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> metody pasuje do żądanego identyfikatora URI prefiksy URI zarejestrowane w usłudze **RegisterPrefix** metody. **Utwórz** metoda prawidłowego obiektu podrzędnego związane z protokołem wróć zainicjowane wystąpienie elementu potomnego może wykonać standardowe żądania/odpowiedzi transakcji dla protokołu bez żadnego pola charakterystyczne dla protokołu zmodyfikowane.  
  
## <a name="connectiongroupname-property"></a>ConnectionGroupName Property  
 <xref:System.Net.WebRequest.ConnectionGroupName%2A> Właściwość jest używany do nazywania grupy połączeń do zasobu, tak aby wiele żądań jest możliwe za pośrednictwem jednego połączenia. Aby zaimplementować Udostępnianie połączenia internetowego, należy użyć metody oparte na protokole, buforowanie i przypisywanie połączeń. Na przykład podana <xref:System.Net.ServicePointManager> klasa implementuje Udostępnianie połączenia dla <xref:System.Net.HttpWebRequest> klasy. **ServicePointManager —** tworzy klasę <xref:System.Net.ServicePoint> , umożliwia połączenie z określonego serwera dla każdej grupy połączeń.  
  
## <a name="contentlength-property"></a>Właściwość ContentLength  
 <xref:System.Net.WebRequest.ContentLength%2A> Właściwość określa liczbę bajtów danych, które zostaną wysłane do serwera podczas przekazywania danych.  
  
 Zazwyczaj <xref:System.Net.WebRequest.Method%2A> można ustawić właściwości, aby wskazać, że trwa przekazywanie gdy **ContentLength** właściwość jest ustawiona na wartość większą niż zero.  
  
## <a name="contenttype-property"></a>Właściwość ContentType  
 <xref:System.Net.WebRequest.ContentType%2A> Właściwość informacje żadnych specjalnych swoje protokół wymaga, można wysyłać do serwera do identyfikacji typów zawartości, które są wysyłane. Zazwyczaj jest to typ zawartości MIME żadnych danych przekazanych.  
  
## <a name="credentials-property"></a>Właściwości poświadczeń  
 <xref:System.Net.WebRequest.Credentials%2A> Właściwość zawiera informacje potrzebne do uwierzytelnienia żądania z serwerem. Szczegółowe informacje o procesie uwierzytelniania musi implementować usługi protokołu. <xref:System.Net.AuthenticationManager> Klasy jest odpowiedzialny za uwierzytelnianie żądań i zapewniając tokenu uwierzytelniania. Musi implementować klasę, która zapewnia poświadczenia używane przez usługi protokołu <xref:System.Net.ICredentials> interfejsu.  
  
## <a name="headers-property"></a>Właściwość nagłówki  
 <xref:System.Net.WebRequest.Headers%2A> Właściwość zawiera dowolną kolekcję par nazwa/wartość metadanych skojarzony z tym żądaniem. Wszystkie metadane wymagane przez protokół, który może być wyrażona jako pary nazwa/wartość mogą być zawarte w **nagłówki** właściwości. Zazwyczaj te informacje należy określić przed wywołaniem <xref:System.Net.WebRequest.GetRequestStream%2A> lub <xref:System.Net.WebRequest.GetResponse%2A> metod; po złożeniu wniosku, metadanych jest traktowane jako tylko do odczytu.  
  
 Nie należy używać **nagłówki** właściwości, aby użyć nagłówka metadanych. Metadane właściwe dla protokołu mogą być widoczne jako właściwości; na przykład <xref:System.Net.HttpWebRequest.UserAgent%2A?displayProperty=nameWithType> ujawnia właściwość **User-Agent** nagłówka HTTP. Jeśli udostępnisz nagłówka metadanych jako właściwość, nie należy zezwalać tę samą właściwość można ustawić za pomocą **nagłówki** właściwości.  
  
## <a name="method-property"></a>Metody właściwości  
 <xref:System.Net.WebRequest.Method%2A> Właściwość zawiera zlecenie lub akcję, która prosi serwer w celu przeprowadzenia żądania. Wartość domyślna dla **metoda** właściwość, należy włączyć działań standardowych żądań/odpowiedzi bez żadnych właściwości specyficzne dla protokołu, należy ustawić. Na przykład <xref:System.Net.HttpWebResponse.Method%2A> wartości domyślne metody GET, żąda zasobu z serwera sieci Web, która zwraca odpowiedź.  
  
 Zazwyczaj **ContentLength** właściwość musi być ustawiona na wartość większą niż zero po **metoda** zostaje ustalona zlecenie lub akcję, która wskazuje, że przekazywanie odbywa się.  
  
## <a name="preauthenticate-property"></a>PreAuthenticate właściwości  
 Zestaw aplikacji <xref:System.Net.WebRequest.PreAuthenticate%2A> właściwości, aby wskazać, że informacje dotyczące uwierzytelniania mają być wysyłane z żądania wstępnego, bez czekania na wezwanie do uwierzytelnienia. **PreAuthenticate** właściwość jest przydatna, jeśli protokół ten obsługuje poświadczenia uwierzytelniania wysyłane z żądania wstępnego tylko.  
  
## <a name="proxy-property"></a>Właściwość serwera proxy  
 <xref:System.Net.WebRequest.Proxy%2A> Właściwość zawiera <xref:System.Net.IWebProxy> interfejs, który umożliwia dostęp do żądanego zasobu. **Proxy** właściwość ma znaczenie tylko wtedy, gdy protokół usługi obsługuje żądania serwerem proxy. Należy ustawić domyślny serwer proxy, jeśli jest on wymagany przez protokół usługi.  
  
 W niektórych środowiskach takich jak za firmową zaporą usługi protokołu może wymagać korzystania z serwera proxy. W takim przypadku należy zaimplementować **IWebProxy** interfejsu, aby utworzyć klasy proxy, który będzie działać z protokołu.  
  
## <a name="requesturi-property"></a>Właściwość RequestUri  
 <xref:System.Net.WebRequest.RequestUri%2A> Właściwość zawiera identyfikator URI, który został przekazany do **WebRequest.Create** metody. Jest tylko do odczytu i nie można zmienić raz **WebRequest** została utworzona. Jeśli protokół usługi obsługuje przekierowania, odpowiedzi mogą pochodzić z zasobu zidentyfikowanego z użyciem innego identyfikatora URI. Jeśli potrzebujesz uzyskać dostęp do identyfikatora URI, który odpowiedzi, należy podać dodatkowe właściwości, zawierającą tego identyfikatora URI.  
  
## <a name="timeout-property"></a>Właściwość limitu czasu  
 <xref:System.Net.WebRequest.Timeout%2A> Właściwość zawiera czas (w milisekundach) oczekiwania, zanim upłynie limit czasu żądania i zgłasza wyjątek. **Limit czasu** ma zastosowanie tylko do synchroniczne żądań wykonywanych przy użyciu <xref:System.Net.WebRequest.GetResponse%2A> metody należy użyć żądań asynchronicznych <xref:System.Net.WebRequest.Abort%2A> metodę, aby anulować oczekujące żądanie.  
  
 Ustawienie **limitu czasu** właściwość ma znaczenie tylko wtedy, gdy klasa określona przez protokół implementuje proces limitu czasu.  
  
## <a name="abort-method"></a>Abort — Metoda  
 <xref:System.Net.WebRequest.Abort%2A> Metoda anuluje oczekiwanie asynchroniczne żądanie do serwera. Po żądanie zostało anulowane, wywołanie **metody GetResponse**, **BeginGetResponse w czasie**, **EndGetResponse**, **GetRequestStream**,  **Elementu BeginGetRequestStream**, lub **EndGetRequestStream** zgłosi <xref:System.Net.WebException> z <xref:System.Net.WebException.Status%2A> właściwością <xref:System.Net.WebExceptionStatus>.  
  
## <a name="begingetrequeststream-and-endgetrequeststream-methods"></a>Elementu BeginGetRequestStream i metod EndGetRequestStream  
 <xref:System.Net.WebRequest.BeginGetRequestStream%2A> Metoda uruchamia asynchroniczne żądanie dla strumienia, który służy do przekazywania danych do serwera. <xref:System.Net.WebRequest.EndGetRequestStream%2A> Metody ukończenia żądania asynchronicznego i zwraca żądany strumień. Te metody wdrożenia **GetRequestStream** metody przy użyciu standardowego wzorca asynchronicznego środowiska .NET Framework.  
  
## <a name="begingetresponse-and-endgetresponse-methods"></a>Metody EndGetResponse i BeginGetResponse w czasie  
 <xref:System.Net.WebRequest.BeginGetResponse%2A> Metoda uruchamia asynchroniczne żądanie do serwera. <xref:System.Net.WebRequest.EndGetResponse%2A> Metody ukończenia żądania asynchronicznego i zwraca żądana odpowiedź. Te metody wdrożenia **metody GetResponse** metody przy użyciu standardowego wzorca asynchronicznego środowiska .NET Framework.  
  
## <a name="getrequeststream-method"></a>Metoda GetRequestStream  
 <xref:System.Net.WebRequest.GetRequestStream%2A> Metoda zwraca strumień, który jest używany do zapisywania danych żądanego serwera. Strumień zwrócony powinny być tylko do zapisu strumienia, który nie ma; jest on przeznaczony jako jednokierunkowe strumień danych, które są zapisywane do serwera. Zwraca wartość false dla strumienia <xref:System.IO.Stream.CanRead%2A> i <xref:System.IO.Stream.CanSeek%2A> właściwości i wartość true dla <xref:System.IO.Stream.CanWrite%2A> właściwości.  
  
 **GetRequestStream** metoda zazwyczaj otwiera połączenie z serwerem, i przed zwróceniem strumienia, wysyła informacje nagłówka, który wskazuje, że dane jest wysyłanych do serwera. Ponieważ **GetRequestStream** rozpoczyna żądanie dowolne ustawienie **nagłówka** właściwości lub **ContentLength** właściwość nie jest zazwyczaj dozwolona po wywołaniu **GetRequestStream**.  
  
## <a name="getresponse-method"></a>Metody GetResponse — metoda  
 <xref:System.Net.WebRequest.GetResponse%2A> Metoda zwraca obiekt podrzędny związane z protokołem <xref:System.Net.WebResponse> klasa, która reprezentuje odpowiedź z serwera. Chyba, że żądania została zainicjowana przez **GetRequestStream** metody **metody GetResponse** metoda utworzyła połączenie z zasobu zidentyfikowanego z użyciem **RequestUri**, wysyła informacje o nagłówku wskazujący typ żądanie wykonywane i odbiera odpowiedź z zasobu.  
  
 Gdy **metody GetResponse** metoda jest wywoływana, należy rozważyć wszystkie właściwości tylko do odczytu. **WebRequest** wystąpień są przeznaczone do jednorazowego użytku; Jeśli chcesz wprowadzić inne żądanie, należy utworzyć nową **WebRequest**.  
  
 **Metody GetResponse** metoda jest odpowiedzialna za tworzenie odpowiednich **elementu WebResponse** podrzędnych zawiera przychodzącą odpowiedź.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Net.WebRequest>
- <xref:System.Net.HttpWebRequest>
- <xref:System.Net.FileWebRequest>
- [Programowanie protokołów podłączanych](../../../docs/framework/network-programming/programming-pluggable-protocols.md)
- [Wyprowadzanie z elementu WebResponse](../../../docs/framework/network-programming/deriving-from-webresponse.md)
