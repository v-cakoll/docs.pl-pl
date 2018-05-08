---
title: Sieć Web i uprawnienia gniazda
ms.date: 03/30/2017
helpviewer_keywords:
- Networking
- positions [.NET Framework], accepting
- sockets, permissions
- network, permissions
- Internet, permissions
- Network Resources
- SocketPermission class, about SocketPermission class
- positions [.NET Framework], connecting
- WebPermission class, about WebPermission class
- permissions [.NET Framework], sockets
- security [.NET Framework], Internet
- positions [.NET Framework], granting
ms.assetid: d51ad8cb-03ae-4a51-bfcd-cfcf6b98afa9
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 4353f029d2e82460ab413bc8ccc248577a505504
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="web-and-socket-permissions"></a>Sieć Web i uprawnienia gniazda
Zabezpieczenia internetowe dla aplikacji za pomocą <xref:System.Net> przestrzeni nazw jest zapewniana przez <xref:System.Net.WebPermission> i <xref:System.Net.SocketPermission> klasy. **WebPermission** klasa steruje aplikacji prawo do dane żądania z identyfikatora URI lub do obsługi identyfikatora URI z Internetem. **SocketPermission** klasy formantów aplikacji przez prawo, aby użyć <xref:System.Net.Sockets.Socket> akceptować dane na port lokalny lub skontaktuj się z urządzeń zdalnych przy użyciu protokołu transportu na inny adres, oparta na hoście, a numer portu i protokół Transport gniazda.  
  
 Klasy uprawnień, których można użyć zależy od typu aplikacji. Aplikacje używające <xref:System.Net.WebRequest> i jego elementy podrzędne powinny używać **WebPermission** klasy do zarządzania uprawnieniami. Aplikacje używające dostęp na poziomie gniazda powinny używać **SocketPermission** klasy do zarządzania uprawnieniami.  
  
 **WebPermission** i **SocketPermission** zdefiniować dwa uprawnienia: Zaakceptuj i nawiąż połączenie. Zaakceptuj przyznaje prawa do odpowiedzi połączenia przychodzącego z innej strony aplikacji. Połącz przyznaje uprawnienia do nawiązania połączenia do innej strony aplikacji.  
  
 Dla **SocketPermission** wystąpienia, akceptować oznacza, że aplikacja może akceptować połączeń przychodzących na komputerze lokalnym transportu adres; połączyć oznacza, że aplikacja może nawiązać połączenie niektórych adres transportu (lokalnej lub zdalnej).  
  
 Dla **WebPermission** wystąpienia, akceptować oznacza, że aplikację można wyeksportować kontrolowane przez identyfikator URI **WebPermission** World; połączyć oznacza, że aplikacja może uzyskiwać dostęp do tego identyfikatora URI (czy jest lokalnych lub zdalnych).  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia](../../../docs/standard/security/index.md)  
 [Zabezpieczenia w programowaniu sieciowym](../../../docs/framework/network-programming/security-in-network-programming.md)
