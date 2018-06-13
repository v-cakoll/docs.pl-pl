---
title: Grupowanie połączenia
ms.date: 03/30/2017
helpviewer_keywords:
- Internet, connections
- connections [.NET Framework], grouping
- WebRequest class, connection grouping
- network resources, connections
- connection pooling
ms.assetid: 2ec502e8-4ba0-4c22-9410-f28eaf4eee63
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: bbf34f1e653e95ea30a3e9945fc74c99cfdc3a45
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33395050"
---
# <a name="connection-grouping"></a>Grupowanie połączenia
Grupowanie połączenia kojarzy w jednej aplikacji do puli połączeń zdefiniowanych określonego żądania. Może to być wymagane przez aplikację warstwy środkowej, nawiązuje połączenie z serwerem zaplecza w imieniu użytkownika, który korzysta z protokołu uwierzytelniania, która obsługuje delegowanie, takie jak Kerberos, lub przez aplikację warstwy środkowej, który udostępnia własne poświadczenia, jak w programie przykład poniżej. Na przykład załóżmy, że użytkownik, Jan, odwiedza wewnętrznej witryny sieci Web, który wyświetla informacje o jego Lista płac. Po uwierzytelnieniu Jan serwera aplikacji w warstwie środkowej służy do łączenia się z serwerem zaplecza można pobrać informacji o jego Lista płac Jana poświadczeń. Następnie Susan odwiedza witrynę i żąda informacji jej płacowego. Ponieważ aplikacja warstwy środkowej wykonała już połączenie przy użyciu poświadczeń Jana, serwera zaplecza odpowiada Jana informacje. Jednak jeśli aplikacja przypisuje każde żądanie wysłane do serwera zaplecza do grupy połączenia z nazwą użytkownika, następnie każdy użytkownik należy do puli oddzielnego połączenia i przypadkowo nie można udostępniać informacje o uwierzytelnianiu z innym użytkownikiem.  
  
 Aby przypisać żądania do określonego połączenia grupy, należy przypisać nazwy do <xref:System.Net.WebRequest.ConnectionGroupName%2A> właściwości użytkownika <xref:System.Net.WebRequest> przed wykonaniem żądania.  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie połączeniami](../../../docs/framework/network-programming/managing-connections.md)  
 [Instrukcje: przypisywanie informacji użytkownika do połączeń grupowych](../../../docs/framework/network-programming/how-to-assign-user-information-to-group-connections.md)
