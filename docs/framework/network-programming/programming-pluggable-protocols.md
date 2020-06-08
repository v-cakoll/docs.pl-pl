---
title: Programowanie protokołów podłączanych
description: Dowiedz się, jak klasy abstrakcyjne i WebResponse są obsługiwane przez podłączane protokoły, które umożliwiają aplikacji pobieranie danych bez określania protokołu.
ms.date: 03/30/2017
helpviewer_keywords:
- downloading Internet resources, pluggable protocols
- WebRequest class, pluggable protocols
- response to Internet request, pluggable protocols
- WebResponse class, pluggable protocols
- sending data, pluggable protocols
- network resources, pluggable protocols
- Internet, pluggable protocols
- programming pluggable protocols
- pluggable protocols, programming
- requesting data from Internet, pluggable protocols
- receiving data, pluggable protocols
- protocols, pluggable
ms.assetid: 66ef8456-7576-4e97-8956-959b216373db
ms.openlocfilehash: 510f616295abc13d93e0e0af5a37aca097d343e3
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502200"
---
# <a name="programming-pluggable-protocols"></a>Programowanie protokołów podłączanych
Abstrakcyjne <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse> klasy stanowią podstawę dla protokołów podłączanych. Dzięki wykorzystaniu klas specyficznych dla protokołu z <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse> , aplikacja może zażądać danych z zasobu internetowego i odczytać odpowiedź bez określania używanego protokołu.  
  
 Aby można było utworzyć specyficzny dla protokołu <xref:System.Net.WebRequest> , należy zarejestrować metodę Create. Użyj metody statycznej <xref:System.Net.WebRequest.RegisterPrefix%28System.String%2CSystem.Net.IWebRequestCreate%29> <xref:System.Net.WebRequest> w celu zarejestrowania <xref:System.Net.WebRequest> elementu podrzędnego w celu obsługi zestawu żądań do określonego schematu internetowego, schematu i serwera, lub schematu, serwera i ścieżki.  
  
 W większości przypadków będzie można wysyłać i odbierać dane przy użyciu metod i właściwości <xref:System.Net.WebRequest> klasy. Jeśli jednak chcesz uzyskać dostęp do właściwości specyficznych dla protokołu, możesz rzutowanie a <xref:System.Net.WebRequest> do określonego wystąpienia klasy pochodnej.  
  
 Aby móc korzystać z protokołów podłączanych, <xref:System.Net.WebRequest> elementy podrzędne muszą udostępniać domyślną transakcję żądanie-odpowiedź, która nie wymaga ustawiania właściwości specyficznych dla protokołu. Na przykład <xref:System.Net.HttpWebRequest> Klasa, która implementuje <xref:System.Net.WebRequest> klasę dla protokołu HTTP, `GET` Domyślnie zapewnia żądanie i zwraca wartość <xref:System.Net.HttpWebResponse> zawierającą Strumień zwrócony z serwera sieci Web.  
  
## <a name="see-also"></a>Zobacz także

- [Wyprowadzanie z elementu WebRequest](deriving-from-webrequest.md)
- [Wyprowadzanie z elementu WebResponse](deriving-from-webresponse.md)
- [Programowanie dla sieci w programie .NET Framework](index.md)
- [Instrukcje: rzutowanie elementu WebRequest w celu uzyskania dostępu do właściwości specyficznych dla protokołu](how-to-typecast-a-webrequest-to-access-protocol-specific-properties.md)
