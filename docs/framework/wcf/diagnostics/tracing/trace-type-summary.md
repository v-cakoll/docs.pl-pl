---
title: Podsumowanie typu śledzenia
ms.date: 03/30/2017
ms.assetid: e639410b-d1d1-479c-b78e-a4701d4e4085
ms.openlocfilehash: e3bc66753dd44e1dc4c7417caf593820300f69a5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486045"
---
# <a name="trace-type-summary"></a><span data-ttu-id="86620-102">Podsumowanie typu śledzenia</span><span class="sxs-lookup"><span data-stu-id="86620-102">Trace Type Summary</span></span>
<span data-ttu-id="86620-103">[Źródło poziomy](http://go.microsoft.com/fwlink/?LinkID=94943) definiuje różne poziomy śledzenia: krytyczny, błąd, ostrzeżenie, informacje i pełne, jak również tak jak opisano w `ActivityTracing` flagi, które włącza dane wyjściowe śledzenia zdarzeń transfer granic i działania.</span><span class="sxs-lookup"><span data-stu-id="86620-103">[Source Levels](http://go.microsoft.com/fwlink/?LinkID=94943) defines various trace levels: Critical, Error, Warning, Information, and Verbose, as well as provides description of the `ActivityTracing` flag, which toggles the output of trace boundary and activity transfer events.</span></span>  
  
 <span data-ttu-id="86620-104">Można również przejrzeć [element TraceEventType](http://go.microsoft.com/fwlink/?LinkId=95169) dla typów danych śledzenia, które może być wysyłany z <xref:System.Diagnostics>.</span><span class="sxs-lookup"><span data-stu-id="86620-104">You can also review [TraceEventType](http://go.microsoft.com/fwlink/?LinkId=95169) for the types of traces which can be emitted from <xref:System.Diagnostics>.</span></span>  
  
 <span data-ttu-id="86620-105">W poniższej tabeli wymieniono najważniejsze alerty.</span><span class="sxs-lookup"><span data-stu-id="86620-105">The following table lists the most important ones.</span></span>  
  
|<span data-ttu-id="86620-106">Typ śledzenia</span><span class="sxs-lookup"><span data-stu-id="86620-106">Trace Type</span></span>|<span data-ttu-id="86620-107">Opis</span><span class="sxs-lookup"><span data-stu-id="86620-107">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="86620-108">Krytyczny</span><span class="sxs-lookup"><span data-stu-id="86620-108">Critical</span></span>|<span data-ttu-id="86620-109">Błąd krytyczny lub aplikacji awarii.</span><span class="sxs-lookup"><span data-stu-id="86620-109">Fatal error or application crash.</span></span>|  
|<span data-ttu-id="86620-110">Błąd</span><span class="sxs-lookup"><span data-stu-id="86620-110">Error</span></span>|<span data-ttu-id="86620-111">Nieodwracalny błąd.</span><span class="sxs-lookup"><span data-stu-id="86620-111">Recoverable error.</span></span>|  
|<span data-ttu-id="86620-112">Ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="86620-112">Warning</span></span>|<span data-ttu-id="86620-113">Komunikat informacyjny.</span><span class="sxs-lookup"><span data-stu-id="86620-113">Informational message.</span></span>|  
|<span data-ttu-id="86620-114">Informacje</span><span class="sxs-lookup"><span data-stu-id="86620-114">Information</span></span>|<span data-ttu-id="86620-115">Niekrytyczny problem.</span><span class="sxs-lookup"><span data-stu-id="86620-115">Non-critical problem.</span></span>|  
|<span data-ttu-id="86620-116">Pełny</span><span class="sxs-lookup"><span data-stu-id="86620-116">Verbose</span></span>|<span data-ttu-id="86620-117">Śledzenie debugowania.</span><span class="sxs-lookup"><span data-stu-id="86620-117">Debugging trace.</span></span>|  
|<span data-ttu-id="86620-118">Uruchamianie</span><span class="sxs-lookup"><span data-stu-id="86620-118">Start</span></span>|<span data-ttu-id="86620-119">Rozpoczynanie przetwarzania jednostki logicznej.</span><span class="sxs-lookup"><span data-stu-id="86620-119">Starting of a logical unit of processing.</span></span>|  
|<span data-ttu-id="86620-120">Wstrzymaj</span><span class="sxs-lookup"><span data-stu-id="86620-120">Suspend</span></span>|<span data-ttu-id="86620-121">Zawieszenie jednostki logicznej przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="86620-121">Suspension of a logical unit of processing.</span></span>|  
|<span data-ttu-id="86620-122">Wznawianie</span><span class="sxs-lookup"><span data-stu-id="86620-122">Resume</span></span>|<span data-ttu-id="86620-123">Wznowienie przetwarzania jednostki logicznej.</span><span class="sxs-lookup"><span data-stu-id="86620-123">Resumption of a logical unit of processing.</span></span>|  
|<span data-ttu-id="86620-124">Zatrzymywanie</span><span class="sxs-lookup"><span data-stu-id="86620-124">Stop</span></span>|<span data-ttu-id="86620-125">Zatrzymywanie jednostki logicznej przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="86620-125">Stopping of a logical unit of processing.</span></span>|  
|<span data-ttu-id="86620-126">Transfer</span><span class="sxs-lookup"><span data-stu-id="86620-126">Transfer</span></span>|<span data-ttu-id="86620-127">Zmiana tożsamości korelacji.</span><span class="sxs-lookup"><span data-stu-id="86620-127">Changing of correlation identity.</span></span>|  
  
 <span data-ttu-id="86620-128">Działanie jest zdefiniowany jako kombinacji typów śledzenia powyżej.</span><span class="sxs-lookup"><span data-stu-id="86620-128">An activity is defined as a combination of the trace types above.</span></span>  
  
 <span data-ttu-id="86620-129">Poniżej znajduje się wyrażenie regularne definiuje idealne działania w zakresie lokalnego (źródła)</span><span class="sxs-lookup"><span data-stu-id="86620-129">The following is a regular expression that defines an ideal activity in a local (trace source) scope,</span></span>  
  
 `R = Start (Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop`  
  
 <span data-ttu-id="86620-130">Oznacza to, że działanie muszą spełniać następujące warunki.</span><span class="sxs-lookup"><span data-stu-id="86620-130">This means that an activity must satisfy the following conditions.</span></span>  
  
-   <span data-ttu-id="86620-131">Musi zaczynać się i odpowiednio Zatrzymaj śledzenie rozpoczęcia i zakończenia</span><span class="sxs-lookup"><span data-stu-id="86620-131">It must start and stop respectively by a Start and Stop traces</span></span>  
  
-   <span data-ttu-id="86620-132">Musi mieć śledzenia Transfer poprzedzającego śledzenia wstrzymania lub wznowienia</span><span class="sxs-lookup"><span data-stu-id="86620-132">It must have a Transfer trace immediately preceding a Suspend or Resume trace</span></span>  
  
-   <span data-ttu-id="86620-133">Nie może mieć śladów między śladów wstrzymywanie i wznawianie, jeśli istnieją takie dane śledzenia</span><span class="sxs-lookup"><span data-stu-id="86620-133">It must not have any traces between the Suspend and Resume traces if such traces exist</span></span>  
  
-   <span data-ttu-id="86620-134">Tak długo, jak poprzednie warunki są spełnione może mieć żadnych i ślady krytyczne/błędu/ostrzeżenia/informacji/Verbose/Transfer</span><span class="sxs-lookup"><span data-stu-id="86620-134">It can have any and as many of critical/Error/Warning/Information/Verbose/Transfer traces as long as the previous conditions are observed</span></span>  
  
 <span data-ttu-id="86620-135">Poniżej znajduje się wyrażenie regularne definiuje działania idealne rozwiązanie w zakresie globalnym</span><span class="sxs-lookup"><span data-stu-id="86620-135">The following is a regular expression that defines an ideal activity in the global scope,</span></span>  
  
```  
R+   
```  
  
 <span data-ttu-id="86620-136">z języka R są wyrażenia regularnego do działania w zakresie lokalnym.</span><span class="sxs-lookup"><span data-stu-id="86620-136">with R being the regular expression for an activity in the local scope.</span></span> <span data-ttu-id="86620-137">Przekłada się to,</span><span class="sxs-lookup"><span data-stu-id="86620-137">This translates to,</span></span>  
  
```  
[R+ = Start ( Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop]+  
```
