---
ms.openlocfilehash: 3e8601ba76dfb05e3d70b3af7440bd7e228768d0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621169"
---
### <a name="allow-unicode-in-uris-that-resemble-unc-shares"></a><span data-ttu-id="9a301-101">Zezwalaj na kodowanie Unicode w identyfikatorach URI, które przypominają udziały UNC</span><span class="sxs-lookup"><span data-stu-id="9a301-101">Allow Unicode in URIs that resemble UNC shares</span></span>

#### <a name="details"></a><span data-ttu-id="9a301-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="9a301-102">Details</span></span>

<span data-ttu-id="9a301-103">W programie <xref:System.Uri?displayProperty=fullName> konstruowanie identyfikatora URI pliku zawierającego zarówno nazwę udziału UNC, jak i znaki Unicode nie spowoduje już wystąpienia identyfikatora URI z nieprawidłowym stanem wewnętrznym.</span><span class="sxs-lookup"><span data-stu-id="9a301-103">In <xref:System.Uri?displayProperty=fullName>, constructing a file URI containing both a UNC share name and Unicode characters will no longer result in a URI with invalid internal state.</span></span> <span data-ttu-id="9a301-104">Zachowanie zmieni się tylko wtedy, gdy spełnione są wszystkie następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="9a301-104">The behavior will change only when all of the following are true:</span></span><ul><li><span data-ttu-id="9a301-105">Identyfikator URI ma schemat <code>file:</code> i ma cztery lub więcej ukośników.</span><span class="sxs-lookup"><span data-stu-id="9a301-105">The URI has the scheme <code>file:</code> and is followed by four or more slashes.</span></span></li><li><span data-ttu-id="9a301-106">Nazwa hosta zaczyna się od znaku podkreślenia lub innego niezastrzeżonego symbolu.</span><span class="sxs-lookup"><span data-stu-id="9a301-106">The host name begins with an underscore or other non-reserved symbol.</span></span></li><li><span data-ttu-id="9a301-107">Identyfikator URI zawiera znaki Unicode.</span><span class="sxs-lookup"><span data-stu-id="9a301-107">The URI contains Unicode characters.</span></span></li></ul>

#### <a name="suggestion"></a><span data-ttu-id="9a301-108">Sugestia</span><span class="sxs-lookup"><span data-stu-id="9a301-108">Suggestion</span></span>

<span data-ttu-id="9a301-109">Aplikacje korzystające z identyfikatorów URI spójnie zawierające kod Unicode mogą korzystać z tego zachowania, aby nie zezwalać na odwołania do udziałów UNC.</span><span class="sxs-lookup"><span data-stu-id="9a301-109">Applications working with URIs consistently containing Unicode could have conceivably used this behavior to disallow references to UNC shares.</span></span> <span data-ttu-id="9a301-110">Aplikacje te powinny być używane w <xref:System.Uri.IsUnc> zamian.</span><span class="sxs-lookup"><span data-stu-id="9a301-110">Those applications should use <xref:System.Uri.IsUnc> instead.</span></span>

| <span data-ttu-id="9a301-111">Nazwa</span><span class="sxs-lookup"><span data-stu-id="9a301-111">Name</span></span>    | <span data-ttu-id="9a301-112">Wartość</span><span class="sxs-lookup"><span data-stu-id="9a301-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="9a301-113">Zakres</span><span class="sxs-lookup"><span data-stu-id="9a301-113">Scope</span></span>   |<span data-ttu-id="9a301-114">Brzeg</span><span class="sxs-lookup"><span data-stu-id="9a301-114">Edge</span></span>|
|<span data-ttu-id="9a301-115">Wersja</span><span class="sxs-lookup"><span data-stu-id="9a301-115">Version</span></span>|<span data-ttu-id="9a301-116">4.7.2</span><span class="sxs-lookup"><span data-stu-id="9a301-116">4.7.2</span></span>|
|<span data-ttu-id="9a301-117">Typ</span><span class="sxs-lookup"><span data-stu-id="9a301-117">Type</span></span>|<span data-ttu-id="9a301-118">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="9a301-118">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9a301-119">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="9a301-119">Affected APIs</span></span>

-<xref:System.Uri?displayProperty=nameWithType></li></ul>|
