---
title: Dostawcy CLR ETW
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ETW, CLR providers
- CLR ETW providers
ms.assetid: 0beafad4-b2c8-47f4-b342-83411d57a51f
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 18353939108d58eb2aaffee97e059e4430b25e3a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="clr-etw-providers"></a><span data-ttu-id="791eb-102">Dostawcy CLR ETW</span><span class="sxs-lookup"><span data-stu-id="791eb-102">CLR ETW Providers</span></span>
<span data-ttu-id="791eb-103">Środowisko uruchomieniowe języka wspólnego (CLR) ma dwóch dostawców: stert dostawcy i dostawcy środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="791eb-103">The common language runtime (CLR) has two providers: the runtime provider and the rundown provider.</span></span>  
  
 <span data-ttu-id="791eb-104">Dostawcy środowiska uruchomieniowego informuje o zdarzeniach, w zależności od tego, które są włączone słowa kluczowe (kategorie zdarzeń).</span><span class="sxs-lookup"><span data-stu-id="791eb-104">The runtime provider raises events, depending on which keywords (categories of events) are enabled.</span></span> <span data-ttu-id="791eb-105">Na przykład może zbierać zdarzenia modułu ładującego, włączając `LoaderKeyword` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="791eb-105">For example, you can collect loader events by enabling the `LoaderKeyword` keyword.</span></span>  
  
 <span data-ttu-id="791eb-106">Zdarzenia śledzenia zdarzeń systemu Windows (ETW) są rejestrowane w pliku, który ma rozszerzenie etl, które później mogą być używane po przetwarzane w plikach plik wartości rozdzielanych przecinkami (.csv) zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="791eb-106">Event tracking for Windows (ETW) events are logged into a file that has an .etl extension, which can later be post-processed in comma-separated value (.csv) files as needed.</span></span> <span data-ttu-id="791eb-107">Aby uzyskać informacje na temat konwertowania pliku etl do pliku CSV, zobacz [kontrolowanie rejestrowania Framework .NET](../../../docs/framework/performance/controlling-logging.md).</span><span class="sxs-lookup"><span data-stu-id="791eb-107">For information about how to convert the .etl file to a .csv file, see [Controlling .NET Framework Logging](../../../docs/framework/performance/controlling-logging.md).</span></span>  
  
## <a name="the-runtime-provider"></a><span data-ttu-id="791eb-108">Dostawcy środowiska wykonawczego</span><span class="sxs-lookup"><span data-stu-id="791eb-108">The Runtime Provider</span></span>  
 <span data-ttu-id="791eb-109">Dostawca środowiska uruchomieniowego jest głównym dostawcy CLR ETW.</span><span class="sxs-lookup"><span data-stu-id="791eb-109">The runtime provider is the main CLR ETW provider.</span></span>  
  
 <span data-ttu-id="791eb-110">Dostawca środowiska uruchomieniowego CLR identyfikator GUID jest e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.</span><span class="sxs-lookup"><span data-stu-id="791eb-110">The CLR runtime provider GUID is e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.</span></span>  
  
 <span data-ttu-id="791eb-111">Przykłady tego, jak rejestrować i przeglądać zdarzenia CLR ETW za pomocą powszechnie dostępnych narzędzi, zobacz [kontrolowanie rejestrowania Framework .NET](../../../docs/framework/performance/controlling-logging.md).</span><span class="sxs-lookup"><span data-stu-id="791eb-111">For examples of how to log and view CLR ETW events by using commonly available tools, see [Controlling .NET Framework Logging](../../../docs/framework/performance/controlling-logging.md).</span></span>  
  
 <span data-ttu-id="791eb-112">Oprócz przy użyciu słów kluczowych, takich jak `LoaderKeyword`, trzeba włączyć słowa kluczowe do rejestrowania zdarzeń, które może być uruchamiany zbyt często.</span><span class="sxs-lookup"><span data-stu-id="791eb-112">In addition to using keywords such as `LoaderKeyword`, you may have to enable keywords for logging events that may be raised too frequently.</span></span> <span data-ttu-id="791eb-113">`StartEnumerationKeyword` i `EndEnumerationKeyword` słów kluczowych, Włącz te zdarzenia i podsumowano w [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).</span><span class="sxs-lookup"><span data-stu-id="791eb-113">The `StartEnumerationKeyword` and the `EndEnumerationKeyword` keywords enable these events and are summarized in [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).</span></span>  
  
