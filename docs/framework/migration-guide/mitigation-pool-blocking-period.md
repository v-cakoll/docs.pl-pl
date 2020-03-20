---
title: 'Łagodzenie: Okres blokowania puli'
ms.date: 03/30/2017
ms.assetid: 92d2de20-79be-4df1-b182-144143a8866a
ms.openlocfilehash: 98396d4254975d1806a8477cbcd2380cb52ceaf3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457847"
---
# <a name="mitigation-pool-blocking-period"></a><span data-ttu-id="c5a43-102">Łagodzenie: Okres blokowania puli</span><span class="sxs-lookup"><span data-stu-id="c5a43-102">Mitigation: Pool Blocking Period</span></span>
<span data-ttu-id="c5a43-103">Okres blokowania puli połączeń został usunięty dla połączeń z bazami danych SQL platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="c5a43-103">The connection pool blocking period has been removed for connections to Azure SQL databases.</span></span>  
  
## <a name="additional-description"></a><span data-ttu-id="c5a43-104">Dodatkowy opis</span><span class="sxs-lookup"><span data-stu-id="c5a43-104">Additional description</span></span>  
 <span data-ttu-id="c5a43-105">W .NET Framework 4.6.1 i wcześniejszych wersjach, gdy aplikacja napotka przejściowy błąd połączenia podczas łączenia się z bazą danych, nie można szybko ponowić próbę połączenia, ponieważ pula połączeń buforuje błąd i ponownie zgłasza go na 5 sekund do 1 min. Aby uzyskać więcej informacji, zobacz [Sql Server Connection Pooling (ADO.NET)](../data/adonet/sql-server-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="c5a43-105">In the .NET Framework 4.6.1 and earlier versions, when an app encounters a transient connection failure when connecting to a database, the connection attempt cannot be retried quickly, because the connection pool caches the error and re-throws it for 5 seconds to 1 min. For more information, see [SQL Server Connection Pooling (ADO.NET)](../data/adonet/sql-server-connection-pooling.md).</span></span> <span data-ttu-id="c5a43-106">To zachowanie jest problematyczne dla połączeń z bazami danych SQL platformy Azure, które często nie z błędami przejściowymi, które są zwykle odzyskane w ciągu kilku sekund.</span><span class="sxs-lookup"><span data-stu-id="c5a43-106">This behavior is problematic for connections to Azure SQL databases, which often fail with transient errors that are typically recovered from within a few seconds.</span></span> <span data-ttu-id="c5a43-107">Funkcja blokowania puli połączeń oznacza, że aplikacja nie może połączyć się z bazą danych przez dłuższy czas, nawet jeśli baza danych jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="c5a43-107">The connection pool blocking feature means that the app cannot connect to the database for an extensive period, even though the database is available.</span></span> <span data-ttu-id="c5a43-108">To zachowanie jest szczególnie problematyczne dla aplikacji sieci web, które łączą się z bazami danych SQL platformy Azure i które muszą być renderowane w ciągu kilku sekund.</span><span class="sxs-lookup"><span data-stu-id="c5a43-108">This behavior is particularly problematic for web apps that connect to Azure SQL databases and that need to render within a few seconds.</span></span>  
  
 <span data-ttu-id="c5a43-109">Począwszy od programu .NET Framework 4.6.2, dla otwartych żądań połączeń do \*znanych baz danych \*SQL platformy Azure \*(\*.database.windows.net, .database.chinacloudapi.cn, .database.usgovcloudapi.net, .database.cloudapi.de), błędy otwierania połączenia nie są buforowane.</span><span class="sxs-lookup"><span data-stu-id="c5a43-109">Starting with the .NET Framework 4.6.2, for connection open requests to known Azure SQL databases (\*.database.windows.net, \*.database.chinacloudapi.cn, \*.database.usgovcloudapi.net, \*.database.cloudapi.de), connection open errors are not cached.</span></span> <span data-ttu-id="c5a43-110">W przypadku wszystkich innych prób połączenia okres blokowania puli połączeń jest nadal wymuszany.</span><span class="sxs-lookup"><span data-stu-id="c5a43-110">For all other connection attempts, the connection pool blocking period continues to be enforced.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="c5a43-111">Wpływ</span><span class="sxs-lookup"><span data-stu-id="c5a43-111">Impact</span></span>  
 <span data-ttu-id="c5a43-112">Ta zmiana umożliwia natychmiastowe ponowienie próby ponownego ponawiania otwartej próby połączenia dla baz danych SQL platformy Azure, co zwiększa wydajność aplikacji z obsługą chmury.</span><span class="sxs-lookup"><span data-stu-id="c5a43-112">This change allows the connection open attempt to be retried immediately for Azure SQL databases, thereby improving the performance of cloud-enabled apps.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="c5a43-113">Środki zaradcze</span><span class="sxs-lookup"><span data-stu-id="c5a43-113">Mitigation</span></span>  
 <span data-ttu-id="c5a43-114">W przypadku aplikacji, na które ta zmiana ma negatywny wpływ, okres blokowania <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A?displayProperty=nameWithType> puli połączeń można skonfigurować, ustawiając nową właściwość.</span><span class="sxs-lookup"><span data-stu-id="c5a43-114">For apps that are adversely affected by this change, the connection pool blocking period can be configured by setting the new <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A?displayProperty=nameWithType> property.</span></span>  <span data-ttu-id="c5a43-115">Wartość właściwości jest członkiem wyliczenia, <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType> które może przyjmować jedną z trzech wartości:</span><span class="sxs-lookup"><span data-stu-id="c5a43-115">The value of the property is a member of the <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType> enumeration that can take either of three values:</span></span>  
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.Auto?displayProperty=nameWithType>
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock?displayProperty=nameWithType>
  
 <span data-ttu-id="c5a43-116">Poprzednie zachowanie można przywrócić, <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> ustawiając <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>właściwość na .</span><span class="sxs-lookup"><span data-stu-id="c5a43-116">The previous behavior can be restored by setting the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> property to <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5a43-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c5a43-117">See also</span></span>

- [<span data-ttu-id="c5a43-118">Zgodność aplikacji</span><span class="sxs-lookup"><span data-stu-id="c5a43-118">Application compatibility</span></span>](application-compatibility.md)
