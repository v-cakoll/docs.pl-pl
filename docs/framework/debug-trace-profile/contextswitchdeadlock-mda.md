---
title: contextSwitchDeadlock MDA
description: Przeczytaj o contextSwitchDeadlock Managed Debug Assistant (MDA) w programie .NET, który jest uaktywniany w przypadku wykrycia zakleszczenia podczas przejścia kontekstu COM.
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
ms.openlocfilehash: 52db4f2c88bac4e8cac621cca989fa10acb43f94
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2020
ms.locfileid: "85416021"
---
# <a name="contextswitchdeadlock-mda"></a><span data-ttu-id="a0ffe-103">contextSwitchDeadlock MDA</span><span class="sxs-lookup"><span data-stu-id="a0ffe-103">contextSwitchDeadlock MDA</span></span>

<span data-ttu-id="a0ffe-104">`contextSwitchDeadlock`Asystent debugowania zarządzanego (MDA) jest uaktywniany w przypadku wykrycia zakleszczenia podczas próby przejścia kontekstu com.</span><span class="sxs-lookup"><span data-stu-id="a0ffe-104">The `contextSwitchDeadlock` managed debugging assistant (MDA) is activated when a deadlock is detected during an attempted COM context transition.</span></span>

## <a name="symptoms"></a><span data-ttu-id="a0ffe-105">Objawy</span><span class="sxs-lookup"><span data-stu-id="a0ffe-105">Symptoms</span></span>

<span data-ttu-id="a0ffe-106">Najbardziej typowym objawem jest to, że wywołanie niezarządzanego składnika COM z kodu zarządzanego nie zwraca.</span><span class="sxs-lookup"><span data-stu-id="a0ffe-106">The most common symptom is that a call on an unmanaged COM component from managed code does not return.</span></span>  <span data-ttu-id="a0ffe-107">Innym objawem jest wzrost wykorzystania pamięci z upływem czasu.</span><span class="sxs-lookup"><span data-stu-id="a0ffe-107">Another symptom is memory usage increasing over time.</span></span>

## <a name="cause"></a><span data-ttu-id="a0ffe-108">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="a0ffe-108">Cause</span></span>

<span data-ttu-id="a0ffe-109">Najbardziej prawdopodobną przyczyną jest to, że wątek jednowątkowego apartamentu (STA) nie pompuje komunikatów.</span><span class="sxs-lookup"><span data-stu-id="a0ffe-109">The most probable cause is that a single-threaded apartment (STA) thread is not pumping messages.</span></span> <span data-ttu-id="a0ffe-110">Wątek STA jest czekał bez pompowania komunikatów lub wykonuje długotrwałe operacje i nie zezwala na pompę kolejki komunikatów.</span><span class="sxs-lookup"><span data-stu-id="a0ffe-110">The STA thread is either waiting without pumping messages or is performing lengthy operations and is not allowing the message queue to pump.</span></span>

<span data-ttu-id="a0ffe-111">Zwiększenie użycia pamięci w czasie jest spowodowane przez wątek finalizatora próbujący wywołać `Release` na niezarządzanym składniku com i ten składnik nie zwraca.</span><span class="sxs-lookup"><span data-stu-id="a0ffe-111">Memory usage increasing over time is caused by the finalizer thread attempting to call `Release` on an unmanaged COM component and that component is not returning.</span></span>  <span data-ttu-id="a0ffe-112">Zapobiega to odzyskiwaniu innych obiektów przez finalizatora.</span><span class="sxs-lookup"><span data-stu-id="a0ffe-112">This prevents the finalizer from reclaiming other objects.</span></span>

<span data-ttu-id="a0ffe-113">Domyślnie model wątkowości głównego wątku Visual Basic aplikacji konsolowych to STA.</span><span class="sxs-lookup"><span data-stu-id="a0ffe-113">By default, the threading model for the main thread of Visual Basic console applications is STA.</span></span> <span data-ttu-id="a0ffe-114">To zdarzenie MDA jest uaktywniane, jeśli wątek STA używa współdziałania COM bezpośrednio lub pośrednio za pośrednictwem środowiska uruchomieniowego języka wspólnego lub formantu innej firmy.</span><span class="sxs-lookup"><span data-stu-id="a0ffe-114">This MDA is activated if an STA thread uses COM interoperability either directly or indirectly through the common language runtime or a third-party control.</span></span>  <span data-ttu-id="a0ffe-115">Aby uniknąć aktywowania tego MDA w Visual Basic aplikacji konsolowej, Zastosuj <xref:System.MTAThreadAttribute> atrybut do metody Main lub zmodyfikuj aplikację w celu wypróbowania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="a0ffe-115">To avoid activating this MDA in a Visual Basic console application, apply the <xref:System.MTAThreadAttribute> attribute to the main method or modify the application to pump messages.</span></span>

