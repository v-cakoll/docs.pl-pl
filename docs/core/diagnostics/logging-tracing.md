---
title: Rejestrowanie i śledzenie — .NET Core
description: Wprowadzenie do rejestrowania i śledzenia w programie .NET Core.
ms.date: 08/05/2019
ms.openlocfilehash: 392b88c9ea3c31c919a605ac0a5c886f7d63f79a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714420"
---
# <a name="net-core-logging-and-tracing"></a><span data-ttu-id="f52d8-103">Rejestrowanie i śledzenie w programie .NET Core</span><span class="sxs-lookup"><span data-stu-id="f52d8-103">.NET Core logging and tracing</span></span>

<span data-ttu-id="f52d8-104">Rejestrowanie i śledzenie są bardzo dwie nazwy dla tej samej techniki.</span><span class="sxs-lookup"><span data-stu-id="f52d8-104">Logging and tracing are really two names for the same technique.</span></span> <span data-ttu-id="f52d8-105">Prosta technika została użyta od momentu wczesnego dnia komputerów.</span><span class="sxs-lookup"><span data-stu-id="f52d8-105">The simple technique has been used since the early days of computers.</span></span> <span data-ttu-id="f52d8-106">Po prostu obejmuje instrumentację aplikacji w celu zapisania danych wyjściowych do późniejszego wykorzystania.</span><span class="sxs-lookup"><span data-stu-id="f52d8-106">It simply involves instrumenting an application to write output to be consumed later.</span></span>

## <a name="reasons-to-use-logging-and-tracing"></a><span data-ttu-id="f52d8-107">Przyczyny używania rejestrowania i śledzenia</span><span class="sxs-lookup"><span data-stu-id="f52d8-107">Reasons to use logging and tracing</span></span>

<span data-ttu-id="f52d8-108">Ta prosta technika jest Surprisingly zaawansowana.</span><span class="sxs-lookup"><span data-stu-id="f52d8-108">This simple technique is surprisingly powerful.</span></span> <span data-ttu-id="f52d8-109">Może być używana w sytuacjach, w których debuger kończy się niepowodzeniem:</span><span class="sxs-lookup"><span data-stu-id="f52d8-109">It can be used in situations where a debugger fails:</span></span>

- <span data-ttu-id="f52d8-110">Problemy występujące w długim okresie czasu mogą być trudne do debugowania przy użyciu tradycyjnego debugera.</span><span class="sxs-lookup"><span data-stu-id="f52d8-110">Issues occurring over long periods of time, can be difficult to debug with a traditional debugger.</span></span> <span data-ttu-id="f52d8-111">Dzienniki pozwalają na szczegółowe przeglądy po dłuższym okresie.</span><span class="sxs-lookup"><span data-stu-id="f52d8-111">Logs allow for detailed post-mortem review spanning long periods of time.</span></span> <span data-ttu-id="f52d8-112">Z kolei debugery są ograniczone do analizy w czasie rzeczywistym.</span><span class="sxs-lookup"><span data-stu-id="f52d8-112">In contrast, debuggers are constrained to real-time analysis.</span></span>
- <span data-ttu-id="f52d8-113">Aplikacje wielowątkowe i aplikacje rozproszone często są trudne do debugowania.</span><span class="sxs-lookup"><span data-stu-id="f52d8-113">Multi-threaded applications and distributed applications are often difficult to debug.</span></span>  <span data-ttu-id="f52d8-114">Dołączanie debugera powoduje modyfikację zachowań.</span><span class="sxs-lookup"><span data-stu-id="f52d8-114">Attaching a debugger tends to modify behaviors.</span></span> <span data-ttu-id="f52d8-115">Szczegółowe dzienniki można analizować w miarę potrzeby, aby zrozumieć złożone systemy.</span><span class="sxs-lookup"><span data-stu-id="f52d8-115">Detailed logs can be analyzed as needed to understand complex systems.</span></span>
- <span data-ttu-id="f52d8-116">Problemy w aplikacjach rozproszonych mogą powstać w wyniku złożonej interakcji między wieloma składnikami i może nie być uzasadnione, aby podłączyć debuger do każdej części systemu.</span><span class="sxs-lookup"><span data-stu-id="f52d8-116">Issues in distributed applications may arise from a complex interaction between many components and it may not be reasonable to connect a debugger to every part of the system.</span></span>
- <span data-ttu-id="f52d8-117">Nie należy zawiesić wielu usług.</span><span class="sxs-lookup"><span data-stu-id="f52d8-117">Many services shouldn't be stalled.</span></span> <span data-ttu-id="f52d8-118">Dołączanie debugera często powoduje błędy limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="f52d8-118">Attaching a debugger often causes timeout failures.</span></span>
- <span data-ttu-id="f52d8-119">Problemy nie są zawsze obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="f52d8-119">Issues aren't always foreseen.</span></span> <span data-ttu-id="f52d8-120">Rejestrowanie i śledzenie zostało zaprojektowane z myślą o niskim obciążeniu, dzięki czemu program może zawsze rejestrować się w przypadku wystąpienia problemu.</span><span class="sxs-lookup"><span data-stu-id="f52d8-120">Logging and tracing are designed for low overhead so that programs can always be recording in case an issue occurs.</span></span>

