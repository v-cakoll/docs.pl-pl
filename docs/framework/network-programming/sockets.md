---
title: Gniazda
ms.date: 03/30/2017
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- data requests, sockets
- Windows Sockets
- sockets, about sockets
- Socket class, about Socket class
- sockets
- requesting data from Internet, sockets
- network, sockets
- receiving data, sockets
- protocols, sockets
- Internet, sockets
ms.assetid: 10d22735-bd37-42c1-a2be-c1932f979a7d
ms.openlocfilehash: cffad6b4677a880bd63f5ae0232c639f7a262c59
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047258"
---
# <a name="sockets"></a>Gniazda
Obszar <xref:System.Net.Sockets> nazw zawiera zarządzaną implementację interfejsu Windows Sockets. Wszystkie inne klasy dostępu <xref:System.Net> do sieci w obszarze nazw są zbudowane na tej implementacji gniazd.  
  
 Klasa .NET <xref:System.Net.Sockets.Socket> Framework jest wersją kodu zarządzanego usług socket dostarczanych przez interfejs API Winsock32. W większości przypadków **Socket** metody klasy po prostu marshal danych do ich odpowiedników natywnych Win32 i obsługi wszelkich niezbędnych kontroli zabezpieczeń.  
  
 **Socket** Klasa obsługuje dwa podstawowe tryby, synchroniczne i asynchroniczne. W trybie synchronicznym wywołania funkcji, <xref:System.Net.Sockets.Socket.Send%2A> które <xref:System.Net.Sockets.Socket.Receive%2A>wykonują operacje sieciowe (takie jak i ) czekać, aż operacja zakończy się przed zwróceniem kontroli do programu wywołującego. W trybie asynchronicznego te wywołania zwracają natychmiast.  
  
## <a name="see-also"></a>Zobacz też

- [Instrukcje: tworzenie gniazda](how-to-create-a-socket.md)

- [Korzystanie z protokołów aplikacji](using-application-protocols.md)
