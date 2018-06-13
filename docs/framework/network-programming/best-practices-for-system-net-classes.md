---
title: Najlepsze rozwiązania dotyczące klas System.Net
ms.date: 03/30/2017
helpviewer_keywords:
- sending data, best practices
- requesting data from Internet, best practices
- WebRequest class, best practices
- data requests, best practices
- WebResponse class, best practices
- best practices, data requests
- receiving data, best practices
ms.assetid: 716decc6-5952-47b7-9c5a-ba6fc5698684
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: c74f9d0534675d07c87d3edbcf8434cd98f6c621
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33393948"
---
# <a name="best-practices-for-systemnet-classes"></a>Najlepsze rozwiązania dotyczące klas System.Net
Poniższe zalecenia pomogą używać klas zawartych w <xref:System.Net> do ich najważniejsze korzyści:  
  
-   Najlepsze rozwiązania zabezpieczeń TLS (Transport Layer), zobacz [zabezpieczeń TLS (Transport Layer) najlepsze rozwiązania z .NET Framework](tls.md).

-   Użyj <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse> Jeśli to możliwe, zamiast rzutowanie typów do klas podrzędnych. Aplikacje używające **WebRequest** i **WebResponse** można korzystać z nowych protokołów internetowych bez konieczności zmiany szeroką gamę kodu.  
  
-   Podczas pisania aplikacji programu ASP.NET, działające na serwerze przy użyciu **System.Net** klas, często jest lepsze z punktu widzenia wydajności, aby użyć metod asynchronicznych dla <xref:System.Net.WebRequest.GetResponse%2A> i <xref:System.Net.WebResponse.GetResponseStream%2A>.  
  
-   Liczba połączeń otwarty do zasobu internetowego może mieć znaczący wpływ na wydajność sieci i przepływności. **System.Net** domyślnie używa dwóch połączeń każdej aplikacji na hoście. Ustawienie <xref:System.Net.ServicePoint.ConnectionLimit%2A> właściwości w <xref:System.Net.ServicePoint> dla aplikacji można zwiększyć tę liczbę na określonym hoście. Ustawienie <xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=nameWithType> właściwości można zwiększyć to ustawienie domyślne dla wszystkich hostów.  
  
-   Podczas zapisywania protokoły poziomu gniazda, spróbuj użyć <xref:System.Net.Sockets.TcpClient> lub <xref:System.Net.Sockets.UdpClient> Jeśli to możliwe, zamiast bezpośrednio do zapisywania <xref:System.Net.Sockets.Socket>. Te klasy klienta dwóch hermetyzować Tworzenie gniazda TCP i UDP bez konieczności obsługi szczegóły połączenia.  
  
-   Podczas uzyskiwania dostępu do witryn, które wymagają poświadczeń, użyj <xref:System.Net.CredentialCache> klasy w celu utworzenia pamięci podręcznej poświadczeń, a nie zapewniania kontaktu z każdym żądaniem. **CredentialCache** klasy wyszukiwania w pamięci podręcznej, aby znaleźć odpowiednie poświadczenia, aby zaprezentować żądanie, co uwalnia możesz odpowiedzialności tworzenia i prezentowania poświadczeń na podstawie adresu URL.  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie dla sieci w programie .NET Framework](../../../docs/framework/network-programming/index.md)
