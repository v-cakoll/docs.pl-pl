---
title: Wyprowadzanie z WebRequest
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WebRequest class, pluggable protocols
- protocol-specific request handler
- sending data, pluggable protocols
- pluggable protocols, class criteria
- Internet, pluggable protocols
- receiving data, pluggable protocols
- protocols, pluggable
ms.assetid: 9810c177-973e-43d7-823c-14960bd625ea
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 83579c25c154462cb21488acf9fcf84999b9a2d4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="deriving-from-webrequest"></a>Wyprowadzanie z WebRequest
<xref:System.Net.WebRequest> Klasa jest abstrakcyjna klasa podstawowa, która udostępnia podstawowe metody i właściwości dla tworzenia protokołem żądania obsługi, który pasuje do modelu protokołu podłączanej .NET Framework. Aplikacje używające **WebRequest** klasy można zażądać danych, aby określić protokół używany przy użyciu obsługiwanych protokołów bez konieczności.  
  
 Dwa kryteria muszą zostać spełnione w kolejności dla klasy oparte na protokole ma być używany jako protokołu podłączanej: musi implementować klasę <xref:System.Net.IWebRequestCreate> interfejsu który należy zarejestrować się <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> metody. Klasa musi zastępować wszystkie metody abstrakcyjne i właściwości **WebRequest** podłączany interfejs.  
  
 **WebRequest** wystąpienia są przeznaczone do jednorazowego użytku; Jeśli chcesz utworzyć innego żądania, Utwórz nową **WebRequest**. **WebRequest** obsługuje <xref:System.Runtime.Serialization.ISerializable> interfejs umożliwia deweloperom serializować szablonu **WebRequest** i ponownie skonstruuj szablonu dla dodatkowych żądań.  
  
## <a name="iwebrequest-create-method"></a>IWebRequest Create — metoda  
 <xref:System.Net.IWebRequestCreate.Create%2A> Metody jest odpowiedzialny za inicjowanie nowe wystąpienie klasy specyficzne dla protokołu. Podczas tworzenia nowego **WebRequest** jest tworzony, <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> metody żądanego identyfikatora URI jest zgodny z prefiksy URI zarejestrowany **RegisterPrefix** metody. **Utwórz** metody prawidłowego obiektu podrzędnego protokołem wróć zainicjowane wystąpienia obiektu podrzędnego może wykonać transakcji standardowe żądanie/odpowiedź protokołu bez konieczności żadnego pola oparte na protokole modyfikowane.  
  
## <a name="connectiongroupname-property"></a>Właściwość ConnectionGroupName  
 <xref:System.Net.WebRequest.ConnectionGroupName%2A> Właściwość jest używana do nazwy grupy połączeń do zasobu, aby można było wprowadzić wiele żądań za pośrednictwem jednego połączenia. Aby zaimplementować Udostępnianie połączenia internetowego, należy użyć metody oparte na protokole buforowanie i przypisywanie połączenia. Przykładowo, podana <xref:System.Net.ServicePointManager> klasa implementuje Udostępnianie połączenia dla <xref:System.Net.HttpWebRequest> klasy. **ServicePointManager —** tworzy klasy <xref:System.Net.ServicePoint> zapewnia połączenie z określonym serwerem dla każdej grupy połączeń.  
  
## <a name="contentlength-property"></a>Właściwość ContentLength  
 <xref:System.Net.WebRequest.ContentLength%2A> Właściwość określa liczbę bajtów danych, które zostaną wysłane do serwera podczas przekazywania danych.  
  
 Zazwyczaj <xref:System.Net.WebRequest.Method%2A> musi być ustawiona właściwość, aby wskazać, że trwa przekazywanie umieść kiedy **ContentLength** właściwości ustawiono wartość większą niż zero.  
  
## <a name="contenttype-property"></a>Właściwość ContentType  
 <xref:System.Net.WebRequest.ContentType%2A> Właściwość zapewnia wszystkie informacje specjalne protokołu użytkownika wymaga do wysyłania do serwera, aby zidentyfikować typu zawartości, który jest wysyłany. Zazwyczaj jest to typ zawartości MIME wszelkie dane przekazane.  
  
## <a name="credentials-property"></a>Właściwość poświadczeń  
 <xref:System.Net.WebRequest.Credentials%2A> Właściwość zawiera informacje potrzebne do uwierzytelnienia żądania na serwerze. Szczegóły procesu uwierzytelniania musi implementować sieci protokołu. <xref:System.Net.AuthenticationManager> Klasy jest odpowiedzialny za uwierzytelniania żądań i zapewnianie tokenu uwierzytelniania. Klasa, która zapewnia poświadczenia używane przez użytkownika protokołu musi implementować <xref:System.Net.ICredentials> interfejsu.  
  
