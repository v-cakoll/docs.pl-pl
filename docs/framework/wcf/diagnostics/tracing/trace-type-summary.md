---
title: Podsumowanie typu śledzenia
ms.date: 03/30/2017
ms.assetid: e639410b-d1d1-479c-b78e-a4701d4e4085
ms.openlocfilehash: 8ed6dceb19caa52f928f285064c60337e3f15a87
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674841"
---
# <a name="trace-type-summary"></a><span data-ttu-id="e6747-102">Podsumowanie typu śledzenia</span><span class="sxs-lookup"><span data-stu-id="e6747-102">Trace Type Summary</span></span>
<span data-ttu-id="e6747-103">[Poziomy źródła](xref:System.Diagnostics.SourceLevels) definiuje różne poziomy śledzenia: Krytyczne, Błąd, Ostrzeżenie, Informacje i Pełne, a `ActivityTracing` także zawiera opis flagi, która przełącza dane wyjściowe śledzenia granic i zdarzeń transferu działania.</span><span class="sxs-lookup"><span data-stu-id="e6747-103">[Source Levels](xref:System.Diagnostics.SourceLevels) defines various trace levels: Critical, Error, Warning, Information, and Verbose, as well as provides a description of the `ActivityTracing` flag, which toggles the output of trace boundary and activity transfer events.</span></span>  
  
 <span data-ttu-id="e6747-104">Można również <xref:System.Diagnostics.TraceEventType> przejrzeć typy śladów, które <xref:System.Diagnostics>mogą być emitowane z .</span><span class="sxs-lookup"><span data-stu-id="e6747-104">You can also review <xref:System.Diagnostics.TraceEventType> for the types of traces which can be emitted from <xref:System.Diagnostics>.</span></span>  
  
 <span data-ttu-id="e6747-105">W poniższej tabeli wymieniono najważniejsze z nich.</span><span class="sxs-lookup"><span data-stu-id="e6747-105">The following table lists the most important ones.</span></span>  
  
|<span data-ttu-id="e6747-106">Typ śledzenia</span><span class="sxs-lookup"><span data-stu-id="e6747-106">Trace Type</span></span>|<span data-ttu-id="e6747-107">Opis</span><span class="sxs-lookup"><span data-stu-id="e6747-107">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="e6747-108">Krytyczny</span><span class="sxs-lookup"><span data-stu-id="e6747-108">Critical</span></span>|<span data-ttu-id="e6747-109">Błąd krytyczny lub awaria aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e6747-109">Fatal error or application crash.</span></span>|  
|<span data-ttu-id="e6747-110">Błąd</span><span class="sxs-lookup"><span data-stu-id="e6747-110">Error</span></span>|<span data-ttu-id="e6747-111">Błąd do odzyskania.</span><span class="sxs-lookup"><span data-stu-id="e6747-111">Recoverable error.</span></span>|  
|<span data-ttu-id="e6747-112">Ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="e6747-112">Warning</span></span>|<span data-ttu-id="e6747-113">Wiadomość informacyjna.</span><span class="sxs-lookup"><span data-stu-id="e6747-113">Informational message.</span></span>|  
|<span data-ttu-id="e6747-114">Informacje</span><span class="sxs-lookup"><span data-stu-id="e6747-114">Information</span></span>|<span data-ttu-id="e6747-115">Problem niekrytyczny.</span><span class="sxs-lookup"><span data-stu-id="e6747-115">Non-critical problem.</span></span>|  
|<span data-ttu-id="e6747-116">Pełny</span><span class="sxs-lookup"><span data-stu-id="e6747-116">Verbose</span></span>|<span data-ttu-id="e6747-117">Debugowanie śledzenia.</span><span class="sxs-lookup"><span data-stu-id="e6747-117">Debugging trace.</span></span>|  
|<span data-ttu-id="e6747-118">Rozpoczęcie</span><span class="sxs-lookup"><span data-stu-id="e6747-118">Start</span></span>|<span data-ttu-id="e6747-119">Rozpoczęcie logicznej jednostki przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="e6747-119">Starting of a logical unit of processing.</span></span>|  
|<span data-ttu-id="e6747-120">Wstrzymanie</span><span class="sxs-lookup"><span data-stu-id="e6747-120">Suspend</span></span>|<span data-ttu-id="e6747-121">Zawieszenie logicznej jednostki przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="e6747-121">Suspension of a logical unit of processing.</span></span>|  
|<span data-ttu-id="e6747-122">Resume</span><span class="sxs-lookup"><span data-stu-id="e6747-122">Resume</span></span>|<span data-ttu-id="e6747-123">Wznowienie logicznej jednostki przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="e6747-123">Resumption of a logical unit of processing.</span></span>|  
|<span data-ttu-id="e6747-124">Stop</span><span class="sxs-lookup"><span data-stu-id="e6747-124">Stop</span></span>|<span data-ttu-id="e6747-125">Zatrzymywanie logicznej jednostki przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="e6747-125">Stopping of a logical unit of processing.</span></span>|  
|<span data-ttu-id="e6747-126">Transfer</span><span class="sxs-lookup"><span data-stu-id="e6747-126">Transfer</span></span>|<span data-ttu-id="e6747-127">Zmiana tożsamości korelacji.</span><span class="sxs-lookup"><span data-stu-id="e6747-127">Changing of correlation identity.</span></span>|  
  
 <span data-ttu-id="e6747-128">Działanie jest zdefiniowane jako kombinacja typów śledzenia powyżej.</span><span class="sxs-lookup"><span data-stu-id="e6747-128">An activity is defined as a combination of the trace types above.</span></span>  
  
 <span data-ttu-id="e6747-129">Poniżej znajduje się wyrażenie regularne, które definiuje idealne działanie w zakresie lokalnym (źródło śledzenia),</span><span class="sxs-lookup"><span data-stu-id="e6747-129">The following is a regular expression that defines an ideal activity in a local (trace source) scope,</span></span>  
  
 `R = Start (Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop`  
  
 <span data-ttu-id="e6747-130">Oznacza to, że działanie musi spełniać następujące warunki.</span><span class="sxs-lookup"><span data-stu-id="e6747-130">This means that an activity must satisfy the following conditions.</span></span>  
  
