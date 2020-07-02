---
ms.openlocfilehash: c53fe57f3278741a927a2f00b11af6e26dafce66
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620149"
---
### <a name="aspnet-mvc-now-escapes-spaces-in-strings-passed-in-via-route-parameters"></a><span data-ttu-id="c2124-101">ASP.NET MVC teraz wyprowadza spacje w ciągach przesyłanych za pośrednictwem parametrów trasy</span><span class="sxs-lookup"><span data-stu-id="c2124-101">ASP.NET MVC now escapes spaces in strings passed in via route parameters</span></span>

#### <a name="details"></a><span data-ttu-id="c2124-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="c2124-102">Details</span></span>

<span data-ttu-id="c2124-103">Aby zapewnić zgodność ze standardem RFC 2396, w przypadku wypełniania parametrów akcji z trasy są teraz zmieniane spacje w ścieżkach tras.</span><span class="sxs-lookup"><span data-stu-id="c2124-103">In order to conform to RFC 2396, spaces in route paths are now escaped when populating action parameters from a route.</span></span> <span data-ttu-id="c2124-104">W związku z tym, w <code>/controller/action/some data</code> <code>/controller/action/{data}</code> przeciwieństwie do trasy i podania <code>some data</code> jako parametru danych, będzie ona teraz dostarczana <code>some%20data</code> .</span><span class="sxs-lookup"><span data-stu-id="c2124-104">So, whereas  <code>/controller/action/some data</code> would previously match the route <code>/controller/action/{data}</code> and provide <code>some data</code> as the data parameter, it will now provide <code>some%20data</code> instead.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="c2124-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="c2124-105">Suggestion</span></span>

<span data-ttu-id="c2124-106">Kod powinien zostać zaktualizowany do nieucieczki parametrów ciągu z trasy.</span><span class="sxs-lookup"><span data-stu-id="c2124-106">Code should be updated to unescape string parameters from a route.</span></span> <span data-ttu-id="c2124-107">Jeśli oryginalny identyfikator URI jest wymagany, dostęp do niego można uzyskać za pomocą <xref:System.Net.HttpWebRequest.RequestUri> . Interfejs API OriginalString.</span><span class="sxs-lookup"><span data-stu-id="c2124-107">If the original URI is needed, it can be accessed with the <xref:System.Net.HttpWebRequest.RequestUri>.OriginalString API.</span></span>

| <span data-ttu-id="c2124-108">Nazwa</span><span class="sxs-lookup"><span data-stu-id="c2124-108">Name</span></span>    | <span data-ttu-id="c2124-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="c2124-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c2124-110">Zakres</span><span class="sxs-lookup"><span data-stu-id="c2124-110">Scope</span></span>   |<span data-ttu-id="c2124-111">Mały</span><span class="sxs-lookup"><span data-stu-id="c2124-111">Minor</span></span>|
|<span data-ttu-id="c2124-112">Wersja</span><span class="sxs-lookup"><span data-stu-id="c2124-112">Version</span></span>|<span data-ttu-id="c2124-113">4.5.2</span><span class="sxs-lookup"><span data-stu-id="c2124-113">4.5.2</span></span>|
|<span data-ttu-id="c2124-114">Typ</span><span class="sxs-lookup"><span data-stu-id="c2124-114">Type</span></span>|<span data-ttu-id="c2124-115">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="c2124-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c2124-116">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="c2124-116">Affected APIs</span></span>

-<xref:System.Web.Mvc.RouteAttribute.%23ctor(System.String)></li></ul>|