## <a name="the-rundown-provider"></a><span data-ttu-id="791eb-114">Dostawca stert</span><span class="sxs-lookup"><span data-stu-id="791eb-114">The Rundown Provider</span></span>  
 <span data-ttu-id="791eb-115">Stert dostawcy musi być włączona w niektórych specjalnych.</span><span class="sxs-lookup"><span data-stu-id="791eb-115">The rundown provider must be turned on for certain special-purpose uses.</span></span> <span data-ttu-id="791eb-116">Jednak w przypadku większości użytkowników dostawcy środowiska uruchomieniowego powinny wystarczyć.</span><span class="sxs-lookup"><span data-stu-id="791eb-116">However, for a majority of users, the runtime provider should suffice.</span></span>  
  
 <span data-ttu-id="791eb-117">Dostawca stert CLR identyfikator GUID jest A669021C-C450-4609-A035-5AF59AF4DF18.</span><span class="sxs-lookup"><span data-stu-id="791eb-117">The CLR rundown provider GUID is A669021C-C450-4609-A035-5AF59AF4DF18.</span></span>  
  
 <span data-ttu-id="791eb-118">Zwykle ETW rejestrowanie jest włączone, przed uruchamia proces i rejestrowanie jest wyłączone, po zamknięciu procesu.</span><span class="sxs-lookup"><span data-stu-id="791eb-118">Normally, ETW logging is enabled before a process launches, and the logging is turned off after the process exits.</span></span> <span data-ttu-id="791eb-119">Jednak jeśli rejestrowanie funkcji ETW jest włączona, gdy proces jest wykonywany, dodatkowe potrzebne są informacje o procesie.</span><span class="sxs-lookup"><span data-stu-id="791eb-119">However, if ETW logging is turned on while the process is executing, additional information is needed about the process.</span></span> <span data-ttu-id="791eb-120">Na przykład do rozpoznawania symboli należy rejestrować zdarzenia metod dla metod, które zostały już załadowane przed włączone rejestrowanie.</span><span class="sxs-lookup"><span data-stu-id="791eb-120">For example, for symbol resolution you have to log method events for methods that were already loaded before logging was turned on.</span></span>  
  
 <span data-ttu-id="791eb-121">`DCStart` i `DCEnd` zdarzenia przechwytywania stanu procesu, gdy funkcja zbierania danych został uruchamiania i zatrzymywania.</span><span class="sxs-lookup"><span data-stu-id="791eb-121">The `DCStart` and `DCEnd` events capture the state of the process when data collection was started and stopped.</span></span> <span data-ttu-id="791eb-122">(Stan odwołuje się do informacji na wysokim poziomie, łącznie z metod, które zostały już just-in-time (JIT) skompilowany i zestawy, które zostały załadowane). Te dwa zdarzenia zawiera informacje o co została już wykonana w procesie; na przykład które metody zostały JIT-skompilowany i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="791eb-122">(State refers to information at a high level, including the methods that were already just-in-time (JIT) compiled and assemblies that were loaded.) These two events can provide information about what has already happened in the process; for example, which methods were JIT- compiled, and so on.</span></span>  
  
 <span data-ttu-id="791eb-123">Tylko zdarzenia o `DC`, `DCStart`, `DCEnd`, lub `DCInit` w nazwach pojawienia się w obszarze stert dostawcy.</span><span class="sxs-lookup"><span data-stu-id="791eb-123">Only the events with `DC`, `DCStart`, `DCEnd`, or `DCInit` in their names are raised under the rundown provider.</span></span> <span data-ttu-id="791eb-124">Ponadto te zdarzenia są generowane tylko w przypadku zamknięcia dostawcy.</span><span class="sxs-lookup"><span data-stu-id="791eb-124">Additionally, these events are raised only under the rundown provider.</span></span>  
  
 <span data-ttu-id="791eb-125">Oprócz filtrów słów kluczowych zdarzeń, obsługuje również dostawcę stert `StartRundownKeyword` i `EndRundownKeyword` słów kluczowych w celu zapewnienia docelowe filtrowania.</span><span class="sxs-lookup"><span data-stu-id="791eb-125">In addition to the event keyword filters, the rundown provider also supports the `StartRundownKeyword` and `EndRundownKeyword` keywords to provide targeted filtering.</span></span>  
  
