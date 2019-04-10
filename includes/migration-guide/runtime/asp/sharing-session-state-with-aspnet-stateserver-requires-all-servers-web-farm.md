---
ms.openlocfilehash: 958a89015420ce5632d596688963d576c40b4cb6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235581"
---
### <a name="sharing-session-state-with-aspnet-stateserver-requires-all-servers-in-the-web-farm-to-use-the-same-net-framework-version"></a><span data-ttu-id="56bb1-101">Udostępnianie stanu sesji Asp.Net StateServer wymaga wszystkie serwery w farmie sieci web, aby użyć tej samej wersji .NET Framework</span><span class="sxs-lookup"><span data-stu-id="56bb1-101">Sharing session state with Asp.Net StateServer requires all servers in the web farm to use the same .NET Framework version</span></span>

|   |   |
|---|---|
|<span data-ttu-id="56bb1-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="56bb1-102">Details</span></span>|<span data-ttu-id="56bb1-103">Podczas włączania <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=name> stanu sesji, wszystkie serwery w farmie internetowej danego musi być tę samą wersję programu .NET Framework w kolejności stanu zostać prawidłowo udostępnione.</span><span class="sxs-lookup"><span data-stu-id="56bb1-103">When enabling <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=name> session state, all of the servers in the given web farm must use the same version of the .NET Framework in order for state to be properly shared.</span></span>|
|<span data-ttu-id="56bb1-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="56bb1-104">Suggestion</span></span>|<span data-ttu-id="56bb1-105">Pamiętaj uaktualnić wersje programu .NET Framework na serwerach sieci web, które udostępnianie stanu w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="56bb1-105">Be sure to upgrade .NET Framework versions on web servers that share state at the same time.</span></span>|
|<span data-ttu-id="56bb1-106">Zakres</span><span class="sxs-lookup"><span data-stu-id="56bb1-106">Scope</span></span>|<span data-ttu-id="56bb1-107">Krawędź</span><span class="sxs-lookup"><span data-stu-id="56bb1-107">Edge</span></span>|
|<span data-ttu-id="56bb1-108">Wersja</span><span class="sxs-lookup"><span data-stu-id="56bb1-108">Version</span></span>|<span data-ttu-id="56bb1-109">4.5</span><span class="sxs-lookup"><span data-stu-id="56bb1-109">4.5</span></span>|
|<span data-ttu-id="56bb1-110">Typ</span><span class="sxs-lookup"><span data-stu-id="56bb1-110">Type</span></span>|<span data-ttu-id="56bb1-111">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="56bb1-111">Runtime</span></span>|
|<span data-ttu-id="56bb1-112">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="56bb1-112">Affected APIs</span></span>|<ul><li><xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=nameWithType></li></ul>|
