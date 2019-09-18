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
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046865"
---
# <a name="web-and-socket-permissions"></a><span data-ttu-id="51597-102">Internet i uprawnienia gniazd</span><span class="sxs-lookup"><span data-stu-id="51597-102">Web and Socket Permissions</span></span>
<span data-ttu-id="51597-103">Zabezpieczenia internetowe dla aplikacji korzystających <xref:System.Net> z przestrzeni nazw są udostępniane <xref:System.Net.WebPermission> przez <xref:System.Net.SocketPermission> klasy i.</span><span class="sxs-lookup"><span data-stu-id="51597-103">Internet security for applications using the <xref:System.Net> namespace is provided by the <xref:System.Net.WebPermission> and <xref:System.Net.SocketPermission> classes.</span></span> <span data-ttu-id="51597-104">Klasa **uprawnień** sieci Web kontroluje prawo aplikacji do żądania danych od identyfikatora URI lub do połączenia z Internetem za pomocą identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="51597-104">The **WebPermission** class controls an application's right to request data from a URI or to serve a URI to the Internet.</span></span> <span data-ttu-id="51597-105">Klasa **SocketPermission** kontroluje prawo aplikacji do użycia <xref:System.Net.Sockets.Socket> do akceptowania danych na porcie lokalnym lub kontaktowania się z urządzeniami zdalnymi przy użyciu protokołu transportowego na innym adresie, na podstawie hosta, numeru portu i protokołu transportowego używając.</span><span class="sxs-lookup"><span data-stu-id="51597-105">The **SocketPermission** class controls an application's right to use a <xref:System.Net.Sockets.Socket> to accept data on a local port or to contact remote devices using a transport protocol at another address, based on the host, port number, and transport protocol of the socket.</span></span>  
  
 <span data-ttu-id="51597-106">Której klasy uprawnień używasz, zależy od typu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="51597-106">Which permission class you use depends on your application type.</span></span> <span data-ttu-id="51597-107">Aplikacje, które <xref:System.Net.WebRequest> używają i ich elementów **podrzędnych, powinny używać klasy** webpermissions do zarządzania uprawnieniami.</span><span class="sxs-lookup"><span data-stu-id="51597-107">Applications that use <xref:System.Net.WebRequest> and its descendants should use the **WebPermission** class to manage permissions.</span></span> <span data-ttu-id="51597-108">Aplikacje korzystające z dostępu na poziomie gniazda powinny używać klasy **SocketPermission** do zarządzania uprawnieniami.</span><span class="sxs-lookup"><span data-stu-id="51597-108">Applications that use socket-level access should use the **SocketPermission** class to manage permissions.</span></span>  
  
 <span data-ttu-id="51597-109">**WebPermission** i **SocketPermission** definiują dwa uprawnienia: Zaakceptuj i Połącz.</span><span class="sxs-lookup"><span data-stu-id="51597-109">**WebPermission** and **SocketPermission** define two permissions: accept and connect.</span></span> <span data-ttu-id="51597-110">Zaakceptuj przyznaje aplikacji prawo do odpowiedzi na połączenie przychodzące od innej strony.</span><span class="sxs-lookup"><span data-stu-id="51597-110">Accept grants the application the right to answer an incoming connection from another party.</span></span> <span data-ttu-id="51597-111">Connect przyznaje aplikacji prawo do zainicjowania połączenia z inną stroną.</span><span class="sxs-lookup"><span data-stu-id="51597-111">Connect grants the application the right to initiate a connection to another party.</span></span>  
  
 <span data-ttu-id="51597-112">W przypadku wystąpień **SocketPermission** Akceptuj oznacza, że aplikacja może akceptować połączenia przychodzące na lokalnym adresie transportu; Łączenie oznacza, że aplikacja może połączyć się z niektórym (lub lokalnym) adresem transportowym.</span><span class="sxs-lookup"><span data-stu-id="51597-112">For **SocketPermission** instances, accept means that an application can accept incoming connections on a local transport address; connect means that an application can connect to some remote (or local) transport address.</span></span>  
  
 <span data-ttu-id="51597-113">W przypadku wystąpień z **uprawnieniami WebPermission** Zaakceptuj oznacza, że aplikacja może eksportować identyfikator URI kontrolowany przez **uprawnienie WebPermission** na świecie; połączenie oznacza, że aplikacja może uzyskać dostęp do tego identyfikatora URI (niezależnie od tego, czy jest to zdalne czy lokalne).</span><span class="sxs-lookup"><span data-stu-id="51597-113">For **WebPermission** instances, accept means that an application can export the URI controlled by the **WebPermission** to the world; connect means that an application can access that URI (whether it is remote or local).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51597-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="51597-114">See also</span></span>

- [<span data-ttu-id="51597-115">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="51597-115">Security</span></span>](../../standard/security/index.md)
- [<span data-ttu-id="51597-116">Zabezpieczenia w programowaniu sieciowym</span><span class="sxs-lookup"><span data-stu-id="51597-116">Security in Network Programming</span></span>](security-in-network-programming.md)
