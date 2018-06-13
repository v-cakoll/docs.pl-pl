---
title: Protokoły podłączany programowania
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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: fe9f9216c00448391967b82c84207f95eaccdb53
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33396145"
---
# <a name="programming-pluggable-protocols"></a>Protokoły podłączany programowania
Abstract <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse> klasy podanie podłączany protokołów podstawowym. Przez wyprowadzanie klasy specyficzne dla protokołu z <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse>, aplikacji można dane żądania z zasobu internetowego i bez określania protokołu używanego do odczytu odpowiedzi.  
  
 Przed utworzeniem oparte na protokole <xref:System.Net.WebRequest>, należy zarejestrować jego metody Create. Użyj statycznych <xref:System.Net.WebRequest.RegisterPrefix%28System.String%2CSystem.Net.IWebRequestCreate%29> metody <xref:System.Net.WebRequest> zarejestrować <xref:System.Net.WebRequest> elementów podrzędnych do obsługi żądań do określonego schematu Internet, schemat i serwer lub do schematu, serwera i ścieżki zestawu.  
  
 W większości przypadków będzie mógł wysyłać i odbierać dane przy użyciu metody i właściwości <xref:System.Net.WebRequest> klasy. Jednak jeśli potrzebujesz dostępu do właściwości specyficzne dla protokołu, użytkownik może rzutowanie typu <xref:System.Net.WebRequest> określonego wystąpienia klas pochodnych.  
  
 Aby móc korzystać z protokołów podłączane z <xref:System.Net.WebRequest> descendants musi podać transakcji żądanie i odpowiedź domyślna, która nie wymaga właściwości specyficzne dla protokołu. Na przykład <xref:System.Net.HttpWebRequest> klasy, która implementuje <xref:System.Net.WebRequest> klasy do obsługi protokołu HTTP, zapewnia `GET` żądanie domyślnie i zwraca <xref:System.Net.HttpWebResponse> zawierający strumienia zwrócone z serwera sieci Web.  
  
## <a name="see-also"></a>Zobacz też  
 [Wyprowadzanie z elementu WebRequest](../../../docs/framework/network-programming/deriving-from-webrequest.md)  
 [Wyprowadzanie z elementu WebResponse](../../../docs/framework/network-programming/deriving-from-webresponse.md)  
 [Programowanie dla sieci w programie .NET Framework](../../../docs/framework/network-programming/index.md)  
 [Instrukcje: rzutowanie elementu WebRequest w celu uzyskania dostępu do właściwości specyficznych dla protokołu](../../../docs/framework/network-programming/how-to-typecast-a-webrequest-to-access-protocol-specific-properties.md)