### <a name="start-rundown"></a><span data-ttu-id="791eb-126">Uruchom uwalniania</span><span class="sxs-lookup"><span data-stu-id="791eb-126">Start Rundown</span></span>  
 <span data-ttu-id="791eb-127">Uwalniania rozpoczęcia jest wyzwalane, gdy włączono rejestrowanie w obszarze dostawcy stert z `StartRundownKeyword` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="791eb-127">A start rundown is triggered when logging under the rundown provider is enabled with the `StartRundownKeyword` keyword.</span></span> <span data-ttu-id="791eb-128">Powoduje to `DCStart` się zdarzenia i przechwytywanie stanu systemu.</span><span class="sxs-lookup"><span data-stu-id="791eb-128">This causes the `DCStart` event to be raised, and captures the state of the system.</span></span> <span data-ttu-id="791eb-129">Przed rozpoczęciem wyliczania `DCStartInit` zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="791eb-129">Before the start of the enumeration, the `DCStartInit` event is raised.</span></span> <span data-ttu-id="791eb-130">Na koniec wyliczenia `DCStartComplete` zdarzenia powiadomiono kontrolerem zbierania danych zakończone normalnie.</span><span class="sxs-lookup"><span data-stu-id="791eb-130">At the end of the enumeration, the `DCStartComplete` event is raised to notify the controller that data collection terminated normally.</span></span>  
  
