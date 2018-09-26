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
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 0c99e63f09d756bfff8cced846c2fe0f61722b8c
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47078451"
---
# <a name="http"></a>HTTP
Program .NET Framework oferuje kompleksowe wsparcie dla protokołu HTTP, co sprawia, że większość cały ruch z Internetu za pomocą <xref:System.Net.HttpWebRequest> i <xref:System.Net.HttpWebResponse> klasy. Te klasy pochodne <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse>, zwracane są domyślnie zawsze wtedy, gdy metoda statyczna <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> napotka przez identyfikator URI rozpoczynający się od "http" lub "https". W większości przypadków **WebRequest** i **elementu WebResponse** klasy zapewnia wszystko co jest niezbędne do utworzenia żądania, ale jeśli potrzebujesz dostępu do funkcji specyficznych dla protokołu HTTP, widoczne jako właściwości, możesz rzutowanie typu te klasy **HttpWebRequest** lub **HttpWebResponse**.  
  
 **HttpWebRequest** i **HttpWebResponse** hermetyzują standardowy transakcji żądań i odpowiedzi HTTP i zapewniają dostęp do wspólnych nagłówków HTTP. W ramach tych zajęć również obsługiwać większość funkcje protokołu HTTP 1.1, w tym przetwarzanie potokowe, wysyłania i odbierania danych w fragmentów, uwierzytelnianie, wstępnego uwierzytelniania, szyfrowanie, obsługa serwera proxy, weryfikacji certyfikatu serwera i zarządzania połączeniami. Przechowywane w i dostępne za pośrednictwem niestandardowych nagłówków i nagłówki nie są dostarczane za pośrednictwem właściwości **nagłówki** właściwości.  
  
 **HttpWebRequest** jest używany przez domyślną klasę **WebRequest** i nie musi zostać zarejestrowany, aby przekazać identyfikator URI, który ma **WebRequest.Create** metody.  
  
 Można uczynić aplikację automatycznie podążał za przekierowaniami HTTP, ustawiając <xref:System.Net.HttpWebRequest.AllowAutoRedirect%2A> właściwości **true** (ustawienie domyślne). Aplikacja będzie przekierowywać żądania oraz <xref:System.Net.HttpWebResponse.ResponseUri%2A> właściwość **HttpWebResponse** będzie zawierać rzeczywistego zasobu sieci Web, która odpowiedział na żądanie. Jeśli ustawisz **AllowAutoRedirect** do **false**, aplikacja musi być w stanie obsłużyć przekierowań jako błędy protokołu HTTP.  
  
 Aplikacje otrzymywać komunikaty o błędach protokołu HTTP przez Przechwytywanie <xref:System.Net.WebException> z <xref:System.Net.WebException.Status%2A> równa <xref:System.Net.WebExceptionStatus>. <xref:System.Net.WebException.Response%2A> Właściwość zawiera **elementu WebResponse** wysłanych przez serwer i wskazuje rzeczywiste Napotkano błąd HTTP.  
  
## <a name="see-also"></a>Zobacz też  
 [Dostęp do Internetu za pośrednictwem serwera proxy](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 [Korzystanie z protokołów aplikacji](../../../docs/framework/network-programming/using-application-protocols.md)  
 [Instrukcje: dostęp do właściwości specyficznych dla protokołu HTTP](../../../docs/framework/network-programming/how-to-access-http-specific-properties.md)
