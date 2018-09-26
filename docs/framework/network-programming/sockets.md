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
author: mcleblanc
ms.author: markl
ms.openlocfilehash: ce7ded81ad23c2df55afa9360435e8391fea7a63
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47176828"
---
# <a name="sockets"></a><span data-ttu-id="583f4-102">Gniazda</span><span class="sxs-lookup"><span data-stu-id="583f4-102">Sockets</span></span>
<span data-ttu-id="583f4-103"><xref:System.Net.Sockets> Przestrzeń nazw zawiera zarządzaną implementację interfejsu Windows Sockets.</span><span class="sxs-lookup"><span data-stu-id="583f4-103">The <xref:System.Net.Sockets> namespace contains a managed implementation of the Windows Sockets interface.</span></span> <span data-ttu-id="583f4-104">Wszystkie inne — dostęp do sieci klas w <xref:System.Net> przestrzeni nazw są zbudowane na podstawie tej implementacji gniazda.</span><span class="sxs-lookup"><span data-stu-id="583f4-104">All other network-access classes in the <xref:System.Net> namespace are built on top of this implementation of sockets.</span></span>  
  
 <span data-ttu-id="583f4-105">.NET Framework <xref:System.Net.Sockets.Socket> klasy jest wersja kodu zarządzanego usług gniazda udostępniony przez interfejs API Winsock32.</span><span class="sxs-lookup"><span data-stu-id="583f4-105">The .NET Framework <xref:System.Net.Sockets.Socket> class is a managed-code version of the socket services provided by the Winsock32 API.</span></span> <span data-ttu-id="583f4-106">W większości przypadków **gniazda** metody klasy, po prostu kierować dane do natywnego elementom systemu Win32 i obsługiwać wszystkie kontrole zabezpieczeń wymagane.</span><span class="sxs-lookup"><span data-stu-id="583f4-106">In most cases, the **Socket** class methods simply marshal data into their native Win32 counterparts and handle any necessary security checks.</span></span>  
  
 <span data-ttu-id="583f4-107">**Gniazda** klasy obsługuje dwa tryby podstawowe, synchroniczne i asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="583f4-107">The **Socket** class supports two basic modes, synchronous and asynchronous.</span></span> <span data-ttu-id="583f4-108">W trybie synchronicznym wywołania funkcji, które wykonują operacje sieciowe (takie jak <xref:System.Net.Sockets.Socket.Send%2A> i <xref:System.Net.Sockets.Socket.Receive%2A>) poczekaj, aż operacja kończy się przed zwróceniem sterowania do program wywołujący.</span><span class="sxs-lookup"><span data-stu-id="583f4-108">In synchronous mode, calls to functions that perform network operations (such as <xref:System.Net.Sockets.Socket.Send%2A> and <xref:System.Net.Sockets.Socket.Receive%2A>) wait until the operation completes before returning control to the calling program.</span></span> <span data-ttu-id="583f4-109">W trybie asynchronicznym te wywołania zwraca natychmiast.</span><span class="sxs-lookup"><span data-stu-id="583f4-109">In asynchronous mode, these calls return immediately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="583f4-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="583f4-110">See Also</span></span>  
 [<span data-ttu-id="583f4-111">Instrukcje: tworzenie gniazda</span><span class="sxs-lookup"><span data-stu-id="583f4-111">How to: Create a Socket</span></span>](../../../docs/framework/network-programming/how-to-create-a-socket.md)  
    
 [<span data-ttu-id="583f4-112">Korzystanie z protokołów aplikacji</span><span class="sxs-lookup"><span data-stu-id="583f4-112">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)