## <a name="net-core-apis"></a><span data-ttu-id="f52d8-121">Interfejsy API platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="f52d8-121">.NET Core APIs</span></span>

### <a name="print-style-apis"></a><span data-ttu-id="f52d8-122">Interfejsy API stylu drukowania</span><span class="sxs-lookup"><span data-stu-id="f52d8-122">Print style APIs</span></span>

<span data-ttu-id="f52d8-123">Klasy <xref:System.Console?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace?displayProperty=nameWithType>i <xref:System.Diagnostics.Debug?displayProperty=nameWithType> każdy oferują podobne interfejsy API stylu drukowania wygodne do rejestrowania.</span><span class="sxs-lookup"><span data-stu-id="f52d8-123">The <xref:System.Console?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace?displayProperty=nameWithType>, and <xref:System.Diagnostics.Debug?displayProperty=nameWithType> classes each provide similar print style APIs convenient for logging.</span></span>

<span data-ttu-id="f52d8-124">Wybór interfejsu API drukowania stylu do użycia.</span><span class="sxs-lookup"><span data-stu-id="f52d8-124">The choice of which print style API to use is up to you.</span></span> <span data-ttu-id="f52d8-125">Kluczowe różnice są następujące:</span><span class="sxs-lookup"><span data-stu-id="f52d8-125">The key differences are:</span></span>

- <xref:System.Console?displayProperty=nameWithType>
  - <span data-ttu-id="f52d8-126">Zawsze włączone i zawsze zapisuje się w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="f52d8-126">Always enabled and always writes to the console.</span></span>
  - <span data-ttu-id="f52d8-127">Przydatne w przypadku informacji, które mogą być wymagane przez klienta w wersji.</span><span class="sxs-lookup"><span data-stu-id="f52d8-127">Useful for information that your customer may need to see in the release.</span></span>
  - <span data-ttu-id="f52d8-128">Ponieważ jest to najprostszy sposób, często jest używany do tymczasowego debugowania ad hoc.</span><span class="sxs-lookup"><span data-stu-id="f52d8-128">Because it's the simplest approach, it's often used for ad-hoc temporary debugging.</span></span> <span data-ttu-id="f52d8-129">Ten kod debugowania często nigdy nie jest sprawdzany w kontroli źródła.</span><span class="sxs-lookup"><span data-stu-id="f52d8-129">This debug code is often never checked in to source control.</span></span>
- <xref:System.Diagnostics.Trace?displayProperty=nameWithType>
  - <span data-ttu-id="f52d8-130">Włączone tylko wtedy, gdy `TRACE` jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="f52d8-130">Only enabled when `TRACE` is defined.</span></span>
  - <span data-ttu-id="f52d8-131">Domyślnie <xref:System.Diagnostics.DefaultTraceListener>zapisu do dołączonego <xref:System.Diagnostics.Trace.Listeners>.</span><span class="sxs-lookup"><span data-stu-id="f52d8-131">Writes to attached <xref:System.Diagnostics.Trace.Listeners>, by default the <xref:System.Diagnostics.DefaultTraceListener>.</span></span>
  - <span data-ttu-id="f52d8-132">Użyj tego interfejsu API podczas tworzenia dzienników, które będą włączone w większości kompilacji.</span><span class="sxs-lookup"><span data-stu-id="f52d8-132">Use this API when creating logs that will be enabled in most builds.</span></span>
