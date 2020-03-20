---
title: HTTP
ms.date: 03/30/2017
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
ms.openlocfilehash: c8c799a50e5d63bbf411c338eb9e93f85a942bb0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048008"
---
# <a name="http"></a>HTTP
.NET Framework zapewnia kompleksową obsługę protokołu HTTP, który stanowi większość całego <xref:System.Net.HttpWebRequest> <xref:System.Net.HttpWebResponse> ruchu internetowego, z i klas. Te klasy, pochodne i <xref:System.Net.WebRequest> <xref:System.Net.WebResponse>, są zwracane domyślnie, gdy metoda <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> statyczna napotka identyfikator URI, począwszy od "http" lub "https". W większości przypadków **WebRequest** i **WebResponse** klasy zapewniają wszystko, co jest niezbędne do żądania, ale jeśli potrzebujesz dostępu do funkcji specyficznych dla protokołu HTTP udostępniane jako właściwości, można typecast tych klas do **HttpWebRequest** lub **HttpWebResponse**.  
  
 **HttpWebRequest** i **HttpWebResponse** hermetyzują standardową transakcję żądania i odpowiedzi HTTP i zapewnij dostęp do typowych nagłówków HTTP. Klasy te obsługują również większość funkcji HTTP 1.1, w tym tworzenie potoków, wysyłanie i odbieranie danych w fragmentach, uwierzytelnianie, preauthentication, szyfrowanie, obsługa serwera proxy, sprawdzanie poprawności certyfikatów serwera i zarządzanie połączeniami. Niestandardowe nagłówki i nagłówki nie są dostarczane za pośrednictwem właściwości mogą być przechowywane i dostępne za pośrednictwem **headers** właściwości.  
  
 **HttpWebRequest** jest domyślną klasą używaną przez **WebRequest** i nie musi być zarejestrowana, zanim będzie można przekazać identyfikator URI do **WebRequest.Create** metody.  
  
 Aplikację można automatycznie śledzić przekierowania HTTP, <xref:System.Net.HttpWebRequest.AllowAutoRedirect%2A> ustawiając właściwość na **true** (domyślnie). Aplikacja przekieruje żądania, a <xref:System.Net.HttpWebResponse.ResponseUri%2A> właściwość **HttpWebResponse** będzie zawierać rzeczywisty zasób sieci Web, który odpowiedział na żądanie. Jeśli ustawisz **AllowAutoRedirect** na **false,** aplikacja musi mieć możliwość obsługi przekierowań jako błędy protokołu HTTP.  
  
 Aplikacje otrzymują błędy protokołu <xref:System.Net.WebException> HTTP, <xref:System.Net.WebException.Status%2A> łapiąc a z zestawem do <xref:System.Net.WebExceptionStatus>. Właściwość <xref:System.Net.WebException.Response%2A> zawiera **WebResponse** wysłane przez serwer i wskazuje rzeczywisty błąd HTTP napotkany.  
  
## <a name="see-also"></a>Zobacz też

- [Dostęp do Internetu za pośrednictwem serwera proxy](accessing-the-internet-through-a-proxy.md)
- [Korzystanie z protokołów aplikacji](using-application-protocols.md)
- [Instrukcje: dostęp do właściwości specyficznych dla protokołu HTTP](how-to-access-http-specific-properties.md)
