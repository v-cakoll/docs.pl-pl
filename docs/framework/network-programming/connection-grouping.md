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
ms.openlocfilehash: 007366764a7b8e1208e22ef5895e6a9093b090e4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048644"
---
# <a name="connection-grouping"></a><span data-ttu-id="e8d23-102">Grupowanie połączeń</span><span class="sxs-lookup"><span data-stu-id="e8d23-102">Connection Grouping</span></span>
<span data-ttu-id="e8d23-103">Grupowanie połączeń kojarzy określone żądania w ramach jednej aplikacji ze zdefiniowaną pulą połączeń.</span><span class="sxs-lookup"><span data-stu-id="e8d23-103">Connection grouping associates specific requests within a single application to a defined connection pool.</span></span> <span data-ttu-id="e8d23-104">Może to być wymagane przez aplikację warstwy środkowej, która łączy się z serwerem zaplecza w imieniu użytkownika i używa protokołu uwierzytelniania obsługującego delegowanie, takiego jak Kerberos, lub przez aplikację warstwy środkowej, która dostarcza własne poświadczenia, tak jak w przykład poniżej.</span><span class="sxs-lookup"><span data-stu-id="e8d23-104">This can be required by a middle-tier application that connects to a back-end server on behalf of a user and uses an authentication protocol that supports delegation, such as Kerberos, or by a middle-tier application that supplies its own credentials, as in the example below.</span></span> <span data-ttu-id="e8d23-105">Załóżmy na przykład, że użytkownik Joe odwiedza wewnętrzną witrynę sieci Web, która wyświetla jego informacje o liście płac.</span><span class="sxs-lookup"><span data-stu-id="e8d23-105">For example, suppose a user, Joe, visits an internal Web site that displays his payroll information.</span></span> <span data-ttu-id="e8d23-106">Po uwierzytelnieniu Joe, serwer aplikacji warstwy środkowej używa poświadczeń Joe do łączenia się z serwerem zaplecza, aby pobrać jego informacje o liście płac.</span><span class="sxs-lookup"><span data-stu-id="e8d23-106">After authenticating Joe, the middle-tier application server uses Joe's credentials to connect to the back-end server to retrieve his payroll information.</span></span> <span data-ttu-id="e8d23-107">Następnie Susan odwiedza witrynę i żąda informacji o płacach.</span><span class="sxs-lookup"><span data-stu-id="e8d23-107">Next, Susan visits the site and requests her payroll information.</span></span> <span data-ttu-id="e8d23-108">Ponieważ aplikacja warstwy środkowej już nawiązało połączenie przy użyciu poświadczeń Joe, serwer zaplecza odpowiada informacjami Joe.</span><span class="sxs-lookup"><span data-stu-id="e8d23-108">Because the middle-tier application has already made a connection using Joe's credentials, the back-end server responds with Joe's information.</span></span> <span data-ttu-id="e8d23-109">Jeśli jednak aplikacja przypisuje każde żądanie wysłane do serwera zaplecza do grupy połączeń utworzonej z nazwy użytkownika, każdy użytkownik należy do oddzielnej puli połączeń i nie może przypadkowo udostępnić informacji uwierzytelniania innemu użytkownikowi.</span><span class="sxs-lookup"><span data-stu-id="e8d23-109">However, if the application assigns each request sent to the back-end server to a connection group formed from the user name, then each user belongs to a separate connection pool and cannot accidentally share authentication information with another user.</span></span>  
  
 <span data-ttu-id="e8d23-110">Aby przypisać żądanie do określonej grupy połączeń, należy <xref:System.Net.WebRequest.ConnectionGroupName%2A> przypisać <xref:System.Net.WebRequest> nazwę do właściwości przed złożeniem żądania.</span><span class="sxs-lookup"><span data-stu-id="e8d23-110">To assign a request to a specific connection group, you must assign a name to the <xref:System.Net.WebRequest.ConnectionGroupName%2A> property of your <xref:System.Net.WebRequest> before making the request.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8d23-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e8d23-111">See also</span></span>

- [<span data-ttu-id="e8d23-112">Zarządzanie połączeniami</span><span class="sxs-lookup"><span data-stu-id="e8d23-112">Managing Connections</span></span>](managing-connections.md)
- [<span data-ttu-id="e8d23-113">Instrukcje: przypisywanie informacji użytkownika do połączeń grupowych</span><span class="sxs-lookup"><span data-stu-id="e8d23-113">How to: Assign User Information to Group Connections</span></span>](how-to-assign-user-information-to-group-connections.md)
