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
ms.openlocfilehash: ce365d088c01ae4a89c77713b6970ae3389b3f0e
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50190953"
---
# <a name="best-practices-for-systemnet-classes"></a>Najlepsze rozwiązania dotyczące klas System.Net
Poniższe zalecenia pomogą należy używać klas znajdujących się w <xref:System.Net> do ich Najważniejsze zalety:  
  
-   Najlepsze rozwiązania dotyczące zabezpieczeń TLS (Transport Layer), zobacz [zabezpieczeń TLS (Transport Layer) najlepszych rozwiązań za pomocą .NET Framework](tls.md).

-   Użyj <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse> zawsze, gdy jest to możliwe, zamiast rzutowania typu do klas podrzędnych. Aplikacje, które używają **WebRequest** i **elementu WebResponse** korzystać z zalet nowe protokoły internetowe bez konieczności wprowadzania zmian w kodzie rozbudowane.  
  
-   Podczas pisania aplikacji platformy ASP.NET, korzystających z serwerem za pomocą **przestrzeni nazw System.Net** klas, często lepiej jest, z punktu widzenia wydajności można używać metod asynchronicznych dla <xref:System.Net.WebRequest.GetResponse%2A> i <xref:System.Net.WebResponse.GetResponseStream%2A>.  
  
-   Liczba połączeń otwarty do zasobu internetowego może mieć znaczący wpływ na wydajność sieci i przepustowość. **Przestrzeni nazw System.Net** domyślnie używa dwóch połączeń dla jednej aplikacji na każdym hoście. Ustawienie <xref:System.Net.ServicePoint.ConnectionLimit%2A> właściwość <xref:System.Net.ServicePoint> dla aplikacji można zwiększyć tę liczbę dla konkretnego hosta. Ustawienie <xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=nameWithType> właściwości można zwiększyć to ustawienie domyślne dla wszystkich hostów.  
  
-   Podczas pisania protokoły poziomu gniazda, spróbuj użyć <xref:System.Net.Sockets.TcpClient> lub <xref:System.Net.Sockets.UdpClient> zawsze, gdy jest to możliwe, zamiast zapisywania bezpośrednio do <xref:System.Net.Sockets.Socket>. W ramach tych zajęć dwóch klientów hermetyzować Tworzenie gniazda TCP i UDP, bez konieczności obsługi szczegółów połączenia.  
  
-   Podczas uzyskiwania dostępu do witryn, które wymagają poświadczeń, użyj <xref:System.Net.CredentialCache> klasy w celu utworzenia pamięci podręcznej poświadczeń, a nie dostarczanie każde żądanie. **CredentialCache** klasy wyszukuje w pamięci podręcznej, aby znaleźć odpowiednie poświadczenia, aby przedstawić z żądaniem zwalniania należy z odpowiedzialność za tworzenie i prezentowanie poświadczeń opartych na adres URL.  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie dla sieci w programie .NET Framework](../../../docs/framework/network-programming/index.md)
