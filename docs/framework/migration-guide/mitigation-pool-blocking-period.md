---
title: 'Środki zaradcze: Okres blokuje puli'
ms.date: 03/30/2017
ms.assetid: 92d2de20-79be-4df1-b182-144143a8866a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e402ba9cb5de8e85ce6912e2e5b760ef340c2cf4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="mitigation-pool-blocking-period"></a><span data-ttu-id="da34f-102">Środki zaradcze: Okres blokuje puli</span><span class="sxs-lookup"><span data-stu-id="da34f-102">Mitigation: Pool Blocking Period</span></span>
<span data-ttu-id="da34f-103">Blokowanie czasu puli połączeń zostało usunięte dla połączeń z bazami danych Azure SQL.</span><span class="sxs-lookup"><span data-stu-id="da34f-103">The connection pool blocking period has been removed for connections to Azure SQL databases.</span></span>  
  
## <a name="additional-description"></a><span data-ttu-id="da34f-104">Dodatkowy opis</span><span class="sxs-lookup"><span data-stu-id="da34f-104">Additional description</span></span>  
 <span data-ttu-id="da34f-105">W [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] i starszych wersjach, gdy aplikacja napotka błąd przejściowy połączenia podczas nawiązywania połączenia z bazą danych, próba połączenia nie może zostać powtórzone szybko, ponieważ puli połączeń buforuje błędu i ponownie zgłasza wyjątek 5 sekund na 1 min. Aby uzyskać więcej informacji, zobacz [programu SQL Server połączenia buforowanie (ADO.NET)](../../../docs/framework/data/adonet/sql-server-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="da34f-105">In the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] and earlier versions, when an app encounters a transient connection failure when connecting to a database, the connection attempt cannot be retried quickly, because the connection pool caches the error and re-throws it for 5 seconds to 1 min. For more information, see [SQL Server Connection Pooling (ADO.NET)](../../../docs/framework/data/adonet/sql-server-connection-pooling.md).</span></span> <span data-ttu-id="da34f-106">To zachowanie jest powodować problemy dla połączeń z bazami danych Azure SQL, które często nie przejściowych błędów, które są zazwyczaj odzyskała sprawność działania po w ciągu kilku sekund.</span><span class="sxs-lookup"><span data-stu-id="da34f-106">This behavior is problematic for connections to Azure SQL databases, which often fail with transient errors that are typically recovered from within a few seconds.</span></span> <span data-ttu-id="da34f-107">Funkcja blokowania puli połączeń oznacza, że aplikacji nie można połączyć z bazą danych na okres szeroką gamę nawet, jeśli baza danych jest dostępne.</span><span class="sxs-lookup"><span data-stu-id="da34f-107">The connection pool blocking feature means that the app cannot connect to the database for an extensive period, even though the database is available.</span></span> <span data-ttu-id="da34f-108">To zachowanie jest szczególnie powodować problemy dla aplikacji sieci web, który nawiązać połączenie bazy danych Azure SQL i który należy do renderowania w ciągu kilku sekund.</span><span class="sxs-lookup"><span data-stu-id="da34f-108">This behavior is particularly problematic for web apps that connect to Azure SQL databases and that need to render within a few seconds.</span></span>  
  
 <span data-ttu-id="da34f-109">Począwszy od [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]dla połączenie jest otwarte żądania do znanego baz danych Azure SQL (*. database.windows.net, \*. database.chinacloudapi.cn, \*. database.usgovcloudapi.net, \*. database.cloudapi.de), Otwórz błędów połączenia nie są buforowane.</span><span class="sxs-lookup"><span data-stu-id="da34f-109">Starting with the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], for connection open requests to known Azure SQL databases (*.database.windows.net, \*.database.chinacloudapi.cn, \*.database.usgovcloudapi.net, \*.database.cloudapi.de), connection open errors are not cached.</span></span> <span data-ttu-id="da34f-110">Dla wszystkich innych prób połączenia połączenia czasu blokowania puli nadal mają być egzekwowane.</span><span class="sxs-lookup"><span data-stu-id="da34f-110">For all other connection attempts, the connection pool blocking period continues to be enforced.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="da34f-111">Wpływ</span><span class="sxs-lookup"><span data-stu-id="da34f-111">Impact</span></span>  
 <span data-ttu-id="da34f-112">Ta zmiana umożliwia Otwórz próba ponowienia natychmiast baz danych Azure SQL, zwiększając wydajność aplikacji z włączoną obsługą chmury.</span><span class="sxs-lookup"><span data-stu-id="da34f-112">This change allows the connection open attempt to be retried immediately for Azure SQL databases, thereby improving the performance of cloud-enabled apps.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="da34f-113">Ograniczenie</span><span class="sxs-lookup"><span data-stu-id="da34f-113">Mitigation</span></span>  
 <span data-ttu-id="da34f-114">Połączenia czasu blokowania puli aplikacji, które niekorzystny wpływ na tę zmianę, można skonfigurować przez ustawienie nowego <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="da34f-114">For apps that are adversely affected by this change, the connection pool blocking period can be configured by setting the new <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> property.</span></span>  <span data-ttu-id="da34f-115">Wartość właściwości jest elementem członkowskim <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType> wyliczenia, który może przybrać jedną z trzech wartości:</span><span class="sxs-lookup"><span data-stu-id="da34f-115">The value of the property is a member of the <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType> enumeration that can take either of three values:</span></span>  
  
-   `PoolBlockingPeriod.AlwaysBlock` 
  
-   `PoolBlockingPeriod.Auto`  
  
-   `PoolBlockingPeriod.NeverBlock` 
  
 <span data-ttu-id="da34f-116">Poprzednie mogą zostać przywrócone przez ustawienie <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> właściwości `PoolBlockingPeriod.AlwaysBlock`.</span><span class="sxs-lookup"><span data-stu-id="da34f-116">The previous behavior can be restored by setting the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> property to `PoolBlockingPeriod.AlwaysBlock`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da34f-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="da34f-117">See Also</span></span>  
 [<span data-ttu-id="da34f-118">Zmiany środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="da34f-118">Runtime Changes</span></span>](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6-2.md)
