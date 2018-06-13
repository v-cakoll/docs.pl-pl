---
title: Wyprowadzanie z obiektu WebResponse
ms.date: 03/30/2017
helpviewer_keywords:
- Deriving from WebResponse
ms.assetid: f11d4866-a199-4087-9306-a5a4c18b13db
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 14a1260bf67469e792439985fec43ac44c6f0c9f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33395817"
---
# <a name="deriving-from-webresponse"></a>Wyprowadzanie z obiektu WebResponse
<xref:System.Net.WebResponse> Klasa jest abstrakcyjna klasa podstawowa, która udostępnia podstawowe metody i właściwości, do tworzenia odpowiedzi specyficzne dla protokołu, który pasuje do modelu protokołu podłączanej .NET Framework. Aplikacje używające <xref:System.Net.WebRequest> klasy dane żądania z zasobów odbierania odpowiedzi w **WebResponse**. Oparte na protokole **WebResponse** elementy podrzędne muszą implementować abstrakcyjne elementy członkowskie z **WebResponse** klasy.  
  
 Skojarzony **WebRequest** klasy należy utworzyć **WebResponse** elementów podrzędnych. Na przykład <xref:System.Net.HttpWebResponse> wystąpienia są tworzone tylko w wyniku wywołania metody <xref:System.Net.HttpWebRequest.GetResponse%2A?displayProperty=nameWithType> lub <xref:System.Net.HttpWebRequest.EndGetResponse%2A?displayProperty=nameWithType>. Każdy **WebResponse** zawiera wynik żądania z zasobem i nie jest przeznaczona do ponownego wykorzystania.  
  
## <a name="contentlength-property"></a>Właściwość ContentLength  
 <xref:System.Net.WebResponse.ContentLength%2A> Właściwość wskazuje liczbę bajtów danych, które są dostępne ze strumienia zwrócone przez <xref:System.Net.WebResponse.GetResponseStream%2A> metody. **ContentLength** właściwości nie wskazuje liczbę bajtów informacji nagłówka lub metadane zwrócony przez serwer; oznacza tylko liczba bajtów danych żądanego zasobu sam.  
  
## <a name="contenttype-property"></a>Właściwość ContentType  
 <xref:System.Net.WebResponse.ContentType%2A> Właściwość zapewnia wszystkie informacje specjalne protokołu użytkownika wymaga do wysłania do klienta w celu zidentyfikowania typu zawartości, które są wysyłane przez serwer. Zazwyczaj jest to typ zawartości MIME żadnych danych zwracanych.  
  
## <a name="headers-property"></a>Właściwość nagłówki  
 <xref:System.Net.WebResponse.Headers%2A> Właściwość zawiera dowolną kolekcję par nazwa/wartość metadane skojarzone z odpowiedzią. Wszystkie metadane wymagane przez protokół, który może zostać wyrażona jako pary nazwa/wartość może być uwzględniony w **nagłówki** właściwości.  
  
 Nie należy używać **nagłówki** właściwość, aby użyć nagłówka metadanych. Metadane specyficzne dla protokołu może być udostępniany jako właściwości; na przykład <xref:System.Net.HttpWebResponse.LastModified%2A?displayProperty=nameWithType> ujawnia właściwości **Last-Modified** nagłówka HTTP. Gdy uwidaczniać metadane nagłówka jako właściwość, nie należy zezwalać tę samą właściwość można ustawić za pomocą **nagłówki** właściwości.  
  
## <a name="responseuri-property"></a>Właściwość ResponseUri  
 <xref:System.Net.WebResponse.ResponseUri%2A> Właściwość zawiera identyfikator URI zasobu, który faktycznie dostarczony odpowiedzi. Dla protokołów, które nie obsługują przekierowanie **ResponseUri** będzie taka sama jak <xref:System.Net.WebRequest.RequestUri%2A> właściwość **WebRequest** , który utworzył odpowiedzi. Jeśli protokół obsługuje żądania, przekierowywanie **ResponseUri** będzie zawierać identyfikator URI odpowiedzi.  
  
## <a name="close-method"></a>Close — Metoda  
 <xref:System.Net.WebResponse.Close%2A> Metody zamyka wszystkie połączenia przez żądania i odpowiedzi i czyści zasoby wykorzystywane przez odpowiedzi. **Zamknij** metody zamyka wszystkie wystąpienia strumienia używane przez odpowiedzi, ale go nie zgłasza wyjątek, jeśli w strumieniu odpowiedzi wcześniej został zamknięty przez wywołanie do <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> metody.  
  
## <a name="getresponsestream-method"></a>Metody GetResponseStream  
 <xref:System.Net.WebResponse.GetResponseStream%2A> Metoda zwraca strumień zawierające odpowiedzi z żądanego zasobu. W strumieniu odpowiedzi zawiera tylko danych zwróconych przez zasób. nagłówek ani metadanych dołączenia w odpowiedzi powinny być usunięte z odpowiedzi i widoczne dla aplikacji za pomocą właściwości specyficzne dla protokołu lub **nagłówki** właściwości.  
  
 Wystąpienia strumienia zwrócone przez **GetResponseStream** metoda jest należące do aplikacji i może zostać zamknięty bez zamykania **WebResponse**. Według konwencji wywoływania **WebResponse.Close** metoda powoduje zamknięcie Strumień zwrócony przez **GetResponse**.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Net.WebResponse>  
 <xref:System.Net.HttpWebResponse>  
 <xref:System.Net.FileWebResponse>  
 [Programowanie protokołów podłączanych](../../../docs/framework/network-programming/programming-pluggable-protocols.md)  
 [Wyprowadzanie z elementu WebRequest](../../../docs/framework/network-programming/deriving-from-webrequest.md)
