---
title: Rejestrowanie i śledzenie — .NET Core
description: Wprowadzenie do rejestrowania i śledzenia .NET Core.
ms.date: 08/05/2019
ms.openlocfilehash: 392b88c9ea3c31c919a605ac0a5c886f7d63f79a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714420"
---
# <a name="net-core-logging-and-tracing"></a><span data-ttu-id="33a92-103">Rejestrowanie i śledzenie programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="33a92-103">.NET Core logging and tracing</span></span>

<span data-ttu-id="33a92-104">Rejestrowanie i śledzenie są naprawdę dwie nazwy dla tej samej techniki.</span><span class="sxs-lookup"><span data-stu-id="33a92-104">Logging and tracing are really two names for the same technique.</span></span> <span data-ttu-id="33a92-105">Prosta technika jest stosowana od wczesnych dni komputerów.</span><span class="sxs-lookup"><span data-stu-id="33a92-105">The simple technique has been used since the early days of computers.</span></span> <span data-ttu-id="33a92-106">Obejmuje po prostu instrumenting aplikacji do zapisu danych wyjściowych do zużycia później.</span><span class="sxs-lookup"><span data-stu-id="33a92-106">It simply involves instrumenting an application to write output to be consumed later.</span></span>

## <a name="reasons-to-use-logging-and-tracing"></a><span data-ttu-id="33a92-107">Powody używania rejestrowania i śledzenia</span><span class="sxs-lookup"><span data-stu-id="33a92-107">Reasons to use logging and tracing</span></span>

<span data-ttu-id="33a92-108">Ta prosta technika jest zaskakująco potężna.</span><span class="sxs-lookup"><span data-stu-id="33a92-108">This simple technique is surprisingly powerful.</span></span> <span data-ttu-id="33a92-109">Może być używany w sytuacjach, gdy debuger nie powiedzie się:</span><span class="sxs-lookup"><span data-stu-id="33a92-109">It can be used in situations where a debugger fails:</span></span>

- <span data-ttu-id="33a92-110">Problemy występujące przez długi czas, może być trudne do debugowania z tradycyjnym debugerem.</span><span class="sxs-lookup"><span data-stu-id="33a92-110">Issues occurring over long periods of time, can be difficult to debug with a traditional debugger.</span></span> <span data-ttu-id="33a92-111">Dzienniki pozwalają na szczegółową kontrolę pośmiertną obejmującą długie okresy czasu.</span><span class="sxs-lookup"><span data-stu-id="33a92-111">Logs allow for detailed post-mortem review spanning long periods of time.</span></span> <span data-ttu-id="33a92-112">Natomiast debuggery są ograniczone do analizy w czasie rzeczywistym.</span><span class="sxs-lookup"><span data-stu-id="33a92-112">In contrast, debuggers are constrained to real-time analysis.</span></span>
- <span data-ttu-id="33a92-113">Aplikacje wielowątkowe i aplikacje rozproszone są często trudne do debugowania.</span><span class="sxs-lookup"><span data-stu-id="33a92-113">Multi-threaded applications and distributed applications are often difficult to debug.</span></span>  <span data-ttu-id="33a92-114">Dołączanie debugera ma tendencję do modyfikowania zachowań.</span><span class="sxs-lookup"><span data-stu-id="33a92-114">Attaching a debugger tends to modify behaviors.</span></span> <span data-ttu-id="33a92-115">Szczegółowe dzienniki mogą być analizowane w razie potrzeby, aby zrozumieć złożone systemy.</span><span class="sxs-lookup"><span data-stu-id="33a92-115">Detailed logs can be analyzed as needed to understand complex systems.</span></span>
- <span data-ttu-id="33a92-116">Problemy w aplikacjach rozproszonych mogą wynikać ze złożonej interakcji między wieloma składnikami i może nie być uzasadnione łączenie debugera z każdą częścią systemu.</span><span class="sxs-lookup"><span data-stu-id="33a92-116">Issues in distributed applications may arise from a complex interaction between many components and it may not be reasonable to connect a debugger to every part of the system.</span></span>
- <span data-ttu-id="33a92-117">Wiele usług nie powinno być wstrzymanych.</span><span class="sxs-lookup"><span data-stu-id="33a92-117">Many services shouldn't be stalled.</span></span> <span data-ttu-id="33a92-118">Dołączanie debugera często powoduje błędy timeout.</span><span class="sxs-lookup"><span data-stu-id="33a92-118">Attaching a debugger often causes timeout failures.</span></span>
- <span data-ttu-id="33a92-119">Problemy nie zawsze są przewidziane.</span><span class="sxs-lookup"><span data-stu-id="33a92-119">Issues aren't always foreseen.</span></span> <span data-ttu-id="33a92-120">Rejestrowanie i śledzenie są przeznaczone dla niskiego narzutów, dzięki czemu programy zawsze mogą nagrywać w przypadku wystąpienia problemu.</span><span class="sxs-lookup"><span data-stu-id="33a92-120">Logging and tracing are designed for low overhead so that programs can always be recording in case an issue occurs.</span></span>

