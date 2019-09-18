---
title: Programowanie protokołów podłączanych
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
ms.openlocfilehash: 94dfedd317782b9e518df02c84d9af55b1ef2b69
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047400"
---
# <a name="programming-pluggable-protocols"></a>Programowanie protokołów podłączanych
Abstrakcyjne <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse> klasy stanowią podstawę dla protokołów podłączanych. Dzięki wykorzystaniu klas specyficznych dla <xref:System.Net.WebRequest> protokołu <xref:System.Net.WebResponse>z i, aplikacja może zażądać danych z zasobu internetowego i odczytać odpowiedź bez określania używanego protokołu.  
  
 Aby można było utworzyć specyficzny <xref:System.Net.WebRequest>dla protokołu, należy zarejestrować metodę Create. Użyj <xref:System.Net.WebRequest.RegisterPrefix%28System.String%2CSystem.Net.IWebRequestCreate%29> <xref:System.Net.WebRequest> metody statycznej w celu zarejestrowania elementu podrzędnego w celu obsługi zestawu żądań do określonego schematu internetowego, schematu i serwera, lub schematu, serwera i ścieżki. <xref:System.Net.WebRequest>  
  
 W większości przypadków będzie można wysyłać i odbierać dane przy użyciu metod i właściwości <xref:System.Net.WebRequest> klasy. Jeśli jednak chcesz uzyskać dostęp do właściwości specyficznych dla protokołu, możesz rzutowanie a <xref:System.Net.WebRequest> do określonego wystąpienia klasy pochodnej.  
  
 Aby móc korzystać z protokołów podłączanych, <xref:System.Net.WebRequest> elementy podrzędne muszą udostępniać domyślną transakcję żądanie-odpowiedź, która nie wymaga ustawiania właściwości specyficznych dla protokołu. Na przykład <xref:System.Net.HttpWebRequest> Klasa, która <xref:System.Net.WebRequest> implementuje klasę `GET` dla protokołu HTTP, domyślnie zapewnia żądanie i zwraca <xref:System.Net.HttpWebResponse> wartość zawierającą Strumień zwrócony z serwera sieci Web.  
  
## <a name="see-also"></a>Zobacz także

- [Wyprowadzanie z elementu WebRequest](deriving-from-webrequest.md)
- [Wyprowadzanie z elementu WebResponse](deriving-from-webresponse.md)
- [Programowanie dla sieci w programie .NET Framework](index.md)
- [Instrukcje: Rzutowanie żądania sieci Webw celu uzyskania dostępu do właściwości specyficznych dla protokołu](how-to-typecast-a-webrequest-to-access-protocol-specific-properties.md)
