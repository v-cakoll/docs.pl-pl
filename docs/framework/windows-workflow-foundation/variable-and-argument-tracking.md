---
title: "Zmienna i śledzenia argumentu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8f3d9d30-d899-49aa-b7ce-a8d0d32c4ff0
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 76a9d169b7b8b551685f67288667036ad7b4c87b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="variable-and-argument-tracking"></a><span data-ttu-id="83930-102">Zmienna i śledzenia argumentu</span><span class="sxs-lookup"><span data-stu-id="83930-102">Variable and Argument Tracking</span></span>
<span data-ttu-id="83930-103">Podczas śledzenia wykonywanie przepływu pracy, często jest przydatne w celu wyodrębnienia danych.</span><span class="sxs-lookup"><span data-stu-id="83930-103">When tracking the execution of a workflow, it is often useful to extract data.</span></span> <span data-ttu-id="83930-104">Zapewnia dodatkowy kontekst podczas uzyskiwania dostępu do wykonywania post rekordu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="83930-104">This provides additional context when accessing a tracking record post execution.</span></span> <span data-ttu-id="83930-105">W [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], można wyodrębnić wszelkie widoczne zmiennej lub argumentu w zakresie wszystkie działania w przepływie pracy za pomocą śledzenia.</span><span class="sxs-lookup"><span data-stu-id="83930-105">In [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], you can extract any visible variable or argument within the scope of any activity in a workflow using tracking.</span></span> <span data-ttu-id="83930-106">Śledzenie profile ułatwiają wyodrębnić dane.</span><span class="sxs-lookup"><span data-stu-id="83930-106">Tracking profiles make it easy to extract data.</span></span>  
  
## <a name="variables-and-arguments"></a><span data-ttu-id="83930-107">Argumenty i zmienne</span><span class="sxs-lookup"><span data-stu-id="83930-107">Variables and Arguments</span></span>  
 <span data-ttu-id="83930-108">Gdy działanie emituje ActivityStateRecord są wyodrębniane zmienne i argumentów.</span><span class="sxs-lookup"><span data-stu-id="83930-108">Variables and arguments are extracted when an activity emits an ActivityStateRecord.</span></span>  <span data-ttu-id="83930-109">Zmienna jest niedostępna do wyodrębnienia tylko wtedy, gdy znajduje się w zakresie działania.</span><span class="sxs-lookup"><span data-stu-id="83930-109">A variable is available for extraction only if it is within the scope of the activity.</span></span> <span data-ttu-id="83930-110">Zmienna do wyodrębnienia w działaniu jest określony w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="83930-110">A variable to be extracted within an activity is specified in the following manner:</span></span>  
  
-   <span data-ttu-id="83930-111">Jeśli zmienna jest określona przez nazwę zmiennej, śledzenie wygląda zmiennej w ramach bieżącego działania jest włączone śledzenie i działania nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="83930-111">If a variable is specified by the variable name, then tracking looks for the variable within the current activity being tracked and in parent activities.</span></span> <span data-ttu-id="83930-112">Zmienna jest przeszukiwane w bieżącym zakresie działania i w zakresie nadrzędnym.</span><span class="sxs-lookup"><span data-stu-id="83930-112">The variable is searched in current activity scope and in parent scope.</span></span>  
  
