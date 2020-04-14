---
ms.openlocfilehash: 7444ddbdd4a7c5f731fba8528ee2334374fc254e
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81275098"
---
### <a name="aspnet-mvc-now-escapes-spaces-in-strings-passed-in-via-route-parameters"></a><span data-ttu-id="23e16-101">ASP.NET MVC teraz ucieka przestrzenie w ciągach przekazywane za pośrednictwem parametrów trasy</span><span class="sxs-lookup"><span data-stu-id="23e16-101">ASP.NET MVC now escapes spaces in strings passed in via route parameters</span></span>

|   |   |
|---|---|
|<span data-ttu-id="23e16-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="23e16-102">Details</span></span>|<span data-ttu-id="23e16-103">Aby zapewnić zgodność z rfc 2396, miejsca w ścieżkach trasy są teraz wysuwają się podczas wypełniania parametrów akcji z trasy.</span><span class="sxs-lookup"><span data-stu-id="23e16-103">In order to conform to RFC 2396, spaces in route paths are now escaped when populating action parameters from a route.</span></span> <span data-ttu-id="23e16-104">Tak, podczas <code>/controller/action/some data</code> gdy wcześniej dopasować <code>/controller/action/{data}</code> <code>some data</code> trasę i podać jako parametr <code>some%20data</code> danych, będzie teraz zapewnić zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="23e16-104">So, whereas  <code>/controller/action/some data</code> would previously match the route <code>/controller/action/{data}</code> and provide <code>some data</code> as the data parameter, it will now provide <code>some%20data</code> instead.</span></span>|
|<span data-ttu-id="23e16-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="23e16-105">Suggestion</span></span>|<span data-ttu-id="23e16-106">Kod powinien zostać zaktualizowany do parametrów ciągu unescape z trasy.</span><span class="sxs-lookup"><span data-stu-id="23e16-106">Code should be updated to unescape string parameters from a route.</span></span> <span data-ttu-id="23e16-107">Jeśli wymagany jest oryginalny identyfikator URI, można <xref:System.Net.HttpWebRequest.RequestUri>uzyskać do niego dostęp za pomocą pliku . Interfejs API originalstring.</span><span class="sxs-lookup"><span data-stu-id="23e16-107">If the original URI is needed, it can be accessed with the <xref:System.Net.HttpWebRequest.RequestUri>.OriginalString API.</span></span>|
|<span data-ttu-id="23e16-108">Zakres</span><span class="sxs-lookup"><span data-stu-id="23e16-108">Scope</span></span>|<span data-ttu-id="23e16-109">Mały</span><span class="sxs-lookup"><span data-stu-id="23e16-109">Minor</span></span>|
|<span data-ttu-id="23e16-110">Wersja</span><span class="sxs-lookup"><span data-stu-id="23e16-110">Version</span></span>|<span data-ttu-id="23e16-111">4.5.2</span><span class="sxs-lookup"><span data-stu-id="23e16-111">4.5.2</span></span>|
|<span data-ttu-id="23e16-112">Typ</span><span class="sxs-lookup"><span data-stu-id="23e16-112">Type</span></span>|<span data-ttu-id="23e16-113">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="23e16-113">Runtime</span></span>|
|<span data-ttu-id="23e16-114">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="23e16-114">Affected APIs</span></span>|<ul><li><xref:System.Web.Mvc.RouteAttribute.%23ctor(System.String)></li></ul>|
