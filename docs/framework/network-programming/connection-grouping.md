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
ms.openlocfilehash: 28d8771b4535c20a2b65fc8dbbe45407eb041a34
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54658068"
---
# <a name="connection-grouping"></a>Grupowanie połączeń
Grupowanie połączeń kojarzy określonego żądania w ramach jednej aplikacji z pulą określonego połączenia. Może to być wymagane przez aplikację warstwy środkowej, nawiązuje połączenie z serwerem zaplecza w imieniu użytkownika, która korzysta z protokołu uwierzytelniania, obsługującym delegowanie, takich jak Kerberos, lub przez aplikację warstwy środkowej, która udostępnia własne poświadczenia, podobnie jak w Poniższy przykład. Na przykład załóżmy, że użytkownik, Jan, odwiedzi wewnętrznej witryny sieci Web, który wyświetla jego informacji o płacach. Po uwierzytelnieniu Jan, serwera aplikacji warstwy środkowej używa poświadczeń Jana nawiązać połączenia z serwerem zaplecza w celu pobrania jego informacji o płacach. Następnie Susan odwiedza witryny i żąda jej informacji o płacach. Ponieważ aplikacja warstwy środkowej ma już nawiązaniu połączenia przy użyciu poświadczeń Jana, serwer zaplecza odpowiada Jana informacji. Jeśli jednak aplikacja przypisuje każdego żądania wysyłanego do serwerów zaplecza z grupą połączenia utworzonych na podstawie nazwy użytkownika, następnie każdy użytkownik należy do puli osobnego połączenia i przypadkowo nie można udostępniać informacje o uwierzytelnianiu przy użyciu innego użytkownika.  
  
 Aby przypisać grupy określone połączenie na żądanie, należy przypisać nazwy do <xref:System.Net.WebRequest.ConnectionGroupName%2A> właściwości usługi <xref:System.Net.WebRequest> przed wykonaniem żądania.  
  
## <a name="see-also"></a>Zobacz także
- [Zarządzanie połączeniami](../../../docs/framework/network-programming/managing-connections.md)
- [Instrukcje: Przypisywanie informacji użytkownika do połączeń grupowych](../../../docs/framework/network-programming/how-to-assign-user-information-to-group-connections.md)
