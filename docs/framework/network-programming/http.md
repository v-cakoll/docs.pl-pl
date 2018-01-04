---
title: HTTP
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- protocols, HTTP
- sending data, HTTP
- HttpWebResponse class, sending and receiving data
- HTTP
- receiving data, HTTP
- application protocols, HTTP
- Internet, HTTP
- network resources, HTTP
- HTTP, about HTTP
- HttpWebRequest class, sending and receiving data
ms.assetid: 985fe5d8-eb71-4024-b361-41fbdc1618d8
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: f72a77e19d04c0dd55887628033f7c975ac3ff25
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="http"></a>HTTP
.NET Framework zapewnia kompleksowe obsługę protokołu HTTP, dzięki czemu większość cały ruch internetowy, z <xref:System.Net.HttpWebRequest> i <xref:System.Net.HttpWebResponse> klasy. Te klasy wyprowadzone z <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse>, zwracane są domyślnie zawsze, gdy metody statycznej <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> napotka przez identyfikator URI rozpoczynający się od "http" lub "https". W większości przypadków **WebRequest** i **WebResponse** klasy podać wszystko jest to niezbędne do zapewnienia żądania, ale jeśli potrzebny jest dostęp do funkcji specyficzne dla protokołu HTTP udostępniony jako właściwości, można rzutowanie typu te klasy do **HttpWebRequest** lub **HttpWebResponse**.  
  
 **HttpWebRequest** i **HttpWebResponse** hermetyzują standardowy transakcji żądanie i odpowiedź HTTP i zapewnienia dostępu do typowych nagłówków HTTP. Te klasy również obsługiwać większość funkcje protokołu HTTP 1.1, w tym przetwarzanie potokowe, wysyłania i odbierania danych w fragmentów, uwierzytelniania wstępnego uwierzytelniania, szyfrowania, obsługi serwera proxy, weryfikacji certyfikatu serwera i zarządzanie połączeniami. Przechowywane w i dostępne za pośrednictwem niestandardowe nagłówki i nagłówki nie są realizowane za pośrednictwem właściwości **nagłówki** właściwości.  
  
 **HttpWebRequest** jest używany przez domyślną klasę **WebRequest** i nie musi być zarejestrowane przed można przekazać identyfikatora URI do **WebRequest.Create** metody.  
  
 Umożliwia aplikacji wykonaj przekierowania HTTP automatycznie przez ustawienie <xref:System.Net.HttpWebRequest.AllowAutoRedirect%2A> właściwości **true** (ustawienie domyślne). Aplikacja będzie przekierowywać żądania i <xref:System.Net.HttpWebResponse.ResponseUri%2A> właściwość **HttpWebResponse** będzie zawierać rzeczywiste zasobu sieci Web, który odpowiedział na żądanie. Jeśli ustawisz **AllowAutoRedirect** do **false**, aplikacja musi mieć możliwość obsługi przekierowania jako błędy protokołu HTTP.  
  
 Aplikacje odbierać błędy protokołu HTTP przez <xref:System.Net.WebException> z <xref:System.Net.WebException.Status%2A> ustawioną <xref:System.Net.WebExceptionStatus>. <xref:System.Net.WebException.Response%2A> Właściwość zawiera **WebResponse** wysyłane przez serwer i wskazuje rzeczywiste wystąpił błąd protokołu HTTP.  
  
## <a name="see-also"></a>Zobacz też  
 [Dostęp do Internetu za pośrednictwem serwera proxy](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 [Korzystanie z protokołów aplikacji](../../../docs/framework/network-programming/using-application-protocols.md)  
 [Instrukcje: dostęp do właściwości specyficznych dla protokołu HTTP](../../../docs/framework/network-programming/how-to-access-http-specific-properties.md)