-   <span data-ttu-id="83930-113">Jeśli zmienne, które mają zostać wyodrębnione są określane przy użyciu nazwy = "*", a następnie są wyodrębniane wszystkie zmienne w ramach bieżącego działania, które są śledzone.</span><span class="sxs-lookup"><span data-stu-id="83930-113">If variables to be extracted are specified by using name="*", then all variables within the current activity being tracked are extracted.</span></span> <span data-ttu-id="83930-114">W takim przypadku zmienne znajdują się w zakresie ale zdefiniowany w obiekcie nadrzędnym, które nie są wyodrębniane działań.</span><span class="sxs-lookup"><span data-stu-id="83930-114">In this case variables that are in scope but defined in parent activities are not extracted.</span></span>  
  
 <span data-ttu-id="83930-115">Podczas wyodrębniania argumenty, argumenty wyodrębnione zależą od stanu działania.</span><span class="sxs-lookup"><span data-stu-id="83930-115">When extracting arguments, the arguments extracted depend on the state of the activity.</span></span> <span data-ttu-id="83930-116">Gdy stan działania to Executing, następnie tylko `InArguments` są dostępne do wyodrębnienia.</span><span class="sxs-lookup"><span data-stu-id="83930-116">When the state of an activity is Executing, then only the `InArguments` are available for extraction.</span></span> <span data-ttu-id="83930-117">Wszystkie inne działania stanu (zamknięte, Faulted Canceled) wszystkie argumenty, zarówno InArguments i OutArguments, są dostępne do wyodrębnienia.</span><span class="sxs-lookup"><span data-stu-id="83930-117">For any other activity state (Closed, Faulted, Canceled), all arguments, both InArguments and OutArguments, are available for extraction.</span></span>  
  
 <span data-ttu-id="83930-118">W poniższym przykładzie przedstawiono kwerendy stanu działania, która wyodrębnia zmiennych i argumenty podczas działania `Closed` śledzenia rekord jest emitowany.</span><span class="sxs-lookup"><span data-stu-id="83930-118">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="83930-119">Argumenty i zmienne można wyodrębnić tylko z <xref:System.Activities.Tracking.ActivityStateRecord> i w związku z tym jest subskrybowana w ramach śledzenia profilowania za pomocą <xref:System.Activities.Tracking.ActivityStateQuery>.</span><span class="sxs-lookup"><span data-stu-id="83930-119">Variables and arguments can be extracted only with an <xref:System.Activities.Tracking.ActivityStateRecord> and thus are subscribed to within a tracking profile using <xref:System.Activities.Tracking.ActivityStateQuery>.</span></span>  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <variables>  
    <variable name="FromAddress"/>  
  </variables>  
  <arguments>  
    <argument name="Result"/>  
  </arguments>  
</activityStateQuery>  
```  
  
## <a name="protecting-information-stored-within-variables-and-arguments"></a><span data-ttu-id="83930-120">Chroni dane przechowywane w zmiennych i argumenty</span><span class="sxs-lookup"><span data-stu-id="83930-120">Protecting Information Stored Within Variables and Arguments</span></span>  
 <span data-ttu-id="83930-121">Śledzonych zmiennej lub argumentu jest domyślnie widoczne przez środowisko uruchomieniowe programu WF.</span><span class="sxs-lookup"><span data-stu-id="83930-121">A tracked variable or argument is by default made visible by the WF runtime.</span></span> <span data-ttu-id="83930-122">Projektant przepływu pracy można chronić przed dostępem w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="83930-122">A workflow developer can protect it from being accessed by taking the following steps:</span></span>  
  
1.  <span data-ttu-id="83930-123">Wartość zmiennej szyfrowania.</span><span class="sxs-lookup"><span data-stu-id="83930-123">Encrypt the value of a variable.</span></span>  
  
2.  <span data-ttu-id="83930-124">Formant tworzenia profilu śledzenia, aby zapobiec wyodrębniania zmiennej lub argumentu.</span><span class="sxs-lookup"><span data-stu-id="83930-124">Control the authoring of a tracking profile to prevent the extraction of a variable or argument.</span></span>  
  
3.  <span data-ttu-id="83930-125">Uczestników śledzenia niestandardowych upewnij się, że kodzie WF nie ujawnia poufne informacje, które są przechowywane w zmiennych lub argumentów.</span><span class="sxs-lookup"><span data-stu-id="83930-125">For custom tracking participants ensure that the WF code does not disclose sensitive information that is stored in variables or arguments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83930-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="83930-126">See Also</span></span>  
 [<span data-ttu-id="83930-127">Windows Server AppFabric monitorowania</span><span class="sxs-lookup"><span data-stu-id="83930-127">Windows Server App Fabric Monitoring</span></span>](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [<span data-ttu-id="83930-128">Monitorowanie aplikacji przy użyciu rozwiązania AppFabric</span><span class="sxs-lookup"><span data-stu-id="83930-128">Monitoring Applications with App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkId=201275)