## <a name="net-core-apis"></a><span data-ttu-id="33a92-121">Interfejsy API rdzenia .NET</span><span class="sxs-lookup"><span data-stu-id="33a92-121">.NET Core APIs</span></span>

### <a name="print-style-apis"></a><span data-ttu-id="33a92-122">Interfejsy API stylu drukowania</span><span class="sxs-lookup"><span data-stu-id="33a92-122">Print style APIs</span></span>

<span data-ttu-id="33a92-123"><xref:System.Console?displayProperty=nameWithType>Interfejsy <xref:System.Diagnostics.Trace?displayProperty=nameWithType>API , i <xref:System.Diagnostics.Debug?displayProperty=nameWithType> klasy zapewniają podobne interfejsy API stylu drukowania wygodne do rejestrowania.</span><span class="sxs-lookup"><span data-stu-id="33a92-123">The <xref:System.Console?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace?displayProperty=nameWithType>, and <xref:System.Diagnostics.Debug?displayProperty=nameWithType> classes each provide similar print style APIs convenient for logging.</span></span>

<span data-ttu-id="33a92-124">Wybór interfejsu API stylu drukowania zależy od Ciebie.</span><span class="sxs-lookup"><span data-stu-id="33a92-124">The choice of which print style API to use is up to you.</span></span> <span data-ttu-id="33a92-125">Kluczowe różnice to:</span><span class="sxs-lookup"><span data-stu-id="33a92-125">The key differences are:</span></span>

- <xref:System.Console?displayProperty=nameWithType>
  - <span data-ttu-id="33a92-126">Zawsze włączony i zawsze zapisuje w konsoli.</span><span class="sxs-lookup"><span data-stu-id="33a92-126">Always enabled and always writes to the console.</span></span>
  - <span data-ttu-id="33a92-127">Przydatne informacje, które klient może być konieczne, aby zobaczyć w wydaniu.</span><span class="sxs-lookup"><span data-stu-id="33a92-127">Useful for information that your customer may need to see in the release.</span></span>
  - <span data-ttu-id="33a92-128">Ponieważ jest to najprostsze podejście, jest często używany do tymczasowego debugowania ad hoc.</span><span class="sxs-lookup"><span data-stu-id="33a92-128">Because it's the simplest approach, it's often used for ad-hoc temporary debugging.</span></span> <span data-ttu-id="33a92-129">Ten kod debugowania często nigdy nie jest zaewidencjonowany do kontroli źródła.</span><span class="sxs-lookup"><span data-stu-id="33a92-129">This debug code is often never checked in to source control.</span></span>
- <xref:System.Diagnostics.Trace?displayProperty=nameWithType>
  - <span data-ttu-id="33a92-130">Włączone tylko `TRACE` wtedy, gdy jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="33a92-130">Only enabled when `TRACE` is defined.</span></span>
  - <span data-ttu-id="33a92-131">Zapisuje do <xref:System.Diagnostics.Trace.Listeners>dołączonego , <xref:System.Diagnostics.DefaultTraceListener>domyślnie .</span><span class="sxs-lookup"><span data-stu-id="33a92-131">Writes to attached <xref:System.Diagnostics.Trace.Listeners>, by default the <xref:System.Diagnostics.DefaultTraceListener>.</span></span>
  - <span data-ttu-id="33a92-132">Użyj tego interfejsu API podczas tworzenia dzienników, które będą włączone w większości kompilacji.</span><span class="sxs-lookup"><span data-stu-id="33a92-132">Use this API when creating logs that will be enabled in most builds.</span></span>
