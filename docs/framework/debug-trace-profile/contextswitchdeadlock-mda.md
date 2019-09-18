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
ms.openlocfilehash: 7bcdb235ff2a73514c5bb3ad7abc3f4c3fc8e441
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052922"
---
# <a name="contextswitchdeadlock-mda"></a><span data-ttu-id="f0ce9-102">contextSwitchDeadlock MDA</span><span class="sxs-lookup"><span data-stu-id="f0ce9-102">contextSwitchDeadlock MDA</span></span>

<span data-ttu-id="f0ce9-103">Asystent `contextSwitchDeadlock` debugowania zarządzanego (MDA) jest uaktywniany w przypadku wykrycia zakleszczenia podczas próby przejścia kontekstu com.</span><span class="sxs-lookup"><span data-stu-id="f0ce9-103">The `contextSwitchDeadlock` managed debugging assistant (MDA) is activated when a deadlock is detected during an attempted COM context transition.</span></span>

## <a name="symptoms"></a><span data-ttu-id="f0ce9-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="f0ce9-104">Symptoms</span></span>

<span data-ttu-id="f0ce9-105">Najbardziej typowym objawem jest to, że wywołanie niezarządzanego składnika COM z kodu zarządzanego nie zwraca.</span><span class="sxs-lookup"><span data-stu-id="f0ce9-105">The most common symptom is that a call on an unmanaged COM component from managed code does not return.</span></span>  <span data-ttu-id="f0ce9-106">Innym objawem jest wzrost wykorzystania pamięci z upływem czasu.</span><span class="sxs-lookup"><span data-stu-id="f0ce9-106">Another symptom is memory usage increasing over time.</span></span>

## <a name="cause"></a><span data-ttu-id="f0ce9-107">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="f0ce9-107">Cause</span></span>

<span data-ttu-id="f0ce9-108">Najbardziej prawdopodobną przyczyną jest to, że wątek jednowątkowego apartamentu (STA) nie pompuje komunikatów.</span><span class="sxs-lookup"><span data-stu-id="f0ce9-108">The most probable cause is that a single-threaded apartment (STA) thread is not pumping messages.</span></span> <span data-ttu-id="f0ce9-109">Wątek STA jest czekał bez pompowania komunikatów lub wykonuje długotrwałe operacje i nie zezwala na pompę kolejki komunikatów.</span><span class="sxs-lookup"><span data-stu-id="f0ce9-109">The STA thread is either waiting without pumping messages or is performing lengthy operations and is not allowing the message queue to pump.</span></span>

<span data-ttu-id="f0ce9-110">Zwiększenie użycia pamięci w czasie jest spowodowane przez wątek finalizatora próbujący wywołać `Release` na niezarządzanym składniku com i ten składnik nie zwraca.</span><span class="sxs-lookup"><span data-stu-id="f0ce9-110">Memory usage increasing over time is caused by the finalizer thread attempting to call `Release` on an unmanaged COM component and that component is not returning.</span></span>  <span data-ttu-id="f0ce9-111">Zapobiega to odzyskiwaniu innych obiektów przez finalizatora.</span><span class="sxs-lookup"><span data-stu-id="f0ce9-111">This prevents the finalizer from reclaiming other objects.</span></span>

<span data-ttu-id="f0ce9-112">Domyślnie model wątkowości głównego wątku Visual Basic aplikacji konsolowych to STA.</span><span class="sxs-lookup"><span data-stu-id="f0ce9-112">By default, the threading model for the main thread of Visual Basic console applications is STA.</span></span> <span data-ttu-id="f0ce9-113">To zdarzenie MDA jest uaktywniane, jeśli wątek STA używa współdziałania COM bezpośrednio lub pośrednio za pośrednictwem środowiska uruchomieniowego języka wspólnego lub formantu innej firmy.</span><span class="sxs-lookup"><span data-stu-id="f0ce9-113">This MDA is activated if an STA thread uses COM interoperability either directly or indirectly through the common language runtime or a third-party control.</span></span>  <span data-ttu-id="f0ce9-114">Aby uniknąć aktywowania tego MDA w Visual Basic aplikacji konsolowej, Zastosuj <xref:System.MTAThreadAttribute> atrybut do metody Main lub zmodyfikuj aplikację w celu wypróbowania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="f0ce9-114">To avoid activating this MDA in a Visual Basic console application, apply the <xref:System.MTAThreadAttribute> attribute to the main method or modify the application to pump messages.</span></span>

