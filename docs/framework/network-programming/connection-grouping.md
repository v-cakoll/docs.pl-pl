---
title: Grupowanie połączeń
ms.date: 03/30/2017
helpviewer_keywords:
- Internet, connections
- connections [.NET Framework], grouping
- WebRequest class, connection grouping
- network resources, connections
- connection pooling
ms.assetid: 2ec502e8-4ba0-4c22-9410-f28eaf4eee63
ms.openlocfilehash: 28d8771b4535c20a2b65fc8dbbe45407eb041a34
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54658068"
---
# <a name="connection-grouping"></a><span data-ttu-id="a0a89-102">Grupowanie połączeń</span><span class="sxs-lookup"><span data-stu-id="a0a89-102">Connection Grouping</span></span>
<span data-ttu-id="a0a89-103">Grupowanie połączeń kojarzy określonego żądania w ramach jednej aplikacji z pulą określonego połączenia.</span><span class="sxs-lookup"><span data-stu-id="a0a89-103">Connection grouping associates specific requests within a single application to a defined connection pool.</span></span> <span data-ttu-id="a0a89-104">Może to być wymagane przez aplikację warstwy środkowej, nawiązuje połączenie z serwerem zaplecza w imieniu użytkownika, która korzysta z protokołu uwierzytelniania, obsługującym delegowanie, takich jak Kerberos, lub przez aplikację warstwy środkowej, która udostępnia własne poświadczenia, podobnie jak w Poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="a0a89-104">This can be required by a middle-tier application that connects to a back-end server on behalf of a user and uses an authentication protocol that supports delegation, such as Kerberos, or by a middle-tier application that supplies its own credentials, as in the example below.</span></span> <span data-ttu-id="a0a89-105">Na przykład załóżmy, że użytkownik, Jan, odwiedzi wewnętrznej witryny sieci Web, który wyświetla jego informacji o płacach.</span><span class="sxs-lookup"><span data-stu-id="a0a89-105">For example, suppose a user, Joe, visits an internal Web site that displays his payroll information.</span></span> <span data-ttu-id="a0a89-106">Po uwierzytelnieniu Jan, serwera aplikacji warstwy środkowej używa poświadczeń Jana nawiązać połączenia z serwerem zaplecza w celu pobrania jego informacji o płacach.</span><span class="sxs-lookup"><span data-stu-id="a0a89-106">After authenticating Joe, the middle-tier application server uses Joe's credentials to connect to the back-end server to retrieve his payroll information.</span></span> <span data-ttu-id="a0a89-107">Następnie Susan odwiedza witryny i żąda jej informacji o płacach.</span><span class="sxs-lookup"><span data-stu-id="a0a89-107">Next, Susan visits the site and requests her payroll information.</span></span> <span data-ttu-id="a0a89-108">Ponieważ aplikacja warstwy środkowej ma już nawiązaniu połączenia przy użyciu poświadczeń Jana, serwer zaplecza odpowiada Jana informacji.</span><span class="sxs-lookup"><span data-stu-id="a0a89-108">Because the middle-tier application has already made a connection using Joe's credentials, the back-end server responds with Joe's information.</span></span> <span data-ttu-id="a0a89-109">Jeśli jednak aplikacja przypisuje każdego żądania wysyłanego do serwerów zaplecza z grupą połączenia utworzonych na podstawie nazwy użytkownika, następnie każdy użytkownik należy do puli osobnego połączenia i przypadkowo nie można udostępniać informacje o uwierzytelnianiu przy użyciu innego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a0a89-109">However, if the application assigns each request sent to the back-end server to a connection group formed from the user name, then each user belongs to a separate connection pool and cannot accidentally share authentication information with another user.</span></span>  
  
 <span data-ttu-id="a0a89-110">Aby przypisać grupy określone połączenie na żądanie, należy przypisać nazwy do <xref:System.Net.WebRequest.ConnectionGroupName%2A> właściwości usługi <xref:System.Net.WebRequest> przed wykonaniem żądania.</span><span class="sxs-lookup"><span data-stu-id="a0a89-110">To assign a request to a specific connection group, you must assign a name to the <xref:System.Net.WebRequest.ConnectionGroupName%2A> property of your <xref:System.Net.WebRequest> before making the request.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0a89-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a0a89-111">See also</span></span>
- [<span data-ttu-id="a0a89-112">Zarządzanie połączeniami</span><span class="sxs-lookup"><span data-stu-id="a0a89-112">Managing Connections</span></span>](../../../docs/framework/network-programming/managing-connections.md)
- [<span data-ttu-id="a0a89-113">Instrukcje: Przypisywanie informacji użytkownika do połączeń grupowych</span><span class="sxs-lookup"><span data-stu-id="a0a89-113">How to: Assign User Information to Group Connections</span></span>](../../../docs/framework/network-programming/how-to-assign-user-information-to-group-connections.md)