- <span data-ttu-id="e6747-131">Musi rozpocząć i zatrzymać odpowiednio przez ślady start i stop</span><span class="sxs-lookup"><span data-stu-id="e6747-131">It must start and stop respectively by a Start and Stop traces</span></span>  
  
- <span data-ttu-id="e6747-132">Musi mieć transfer śledzenia bezpośrednio poprzedzających wstrzymanie lub wznowienie śledzenia</span><span class="sxs-lookup"><span data-stu-id="e6747-132">It must have a Transfer trace immediately preceding a Suspend or Resume trace</span></span>  
  
- <span data-ttu-id="e6747-133">Nie może mieć żadnych śladów między wstrzymywają i wznawiaj ślady, jeśli takie ślady istnieją</span><span class="sxs-lookup"><span data-stu-id="e6747-133">It must not have any traces between the Suspend and Resume traces if such traces exist</span></span>  
  
- <span data-ttu-id="e6747-134">Może mieć dowolną i dowolną liczbę krytycznych/błąd/ostrzeżenie/informacje/pełne/transferowe ślady, o ile zaobserwowano poprzednie warunki</span><span class="sxs-lookup"><span data-stu-id="e6747-134">It can have any and as many of critical/Error/Warning/Information/Verbose/Transfer traces as long as the previous conditions are observed</span></span>  
  
 <span data-ttu-id="e6747-135">Poniżej znajduje się wyrażenie regularne, które definiuje idealne działanie w zakresie globalnym,</span><span class="sxs-lookup"><span data-stu-id="e6747-135">The following is a regular expression that defines an ideal activity in the global scope,</span></span>  
  
`R+`  
  
 <span data-ttu-id="e6747-136">z R jest wyrażeniem regularnym dla działania w zakresie lokalnym.</span><span class="sxs-lookup"><span data-stu-id="e6747-136">with R being the regular expression for an activity in the local scope.</span></span> <span data-ttu-id="e6747-137">Przekłada się to na,</span><span class="sxs-lookup"><span data-stu-id="e6747-137">This translates to,</span></span>  
  
`[R+ = Start ( Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop]+`
