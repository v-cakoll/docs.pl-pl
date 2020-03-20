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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047400"
---
# <a name="programming-pluggable-protocols"></a>Programowanie protokołów podłączanych
Abstrakcyjne <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> i klasy stanowią podstawę dla protokołów podłączanych. Poprzez wyprowadzanie klas specyficznych dla protokołu z <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse>, aplikacja może żądać danych z zasobu internetowego i odczytać odpowiedź bez określania używanego protokołu.  
  
 Przed utworzeniem specyficznego <xref:System.Net.WebRequest>dla protokołu, należy zarejestrować jego Create metody. Użyj metody <xref:System.Net.WebRequest.RegisterPrefix%28System.String%2CSystem.Net.IWebRequestCreate%29> statycznej, <xref:System.Net.WebRequest> aby <xref:System.Net.WebRequest> zarejestrować element podrzędny do obsługi zestawu żądań do określonego schematu internetowego, do schematu i serwera lub do schematu, serwera i ścieżki.  
  
 W większości przypadków będzie można wysyłać i odbierać dane <xref:System.Net.WebRequest> przy użyciu metod i właściwości klasy. Jednak jeśli chcesz uzyskać dostęp do właściwości specyficznych dla <xref:System.Net.WebRequest> protokołu, można typecast do określonego wystąpienia klasy pochodnej.  
  
 Aby skorzystać z protokołów pluggable, elementy <xref:System.Net.WebRequest> podrzędne muszą podać domyślną transakcję żądania i odpowiedzi, która nie wymaga ustawienia właściwości specyficznych dla protokołu. Na przykład <xref:System.Net.HttpWebRequest> klasa, która implementuje <xref:System.Net.WebRequest> klasę dla `GET` protokołu HTTP, domyślnie dostarcza żądanie i zwraca <xref:System.Net.HttpWebResponse> strumień zwracany z serwera sieci Web.  
  
## <a name="see-also"></a>Zobacz też

- [Wyprowadzanie z elementu WebRequest](deriving-from-webrequest.md)
- [Wyprowadzanie z elementu WebResponse](deriving-from-webresponse.md)
- [Programowanie dla sieci w programie .NET Framework](index.md)
- [Instrukcje: rzutowanie elementu WebRequest w celu uzyskania dostępu do właściwości specyficznych dla protokołu](how-to-typecast-a-webrequest-to-access-protocol-specific-properties.md)
