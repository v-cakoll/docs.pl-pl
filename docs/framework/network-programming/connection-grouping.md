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
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048644"
---
# <a name="connection-grouping"></a>Grupowanie połączeń
Grupowanie połączeń kojarzy określone żądania w ramach jednej aplikacji z określoną pulą połączeń. Może to być wymagane przez aplikację warstwy środkowej, która łączy się z serwerem zaplecza w imieniu użytkownika i używa protokołu uwierzytelniania obsługującego delegowanie, takiego jak Kerberos lub przez aplikację warstwy środkowej, która dostarcza własne poświadczenia, jak w przykład poniżej. Załóżmy na przykład, że użytkownik, Jan znajduje się w wewnętrznej witrynie sieci Web, która wyświetla informacje o płacach. Po uwierzytelnieniu Jan serwer aplikacji warstwy środkowej używa poświadczeń Jan do łączenia się z serwerem zaplecza w celu pobrania informacji o płacach. Następnie Susan odwiedza witrynę i żąda informacji o płacach. Ponieważ aplikacja warstwy środkowej ma już połączenie przy użyciu poświadczeń Jan, serwer zaplecza reaguje na informacje o Jan. Jeśli jednak aplikacja przypisze każde żądanie wysyłane do serwera zaplecza do grupy połączeń utworzonej przy użyciu nazwy użytkownika, każdy użytkownik należy do osobnej puli połączeń i nie może przypadkowo udostępnić informacji uwierzytelniania innym użytkownikom.  
  
 Aby przypisać żądanie do określonej grupy połączeń, należy przypisać nazwę do <xref:System.Net.WebRequest.ConnectionGroupName%2A> właściwości <xref:System.Net.WebRequest> przed wykonaniem żądania.  
  
## <a name="see-also"></a>Zobacz także

- [Zarządzanie połączeniami](managing-connections.md)
- [Instrukcje: Przypisywanie informacji o użytkowniku do połączeń grupowych](how-to-assign-user-information-to-group-connections.md)
