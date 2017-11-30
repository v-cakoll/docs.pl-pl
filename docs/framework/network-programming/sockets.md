---
title: Gniazda
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: de5778e398a9a7205e99cc810d0b672ac247da08
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="sockets"></a><span data-ttu-id="e0772-102">Gniazda</span><span class="sxs-lookup"><span data-stu-id="e0772-102">Sockets</span></span>
<span data-ttu-id="e0772-103"><xref:System.Net.Sockets> Przestrzeń nazw zawiera zarządzaną implementację interfejsu Windows Sockets.</span><span class="sxs-lookup"><span data-stu-id="e0772-103">The <xref:System.Net.Sockets> namespace contains a managed implementation of the Windows Sockets interface.</span></span> <span data-ttu-id="e0772-104">Wszystkie inne sieci dostęp do klas w <xref:System.Net> przestrzeni nazw są oparte na tej implementacji gniazd.</span><span class="sxs-lookup"><span data-stu-id="e0772-104">All other network-access classes in the <xref:System.Net> namespace are built on top of this implementation of sockets.</span></span>  
  
 <span data-ttu-id="e0772-105">.NET Framework <xref:System.Net.Sockets.Socket> klasy jest wersja kodu zarządzanego usług gniazda udostępniony przez interfejs API Winsock32.</span><span class="sxs-lookup"><span data-stu-id="e0772-105">The .NET Framework <xref:System.Net.Sockets.Socket> class is a managed-code version of the socket services provided by the Winsock32 API.</span></span> <span data-ttu-id="e0772-106">W większości przypadków **gniazda** metody klasy, po prostu organizowania danych do ich macierzystym odpowiednikowi Win32 i obsługiwać żadnych kontroli zabezpieczeń niezbędne.</span><span class="sxs-lookup"><span data-stu-id="e0772-106">In most cases, the **Socket** class methods simply marshal data into their native Win32 counterparts and handle any necessary security checks.</span></span>  
  
 <span data-ttu-id="e0772-107">**Gniazda** klasa obsługuje dwa tryby podstawowe synchroniczne i asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="e0772-107">The **Socket** class supports two basic modes, synchronous and asynchronous.</span></span> <span data-ttu-id="e0772-108">W trybie synchronicznym wywołań funkcji, które wykonują operacje sieciowe (takie jak <xref:System.Net.Sockets.Socket.Send%2A> i <xref:System.Net.Sockets.Socket.Receive%2A>) poczekaj na zakończenie operacji przed zwróceniem sterowania do wywoływania programu.</span><span class="sxs-lookup"><span data-stu-id="e0772-108">In synchronous mode, calls to functions that perform network operations (such as <xref:System.Net.Sockets.Socket.Send%2A> and <xref:System.Net.Sockets.Socket.Receive%2A>) wait until the operation completes before returning control to the calling program.</span></span> <span data-ttu-id="e0772-109">W trybie asynchronicznym tych wywołań zwracać natychmiast.</span><span class="sxs-lookup"><span data-stu-id="e0772-109">In asynchronous mode, these calls return immediately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0772-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e0772-110">See Also</span></span>  
 [<span data-ttu-id="e0772-111">Porady: Tworzenie gniazda</span><span class="sxs-lookup"><span data-stu-id="e0772-111">How to: Create a Socket</span></span>](../../../docs/framework/network-programming/how-to-create-a-socket.md)  
    
 [<span data-ttu-id="e0772-112">Przy użyciu protokołów aplikacji</span><span class="sxs-lookup"><span data-stu-id="e0772-112">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)
