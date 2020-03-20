---
ms.openlocfilehash: 2278d82d5362fe217ca4bce02a052d4b440843c2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803232"
---
### <a name="aspnet-mvc-now-escapes-spaces-in-strings-passed-in-via-route-parameters"></a><span data-ttu-id="41da2-101">ASP.NET MVC teraz ucieka przestrzenie w ciągach przekazywane za pośrednictwem parametrów trasy</span><span class="sxs-lookup"><span data-stu-id="41da2-101">ASP.NET MVC now escapes spaces in strings passed in via route parameters</span></span>

|   |   |
|---|---|
|<span data-ttu-id="41da2-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="41da2-102">Details</span></span>|<span data-ttu-id="41da2-103">Aby zapewnić zgodność z rfc 2396, miejsca w ścieżkach trasy są teraz wysuwają się podczas wypełniania parametrów akcji z trasy.</span><span class="sxs-lookup"><span data-stu-id="41da2-103">In order to conform to RFC 2396, spaces in route paths are now escaped when populating action parameters from a route.</span></span> <span data-ttu-id="41da2-104">Tak, podczas <code>/controller/action/some data</code> gdy wcześniej dopasować <code>/controller/action/{data}</code> <code>some data</code> trasę i podać jako parametr <code>some%20data</code> danych, będzie teraz zapewnić zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="41da2-104">So, whereas  <code>/controller/action/some data</code> would previously match the route <code>/controller/action/{data}</code> and provide <code>some data</code> as the data parameter, it will now provide <code>some%20data</code> instead.</span></span>|
|<span data-ttu-id="41da2-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="41da2-105">Suggestion</span></span>|<span data-ttu-id="41da2-106">Kod powinien zostać zaktualizowany do parametrów ciągu unescape z trasy.</span><span class="sxs-lookup"><span data-stu-id="41da2-106">Code should be updated to unescape string parameters from a route.</span></span> <span data-ttu-id="41da2-107">Jeśli wymagany jest oryginalny identyfikator URI, można <xref:System.Net.HttpWebRequest.RequestUri>uzyskać do niego dostęp za pomocą pliku . Interfejs API originalstring.</span><span class="sxs-lookup"><span data-stu-id="41da2-107">If the original URI is needed, it can be accessed with the <xref:System.Net.HttpWebRequest.RequestUri>.OriginalString API.</span></span>|
|<span data-ttu-id="41da2-108">Zakres</span><span class="sxs-lookup"><span data-stu-id="41da2-108">Scope</span></span>|<span data-ttu-id="41da2-109">Mały</span><span class="sxs-lookup"><span data-stu-id="41da2-109">Minor</span></span>|
|<span data-ttu-id="41da2-110">Wersja</span><span class="sxs-lookup"><span data-stu-id="41da2-110">Version</span></span>|<span data-ttu-id="41da2-111">4.5.2</span><span class="sxs-lookup"><span data-stu-id="41da2-111">4.5.2</span></span>|
|<span data-ttu-id="41da2-112">Typ</span><span class="sxs-lookup"><span data-stu-id="41da2-112">Type</span></span>|<span data-ttu-id="41da2-113">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="41da2-113">Runtime</span></span>|
|<span data-ttu-id="41da2-114">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="41da2-114">Affected APIs</span></span>|<ul><li><xref:System.Web.Mvc.RouteAttribute.%23ctor(System.String)?displayProperty=nameWithType></li></ul>|
