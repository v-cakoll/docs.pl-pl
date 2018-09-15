---
title: Zmienna śledzenie argumentów i
ms.date: 03/30/2017
ms.assetid: 8f3d9d30-d899-49aa-b7ce-a8d0d32c4ff0
ms.openlocfilehash: 45ed3761cd7ead82650023b93a2f32a43e847339
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/15/2018
ms.locfileid: "45646166"
---
# <a name="variable-and-argument-tracking"></a><span data-ttu-id="50794-102">Zmienna śledzenie argumentów i</span><span class="sxs-lookup"><span data-stu-id="50794-102">Variable and Argument Tracking</span></span>
<span data-ttu-id="50794-103">Podczas śledzenia wykonywania przepływu pracy, jest często przydatne w celu wyodrębnienia danych.</span><span class="sxs-lookup"><span data-stu-id="50794-103">When tracking the execution of a workflow, it is often useful to extract data.</span></span> <span data-ttu-id="50794-104">Umożliwia to dodatkowy kontekst podczas uzyskiwania dostępu do śledzenia rekordów post wykonywania.</span><span class="sxs-lookup"><span data-stu-id="50794-104">This provides additional context when accessing a tracking record post execution.</span></span> <span data-ttu-id="50794-105">W [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], można wyodrębnić wszystkie widoczne zmiennej lub argumentu w zakresie wszelkie działania w przepływie pracy przy użyciu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="50794-105">In [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], you can extract any visible variable or argument within the scope of any activity in a workflow using tracking.</span></span> <span data-ttu-id="50794-106">Profile śledzenia ułatwiają do wyodrębniania danych.</span><span class="sxs-lookup"><span data-stu-id="50794-106">Tracking profiles make it easy to extract data.</span></span>  
  
## <a name="variables-and-arguments"></a><span data-ttu-id="50794-107">Zmienne i argumenty</span><span class="sxs-lookup"><span data-stu-id="50794-107">Variables and Arguments</span></span>  
 <span data-ttu-id="50794-108">Zmienne i argumenty są wyodrębniane, gdy działanie wyemituje ActivityStateRecord.</span><span class="sxs-lookup"><span data-stu-id="50794-108">Variables and arguments are extracted when an activity emits an ActivityStateRecord.</span></span>  <span data-ttu-id="50794-109">Zmienna jest dostępna do wyodrębnienia, tylko wtedy, gdy jest w zakresie działania.</span><span class="sxs-lookup"><span data-stu-id="50794-109">A variable is available for extraction only if it is within the scope of the activity.</span></span> <span data-ttu-id="50794-110">Zmienna ma zostać wyodrębniony w ramach działania jest określony w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="50794-110">A variable to be extracted within an activity is specified in the following manner:</span></span>  
  
-   <span data-ttu-id="50794-111">Jeśli zmienna jest określona przez nazwę zmiennej, śledzenie wygląda zmiennej w ramach bieżącego działania, które są śledzone i działania nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="50794-111">If a variable is specified by the variable name, then tracking looks for the variable within the current activity being tracked and in parent activities.</span></span> <span data-ttu-id="50794-112">Zmienna jest przeszukiwany w bieżącym zakresie działania, a także w zakresie nadrzędnym.</span><span class="sxs-lookup"><span data-stu-id="50794-112">The variable is searched in current activity scope and in parent scope.</span></span>  
  
