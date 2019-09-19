---
title: Wyprowadzanie z elementu WebResponse
ms.date: 03/30/2017
helpviewer_keywords:
- Deriving from WebResponse
ms.assetid: f11d4866-a199-4087-9306-a5a4c18b13db
ms.openlocfilehash: bd06928b08eb085ef13371687fb1e5b92c6c1d86
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048579"
---
# <a name="deriving-from-webresponse"></a>Wyprowadzanie z elementu WebResponse
<xref:System.Net.WebResponse> Klasa jest abstrakcyjną klasą bazową, która udostępnia podstawowe metody i właściwości służące do tworzenia odpowiedzi specyficznej dla protokołu, która pasuje do .NET Framework modelu protokołów podłączanych. Aplikacje, które używają <xref:System.Net.WebRequest> klasy do żądania danych z zasobów odbierają odpowiedzi w **WebResponse**. Elementy podrzędne **WebResponse** specyficzne dla protokołu muszą implementować abstrakcyjne elementy członkowskie klasy **WebResponse** .  
  
 Skojarzona Klasa **WebRequest** musi tworzyć elementy podrzędne **WebResponse** . Na przykład <xref:System.Net.HttpWebResponse> wystąpienia są tworzone tylko w wyniku wywołania <xref:System.Net.HttpWebRequest.GetResponse%2A?displayProperty=nameWithType> lub <xref:System.Net.HttpWebRequest.EndGetResponse%2A?displayProperty=nameWithType>. Każdy **WebResponse** zawiera wynik żądania do zasobu i nie jest przeznaczony do użycia ponownie.  
  
## <a name="contentlength-property"></a>Właściwość ContentLength  
 Właściwość wskazuje liczbę bajtów danych, które są dostępne ze strumienia zwróconego <xref:System.Net.WebResponse.GetResponseStream%2A> przez metodę. <xref:System.Net.WebResponse.ContentLength%2A> Właściwość **ContentLength** nie wskazuje liczby bajtów informacji o nagłówku lub metadanych zwracanych przez serwer; wskazuje tylko liczbę bajtów danych w żądanym zasobie.  
  
## <a name="contenttype-property"></a>ContentType — Właściwość  
 <xref:System.Net.WebResponse.ContentType%2A> Właściwość zawiera wszelkie specjalne informacje, które są wymagane przez protokół do wysłania do klienta w celu zidentyfikowania typu zawartości wysyłanej przez serwer. Zwykle jest to typ zawartości MIME zwracanych danych.  
  
## <a name="headers-property"></a>Heads — Właściwość  
 <xref:System.Net.WebResponse.Headers%2A> Właściwość zawiera arbitralną kolekcję par nazwa/wartość metadanych skojarzonych z odpowiedzią. Wszystkie metadane potrzebne przez protokół, które mogą być wyrażone jako para nazwa/wartość, mogą być zawarte we właściwości **Heads** .  
  
 Nie jest wymagane używanie właściwości **Headers** do używania metadanych nagłówka. Metadane specyficzne dla protokołu mogą być uwidocznione jako właściwości; na przykład <xref:System.Net.HttpWebResponse.LastModified%2A?displayProperty=nameWithType> Właściwość uwidacznia **ostatnio zmodyfikowanego** nagłówka HTTP. Po udostępnieniu metadanych nagłówka jako właściwości nie należy zezwalać na ustawienie tej samej właściwości przy użyciu właściwości **Heads** .  
  
## <a name="responseuri-property"></a>Właściwość ResponseUri  
 <xref:System.Net.WebResponse.ResponseUri%2A> Właściwość zawiera identyfikator URI zasobu, który faktycznie podał odpowiedź. W przypadku protokołów, które nie obsługują przekierowania, **ResponseUri** będzie taka sama jak <xref:System.Net.WebRequest.RequestUri%2A> Właściwość **żądania** Web, która utworzyła odpowiedź. Jeśli protokół obsługuje przekierowywanie żądania, **ResponseUri** będzie zawierać identyfikator URI odpowiedzi.  
  
## <a name="close-method"></a>Close — Metoda  
 <xref:System.Net.WebResponse.Close%2A> Metoda zamyka wszystkie połączenia wykonywane przez żądanie i odpowiedź i czyści zasoby używane przez odpowiedź. Metoda **Close** zamyka wszystkie wystąpienia strumienia używane przez odpowiedź, ale nie zgłasza wyjątku, jeśli strumień odpowiedzi został wcześniej zamknięty przez wywołanie <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> metody.  
  
## <a name="getresponsestream-method"></a>Metody GetResponseStream, Metoda  
 <xref:System.Net.WebResponse.GetResponseStream%2A> Metoda zwraca strumień zawierający odpowiedź z żądanego zasobu. Strumień odpowiedzi zawiera tylko dane zwrócone przez zasób; wszystkie nagłówki lub metadane zawarte w odpowiedzi powinny być usuwane z odpowiedzi i udostępniane aplikacji za pośrednictwem właściwości specyficznych dla protokołu lub właściwości **Heads** .  
  
 Wystąpienie strumienia zwrócone przez metodę **metody GetResponseStream** jest własnością aplikacji i może być zamknięte bez zamykania **WebResponse**. Zgodnie z Konwencją wywołanie metody **WebResponse. Close** zamyka również Strumień zwrócony przez metodę **GetResponse**.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Net.WebResponse>
- <xref:System.Net.HttpWebResponse>
- <xref:System.Net.FileWebResponse>
- [Programowanie protokołów podłączanych](programming-pluggable-protocols.md)
- [Wyprowadzanie z elementu WebRequest](deriving-from-webrequest.md)