## <a name="headers-property"></a>Właściwość nagłówki  
 <xref:System.Net.WebRequest.Headers%2A> Właściwość zawiera dowolną kolekcję par nazwa/wartość metadane skojarzone z żądaniem. Wszystkie metadane wymagane przez protokół, który może zostać wyrażona jako pary nazwa/wartość może być uwzględniony w **nagłówki** właściwości. Zwykle te informacje należy ustawić przed wywołaniem <xref:System.Net.WebRequest.GetRequestStream%2A> lub <xref:System.Net.WebRequest.GetResponse%2A> metod; po wprowadzono żądanie metadanych jest traktowane jako tylko do odczytu.  
  
 Nie należy używać **nagłówki** właściwość, aby użyć nagłówka metadanych. Metadane specyficzne dla protokołu może być udostępniany jako właściwości; na przykład <xref:System.Net.HttpWebRequest.UserAgent%2A?displayProperty=nameWithType> ujawnia właściwości **agenta użytkownika** nagłówka HTTP. Gdy uwidaczniać metadane nagłówka jako właściwość, nie należy zezwalać tę samą właściwość można ustawić za pomocą **nagłówki** właściwości.  
  
## <a name="method-property"></a>Właściwość — metoda  
 <xref:System.Net.WebRequest.Method%2A> Właściwość zawiera zlecenie lub akcję, która jest "proszenia" serwera do wykonania żądania. Wartość domyślna dla **metody** właściwość, należy włączyć działanie standardowe żądanie/odpowiedź bez konieczności ustawiania żadnych właściwości specyficzne dla protokołu. Na przykład <xref:System.Net.HttpWebResponse.Method%2A> ustawienia domyślne metody GET, który żąda zasobu z serwera sieci Web i zwraca odpowiedź.  
  
 Zazwyczaj **ContentLength** właściwości musi być ustawiona na wartość większą niż zero w przypadku **metody** właściwości ustawiono zlecenie lub akcji, która wskazuje, że przekazanie odbywa się.  
  
## <a name="preauthenticate-property"></a>PreAuthenticate właściwości  
 Zestaw aplikacji <xref:System.Net.WebRequest.PreAuthenticate%2A> właściwości, aby wskazać, że informacje o uwierzytelnianiu mają być wysyłane z żądania początkowego zamiast oczekiwania na żądanie uwierzytelniania. **PreAuthenticate** właściwość jest tylko istotne, jeśli protokół obsługuje poświadczenia uwierzytelniania wysyłane z żądania początkowego.  
  
## <a name="proxy-property"></a>Właściwości serwera proxy  
 <xref:System.Net.WebRequest.Proxy%2A> Zawiera właściwość <xref:System.Net.IWebProxy> interfejsu, który umożliwia dostęp do żądanego zasobu. **Proxy** właściwość ma znaczenie tylko wtedy, gdy Twoje protokół obsługuje żądania serwerem proxy. Domyślny serwer proxy musi być ustawiona, jeśli jest on wymagany przez protokół użytkownika.  
  
 W niektórych środowiskach takie jak za firmową zaporą, Twoje protokół może być konieczne do korzystania z serwera proxy. W takim przypadku należy zaimplementować **IWebProxy** interfejsu można utworzyć klasy proxy, który będzie działać z protokołu.  
  
## <a name="requesturi-property"></a>Właściwość RequestUri  
 <xref:System.Net.WebRequest.RequestUri%2A> Właściwość zawiera identyfikator URI, który został przekazany do **WebRequest.Create** metody. Jest tylko do odczytu i nie można zmienić raz **WebRequest** został utworzony. Jeśli Twoje protokołu obsługuje przekierowania, odpowiedzi mogą pochodzić z zasobu identyfikowanego przez inny identyfikator URI. Jeśli należy zapewnić dostęp do identyfikatora URI, który odpowiedzi, należy podać dodatkowe właściwości zawierające tego identyfikatora URI.  
  
## <a name="timeout-property"></a>Właściwość limit czasu  
 <xref:System.Net.WebRequest.Timeout%2A> Właściwość zawiera czas (w milisekundach) oczekiwania na żądanie upłynie limit czasu i zgłasza wyjątek. **Limit czasu** ma zastosowanie tylko do synchroniczne żądań wysyłanych z <xref:System.Net.WebRequest.GetResponse%2A> metody; żądania asynchroniczne muszą używać <xref:System.Net.WebRequest.Abort%2A> metodę, aby anulować oczekujące żądania.  
  
 Ustawienie **limitu czasu** właściwość ma znaczenie tylko wtedy, gdy klasa protokołem implementuje procesu limitu czasu.  
  
