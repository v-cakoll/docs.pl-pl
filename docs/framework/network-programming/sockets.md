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
# <a name="sockets"></a><span data-ttu-id="5ad18-103">Gniazda</span><span class="sxs-lookup"><span data-stu-id="5ad18-103">Sockets</span></span>
<span data-ttu-id="5ad18-104"><xref:System.Net.Sockets>Przestrzeń nazw zawiera zarządzaną implementację interfejsu Windows Sockets.</span><span class="sxs-lookup"><span data-stu-id="5ad18-104">The <xref:System.Net.Sockets> namespace contains a managed implementation of the Windows Sockets interface.</span></span> <span data-ttu-id="5ad18-105">Wszystkie inne klasy dostępu do sieci w <xref:System.Net> przestrzeni nazw są zbudowane na podstawie tej implementacji gniazd.</span><span class="sxs-lookup"><span data-stu-id="5ad18-105">All other network-access classes in the <xref:System.Net> namespace are built on top of this implementation of sockets.</span></span>  
  
 <span data-ttu-id="5ad18-106">Klasa .NET Framework <xref:System.Net.Sockets.Socket> jest wersją kodu zarządzanego usługi gniazd udostępnianą przez interfejs API WinSock32.</span><span class="sxs-lookup"><span data-stu-id="5ad18-106">The .NET Framework <xref:System.Net.Sockets.Socket> class is a managed-code version of the socket services provided by the Winsock32 API.</span></span> <span data-ttu-id="5ad18-107">W większości przypadków klasy **gniazda** są po prostu kierowanie danych do ich natywnych odpowiedników Win32 i obsługę wszelkich niezbędnych kontroli zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="5ad18-107">In most cases, the **Socket** class methods simply marshal data into their native Win32 counterparts and handle any necessary security checks.</span></span>  
  
 <span data-ttu-id="5ad18-108">Klasa **Socket** obsługuje dwa podstawowe tryby, synchroniczne i asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="5ad18-108">The **Socket** class supports two basic modes, synchronous and asynchronous.</span></span> <span data-ttu-id="5ad18-109">W trybie synchronicznym wywołania funkcji wykonujących operacje sieciowe (takie jak <xref:System.Net.Sockets.Socket.Send%2A> i <xref:System.Net.Sockets.Socket.Receive%2A> ) czekają na zakończenie operacji przed zwróceniem kontroli do wywołującego programu.</span><span class="sxs-lookup"><span data-stu-id="5ad18-109">In synchronous mode, calls to functions that perform network operations (such as <xref:System.Net.Sockets.Socket.Send%2A> and <xref:System.Net.Sockets.Socket.Receive%2A>) wait until the operation completes before returning control to the calling program.</span></span> <span data-ttu-id="5ad18-110">W trybie asynchronicznym te wywołania zwracają się natychmiast.</span><span class="sxs-lookup"><span data-stu-id="5ad18-110">In asynchronous mode, these calls return immediately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ad18-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5ad18-111">See also</span></span>

- [<span data-ttu-id="5ad18-112">Instrukcje: tworzenie gniazda</span><span class="sxs-lookup"><span data-stu-id="5ad18-112">How to: Create a Socket</span></span>](how-to-create-a-socket.md)

- [<span data-ttu-id="5ad18-113">Korzystanie z protokołów aplikacji</span><span class="sxs-lookup"><span data-stu-id="5ad18-113">Using Application Protocols</span></span>](using-application-protocols.md)
