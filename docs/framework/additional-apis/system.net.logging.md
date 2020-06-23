---
title: Klasa rejestrowania (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Logging
- System.Net.Logging.Associate
- System.Net.Logging.Enter
- System.Net.Logging.Exception
- System.Net.Logging.Exit
- System.Net.Logging.get_Http
- System.Net.Logging.get_On
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: ad85fdd41252ed147eb5fe1a9db029db046d720c
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990390"
---
# <a name="logging-class"></a><span data-ttu-id="f0319-102">Logging, klasa</span><span class="sxs-lookup"><span data-stu-id="f0319-102">Logging class</span></span>

<span data-ttu-id="f0319-103">Zapewnia funkcję rejestrowania śledzenia.</span><span class="sxs-lookup"><span data-stu-id="f0319-103">Provides trace logging functionality.</span></span>

```csharp
internal class Logging
```

> [!WARNING]
> <span data-ttu-id="f0319-104">Ta klasa jest wewnętrzna i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="f0319-104">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="f0319-105">Firma Microsoft nie obsługuje korzystania z tej klasy w aplikacji produkcyjnej w żadnej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="f0319-105">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="associate-method"></a><span data-ttu-id="f0319-106">Skojarz metodę</span><span class="sxs-lookup"><span data-stu-id="f0319-106">Associate method</span></span>

<span data-ttu-id="f0319-107">Rejestruje informacje, które są ze sobą skojarzone dwa obiekty.</span><span class="sxs-lookup"><span data-stu-id="f0319-107">Logs information that two objects are associated with each other.</span></span>

```csharp
internal static void Associate(TraceSource traceSource, object objA, object objB)
```

### <a name="parameters"></a><span data-ttu-id="f0319-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="f0319-108">Parameters</span></span>

- <span data-ttu-id="f0319-109">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="f0319-109">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="f0319-110">Źródło śledzenia do rejestrowania zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f0319-110">The trace source to log the event to.</span></span>

- <span data-ttu-id="f0319-111">`objA` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="f0319-111">`objA` <xref:System.Object></span></span>

  <span data-ttu-id="f0319-112">Obiekt, z którym ma zostać skojarzone `objB` .</span><span class="sxs-lookup"><span data-stu-id="f0319-112">The object to associate with `objB`.</span></span>

- <span data-ttu-id="f0319-113">`objB` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="f0319-113">`objB` <xref:System.Object></span></span>

  <span data-ttu-id="f0319-114">Obiekt, z którym ma zostać skojarzone `objA` .</span><span class="sxs-lookup"><span data-stu-id="f0319-114">The object to associate with `objA`.</span></span>

## <a name="entertracesource-object-string-string-method"></a><span data-ttu-id="f0319-115">Enter (TraceSource, Object, String, String) — Metoda</span><span class="sxs-lookup"><span data-stu-id="f0319-115">Enter(TraceSource, object, string, string) method</span></span>

<span data-ttu-id="f0319-116">Rejestruje wejście do metody.</span><span class="sxs-lookup"><span data-stu-id="f0319-116">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, object obj, string method, string param)
```

### <a name="parameters"></a><span data-ttu-id="f0319-117">Parametry</span><span class="sxs-lookup"><span data-stu-id="f0319-117">Parameters</span></span>

- <span data-ttu-id="f0319-118">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="f0319-118">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="f0319-119">Źródło śledzenia do rejestrowania zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f0319-119">The trace source to log the event to.</span></span>

- <span data-ttu-id="f0319-120">`obj` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="f0319-120">`obj` <xref:System.Object></span></span>

  <span data-ttu-id="f0319-121">Obiekt, w którym metoda została wywołana.</span><span class="sxs-lookup"><span data-stu-id="f0319-121">The object that the method was called on.</span></span>

- <span data-ttu-id="f0319-122">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="f0319-122">`method` <xref:System.String></span></span>

  <span data-ttu-id="f0319-123">Metoda, która jest wprowadzana.</span><span class="sxs-lookup"><span data-stu-id="f0319-123">The method that is being entered.</span></span>

- <span data-ttu-id="f0319-124">`param` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="f0319-124">`param` <xref:System.String></span></span>

  <span data-ttu-id="f0319-125">Parametry, które zostały przesłane do metody.</span><span class="sxs-lookup"><span data-stu-id="f0319-125">The parameters that were passed to the method.</span></span>

## <a name="entertracesource-object-string-object-method"></a><span data-ttu-id="f0319-126">Enter (TraceSource, Object, String, Object) — Metoda</span><span class="sxs-lookup"><span data-stu-id="f0319-126">Enter(TraceSource, object, string, object) method</span></span>

<span data-ttu-id="f0319-127">Rejestruje wejście do metody.</span><span class="sxs-lookup"><span data-stu-id="f0319-127">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, object obj, string method, object paramObject)
```

