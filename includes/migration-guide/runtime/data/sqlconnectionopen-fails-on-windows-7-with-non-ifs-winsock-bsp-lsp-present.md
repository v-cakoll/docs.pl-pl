---
ms.openlocfilehash: a1db9916c69c5974191eb6108fb54a0d9ff060d2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622136"
---
### <a name="sqlconnectionopen-fails-on-windows-7-with-non-ifs-winsock-bsp-or-lsp-present"></a><span data-ttu-id="11689-101">Element SqlConnection. Open kończy się niepowodzeniem w systemie Windows 7 z obecnym zestawu Winsock lub LSP</span><span class="sxs-lookup"><span data-stu-id="11689-101">SqlConnection.Open fails on Windows 7 with non-IFS Winsock BSP or LSP present</span></span>

#### <a name="details"></a><span data-ttu-id="11689-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="11689-102">Details</span></span>

<span data-ttu-id="11689-103"><xref:System.Data.SqlClient.SqlConnection.Open>i <xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)> Niepowodzenie w .NET Framework 4,5 w przypadku uruchamiania na komputerze z systemem Windows 7, na którym znajdują się na nim zestawu Winsock Aby określić, czy zainstalowano program zestawu Winsock lub LSP, użyj <code>netsh WinSock Show Catalog</code> polecenia i sprawdź każdy <code>Winsock Catalog Provider Entry</code> zwracany element.</span><span class="sxs-lookup"><span data-stu-id="11689-103"><xref:System.Data.SqlClient.SqlConnection.Open> and <xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)> fail in the .NET Framework 4.5 if running on a Windows 7 machine with a non-IFS Winsock BSP or LSP are present on the computer.To determine whether a non-IFS BSP or LSP is installed, use the <code>netsh WinSock Show Catalog</code> command, and examine every <code>Winsock Catalog Provider Entry</code> item that is returned.</span></span> <span data-ttu-id="11689-104">Jeśli wartość flag usługi ma <code>0x20000</code> ustawiony bit, Dostawca używa dojść IFS i będzie działał poprawnie.</span><span class="sxs-lookup"><span data-stu-id="11689-104">If the Service Flags value has the <code>0x20000</code> bit set, the provider uses IFS handles and will work correctly.</span></span> <span data-ttu-id="11689-105">Jeśli <code>0x20000</code> bit jest wyczyszczony (nie ustawiono), jest to NIEIFS zestawu Winsock lub LSP.</span><span class="sxs-lookup"><span data-stu-id="11689-105">If the <code>0x20000</code> bit is clear (not set), it is a non-IFS BSP or LSP.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="11689-106">Sugestia</span><span class="sxs-lookup"><span data-stu-id="11689-106">Suggestion</span></span>

<span data-ttu-id="11689-107">Ta usterka została rozwiązana w .NET Framework 4.5.2, dlatego można ją uniknąć, uaktualniając .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="11689-107">This bug has been fixed in the .NET Framework 4.5.2, so it can be avoided by upgrading the .NET Framework.</span></span> <span data-ttu-id="11689-108">Alternatywnie można to uniknąć, usuwając wszystkie zainstalowane Lspy Winsock inne niż IFS.</span><span class="sxs-lookup"><span data-stu-id="11689-108">Alternatively, it can be avoided by removing any installed non-IFS Winsock LSPs.</span></span>

| <span data-ttu-id="11689-109">Nazwa</span><span class="sxs-lookup"><span data-stu-id="11689-109">Name</span></span>    | <span data-ttu-id="11689-110">Wartość</span><span class="sxs-lookup"><span data-stu-id="11689-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="11689-111">Zakres</span><span class="sxs-lookup"><span data-stu-id="11689-111">Scope</span></span>   |<span data-ttu-id="11689-112">Mały</span><span class="sxs-lookup"><span data-stu-id="11689-112">Minor</span></span>|
|<span data-ttu-id="11689-113">Wersja</span><span class="sxs-lookup"><span data-stu-id="11689-113">Version</span></span>|<span data-ttu-id="11689-114">4.5</span><span class="sxs-lookup"><span data-stu-id="11689-114">4.5</span></span>|
|<span data-ttu-id="11689-115">Typ</span><span class="sxs-lookup"><span data-stu-id="11689-115">Type</span></span>|<span data-ttu-id="11689-116">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="11689-116">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="11689-117">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="11689-117">Affected APIs</span></span>

-<xref:System.Data.SqlClient.SqlConnection.Open?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)?displayProperty=nameWithType></li></ul>|