- <xref:System.Diagnostics.Debug?displayProperty=nameWithType>
  - <span data-ttu-id="f52d8-133">Włączone tylko wtedy, gdy `DEBUG` jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="f52d8-133">Only enabled when `DEBUG` is defined.</span></span>
  - <span data-ttu-id="f52d8-134">Zapisuje do dołączonego debugera.</span><span class="sxs-lookup"><span data-stu-id="f52d8-134">Writes to an attached debugger.</span></span>
  - <span data-ttu-id="f52d8-135">W przypadku `*nix` zapisów do stderr, jeśli `COMPlus_DebugWriteToStdErr` jest ustawiony.</span><span class="sxs-lookup"><span data-stu-id="f52d8-135">On `*nix` writes to stderr if `COMPlus_DebugWriteToStdErr` is set.</span></span>
  - <span data-ttu-id="f52d8-136">Użyj tego interfejsu API podczas tworzenia dzienników, które będą włączone tylko w kompilacjach debugowania.</span><span class="sxs-lookup"><span data-stu-id="f52d8-136">Use this API when creating logs that will be enabled only in debug builds.</span></span>

### <a name="logging-events"></a><span data-ttu-id="f52d8-137">Rejestrowanie zdarzeń</span><span class="sxs-lookup"><span data-stu-id="f52d8-137">Logging events</span></span>

<span data-ttu-id="f52d8-138">Poniższe interfejsy API są bardziej zorientowane na zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f52d8-138">The following APIs are more event oriented.</span></span> <span data-ttu-id="f52d8-139">Zamiast rejestrowania prostych ciągów rejestruje obiekty zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f52d8-139">Rather than logging simple strings they log event objects.</span></span>

