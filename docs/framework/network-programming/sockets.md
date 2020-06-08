---
title: Gniazda
description: Dowiedz się więcej o klasie .NET Framework Socket, która jest wersją kodu zarządzanego usług gniazd dostarczonych przez interfejs API WinSock32.
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
ms.openlocfilehash: b44409a0fafc770625be55881ccef3b57045acef
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502135"
---
# <a name="sockets"></a>Gniazda
<xref:System.Net.Sockets>Przestrzeń nazw zawiera zarządzaną implementację interfejsu Windows Sockets. Wszystkie inne klasy dostępu do sieci w <xref:System.Net> przestrzeni nazw są zbudowane na podstawie tej implementacji gniazd.  
  
 Klasa .NET Framework <xref:System.Net.Sockets.Socket> jest wersją kodu zarządzanego usługi gniazd udostępnianą przez interfejs API WinSock32. W większości przypadków klasy **gniazda** są po prostu kierowanie danych do ich natywnych odpowiedników Win32 i obsługę wszelkich niezbędnych kontroli zabezpieczeń.  
  
 Klasa **Socket** obsługuje dwa podstawowe tryby, synchroniczne i asynchroniczne. W trybie synchronicznym wywołania funkcji wykonujących operacje sieciowe (takie jak <xref:System.Net.Sockets.Socket.Send%2A> i <xref:System.Net.Sockets.Socket.Receive%2A> ) czekają na zakończenie operacji przed zwróceniem kontroli do wywołującego programu. W trybie asynchronicznym te wywołania zwracają się natychmiast.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: tworzenie gniazda](how-to-create-a-socket.md)

- [Korzystanie z protokołów aplikacji](using-application-protocols.md)
