---
title: Wyprowadzanie z elementu WebResponse
ms.date: 03/30/2017
helpviewer_keywords:
- Deriving from WebResponse
ms.assetid: f11d4866-a199-4087-9306-a5a4c18b13db
ms.openlocfilehash: bd06928b08eb085ef13371687fb1e5b92c6c1d86
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048579"
---
# <a name="deriving-from-webresponse"></a>Wyprowadzanie z elementu WebResponse
Klasa <xref:System.Net.WebResponse> jest abstrakcyjną klasą podstawową, która udostępnia podstawowe metody i właściwości tworzenia odpowiedzi specyficznej dla protokołu, która pasuje do modelu protokołu .NET Framework pluggable protocol. Aplikacje, <xref:System.Net.WebRequest> które używają tej klasy do żądania danych z zasobów, otrzymują odpowiedzi w **webresponse**. Elementy **podrzędne webresponse** specyficzne dla protokołu muszą implementować abstrakcyjne elementy członkowskie klasy **WebResponse.**  
  
 Skojarzona klasa **WebRequest** musi utworzyć elementy **podrzędne WebResponse.** Na przykład <xref:System.Net.HttpWebResponse> wystąpienia są tworzone tylko w <xref:System.Net.HttpWebRequest.GetResponse%2A?displayProperty=nameWithType> <xref:System.Net.HttpWebRequest.EndGetResponse%2A?displayProperty=nameWithType>wyniku wywołania lub . Każda **webresponse** zawiera wynik żądania do zasobu i nie jest przeznaczony do ponownego użycia.  
  
## <a name="contentlength-property"></a>Właściwość ContentLength  
 Właściwość <xref:System.Net.WebResponse.ContentLength%2A> wskazuje liczbę bajtów danych, które są dostępne <xref:System.Net.WebResponse.GetResponseStream%2A> ze strumienia zwróconego przez metodę. **Właściwość ContentLength** nie wskazuje liczby bajtów informacji nagłówka lub metadanych zwracanych przez serwer; wskazuje tylko liczbę bajtów danych w samym żądanym zasobie.  
  
## <a name="contenttype-property"></a>Właściwość ContentType  
 Właściwość <xref:System.Net.WebResponse.ContentType%2A> zawiera wszelkie specjalne informacje, które protokół wymaga wysłania do klienta w celu zidentyfikowania typu zawartości wysyłanej przez serwer. Zazwyczaj jest to typ zawartości MIME zwracanych danych.  
  
## <a name="headers-property"></a>Właściwość nagłówków  
 Właściwość <xref:System.Net.WebResponse.Headers%2A> zawiera dowolną kolekcję pary nazw/wartości metadanych skojarzonych z odpowiedzią. Wszystkie metadane wymagane przez protokół, które mogą być wyrażone jako para nazwa/wartość mogą być zawarte w **Headers** właściwości.  
  
 Nie musisz używać właściwości **Nagłówki** do używania metadanych nagłówka. Metadane specyficzne dla protokołu mogą być udostępniane jako właściwości; na przykład <xref:System.Net.HttpWebResponse.LastModified%2A?displayProperty=nameWithType> właściwość udostępnia **nagłówek HTTP ostatniej modyfikacji.** Podczas uwidaczniania metadanych nagłówka jako właściwości, nie należy zezwalać na tę samą właściwość, aby ustawić przy użyciu **headers** właściwości.  
  
## <a name="responseuri-property"></a>Właściwość ResponseUri  
 Właściwość <xref:System.Net.WebResponse.ResponseUri%2A> zawiera identyfikator URI zasobu, który faktycznie pod warunkiem odpowiedzi. Dla protokołów, które nie obsługują przekierowania **ResponseUri** <xref:System.Net.WebRequest.RequestUri%2A> będzie taka sama jak właściwość **WebRequest,** który utworzył odpowiedź. Jeśli protokół obsługuje przekierowywanie **żądania, ResponseUri** będzie zawierać identyfikator URI odpowiedzi.  
  
## <a name="close-method"></a>Close — Metoda  
 Metoda <xref:System.Net.WebResponse.Close%2A> zamyka wszystkie połączenia wykonane przez żądanie i odpowiedź i czyści zasoby używane przez odpowiedź. **Close** Metoda zamyka wszelkie wystąpienia strumienia używane przez odpowiedź, ale nie zgłasza wyjątek, jeśli strumień <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> odpowiedzi został wcześniej zamknięty przez wywołanie metody.  
  
## <a name="getresponsestream-method"></a>Metoda GetResponseStream  
 Metoda <xref:System.Net.WebResponse.GetResponseStream%2A> zwraca strumień zawierający odpowiedź z żądanego zasobu. Strumień odpowiedzi zawiera tylko dane zwracane przez zasób; każdy nagłówek lub metadane zawarte w odpowiedzi powinny zostać usunięte z odpowiedzi i narażone na aplikację za pośrednictwem właściwości specyficznych dla protokołu lub **headers** właściwości.  
  
 Wystąpienie strumienia **zwrócone przez GetResponseStream** metoda jest własnością aplikacji i może być zamknięty bez zamykania **WebResponse**. Zgodnie z konwencją wywołanie **Metody WebResponse.Close** również zamyka strumień zwrócony przez **GetResponse**.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Net.WebResponse>
- <xref:System.Net.HttpWebResponse>
- <xref:System.Net.FileWebResponse>
- [Programowanie protokołów podłączanych](programming-pluggable-protocols.md)
- [Wyprowadzanie z elementu WebRequest](deriving-from-webrequest.md)
