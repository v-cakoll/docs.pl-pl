---
ms.openlocfilehash: b521f4163bf5bf4a369d0eec12dae503703a976e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614646"
---
### <a name="throttle-concurrent-requests-per-session"></a><span data-ttu-id="77102-101">Ogranicz współbieżne żądania na sesję</span><span class="sxs-lookup"><span data-stu-id="77102-101">Throttle concurrent requests per session</span></span>

#### <a name="details"></a><span data-ttu-id="77102-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="77102-102">Details</span></span>

<span data-ttu-id="77102-103">W .NET Framework 4.6.2 i starszych ASP.NET wykonuje żądania z tym samym identyfikatorem sesji sekwencyjnie, a ASP.NET zawsze domyślnie wystawia identyfikator sesji za pomocą plików cookie.</span><span class="sxs-lookup"><span data-stu-id="77102-103">In the .NET Framework 4.6.2 and earlier, ASP.NET executes requests with the same Sessionid sequentially, and ASP.NET always issues the Sessionid through cookies by default.</span></span> <span data-ttu-id="77102-104">Jeśli odpowiedź strony zajmuje dużo czasu, znacznie obniży wydajność serwera, naciskając klawisz <kbd>F5</kbd> w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="77102-104">If a page takes a long time to respond, it will significantly degrade server performance just by pressing <kbd>F5</kbd> on the browser.</span></span> <span data-ttu-id="77102-105">W ramach poprawki dodaliśmy licznik do śledzenia żądań umieszczonych w kolejce i kończy żądania po przekroczeniu określonego limitu.</span><span class="sxs-lookup"><span data-stu-id="77102-105">In the fix, we added a counter to track the queued requests and terminate the requests when they exceed a specified limit.</span></span> <span data-ttu-id="77102-106">Wartość domyślna to 50.</span><span class="sxs-lookup"><span data-stu-id="77102-106">The default value is 50.</span></span> <span data-ttu-id="77102-107">Jeśli limit zostanie osiągnięty, w dzienniku zdarzeń zostanie zarejestrowane ostrzeżenie, a odpowiedź HTTP 500 może zostać zarejestrowana w dzienniku usług IIS.</span><span class="sxs-lookup"><span data-stu-id="77102-107">If the limit is reached, a warning will be logged in the event log, and an HTTP 500 response may be recorded in the IIS log.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="77102-108">Sugestia</span><span class="sxs-lookup"><span data-stu-id="77102-108">Suggestion</span></span>

<span data-ttu-id="77102-109">Aby przywrócić stare zachowanie, można dodać następujące ustawienie do pliku web.config, aby zrezygnować z nowego zachowania.</span><span class="sxs-lookup"><span data-stu-id="77102-109">To restore the old behavior, you can add the following setting to your web.config file to opt out of the new behavior.</span></span>

```xml
<appSettings>
    <add key="aspnet:RequestQueueLimitPerSession" value="2147483647"/>
</appSettings>
```

| <span data-ttu-id="77102-110">Nazwa</span><span class="sxs-lookup"><span data-stu-id="77102-110">Name</span></span>    | <span data-ttu-id="77102-111">Wartość</span><span class="sxs-lookup"><span data-stu-id="77102-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="77102-112">Zakres</span><span class="sxs-lookup"><span data-stu-id="77102-112">Scope</span></span>   | <span data-ttu-id="77102-113">Brzeg</span><span class="sxs-lookup"><span data-stu-id="77102-113">Edge</span></span>        |
| <span data-ttu-id="77102-114">Wersja</span><span class="sxs-lookup"><span data-stu-id="77102-114">Version</span></span> | <span data-ttu-id="77102-115">4,7</span><span class="sxs-lookup"><span data-stu-id="77102-115">4.7</span></span>         |
| <span data-ttu-id="77102-116">Typ</span><span class="sxs-lookup"><span data-stu-id="77102-116">Type</span></span>    | <span data-ttu-id="77102-117">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="77102-117">Retargeting</span></span> |
