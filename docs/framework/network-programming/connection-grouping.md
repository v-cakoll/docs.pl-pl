---
title: Grupowanie połączeń
ms.date: 03/30/2017
helpviewer_keywords:
- Internet, connections
- connections [.NET Framework], grouping
- WebRequest class, connection grouping
- network resources, connections
- connection pooling
ms.assetid: 2ec502e8-4ba0-4c22-9410-f28eaf4eee63
ms.openlocfilehash: 007366764a7b8e1208e22ef5895e6a9093b090e4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048644"
---
# <a name="connection-grouping"></a>Grupowanie połączeń
Grupowanie połączeń kojarzy określone żądania w ramach jednej aplikacji ze zdefiniowaną pulą połączeń. Może to być wymagane przez aplikację warstwy środkowej, która łączy się z serwerem zaplecza w imieniu użytkownika i używa protokołu uwierzytelniania obsługującego delegowanie, takiego jak Kerberos, lub przez aplikację warstwy środkowej, która dostarcza własne poświadczenia, tak jak w przykład poniżej. Załóżmy na przykład, że użytkownik Joe odwiedza wewnętrzną witrynę sieci Web, która wyświetla jego informacje o liście płac. Po uwierzytelnieniu Joe, serwer aplikacji warstwy środkowej używa poświadczeń Joe do łączenia się z serwerem zaplecza, aby pobrać jego informacje o liście płac. Następnie Susan odwiedza witrynę i żąda informacji o płacach. Ponieważ aplikacja warstwy środkowej już nawiązało połączenie przy użyciu poświadczeń Joe, serwer zaplecza odpowiada informacjami Joe. Jeśli jednak aplikacja przypisuje każde żądanie wysłane do serwera zaplecza do grupy połączeń utworzonej z nazwy użytkownika, każdy użytkownik należy do oddzielnej puli połączeń i nie może przypadkowo udostępnić informacji uwierzytelniania innemu użytkownikowi.  
  
 Aby przypisać żądanie do określonej grupy połączeń, należy <xref:System.Net.WebRequest.ConnectionGroupName%2A> przypisać <xref:System.Net.WebRequest> nazwę do właściwości przed złożeniem żądania.  
  
## <a name="see-also"></a>Zobacz też

- [Zarządzanie połączeniami](managing-connections.md)
- [Instrukcje: przypisywanie informacji użytkownika do połączeń grupowych](how-to-assign-user-information-to-group-connections.md)