## <a name="abort-method"></a>Abort — Metoda  
 <xref:System.Net.WebRequest.Abort%2A> Metody anuluje oczekujące żądania asynchronicznego na serwerze. Po anulowaniu żądania wywoływania **GetResponse**, **BeginGetResponse w czasie**, **EndGetResponse**, **GetRequestStream**,  **Elementu BeginGetRequestStream**, lub **EndGetRequestStream** zgłosi <xref:System.Net.WebException> z <xref:System.Net.WebException.Status%2A> ustawioną właściwość <xref:System.Net.WebExceptionStatus>.  
  
## <a name="begingetrequeststream-and-endgetrequeststream-methods"></a>Elementu BeginGetRequestStream i EndGetRequestStream metody  
 <xref:System.Net.WebRequest.BeginGetRequestStream%2A> Metoda uruchamia asynchroniczne żądanie dla tego strumienia, który służy do przekazywania danych do serwera. <xref:System.Net.WebRequest.EndGetRequestStream%2A> Metoda kończy żądanie asynchroniczne i zwraca strumienia żądane. Wdrożenie tych metod **GetRequestStream** metodę przy użyciu standardowego wzorca asynchronicznego dla platformy .NET Framework.  
  
## <a name="begingetresponse-and-endgetresponse-methods"></a>BeginGetResponse w czasie i metody EndGetResponse  
 <xref:System.Net.WebRequest.BeginGetResponse%2A> Metoda uruchamia asynchroniczne żądanie do serwera. <xref:System.Net.WebRequest.EndGetResponse%2A> Metoda kończy żądanie asynchroniczne i zwraca żądanych odpowiedzi. Wdrożenie tych metod **GetResponse** metodę przy użyciu standardowego wzorca asynchronicznego dla platformy .NET Framework.  
  
## <a name="getrequeststream-method"></a>GetRequestStream — metoda  
 <xref:System.Net.WebRequest.GetRequestStream%2A> Metoda zwraca strumień, który służy do zapisywania danych do żądanego serwera. Strumień zwrócony powinny być tylko do zapisu strumienia, który nie ma; jest on przeznaczony jako jednokierunkowe strumień danych, które są zapisywane na serwerze. Zwraca wartość false dla strumienia <xref:System.IO.Stream.CanRead%2A> i <xref:System.IO.Stream.CanSeek%2A> właściwości i wartość true dla <xref:System.IO.Stream.CanWrite%2A> właściwości.  
  
 **GetRequestStream** metody zazwyczaj otwiera połączenie z serwerem, a przed zwróceniem strumienia, wysyła informacje o nagłówku, która wskazuje, że dane jest wysyłane do serwera. Ponieważ **GetRequestStream** rozpoczyna żądanie dowolne ustawienie **nagłówka** właściwości lub **ContentLength** właściwości zwykle jest niedozwolone po wywołaniu metody **GetRequestStream**.  
  
## <a name="getresponse-method"></a>GetResponse — metoda  
 <xref:System.Net.WebRequest.GetResponse%2A> Metoda zwraca obiekt podrzędny protokołem <xref:System.Net.WebResponse> klasa, która reprezentuje odpowiedzi z serwera. Jeśli żądanie już została zainicjowana przez **GetRequestStream** metody **GetResponse** metoda tworzy połączenie zasobu identyfikowanego przez **RequestUri**, wysyła informacje o nagłówku wskazujący typ żądanie wykonywane i następnie odbiera odpowiedź z zasobu.  
  
 Raz **GetResponse** metoda jest wywoływana, wszystkie właściwości należy traktować jako tylko do odczytu. **WebRequest** wystąpienia są przeznaczone do jednorazowego użytku; mają być innego żądania, należy utworzyć nowy **WebRequest**.  
  
 **GetResponse** metoda jest odpowiedzialna za tworzenie odpowiednie **WebResponse** podrzędne zawierają przychodzące odpowiedzi.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Net.WebRequest>  
 <xref:System.Net.HttpWebRequest>  
 <xref:System.Net.FileWebRequest>  
 [Programowanie protokołów podłączanych](../../../docs/framework/network-programming/programming-pluggable-protocols.md)  
 [Wyprowadzanie z elementu WebResponse](../../../docs/framework/network-programming/deriving-from-webresponse.md)