- <xref:System.Diagnostics.Tracing.EventSource?displayProperty=nameWithType>
  - <span data-ttu-id="f52d8-140">EventSource jest podstawowym głównym interfejsem API śledzenia programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f52d8-140">EventSource is the primary root .NET Core tracing API.</span></span>
  - <span data-ttu-id="f52d8-141">Dostępne we wszystkich wersjach .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="f52d8-141">Available in all .NET Standard versions.</span></span>
  - <span data-ttu-id="f52d8-142">Umożliwia tylko śledzenie obiektów, które można serializować.</span><span class="sxs-lookup"><span data-stu-id="f52d8-142">Only allows tracing serializable objects.</span></span>
  - <span data-ttu-id="f52d8-143">Zapisuje dane w podłączonych [detektorach zdarzeń](xref:System.Diagnostics.Tracing.EventListener).</span><span class="sxs-lookup"><span data-stu-id="f52d8-143">Writes to the attached [event listeners](xref:System.Diagnostics.Tracing.EventListener).</span></span>
  - <span data-ttu-id="f52d8-144">Platforma .NET Core udostępnia detektory dla:</span><span class="sxs-lookup"><span data-stu-id="f52d8-144">.NET Core provides listeners for:</span></span>
    - <span data-ttu-id="f52d8-145">EventPipe platformy .NET Core na wszystkich platformach</span><span class="sxs-lookup"><span data-stu-id="f52d8-145">.NET Core's EventPipe on all platforms</span></span>
    - [<span data-ttu-id="f52d8-146">Śledzenie zdarzeń systemu Windows (ETW)</span><span class="sxs-lookup"><span data-stu-id="f52d8-146">Event Tracing for Windows (ETW)</span></span>](/windows/win32/etw/event-tracing-portal)
    - [<span data-ttu-id="f52d8-147">LTTng — struktura śledzenia dla systemu Linux</span><span class="sxs-lookup"><span data-stu-id="f52d8-147">LTTng tracing framework for Linux</span></span>](https://lttng.org/)

- <xref:System.Diagnostics.DiagnosticSource?displayProperty=nameWithType>
  - <span data-ttu-id="f52d8-148">Zawarte w oprogramowaniu .NET Core i jako [pakiet NuGet](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource) dla .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f52d8-148">Included in .NET Core and as a [NuGet package](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource) for .NET Framework.</span></span>
  - <span data-ttu-id="f52d8-149">Umożliwia śledzenie w procesie obiektów, które nie są możliwe do serializacji.</span><span class="sxs-lookup"><span data-stu-id="f52d8-149">Allows in-process tracing of non-serializable objects.</span></span>
  - <span data-ttu-id="f52d8-150">Zawiera mostek umożliwiający Zapisywanie wybranych pól zarejestrowanych obiektów w <xref:System.Diagnostics.Tracing.EventSource>.</span><span class="sxs-lookup"><span data-stu-id="f52d8-150">Includes a bridge to allow selected fields of logged objects to be written to an <xref:System.Diagnostics.Tracing.EventSource>.</span></span>

- <xref:System.Diagnostics.Activity?displayProperty=nameWithType>
  - <span data-ttu-id="f52d8-151">Przedstawia ostateczny sposób identyfikowania komunikatów dziennika pochodzących z określonego działania lub transakcji.</span><span class="sxs-lookup"><span data-stu-id="f52d8-151">Provides a definitive way to identify log messages resulting from a specific activity or transaction.</span></span> <span data-ttu-id="f52d8-152">Ten obiekt może służyć do skorelowania dzienników w różnych usługach.</span><span class="sxs-lookup"><span data-stu-id="f52d8-152">This object can be used to correlate logs across different services.</span></span>

- <xref:System.Diagnostics.EventLog?displayProperty=nameWithType>
  - <span data-ttu-id="f52d8-153">Tylko system Windows.</span><span class="sxs-lookup"><span data-stu-id="f52d8-153">Windows only.</span></span>
  - <span data-ttu-id="f52d8-154">Zapisuje komunikaty w dzienniku zdarzeń systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="f52d8-154">Writes messages to the Windows Event Log.</span></span>
  - <span data-ttu-id="f52d8-155">Administratorzy systemu oczekują krytycznych komunikatów o błędach aplikacji w dzienniku zdarzeń systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="f52d8-155">System administrators expect fatal application error messages to appear in the Windows Event Log.</span></span>

## <a name="ilogger-and-logging-frameworks"></a><span data-ttu-id="f52d8-156">ILogger i struktury rejestrowania</span><span class="sxs-lookup"><span data-stu-id="f52d8-156">ILogger and logging frameworks</span></span>

<span data-ttu-id="f52d8-157">Interfejsy API niskiego poziomu mogą nie być właściwym wyborem dla potrzeb rejestrowania.</span><span class="sxs-lookup"><span data-stu-id="f52d8-157">The low-level APIs may not be the right choice for your logging needs.</span></span> <span data-ttu-id="f52d8-158">Warto rozważyć strukturę rejestrowania.</span><span class="sxs-lookup"><span data-stu-id="f52d8-158">You may want to consider a logging framework.</span></span>

<span data-ttu-id="f52d8-159">Interfejs <xref:Microsoft.Extensions.Logging.ILogger> został użyty do utworzenia wspólnego interfejsu rejestrowania, w którym rejestratory mogą być wstawiane przez iniekcję zależności.</span><span class="sxs-lookup"><span data-stu-id="f52d8-159">The <xref:Microsoft.Extensions.Logging.ILogger> interface has been used to create a common logging interface where the loggers can be inserted through dependency injection.</span></span>

<span data-ttu-id="f52d8-160">Na przykład, aby umożliwić wybranie najlepszego wyboru dla aplikacji `ASP.NET` oferuje obsługę wybranych platform wbudowanych i innych firm:</span><span class="sxs-lookup"><span data-stu-id="f52d8-160">For instance, to allow you to make the best choice for your application `ASP.NET` offers support for a selection of built-in and third-party frameworks:</span></span>

- [<span data-ttu-id="f52d8-161">ASP.NET wbudowane dostawcy rejestrowania</span><span class="sxs-lookup"><span data-stu-id="f52d8-161">ASP.NET built in logging providers</span></span>](/aspnet/core/fundamentals/logging/#built-in-logging-providers)
- [<span data-ttu-id="f52d8-162">ASP.NET dostawców rejestrowania innych firm</span><span class="sxs-lookup"><span data-stu-id="f52d8-162">ASP.NET Third-party logging providers</span></span>](/aspnet/core/fundamentals/logging/#third-party-logging-providers)

## <a name="logging-related-references"></a><span data-ttu-id="f52d8-163">Rejestrowanie powiązanych odwołań</span><span class="sxs-lookup"><span data-stu-id="f52d8-163">Logging related references</span></span>

- [<span data-ttu-id="f52d8-164">Instrukcje: Kompilowanie warunkowe ze śledzeniem i debugowaniem</span><span class="sxs-lookup"><span data-stu-id="f52d8-164">How to: Compile Conditionally with Trace and Debug</span></span>](../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)

- [<span data-ttu-id="f52d8-165">Instrukcje: Dodawanie instrukcji śledzenia do kodu aplikacji</span><span class="sxs-lookup"><span data-stu-id="f52d8-165">How to: Add Trace Statements to Application Code</span></span>](../../framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)

- <span data-ttu-id="f52d8-166">[Rejestrowanie ASP.NET](/aspnet/core/fundamentals/logging) zawiera omówienie technik rejestrowania, które obsługuje.</span><span class="sxs-lookup"><span data-stu-id="f52d8-166">[ASP.NET Logging](/aspnet/core/fundamentals/logging) provides an overview of the logging techniques it supports.</span></span>

- <span data-ttu-id="f52d8-167">Interpolacja ciągów może uprościć pisanie kodu rejestrowania. [ C# ](../../csharp/language-reference/tokens/interpolated.md)</span><span class="sxs-lookup"><span data-stu-id="f52d8-167">[C# String Interpolation](../../csharp/language-reference/tokens/interpolated.md) can simplify writing logging code.</span></span>

- <span data-ttu-id="f52d8-168">Właściwość <xref:System.Exception.Message?displayProperty=nameWithType> jest przydatna do rejestrowania wyjątków.</span><span class="sxs-lookup"><span data-stu-id="f52d8-168">The <xref:System.Exception.Message?displayProperty=nameWithType> property is useful for logging exceptions.</span></span>

- <span data-ttu-id="f52d8-169">Klasa <xref:System.Diagnostics.StackTrace?displayProperty=nameWithType> może być przydatna do dostarczania informacji o stosie w dziennikach.</span><span class="sxs-lookup"><span data-stu-id="f52d8-169">The <xref:System.Diagnostics.StackTrace?displayProperty=nameWithType> class can be useful to provide stack info in your logs.</span></span>

## <a name="performance-considerations"></a><span data-ttu-id="f52d8-170">Zagadnienia dotyczące wydajności</span><span class="sxs-lookup"><span data-stu-id="f52d8-170">Performance considerations</span></span>

<span data-ttu-id="f52d8-171">Formatowanie ciągu może mieć zauważalny czas przetwarzania procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="f52d8-171">String formatting can take noticeable CPU processing time.</span></span>

<span data-ttu-id="f52d8-172">W przypadku aplikacji o krytycznym znaczeniu zaleca się:</span><span class="sxs-lookup"><span data-stu-id="f52d8-172">In performance critical applications, it's recommended that you:</span></span>

- <span data-ttu-id="f52d8-173">Unikaj wielu rejestracji, gdy nikt nie nasłuchuje.</span><span class="sxs-lookup"><span data-stu-id="f52d8-173">Avoid lots of logging when no one is listening.</span></span> <span data-ttu-id="f52d8-174">Unikaj konstruowania kosztownych komunikatów rejestrowania, sprawdzając, czy rejestrowanie jest włączone jako pierwsze.</span><span class="sxs-lookup"><span data-stu-id="f52d8-174">Avoid constructing costly logging messages by checking if logging is enabled first.</span></span>
- <span data-ttu-id="f52d8-175">Rejestruj tylko to, co jest przydatne.</span><span class="sxs-lookup"><span data-stu-id="f52d8-175">Only log what's useful.</span></span>
- <span data-ttu-id="f52d8-176">Odłóż ozdobne formatowanie do etapu analizy.</span><span class="sxs-lookup"><span data-stu-id="f52d8-176">Defer fancy formatting to the analysis stage.</span></span>
