---
title: contextSwitchDeadlock MDA
ms.date: 03/30/2017
helpviewer_keywords:
- deadlocks [.NET Framework]
- pumping messages
- STA message pumping
- single-threaded COM components
- MDAs (managed debugging assistants), context switching deadlocks
- managed debugging assistants (MDAs), context switching deadlocks
- ContextSwitchDeadlock MDA
- message pumping
- context switching deadlocks
ms.assetid: 26dfaa15-9ddb-4b0a-b6da-999bba664fa6
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c1a0e2a6c7851b261baa3e02f6431e7a4ff697e4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64660324"
---
# <a name="contextswitchdeadlock-mda"></a><span data-ttu-id="0f77a-102">contextSwitchDeadlock MDA</span><span class="sxs-lookup"><span data-stu-id="0f77a-102">contextSwitchDeadlock MDA</span></span>

<span data-ttu-id="0f77a-103">`contextSwitchDeadlock` Zarządzanego Asystenta debugowania (MDA) jest aktywowana po wykryciu zakleszczenie podczas próby przejścia kontekstu COM.</span><span class="sxs-lookup"><span data-stu-id="0f77a-103">The `contextSwitchDeadlock` managed debugging assistant (MDA) is activated when a deadlock is detected during an attempted COM context transition.</span></span>

## <a name="symptoms"></a><span data-ttu-id="0f77a-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="0f77a-104">Symptoms</span></span>

<span data-ttu-id="0f77a-105">Najbardziej typowym symptomem jest wywołanie składnika COM niezarządzane z kodu zarządzanego nie zwraca.</span><span class="sxs-lookup"><span data-stu-id="0f77a-105">The most common symptom is that a call on an unmanaged COM component from managed code does not return.</span></span>  <span data-ttu-id="0f77a-106">Kolejnym objawem może być to wykorzystania pamięci zwiększa się wraz z upływem czasu.</span><span class="sxs-lookup"><span data-stu-id="0f77a-106">Another symptom is memory usage increasing over time.</span></span>

## <a name="cause"></a><span data-ttu-id="0f77a-107">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="0f77a-107">Cause</span></span>

<span data-ttu-id="0f77a-108">Najbardziej prawdopodobna przyczyna to, że wątek jednowątkowego apartamentu (STA) nie jest przekazywanie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="0f77a-108">The most probable cause is that a single-threaded apartment (STA) thread is not pumping messages.</span></span> <span data-ttu-id="0f77a-109">Wątku STA. jest albo oczekiwania bez przekazywania komunikatów operacji długotrwałej lub nie zezwala na kolejki komunikatów, która pompy.</span><span class="sxs-lookup"><span data-stu-id="0f77a-109">The STA thread is either waiting without pumping messages or is performing lengthy operations and is not allowing the message queue to pump.</span></span>

<span data-ttu-id="0f77a-110">Użycie pamięci zwiększa się wraz z upływem czasu jest spowodowany przez wątek finalizatora, próba wywołania `Release` niezarządzanych com i ten składnik nie powraca.</span><span class="sxs-lookup"><span data-stu-id="0f77a-110">Memory usage increasing over time is caused by the finalizer thread attempting to call `Release` on an unmanaged COM component and that component is not returning.</span></span>  <span data-ttu-id="0f77a-111">To uniemożliwia to finalizatorowi odzyskiwaniu innych obiektów.</span><span class="sxs-lookup"><span data-stu-id="0f77a-111">This prevents the finalizer from reclaiming other objects.</span></span>

<span data-ttu-id="0f77a-112">Domyślnie modelu wątkowości dla głównego wątku aplikacji konsoli języka Visual Basic jest komórce jednowątkowej</span><span class="sxs-lookup"><span data-stu-id="0f77a-112">By default, the threading model for the main thread of Visual Basic console applications is STA.</span></span> <span data-ttu-id="0f77a-113">To zdarzenie MDA jest aktywowane, jeśli w wątku STA. używa współdziałania COM bezpośrednio lub pośrednio za pośrednictwem środowiska uruchomieniowego języka wspólnego lub kontroli innych firm.</span><span class="sxs-lookup"><span data-stu-id="0f77a-113">This MDA is activated if an STA thread uses COM interoperability either directly or indirectly through the common language runtime or a third-party control.</span></span>  <span data-ttu-id="0f77a-114">Aby uniknąć aktywowanie to zdarzenie MDA w aplikację konsolową w języku Visual Basic, należy zastosować <xref:System.MTAThreadAttribute> atrybutu do głównej metody lub zmodyfikować aplikację tak, by przekazywać komunikaty.</span><span class="sxs-lookup"><span data-stu-id="0f77a-114">To avoid activating this MDA in a Visual Basic console application, apply the <xref:System.MTAThreadAttribute> attribute to the main method or modify the application to pump messages.</span></span>