- <xref:System.Diagnostics.Debug?displayProperty=nameWithType>
  - <span data-ttu-id="33a92-133">Włączone tylko `DEBUG` wtedy, gdy jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="33a92-133">Only enabled when `DEBUG` is defined.</span></span>
  - <span data-ttu-id="33a92-134">Zapisuje do dołączonego debugera.</span><span class="sxs-lookup"><span data-stu-id="33a92-134">Writes to an attached debugger.</span></span>
  - <span data-ttu-id="33a92-135">Na `*nix` zapisuje do stderr jeśli `COMPlus_DebugWriteToStdErr` jest ustawiona.</span><span class="sxs-lookup"><span data-stu-id="33a92-135">On `*nix` writes to stderr if `COMPlus_DebugWriteToStdErr` is set.</span></span>
  - <span data-ttu-id="33a92-136">Użyj tego interfejsu API podczas tworzenia dzienników, które będą włączone tylko w kompilacjach debugowania.</span><span class="sxs-lookup"><span data-stu-id="33a92-136">Use this API when creating logs that will be enabled only in debug builds.</span></span>

### <a name="logging-events"></a><span data-ttu-id="33a92-137">Rejestrowanie zdarzeń</span><span class="sxs-lookup"><span data-stu-id="33a92-137">Logging events</span></span>

<span data-ttu-id="33a92-138">Następujące interfejsy API są bardziej zorientowane na zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="33a92-138">The following APIs are more event oriented.</span></span> <span data-ttu-id="33a92-139">Zamiast rejestrowania prostych ciągów rejestrują obiekty zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="33a92-139">Rather than logging simple strings they log event objects.</span></span>

