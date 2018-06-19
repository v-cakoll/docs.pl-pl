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
manager: markl
ms.openlocfilehash: b234846e63eab59602069aa72125df116e30375d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33398290"
---
# <a name="sockets"></a><span data-ttu-id="e996d-102">Gniazda</span><span class="sxs-lookup"><span data-stu-id="e996d-102">Sockets</span></span>
<span data-ttu-id="e996d-103"><xref:System.Net.Sockets> Przestrzeń nazw zawiera zarządzaną implementację interfejsu Windows Sockets.</span><span class="sxs-lookup"><span data-stu-id="e996d-103">The <xref:System.Net.Sockets> namespace contains a managed implementation of the Windows Sockets interface.</span></span> <span data-ttu-id="e996d-104">Wszystkie inne sieci dostęp do klas w <xref:System.Net> przestrzeni nazw są oparte na tej implementacji gniazd.</span><span class="sxs-lookup"><span data-stu-id="e996d-104">All other network-access classes in the <xref:System.Net> namespace are built on top of this implementation of sockets.</span></span>  
  
 <span data-ttu-id="e996d-105">.NET Framework <xref:System.Net.Sockets.Socket> klasy jest wersja kodu zarządzanego usług gniazda udostępniony przez interfejs API Winsock32.</span><span class="sxs-lookup"><span data-stu-id="e996d-105">The .NET Framework <xref:System.Net.Sockets.Socket> class is a managed-code version of the socket services provided by the Winsock32 API.</span></span> <span data-ttu-id="e996d-106">W większości przypadków **gniazda** metody klasy, po prostu organizowania danych do ich macierzystym odpowiednikowi Win32 i obsługiwać żadnych kontroli zabezpieczeń niezbędne.</span><span class="sxs-lookup"><span data-stu-id="e996d-106">In most cases, the **Socket** class methods simply marshal data into their native Win32 counterparts and handle any necessary security checks.</span></span>  
  
 <span data-ttu-id="e996d-107">**Gniazda** klasa obsługuje dwa tryby podstawowe synchroniczne i asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="e996d-107">The **Socket** class supports two basic modes, synchronous and asynchronous.</span></span> <span data-ttu-id="e996d-108">W trybie synchronicznym wywołań funkcji, które wykonują operacje sieciowe (takie jak <xref:System.Net.Sockets.Socket.Send%2A> i <xref:System.Net.Sockets.Socket.Receive%2A>) poczekaj na zakończenie operacji przed zwróceniem sterowania do wywoływania programu.</span><span class="sxs-lookup"><span data-stu-id="e996d-108">In synchronous mode, calls to functions that perform network operations (such as <xref:System.Net.Sockets.Socket.Send%2A> and <xref:System.Net.Sockets.Socket.Receive%2A>) wait until the operation completes before returning control to the calling program.</span></span> <span data-ttu-id="e996d-109">W trybie asynchronicznym tych wywołań zwracać natychmiast.</span><span class="sxs-lookup"><span data-stu-id="e996d-109">In asynchronous mode, these calls return immediately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e996d-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e996d-110">See Also</span></span>  
 [<span data-ttu-id="e996d-111">Instrukcje: tworzenie gniazda</span><span class="sxs-lookup"><span data-stu-id="e996d-111">How to: Create a Socket</span></span>](../../../docs/framework/network-programming/how-to-create-a-socket.md)  
    
 [<span data-ttu-id="e996d-112">Korzystanie z protokołów aplikacji</span><span class="sxs-lookup"><span data-stu-id="e996d-112">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)
