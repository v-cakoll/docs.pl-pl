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
ms.openlocfilehash: fbb4e5d7171c50c06f55706df90240ffa205ee73
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967621"
---
# <a name="web-and-socket-permissions"></a>Internet i uprawnienia gniazd
Zabezpieczenia internetowe dla aplikacji korzystających <xref:System.Net> z przestrzeni nazw są udostępniane <xref:System.Net.WebPermission> przez <xref:System.Net.SocketPermission> klasy i. Klasa **uprawnień** sieci Web kontroluje prawo aplikacji do żądania danych od identyfikatora URI lub do połączenia z Internetem za pomocą identyfikatora URI. Klasa **SocketPermission** kontroluje prawo aplikacji do użycia <xref:System.Net.Sockets.Socket> do akceptowania danych na porcie lokalnym lub kontaktowania się z urządzeniami zdalnymi przy użyciu protokołu transportowego na innym adresie, na podstawie hosta, numeru portu i protokołu transportowego używając.  
  
 Której klasy uprawnień używasz, zależy od typu aplikacji. Aplikacje, które <xref:System.Net.WebRequest> używają i ich elementów podrzędnych, powinny używać klasy webpermissions do zarządzania uprawnieniami. Aplikacje korzystające z dostępu na poziomie gniazda powinny używać klasy **SocketPermission** do zarządzania uprawnieniami.  
  
 **WebPermission** i **SocketPermission** definiują dwa uprawnienia: Zaakceptuj i Połącz. Zaakceptuj przyznaje aplikacji prawo do odpowiedzi na połączenie przychodzące od innej strony. Connect przyznaje aplikacji prawo do zainicjowania połączenia z inną stroną.  
  
 W przypadku wystąpień **SocketPermission** Akceptuj oznacza, że aplikacja może akceptować połączenia przychodzące na lokalnym adresie transportu; Łączenie oznacza, że aplikacja może połączyć się z niektórym (lub lokalnym) adresem transportowym.  
  
 W przypadku wystąpień z **uprawnieniami WebPermission** Zaakceptuj oznacza, że aplikacja może eksportować identyfikator URI kontrolowany przez **uprawnienie WebPermission** na świecie; połączenie oznacza, że aplikacja może uzyskać dostęp do tego identyfikatora URI (niezależnie od tego, czy jest to zdalne czy lokalne).  
  
## <a name="see-also"></a>Zobacz także

- [Zabezpieczenia](../../standard/security/index.md)
- [Zabezpieczenia w programowaniu sieciowym](../../../docs/framework/network-programming/security-in-network-programming.md)
