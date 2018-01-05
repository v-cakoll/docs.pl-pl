---
title: "Sieć Web i uprawnienia gniazda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: b426b5e7e6a9b617311db05670f526fc415d591d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="web-and-socket-permissions"></a><span data-ttu-id="c849d-102">Sieć Web i uprawnienia gniazda</span><span class="sxs-lookup"><span data-stu-id="c849d-102">Web and Socket Permissions</span></span>
<span data-ttu-id="c849d-103">Zabezpieczenia internetowe dla aplikacji za pomocą <xref:System.Net> przestrzeni nazw jest zapewniana przez <xref:System.Net.WebPermission> i <xref:System.Net.SocketPermission> klasy.</span><span class="sxs-lookup"><span data-stu-id="c849d-103">Internet security for applications using the <xref:System.Net> namespace is provided by the <xref:System.Net.WebPermission> and <xref:System.Net.SocketPermission> classes.</span></span> <span data-ttu-id="c849d-104">**WebPermission** klasa steruje aplikacji prawo do dane żądania z identyfikatora URI lub do obsługi identyfikatora URI z Internetem.</span><span class="sxs-lookup"><span data-stu-id="c849d-104">The **WebPermission** class controls an application's right to request data from a URI or to serve a URI to the Internet.</span></span> <span data-ttu-id="c849d-105">**SocketPermission** klasy formantów aplikacji przez prawo, aby użyć <xref:System.Net.Sockets.Socket> akceptować dane na port lokalny lub skontaktuj się z urządzeń zdalnych przy użyciu protokołu transportu na inny adres, oparta na hoście, a numer portu i protokół Transport gniazda.</span><span class="sxs-lookup"><span data-stu-id="c849d-105">The **SocketPermission** class controls an application's right to use a <xref:System.Net.Sockets.Socket> to accept data on a local port or to contact remote devices using a transport protocol at another address, based on the host, port number, and transport protocol of the socket.</span></span>  
  
 <span data-ttu-id="c849d-106">Klasy uprawnień, których można użyć zależy od typu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c849d-106">Which permission class you use depends on your application type.</span></span> <span data-ttu-id="c849d-107">Aplikacje używające <xref:System.Net.WebRequest> i jego elementy podrzędne powinny używać **WebPermission** klasy do zarządzania uprawnieniami.</span><span class="sxs-lookup"><span data-stu-id="c849d-107">Applications that use <xref:System.Net.WebRequest> and its descendants should use the **WebPermission** class to manage permissions.</span></span> <span data-ttu-id="c849d-108">Aplikacje używające dostęp na poziomie gniazda powinny używać **SocketPermission** klasy do zarządzania uprawnieniami.</span><span class="sxs-lookup"><span data-stu-id="c849d-108">Applications that use socket-level access should use the **SocketPermission** class to manage permissions.</span></span>  
  
 <span data-ttu-id="c849d-109">**WebPermission** i **SocketPermission** zdefiniować dwa uprawnienia: Zaakceptuj i nawiąż połączenie.</span><span class="sxs-lookup"><span data-stu-id="c849d-109">**WebPermission** and **SocketPermission** define two permissions: accept and connect.</span></span> <span data-ttu-id="c849d-110">Zaakceptuj przyznaje prawa do odpowiedzi połączenia przychodzącego z innej strony aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c849d-110">Accept grants the application the right to answer an incoming connection from another party.</span></span> <span data-ttu-id="c849d-111">Połącz przyznaje uprawnienia do nawiązania połączenia do innej strony aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c849d-111">Connect grants the application the right to initiate a connection to another party.</span></span>  
  
 <span data-ttu-id="c849d-112">Dla **SocketPermission** wystąpienia, akceptować oznacza, że aplikacja może akceptować połączeń przychodzących na komputerze lokalnym transportu adres; połączyć oznacza, że aplikacja może nawiązać połączenie niektórych adres transportu (lokalnej lub zdalnej).</span><span class="sxs-lookup"><span data-stu-id="c849d-112">For **SocketPermission** instances, accept means that an application can accept incoming connections on a local transport address; connect means that an application can connect to some remote (or local) transport address.</span></span>  
  
 <span data-ttu-id="c849d-113">Dla **WebPermission** wystąpienia, akceptować oznacza, że aplikację można wyeksportować kontrolowane przez identyfikator URI **WebPermission** World; połączyć oznacza, że aplikacja może uzyskiwać dostęp do tego identyfikatora URI (czy jest lokalnych lub zdalnych).</span><span class="sxs-lookup"><span data-stu-id="c849d-113">For **WebPermission** instances, accept means that an application can export the URI controlled by the **WebPermission** to the world; connect means that an application can access that URI (whether it is remote or local).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c849d-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c849d-114">See Also</span></span>  
 [<span data-ttu-id="c849d-115">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="c849d-115">Security</span></span>](../../../docs/standard/security/index.md)  
 [<span data-ttu-id="c849d-116">Zabezpieczenia w programowaniu sieciowym</span><span class="sxs-lookup"><span data-stu-id="c849d-116">Security in Network Programming</span></span>](../../../docs/framework/network-programming/security-in-network-programming.md)
