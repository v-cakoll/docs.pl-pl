---
title: "Porady: odbieranie powiadomień podczas zegar &#39; s zmiany stanu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clocks [WPF], notification of state changes
- notifications [WPF], clocks' state changes
ms.assetid: ecb10fc9-d0c2-45c3-b0a1-7b11baa733da
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f59fddb1add29d52ccba6fc8b8ce84938b53a1c2
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-receive-notification-when-a-clock39s-state-changes"></a><span data-ttu-id="f548f-102">Porady: odbieranie powiadomień podczas zegar &#39; s zmiany stanu</span><span class="sxs-lookup"><span data-stu-id="f548f-102">How to: Receive Notification When a Clock&#39;s State Changes</span></span>
<span data-ttu-id="f548f-103">Zegar <xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated> zdarzenie po jego <xref:System.Windows.Media.Animation.Clock.CurrentState%2A> staje się nieprawidłowy, np. gdy zegar uruchomienia lub zatrzymania.</span><span class="sxs-lookup"><span data-stu-id="f548f-103">A clock's <xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated> event occurs when its <xref:System.Windows.Media.Animation.Clock.CurrentState%2A> becomes invalid, such as when the clock starts or stops.</span></span> <span data-ttu-id="f548f-104">Możesz zarejestrować dla tego zdarzenia z bezpośrednio za pomocą <xref:System.Windows.Media.Animation.Clock>, lub możesz zarejestrować za pomocą <xref:System.Windows.Media.Animation.Timeline>.</span><span class="sxs-lookup"><span data-stu-id="f548f-104">You can register for this event with directly using a <xref:System.Windows.Media.Animation.Clock>, or you can register using a <xref:System.Windows.Media.Animation.Timeline>.</span></span>  
  
 <span data-ttu-id="f548f-105">W poniższym przykładzie <xref:System.Windows.Media.Animation.Storyboard> i dwa <xref:System.Windows.Media.Animation.DoubleAnimation> obiekty służą do animowania szerokość dwóch prostokątów.</span><span class="sxs-lookup"><span data-stu-id="f548f-105">In the following example, a <xref:System.Windows.Media.Animation.Storyboard> and two <xref:System.Windows.Media.Animation.DoubleAnimation> objects are used to animate the width of two rectangles.</span></span> <span data-ttu-id="f548f-106"><xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> Zdarzeń służy do nasłuchiwania zmian stanu zegara.</span><span class="sxs-lookup"><span data-stu-id="f548f-106">The <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> event is used to listen for clock state changes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f548f-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="f548f-107">Example</span></span>  
 [!code-xaml[timingbehaviors_snip#_graphicsmm_StateExampleMarkupWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StateExample.xaml#_graphicsmm_stateexamplemarkupwholepage)]  
  
 [!code-csharp[timingbehaviors_snip#_graphicsmm_StateEventHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StateExample.xaml.cs#_graphicsmm_stateeventhandlers)]
 [!code-vb[timingbehaviors_snip#_graphicsmm_StateEventHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/stateexample.xaml.vb#_graphicsmm_stateeventhandlers)]  
  
 <span data-ttu-id="f548f-108">Na poniższej ilustracji przedstawiono różne stany animacji wprowadzili nadrzędnej osi czasu (*scenorysu*) realizowany.</span><span class="sxs-lookup"><span data-stu-id="f548f-108">The following illustration shows the different states the animations enter as the parent timeline (*Storyboard*) progresses.</span></span>  
  
 <span data-ttu-id="f548f-109">![Zegar stanów dla scenorysu z dwóch animacje](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-3timelines.png "graphicsmm_3timelines")</span><span class="sxs-lookup"><span data-stu-id="f548f-109">![Clock states for a Storyboard with two animations](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-3timelines.png "graphicsmm_3timelines")</span></span>  
  
 <span data-ttu-id="f548f-110">W poniższej tabeli przedstawiono czas, w którym *Animation1*w <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> generowane zdarzenie:</span><span class="sxs-lookup"><span data-stu-id="f548f-110">The following table shows the times at which *Animation1*'s <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> event fires:</span></span>  
  
||||||||  
|-|-|-|-|-|-|-|  
|<span data-ttu-id="f548f-111">Czas (w sekundach)</span><span class="sxs-lookup"><span data-stu-id="f548f-111">Time (Seconds)</span></span>|<span data-ttu-id="f548f-112">1</span><span class="sxs-lookup"><span data-stu-id="f548f-112">1</span></span>|<span data-ttu-id="f548f-113">10</span><span class="sxs-lookup"><span data-stu-id="f548f-113">10</span></span>|<span data-ttu-id="f548f-114">19</span><span class="sxs-lookup"><span data-stu-id="f548f-114">19</span></span>|<span data-ttu-id="f548f-115">21</span><span class="sxs-lookup"><span data-stu-id="f548f-115">21</span></span>|<span data-ttu-id="f548f-116">30</span><span class="sxs-lookup"><span data-stu-id="f548f-116">30</span></span>|<span data-ttu-id="f548f-117">39</span><span class="sxs-lookup"><span data-stu-id="f548f-117">39</span></span>|  
|<span data-ttu-id="f548f-118">Stan</span><span class="sxs-lookup"><span data-stu-id="f548f-118">State</span></span>|<span data-ttu-id="f548f-119">Aktywne</span><span class="sxs-lookup"><span data-stu-id="f548f-119">Active</span></span>|<span data-ttu-id="f548f-120">Aktywne</span><span class="sxs-lookup"><span data-stu-id="f548f-120">Active</span></span>|<span data-ttu-id="f548f-121">Zatrzymany</span><span class="sxs-lookup"><span data-stu-id="f548f-121">Stopped</span></span>|<span data-ttu-id="f548f-122">Aktywne</span><span class="sxs-lookup"><span data-stu-id="f548f-122">Active</span></span>|<span data-ttu-id="f548f-123">Aktywne</span><span class="sxs-lookup"><span data-stu-id="f548f-123">Active</span></span>|<span data-ttu-id="f548f-124">Zatrzymany</span><span class="sxs-lookup"><span data-stu-id="f548f-124">Stopped</span></span>|  
  
 <span data-ttu-id="f548f-125">W poniższej tabeli przedstawiono czas, w którym *Animation2*w <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> generowane zdarzenie:</span><span class="sxs-lookup"><span data-stu-id="f548f-125">The following table shows the times at which *Animation2*'s <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> event fires:</span></span>  
  
||||||||||  
|-|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="f548f-126">Czas (w sekundach)</span><span class="sxs-lookup"><span data-stu-id="f548f-126">Time (Seconds)</span></span>|<span data-ttu-id="f548f-127">1</span><span class="sxs-lookup"><span data-stu-id="f548f-127">1</span></span>|<span data-ttu-id="f548f-128">9</span><span class="sxs-lookup"><span data-stu-id="f548f-128">9</span></span>|<span data-ttu-id="f548f-129">11</span><span class="sxs-lookup"><span data-stu-id="f548f-129">11</span></span>|<span data-ttu-id="f548f-130">19</span><span class="sxs-lookup"><span data-stu-id="f548f-130">19</span></span>|<span data-ttu-id="f548f-131">21</span><span class="sxs-lookup"><span data-stu-id="f548f-131">21</span></span>|<span data-ttu-id="f548f-132">29</span><span class="sxs-lookup"><span data-stu-id="f548f-132">29</span></span>|<span data-ttu-id="f548f-133">31</span><span class="sxs-lookup"><span data-stu-id="f548f-133">31</span></span>|<span data-ttu-id="f548f-134">39</span><span class="sxs-lookup"><span data-stu-id="f548f-134">39</span></span>|  
|<span data-ttu-id="f548f-135">Stan</span><span class="sxs-lookup"><span data-stu-id="f548f-135">State</span></span>|<span data-ttu-id="f548f-136">Aktywne</span><span class="sxs-lookup"><span data-stu-id="f548f-136">Active</span></span>|<span data-ttu-id="f548f-137">Wypełnianie</span><span class="sxs-lookup"><span data-stu-id="f548f-137">Filling</span></span>|<span data-ttu-id="f548f-138">Aktywne</span><span class="sxs-lookup"><span data-stu-id="f548f-138">Active</span></span>|<span data-ttu-id="f548f-139">Zatrzymany</span><span class="sxs-lookup"><span data-stu-id="f548f-139">Stopped</span></span>|<span data-ttu-id="f548f-140">Aktywne</span><span class="sxs-lookup"><span data-stu-id="f548f-140">Active</span></span>|<span data-ttu-id="f548f-141">Wypełnianie</span><span class="sxs-lookup"><span data-stu-id="f548f-141">Filling</span></span>|<span data-ttu-id="f548f-142">Aktywne</span><span class="sxs-lookup"><span data-stu-id="f548f-142">Active</span></span>|<span data-ttu-id="f548f-143">Zatrzymany</span><span class="sxs-lookup"><span data-stu-id="f548f-143">Stopped</span></span>|  
  
 <span data-ttu-id="f548f-144">Zwróć uwagę, że *Animation1*w <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> zdarzenia generowane na 10 sekund, mimo że jego stan pozostaje <xref:System.Windows.Media.Animation.ClockState.Active>.</span><span class="sxs-lookup"><span data-stu-id="f548f-144">Notice that *Animation1*'s  <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> event fires at 10 seconds, even though its state remains <xref:System.Windows.Media.Animation.ClockState.Active>.</span></span> <span data-ttu-id="f548f-145">Jest to spowodowane jego stan zmienił się na 10 sekund, ale zmieniła się z tym <xref:System.Windows.Media.Animation.ClockState.Active> do <xref:System.Windows.Media.Animation.ClockState.Filling> , a następnie z powrotem do <xref:System.Windows.Media.Animation.ClockState.Active> w tej samej osi.</span><span class="sxs-lookup"><span data-stu-id="f548f-145">That's because its state changed at 10 seconds, but it changed from <xref:System.Windows.Media.Animation.ClockState.Active> to <xref:System.Windows.Media.Animation.ClockState.Filling> and then back to <xref:System.Windows.Media.Animation.ClockState.Active> in the same tick.</span></span>
