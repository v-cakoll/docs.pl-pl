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
# <a name="sockets"></a>Gniazda
<xref:System.Net.Sockets> Przestrzeń nazw zawiera zarządzaną implementację interfejsu Windows Sockets. Wszystkie inne sieci dostęp do klas w <xref:System.Net> przestrzeni nazw są oparte na tej implementacji gniazd.  
  
 .NET Framework <xref:System.Net.Sockets.Socket> klasy jest wersja kodu zarządzanego usług gniazda udostępniony przez interfejs API Winsock32. W większości przypadków **gniazda** metody klasy, po prostu organizowania danych do ich macierzystym odpowiednikowi Win32 i obsługiwać żadnych kontroli zabezpieczeń niezbędne.  
  
 **Gniazda** klasa obsługuje dwa tryby podstawowe synchroniczne i asynchroniczne. W trybie synchronicznym wywołań funkcji, które wykonują operacje sieciowe (takie jak <xref:System.Net.Sockets.Socket.Send%2A> i <xref:System.Net.Sockets.Socket.Receive%2A>) poczekaj na zakończenie operacji przed zwróceniem sterowania do wywoływania programu. W trybie asynchronicznym tych wywołań zwracać natychmiast.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Tworzenie gniazda](../../../docs/framework/network-programming/how-to-create-a-socket.md)  
    
 [Przy użyciu protokołów aplikacji](../../../docs/framework/network-programming/using-application-protocols.md)
