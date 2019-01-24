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
ms.openlocfilehash: 468d8afc290d8e725deb13ba57dd990181ae4e19
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54680497"
---
# <a name="sockets"></a><span data-ttu-id="69597-102">Gniazda</span><span class="sxs-lookup"><span data-stu-id="69597-102">Sockets</span></span>
<span data-ttu-id="69597-103"><xref:System.Net.Sockets> Przestrzeń nazw zawiera zarządzaną implementację interfejsu Windows Sockets.</span><span class="sxs-lookup"><span data-stu-id="69597-103">The <xref:System.Net.Sockets> namespace contains a managed implementation of the Windows Sockets interface.</span></span> <span data-ttu-id="69597-104">Wszystkie inne — dostęp do sieci klas w <xref:System.Net> przestrzeni nazw są zbudowane na podstawie tej implementacji gniazda.</span><span class="sxs-lookup"><span data-stu-id="69597-104">All other network-access classes in the <xref:System.Net> namespace are built on top of this implementation of sockets.</span></span>  
  
 <span data-ttu-id="69597-105">.NET Framework <xref:System.Net.Sockets.Socket> klasy jest wersja kodu zarządzanego usług gniazda udostępniony przez interfejs API Winsock32.</span><span class="sxs-lookup"><span data-stu-id="69597-105">The .NET Framework <xref:System.Net.Sockets.Socket> class is a managed-code version of the socket services provided by the Winsock32 API.</span></span> <span data-ttu-id="69597-106">W większości przypadków **gniazda** metody klasy, po prostu kierować dane do natywnego elementom systemu Win32 i obsługiwać wszystkie kontrole zabezpieczeń wymagane.</span><span class="sxs-lookup"><span data-stu-id="69597-106">In most cases, the **Socket** class methods simply marshal data into their native Win32 counterparts and handle any necessary security checks.</span></span>  
  
 <span data-ttu-id="69597-107">**Gniazda** klasy obsługuje dwa tryby podstawowe, synchroniczne i asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="69597-107">The **Socket** class supports two basic modes, synchronous and asynchronous.</span></span> <span data-ttu-id="69597-108">W trybie synchronicznym wywołania funkcji, które wykonują operacje sieciowe (takie jak <xref:System.Net.Sockets.Socket.Send%2A> i <xref:System.Net.Sockets.Socket.Receive%2A>) poczekaj, aż operacja kończy się przed zwróceniem sterowania do program wywołujący.</span><span class="sxs-lookup"><span data-stu-id="69597-108">In synchronous mode, calls to functions that perform network operations (such as <xref:System.Net.Sockets.Socket.Send%2A> and <xref:System.Net.Sockets.Socket.Receive%2A>) wait until the operation completes before returning control to the calling program.</span></span> <span data-ttu-id="69597-109">W trybie asynchronicznym te wywołania zwraca natychmiast.</span><span class="sxs-lookup"><span data-stu-id="69597-109">In asynchronous mode, these calls return immediately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69597-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="69597-110">See also</span></span>
- [<span data-ttu-id="69597-111">Instrukcje: Tworzenie gniazda</span><span class="sxs-lookup"><span data-stu-id="69597-111">How to: Create a Socket</span></span>](../../../docs/framework/network-programming/how-to-create-a-socket.md)

- [<span data-ttu-id="69597-112">Korzystanie z protokołów aplikacji</span><span class="sxs-lookup"><span data-stu-id="69597-112">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)
