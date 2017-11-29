---
title: "Przestarzałe typy w programie Windows Workflow Foundation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4aebe928-a964-4c1c-abf7-0dbbd3604b13
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 085b0590d08843477c4dff4754791c93110b1fb7
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2017
---
# <a name="deprecated-types-in-windows-workflow-foundation"></a><span data-ttu-id="59e39-102">Przestarzałe typy w programie Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="59e39-102">Deprecated types in Windows Workflow Foundation</span></span>
<span data-ttu-id="59e39-103">W przypadku .NET 4 przepływu pracy zespołu wydawane wszystkich nowych aparatu przepływu pracy w <xref:System.Activities> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="59e39-103">In .NET 4 the Workflow Team released an all new Workflow engine in the <xref:System.Activities> namespace.</span></span> <span data-ttu-id="59e39-104">Wraz z wydaniem .NET 4.5 w wersji Beta firma Microsoft oznaczenie większość typów w "WF 3" <xref:System.Workflow.Activities>, <xref:System.Workflow.ComponentModel>, i <xref:System.Workflow.Runtime> przestrzenie nazw jako przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="59e39-104">With the release of .NET 4.5 Beta we are marking most of the types in the "WF 3" <xref:System.Workflow.Activities>, <xref:System.Workflow.ComponentModel>, and  <xref:System.Workflow.Runtime> namespaces as obsolete.</span></span>  
  
## <a name="obsolete-namespaces-and-tools"></a><span data-ttu-id="59e39-105">Przestarzałe obszary nazw i narzędzia</span><span class="sxs-lookup"><span data-stu-id="59e39-105">Obsolete namespaces and tools</span></span>  
 <span data-ttu-id="59e39-106">Następujące zestawy są co najmniej jeden typ publiczny, które zostaną wycofane:</span><span class="sxs-lookup"><span data-stu-id="59e39-106">The following assemblies have one or more public types that will be deprecated:</span></span>  
  
-   <span data-ttu-id="59e39-107">System.Workflow.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="59e39-107">System.Workflow.Activities.dll</span></span>  
  
-   <span data-ttu-id="59e39-108">System.Workflow.ComponentModel.dll</span><span class="sxs-lookup"><span data-stu-id="59e39-108">System.Workflow.ComponentModel.dll</span></span>  
  
-   <span data-ttu-id="59e39-109">System.Workflow.Runtime.dll</span><span class="sxs-lookup"><span data-stu-id="59e39-109">System.Workflow.Runtime.dll</span></span>  
  
-   <span data-ttu-id="59e39-110">System.WorkflowServices.dll</span><span class="sxs-lookup"><span data-stu-id="59e39-110">System.WorkflowServices.dll</span></span>  
  
-   <span data-ttu-id="59e39-111">Microsoft.Workflow.DebugController.dll</span><span class="sxs-lookup"><span data-stu-id="59e39-111">Microsoft.Workflow.DebugController.dll</span></span>  
  
-   <span data-ttu-id="59e39-112">Microsoft.Workflow.Compiler.exe</span><span class="sxs-lookup"><span data-stu-id="59e39-112">Microsoft.Workflow.Compiler.exe</span></span>  
  
-   <span data-ttu-id="59e39-113">WFC.exe</span><span class="sxs-lookup"><span data-stu-id="59e39-113">Wfc.exe</span></span>  
  
 <span data-ttu-id="59e39-114">W związku z tym klienci korzystający z przestarzałe interfejsy API 3 WF wystąpi ostrzeżenia kompilacji z komunikatu podobnego do następującego:</span><span class="sxs-lookup"><span data-stu-id="59e39-114">As a result, customers who are using the deprecated WF 3 APIs will encounter build warnings with a message similar to the following:</span></span>  
  
 <span data-ttu-id="59e39-115">**Ostrzeżenie BC40000: X jest przestarzała: WF 3 typy są przestarzałe. Zamiast tego użyj WF 4.**</span><span class="sxs-lookup"><span data-stu-id="59e39-115">**Warning BC40000: X is obsolete: WF 3 types are deprecated. Please use WF 4 instead.**</span></span> <span data-ttu-id="59e39-116">Typy zostanie usunięty z programu .NET Framework w przyszłej wersji, ale firma Microsoft nie ustalone jeszcze określonym czasie (nie w 4.5).</span><span class="sxs-lookup"><span data-stu-id="59e39-116">We will remove the types from the .NET Framework in a future release, but we have not yet determined that timeframe (not in 4.5).</span></span> <span data-ttu-id="59e39-117">Ten krok bieżącego umożliwia firmie Microsoft w celu komunikowania się z naszym kierunku naszym klientom i Zezwalaj dużo czasu, można przenieść do nowego modelu WF4.</span><span class="sxs-lookup"><span data-stu-id="59e39-117">This current step allows us to communicate our direction to our customers and allow them plenty of time to move to the new WF4 model.</span></span> <span data-ttu-id="59e39-118">Firma Microsoft oczywiście będzie obsługującej te typy WF 3 w obszarze [firmy Microsoft obsługuje technicznego](http://aka.ms/MicrosoftSupportLifecycle).</span><span class="sxs-lookup"><span data-stu-id="59e39-118">We will, of course, continue to support these WF 3 types under the [Microsoft Support Lifecycle Policy](http://aka.ms/MicrosoftSupportLifecycle).</span></span> <span data-ttu-id="59e39-119">Istniejące aplikacje WF3 będą uruchamiane bez problemu na .NET 4.5 i [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] będzie obsługiwać nowych i istniejących rozwiązań opartych na WF3.</span><span class="sxs-lookup"><span data-stu-id="59e39-119">Existing WF3 applications will run without issue on .NET 4.5, and [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] will support new and existing WF3-based solutions.</span></span>  
  
 <span data-ttu-id="59e39-120">Zasady dotyczące typów w <xref:System.Workflow.Activities.Rules> przestrzeni nazw, które nie mają zastępczy w WF 4.5, nie są przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="59e39-120">Rules related types in the <xref:System.Workflow.Activities.Rules> namespace, which do not have a replacement in WF 4.5, have not been deprecated.</span></span>  
  
 <span data-ttu-id="59e39-121">Klienci, którzy mają zostać poddane migracji aplikacji i WF 4 znajdziesz w Pomocy [wskazówek dotyczących migracji 4 przepływu pracy](migration-guidance.md).</span><span class="sxs-lookup"><span data-stu-id="59e39-121">Customers who want to migrate their applications to WF 4 will find help in the [Workflow 4 Migration Guidance](migration-guidance.md).</span></span>
