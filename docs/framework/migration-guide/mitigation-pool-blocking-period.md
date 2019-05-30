---
title: 'Środki zaradcze: Pula czasu blokowania'
ms.date: 03/30/2017
ms.assetid: 92d2de20-79be-4df1-b182-144143a8866a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 01bd548bbafda34202705dda3dda148aae941e2b
ms.sourcegitcommit: 26f4a7697c32978f6a328c89dc4ea87034065989
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/28/2019
ms.locfileid: "66251097"
---
# <a name="mitigation-pool-blocking-period"></a><span data-ttu-id="65326-102">Środki zaradcze: Pula czasu blokowania</span><span class="sxs-lookup"><span data-stu-id="65326-102">Mitigation: Pool Blocking Period</span></span>
<span data-ttu-id="65326-103">Blokuje czasu puli połączeń została usunięta dla połączeń z bazami danych Azure SQL.</span><span class="sxs-lookup"><span data-stu-id="65326-103">The connection pool blocking period has been removed for connections to Azure SQL databases.</span></span>  
  
## <a name="additional-description"></a><span data-ttu-id="65326-104">Dodatkowy opis</span><span class="sxs-lookup"><span data-stu-id="65326-104">Additional description</span></span>  
 <span data-ttu-id="65326-105">W .NET Framework 4.6.1 i wcześniejszymi wersjami, gdy aplikacja napotka błąd przejściowy połączenia podczas nawiązywania połączenia z bazą danych, próba połączenia nie mogą zostać powtórzone szybko, ponieważ pula połączeń buforuje błędu i ponownie zgłasza 5 sekund do 1 min. Aby uzyskać więcej informacji, zobacz [programu SQL Server połączenia puli (ADO.NET)](../../../docs/framework/data/adonet/sql-server-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="65326-105">In the .NET Framework 4.6.1 and earlier versions, when an app encounters a transient connection failure when connecting to a database, the connection attempt cannot be retried quickly, because the connection pool caches the error and re-throws it for 5 seconds to 1 min. For more information, see [SQL Server Connection Pooling (ADO.NET)](../../../docs/framework/data/adonet/sql-server-connection-pooling.md).</span></span> <span data-ttu-id="65326-106">To zachowanie jest problematyczne dla połączeń z bazami danych Azure SQL, które często zakończona niepowodzeniem z błędami przejściowymi, które są zwykle odzyskała sprawność w ciągu kilku sekund.</span><span class="sxs-lookup"><span data-stu-id="65326-106">This behavior is problematic for connections to Azure SQL databases, which often fail with transient errors that are typically recovered from within a few seconds.</span></span> <span data-ttu-id="65326-107">Funkcji blokowania w puli połączeń oznacza, że aplikacji nie można połączyć z bazą danych na okres rozbudowane nawet, jeśli baza danych jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="65326-107">The connection pool blocking feature means that the app cannot connect to the database for an extensive period, even though the database is available.</span></span> <span data-ttu-id="65326-108">To zachowanie jest szczególnie problematyczny dla aplikacji sieci web, które łączą się z bazy danych Azure SQL, które muszą renderowania w ciągu kilku sekund.</span><span class="sxs-lookup"><span data-stu-id="65326-108">This behavior is particularly problematic for web apps that connect to Azure SQL databases and that need to render within a few seconds.</span></span>  
  
 <span data-ttu-id="65326-109">Począwszy od programu .NET Framework 4.6.2 dla połączenia Otwórz żądania do znanych baz danych Azure SQL (\*. database.windows.net, \*. database.chinacloudapi.cn, \*. database.usgovcloudapi.net, \*. database.cloudapi.de ), otwórz błędy połączenia nie są buforowane.</span><span class="sxs-lookup"><span data-stu-id="65326-109">Starting with the .NET Framework 4.6.2, for connection open requests to known Azure SQL databases (\*.database.windows.net, \*.database.chinacloudapi.cn, \*.database.usgovcloudapi.net, \*.database.cloudapi.de), connection open errors are not cached.</span></span> <span data-ttu-id="65326-110">Dla wszystkich innych próby nawiązania połączenia połączenia puli czasu blokowania w dalszym ciągu wymuszane.</span><span class="sxs-lookup"><span data-stu-id="65326-110">For all other connection attempts, the connection pool blocking period continues to be enforced.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="65326-111">Wpływ</span><span class="sxs-lookup"><span data-stu-id="65326-111">Impact</span></span>  
 <span data-ttu-id="65326-112">Próba otwarcia połączenia należy natychmiast ponowić baz danych Azure SQL, a więc poprawa wydajności aplikacji z obsługą chmury dzięki tej zmianie.</span><span class="sxs-lookup"><span data-stu-id="65326-112">This change allows the connection open attempt to be retried immediately for Azure SQL databases, thereby improving the performance of cloud-enabled apps.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="65326-113">Ograniczenie</span><span class="sxs-lookup"><span data-stu-id="65326-113">Mitigation</span></span>  
 <span data-ttu-id="65326-114">Połączenia czasu blokowania puli aplikacji, które niekorzystny wpływ na tę zmianę, można skonfigurować, ustawiając nową <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="65326-114">For apps that are adversely affected by this change, the connection pool blocking period can be configured by setting the new <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A?displayProperty=nameWithType> property.</span></span>  <span data-ttu-id="65326-115">Wartość właściwości jest elementem członkowskim <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType> wyliczenia, która może przyjąć jedną z trzech wartości:</span><span class="sxs-lookup"><span data-stu-id="65326-115">The value of the property is a member of the <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType> enumeration that can take either of three values:</span></span>  
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.Auto?displayProperty=nameWithType>
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock?displayProperty=nameWithType>
  
 <span data-ttu-id="65326-116">Można przywrócić poprzednie zachowanie przez ustawienie <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> właściwość <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="65326-116">The previous behavior can be restored by setting the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> property to <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65326-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="65326-117">See also</span></span>

- [<span data-ttu-id="65326-118">Zmiany środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="65326-118">Runtime Changes</span></span>](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6-2.md)
