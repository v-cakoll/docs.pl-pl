---
title: Internet i uprawnienia gniazd
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
ms.openlocfilehash: 78ad06107155408b2aca854a8251c21a24c6577a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788092"
---
# <a name="web-and-socket-permissions"></a>Internet i uprawnienia gniazd
Zabezpieczenia internetowe dla aplikacji za pomocą <xref:System.Net> przestrzeni nazw są dostarczane przez <xref:System.Net.WebPermission> i <xref:System.Net.SocketPermission> klasy. **WebPermission** klasy kontrolki aplikacji bezpośrednio do dane żądania z identyfikatora URI lub do obsługi identyfikatora URI z Internetem. **SocketPermission** klasy aplikacji w prawo, aby użyć kontrolki <xref:System.Net.Sockets.Socket> akceptować dane na port lokalny lub skontaktuj się z urządzeniami zdalnymi przy użyciu protokołu transportowego poziomu innego adresu, oparte na hoście, a numer portu i protokół Transport gniazda.  
  
 Klasa uprawnień, których używasz, zależy od danego typu aplikacji. Aplikacje, które używają <xref:System.Net.WebRequest> i jego elementy podrzędne należy używać **WebPermission** klasy, aby zarządzać uprawnieniami. Skorzystaj z aplikacji, które używają dostęp na poziomie gniazd **SocketPermission** klasy, aby zarządzać uprawnieniami.  
  
 **WebPermission** i **SocketPermission** zdefiniować dwa uprawnienia: Zaakceptuj i Połącz z. Zaakceptuj nadaje aplikacji prawa do odpowiedzi na połączenia przychodzące z innej strony. Połącz przyznaje uprawnienia do nawiązania połączenia do innej strony aplikacji.  
  
 Dla **SocketPermission** wystąpień, Zaakceptuj oznacza, że aplikacja może akceptować połączeń przychodzących w lokalnym transportu adres; Łączenie oznacza, że aplikacja może nawiązać niektóre adres transportu (lokalnej lub zdalnej).  
  
 Dla **WebPermission** wystąpień, Zaakceptuj oznacza, że aplikację można wyeksportować identyfikatora URI w wartości clientauthtrustmode **WebPermission** na świecie; Łączenie oznacza, że aplikacja może uzyskiwać dostęp do tego identyfikatora URI (czy jest zdalny czy lokalny).  
  
## <a name="see-also"></a>Zobacz także

- [Zabezpieczenia](../../../docs/standard/security/index.md)
- [Zabezpieczenia w programowaniu sieciowym](../../../docs/framework/network-programming/security-in-network-programming.md)