-   <span data-ttu-id="50794-113">Jeśli określono za pomocą nazwy zmiennych, które ma zostać wyodrębniony = "\*", a następnie są wyodrębniane wszystkie zmienne w obrębie bieżącego działania, które są śledzone.</span><span class="sxs-lookup"><span data-stu-id="50794-113">If variables to be extracted are specified by using name="\*", then all variables within the current activity being tracked are extracted.</span></span> <span data-ttu-id="50794-114">W tym przypadku zmienne znajdują się w zakresie ale zdefiniowany w elemencie nadrzędnym, które nie zostały wyodrębnione działań.</span><span class="sxs-lookup"><span data-stu-id="50794-114">In this case variables that are in scope but defined in parent activities are not extracted.</span></span>  
  
 <span data-ttu-id="50794-115">Podczas wyodrębniania argumentów, argumenty wyodrębnione zależą od stanu działania.</span><span class="sxs-lookup"><span data-stu-id="50794-115">When extracting arguments, the arguments extracted depend on the state of the activity.</span></span> <span data-ttu-id="50794-116">Jeśli stan działania jest wykonywanie, następnie tylko `InArguments` są dostępne do wyodrębnienia.</span><span class="sxs-lookup"><span data-stu-id="50794-116">When the state of an activity is Executing, then only the `InArguments` are available for extraction.</span></span> <span data-ttu-id="50794-117">Dla dowolnego innego działania stanu (zamknięte, Faulted anulowane) wszystkie argumenty InArguments i OutArguments, są dostępne do wyodrębnienia.</span><span class="sxs-lookup"><span data-stu-id="50794-117">For any other activity state (Closed, Faulted, Canceled), all arguments, both InArguments and OutArguments, are available for extraction.</span></span>  
  
 <span data-ttu-id="50794-118">W poniższym przykładzie pokazano kwerendą stanu działania, który wyodrębnia zmienne i argumenty podczas działania `Closed` rekord śledzenia jest emitowane.</span><span class="sxs-lookup"><span data-stu-id="50794-118">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="50794-119">Zmienne i argumenty wyodrębniania tylko z <xref:System.Activities.Tracking.ActivityStateRecord> i w związku z tym subskrybują w ramach śledzenia profilu przy użyciu <xref:System.Activities.Tracking.ActivityStateQuery>.</span><span class="sxs-lookup"><span data-stu-id="50794-119">Variables and arguments can be extracted only with an <xref:System.Activities.Tracking.ActivityStateRecord> and thus are subscribed to within a tracking profile using <xref:System.Activities.Tracking.ActivityStateQuery>.</span></span>  
  
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
  
## <a name="protecting-information-stored-within-variables-and-arguments"></a><span data-ttu-id="50794-120">Ochrona informacji przechowywanych w ramach zmienne i argumenty</span><span class="sxs-lookup"><span data-stu-id="50794-120">Protecting Information Stored Within Variables and Arguments</span></span>  
 <span data-ttu-id="50794-121">Śledzone zmiennej lub argumentu jest domyślnie widoczny przez środowisko uruchomieniowe programu WF.</span><span class="sxs-lookup"><span data-stu-id="50794-121">A tracked variable or argument is by default made visible by the WF runtime.</span></span> <span data-ttu-id="50794-122">Projektant przepływu pracy można go chronić przed dostępem, wykonując następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="50794-122">A workflow developer can protect it from being accessed by taking the following steps:</span></span>  
  
1.  <span data-ttu-id="50794-123">Szyfrowanie wartość zmiennej.</span><span class="sxs-lookup"><span data-stu-id="50794-123">Encrypt the value of a variable.</span></span>  
  
2.  <span data-ttu-id="50794-124">Formant tworzenia profilu śledzenia, aby uniknąć wyodrębniania zmiennej lub argumentu.</span><span class="sxs-lookup"><span data-stu-id="50794-124">Control the authoring of a tracking profile to prevent the extraction of a variable or argument.</span></span>  
  
3.  <span data-ttu-id="50794-125">Dla uczestników śledzenia niestandardowego upewnij się, że kod WF nie ujawniają poufne informacje, które są przechowywane w zmiennych lub argumentów.</span><span class="sxs-lookup"><span data-stu-id="50794-125">For custom tracking participants ensure that the WF code does not disclose sensitive information that is stored in variables or arguments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50794-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="50794-126">See Also</span></span>  
 [<span data-ttu-id="50794-127">Windows Server AppFabric monitorowania</span><span class="sxs-lookup"><span data-stu-id="50794-127">Windows Server App Fabric Monitoring</span></span>](https://go.microsoft.com/fwlink/?LinkId=201273)  
 [<span data-ttu-id="50794-128">Monitorowanie aplikacji przy użyciu rozwiązania AppFabric</span><span class="sxs-lookup"><span data-stu-id="50794-128">Monitoring Applications with App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkId=201275)
