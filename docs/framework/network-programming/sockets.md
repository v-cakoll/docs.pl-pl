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
# <a name="sockets"></a><span data-ttu-id="78b19-102">Gniazda</span><span class="sxs-lookup"><span data-stu-id="78b19-102">Sockets</span></span>
<span data-ttu-id="78b19-103">Obszar <xref:System.Net.Sockets> nazw zawiera zarządzaną implementację interfejsu Windows Sockets.</span><span class="sxs-lookup"><span data-stu-id="78b19-103">The <xref:System.Net.Sockets> namespace contains a managed implementation of the Windows Sockets interface.</span></span> <span data-ttu-id="78b19-104">Wszystkie inne klasy dostępu <xref:System.Net> do sieci w obszarze nazw są zbudowane na tej implementacji gniazd.</span><span class="sxs-lookup"><span data-stu-id="78b19-104">All other network-access classes in the <xref:System.Net> namespace are built on top of this implementation of sockets.</span></span>  
  
 <span data-ttu-id="78b19-105">Klasa .NET <xref:System.Net.Sockets.Socket> Framework jest wersją kodu zarządzanego usług socket dostarczanych przez interfejs API Winsock32.</span><span class="sxs-lookup"><span data-stu-id="78b19-105">The .NET Framework <xref:System.Net.Sockets.Socket> class is a managed-code version of the socket services provided by the Winsock32 API.</span></span> <span data-ttu-id="78b19-106">W większości przypadków **Socket** metody klasy po prostu marshal danych do ich odpowiedników natywnych Win32 i obsługi wszelkich niezbędnych kontroli zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="78b19-106">In most cases, the **Socket** class methods simply marshal data into their native Win32 counterparts and handle any necessary security checks.</span></span>  
  
 <span data-ttu-id="78b19-107">**Socket** Klasa obsługuje dwa podstawowe tryby, synchroniczne i asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="78b19-107">The **Socket** class supports two basic modes, synchronous and asynchronous.</span></span> <span data-ttu-id="78b19-108">W trybie synchronicznym wywołania funkcji, <xref:System.Net.Sockets.Socket.Send%2A> które <xref:System.Net.Sockets.Socket.Receive%2A>wykonują operacje sieciowe (takie jak i ) czekać, aż operacja zakończy się przed zwróceniem kontroli do programu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="78b19-108">In synchronous mode, calls to functions that perform network operations (such as <xref:System.Net.Sockets.Socket.Send%2A> and <xref:System.Net.Sockets.Socket.Receive%2A>) wait until the operation completes before returning control to the calling program.</span></span> <span data-ttu-id="78b19-109">W trybie asynchronicznego te wywołania zwracają natychmiast.</span><span class="sxs-lookup"><span data-stu-id="78b19-109">In asynchronous mode, these calls return immediately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78b19-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="78b19-110">See also</span></span>

- [<span data-ttu-id="78b19-111">Instrukcje: tworzenie gniazda</span><span class="sxs-lookup"><span data-stu-id="78b19-111">How to: Create a Socket</span></span>](how-to-create-a-socket.md)

- [<span data-ttu-id="78b19-112">Korzystanie z protokołów aplikacji</span><span class="sxs-lookup"><span data-stu-id="78b19-112">Using Application Protocols</span></span>](using-application-protocols.md)
