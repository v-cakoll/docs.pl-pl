---
title: Internet i uprawnienia gniazd
description: Dowiedz się, w jaki sposób klasy WebPermission i SocketPermission zapewniają bezpieczeństwo internetowe za pomocą przestrzeni nazw System.Net w .NET Framework.
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
ms.openlocfilehash: 08ae360e8097f7281631da2a3f9846994dfbf5b6
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501901"
---
# <a name="web-and-socket-permissions"></a>Internet i uprawnienia gniazd
Zabezpieczenia internetowe dla aplikacji korzystających z <xref:System.Net> przestrzeni nazw są udostępniane <xref:System.Net.WebPermission> przez <xref:System.Net.SocketPermission> klasy i. Klasa **uprawnień** sieci Web kontroluje prawo aplikacji do żądania danych od identyfikatora URI lub do połączenia z Internetem za pomocą identyfikatora URI. Klasa **SocketPermission** kontroluje prawo aplikacji do <xref:System.Net.Sockets.Socket> akceptowania danych na porcie lokalnym lub kontaktowania się z urządzeniami zdalnymi przy użyciu protokołu transportowego na innym adresie w oparciu o hosta, numer portu i protokół transportowy gniazda.  
  
 Której klasy uprawnień używasz, zależy od typu aplikacji. Aplikacje, które używają <xref:System.Net.WebRequest> i ich elementów podrzędnych, powinny **WebPermission** używać klasy webpermissions do zarządzania uprawnieniami. Aplikacje korzystające z dostępu na poziomie gniazda powinny używać klasy **SocketPermission** do zarządzania uprawnieniami.  
  
 **WebPermission** i **SocketPermission** definiują dwa uprawnienia: Zaakceptuj i Połącz. Zaakceptuj przyznaje aplikacji prawo do odpowiedzi na połączenie przychodzące od innej strony. Connect przyznaje aplikacji prawo do zainicjowania połączenia z inną stroną.  
  
 W przypadku wystąpień **SocketPermission** Akceptuj oznacza, że aplikacja może akceptować połączenia przychodzące na lokalnym adresie transportu; Łączenie oznacza, że aplikacja może połączyć się z niektórym (lub lokalnym) adresem transportowym.  
  
 W przypadku wystąpień z **uprawnieniami WebPermission** Zaakceptuj oznacza, że aplikacja może eksportować identyfikator URI kontrolowany przez **uprawnienie WebPermission** na świecie; połączenie oznacza, że aplikacja może uzyskać dostęp do tego identyfikatora URI (niezależnie od tego, czy jest to zdalne czy lokalne).  
  
## <a name="see-also"></a>Zobacz także

- [Bezpieczeństwo](../../standard/security/index.md)
- [Zabezpieczenia w programowaniu sieciowym](security-in-network-programming.md)
