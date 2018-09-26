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
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 5d7a13172c32d7ae47cbe290587ff7620e6060da
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47084748"
---
# <a name="connection-grouping"></a><span data-ttu-id="488f6-102">Grupowanie połączeń</span><span class="sxs-lookup"><span data-stu-id="488f6-102">Connection Grouping</span></span>
<span data-ttu-id="488f6-103">Grupowanie połączeń kojarzy określonego żądania w ramach jednej aplikacji z pulą określonego połączenia.</span><span class="sxs-lookup"><span data-stu-id="488f6-103">Connection grouping associates specific requests within a single application to a defined connection pool.</span></span> <span data-ttu-id="488f6-104">Może to być wymagane przez aplikację warstwy środkowej, nawiązuje połączenie z serwerem zaplecza w imieniu użytkownika, która korzysta z protokołu uwierzytelniania, obsługującym delegowanie, takich jak Kerberos, lub przez aplikację warstwy środkowej, która udostępnia własne poświadczenia, podobnie jak w Poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="488f6-104">This can be required by a middle-tier application that connects to a back-end server on behalf of a user and uses an authentication protocol that supports delegation, such as Kerberos, or by a middle-tier application that supplies its own credentials, as in the example below.</span></span> <span data-ttu-id="488f6-105">Na przykład załóżmy, że użytkownik, Jan, odwiedzi wewnętrznej witryny sieci Web, który wyświetla jego informacji o płacach.</span><span class="sxs-lookup"><span data-stu-id="488f6-105">For example, suppose a user, Joe, visits an internal Web site that displays his payroll information.</span></span> <span data-ttu-id="488f6-106">Po uwierzytelnieniu Jan, serwera aplikacji warstwy środkowej używa poświadczeń Jana nawiązać połączenia z serwerem zaplecza w celu pobrania jego informacji o płacach.</span><span class="sxs-lookup"><span data-stu-id="488f6-106">After authenticating Joe, the middle-tier application server uses Joe's credentials to connect to the back-end server to retrieve his payroll information.</span></span> <span data-ttu-id="488f6-107">Następnie Susan odwiedza witryny i żąda jej informacji o płacach.</span><span class="sxs-lookup"><span data-stu-id="488f6-107">Next, Susan visits the site and requests her payroll information.</span></span> <span data-ttu-id="488f6-108">Ponieważ aplikacja warstwy środkowej ma już nawiązaniu połączenia przy użyciu poświadczeń Jana, serwer zaplecza odpowiada Jana informacji.</span><span class="sxs-lookup"><span data-stu-id="488f6-108">Because the middle-tier application has already made a connection using Joe's credentials, the back-end server responds with Joe's information.</span></span> <span data-ttu-id="488f6-109">Jeśli jednak aplikacja przypisuje każdego żądania wysyłanego do serwerów zaplecza z grupą połączenia utworzonych na podstawie nazwy użytkownika, następnie każdy użytkownik należy do puli osobnego połączenia i przypadkowo nie można udostępniać informacje o uwierzytelnianiu przy użyciu innego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="488f6-109">However, if the application assigns each request sent to the back-end server to a connection group formed from the user name, then each user belongs to a separate connection pool and cannot accidentally share authentication information with another user.</span></span>  
  
 <span data-ttu-id="488f6-110">Aby przypisać grupy określone połączenie na żądanie, należy przypisać nazwy do <xref:System.Net.WebRequest.ConnectionGroupName%2A> właściwości usługi <xref:System.Net.WebRequest> przed wykonaniem żądania.</span><span class="sxs-lookup"><span data-stu-id="488f6-110">To assign a request to a specific connection group, you must assign a name to the <xref:System.Net.WebRequest.ConnectionGroupName%2A> property of your <xref:System.Net.WebRequest> before making the request.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="488f6-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="488f6-111">See Also</span></span>  
 [<span data-ttu-id="488f6-112">Zarządzanie połączeniami</span><span class="sxs-lookup"><span data-stu-id="488f6-112">Managing Connections</span></span>](../../../docs/framework/network-programming/managing-connections.md)  
 [<span data-ttu-id="488f6-113">Instrukcje: przypisywanie informacji użytkownika do połączeń grupowych</span><span class="sxs-lookup"><span data-stu-id="488f6-113">How to: Assign User Information to Group Connections</span></span>](../../../docs/framework/network-programming/how-to-assign-user-information-to-group-connections.md)
