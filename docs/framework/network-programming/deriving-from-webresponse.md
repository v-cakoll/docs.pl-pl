---
title: Wyprowadzanie z elementu WebResponse
ms.date: 03/30/2017
helpviewer_keywords:
- Deriving from WebResponse
ms.assetid: f11d4866-a199-4087-9306-a5a4c18b13db
ms.openlocfilehash: 6bdb21b8aaf8deb39e3abd68a69a9a5a10247e6f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59226048"
---
# <a name="deriving-from-webresponse"></a>Wyprowadzanie z elementu WebResponse
<xref:System.Net.WebResponse> Klasa jest abstrakcyjna klasa bazowa, który udostępnia podstawowe metody i właściwości, do tworzenia odpowiedzi związane z protokołem, który pasuje do modelu podłączanego protokołu .NET Framework. Aplikacje, które używają <xref:System.Net.WebRequest> klasy, żeby dane żądania z zasobów otrzymywać odpowiedzi w **elementu WebResponse**. Oparte na protokole **elementu WebResponse** elementy podrzędne muszą implementować członków abstrakcyjnych z **elementu WebResponse** klasy.  
  
 Skojarzone **WebRequest** należy utworzyć klasę **elementu WebResponse** elementów podrzędnych. Na przykład <xref:System.Net.HttpWebResponse> wystąpienia są tworzone tylko w wyniku wywołania metody <xref:System.Net.HttpWebRequest.GetResponse%2A?displayProperty=nameWithType> lub <xref:System.Net.HttpWebRequest.EndGetResponse%2A?displayProperty=nameWithType>. Każdy **elementu WebResponse** zawiera wynik żądania do zasobu i nie ma na celu można użyć ponownie.  
  
## <a name="contentlength-property"></a>Właściwość ContentLength  
 <xref:System.Net.WebResponse.ContentLength%2A> Właściwość wskazuje liczbę bajtów danych, które są dostępne z Strumień zwrócony przez <xref:System.Net.WebResponse.GetResponseStream%2A> metody. **ContentLength** właściwości nie wskazuje liczbę bajtów informacje nagłówka lub metadane, które są zwracane przez serwer; oznacza to, tylko liczbę bajtów danych w żądanej samego zasobu.  
  
## <a name="contenttype-property"></a>Właściwość ContentType  
 <xref:System.Net.WebResponse.ContentType%2A> Właściwość informacje żadnych specjalnych protokołu usługi wymaga do wysłania do klienta, aby zidentyfikować typ zawartości, które są wysyłane przez serwer. Zazwyczaj jest to typ zawartości MIME wszelkich zwróconych danych.  
  
## <a name="headers-property"></a>Właściwość nagłówki  
 <xref:System.Net.WebResponse.Headers%2A> Właściwość zawiera dowolną kolekcję par nazwa/wartość metadane skojarzone z odpowiedzią. Wszystkie metadane wymagane przez protokół, który może być wyrażona jako pary nazwa/wartość mogą być zawarte w **nagłówki** właściwości.  
  
 Nie należy używać **nagłówki** właściwości, aby użyć nagłówka metadanych. Metadane właściwe dla protokołu mogą być widoczne jako właściwości; na przykład <xref:System.Net.HttpWebResponse.LastModified%2A?displayProperty=nameWithType> ujawnia właściwość **ostatniej modyfikacji** nagłówka HTTP. Jeśli udostępnisz nagłówka metadanych jako właściwość, nie należy zezwalać tę samą właściwość można ustawić za pomocą **nagłówki** właściwości.  
  
## <a name="responseuri-property"></a>Właściwość ResponseUri  
 <xref:System.Net.WebResponse.ResponseUri%2A> Właściwość zawiera identyfikator URI zasobu, który faktycznie podany odpowiedź. Protokoły, które nie obsługują przekierowanie **ResponseUri** będzie taka sama jak <xref:System.Net.WebRequest.RequestUri%2A> właściwość **WebRequest** które tworzone odpowiedzi. Jeśli protokół ten obsługuje przekierowywanie żądań, **ResponseUri** będzie zawierać identyfikator URI odpowiedzi.  
  
## <a name="close-method"></a>Close — Metoda  
 <xref:System.Net.WebResponse.Close%2A> Metoda zamyka wszystkie połączenia dokonanych przez żądania i odpowiedzi i czyści zasoby wykorzystywane przez odpowiedzi. **Zamknij** metoda zamyka wszystkie wystąpienia strumienia używane przez odpowiedzi, ale nie zostanie zgłoszony wyjątek, jeśli w strumieniu odpowiedzi wcześniej zostało zamknięte przez wywołanie <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> metody.  
  
## <a name="getresponsestream-method"></a>Metoda GetResponseStream dla  
 <xref:System.Net.WebResponse.GetResponseStream%2A> Metoda zwraca strumień zawierające odpowiedzi z żądanego zasobu. W strumieniu odpowiedzi zawiera tylko dane zwrócone przez zasób. nagłówek dowolnej metadanych dołączony do odpowiedzi powinny być usunięte z odpowiedzi i widoczne dla aplikacji za pomocą właściwości specyficzne dla protokołu lub **nagłówki** właściwości.  
  
 Wystąpienie strumienia, zwrócone przez **GetResponseStream dla** metoda należące do aplikacji i może zostać zamknięty bez zamykania **elementu WebResponse**. Zgodnie z Konwencją wywoływania **WebResponse.Close** metoda również zamyka Strumień zwrócony przez **metody GetResponse**.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Net.WebResponse>
- <xref:System.Net.HttpWebResponse>
- <xref:System.Net.FileWebResponse>
- [Programowanie protokołów podłączanych](../../../docs/framework/network-programming/programming-pluggable-protocols.md)
- [Wyprowadzanie z elementu WebRequest](../../../docs/framework/network-programming/deriving-from-webrequest.md)
