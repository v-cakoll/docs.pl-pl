---
title: "Grupowanie połączenia"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Internet, connections
- connections [.NET Framework], grouping
- WebRequest class, connection grouping
- network resources, connections
- connection pooling
ms.assetid: 2ec502e8-4ba0-4c22-9410-f28eaf4eee63
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: b947051d809d5e8f5be3410b269c872bfc108ec8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="connection-grouping"></a>Grupowanie połączenia
Grupowanie połączenia kojarzy w jednej aplikacji do puli połączeń zdefiniowanych określonego żądania. Może to być wymagane przez aplikację warstwy środkowej, nawiązuje połączenie z serwerem zaplecza w imieniu użytkownika, który korzysta z protokołu uwierzytelniania, która obsługuje delegowanie, takie jak Kerberos, lub przez aplikację warstwy środkowej, który udostępnia własne poświadczenia, jak w programie przykład poniżej. Na przykład załóżmy, że użytkownik, Jan, odwiedza wewnętrznej witryny sieci Web, który wyświetla informacje o jego Lista płac. Po uwierzytelnieniu Jan serwera aplikacji w warstwie środkowej służy do łączenia się z serwerem zaplecza można pobrać informacji o jego Lista płac Jana poświadczeń. Następnie Susan odwiedza witrynę i żąda informacji jej płacowego. Ponieważ aplikacja warstwy środkowej wykonała już połączenie przy użyciu poświadczeń Jana, serwera zaplecza odpowiada Jana informacje. Jednak jeśli aplikacja przypisuje każde żądanie wysłane do serwera zaplecza do grupy połączenia z nazwą użytkownika, następnie każdy użytkownik należy do puli oddzielnego połączenia i przypadkowo nie można udostępniać informacje o uwierzytelnianiu z innym użytkownikiem.  
  
 Aby przypisać żądania do określonego połączenia grupy, należy przypisać nazwy do <xref:System.Net.WebRequest.ConnectionGroupName%2A> właściwości użytkownika <xref:System.Net.WebRequest> przed wykonaniem żądania.  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie połączeniami](../../../docs/framework/network-programming/managing-connections.md)  
 [Porady: przypisywanie informacje użytkownika do grupy połączeń](../../../docs/framework/network-programming/how-to-assign-user-information-to-group-connections.md)
