---
title: Grupowanie połączenia
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
manager: markl
ms.openlocfilehash: bbf34f1e653e95ea30a3e9945fc74c99cfdc3a45
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33395050"
---
# <a name="connection-grouping"></a><span data-ttu-id="55414-102">Grupowanie połączenia</span><span class="sxs-lookup"><span data-stu-id="55414-102">Connection Grouping</span></span>
<span data-ttu-id="55414-103">Grupowanie połączenia kojarzy w jednej aplikacji do puli połączeń zdefiniowanych określonego żądania.</span><span class="sxs-lookup"><span data-stu-id="55414-103">Connection grouping associates specific requests within a single application to a defined connection pool.</span></span> <span data-ttu-id="55414-104">Może to być wymagane przez aplikację warstwy środkowej, nawiązuje połączenie z serwerem zaplecza w imieniu użytkownika, który korzysta z protokołu uwierzytelniania, która obsługuje delegowanie, takie jak Kerberos, lub przez aplikację warstwy środkowej, który udostępnia własne poświadczenia, jak w programie przykład poniżej.</span><span class="sxs-lookup"><span data-stu-id="55414-104">This can be required by a middle-tier application that connects to a back-end server on behalf of a user and uses an authentication protocol that supports delegation, such as Kerberos, or by a middle-tier application that supplies its own credentials, as in the example below.</span></span> <span data-ttu-id="55414-105">Na przykład załóżmy, że użytkownik, Jan, odwiedza wewnętrznej witryny sieci Web, który wyświetla informacje o jego Lista płac.</span><span class="sxs-lookup"><span data-stu-id="55414-105">For example, suppose a user, Joe, visits an internal Web site that displays his payroll information.</span></span> <span data-ttu-id="55414-106">Po uwierzytelnieniu Jan serwera aplikacji w warstwie środkowej służy do łączenia się z serwerem zaplecza można pobrać informacji o jego Lista płac Jana poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="55414-106">After authenticating Joe, the middle-tier application server uses Joe's credentials to connect to the back-end server to retrieve his payroll information.</span></span> <span data-ttu-id="55414-107">Następnie Susan odwiedza witrynę i żąda informacji jej płacowego.</span><span class="sxs-lookup"><span data-stu-id="55414-107">Next, Susan visits the site and requests her payroll information.</span></span> <span data-ttu-id="55414-108">Ponieważ aplikacja warstwy środkowej wykonała już połączenie przy użyciu poświadczeń Jana, serwera zaplecza odpowiada Jana informacje.</span><span class="sxs-lookup"><span data-stu-id="55414-108">Because the middle-tier application has already made a connection using Joe's credentials, the back-end server responds with Joe's information.</span></span> <span data-ttu-id="55414-109">Jednak jeśli aplikacja przypisuje każde żądanie wysłane do serwera zaplecza do grupy połączenia z nazwą użytkownika, następnie każdy użytkownik należy do puli oddzielnego połączenia i przypadkowo nie można udostępniać informacje o uwierzytelnianiu z innym użytkownikiem.</span><span class="sxs-lookup"><span data-stu-id="55414-109">However, if the application assigns each request sent to the back-end server to a connection group formed from the user name, then each user belongs to a separate connection pool and cannot accidentally share authentication information with another user.</span></span>  
  
 <span data-ttu-id="55414-110">Aby przypisać żądania do określonego połączenia grupy, należy przypisać nazwy do <xref:System.Net.WebRequest.ConnectionGroupName%2A> właściwości użytkownika <xref:System.Net.WebRequest> przed wykonaniem żądania.</span><span class="sxs-lookup"><span data-stu-id="55414-110">To assign a request to a specific connection group, you must assign a name to the <xref:System.Net.WebRequest.ConnectionGroupName%2A> property of your <xref:System.Net.WebRequest> before making the request.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55414-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="55414-111">See Also</span></span>  
 [<span data-ttu-id="55414-112">Zarządzanie połączeniami</span><span class="sxs-lookup"><span data-stu-id="55414-112">Managing Connections</span></span>](../../../docs/framework/network-programming/managing-connections.md)  
 [<span data-ttu-id="55414-113">Instrukcje: przypisywanie informacji użytkownika do połączeń grupowych</span><span class="sxs-lookup"><span data-stu-id="55414-113">How to: Assign User Information to Group Connections</span></span>](../../../docs/framework/network-programming/how-to-assign-user-information-to-group-connections.md)
