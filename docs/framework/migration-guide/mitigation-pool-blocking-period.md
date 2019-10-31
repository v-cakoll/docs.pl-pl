---
title: 'Środki zaradcze: okres blokowania puli'
ms.date: 03/30/2017
ms.assetid: 92d2de20-79be-4df1-b182-144143a8866a
ms.openlocfilehash: b29649be8b52525e1e917d823997521825d56c1b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126172"
---
# <a name="mitigation-pool-blocking-period"></a><span data-ttu-id="333cd-102">Środki zaradcze: okres blokowania puli</span><span class="sxs-lookup"><span data-stu-id="333cd-102">Mitigation: Pool Blocking Period</span></span>
<span data-ttu-id="333cd-103">Okres blokowania puli połączeń został usunięty z połączeń z bazami danych Azure SQL Database.</span><span class="sxs-lookup"><span data-stu-id="333cd-103">The connection pool blocking period has been removed for connections to Azure SQL databases.</span></span>  
  
## <a name="additional-description"></a><span data-ttu-id="333cd-104">Dodatkowy opis</span><span class="sxs-lookup"><span data-stu-id="333cd-104">Additional description</span></span>  
 <span data-ttu-id="333cd-105">W .NET Framework 4.6.1 i starszych wersjach, gdy podczas nawiązywania połączenia z bazą danych wystąpi błąd przejściowy, próba połączenia nie może zostać wznowiona szybko, ponieważ pula połączeń buforuje błąd i ponownie zgłasza go przez 5 sekund do 1 długości. Aby uzyskać więcej informacji, zobacz [SQL Servering pooling (ADO.NET)](../data/adonet/sql-server-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="333cd-105">In the .NET Framework 4.6.1 and earlier versions, when an app encounters a transient connection failure when connecting to a database, the connection attempt cannot be retried quickly, because the connection pool caches the error and re-throws it for 5 seconds to 1 min. For more information, see [SQL Server Connection Pooling (ADO.NET)](../data/adonet/sql-server-connection-pooling.md).</span></span> <span data-ttu-id="333cd-106">To zachowanie jest przyczyną problemów z połączeniami z bazami danych Azure SQL, co często kończy się niepowodzeniem z błędami przejściowymi, które zwykle są odzyskiwane z ciągu kilku sekund.</span><span class="sxs-lookup"><span data-stu-id="333cd-106">This behavior is problematic for connections to Azure SQL databases, which often fail with transient errors that are typically recovered from within a few seconds.</span></span> <span data-ttu-id="333cd-107">Funkcja blokowania puli połączeń oznacza, że aplikacja nie może połączyć się z bazą danych przez dłuższy czas, nawet jeśli baza danych jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="333cd-107">The connection pool blocking feature means that the app cannot connect to the database for an extensive period, even though the database is available.</span></span> <span data-ttu-id="333cd-108">To zachowanie jest szczególnie problematyczne w przypadku aplikacji sieci Web, które łączą się z bazami danych SQL Azure i które muszą być renderowane w ciągu kilku sekund.</span><span class="sxs-lookup"><span data-stu-id="333cd-108">This behavior is particularly problematic for web apps that connect to Azure SQL databases and that need to render within a few seconds.</span></span>  
  
 <span data-ttu-id="333cd-109">Począwszy od .NET Framework 4.6.2, w przypadku żądań otwartych dla połączenia z znanymi bazami danych Azure SQL Database (\*. database.windows.net, \*. database.chinacloudapi.cn, \*. database.usgovcloudapi.net, \*. database.cloudapi.de), połączenie Błędy otwierania nie są buforowane.</span><span class="sxs-lookup"><span data-stu-id="333cd-109">Starting with the .NET Framework 4.6.2, for connection open requests to known Azure SQL databases (\*.database.windows.net, \*.database.chinacloudapi.cn, \*.database.usgovcloudapi.net, \*.database.cloudapi.de), connection open errors are not cached.</span></span> <span data-ttu-id="333cd-110">W przypadku wszystkich innych prób połączenia będzie wymuszany okres blokowania puli połączeń.</span><span class="sxs-lookup"><span data-stu-id="333cd-110">For all other connection attempts, the connection pool blocking period continues to be enforced.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="333cd-111">Wpływ</span><span class="sxs-lookup"><span data-stu-id="333cd-111">Impact</span></span>  
 <span data-ttu-id="333cd-112">Ta zmiana umożliwia natychmiastowe ponawianie próby nawiązania połączenia z bazami danych Azure SQL, co poprawia wydajność aplikacji obsługujących chmurę.</span><span class="sxs-lookup"><span data-stu-id="333cd-112">This change allows the connection open attempt to be retried immediately for Azure SQL databases, thereby improving the performance of cloud-enabled apps.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="333cd-113">Ograniczenie</span><span class="sxs-lookup"><span data-stu-id="333cd-113">Mitigation</span></span>  
 <span data-ttu-id="333cd-114">W przypadku aplikacji, które mają niekorzystnie wpływać na tę zmianę, można skonfigurować okres blokowania puli połączeń, ustawiając nową właściwość <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="333cd-114">For apps that are adversely affected by this change, the connection pool blocking period can be configured by setting the new <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A?displayProperty=nameWithType> property.</span></span>  <span data-ttu-id="333cd-115">Wartość właściwości jest składową wyliczenia <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType>, która może przyjmować jedną z trzech wartości:</span><span class="sxs-lookup"><span data-stu-id="333cd-115">The value of the property is a member of the <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType> enumeration that can take either of three values:</span></span>  
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.Auto?displayProperty=nameWithType>
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock?displayProperty=nameWithType>
  
 <span data-ttu-id="333cd-116">Poprzednie zachowanie można przywrócić, ustawiając właściwość <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> na <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="333cd-116">The previous behavior can be restored by setting the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> property to <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="333cd-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="333cd-117">See also</span></span>

- [<span data-ttu-id="333cd-118">Zmiany środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="333cd-118">Runtime Changes</span></span>](runtime-changes-in-the-net-framework-4-6-2.md)
