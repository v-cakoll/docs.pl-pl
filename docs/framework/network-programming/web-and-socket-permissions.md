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
# <a name="web-and-socket-permissions"></a><span data-ttu-id="d7abf-102">Internet i uprawnienia gniazd</span><span class="sxs-lookup"><span data-stu-id="d7abf-102">Web and Socket Permissions</span></span>
<span data-ttu-id="d7abf-103">Zabezpieczenia internetowe dla <xref:System.Net> aplikacji korzystających z <xref:System.Net.WebPermission> <xref:System.Net.SocketPermission> obszaru nazw jest dostarczana przez i klasy.</span><span class="sxs-lookup"><span data-stu-id="d7abf-103">Internet security for applications using the <xref:System.Net> namespace is provided by the <xref:System.Net.WebPermission> and <xref:System.Net.SocketPermission> classes.</span></span> <span data-ttu-id="d7abf-104">**Klasa WebPermission** kontroluje prawo aplikacji do żądania danych z identyfikatora URI lub do obsługi identyfikatora URI w Internecie.</span><span class="sxs-lookup"><span data-stu-id="d7abf-104">The **WebPermission** class controls an application's right to request data from a URI or to serve a URI to the Internet.</span></span> <span data-ttu-id="d7abf-105">**SocketPermission** Klasy kontroluje prawo aplikacji do <xref:System.Net.Sockets.Socket> używania a do akceptowania danych na porcie lokalnym lub do kontaktu z urządzeniami zdalnymi przy użyciu protokołu transportu pod innym adresem, na podstawie hosta, numer portu i protokołu transportu gniazda.</span><span class="sxs-lookup"><span data-stu-id="d7abf-105">The **SocketPermission** class controls an application's right to use a <xref:System.Net.Sockets.Socket> to accept data on a local port or to contact remote devices using a transport protocol at another address, based on the host, port number, and transport protocol of the socket.</span></span>  
  
 <span data-ttu-id="d7abf-106">Klasa uprawnień, której używasz, zależy od typu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d7abf-106">Which permission class you use depends on your application type.</span></span> <span data-ttu-id="d7abf-107">Aplikacje, <xref:System.Net.WebRequest> które używają i jego elementów podrzędnych należy użyć **WebPermission** klasy do zarządzania uprawnieniami.</span><span class="sxs-lookup"><span data-stu-id="d7abf-107">Applications that use <xref:System.Net.WebRequest> and its descendants should use the **WebPermission** class to manage permissions.</span></span> <span data-ttu-id="d7abf-108">Aplikacje korzystające z dostępu na poziomie gniazda należy użyć **SocketPermission** klasy do zarządzania uprawnieniami.</span><span class="sxs-lookup"><span data-stu-id="d7abf-108">Applications that use socket-level access should use the **SocketPermission** class to manage permissions.</span></span>  
  
 <span data-ttu-id="d7abf-109">**WebPermission** i **SocketPermission** definiują dwa uprawnienia: zaakceptować i połączyć.</span><span class="sxs-lookup"><span data-stu-id="d7abf-109">**WebPermission** and **SocketPermission** define two permissions: accept and connect.</span></span> <span data-ttu-id="d7abf-110">Accept przyznaje aplikacji prawo do odpowiedzi na przychodzące połączenie od innej strony.</span><span class="sxs-lookup"><span data-stu-id="d7abf-110">Accept grants the application the right to answer an incoming connection from another party.</span></span> <span data-ttu-id="d7abf-111">Connect przyznaje aplikacji prawo do zainicjowania połączenia z inną stroną.</span><span class="sxs-lookup"><span data-stu-id="d7abf-111">Connect grants the application the right to initiate a connection to another party.</span></span>  
  
 <span data-ttu-id="d7abf-112">W przypadku wystąpień **SocketPermission** zaakceptuj oznacza, że aplikacja może akceptować połączenia przychodzące na adres transportu lokalnego; connect oznacza, że aplikacja może połączyć się z lokalnym (lub lokalnym) adresem transportu.</span><span class="sxs-lookup"><span data-stu-id="d7abf-112">For **SocketPermission** instances, accept means that an application can accept incoming connections on a local transport address; connect means that an application can connect to some remote (or local) transport address.</span></span>  
  
 <span data-ttu-id="d7abf-113">W przypadku wystąpień **WebPermission** zaakceptuj oznacza, że aplikacja może eksportować identyfikator URI kontrolowany przez **WebPermission** do świata; connect oznacza, że aplikacja może uzyskać dostęp do tego identyfikatora URI (niezależnie od tego, czy jest zdalny, czy lokalny).</span><span class="sxs-lookup"><span data-stu-id="d7abf-113">For **WebPermission** instances, accept means that an application can export the URI controlled by the **WebPermission** to the world; connect means that an application can access that URI (whether it is remote or local).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7abf-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d7abf-114">See also</span></span>

- [<span data-ttu-id="d7abf-115">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="d7abf-115">Security</span></span>](../../standard/security/index.md)
- [<span data-ttu-id="d7abf-116">Zabezpieczenia w programowaniu sieciowym</span><span class="sxs-lookup"><span data-stu-id="d7abf-116">Security in Network Programming</span></span>](security-in-network-programming.md)