### <a name="parameters"></a><span data-ttu-id="f0319-128">Parametry</span><span class="sxs-lookup"><span data-stu-id="f0319-128">Parameters</span></span>

- <span data-ttu-id="f0319-129">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="f0319-129">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="f0319-130">Źródło śledzenia do rejestrowania zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f0319-130">The trace source to log the event to.</span></span>

- <span data-ttu-id="f0319-131">`obj` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="f0319-131">`obj` <xref:System.Object></span></span>

  <span data-ttu-id="f0319-132">Obiekt, w którym metoda została wywołana.</span><span class="sxs-lookup"><span data-stu-id="f0319-132">The object that the method was called on.</span></span>

- <span data-ttu-id="f0319-133">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="f0319-133">`method` <xref:System.String></span></span>

  <span data-ttu-id="f0319-134">Metoda, która jest wprowadzana.</span><span class="sxs-lookup"><span data-stu-id="f0319-134">The method that is being entered.</span></span>

- <span data-ttu-id="f0319-135">`paramObject` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="f0319-135">`paramObject` <xref:System.Object></span></span>

  <span data-ttu-id="f0319-136">Parametry, które zostały przesłane do metody.</span><span class="sxs-lookup"><span data-stu-id="f0319-136">The parameters that were passed to the method.</span></span>

## <a name="entertracesource-string-string-string-method"></a><span data-ttu-id="f0319-137">Enter (TraceSource, String, String, String) — Metoda</span><span class="sxs-lookup"><span data-stu-id="f0319-137">Enter(TraceSource, string, string, string) method</span></span>

<span data-ttu-id="f0319-138">Rejestruje wejście do metody.</span><span class="sxs-lookup"><span data-stu-id="f0319-138">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, string obj, string method, string param)
```

### <a name="parameters"></a><span data-ttu-id="f0319-139">Parametry</span><span class="sxs-lookup"><span data-stu-id="f0319-139">Parameters</span></span>

- <span data-ttu-id="f0319-140">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="f0319-140">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="f0319-141">Źródło śledzenia do rejestrowania zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f0319-141">The trace source to log the event to.</span></span>

- <span data-ttu-id="f0319-142">`obj` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="f0319-142">`obj` <xref:System.String></span></span>

  <span data-ttu-id="f0319-143">Obiekt, w którym metoda została wywołana.</span><span class="sxs-lookup"><span data-stu-id="f0319-143">The object that the method was called on.</span></span>

- <span data-ttu-id="f0319-144">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="f0319-144">`method` <xref:System.String></span></span>

  <span data-ttu-id="f0319-145">Metoda, która jest wprowadzana.</span><span class="sxs-lookup"><span data-stu-id="f0319-145">The method that is being entered.</span></span>

- <span data-ttu-id="f0319-146">`param` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="f0319-146">`param` <xref:System.String></span></span>

  <span data-ttu-id="f0319-147">Parametry, które zostały przesłane do metody.</span><span class="sxs-lookup"><span data-stu-id="f0319-147">The parameters that were passed to the method.</span></span>

## <a name="entertracesource-string-string-object-method"></a><span data-ttu-id="f0319-148">Enter (TraceSource, String, String, Object) — Metoda</span><span class="sxs-lookup"><span data-stu-id="f0319-148">Enter(TraceSource, string, string, object) method</span></span>

<span data-ttu-id="f0319-149">Rejestruje wejście do metody.</span><span class="sxs-lookup"><span data-stu-id="f0319-149">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, string obj, string method, object paramObject)
```

### <a name="parameters"></a><span data-ttu-id="f0319-150">Parametry</span><span class="sxs-lookup"><span data-stu-id="f0319-150">Parameters</span></span>

- <span data-ttu-id="f0319-151">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="f0319-151">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="f0319-152">Źródło śledzenia do rejestrowania zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f0319-152">The trace source to log the event to.</span></span>

