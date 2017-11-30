---
title: "Tworzenie żądania internetowe"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WebRequest class, sending and receiving data
- Networking
- HttpWebResponse class, sending and receiving data
- requesting data from Internet, creating requests
- Network Resources
- Internet, requesting data
- data requests, creating requests
ms.assetid: faab683e-3f1e-4eee-b5e9-59f7245033d5
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 52f1fc2601aca9b4d823d42ed961fcf007e5e5ce
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="creating-internet-requests"></a>Tworzenie żądania internetowe
Tworzenie aplikacji <xref:System.Net.WebRequest> wystąpienia za pośrednictwem <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> metody. To jest metodą statyczną, która tworzy klasę pochodzącą od **WebRequest** oparte na schemat identyfikatora URI przekazywania.  
  
## <a name="web-file-and-ftp-requests"></a>Sieci Web, plików i żądań FTP  
 Platforma .NET Framework zapewnia <xref:System.Net.HttpWebRequest> klasy, która jest pochodną **WebRequest**, do obsługi żądań HTTP i HTTPS. W większości przypadków **WebRequest** klasy zawiera wszystkie właściwości, musisz wysłać żądanie; jednak, w razie potrzeby można rzutować **WebRequest** obiekty utworzone przez **WebRequest.Create**  metodę **HttpWebRequest** typ, aby uzyskać dostęp do właściwości specyficzne dla protokołu HTTP żądania. Podobnie **HttpWebResponse** obiektu obsługuje odpowiedzi z żądań HTTP i HTTPS. Aby uzyskać dostęp do właściwości specyficzne dla protokołu HTTP **HttpWebResponse** obiektu, należy rzutować **WebResponse** obiekty do **HttpWebResponse** typu.  
  
 .NET Framework są także <xref:System.Net.FileWebRequest> i <xref:System.Net.FileWebResponse> klasy do obsługi żądań zasobów, które używają "plików:" schemat identyfikatora URI. Podobnie <xref:System.Net.FtpWebRequest> i <xref:System.Net.FtpWebResponse> klasy są dostarczane do obsługi żądań zasobów, które używają "ftp:" schematu. Jeśli żądanie dotyczy z zasobem, który wykorzystuje dowolne z tych systemów, możesz użyć **WebRequest.Create** metodę, aby uzyskać obiekt, z którym z żądania.  
  
 Do obsługi żądań, które używają inne protokoły poziomu aplikacji, musisz wdrożyć pochodzi od klasy oparte na protokole **WebRequest** i **WebResponse**. Aby uzyskać więcej informacji, zobacz [programowania podłączany protokołów](../../../docs/framework/network-programming/programming-pluggable-protocols.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: dane przy użyciu klasy WebRequest żądania](../../../docs/framework/network-programming/how-to-request-data-using-the-webrequest-class.md)  
 [Żądanie danych](../../../docs/framework/network-programming/requesting-data.md)
