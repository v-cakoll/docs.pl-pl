---
title: Podsumowanie typu śledzenia
ms.date: 03/30/2017
ms.assetid: e639410b-d1d1-479c-b78e-a4701d4e4085
ms.openlocfilehash: 8f54f71ef63338708a29fac5557c7c7e8f257f58
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70856011"
---
# <a name="trace-type-summary"></a><span data-ttu-id="42ae4-102">Podsumowanie typu śledzenia</span><span class="sxs-lookup"><span data-stu-id="42ae4-102">Trace Type Summary</span></span>
<span data-ttu-id="42ae4-103">[Poziomy źródła](https://go.microsoft.com/fwlink/?LinkID=94943) definiują różne poziomy śledzenia: Krytyczne, błąd, ostrzeżenie, informacje i pełne, a także zawiera opis `ActivityTracing` flagi, która przełącza dane wyjściowe z granicy śledzenia i zdarzeń transferu aktywności.</span><span class="sxs-lookup"><span data-stu-id="42ae4-103">[Source Levels](https://go.microsoft.com/fwlink/?LinkID=94943) defines various trace levels: Critical, Error, Warning, Information, and Verbose, as well as provides description of the `ActivityTracing` flag, which toggles the output of trace boundary and activity transfer events.</span></span>  
  
 <span data-ttu-id="42ae4-104">Można również przejrzeć [TraceEventType](https://go.microsoft.com/fwlink/?LinkId=95169) dla typów śladów, które mogą być emitowane z <xref:System.Diagnostics>.</span><span class="sxs-lookup"><span data-stu-id="42ae4-104">You can also review [TraceEventType](https://go.microsoft.com/fwlink/?LinkId=95169) for the types of traces which can be emitted from <xref:System.Diagnostics>.</span></span>  
  
 <span data-ttu-id="42ae4-105">W poniższej tabeli przedstawiono najważniejsze elementy.</span><span class="sxs-lookup"><span data-stu-id="42ae4-105">The following table lists the most important ones.</span></span>  
  
|<span data-ttu-id="42ae4-106">Typ śledzenia</span><span class="sxs-lookup"><span data-stu-id="42ae4-106">Trace Type</span></span>|<span data-ttu-id="42ae4-107">Opis</span><span class="sxs-lookup"><span data-stu-id="42ae4-107">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="42ae4-108">Krytyczny</span><span class="sxs-lookup"><span data-stu-id="42ae4-108">Critical</span></span>|<span data-ttu-id="42ae4-109">Błąd krytyczny lub awaria aplikacji.</span><span class="sxs-lookup"><span data-stu-id="42ae4-109">Fatal error or application crash.</span></span>|  
|<span data-ttu-id="42ae4-110">Błąd</span><span class="sxs-lookup"><span data-stu-id="42ae4-110">Error</span></span>|<span data-ttu-id="42ae4-111">Odwracalny błąd.</span><span class="sxs-lookup"><span data-stu-id="42ae4-111">Recoverable error.</span></span>|  
|<span data-ttu-id="42ae4-112">Ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="42ae4-112">Warning</span></span>|<span data-ttu-id="42ae4-113">Komunikat informacyjny.</span><span class="sxs-lookup"><span data-stu-id="42ae4-113">Informational message.</span></span>|  
|<span data-ttu-id="42ae4-114">Informacje</span><span class="sxs-lookup"><span data-stu-id="42ae4-114">Information</span></span>|<span data-ttu-id="42ae4-115">Problem niekrytyczny.</span><span class="sxs-lookup"><span data-stu-id="42ae4-115">Non-critical problem.</span></span>|  
|<span data-ttu-id="42ae4-116">Pełny</span><span class="sxs-lookup"><span data-stu-id="42ae4-116">Verbose</span></span>|<span data-ttu-id="42ae4-117">Śledzenie debugowania.</span><span class="sxs-lookup"><span data-stu-id="42ae4-117">Debugging trace.</span></span>|  
|<span data-ttu-id="42ae4-118">Uruchamianie</span><span class="sxs-lookup"><span data-stu-id="42ae4-118">Start</span></span>|<span data-ttu-id="42ae4-119">Rozpoczynanie logicznej jednostki przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="42ae4-119">Starting of a logical unit of processing.</span></span>|  
|<span data-ttu-id="42ae4-120">Wstrzymywanie</span><span class="sxs-lookup"><span data-stu-id="42ae4-120">Suspend</span></span>|<span data-ttu-id="42ae4-121">Zawieszenie logicznej jednostki przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="42ae4-121">Suspension of a logical unit of processing.</span></span>|  
|<span data-ttu-id="42ae4-122">Wznawianie</span><span class="sxs-lookup"><span data-stu-id="42ae4-122">Resume</span></span>|<span data-ttu-id="42ae4-123">Wznawianie jednostki logicznej przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="42ae4-123">Resumption of a logical unit of processing.</span></span>|  
|<span data-ttu-id="42ae4-124">Zatrzymywanie</span><span class="sxs-lookup"><span data-stu-id="42ae4-124">Stop</span></span>|<span data-ttu-id="42ae4-125">Zatrzymywanie logicznej jednostki przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="42ae4-125">Stopping of a logical unit of processing.</span></span>|  
|<span data-ttu-id="42ae4-126">Transfer</span><span class="sxs-lookup"><span data-stu-id="42ae4-126">Transfer</span></span>|<span data-ttu-id="42ae4-127">Zmiana tożsamości korelacji.</span><span class="sxs-lookup"><span data-stu-id="42ae4-127">Changing of correlation identity.</span></span>|  
  
 <span data-ttu-id="42ae4-128">Działanie jest zdefiniowane jako kombinacja powyższych typów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="42ae4-128">An activity is defined as a combination of the trace types above.</span></span>  
  
 <span data-ttu-id="42ae4-129">Poniżej znajduje się wyrażenie regularne, które definiuje idealne działanie w zakresie lokalnym (śledzenie źródła),</span><span class="sxs-lookup"><span data-stu-id="42ae4-129">The following is a regular expression that defines an ideal activity in a local (trace source) scope,</span></span>  
  
 `R = Start (Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop`  
  
 <span data-ttu-id="42ae4-130">Oznacza to, że działanie musi spełniać następujące warunki.</span><span class="sxs-lookup"><span data-stu-id="42ae4-130">This means that an activity must satisfy the following conditions.</span></span>  
  
- <span data-ttu-id="42ae4-131">Musi on być odpowiednio uruchamiany i zatrzymany przez uruchamianie i zatrzymywanie śledzenia</span><span class="sxs-lookup"><span data-stu-id="42ae4-131">It must start and stop respectively by a Start and Stop traces</span></span>  
  
- <span data-ttu-id="42ae4-132">Musi mieć ślad transferu bezpośrednio poprzedzający śledzenie wstrzymania lub wznowienia</span><span class="sxs-lookup"><span data-stu-id="42ae4-132">It must have a Transfer trace immediately preceding a Suspend or Resume trace</span></span>  
  
- <span data-ttu-id="42ae4-133">Nie może mieć żadnych śladów między śladami zawieszenia i wznowienia, jeśli istnieją takie ślady</span><span class="sxs-lookup"><span data-stu-id="42ae4-133">It must not have any traces between the Suspend and Resume traces if such traces exist</span></span>  
  
- <span data-ttu-id="42ae4-134">Może to być dowolny i wiele ze śladów krytyczne/błąd/ostrzeżenie/informacja/pełny/transfer, o ile zostały spełnione poprzednie warunki</span><span class="sxs-lookup"><span data-stu-id="42ae4-134">It can have any and as many of critical/Error/Warning/Information/Verbose/Transfer traces as long as the previous conditions are observed</span></span>  
  
 <span data-ttu-id="42ae4-135">Poniżej znajduje się wyrażenie regularne, które definiuje idealne działanie w zakresie globalnym,</span><span class="sxs-lookup"><span data-stu-id="42ae4-135">The following is a regular expression that defines an ideal activity in the global scope,</span></span>  
  
`R+`  
  
 <span data-ttu-id="42ae4-136">za pomocą języka R jest wyrażeniem regularnym dla działania w zakresie lokalnym.</span><span class="sxs-lookup"><span data-stu-id="42ae4-136">with R being the regular expression for an activity in the local scope.</span></span> <span data-ttu-id="42ae4-137">Spowoduje to przetłumaczenie na,</span><span class="sxs-lookup"><span data-stu-id="42ae4-137">This translates to,</span></span>  
  
`[R+ = Start ( Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop]+`
