---
ms.openlocfilehash: 87cb2570d3d47a2acb85b5557141c0fef885516a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621821"
---
### <a name="attempting-a-tcpip-connection-to-a-sql-server-database-that-resolves-to-localhost-fails"></a><span data-ttu-id="1a922-101">Próba połączenia TCP/IP z SQL Server bazą danych, która jest rozpoznawana jako `localhost` Niepowodzenie</span><span class="sxs-lookup"><span data-stu-id="1a922-101">Attempting a TCP/IP connection to a SQL Server database that resolves to `localhost` fails</span></span>

#### <a name="details"></a><span data-ttu-id="1a922-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="1a922-102">Details</span></span>

<span data-ttu-id="1a922-103">W .NET Framework 4,6 i 4.6.1 próbuje nawiązać połączenie TCP/IP z bazą danych SQL Server, która jest rozpoznawana jako <code>localhost</code> błąd, &quot; Wystąpił błąd związany z siecią lub wystąpieniem podczas nawiązywania połączenia z SQL Server.</span><span class="sxs-lookup"><span data-stu-id="1a922-103">In the .NET Framework 4.6 and 4.6.1, attempting a TCP/IP connection to a SQL Server database that resolves to <code>localhost</code> fails with the error, &quot;A network-related or instance-specific error occurred while establishing a connection to SQL Server.</span></span> <span data-ttu-id="1a922-104">Serwer nie został znaleziony lub był niedostępny.</span><span class="sxs-lookup"><span data-stu-id="1a922-104">The server was not found or was not accessible.</span></span> <span data-ttu-id="1a922-105">Sprawdź, czy nazwa wystąpienia jest poprawna i czy SQL Server jest skonfigurowany do zezwalania na połączenia zdalne.</span><span class="sxs-lookup"><span data-stu-id="1a922-105">Verify that the instance name is correct and that SQL Server is configured to allow remote connections.</span></span> <span data-ttu-id="1a922-106">(Dostawca: interfejsy sieciowe SQL, błąd: 26 — błąd lokalizowania określonego serwera/wystąpienia)&quot;</span><span class="sxs-lookup"><span data-stu-id="1a922-106">(provider: SQL Network Interfaces, error: 26 - Error Locating Server/Instance Specified)&quot;</span></span>

#### <a name="suggestion"></a><span data-ttu-id="1a922-107">Sugestia</span><span class="sxs-lookup"><span data-stu-id="1a922-107">Suggestion</span></span>

<span data-ttu-id="1a922-108">Ten problem został rozwiązany i poprzednie zachowanie zostało przywrócone w .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="1a922-108">This issue has been addressed and the previous behavior restored in the .NET Framework 4.6.2.</span></span> <span data-ttu-id="1a922-109">Aby nawiązać połączenie z bazą danych SQL Server, która jest rozpoznawana jako <code>localhost</code> , należy przeprowadzić uaktualnienie do .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="1a922-109">To connect to a SQL Server database that resolves to <code>localhost</code>, upgrade to the .NET Framework 4.6.2.</span></span>

| <span data-ttu-id="1a922-110">Nazwa</span><span class="sxs-lookup"><span data-stu-id="1a922-110">Name</span></span>    | <span data-ttu-id="1a922-111">Wartość</span><span class="sxs-lookup"><span data-stu-id="1a922-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="1a922-112">Zakres</span><span class="sxs-lookup"><span data-stu-id="1a922-112">Scope</span></span>   |<span data-ttu-id="1a922-113">Mały</span><span class="sxs-lookup"><span data-stu-id="1a922-113">Minor</span></span>|
|<span data-ttu-id="1a922-114">Wersja</span><span class="sxs-lookup"><span data-stu-id="1a922-114">Version</span></span>|<span data-ttu-id="1a922-115">4.6</span><span class="sxs-lookup"><span data-stu-id="1a922-115">4.6</span></span>|
|<span data-ttu-id="1a922-116">Typ</span><span class="sxs-lookup"><span data-stu-id="1a922-116">Type</span></span>|<span data-ttu-id="1a922-117">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="1a922-117">Runtime</span></span>|