### <a name="end-rundown"></a><span data-ttu-id="791eb-131">Uwalnianie zakończenia</span><span class="sxs-lookup"><span data-stu-id="791eb-131">End Rundown</span></span>  
 <span data-ttu-id="791eb-132">Uwalniania zakończenia jest wyzwalane, gdy włączono rejestrowanie w obszarze dostawcy stert z `EndRundownKeyword` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="791eb-132">An end rundown is triggered when logging under the rundown provider is enabled with the `EndRundownKeyword` keyword.</span></span> <span data-ttu-id="791eb-133">Końcowy stert zatrzymuje profilowanie na proces, która kontynuuje wykonywanie.</span><span class="sxs-lookup"><span data-stu-id="791eb-133">End rundown stops profiling on a process that continues to execute.</span></span> <span data-ttu-id="791eb-134">`DCEnd` Zdarzenia Przechwytywanie stanu systemu, gdy profilowania jest zatrzymana.</span><span class="sxs-lookup"><span data-stu-id="791eb-134">The `DCEnd` events capture the state of the system when profiling is stopped.</span></span>  
  
 <span data-ttu-id="791eb-135">Przed rozpoczęciem wyliczania `DCEndInit` zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="791eb-135">Before the start of the enumeration, the `DCEndInit` event is raised.</span></span> <span data-ttu-id="791eb-136">Na koniec wyliczenia `DCEndComplete` zdarzenie jest wywoływane w celu powiadomienia klienta, która zbierania danych zwykle przerwana.</span><span class="sxs-lookup"><span data-stu-id="791eb-136">At the end of the enumeration, the `DCEndComplete` event is raised to notify the consumer that data collection terminated normally.</span></span> <span data-ttu-id="791eb-137">Uruchom stert i uwalniania celu są używane przede wszystkim do rozpoznawania zarządzanego symbolu.</span><span class="sxs-lookup"><span data-stu-id="791eb-137">Start rundown and end rundown are primarily used for managed symbol resolution.</span></span> <span data-ttu-id="791eb-138">Start uwalniania może dostarczyć informacji zakres adresów dla metod, które już zostały skompilowane JIT zanim sesja profilowania został uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="791eb-138">Start rundown can provide address range information for methods that were already JIT-compiled before the profiling session was started.</span></span> <span data-ttu-id="791eb-139">Uwalnianie zakończenia może dostarczyć informacji zakres adresów dla wszystkich metod, które zostały skompilowane JIT podczas profilowania ma zostać wyłączone.</span><span class="sxs-lookup"><span data-stu-id="791eb-139">End rundown can provide address range information for all methods that have been JIT-compiled when profiling is about to be turned off.</span></span>  
  
 <span data-ttu-id="791eb-140">Uwalnianie end nie odbywa się automatycznie po zatrzymaniu sesji profilowania.</span><span class="sxs-lookup"><span data-stu-id="791eb-140">End rundown does not happen automatically when a profiling session is stopped.</span></span> <span data-ttu-id="791eb-141">Zamiast tego narzędzia, który chce rozpoznawać zarządzanego symbolu ma jawnie wywołać sesji stert dostawcy CLR z `EndRundownKeyword` — słowo kluczowe włączone tuż przed profilowania jest zatrzymana.</span><span class="sxs-lookup"><span data-stu-id="791eb-141">Instead, a tool that is seeking to perform managed symbol resolution has to explicitly invoke a CLR rundown provider session with the `EndRundownKeyword` keyword enabled, just before profiling is stopped.</span></span>  
  
 <span data-ttu-id="791eb-142">Mimo że uwalniania rozpoczęcia lub zakończenia uwalniania może dostarczyć metody adres zakresu informacji rozpoznanie zarządzanego symbolu, zaleca się używanie `EndRundownKeyword` — słowo kluczowe (które dostaw `DCEnd` zdarzeń) zamiast `StartRundownKeyword` — słowo kluczowe (który dostarcza `DCStart` zdarzeń).</span><span class="sxs-lookup"><span data-stu-id="791eb-142">Although either start rundown or end rundown can provide method address range information for managed symbol resolution, we recommend that you use the `EndRundownKeyword` keyword (which supplies `DCEnd` events) instead of the `StartRundownKeyword` keyword (which supplies `DCStart` events).</span></span> <span data-ttu-id="791eb-143">Przy użyciu `StartRundownKeyword` powoduje, że uwalniania do mają miejsce podczas sesji profilowania, która może przeszkadzać PROFILOWANEGO scenariusza.</span><span class="sxs-lookup"><span data-stu-id="791eb-143">Using `StartRundownKeyword` causes the rundown to happen during the profiling session, which may disturb the profiled scenario.</span></span>  
  
## <a name="etw-data-collection-using-runtime-and-rundown-providers"></a><span data-ttu-id="791eb-144">Zbieranie danych funkcji ETW za pomocą środowiska uruchomieniowego i dostawców stert</span><span class="sxs-lookup"><span data-stu-id="791eb-144">ETW Data Collection Using Runtime and Rundown Providers</span></span>  
 <span data-ttu-id="791eb-145">W poniższym przykładzie pokazano sposób użycia dostawcy stert CLR w sposób umożliwiający rozpoznawanie symboli procesów zarządzanych przy minimalnym wpływie, niezależnie od tego, czy procesy początku ani na końcu wewnątrz lub na zewnątrz PROFILOWANEGO okna.</span><span class="sxs-lookup"><span data-stu-id="791eb-145">The following example demonstrates how to use the CLR rundown provider in a way that allows symbol resolution of managed processes with minimal impact, regardless of whether the processes start or end inside or outside the profiled window.</span></span>  
  
