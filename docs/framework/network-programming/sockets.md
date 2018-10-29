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
ms.openlocfilehash: 3a8e141d79a7f261cd969dc78a656a89ffc8bc30
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2018
ms.locfileid: "50196534"
---
# <a name="sockets"></a>Gniazda
<xref:System.Net.Sockets> Przestrzeń nazw zawiera zarządzaną implementację interfejsu Windows Sockets. Wszystkie inne — dostęp do sieci klas w <xref:System.Net> przestrzeni nazw są zbudowane na podstawie tej implementacji gniazda.  
  
 .NET Framework <xref:System.Net.Sockets.Socket> klasy jest wersja kodu zarządzanego usług gniazda udostępniony przez interfejs API Winsock32. W większości przypadków **gniazda** metody klasy, po prostu kierować dane do natywnego elementom systemu Win32 i obsługiwać wszystkie kontrole zabezpieczeń wymagane.  
  
 **Gniazda** klasy obsługuje dwa tryby podstawowe, synchroniczne i asynchroniczne. W trybie synchronicznym wywołania funkcji, które wykonują operacje sieciowe (takie jak <xref:System.Net.Sockets.Socket.Send%2A> i <xref:System.Net.Sockets.Socket.Receive%2A>) poczekaj, aż operacja kończy się przed zwróceniem sterowania do program wywołujący. W trybie asynchronicznym te wywołania zwraca natychmiast.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: tworzenie gniazda](../../../docs/framework/network-programming/how-to-create-a-socket.md)  
    
 [Korzystanie z protokołów aplikacji](../../../docs/framework/network-programming/using-application-protocols.md)
