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
ms.openlocfilehash: c7324dcbc27c95c7d799592700d46c195e7d952b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048890"
---
# <a name="best-practices-for-systemnet-classes"></a>Najlepsze rozwiązania dotyczące klas System.Net
Poniższe zalecenia pomogą Ci korzystać <xref:System.Net> z klas zawartych w ich najlepsze korzyści:  
  
- Aby zapoznać się z najlepszymi rozwiązaniami dotyczących zabezpieczeń warstwy transportu (TLS), zobacz [Najważniejsze wskazówki dotyczące zabezpieczeń warstwy transportu (TLS) w ramach .NET Framework](tls.md).

- Użyj <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> i, gdy jest to możliwe, zamiast rzutowania typu do klas podrzędnych. Aplikacje korzystające z **webrequest** i **WebResponse** mogą korzystać z nowych protokołów internetowych bez konieczności szeroko zakrojonych zmian kodu.  
  
- Podczas pisania ASP.NET aplikacji, które działają na serwerze przy użyciu **klas System.Net,** często lepiej jest, z punktu widzenia wydajności, używać metod asynchronicznych dla <xref:System.Net.WebRequest.GetResponse%2A> i <xref:System.Net.WebResponse.GetResponseStream%2A>.  
  
- Liczba połączeń otwartych dla zasobu internetowego może mieć znaczący wpływ na wydajność sieci i przepływność. **System.Net** domyślnie używa dwóch połączeń na aplikację na hosta. Ustawienie <xref:System.Net.ServicePoint.ConnectionLimit%2A> właściwości w <xref:System.Net.ServicePoint> aplikacji może zwiększyć tę liczbę dla określonego hosta. Ustawienie <xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=nameWithType> właściwości może zwiększyć tę wartość domyślną dla wszystkich hostów.  
  
- Podczas pisania protokołów na poziomie <xref:System.Net.Sockets.TcpClient> gniazda, spróbuj użyć lub <xref:System.Net.Sockets.UdpClient> w miarę <xref:System.Net.Sockets.Socket>możliwości zamiast pisać bezpośrednio do . Te dwie klasy klienta hermetyzują tworzenie gniazd TCP i UDP bez konieczności obsługi szczegółów połączenia.  
  
- Podczas uzyskiwania dostępu do witryn, <xref:System.Net.CredentialCache> które wymagają poświadczeń, należy użyć klasy do utworzenia pamięci podręcznej poświadczeń, a nie dostarczanie im z każdym żądaniem. **CredentialCache** Klasy przeszukuje pamięci podręcznej, aby znaleźć odpowiednie poświadczenia do przedstawienia z żądaniem, zwalniając użytkownika z odpowiedzialności tworzenia i prezentowania poświadczeń na podstawie adresu URL.  
  
## <a name="see-also"></a>Zobacz też

- [Programowanie dla sieci w programie .NET Framework](index.md)
