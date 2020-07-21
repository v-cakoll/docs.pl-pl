---
title: 'Środki zaradcze: okres blokowania puli'
description: Dowiedz się, jak uniknąć problemów spowodowanych przez okres blokowania puli połączeń, który jest usuwany dla połączeń z bazami danych Azure SQL.
ms.date: 03/30/2017
ms.assetid: 92d2de20-79be-4df1-b182-144143a8866a
ms.openlocfilehash: be60fe87952697d964571176743a4e6f839c4894
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475414"
---
# <a name="mitigation-pool-blocking-period"></a><span data-ttu-id="194b7-103">Środki zaradcze: okres blokowania puli</span><span class="sxs-lookup"><span data-stu-id="194b7-103">Mitigation: Pool Blocking Period</span></span>
<span data-ttu-id="194b7-104">Okres blokowania puli połączeń został usunięty z połączeń z bazami danych Azure SQL Database.</span><span class="sxs-lookup"><span data-stu-id="194b7-104">The connection pool blocking period has been removed for connections to Azure SQL databases.</span></span>  
  
## <a name="additional-description"></a><span data-ttu-id="194b7-105">Dodatkowy opis</span><span class="sxs-lookup"><span data-stu-id="194b7-105">Additional description</span></span>  
 <span data-ttu-id="194b7-106">W .NET Framework 4.6.1 i starszych wersjach, gdy podczas łączenia się z bazą danych w aplikacji wystąpi przejściowy błąd połączenia, próba połączenia nie może być podejmowana szybko, ponieważ pula połączeń buforuje błąd i ponownie zgłasza go przez 5 sekund do 1 minuty. Aby uzyskać więcej informacji, zobacz [SQL Servering pooling (ADO.NET)](../data/adonet/sql-server-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="194b7-106">In the .NET Framework 4.6.1 and earlier versions, when an app encounters a transient connection failure when connecting to a database, the connection attempt cannot be retried quickly, because the connection pool caches the error and re-throws it for 5 seconds to 1 min. For more information, see [SQL Server Connection Pooling (ADO.NET)](../data/adonet/sql-server-connection-pooling.md).</span></span> <span data-ttu-id="194b7-107">To zachowanie jest przyczyną problemów z połączeniami z bazami danych Azure SQL, co często kończy się niepowodzeniem z błędami przejściowymi, które zwykle są odzyskiwane z ciągu kilku sekund.</span><span class="sxs-lookup"><span data-stu-id="194b7-107">This behavior is problematic for connections to Azure SQL databases, which often fail with transient errors that are typically recovered from within a few seconds.</span></span> <span data-ttu-id="194b7-108">Funkcja blokowania puli połączeń oznacza, że aplikacja nie może połączyć się z bazą danych przez dłuższy czas, nawet jeśli baza danych jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="194b7-108">The connection pool blocking feature means that the app cannot connect to the database for an extensive period, even though the database is available.</span></span> <span data-ttu-id="194b7-109">To zachowanie jest szczególnie problematyczne w przypadku aplikacji sieci Web, które łączą się z bazami danych SQL Azure i które muszą być renderowane w ciągu kilku sekund.</span><span class="sxs-lookup"><span data-stu-id="194b7-109">This behavior is particularly problematic for web apps that connect to Azure SQL databases and that need to render within a few seconds.</span></span>  
  
 <span data-ttu-id="194b7-110">Począwszy od .NET Framework 4.6.2, w przypadku żądań otwartych dla połączenia z znanymi bazami danych Azure SQL Database (\*. database.windows.net, \* . Database.chinacloudapi.CN, \* . Database.usgovcloudapi.NET, \* . Database.cloudapi.de), błędy otwarcia połączenia nie są buforowane.</span><span class="sxs-lookup"><span data-stu-id="194b7-110">Starting with the .NET Framework 4.6.2, for connection open requests to known Azure SQL databases (\*.database.windows.net, \*.database.chinacloudapi.cn, \*.database.usgovcloudapi.net, \*.database.cloudapi.de), connection open errors are not cached.</span></span> <span data-ttu-id="194b7-111">W przypadku wszystkich innych prób połączenia będzie wymuszany okres blokowania puli połączeń.</span><span class="sxs-lookup"><span data-stu-id="194b7-111">For all other connection attempts, the connection pool blocking period continues to be enforced.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="194b7-112">Wpływ</span><span class="sxs-lookup"><span data-stu-id="194b7-112">Impact</span></span>  
 <span data-ttu-id="194b7-113">Ta zmiana umożliwia natychmiastowe ponawianie próby nawiązania połączenia z bazami danych Azure SQL, co poprawia wydajność aplikacji obsługujących chmurę.</span><span class="sxs-lookup"><span data-stu-id="194b7-113">This change allows the connection open attempt to be retried immediately for Azure SQL databases, thereby improving the performance of cloud-enabled apps.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="194b7-114">Ograniczanie ryzyka</span><span class="sxs-lookup"><span data-stu-id="194b7-114">Mitigation</span></span>  
 <span data-ttu-id="194b7-115">W przypadku aplikacji, które mają niekorzystnie wpływać na tę zmianę, można skonfigurować okres blokowania puli połączeń, ustawiając nową <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A?displayProperty=nameWithType> Właściwość.</span><span class="sxs-lookup"><span data-stu-id="194b7-115">For apps that are adversely affected by this change, the connection pool blocking period can be configured by setting the new <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A?displayProperty=nameWithType> property.</span></span>  <span data-ttu-id="194b7-116">Wartość właściwości jest składową <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType> wyliczenia, która może przyjmować jedną z trzech wartości:</span><span class="sxs-lookup"><span data-stu-id="194b7-116">The value of the property is a member of the <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType> enumeration that can take either of three values:</span></span>  
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.Auto?displayProperty=nameWithType>
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock?displayProperty=nameWithType>
  
 <span data-ttu-id="194b7-117">Poprzednie zachowanie można przywrócić, ustawiając <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> Właściwość na <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="194b7-117">The previous behavior can be restored by setting the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> property to <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="194b7-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="194b7-118">See also</span></span>

- [<span data-ttu-id="194b7-119">Zgodność aplikacji</span><span class="sxs-lookup"><span data-stu-id="194b7-119">Application compatibility</span></span>](application-compatibility.md)
