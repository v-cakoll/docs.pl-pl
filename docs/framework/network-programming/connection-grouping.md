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
ms.openlocfilehash: 9dc2e656bdaa49bf1a94904ed7806b740eed2252
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50180737"
---
# <a name="connection-grouping"></a>Grupowanie połączeń
Grupowanie połączeń kojarzy określonego żądania w ramach jednej aplikacji z pulą określonego połączenia. Może to być wymagane przez aplikację warstwy środkowej, nawiązuje połączenie z serwerem zaplecza w imieniu użytkownika, która korzysta z protokołu uwierzytelniania, obsługującym delegowanie, takich jak Kerberos, lub przez aplikację warstwy środkowej, która udostępnia własne poświadczenia, podobnie jak w Poniższy przykład. Na przykład załóżmy, że użytkownik, Jan, odwiedzi wewnętrznej witryny sieci Web, który wyświetla jego informacji o płacach. Po uwierzytelnieniu Jan, serwera aplikacji warstwy środkowej używa poświadczeń Jana nawiązać połączenia z serwerem zaplecza w celu pobrania jego informacji o płacach. Następnie Susan odwiedza witryny i żąda jej informacji o płacach. Ponieważ aplikacja warstwy środkowej ma już nawiązaniu połączenia przy użyciu poświadczeń Jana, serwer zaplecza odpowiada Jana informacji. Jeśli jednak aplikacja przypisuje każdego żądania wysyłanego do serwerów zaplecza z grupą połączenia utworzonych na podstawie nazwy użytkownika, następnie każdy użytkownik należy do puli osobnego połączenia i przypadkowo nie można udostępniać informacje o uwierzytelnianiu przy użyciu innego użytkownika.  
  
 Aby przypisać grupy określone połączenie na żądanie, należy przypisać nazwy do <xref:System.Net.WebRequest.ConnectionGroupName%2A> właściwości usługi <xref:System.Net.WebRequest> przed wykonaniem żądania.  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie połączeniami](../../../docs/framework/network-programming/managing-connections.md)  
 [Instrukcje: przypisywanie informacji użytkownika do połączeń grupowych](../../../docs/framework/network-programming/how-to-assign-user-information-to-group-connections.md)