- <span data-ttu-id="f0319-153">`obj` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="f0319-153">`obj` <xref:System.String></span></span>

  <span data-ttu-id="f0319-154">Obiekt, w którym metoda została wywołana.</span><span class="sxs-lookup"><span data-stu-id="f0319-154">The object that the method was called on.</span></span>

- <span data-ttu-id="f0319-155">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="f0319-155">`method` <xref:System.String></span></span>

  <span data-ttu-id="f0319-156">Metoda, która jest wprowadzana.</span><span class="sxs-lookup"><span data-stu-id="f0319-156">The method that is being entered.</span></span>

- <span data-ttu-id="f0319-157">`paramObject` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="f0319-157">`paramObject` <xref:System.Object></span></span>

  <span data-ttu-id="f0319-158">Parametry, które zostały przesłane do metody.</span><span class="sxs-lookup"><span data-stu-id="f0319-158">The parameters that were passed to the method.</span></span>

## <a name="entertracesource-string-string-method"></a><span data-ttu-id="f0319-159">Enter (TraceSource, String, String) — Metoda</span><span class="sxs-lookup"><span data-stu-id="f0319-159">Enter(TraceSource, string, string) method</span></span>

<span data-ttu-id="f0319-160">Rejestruje wejście do metody.</span><span class="sxs-lookup"><span data-stu-id="f0319-160">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, string method, string parameters)
```

### <a name="parameters"></a><span data-ttu-id="f0319-161">Parametry</span><span class="sxs-lookup"><span data-stu-id="f0319-161">Parameters</span></span>

- <span data-ttu-id="f0319-162">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="f0319-162">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="f0319-163">Źródło śledzenia do rejestrowania zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f0319-163">The trace source to log the event to.</span></span>

- <span data-ttu-id="f0319-164">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="f0319-164">`method` <xref:System.String></span></span>

  <span data-ttu-id="f0319-165">Metoda, która jest wprowadzana.</span><span class="sxs-lookup"><span data-stu-id="f0319-165">The method that is being entered.</span></span>

- <span data-ttu-id="f0319-166">`parameters` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="f0319-166">`parameters` <xref:System.String></span></span>

  <span data-ttu-id="f0319-167">Parametry, które zostały przesłane do metody.</span><span class="sxs-lookup"><span data-stu-id="f0319-167">The parameters that were passed to the method.</span></span>

## <a name="entertracesource-string-method"></a><span data-ttu-id="f0319-168">Enter (TraceSource, String) — Metoda</span><span class="sxs-lookup"><span data-stu-id="f0319-168">Enter(TraceSource, string) method</span></span>

<span data-ttu-id="f0319-169">Rejestruje wejście do metody.</span><span class="sxs-lookup"><span data-stu-id="f0319-169">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, string msg)
```

### <a name="parameters"></a><span data-ttu-id="f0319-170">Parametry</span><span class="sxs-lookup"><span data-stu-id="f0319-170">Parameters</span></span>

- <span data-ttu-id="f0319-171">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="f0319-171">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="f0319-172">Źródło śledzenia do rejestrowania zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f0319-172">The trace source to log the event to.</span></span>

- <span data-ttu-id="f0319-173">`msg` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="f0319-173">`msg` <xref:System.String></span></span>

  <span data-ttu-id="f0319-174">Komunikat wejścia do zarejestrowania ze źródłem śledzenia.</span><span class="sxs-lookup"><span data-stu-id="f0319-174">The entrance message to log to the trace source.</span></span>

## <a name="exception-method"></a><span data-ttu-id="f0319-175">Exception — Metoda</span><span class="sxs-lookup"><span data-stu-id="f0319-175">Exception method</span></span>

<span data-ttu-id="f0319-176">Rejestruje wyjątek i przywraca wcięcia.</span><span class="sxs-lookup"><span data-stu-id="f0319-176">Logs an exception and restores indentation.</span></span>

```csharp
internal static void Exception(TraceSource traceSource, object obj, string method, Exception e)
```

### <a name="parameters"></a><span data-ttu-id="f0319-177">Parametry</span><span class="sxs-lookup"><span data-stu-id="f0319-177">Parameters</span></span>

- <span data-ttu-id="f0319-178">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="f0319-178">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="f0319-179">Źródło śledzenia do rejestrowania zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f0319-179">The trace source to log the event to.</span></span>