- <xref:System.Diagnostics.Tracing.EventSource?displayProperty=nameWithType>
  - <span data-ttu-id="33a92-140">EventSource jest głównym głównym interfejsem API śledzenia .NET Core.</span><span class="sxs-lookup"><span data-stu-id="33a92-140">EventSource is the primary root .NET Core tracing API.</span></span>
  - <span data-ttu-id="33a92-141">Dostępne we wszystkich wersjach .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="33a92-141">Available in all .NET Standard versions.</span></span>
  - <span data-ttu-id="33a92-142">Umożliwia tylko śledzenie obiektów serializable.</span><span class="sxs-lookup"><span data-stu-id="33a92-142">Only allows tracing serializable objects.</span></span>
  - <span data-ttu-id="33a92-143">Zapisuje do dołączonego [odbiornika zdarzeń](xref:System.Diagnostics.Tracing.EventListener).</span><span class="sxs-lookup"><span data-stu-id="33a92-143">Writes to the attached [event listeners](xref:System.Diagnostics.Tracing.EventListener).</span></span>
  - <span data-ttu-id="33a92-144">Program .NET Core udostępnia odbiorniki dla:</span><span class="sxs-lookup"><span data-stu-id="33a92-144">.NET Core provides listeners for:</span></span>
    - <span data-ttu-id="33a92-145">Usługa EventPipe programu .NET Core na wszystkich platformach</span><span class="sxs-lookup"><span data-stu-id="33a92-145">.NET Core's EventPipe on all platforms</span></span>
    - [<span data-ttu-id="33a92-146">Śledzenie zdarzeń dla systemu Windows (ETW)</span><span class="sxs-lookup"><span data-stu-id="33a92-146">Event Tracing for Windows (ETW)</span></span>](/windows/win32/etw/event-tracing-portal)
    - [<span data-ttu-id="33a92-147">Struktura śledzenia LTTng dla systemu Linux</span><span class="sxs-lookup"><span data-stu-id="33a92-147">LTTng tracing framework for Linux</span></span>](https://lttng.org/)

- <xref:System.Diagnostics.DiagnosticSource?displayProperty=nameWithType>
  - <span data-ttu-id="33a92-148">Zawarte w .NET Core i jako [pakiet NuGet](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource) dla .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="33a92-148">Included in .NET Core and as a [NuGet package](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource) for .NET Framework.</span></span>
  - <span data-ttu-id="33a92-149">Umożliwia śledzenie obiektów nieseryjnych w procesie.</span><span class="sxs-lookup"><span data-stu-id="33a92-149">Allows in-process tracing of non-serializable objects.</span></span>
  - <span data-ttu-id="33a92-150">Zawiera mostek umożliwiający zapisanie wybranych pól zarejestrowanych obiektów w pliku <xref:System.Diagnostics.Tracing.EventSource>.</span><span class="sxs-lookup"><span data-stu-id="33a92-150">Includes a bridge to allow selected fields of logged objects to be written to an <xref:System.Diagnostics.Tracing.EventSource>.</span></span>

- <xref:System.Diagnostics.Activity?displayProperty=nameWithType>
  - <span data-ttu-id="33a92-151">Zapewnia ostateczny sposób identyfikowania komunikatów dziennika wynikających z określonego działania lub transakcji.</span><span class="sxs-lookup"><span data-stu-id="33a92-151">Provides a definitive way to identify log messages resulting from a specific activity or transaction.</span></span> <span data-ttu-id="33a92-152">Ten obiekt może służyć do skorelowania dzienników w różnych usługach.</span><span class="sxs-lookup"><span data-stu-id="33a92-152">This object can be used to correlate logs across different services.</span></span>

- <xref:System.Diagnostics.EventLog?displayProperty=nameWithType>
  - <span data-ttu-id="33a92-153">Tylko w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="33a92-153">Windows only.</span></span>
  - <span data-ttu-id="33a92-154">Zapisuje wiadomości w dzienniku zdarzeń systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="33a92-154">Writes messages to the Windows Event Log.</span></span>
  - <span data-ttu-id="33a92-155">Administratorzy systemu oczekują, że w dzienniku zdarzeń systemu Windows pojawią się komunikaty o błędach aplikacji krytycznych.</span><span class="sxs-lookup"><span data-stu-id="33a92-155">System administrators expect fatal application error messages to appear in the Windows Event Log.</span></span>

## <a name="ilogger-and-logging-frameworks"></a><span data-ttu-id="33a92-156">Platformy ILogger i rejestrowania</span><span class="sxs-lookup"><span data-stu-id="33a92-156">ILogger and logging frameworks</span></span>

<span data-ttu-id="33a92-157">Interfejsy API niskiego poziomu mogą nie być właściwym wyborem dla potrzeb rejestrowania.</span><span class="sxs-lookup"><span data-stu-id="33a92-157">The low-level APIs may not be the right choice for your logging needs.</span></span> <span data-ttu-id="33a92-158">Warto rozważyć struktury rejestrowania.</span><span class="sxs-lookup"><span data-stu-id="33a92-158">You may want to consider a logging framework.</span></span>

<span data-ttu-id="33a92-159">Interfejs <xref:Microsoft.Extensions.Logging.ILogger> został użyty do utworzenia wspólnego interfejsu rejestrowania, w którym rejestratory mogą być wstawiane za pomocą iniekcji zależności.</span><span class="sxs-lookup"><span data-stu-id="33a92-159">The <xref:Microsoft.Extensions.Logging.ILogger> interface has been used to create a common logging interface where the loggers can be inserted through dependency injection.</span></span>

<span data-ttu-id="33a92-160">Na przykład, aby umożliwić dokonanie najlepszego `ASP.NET` wyboru dla aplikacji oferuje obsługę dla wyboru wbudowanych i innych platform:</span><span class="sxs-lookup"><span data-stu-id="33a92-160">For instance, to allow you to make the best choice for your application `ASP.NET` offers support for a selection of built-in and third-party frameworks:</span></span>

- [<span data-ttu-id="33a92-161">ASP.NET wbudowanych dostawców rejestrowania</span><span class="sxs-lookup"><span data-stu-id="33a92-161">ASP.NET built in logging providers</span></span>](/aspnet/core/fundamentals/logging/#built-in-logging-providers)
- [<span data-ttu-id="33a92-162">ASP.NET zewnętrzni dostawcy usług rejestrowania</span><span class="sxs-lookup"><span data-stu-id="33a92-162">ASP.NET Third-party logging providers</span></span>](/aspnet/core/fundamentals/logging/#third-party-logging-providers)

## <a name="logging-related-references"></a><span data-ttu-id="33a92-163">Rejestrowanie odwołań pokrewnych</span><span class="sxs-lookup"><span data-stu-id="33a92-163">Logging related references</span></span>

- [<span data-ttu-id="33a92-164">Instrukcje: Kompilowanie warunkowe ze śledzeniem i debugowaniem</span><span class="sxs-lookup"><span data-stu-id="33a92-164">How to: Compile Conditionally with Trace and Debug</span></span>](../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)

- [<span data-ttu-id="33a92-165">Porady: dodawanie instrukcji śledzenia do kodu aplikacji</span><span class="sxs-lookup"><span data-stu-id="33a92-165">How to: Add Trace Statements to Application Code</span></span>](../../framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)

- <span data-ttu-id="33a92-166">[ASP.NET rejestrowanie](/aspnet/core/fundamentals/logging) zawiera przegląd technik rejestrowania, które obsługuje.</span><span class="sxs-lookup"><span data-stu-id="33a92-166">[ASP.NET Logging](/aspnet/core/fundamentals/logging) provides an overview of the logging techniques it supports.</span></span>

- <span data-ttu-id="33a92-167">[Interpolacja ciągów C#](../../csharp/language-reference/tokens/interpolated.md) może uprościć pisanie kodu rejestrowania.</span><span class="sxs-lookup"><span data-stu-id="33a92-167">[C# String Interpolation](../../csharp/language-reference/tokens/interpolated.md) can simplify writing logging code.</span></span>

- <span data-ttu-id="33a92-168">Właściwość <xref:System.Exception.Message?displayProperty=nameWithType> jest przydatna do rejestrowania wyjątków.</span><span class="sxs-lookup"><span data-stu-id="33a92-168">The <xref:System.Exception.Message?displayProperty=nameWithType> property is useful for logging exceptions.</span></span>

- <span data-ttu-id="33a92-169">Klasa <xref:System.Diagnostics.StackTrace?displayProperty=nameWithType> może być przydatne do podania informacji stosu w dziennikach.</span><span class="sxs-lookup"><span data-stu-id="33a92-169">The <xref:System.Diagnostics.StackTrace?displayProperty=nameWithType> class can be useful to provide stack info in your logs.</span></span>

## <a name="performance-considerations"></a><span data-ttu-id="33a92-170">Zagadnienia dotyczące wydajności</span><span class="sxs-lookup"><span data-stu-id="33a92-170">Performance considerations</span></span>

<span data-ttu-id="33a92-171">Formatowanie ciągów może zająć zauważalny czas przetwarzania procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="33a92-171">String formatting can take noticeable CPU processing time.</span></span>

<span data-ttu-id="33a92-172">W aplikacjach o krytycznym znaczeniu dla wydajności zaleca się:</span><span class="sxs-lookup"><span data-stu-id="33a92-172">In performance critical applications, it's recommended that you:</span></span>

- <span data-ttu-id="33a92-173">Unikaj dużej ilości rejestrowania, gdy nikt nie słucha.</span><span class="sxs-lookup"><span data-stu-id="33a92-173">Avoid lots of logging when no one is listening.</span></span> <span data-ttu-id="33a92-174">Unikaj konstruowania kosztownych komunikatów rejestrowania, sprawdzając, czy rejestrowanie jest włączone jako pierwsze.</span><span class="sxs-lookup"><span data-stu-id="33a92-174">Avoid constructing costly logging messages by checking if logging is enabled first.</span></span>
- <span data-ttu-id="33a92-175">Rejestruj tylko to, co jest przydatne.</span><span class="sxs-lookup"><span data-stu-id="33a92-175">Only log what's useful.</span></span>
- <span data-ttu-id="33a92-176">Odroczyć fantazyjne formatowanie do etapu analizy.</span><span class="sxs-lookup"><span data-stu-id="33a92-176">Defer fancy formatting to the analysis stage.</span></span>
