---
title: "Najlepsze rozwiązania dotyczące klas System.Net"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- sending data, best practices
- requesting data from Internet, best practices
- WebRequest class, best practices
- data requests, best practices
- WebResponse class, best practices
- best practices, data requests
- receiving data, best practices
ms.assetid: 716decc6-5952-47b7-9c5a-ba6fc5698684
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: e50df22f66d4d55298aad5f3cc501dfb39ffcd9a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="best-practices-for-systemnet-classes"></a>Najlepsze rozwiązania dotyczące klas System.Net
Poniższe zalecenia pomogą używać klas zawartych w <xref:System.Net> do ich najważniejsze korzyści:  
  
-   Użyj <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse> Jeśli to możliwe, zamiast rzutowanie typów do klas podrzędnych. Aplikacje używające **WebRequest** i **WebResponse** można korzystać z nowych protokołów internetowych bez konieczności zmiany szeroką gamę kodu.  
  
-   Podczas pisania aplikacji programu ASP.NET, działające na serwerze przy użyciu **System.Net** klas, często jest lepsze z punktu widzenia wydajności, aby użyć metod asynchronicznych dla <xref:System.Net.WebRequest.GetResponse%2A> i <xref:System.Net.WebResponse.GetResponseStream%2A>.  
  
-   Liczba połączeń otwarty do zasobu internetowego może mieć znaczący wpływ na wydajność sieci i przepływności. **System.Net** domyślnie używa dwóch połączeń każdej aplikacji na hoście. Ustawienie <xref:System.Net.ServicePoint.ConnectionLimit%2A> właściwości w <xref:System.Net.ServicePoint> dla aplikacji można zwiększyć tę liczbę na określonym hoście. Ustawienie <xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=nameWithType> właściwości można zwiększyć to ustawienie domyślne dla wszystkich hostów.  
  
-   Podczas zapisywania protokoły poziomu gniazda, spróbuj użyć <xref:System.Net.Sockets.TcpClient> lub <xref:System.Net.Sockets.UdpClient> Jeśli to możliwe, zamiast bezpośrednio do zapisywania <xref:System.Net.Sockets.Socket>. Te klasy klienta dwóch hermetyzować Tworzenie gniazda TCP i UDP bez konieczności obsługi szczegóły połączenia.  
  
-   Podczas uzyskiwania dostępu do witryn, które wymagają poświadczeń, użyj <xref:System.Net.CredentialCache> klasy w celu utworzenia pamięci podręcznej poświadczeń, a nie zapewniania kontaktu z każdym żądaniem. **CredentialCache** klasy wyszukiwania w pamięci podręcznej, aby znaleźć odpowiednie poświadczenia, aby zaprezentować żądanie, co uwalnia możesz odpowiedzialności tworzenia i prezentowania poświadczeń na podstawie adresu URL.  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie dla sieci w programie .NET Framework](../../../docs/framework/network-programming/index.md)
