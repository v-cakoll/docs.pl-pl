---
title: Tworzenie żądań internetowych
description: Dowiedz się, jak aplikacje tworzą wystąpienia WebRequest za pośrednictwem metody WebRequest. Create, która tworzy klasę pochodną na podstawie przeprowadzonego do niego schematu URI.
ms.date: 03/30/2017
helpviewer_keywords:
- WebRequest class, sending and receiving data
- Networking
- HttpWebResponse class, sending and receiving data
- requesting data from Internet, creating requests
- Network Resources
- Internet, requesting data
- data requests, creating requests
ms.assetid: faab683e-3f1e-4eee-b5e9-59f7245033d5
ms.openlocfilehash: 389c7bf5969eca4322aa680a6f28dec0b899709a
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325638"
---
# <a name="create-internet-requests"></a>Utwórz żądania internetowe

Aplikacje tworzą <xref:System.Net.WebRequest> wystąpienia za pomocą <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> metody. <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType>to metoda statyczna, która tworzy klasę pochodną <xref:System.Net.WebRequest> w oparciu o schemat identyfikatora URI, do którego został przesłany.  
  
## <a name="web-file-and-ftp-requests"></a>Żądania sieci Web, plików i FTP

.NET Framework udostępnia <xref:System.Net.HttpWebRequest> klasę, która pochodzi od `WebRequest` , do obsługi żądań HTTP i https. W większości przypadków `WebRequest` Klasa zawiera wszystkie właściwości, które są potrzebne do wykonania żądania. jednak w razie potrzeby można rzutować `WebRequest` obiekty utworzone przez `WebRequest.Create` metodę na `HttpWebRequest` Typ, aby uzyskać dostęp do właściwości żądania specyficznego dla protokołu HTTP. Podobnie `HttpWebResponse` obiekt obsługuje odpowiedzi z żądań HTTP i https. Aby uzyskać dostęp do właściwości specyficznych dla protokołu HTTP `HttpWebResponse` obiektu, należy rzutować `WebResponse` obiekty na `HttpWebResponse` Typ.  
  
.NET Framework udostępnia również <xref:System.Net.FileWebRequest> klasy i <xref:System.Net.FileWebResponse> obsługujące żądania dla zasobów, które używają schematu identyfikatora URI "File:". Podobnie <xref:System.Net.FtpWebRequest> <xref:System.Net.FtpWebResponse> klasy i są udostępniane do obsługi żądań dotyczących zasobów, które używają schematu "FTP:". Jeśli Twoje żądanie dotyczy zasobu korzystającego z dowolnego z tych schematów, można użyć `WebRequest.Create` metody, aby uzyskać obiekt, z którego ma być wysłane żądanie.  
  
Aby obsługiwać żądania korzystające z innych protokołów na poziomie aplikacji, należy zaimplementować klasy specyficzne dla protokołu pochodzące z `WebRequest` i `WebResponse` . Aby uzyskać więcej informacji, zobacz [programowanie protokołów podłączanych](programming-pluggable-protocols.md).  
  
## <a name="see-also"></a>Zobacz też

- [Instrukcje: żądanie danych przy użyciu klasy WebRequest](how-to-request-data-using-the-webrequest-class.md)
- [Żądanie danych](requesting-data.md)