- <span data-ttu-id="f0319-180">`obj` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="f0319-180">`obj` <xref:System.Object></span></span>

  <span data-ttu-id="f0319-181">Obiekt, w którym wywołano metodę, w której wywołał wyjątek.</span><span class="sxs-lookup"><span data-stu-id="f0319-181">The object that the method that threw an exception was called on.</span></span>

- <span data-ttu-id="f0319-182">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="f0319-182">`method` <xref:System.String></span></span>

  <span data-ttu-id="f0319-183">Metoda, która wywołała wyjątek.</span><span class="sxs-lookup"><span data-stu-id="f0319-183">The method that threw the exception.</span></span>

- <span data-ttu-id="f0319-184">`e` <xref:System.Exception></span><span class="sxs-lookup"><span data-stu-id="f0319-184">`e` <xref:System.Exception></span></span>

  <span data-ttu-id="f0319-185">Zgłoszono wyjątek.</span><span class="sxs-lookup"><span data-stu-id="f0319-185">The exception that was thrown.</span></span>

## <a name="exittracesource-object-string-object-method"></a><span data-ttu-id="f0319-186">Exit (TraceSource, Object, String, Object) — Metoda</span><span class="sxs-lookup"><span data-stu-id="f0319-186">Exit(TraceSource, object, string, object) method</span></span>

<span data-ttu-id="f0319-187">Dzienniki opuszczają funkcję.</span><span class="sxs-lookup"><span data-stu-id="f0319-187">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, object obj, string method, object retObject)
```

### <a name="parameters"></a><span data-ttu-id="f0319-188">Parametry</span><span class="sxs-lookup"><span data-stu-id="f0319-188">Parameters</span></span>

- <span data-ttu-id="f0319-189">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="f0319-189">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="f0319-190">Źródło śledzenia do rejestrowania zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f0319-190">The trace source to log the event to.</span></span>

- <span data-ttu-id="f0319-191">`obj` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="f0319-191">`obj` <xref:System.Object></span></span>

  <span data-ttu-id="f0319-192">Obiekt, w którym metoda została wywołana.</span><span class="sxs-lookup"><span data-stu-id="f0319-192">The object that the method was called on.</span></span>

- <span data-ttu-id="f0319-193">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="f0319-193">`method` <xref:System.String></span></span>

  <span data-ttu-id="f0319-194">Metoda, która jest zamykana.</span><span class="sxs-lookup"><span data-stu-id="f0319-194">The method that is being exited.</span></span>

- <span data-ttu-id="f0319-195">`retObject` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="f0319-195">`retObject` <xref:System.Object></span></span>

  <span data-ttu-id="f0319-196">Wartość, która jest zwracana przez metodę.</span><span class="sxs-lookup"><span data-stu-id="f0319-196">The value that's being returned by the method.</span></span>

## <a name="exittracesource-string-string-object-method"></a><span data-ttu-id="f0319-197">Exit (TraceSource, String, String, Object) — Metoda</span><span class="sxs-lookup"><span data-stu-id="f0319-197">Exit(TraceSource, string, string, object) method</span></span>

<span data-ttu-id="f0319-198">Dzienniki opuszczają funkcję.</span><span class="sxs-lookup"><span data-stu-id="f0319-198">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, string obj, string method, object retObject)
```

### <a name="parameters"></a><span data-ttu-id="f0319-199">Parametry</span><span class="sxs-lookup"><span data-stu-id="f0319-199">Parameters</span></span>

- <span data-ttu-id="f0319-200">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="f0319-200">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="f0319-201">Źródło śledzenia do rejestrowania zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f0319-201">The trace source to log the event to.</span></span>

- <span data-ttu-id="f0319-202">`obj` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="f0319-202">`obj` <xref:System.String></span></span>

  <span data-ttu-id="f0319-203">Obiekt, w którym metoda została wywołana.</span><span class="sxs-lookup"><span data-stu-id="f0319-203">The object that the method was called on.</span></span>

- <span data-ttu-id="f0319-204">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="f0319-204">`method` <xref:System.String></span></span>

  <span data-ttu-id="f0319-205">Metoda, która jest zamykana.</span><span class="sxs-lookup"><span data-stu-id="f0319-205">The method that is being exited.</span></span>

