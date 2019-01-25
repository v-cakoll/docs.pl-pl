---
title: Sieć Web i uprawnienia gniazd
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
ms.openlocfilehash: b4395d26114425556f0457f03667d0f95f786ca7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54677644"
---
# <a name="web-and-socket-permissions"></a><span data-ttu-id="6df78-102">Sieć Web i uprawnienia gniazd</span><span class="sxs-lookup"><span data-stu-id="6df78-102">Web and Socket Permissions</span></span>
<span data-ttu-id="6df78-103">Zabezpieczenia internetowe dla aplikacji za pomocą <xref:System.Net> przestrzeni nazw są dostarczane przez <xref:System.Net.WebPermission> i <xref:System.Net.SocketPermission> klasy.</span><span class="sxs-lookup"><span data-stu-id="6df78-103">Internet security for applications using the <xref:System.Net> namespace is provided by the <xref:System.Net.WebPermission> and <xref:System.Net.SocketPermission> classes.</span></span> <span data-ttu-id="6df78-104">**WebPermission** klasy kontrolki aplikacji bezpośrednio do dane żądania z identyfikatora URI lub do obsługi identyfikatora URI z Internetem.</span><span class="sxs-lookup"><span data-stu-id="6df78-104">The **WebPermission** class controls an application's right to request data from a URI or to serve a URI to the Internet.</span></span> <span data-ttu-id="6df78-105">**SocketPermission** klasy aplikacji w prawo, aby użyć kontrolki <xref:System.Net.Sockets.Socket> akceptować dane na port lokalny lub skontaktuj się z urządzeniami zdalnymi przy użyciu protokołu transportowego poziomu innego adresu, oparte na hoście, a numer portu i protokół Transport gniazda.</span><span class="sxs-lookup"><span data-stu-id="6df78-105">The **SocketPermission** class controls an application's right to use a <xref:System.Net.Sockets.Socket> to accept data on a local port or to contact remote devices using a transport protocol at another address, based on the host, port number, and transport protocol of the socket.</span></span>  
  
 <span data-ttu-id="6df78-106">Klasa uprawnień, których używasz, zależy od danego typu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6df78-106">Which permission class you use depends on your application type.</span></span> <span data-ttu-id="6df78-107">Aplikacje, które używają <xref:System.Net.WebRequest> i jego elementy podrzędne należy używać **WebPermission** klasy, aby zarządzać uprawnieniami.</span><span class="sxs-lookup"><span data-stu-id="6df78-107">Applications that use <xref:System.Net.WebRequest> and its descendants should use the **WebPermission** class to manage permissions.</span></span> <span data-ttu-id="6df78-108">Skorzystaj z aplikacji, które używają dostęp na poziomie gniazd **SocketPermission** klasy, aby zarządzać uprawnieniami.</span><span class="sxs-lookup"><span data-stu-id="6df78-108">Applications that use socket-level access should use the **SocketPermission** class to manage permissions.</span></span>  
  
 <span data-ttu-id="6df78-109">**WebPermission** i **SocketPermission** zdefiniować dwa uprawnienia: Zaakceptuj i Połącz z.</span><span class="sxs-lookup"><span data-stu-id="6df78-109">**WebPermission** and **SocketPermission** define two permissions: accept and connect.</span></span> <span data-ttu-id="6df78-110">Zaakceptuj nadaje aplikacji prawa do odpowiedzi na połączenia przychodzące z innej strony.</span><span class="sxs-lookup"><span data-stu-id="6df78-110">Accept grants the application the right to answer an incoming connection from another party.</span></span> <span data-ttu-id="6df78-111">Połącz przyznaje uprawnienia do nawiązania połączenia do innej strony aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6df78-111">Connect grants the application the right to initiate a connection to another party.</span></span>  
  
 <span data-ttu-id="6df78-112">Dla **SocketPermission** wystąpień, Zaakceptuj oznacza, że aplikacja może akceptować połączeń przychodzących w lokalnym transportu adres; Łączenie oznacza, że aplikacja może nawiązać niektóre adres transportu (lokalnej lub zdalnej).</span><span class="sxs-lookup"><span data-stu-id="6df78-112">For **SocketPermission** instances, accept means that an application can accept incoming connections on a local transport address; connect means that an application can connect to some remote (or local) transport address.</span></span>  
  
 <span data-ttu-id="6df78-113">Dla **WebPermission** wystąpień, Zaakceptuj oznacza, że aplikację można wyeksportować identyfikatora URI w wartości clientauthtrustmode **WebPermission** na świecie; Łączenie oznacza, że aplikacja może uzyskiwać dostęp do tego identyfikatora URI (czy jest zdalny czy lokalny).</span><span class="sxs-lookup"><span data-stu-id="6df78-113">For **WebPermission** instances, accept means that an application can export the URI controlled by the **WebPermission** to the world; connect means that an application can access that URI (whether it is remote or local).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6df78-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6df78-114">See also</span></span>
- [<span data-ttu-id="6df78-115">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="6df78-115">Security</span></span>](../../../docs/standard/security/index.md)
- [<span data-ttu-id="6df78-116">Zabezpieczenia w programowaniu sieciowym</span><span class="sxs-lookup"><span data-stu-id="6df78-116">Security in Network Programming</span></span>](../../../docs/framework/network-programming/security-in-network-programming.md)