<span data-ttu-id="f0ce9-115">W przypadku spełnienia wszystkich następujących warunków zdarzenie MDA może być nieaktywne.</span><span class="sxs-lookup"><span data-stu-id="f0ce9-115">It is possible for this MDA to be falsely activated when all of the following conditions are met:</span></span>

- <span data-ttu-id="f0ce9-116">Aplikacja tworzy składniki COM z wątków STA bezpośrednio lub pośrednio za pośrednictwem bibliotek.</span><span class="sxs-lookup"><span data-stu-id="f0ce9-116">An application creates COM components from STA threads either directly or indirectly through libraries.</span></span>

- <span data-ttu-id="f0ce9-117">Aplikacja została zatrzymana w debugerze, a użytkownik może kontynuować działanie aplikacji lub wykonać operację kroku.</span><span class="sxs-lookup"><span data-stu-id="f0ce9-117">The application was stopped in the debugger and the user either continued the application or performed a step operation.</span></span>

- <span data-ttu-id="f0ce9-118">Debugowanie niezarządzane nie jest włączone.</span><span class="sxs-lookup"><span data-stu-id="f0ce9-118">Unmanaged debugging is not enabled.</span></span>

<span data-ttu-id="f0ce9-119">Aby określić, czy MDA jest aktualnie aktywowany, wyłącz wszystkie punkty przerwania, uruchom ponownie aplikację i zezwól na jej uruchomienie bez zatrzymywania.</span><span class="sxs-lookup"><span data-stu-id="f0ce9-119">To determine if the MDA is being falsely activated, disable all breakpoints, restart the application, and allow it to run without stopping.</span></span> <span data-ttu-id="f0ce9-120">Jeśli zdarzenie MDA nie zostanie aktywowane, prawdopodobnie początkowa aktywacja miała wartość false.</span><span class="sxs-lookup"><span data-stu-id="f0ce9-120">If the MDA is not activated, it is likely the initial activation was false.</span></span> <span data-ttu-id="f0ce9-121">W takim przypadku należy wyłączyć MDA, aby uniknąć interwencji z sesją debugowania.</span><span class="sxs-lookup"><span data-stu-id="f0ce9-121">In this case, disable the MDA to avoid interference with the debugging session.</span></span>

> [!NOTE]
> <span data-ttu-id="f0ce9-122">To zdarzenie MDA jest w domyślnym zestawie dla programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f0ce9-122">This MDA is in the default set for Visual Studio.</span></span> <span data-ttu-id="f0ce9-123">Aby uzyskać informacje na temat sposobu wyłączania usługi MDA, zobacz [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md#enable-and-disable-mdas).</span><span class="sxs-lookup"><span data-stu-id="f0ce9-123">For information about how to disable MDAs, see [Diagnosing Errors with Managed Debugging Assistants](diagnosing-errors-with-managed-debugging-assistants.md#enable-and-disable-mdas).</span></span>

## <a name="resolution"></a><span data-ttu-id="f0ce9-124">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="f0ce9-124">Resolution</span></span>

<span data-ttu-id="f0ce9-125">Przestrzegaj reguł COM dotyczących pompowania komunikatów STA.</span><span class="sxs-lookup"><span data-stu-id="f0ce9-125">Follow COM rules regarding STA message pumping.</span></span>

## <a name="effect-on-the-runtime"></a><span data-ttu-id="f0ce9-126">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="f0ce9-126">Effect on the Runtime</span></span>

<span data-ttu-id="f0ce9-127">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="f0ce9-127">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="f0ce9-128">Raportuje tylko dane dotyczące kontekstów COM.</span><span class="sxs-lookup"><span data-stu-id="f0ce9-128">It only reports data about COM contexts.</span></span>

## <a name="output"></a><span data-ttu-id="f0ce9-129">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="f0ce9-129">Output</span></span>

<span data-ttu-id="f0ce9-130">Komunikat opisujący bieżący kontekst i kontekst docelowy.</span><span class="sxs-lookup"><span data-stu-id="f0ce9-130">A message describing the current context and the target context.</span></span>

## <a name="configuration"></a><span data-ttu-id="f0ce9-131">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="f0ce9-131">Configuration</span></span>

```xml
<mdaConfig>
  <assistants>
    <contextSwitchDeadlock />
  </assistants>
</mdaConfig>
```

## <a name="see-also"></a><span data-ttu-id="f0ce9-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f0ce9-132">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="f0ce9-133">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="f0ce9-133">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="f0ce9-134">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="f0ce9-134">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
