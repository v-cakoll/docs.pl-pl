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
# <a name="web-and-socket-permissions"></a><span data-ttu-id="2d9c1-103">Internet i uprawnienia gniazd</span><span class="sxs-lookup"><span data-stu-id="2d9c1-103">Web and Socket Permissions</span></span>
<span data-ttu-id="2d9c1-104">Zabezpieczenia internetowe dla aplikacji korzystających z <xref:System.Net> przestrzeni nazw są udostępniane <xref:System.Net.WebPermission> przez <xref:System.Net.SocketPermission> klasy i.</span><span class="sxs-lookup"><span data-stu-id="2d9c1-104">Internet security for applications using the <xref:System.Net> namespace is provided by the <xref:System.Net.WebPermission> and <xref:System.Net.SocketPermission> classes.</span></span> <span data-ttu-id="2d9c1-105">Klasa **uprawnień** sieci Web kontroluje prawo aplikacji do żądania danych od identyfikatora URI lub do połączenia z Internetem za pomocą identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="2d9c1-105">The **WebPermission** class controls an application's right to request data from a URI or to serve a URI to the Internet.</span></span> <span data-ttu-id="2d9c1-106">Klasa **SocketPermission** kontroluje prawo aplikacji do <xref:System.Net.Sockets.Socket> akceptowania danych na porcie lokalnym lub kontaktowania się z urządzeniami zdalnymi przy użyciu protokołu transportowego na innym adresie w oparciu o hosta, numer portu i protokół transportowy gniazda.</span><span class="sxs-lookup"><span data-stu-id="2d9c1-106">The **SocketPermission** class controls an application's right to use a <xref:System.Net.Sockets.Socket> to accept data on a local port or to contact remote devices using a transport protocol at another address, based on the host, port number, and transport protocol of the socket.</span></span>  
  
 <span data-ttu-id="2d9c1-107">Której klasy uprawnień używasz, zależy od typu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2d9c1-107">Which permission class you use depends on your application type.</span></span> <span data-ttu-id="2d9c1-108">Aplikacje, które używają <xref:System.Net.WebRequest> i ich elementów podrzędnych, powinny **WebPermission** używać klasy webpermissions do zarządzania uprawnieniami.</span><span class="sxs-lookup"><span data-stu-id="2d9c1-108">Applications that use <xref:System.Net.WebRequest> and its descendants should use the **WebPermission** class to manage permissions.</span></span> <span data-ttu-id="2d9c1-109">Aplikacje korzystające z dostępu na poziomie gniazda powinny używać klasy **SocketPermission** do zarządzania uprawnieniami.</span><span class="sxs-lookup"><span data-stu-id="2d9c1-109">Applications that use socket-level access should use the **SocketPermission** class to manage permissions.</span></span>  
  
 <span data-ttu-id="2d9c1-110">**WebPermission** i **SocketPermission** definiują dwa uprawnienia: Zaakceptuj i Połącz.</span><span class="sxs-lookup"><span data-stu-id="2d9c1-110">**WebPermission** and **SocketPermission** define two permissions: accept and connect.</span></span> <span data-ttu-id="2d9c1-111">Zaakceptuj przyznaje aplikacji prawo do odpowiedzi na połączenie przychodzące od innej strony.</span><span class="sxs-lookup"><span data-stu-id="2d9c1-111">Accept grants the application the right to answer an incoming connection from another party.</span></span> <span data-ttu-id="2d9c1-112">Connect przyznaje aplikacji prawo do zainicjowania połączenia z inną stroną.</span><span class="sxs-lookup"><span data-stu-id="2d9c1-112">Connect grants the application the right to initiate a connection to another party.</span></span>  
  
 <span data-ttu-id="2d9c1-113">W przypadku wystąpień **SocketPermission** Akceptuj oznacza, że aplikacja może akceptować połączenia przychodzące na lokalnym adresie transportu; Łączenie oznacza, że aplikacja może połączyć się z niektórym (lub lokalnym) adresem transportowym.</span><span class="sxs-lookup"><span data-stu-id="2d9c1-113">For **SocketPermission** instances, accept means that an application can accept incoming connections on a local transport address; connect means that an application can connect to some remote (or local) transport address.</span></span>  
  
 <span data-ttu-id="2d9c1-114">W przypadku wystąpień z **uprawnieniami WebPermission** Zaakceptuj oznacza, że aplikacja może eksportować identyfikator URI kontrolowany przez **uprawnienie WebPermission** na świecie; połączenie oznacza, że aplikacja może uzyskać dostęp do tego identyfikatora URI (niezależnie od tego, czy jest to zdalne czy lokalne).</span><span class="sxs-lookup"><span data-stu-id="2d9c1-114">For **WebPermission** instances, accept means that an application can export the URI controlled by the **WebPermission** to the world; connect means that an application can access that URI (whether it is remote or local).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d9c1-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2d9c1-115">See also</span></span>

- [<span data-ttu-id="2d9c1-116">Bezpieczeństwo</span><span class="sxs-lookup"><span data-stu-id="2d9c1-116">Security</span></span>](../../standard/security/index.md)
- [<span data-ttu-id="2d9c1-117">Zabezpieczenia w programowaniu sieciowym</span><span class="sxs-lookup"><span data-stu-id="2d9c1-117">Security in Network Programming</span></span>](security-in-network-programming.md)
