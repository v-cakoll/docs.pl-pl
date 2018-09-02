---
title: Podsumowanie typu śledzenia
ms.date: 03/30/2017
ms.assetid: e639410b-d1d1-479c-b78e-a4701d4e4085
ms.openlocfilehash: 73777df2b58b14947c416ce409bcb42d439499ec
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43403846"
---
# <a name="trace-type-summary"></a><span data-ttu-id="6dce8-102">Podsumowanie typu śledzenia</span><span class="sxs-lookup"><span data-stu-id="6dce8-102">Trace Type Summary</span></span>
<span data-ttu-id="6dce8-103">[Źródło poziomy](https://go.microsoft.com/fwlink/?LinkID=94943) definiuje różne poziomy śledzenia: krytyczny, błąd, ostrzeżenie, informacje i pełne informacje, jak również tak jak opisano w `ActivityTracing` flagi, które włącza/wyłącza dane wyjściowe śledzenia zdarzenia transferu granic i działania.</span><span class="sxs-lookup"><span data-stu-id="6dce8-103">[Source Levels](https://go.microsoft.com/fwlink/?LinkID=94943) defines various trace levels: Critical, Error, Warning, Information, and Verbose, as well as provides description of the `ActivityTracing` flag, which toggles the output of trace boundary and activity transfer events.</span></span>  
  
 <span data-ttu-id="6dce8-104">Możesz również przejrzeć [opcją TraceEventType](https://go.microsoft.com/fwlink/?LinkId=95169) dla typów danych śledzenia, które mogą być emitowane przez <xref:System.Diagnostics>.</span><span class="sxs-lookup"><span data-stu-id="6dce8-104">You can also review [TraceEventType](https://go.microsoft.com/fwlink/?LinkId=95169) for the types of traces which can be emitted from <xref:System.Diagnostics>.</span></span>  
  
 <span data-ttu-id="6dce8-105">W poniższej tabeli wymieniono najważniejsze.</span><span class="sxs-lookup"><span data-stu-id="6dce8-105">The following table lists the most important ones.</span></span>  
  
|<span data-ttu-id="6dce8-106">Typ śledzenia</span><span class="sxs-lookup"><span data-stu-id="6dce8-106">Trace Type</span></span>|<span data-ttu-id="6dce8-107">Opis</span><span class="sxs-lookup"><span data-stu-id="6dce8-107">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="6dce8-108">Krytyczny</span><span class="sxs-lookup"><span data-stu-id="6dce8-108">Critical</span></span>|<span data-ttu-id="6dce8-109">Błąd krytyczny lub aplikacji awarii.</span><span class="sxs-lookup"><span data-stu-id="6dce8-109">Fatal error or application crash.</span></span>|  
|<span data-ttu-id="6dce8-110">Błąd</span><span class="sxs-lookup"><span data-stu-id="6dce8-110">Error</span></span>|<span data-ttu-id="6dce8-111">Nieodwracalny błąd.</span><span class="sxs-lookup"><span data-stu-id="6dce8-111">Recoverable error.</span></span>|  
|<span data-ttu-id="6dce8-112">Ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="6dce8-112">Warning</span></span>|<span data-ttu-id="6dce8-113">Komunikat informacyjny.</span><span class="sxs-lookup"><span data-stu-id="6dce8-113">Informational message.</span></span>|  
|<span data-ttu-id="6dce8-114">Informacje</span><span class="sxs-lookup"><span data-stu-id="6dce8-114">Information</span></span>|<span data-ttu-id="6dce8-115">Niekrytyczne problem.</span><span class="sxs-lookup"><span data-stu-id="6dce8-115">Non-critical problem.</span></span>|  
|<span data-ttu-id="6dce8-116">Pełny</span><span class="sxs-lookup"><span data-stu-id="6dce8-116">Verbose</span></span>|<span data-ttu-id="6dce8-117">Śledzenie debugowania.</span><span class="sxs-lookup"><span data-stu-id="6dce8-117">Debugging trace.</span></span>|  
|<span data-ttu-id="6dce8-118">Uruchamianie</span><span class="sxs-lookup"><span data-stu-id="6dce8-118">Start</span></span>|<span data-ttu-id="6dce8-119">Uruchamianie jednostki logicznej przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="6dce8-119">Starting of a logical unit of processing.</span></span>|  
|<span data-ttu-id="6dce8-120">Wstrzymywanie</span><span class="sxs-lookup"><span data-stu-id="6dce8-120">Suspend</span></span>|<span data-ttu-id="6dce8-121">Zawieszenie jednostki logicznej przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="6dce8-121">Suspension of a logical unit of processing.</span></span>|  
|<span data-ttu-id="6dce8-122">Wznawianie</span><span class="sxs-lookup"><span data-stu-id="6dce8-122">Resume</span></span>|<span data-ttu-id="6dce8-123">Wznowienie przetwarzania jednostkę logiczną.</span><span class="sxs-lookup"><span data-stu-id="6dce8-123">Resumption of a logical unit of processing.</span></span>|  
|<span data-ttu-id="6dce8-124">Zatrzymywanie</span><span class="sxs-lookup"><span data-stu-id="6dce8-124">Stop</span></span>|<span data-ttu-id="6dce8-125">Zatrzymywanie jednostki logicznej przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="6dce8-125">Stopping of a logical unit of processing.</span></span>|  
|<span data-ttu-id="6dce8-126">Transfer</span><span class="sxs-lookup"><span data-stu-id="6dce8-126">Transfer</span></span>|<span data-ttu-id="6dce8-127">Zmiana tożsamości korelacji.</span><span class="sxs-lookup"><span data-stu-id="6dce8-127">Changing of correlation identity.</span></span>|  
  
 <span data-ttu-id="6dce8-128">Działanie jest zdefiniowany jako kombinacja powyższych typów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="6dce8-128">An activity is defined as a combination of the trace types above.</span></span>  
  
 <span data-ttu-id="6dce8-129">Oto wyrażeń regularnych, które definiuje działania idealnym rozwiązaniem w zakresie lokalnego (źródła)</span><span class="sxs-lookup"><span data-stu-id="6dce8-129">The following is a regular expression that defines an ideal activity in a local (trace source) scope,</span></span>  
  
 `R = Start (Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop`  
  
 <span data-ttu-id="6dce8-130">Oznacza to, że działanie musi spełniać następujące warunki.</span><span class="sxs-lookup"><span data-stu-id="6dce8-130">This means that an activity must satisfy the following conditions.</span></span>  
  
-   <span data-ttu-id="6dce8-131">Musi zaczynać się i Zatrzymaj odpowiednio przez uruchamianie i zatrzymywanie danych śledzenia</span><span class="sxs-lookup"><span data-stu-id="6dce8-131">It must start and stop respectively by a Start and Stop traces</span></span>  
  
-   <span data-ttu-id="6dce8-132">Musi on mieć śledzenia transferu, bezpośrednio poprzedzających śledzenia wstrzymania lub wznowienia</span><span class="sxs-lookup"><span data-stu-id="6dce8-132">It must have a Transfer trace immediately preceding a Suspend or Resume trace</span></span>  
  
-   <span data-ttu-id="6dce8-133">Nie może mieć żadnych śladów między śledzenia wstrzymywanie i wznawianie, jeśli istnieją takie ślady</span><span class="sxs-lookup"><span data-stu-id="6dce8-133">It must not have any traces between the Suspend and Resume traces if such traces exist</span></span>  
  
-   <span data-ttu-id="6dce8-134">Tak długo, jak poprzednie warunki zostały spełnione może mieć żadnych i jak najwięcej ślady krytyczne/błędu/ostrzeżenia/informacji/Verbose/Transfer</span><span class="sxs-lookup"><span data-stu-id="6dce8-134">It can have any and as many of critical/Error/Warning/Information/Verbose/Transfer traces as long as the previous conditions are observed</span></span>  
  
 <span data-ttu-id="6dce8-135">Oto wyrażeń regularnych, które definiuje działania idealnym rozwiązaniem w zakresie globalnym</span><span class="sxs-lookup"><span data-stu-id="6dce8-135">The following is a regular expression that defines an ideal activity in the global scope,</span></span>  
  
```  
R+   
```  
  
 <span data-ttu-id="6dce8-136">przy użyciu języka R trwa wyrażenia regularnego dla działania w zakresie lokalnym.</span><span class="sxs-lookup"><span data-stu-id="6dce8-136">with R being the regular expression for an activity in the local scope.</span></span> <span data-ttu-id="6dce8-137">Przekłada się to,</span><span class="sxs-lookup"><span data-stu-id="6dce8-137">This translates to,</span></span>  
  
```  
[R+ = Start ( Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop]+  
```
