---
title: "Wskazówki dotyczące migracji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cb65c132-58c9-4028-b3d4-1efc71d5e60e
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b2424766be26003180f40dfd4b2f4ace2c371154
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="migration-guidance"></a><span data-ttu-id="541a6-102">Wskazówki dotyczące migracji</span><span class="sxs-lookup"><span data-stu-id="541a6-102">Migration Guidance</span></span>
<span data-ttu-id="541a6-103">W [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], firma Microsoft udostępnia drugą wersją główną [!INCLUDE[wf](../../../includes/wf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="541a6-103">In the [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], Microsoft is releasing the second major version of [!INCLUDE[wf](../../../includes/wf-md.md)].</span></span> [!INCLUDE[wf1](../../../includes/wf1-md.md)]<span data-ttu-id="541a6-104">została wydana w [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] (to uwzględnione typy w przestrzeniach nazw System.Workflow.*; teraz nazywane WF3) i rozszerzony w [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="541a6-104"> was released in [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] (this included the types in the System.Workflow.* namespaces; now referred to as WF3) and enhanced in [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)].</span></span> <span data-ttu-id="541a6-105">WF3 jest również częścią [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], ale istnieją obok nowej technologii przepływu pracy (typy węzła System.Activities.\* przestrzeni nazw; określone jako WF4).</span><span class="sxs-lookup"><span data-stu-id="541a6-105">WF3 is also part of the [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], but it exists there alongside new workflow technology (the types in the System.Activities.\* namespaces; referred to as WF4).</span></span> <span data-ttu-id="541a6-106">Podczas określania, kiedy należy przyjąć WF4, należy najpierw rozpoznaje, że kontrolować czas.</span><span class="sxs-lookup"><span data-stu-id="541a6-106">When considering when to adopt WF4, it is important to first recognize that you control the timing.</span></span>  
  
-   <span data-ttu-id="541a6-107">WF3 jest w pełni obsługiwane częścią [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="541a6-107">WF3 is a fully supported part of the [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].</span></span>  
  
-   <span data-ttu-id="541a6-108">Aplikacje WF3 działać na [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] bez żadnych modyfikacji i nadal w pełni obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="541a6-108">WF3 applications run on the [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] without modification and continue to be fully supported.</span></span>  
  
-   <span data-ttu-id="541a6-109">Można tworzyć nowe aplikacje WF3 i istniejące aplikacje mogą być edytowane w [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] i są w pełni obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="541a6-109">New WF3 applications can be created and your existing applications can be edited in [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] and are fully supported.</span></span>  
  
 <span data-ttu-id="541a6-110">W związku z tym decyzji o przyjęciu programu .NET Framework 4 jest całkowicie niezależna od programu decyzji o przeniesieniu na WF4 (System.Activities.*) z WF3 (System.Workflow.\*).</span><span class="sxs-lookup"><span data-stu-id="541a6-110">Thus, the decision to adopt the .NET Framework 4 is decoupled from your decision to move to WF4 (System.Activities.*) from WF3 (System.Workflow.\*).</span></span> <span data-ttu-id="541a6-111">Ten temat zawiera łącza do wskazówek dotyczących migracji WF, który zawiera informacje o pracy z WF3 i WF4.</span><span class="sxs-lookup"><span data-stu-id="541a6-111">This topic provides links to WF migration guidance that provides information about working with WF3 and WF4.</span></span>  
  
## <a name="wf-migration-whitepapers-and-cookbooks"></a><span data-ttu-id="541a6-112">Oficjalne dokumenty programu WF migracji i Cookbooks</span><span class="sxs-lookup"><span data-stu-id="541a6-112">WF Migration Whitepapers and Cookbooks</span></span>  
 <span data-ttu-id="541a6-113">[Omówienie migracji WF](http://go.microsoft.com/fwlink/?LinkId=153873) temat zawiera ogólne omówienie relacji między strategie WF3 i WF4 i migracji.</span><span class="sxs-lookup"><span data-stu-id="541a6-113">The [WF Migration Overview](http://go.microsoft.com/fwlink/?LinkId=153873) topic provides a broad overview of the relationship between WF3 and WF4 and migration strategies.</span></span> <span data-ttu-id="541a6-114">Tematy uzupełniające przejść do szczegółów w określonych tematów.</span><span class="sxs-lookup"><span data-stu-id="541a6-114">Companion topics drill into specific topics.</span></span>  
  
 [<span data-ttu-id="541a6-115">Omówienie migracji WF</span><span class="sxs-lookup"><span data-stu-id="541a6-115">WF Migration Overview</span></span>](http://go.microsoft.com/fwlink/?LinkId=153873)  
 <span data-ttu-id="541a6-116">Opisuje relację między WF3 i WF4 i opcje, które mają jako użytkownik lub potencjalne przepływu pracy technologii .NET 4.</span><span class="sxs-lookup"><span data-stu-id="541a6-116">Describes the relationship between WF3 and WF4, and the choices you have as a user or a potential user of workflow technology in .NET 4.</span></span>  
  
 [<span data-ttu-id="541a6-117">Migracja WF: Najlepsze rozwiązania dotyczące WF3 programowanie</span><span class="sxs-lookup"><span data-stu-id="541a6-117">WF Migration: Best Practices for WF3 Development</span></span>](http://go.microsoft.com/fwlink/?LinkId=153852)  
 <span data-ttu-id="541a6-118">W tym artykule omówiono sposób projektowania artefakty WF3, dlatego może być łatwiej migracji do WF4.</span><span class="sxs-lookup"><span data-stu-id="541a6-118">Discusses how to design WF3 artifacts so they can be more easily migrated to WF4.</span></span>  
  
 [<span data-ttu-id="541a6-119">Wskazówki dotyczące WF: reguły</span><span class="sxs-lookup"><span data-stu-id="541a6-119">WF Guidance: Rules</span></span>](http://go.microsoft.com/fwlink/?LinkId=153854)  
 <span data-ttu-id="541a6-120">Omówiono sposoby dostosowania związane z reguły inwestycji do przodu do [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="541a6-120">Discusses how to bring rules-related investments forward into [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] solutions.</span></span>  
  
 [<span data-ttu-id="541a6-121">Wskazówki dotyczące WF: Automatu stanów</span><span class="sxs-lookup"><span data-stu-id="541a6-121">WF Guidance: State Machine</span></span>](http://go.microsoft.com/fwlink/?LinkId=153855)  
 <span data-ttu-id="541a6-122">W tym artykule omówiono przepływ sterowania WF4 modelowania w przypadku braku aktywności komputera stanu.</span><span class="sxs-lookup"><span data-stu-id="541a6-122">Discusses WF4 control flow modeling in the absence of a State-Machine activity.</span></span>  
  
 <span data-ttu-id="541a6-123">Należy pamiętać, że w tych wskazówkach dotyczy tylko projektów przepływu pracy, które odnoszą się do programu .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="541a6-123">Note that this guidance only applies to workflow projects that target .NET Framework 4.</span></span> <span data-ttu-id="541a6-124">Stan pracy maszyny zostały dodane w programie .NET 4.0.1 wraz z wydaniem Platform Update 1 i zostały zawarte w ramach programu .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="541a6-124">State Machine workflows were added in .NET 4.0.1 with the release of Platform Update 1, and were included as part of .NET Framework 4.5.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="541a6-125">Stan maszyny z przepływów pracy w programie .NET 4.0.1 — 4.0.3 i .NET Framework 4.5, zobacz [aktualizacji dla programu Microsoft .NET Framework 4 funkcji 4.0.1](http://msdn.microsoft.com/en-us/de3297bd-c3e1-4126-95be-2ed7fe2a98fc) i [przepływy pracy maszyny stanu](../../../docs/framework/windows-workflow-foundation/state-machine-workflows.md).</span><span class="sxs-lookup"><span data-stu-id="541a6-125"> state machine workflows in .NET 4.0.1 - 4.0.3 and .NET Framework 4.5, see [Update 4.0.1 for Microsoft .NET Framework 4 Features](http://msdn.microsoft.com/en-us/de3297bd-c3e1-4126-95be-2ed7fe2a98fc) and [State Machine Workflows](../../../docs/framework/windows-workflow-foundation/state-machine-workflows.md).</span></span>  
  
 [<span data-ttu-id="541a6-126">WF Cookbook migracji: Niestandardowe działania</span><span class="sxs-lookup"><span data-stu-id="541a6-126">WF Migration Cookbook: Custom Activities</span></span>](http://go.microsoft.com/fwlink/?LinkId=153856)  
 <span data-ttu-id="541a6-127">Zawiera instrukcje dotyczące zmiany projektu WF3 niestandardowych działań na WF4 i przykłady.</span><span class="sxs-lookup"><span data-stu-id="541a6-127">Provides examples and instructions for redesigning WF3 custom activities on WF4.</span></span>  
  
 [<span data-ttu-id="541a6-128">Programu WF Cookbook migracji: Zaawansowane niestandardowych działań</span><span class="sxs-lookup"><span data-stu-id="541a6-128">WF Migration Cookbook: Advanced Custom Activities</span></span>](http://go.microsoft.com/fwlink/?LinkId=275560)  
 <span data-ttu-id="541a6-129">Zawiera wskazówki dotyczące zmodyfikowanie zaawansowanych WF3 niestandardowych działań korzystających z kolejek WF3 i harmonogram działania podrzędne jako WF4 działań niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="541a6-129">Provides guidance for redesigning advanced WF3 custom activities that use WF3 queues and schedule child activities as WF4 custom activities.</span></span>  
  
 [<span data-ttu-id="541a6-130">WF migracji Cookbook: przepływów pracy</span><span class="sxs-lookup"><span data-stu-id="541a6-130">WF Migration Cookbook: Workflows</span></span>](http://go.microsoft.com/fwlink/?LinkId=153858)  
 <span data-ttu-id="541a6-131">Zawiera instrukcje dotyczące zmiany projektu przepływów pracy WF3 na WF4 i przykłady.</span><span class="sxs-lookup"><span data-stu-id="541a6-131">Provides examples and instructions for redesigning WF3 workflows on WF4.</span></span>  
  
 [<span data-ttu-id="541a6-132">WF Cookbook migracji: Hosting przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="541a6-132">WF Migration Cookbook: Workflow Hosting</span></span>](http://go.microsoft.com/fwlink/?LinkId=275561)  
 <span data-ttu-id="541a6-133">Zawiera wskazówki dotyczące zmodyfikowanie kodu hostingu WF3 jako kod obsługi WF4.</span><span class="sxs-lookup"><span data-stu-id="541a6-133">Provides guidance for redesigning WF3 hosting code as WF4 hosting code.</span></span> <span data-ttu-id="541a6-134">Celem jest, aby pokrywał się podstawowe różnice w przepływie pracy hosting między WF3 i WF4.</span><span class="sxs-lookup"><span data-stu-id="541a6-134">The goal is to cover the key differences in workflow hosting between WF3 and WF4.</span></span>  
  
 [<span data-ttu-id="541a6-135">WF Cookbook migracji: Śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="541a6-135">WF Migration Cookbook: Workflow Tracking</span></span>](http://go.microsoft.com/fwlink/?LinkId=275562)  
 <span data-ttu-id="541a6-136">Zawiera wskazówki dotyczące zmiany projektu kod śledzenia WF3 i konfiguracji przy użyciu równoważne WF4 kod śledzenia i konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="541a6-136">Provides guidance for redesigning WF3 tracking code and configuration using equivalent WF4 tracking code and configuration.</span></span>  
  
 [<span data-ttu-id="541a6-137">WF wskazówek: Usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="541a6-137">WF Guidance: Workflow Services</span></span>](http://go.microsoft.com/fwlink/?LinkId=275564)  
 <span data-ttu-id="541a6-138">Udostępnia zorientowane na przykład szczegółowe instrukcje dotyczące zmiany projektu przepływy pracy, które implementują Windows Communication Foundation (WCF) usługi sieci web (nazywane usług przepływu pracy) utworzone w WF3 WF4, na potrzeby typowych scenariuszy dla out-of-box działania.</span><span class="sxs-lookup"><span data-stu-id="541a6-138">Provides example-oriented step-by-step instructions for redesigning workflows that implement Windows Communication Foundation (WCF) web services (commonly referred to as workflow services) created in WF3 to use WF4, for common scenarios for out-of-box activities.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="541a6-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="541a6-139">See Also</span></span>  
 <xref:System.Activities.Statements.Interop>