- <span data-ttu-id="f0319-206">`retObject` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="f0319-206">`retObject` <xref:System.Object></span></span>

  <span data-ttu-id="f0319-207">Wartość, która jest zwracana przez metodę.</span><span class="sxs-lookup"><span data-stu-id="f0319-207">The value that's being returned by the method.</span></span>

## <a name="exittracesource-object-string-string-method"></a><span data-ttu-id="f0319-208">Exit (TraceSource, Object, String, String) — Metoda</span><span class="sxs-lookup"><span data-stu-id="f0319-208">Exit(TraceSource, object, string, string) method</span></span>

<span data-ttu-id="f0319-209">Dzienniki opuszczają funkcję.</span><span class="sxs-lookup"><span data-stu-id="f0319-209">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, object obj, string method, string retValue)
```

### <a name="parameters"></a><span data-ttu-id="f0319-210">Parametry</span><span class="sxs-lookup"><span data-stu-id="f0319-210">Parameters</span></span>

- <span data-ttu-id="f0319-211">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="f0319-211">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="f0319-212">Źródło śledzenia do rejestrowania zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f0319-212">The trace source to log the event to.</span></span>

- <span data-ttu-id="f0319-213">`obj` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="f0319-213">`obj` <xref:System.Object></span></span>

  <span data-ttu-id="f0319-214">Obiekt, w którym metoda została wywołana.</span><span class="sxs-lookup"><span data-stu-id="f0319-214">The object that the method was called on.</span></span>

- <span data-ttu-id="f0319-215">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="f0319-215">`method` <xref:System.String></span></span>

  <span data-ttu-id="f0319-216">Metoda, która jest zamykana.</span><span class="sxs-lookup"><span data-stu-id="f0319-216">The method that is being exited.</span></span>

- <span data-ttu-id="f0319-217">`retValue` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="f0319-217">`retValue` <xref:System.String></span></span>

  <span data-ttu-id="f0319-218">Wartość, która jest zwracana przez metodę.</span><span class="sxs-lookup"><span data-stu-id="f0319-218">The value that's being returned by the method.</span></span>

## <a name="exittracesource-string-string-string-method"></a><span data-ttu-id="f0319-219">Exit (TraceSource, String, String, String) — Metoda</span><span class="sxs-lookup"><span data-stu-id="f0319-219">Exit(TraceSource, string, string, string) method</span></span>

<span data-ttu-id="f0319-220">Dzienniki opuszczają funkcję.</span><span class="sxs-lookup"><span data-stu-id="f0319-220">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, string obj, string method, string retValue)
```

### <a name="parameters"></a><span data-ttu-id="f0319-221">Parametry</span><span class="sxs-lookup"><span data-stu-id="f0319-221">Parameters</span></span>

- <span data-ttu-id="f0319-222">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="f0319-222">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="f0319-223">Źródło śledzenia do rejestrowania zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f0319-223">The trace source to log the event to.</span></span>

- <span data-ttu-id="f0319-224">`obj` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="f0319-224">`obj` <xref:System.String></span></span>

  <span data-ttu-id="f0319-225">Obiekt, w którym metoda została wywołana.</span><span class="sxs-lookup"><span data-stu-id="f0319-225">The object that the method was called on.</span></span>

- <span data-ttu-id="f0319-226">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="f0319-226">`method` <xref:System.String></span></span>

  <span data-ttu-id="f0319-227">Metoda, która jest zamykana.</span><span class="sxs-lookup"><span data-stu-id="f0319-227">The method that is being exited.</span></span>

- <span data-ttu-id="f0319-228">`retValue` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="f0319-228">`retValue` <xref:System.String></span></span>

  <span data-ttu-id="f0319-229">Wartość, która jest zwracana przez metodę.</span><span class="sxs-lookup"><span data-stu-id="f0319-229">The value that's being returned by the method.</span></span>

## <a name="exittracesource-string-string-method"></a><span data-ttu-id="f0319-230">Exit (TraceSource, String, String) — Metoda</span><span class="sxs-lookup"><span data-stu-id="f0319-230">Exit(TraceSource, string, string) method</span></span>