1.  <span data-ttu-id="791eb-146">Włącz rejestrowanie funkcji ETW przy użyciu dostawcy środowiska uruchomieniowego CLR:</span><span class="sxs-lookup"><span data-stu-id="791eb-146">Turn on ETW logging by using the CLR runtime provider:</span></span>  
  
    ```  
    xperf -start clr -on e13c0d23-ccbc-4e12-931b-d9cc2eee27e4:0x1CCBD:0x5 -f clr1.etl      
    ```  
  
     <span data-ttu-id="791eb-147">Dziennika są zapisywane do pliku clr1.etl.</span><span class="sxs-lookup"><span data-stu-id="791eb-147">The log will be saved to the clr1.etl file.</span></span>  
  
2.  <span data-ttu-id="791eb-148">Aby zatrzymać profilowanie podczas procesu kontynuuje wykonywanie, uruchom stert dostawcy, aby przechwycić `DCEnd` zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="791eb-148">To stop profiling while the process continues to execute, start the rundown provider to capture the `DCEnd` events:</span></span>  
  
    ```  
    xperf -start clrRundown -on A669021C-C450-4609-A035-5AF59AF4DF18:0xB8:0x5 -f clr2.etl      
    ```  
  
     <span data-ttu-id="791eb-149">Umożliwia to kolekcja `DCEnd` zdarzeń, aby rozpocząć sesję zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="791eb-149">This enables the collection of `DCEnd` events to start a rundown session.</span></span> <span data-ttu-id="791eb-150">Może być konieczne odczekanie 30 do 60 sekund dla wszystkich zdarzeń mają być zbierane.</span><span class="sxs-lookup"><span data-stu-id="791eb-150">You may need to wait 30 to 60 seconds for all events to be collected.</span></span> <span data-ttu-id="791eb-151">Dziennika są zapisywane do pliku clr1.et2.</span><span class="sxs-lookup"><span data-stu-id="791eb-151">The log will be saved to the clr1.et2 file.</span></span>  
  
3.  <span data-ttu-id="791eb-152">Wyłącz wszystkie profilowania ETW:</span><span class="sxs-lookup"><span data-stu-id="791eb-152">Turn off all ETW profiling:</span></span>  
  
    ```  
    xperf -stop clrRundown   
    xperf -stop clr  
    ```  
  
4.  <span data-ttu-id="791eb-153">Scalanie profili można utworzyć jeden plik dziennika:</span><span class="sxs-lookup"><span data-stu-id="791eb-153">Merge the profiles to create one log file:</span></span>  
  
    ```  
    xperf -merge -d clr1.etl clr2.etl merged.etl  
    ```  
  
     <span data-ttu-id="791eb-154">Plik merged.etl będzie zawierał zdarzenia środowiska uruchomieniowego i sesje stert dostawcy.</span><span class="sxs-lookup"><span data-stu-id="791eb-154">The merged.etl file will contain the events from the runtime and the rundown provider sessions.</span></span>  
  
 <span data-ttu-id="791eb-155">To narzędzie można wykonać kroki 2 i 3 (uruchamianie zamknięcia sesji i następnie Kończenie profilowania) zamiast natychmiast wyłączenie profilowania, gdy użytkownik żądań profilowanie, aby zostać zatrzymane.</span><span class="sxs-lookup"><span data-stu-id="791eb-155">A tool can execute steps 2 and 3 (starting a rundown session and then terminating profiling) instead of immediately turning off profiling when a user requests profiling to be stopped.</span></span> <span data-ttu-id="791eb-156">Narzędzia można również wykonać krok 4.</span><span class="sxs-lookup"><span data-stu-id="791eb-156">A tool can also execute step 4.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="791eb-157">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="791eb-157">See Also</span></span>  
 [<span data-ttu-id="791eb-158">Zdarzenia ETW w środowisko uruchomieniowe języka wspólnego</span><span class="sxs-lookup"><span data-stu-id="791eb-158">ETW Events in the Common Language Runtime</span></span>](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)