<span data-ttu-id="a0ffe-116">W przypadku spełnienia wszystkich następujących warunków zdarzenie MDA może być nieaktywne.</span><span class="sxs-lookup"><span data-stu-id="a0ffe-116">It is possible for this MDA to be falsely activated when all of the following conditions are met:</span></span>

- <span data-ttu-id="a0ffe-117">Aplikacja tworzy składniki COM z wątków STA bezpośrednio lub pośrednio za pośrednictwem bibliotek.</span><span class="sxs-lookup"><span data-stu-id="a0ffe-117">An application creates COM components from STA threads either directly or indirectly through libraries.</span></span>

- <span data-ttu-id="a0ffe-118">Aplikacja została zatrzymana w debugerze, a użytkownik może kontynuować działanie aplikacji lub wykonać operację kroku.</span><span class="sxs-lookup"><span data-stu-id="a0ffe-118">The application was stopped in the debugger and the user either continued the application or performed a step operation.</span></span>

- <span data-ttu-id="a0ffe-119">Debugowanie niezarządzane nie jest włączone.</span><span class="sxs-lookup"><span data-stu-id="a0ffe-119">Unmanaged debugging is not enabled.</span></span>

<span data-ttu-id="a0ffe-120">Aby określić, czy MDA jest aktualnie aktywowany, wyłącz wszystkie punkty przerwania, uruchom ponownie aplikację i zezwól na jej uruchomienie bez zatrzymywania.</span><span class="sxs-lookup"><span data-stu-id="a0ffe-120">To determine if the MDA is being falsely activated, disable all breakpoints, restart the application, and allow it to run without stopping.</span></span> <span data-ttu-id="a0ffe-121">Jeśli zdarzenie MDA nie zostanie aktywowane, prawdopodobnie początkowa aktywacja miała wartość false.</span><span class="sxs-lookup"><span data-stu-id="a0ffe-121">If the MDA is not activated, it is likely the initial activation was false.</span></span> <span data-ttu-id="a0ffe-122">W takim przypadku należy wyłączyć MDA, aby uniknąć interwencji z sesją debugowania.</span><span class="sxs-lookup"><span data-stu-id="a0ffe-122">In this case, disable the MDA to avoid interference with the debugging session.</span></span>

> [!NOTE]
> <span data-ttu-id="a0ffe-123">To zdarzenie MDA jest w domyślnym zestawie dla programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a0ffe-123">This MDA is in the default set for Visual Studio.</span></span> <span data-ttu-id="a0ffe-124">Aby uzyskać informacje na temat sposobu wyłączania usługi MDA, zobacz [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md#enable-and-disable-mdas).</span><span class="sxs-lookup"><span data-stu-id="a0ffe-124">For information about how to disable MDAs, see [Diagnosing Errors with Managed Debugging Assistants](diagnosing-errors-with-managed-debugging-assistants.md#enable-and-disable-mdas).</span></span>

## <a name="resolution"></a><span data-ttu-id="a0ffe-125">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="a0ffe-125">Resolution</span></span>

<span data-ttu-id="a0ffe-126">Przestrzegaj reguł COM dotyczących pompowania komunikatów STA.</span><span class="sxs-lookup"><span data-stu-id="a0ffe-126">Follow COM rules regarding STA message pumping.</span></span>

## <a name="effect-on-the-runtime"></a><span data-ttu-id="a0ffe-127">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="a0ffe-127">Effect on the Runtime</span></span>

<span data-ttu-id="a0ffe-128">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="a0ffe-128">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="a0ffe-129">Raportuje tylko dane dotyczące kontekstów COM.</span><span class="sxs-lookup"><span data-stu-id="a0ffe-129">It only reports data about COM contexts.</span></span>

## <a name="output"></a><span data-ttu-id="a0ffe-130">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="a0ffe-130">Output</span></span>

<span data-ttu-id="a0ffe-131">Komunikat opisujący bieżący kontekst i kontekst docelowy.</span><span class="sxs-lookup"><span data-stu-id="a0ffe-131">A message describing the current context and the target context.</span></span>

## <a name="configuration"></a><span data-ttu-id="a0ffe-132">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="a0ffe-132">Configuration</span></span>

```xml
<mdaConfig>
  <assistants>
    <contextSwitchDeadlock />
  </assistants>
</mdaConfig>
```

## <a name="see-also"></a><span data-ttu-id="a0ffe-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a0ffe-133">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="a0ffe-134">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="a0ffe-134">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="a0ffe-135">Organizowanie międzyoperacyjne</span><span class="sxs-lookup"><span data-stu-id="a0ffe-135">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
