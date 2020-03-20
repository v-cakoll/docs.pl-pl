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
ms.openlocfilehash: d1b993acbf20eac244e596075c3f826bba3211a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "71046865"
---
# <a name="web-and-socket-permissions"></a>Internet i uprawnienia gniazd
Zabezpieczenia internetowe dla <xref:System.Net> aplikacji korzystających z <xref:System.Net.WebPermission> <xref:System.Net.SocketPermission> obszaru nazw jest dostarczana przez i klasy. **Klasa WebPermission** kontroluje prawo aplikacji do żądania danych z identyfikatora URI lub do obsługi identyfikatora URI w Internecie. **SocketPermission** Klasy kontroluje prawo aplikacji do <xref:System.Net.Sockets.Socket> używania a do akceptowania danych na porcie lokalnym lub do kontaktu z urządzeniami zdalnymi przy użyciu protokołu transportu pod innym adresem, na podstawie hosta, numer portu i protokołu transportu gniazda.  
  
 Klasa uprawnień, której używasz, zależy od typu aplikacji. Aplikacje, <xref:System.Net.WebRequest> które używają i jego elementów podrzędnych należy użyć **WebPermission** klasy do zarządzania uprawnieniami. Aplikacje korzystające z dostępu na poziomie gniazda należy użyć **SocketPermission** klasy do zarządzania uprawnieniami.  
  
 **WebPermission** i **SocketPermission** definiują dwa uprawnienia: zaakceptować i połączyć. Accept przyznaje aplikacji prawo do odpowiedzi na przychodzące połączenie od innej strony. Connect przyznaje aplikacji prawo do zainicjowania połączenia z inną stroną.  
  
 W przypadku wystąpień **SocketPermission** zaakceptuj oznacza, że aplikacja może akceptować połączenia przychodzące na adres transportu lokalnego; connect oznacza, że aplikacja może połączyć się z lokalnym (lub lokalnym) adresem transportu.  
  
 W przypadku wystąpień **WebPermission** zaakceptuj oznacza, że aplikacja może eksportować identyfikator URI kontrolowany przez **WebPermission** do świata; connect oznacza, że aplikacja może uzyskać dostęp do tego identyfikatora URI (niezależnie od tego, czy jest zdalny, czy lokalny).  
  
## <a name="see-also"></a>Zobacz też

- [Zabezpieczenia](../../standard/security/index.md)
- [Zabezpieczenia w programowaniu sieciowym](security-in-network-programming.md)
