---
ms.openlocfilehash: 958a89015420ce5632d596688963d576c40b4cb6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59981630"
---
### <a name="sharing-session-state-with-aspnet-stateserver-requires-all-servers-in-the-web-farm-to-use-the-same-net-framework-version"></a><span data-ttu-id="29a03-101">Udostępnianie stanu sesji Asp.Net StateServer wymaga wszystkie serwery w farmie sieci web, aby użyć tej samej wersji .NET Framework</span><span class="sxs-lookup"><span data-stu-id="29a03-101">Sharing session state with Asp.Net StateServer requires all servers in the web farm to use the same .NET Framework version</span></span>

|   |   |
|---|---|
|<span data-ttu-id="29a03-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="29a03-102">Details</span></span>|<span data-ttu-id="29a03-103">Podczas włączania <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=name> stanu sesji, wszystkie serwery w farmie internetowej danego musi być tę samą wersję programu .NET Framework w kolejności stanu zostać prawidłowo udostępnione.</span><span class="sxs-lookup"><span data-stu-id="29a03-103">When enabling <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=name> session state, all of the servers in the given web farm must use the same version of the .NET Framework in order for state to be properly shared.</span></span>|
|<span data-ttu-id="29a03-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="29a03-104">Suggestion</span></span>|<span data-ttu-id="29a03-105">Pamiętaj uaktualnić wersje programu .NET Framework na serwerach sieci web, które udostępnianie stanu w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="29a03-105">Be sure to upgrade .NET Framework versions on web servers that share state at the same time.</span></span>|
|<span data-ttu-id="29a03-106">Zakres</span><span class="sxs-lookup"><span data-stu-id="29a03-106">Scope</span></span>|<span data-ttu-id="29a03-107">Krawędź</span><span class="sxs-lookup"><span data-stu-id="29a03-107">Edge</span></span>|
|<span data-ttu-id="29a03-108">Wersja</span><span class="sxs-lookup"><span data-stu-id="29a03-108">Version</span></span>|<span data-ttu-id="29a03-109">4.5</span><span class="sxs-lookup"><span data-stu-id="29a03-109">4.5</span></span>|
|<span data-ttu-id="29a03-110">Typ</span><span class="sxs-lookup"><span data-stu-id="29a03-110">Type</span></span>|<span data-ttu-id="29a03-111">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="29a03-111">Runtime</span></span>|
|<span data-ttu-id="29a03-112">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="29a03-112">Affected APIs</span></span>|<ul><li><xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=nameWithType></li></ul>|
