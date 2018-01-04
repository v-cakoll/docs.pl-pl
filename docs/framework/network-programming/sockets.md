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
ms.workload: dotnet
ms.openlocfilehash: 9050c7bdae8f08601259e865742016f188d3e0af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="sockets"></a>Gniazda
<xref:System.Net.Sockets> Przestrzeń nazw zawiera zarządzaną implementację interfejsu Windows Sockets. Wszystkie inne sieci dostęp do klas w <xref:System.Net> przestrzeni nazw są oparte na tej implementacji gniazd.  
  
 .NET Framework <xref:System.Net.Sockets.Socket> klasy jest wersja kodu zarządzanego usług gniazda udostępniony przez interfejs API Winsock32. W większości przypadków **gniazda** metody klasy, po prostu organizowania danych do ich macierzystym odpowiednikowi Win32 i obsługiwać żadnych kontroli zabezpieczeń niezbędne.  
  
 **Gniazda** klasa obsługuje dwa tryby podstawowe synchroniczne i asynchroniczne. W trybie synchronicznym wywołań funkcji, które wykonują operacje sieciowe (takie jak <xref:System.Net.Sockets.Socket.Send%2A> i <xref:System.Net.Sockets.Socket.Receive%2A>) poczekaj na zakończenie operacji przed zwróceniem sterowania do wywoływania programu. W trybie asynchronicznym tych wywołań zwracać natychmiast.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: tworzenie gniazda](../../../docs/framework/network-programming/how-to-create-a-socket.md)  
    
 [Korzystanie z protokołów aplikacji](../../../docs/framework/network-programming/using-application-protocols.md)
