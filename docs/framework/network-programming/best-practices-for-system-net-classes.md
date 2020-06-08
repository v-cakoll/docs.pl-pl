---
title: Najlepsze rozwiązania dotyczące klas System.Net
description: Postępuj zgodnie z poniższymi zaleceniami, aby używać klas zawartych w System.Net do ich najlepszej korzyści w programowaniu .NET Framework.
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
ms.openlocfilehash: 583fa5e57c7c4d60252dddfd425596e7acad7c0d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502681"
---
# <a name="best-practices-for-systemnet-classes"></a>Najlepsze rozwiązania dotyczące klas System.Net
Poniższe zalecenia ułatwią korzystanie z klas zawartych w programie w <xref:System.Net> celu uzyskania najlepszej korzyści:  
  
- W przypadku najlepszych rozwiązań Transport Layer Security (TLS) zobacz [Transport Layer Security (TLS) Best Practices with .NET Framework](tls.md).

- Używaj <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse> wszędzie tam, gdzie to możliwe, zamiast typu rzutowania na klasy podrzędne. Aplikacje korzystające z **WebRequest** i **WebResponse** mogą korzystać z nowych protokołów internetowych bez konieczności wprowadzania szczegółowych zmian w kodzie.  
  
- Podczas pisania aplikacji ASP.NET, które działają na serwerze przy użyciu klas **System.NET** , często są one lepsze od punktu widzenia wydajności, aby użyć metod asynchronicznych dla <xref:System.Net.WebRequest.GetResponse%2A> i <xref:System.Net.WebResponse.GetResponseStream%2A> .  
  
- Liczba połączeń otwartych w ramach zasobu internetowego może mieć znaczny wpływ na wydajność sieci i przepływność. **System.NET** domyślnie używa dwóch połączeń dla każdej aplikacji na hosta. Ustawienie <xref:System.Net.ServicePoint.ConnectionLimit%2A> właściwości w <xref:System.Net.ServicePoint> aplikacji może zwiększyć ten numer dla określonego hosta. Ustawienie <xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=nameWithType> właściwości może zwiększyć wartość domyślną dla wszystkich hostów.  
  
- Podczas pisania protokołów na poziomie gniazda, spróbuj użyć <xref:System.Net.Sockets.TcpClient> lub, <xref:System.Net.Sockets.UdpClient> Jeśli to możliwe, zamiast pisać bezpośrednio do <xref:System.Net.Sockets.Socket> . Te dwie klasy klienckie hermetyzują tworzenie gniazd TCP i UDP bez konieczności obsługi szczegółów połączenia.  
  
- Podczas uzyskiwania dostępu do witryn, które wymagają poświadczeń, należy użyć <xref:System.Net.CredentialCache> klasy do utworzenia pamięci podręcznej poświadczeń, a nie dostarczenia ich do każdego żądania. Klasa **CredentialCache** przeszukuje pamięć podręczną, aby znaleźć odpowiednie poświadczenia do zaprezentowania z żądaniem, co uwalnia z odpowiedzialności za tworzenie i prezentowanie poświadczeń na podstawie adresu URL.  
  
## <a name="see-also"></a>Zobacz także

- [Programowanie dla sieci w programie .NET Framework](index.md)