<span data-ttu-id="0f77a-115">Możliwe jest, to zdarzenie MDA błędnie zostanie uaktywniony, gdy są spełnione wszystkie następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="0f77a-115">It is possible for this MDA to be falsely activated when all of the following conditions are met:</span></span>

- <span data-ttu-id="0f77a-116">Aplikacja tworzy składników COM z wątków STA bezpośrednio lub pośrednio za pośrednictwem biblioteki.</span><span class="sxs-lookup"><span data-stu-id="0f77a-116">An application creates COM components from STA threads either directly or indirectly through libraries.</span></span>

- <span data-ttu-id="0f77a-117">Aplikacja została zatrzymana w debugerze, a użytkownik nadal aplikacji lub wykonana operacja kroku.</span><span class="sxs-lookup"><span data-stu-id="0f77a-117">The application was stopped in the debugger and the user either continued the application or performed a step operation.</span></span>

- <span data-ttu-id="0f77a-118">Debugowanie niezarządzane nie jest włączona.</span><span class="sxs-lookup"><span data-stu-id="0f77a-118">Unmanaged debugging is not enabled.</span></span>

<span data-ttu-id="0f77a-119">Aby określić, jeśli zdarzenie MDA jest aktywowane błędnie, wyłącz wszystkie punkty przerwania, uruchom ponownie aplikację i zezwolenia na jego uruchomienie bez zatrzymywania.</span><span class="sxs-lookup"><span data-stu-id="0f77a-119">To determine if the MDA is being falsely activated, disable all breakpoints, restart the application, and allow it to run without stopping.</span></span> <span data-ttu-id="0f77a-120">Jeśli zdarzenie MDA nie został aktywowany, prawdopodobnie początkowej aktywacji została wartość false.</span><span class="sxs-lookup"><span data-stu-id="0f77a-120">If the MDA is not activated, it is likely the initial activation was false.</span></span> <span data-ttu-id="0f77a-121">W takim przypadku należy wyłączyć MDA, aby uniknąć zakłócenia w sesji debugowania.</span><span class="sxs-lookup"><span data-stu-id="0f77a-121">In this case, disable the MDA to avoid interference with the debugging session.</span></span>

> [!NOTE]
> <span data-ttu-id="0f77a-122">To zdarzenie MDA jest domyślnym zestawem dla programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0f77a-122">This MDA is in the default set for Visual Studio.</span></span> <span data-ttu-id="0f77a-123">Aby uzyskać informacje na temat wyłączania mda, zobacz [diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md#enable-and-disable-mdas).</span><span class="sxs-lookup"><span data-stu-id="0f77a-123">For information about how to disable MDAs, see [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md#enable-and-disable-mdas).</span></span>

## <a name="resolution"></a><span data-ttu-id="0f77a-124">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="0f77a-124">Resolution</span></span>

<span data-ttu-id="0f77a-125">Postępuj zgodnie z COM reguły dotyczące przekazywanie komunikatów STA.</span><span class="sxs-lookup"><span data-stu-id="0f77a-125">Follow COM rules regarding STA message pumping.</span></span>

## <a name="effect-on-the-runtime"></a><span data-ttu-id="0f77a-126">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="0f77a-126">Effect on the Runtime</span></span>

<span data-ttu-id="0f77a-127">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="0f77a-127">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="0f77a-128">Informuje jedynie dane o kontekstach COM.</span><span class="sxs-lookup"><span data-stu-id="0f77a-128">It only reports data about COM contexts.</span></span>

## <a name="output"></a><span data-ttu-id="0f77a-129">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="0f77a-129">Output</span></span>

<span data-ttu-id="0f77a-130">Komunikat opisujący bieżący kontekst i kontekst docelowego.</span><span class="sxs-lookup"><span data-stu-id="0f77a-130">A message describing the current context and the target context.</span></span>

## <a name="configuration"></a><span data-ttu-id="0f77a-131">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="0f77a-131">Configuration</span></span>

```xml
<mdaConfig>
  <assistants>
    <contextSwitchDeadlock />
  </assistants>
</mdaConfig>
```

## <a name="see-also"></a><span data-ttu-id="0f77a-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0f77a-132">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="0f77a-133">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="0f77a-133">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="0f77a-134">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="0f77a-134">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
