---
ms.openlocfilehash: 0fe07ac21effacffc56d37ccb46a121f443acd20
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620173"
---
### <a name="sharing-session-state-with-aspnet-stateserver-requires-all-servers-in-the-web-farm-to-use-the-same-net-framework-version"></a><span data-ttu-id="d8bd5-101">Udostępnianie stanu sesji przy użyciu Asp.Net StateServer wymaga, aby wszystkie serwery w kolektywie serwerów sieci Web używały tej samej wersji .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d8bd5-101">Sharing session state with Asp.Net StateServer requires all servers in the web farm to use the same .NET Framework version</span></span>

#### <a name="details"></a><span data-ttu-id="d8bd5-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="d8bd5-102">Details</span></span>

<span data-ttu-id="d8bd5-103">Podczas włączania <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=fullName> stanu sesji wszystkie serwery w danej farmie sieci Web muszą używać tej samej wersji .NET Framework, aby zapewnić prawidłowe udostępnianie stanu.</span><span class="sxs-lookup"><span data-stu-id="d8bd5-103">When enabling <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=fullName> session state, all of the servers in the given web farm must use the same version of the .NET Framework in order for state to be properly shared.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="d8bd5-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="d8bd5-104">Suggestion</span></span>

<span data-ttu-id="d8bd5-105">Pamiętaj, aby uaktualnić .NET Framework wersje na serwerach sieci Web, które udostępniają stan w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="d8bd5-105">Be sure to upgrade .NET Framework versions on web servers that share state at the same time.</span></span>

| <span data-ttu-id="d8bd5-106">Nazwa</span><span class="sxs-lookup"><span data-stu-id="d8bd5-106">Name</span></span>    | <span data-ttu-id="d8bd5-107">Wartość</span><span class="sxs-lookup"><span data-stu-id="d8bd5-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="d8bd5-108">Zakres</span><span class="sxs-lookup"><span data-stu-id="d8bd5-108">Scope</span></span>   |<span data-ttu-id="d8bd5-109">Brzeg</span><span class="sxs-lookup"><span data-stu-id="d8bd5-109">Edge</span></span>|
|<span data-ttu-id="d8bd5-110">Wersja</span><span class="sxs-lookup"><span data-stu-id="d8bd5-110">Version</span></span>|<span data-ttu-id="d8bd5-111">4.5</span><span class="sxs-lookup"><span data-stu-id="d8bd5-111">4.5</span></span>|
|<span data-ttu-id="d8bd5-112">Typ</span><span class="sxs-lookup"><span data-stu-id="d8bd5-112">Type</span></span>|<span data-ttu-id="d8bd5-113">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="d8bd5-113">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d8bd5-114">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="d8bd5-114">Affected APIs</span></span>

-<xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=nameWithType></li></ul>|