<span data-ttu-id="f0319-231">Dzienniki opuszczają funkcję.</span><span class="sxs-lookup"><span data-stu-id="f0319-231">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, string method, string parameters)
```

### <a name="parameters"></a><span data-ttu-id="f0319-232">Parametry</span><span class="sxs-lookup"><span data-stu-id="f0319-232">Parameters</span></span>

- <span data-ttu-id="f0319-233">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="f0319-233">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="f0319-234">Źródło śledzenia do rejestrowania zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f0319-234">The trace source to log the event to.</span></span>

- <span data-ttu-id="f0319-235">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="f0319-235">`method` <xref:System.String></span></span>

  <span data-ttu-id="f0319-236">Metoda, która jest zamykana.</span><span class="sxs-lookup"><span data-stu-id="f0319-236">The method that is being exited.</span></span>

- <span data-ttu-id="f0319-237">`parameters` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="f0319-237">`parameters` <xref:System.String></span></span>

  <span data-ttu-id="f0319-238">Parametry, które zostały przesłane do metody, która jest zamykana.</span><span class="sxs-lookup"><span data-stu-id="f0319-238">The parameters that were passed to the method that's being exited.</span></span>

## <a name="exittracesource-string-method"></a><span data-ttu-id="f0319-239">Exit (TraceSource, String) — Metoda</span><span class="sxs-lookup"><span data-stu-id="f0319-239">Exit(TraceSource, string) method</span></span>

<span data-ttu-id="f0319-240">Dzienniki opuszczają funkcję.</span><span class="sxs-lookup"><span data-stu-id="f0319-240">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, string msg)
```

### <a name="parameters"></a><span data-ttu-id="f0319-241">Parametry</span><span class="sxs-lookup"><span data-stu-id="f0319-241">Parameters</span></span>

- <span data-ttu-id="f0319-242">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="f0319-242">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="f0319-243">Źródło śledzenia do rejestrowania zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f0319-243">The trace source to log the event to.</span></span>

- <span data-ttu-id="f0319-244">`msg` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="f0319-244">`msg` <xref:System.String></span></span>

  <span data-ttu-id="f0319-245">Komunikat wyjściowy do zarejestrowania ze źródłem śledzenia.</span><span class="sxs-lookup"><span data-stu-id="f0319-245">The exit message to log to the trace source.</span></span>

## <a name="http-property"></a><span data-ttu-id="f0319-246">Właściwość protokołu http</span><span class="sxs-lookup"><span data-stu-id="f0319-246">Http property</span></span>

<span data-ttu-id="f0319-247">Pobiera źródło śledzenia dla "System .NET. http".</span><span class="sxs-lookup"><span data-stu-id="f0319-247">Gets the trace source for "System.Net.Http".</span></span>

```csharp
internal static TraceSource Http { get; }
```

### <a name="property-value"></a><span data-ttu-id="f0319-248">Wartość właściwości</span><span class="sxs-lookup"><span data-stu-id="f0319-248">Property value</span></span>

<xref:System.Diagnostics.TraceSource>\
<span data-ttu-id="f0319-249">Źródło śledzenia dla "System .NET. http" lub `null` Rejestrowanie nie jest włączone.</span><span class="sxs-lookup"><span data-stu-id="f0319-249">The trace source for "System.Net.Http", or `null` if logging is not enabled.</span></span>

## <a name="on-property"></a><span data-ttu-id="f0319-250">Właściwość on</span><span class="sxs-lookup"><span data-stu-id="f0319-250">On property</span></span>

<span data-ttu-id="f0319-251">Pobiera wartość wskazującą, czy rejestrowanie jest włączone.</span><span class="sxs-lookup"><span data-stu-id="f0319-251">Gets a value that indicates whether logging is enabled.</span></span>

```csharp
internal static bool On { get; }
```

### <a name="property-value"></a><span data-ttu-id="f0319-252">Wartość właściwości</span><span class="sxs-lookup"><span data-stu-id="f0319-252">Property value</span></span>

<xref:System.Boolean>\
<span data-ttu-id="f0319-253">`true`Jeśli rejestrowanie jest włączone; w przeciwnym razie `false` .</span><span class="sxs-lookup"><span data-stu-id="f0319-253">`true` if logging is enabled; otherwise, `false`.</span></span>

## <a name="requirements"></a><span data-ttu-id="f0319-254">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f0319-254">Requirements</span></span>

<span data-ttu-id="f0319-255">**Przestrzeń nazw:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="f0319-255">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="f0319-256">**Zestaw:** System (w System.dll)</span><span class="sxs-lookup"><span data-stu-id="f0319-256">**Assembly:** System (in System.dll)</span></span>
