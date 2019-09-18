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
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047258"
---
# <a name="sockets"></a><span data-ttu-id="82e55-102">Gniazda</span><span class="sxs-lookup"><span data-stu-id="82e55-102">Sockets</span></span>
<span data-ttu-id="82e55-103"><xref:System.Net.Sockets> Przestrzeń nazw zawiera zarządzaną implementację interfejsu Windows Sockets.</span><span class="sxs-lookup"><span data-stu-id="82e55-103">The <xref:System.Net.Sockets> namespace contains a managed implementation of the Windows Sockets interface.</span></span> <span data-ttu-id="82e55-104">Wszystkie inne klasy dostępu do sieci w <xref:System.Net> przestrzeni nazw są zbudowane na podstawie tej implementacji gniazd.</span><span class="sxs-lookup"><span data-stu-id="82e55-104">All other network-access classes in the <xref:System.Net> namespace are built on top of this implementation of sockets.</span></span>  
  
 <span data-ttu-id="82e55-105">Klasa .NET Framework <xref:System.Net.Sockets.Socket> jest wersją kodu zarządzanego usługi gniazd udostępnianą przez interfejs API WinSock32.</span><span class="sxs-lookup"><span data-stu-id="82e55-105">The .NET Framework <xref:System.Net.Sockets.Socket> class is a managed-code version of the socket services provided by the Winsock32 API.</span></span> <span data-ttu-id="82e55-106">W większości przypadków klasy **gniazda** są po prostu kierowanie danych do ich natywnych odpowiedników Win32 i obsługę wszelkich niezbędnych kontroli zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="82e55-106">In most cases, the **Socket** class methods simply marshal data into their native Win32 counterparts and handle any necessary security checks.</span></span>  
  
 <span data-ttu-id="82e55-107">Klasa **Socket** obsługuje dwa podstawowe tryby, synchroniczne i asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="82e55-107">The **Socket** class supports two basic modes, synchronous and asynchronous.</span></span> <span data-ttu-id="82e55-108">W trybie synchronicznym wywołania funkcji wykonujących operacje sieciowe (takie jak <xref:System.Net.Sockets.Socket.Send%2A> i <xref:System.Net.Sockets.Socket.Receive%2A>) czekają na zakończenie operacji przed zwróceniem kontroli do wywołującego programu.</span><span class="sxs-lookup"><span data-stu-id="82e55-108">In synchronous mode, calls to functions that perform network operations (such as <xref:System.Net.Sockets.Socket.Send%2A> and <xref:System.Net.Sockets.Socket.Receive%2A>) wait until the operation completes before returning control to the calling program.</span></span> <span data-ttu-id="82e55-109">W trybie asynchronicznym te wywołania zwracają się natychmiast.</span><span class="sxs-lookup"><span data-stu-id="82e55-109">In asynchronous mode, these calls return immediately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82e55-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="82e55-110">See also</span></span>

- [<span data-ttu-id="82e55-111">Instrukcje: Utwórz gniazdo</span><span class="sxs-lookup"><span data-stu-id="82e55-111">How to: Create a Socket</span></span>](how-to-create-a-socket.md)

- [<span data-ttu-id="82e55-112">Korzystanie z protokołów aplikacji</span><span class="sxs-lookup"><span data-stu-id="82e55-112">Using Application Protocols</span></span>](using-application-protocols.md)
