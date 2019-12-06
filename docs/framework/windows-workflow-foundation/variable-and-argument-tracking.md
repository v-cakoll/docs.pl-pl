---
title: Śledzenie argumentów i zmiennych
ms.date: 03/30/2017
ms.assetid: 8f3d9d30-d899-49aa-b7ce-a8d0d32c4ff0
ms.openlocfilehash: c5d3fe6626c22184edd83de6aedad8589ab2ef35
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837548"
---
# <a name="variable-and-argument-tracking"></a><span data-ttu-id="8259f-102">Śledzenie argumentów i zmiennych</span><span class="sxs-lookup"><span data-stu-id="8259f-102">Variable and Argument Tracking</span></span>
<span data-ttu-id="8259f-103">Podczas śledzenia wykonywania przepływu pracy często warto wyodrębnić dane.</span><span class="sxs-lookup"><span data-stu-id="8259f-103">When tracking the execution of a workflow, it is often useful to extract data.</span></span> <span data-ttu-id="8259f-104">Zapewnia to dodatkowy kontekst podczas uzyskiwania dostępu do rekordu śledzenia po wykonaniu.</span><span class="sxs-lookup"><span data-stu-id="8259f-104">This provides additional context when accessing a tracking record post execution.</span></span> <span data-ttu-id="8259f-105">W [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]można wyodrębnić wszelką widoczną zmienną lub argument w zakresie dowolnego działania w przepływie pracy przy użyciu funkcji śledzenia.</span><span class="sxs-lookup"><span data-stu-id="8259f-105">In [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], you can extract any visible variable or argument within the scope of any activity in a workflow using tracking.</span></span> <span data-ttu-id="8259f-106">Profile śledzenia ułatwiają wyodrębnianie danych.</span><span class="sxs-lookup"><span data-stu-id="8259f-106">Tracking profiles make it easy to extract data.</span></span>  
  
## <a name="variables-and-arguments"></a><span data-ttu-id="8259f-107">Zmienne i argumenty</span><span class="sxs-lookup"><span data-stu-id="8259f-107">Variables and Arguments</span></span>  
 <span data-ttu-id="8259f-108">Zmienne i argumenty są wyodrębniane, gdy działanie emituje ActivityStateRecord.</span><span class="sxs-lookup"><span data-stu-id="8259f-108">Variables and arguments are extracted when an activity emits an ActivityStateRecord.</span></span>  <span data-ttu-id="8259f-109">Zmienna jest dostępna do wyodrębnienia tylko wtedy, gdy znajduje się w zakresie działania.</span><span class="sxs-lookup"><span data-stu-id="8259f-109">A variable is available for extraction only if it is within the scope of the activity.</span></span> <span data-ttu-id="8259f-110">Zmienna do wyodrębnienia w ramach działania jest określana w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8259f-110">A variable to be extracted within an activity is specified in the following manner:</span></span>  
  
- <span data-ttu-id="8259f-111">Jeśli zmienna jest określona przez nazwę zmiennej, śledzenie szuka zmiennej w ramach bieżącego działania śledzonego i w działaniach nadrzędnych.</span><span class="sxs-lookup"><span data-stu-id="8259f-111">If a variable is specified by the variable name, then tracking looks for the variable within the current activity being tracked and in parent activities.</span></span> <span data-ttu-id="8259f-112">Zmienna jest przeszukiwana w zakresie bieżącego działania i w zakresie nadrzędnym.</span><span class="sxs-lookup"><span data-stu-id="8259f-112">The variable is searched in current activity scope and in parent scope.</span></span>  
  
- <span data-ttu-id="8259f-113">Jeśli zmienne do wyodrębnienia są określone przy użyciu Name = "\*", wszystkie zmienne w monitorowanym działaniu są wyodrębniane.</span><span class="sxs-lookup"><span data-stu-id="8259f-113">If variables to be extracted are specified by using name="\*", then all variables within the current activity being tracked are extracted.</span></span> <span data-ttu-id="8259f-114">W tym przypadku zmienne, które znajdują się w zakresie, ale zdefiniowane w działaniach nadrzędnych, nie są wyodrębniane.</span><span class="sxs-lookup"><span data-stu-id="8259f-114">In this case variables that are in scope but defined in parent activities are not extracted.</span></span>  
  
 <span data-ttu-id="8259f-115">Podczas wyodrębniania argumentów wyodrębnione argumenty zależą od stanu działania.</span><span class="sxs-lookup"><span data-stu-id="8259f-115">When extracting arguments, the arguments extracted depend on the state of the activity.</span></span> <span data-ttu-id="8259f-116">Gdy wykonywany jest stan działania, tylko `InArguments` są dostępne do wyodrębnienia.</span><span class="sxs-lookup"><span data-stu-id="8259f-116">When the state of an activity is Executing, then only the `InArguments` are available for extraction.</span></span> <span data-ttu-id="8259f-117">W przypadku każdego innego stanu działania (zamknięte, nieuszkodzone, anulowane) wszystkie argumenty, zarówno argument, jak i, są dostępne do wyodrębnienia.</span><span class="sxs-lookup"><span data-stu-id="8259f-117">For any other activity state (Closed, Faulted, Canceled), all arguments, both InArguments and OutArguments, are available for extraction.</span></span>  
  
 <span data-ttu-id="8259f-118">W poniższym przykładzie przedstawiono zapytanie o stan działania, które wyodrębnia zmienne i argumenty w przypadku wyemitowania rekordu śledzenia `Closed` działania.</span><span class="sxs-lookup"><span data-stu-id="8259f-118">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="8259f-119">Zmienne i argumenty mogą być wyodrębniane tylko za pomocą <xref:System.Activities.Tracking.ActivityStateRecord> i w ten sposób są subskrybowane w ramach profilu śledzenia przy użyciu <xref:System.Activities.Tracking.ActivityStateQuery>.</span><span class="sxs-lookup"><span data-stu-id="8259f-119">Variables and arguments can be extracted only with an <xref:System.Activities.Tracking.ActivityStateRecord> and thus are subscribed to within a tracking profile using <xref:System.Activities.Tracking.ActivityStateQuery>.</span></span>  
  
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
  
## <a name="protecting-information-stored-within-variables-and-arguments"></a><span data-ttu-id="8259f-120">Ochrona informacji przechowywanych w zmiennych i argumentach</span><span class="sxs-lookup"><span data-stu-id="8259f-120">Protecting Information Stored Within Variables and Arguments</span></span>  
 <span data-ttu-id="8259f-121">Śledzona zmienna lub argument jest domyślnie widoczny dla środowiska uruchomieniowego WF.</span><span class="sxs-lookup"><span data-stu-id="8259f-121">A tracked variable or argument is by default made visible by the WF runtime.</span></span> <span data-ttu-id="8259f-122">Deweloper przepływu pracy może chronić go przed dostępem, wykonując następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="8259f-122">A workflow developer can protect it from being accessed by taking the following steps:</span></span>  
  
1. <span data-ttu-id="8259f-123">Szyfruj wartość zmiennej.</span><span class="sxs-lookup"><span data-stu-id="8259f-123">Encrypt the value of a variable.</span></span>  
  
2. <span data-ttu-id="8259f-124">Kontroluj Tworzenie profilu śledzenia, aby zapobiec wyodrębnianiu zmiennej lub argumentu.</span><span class="sxs-lookup"><span data-stu-id="8259f-124">Control the authoring of a tracking profile to prevent the extraction of a variable or argument.</span></span>  
  
3. <span data-ttu-id="8259f-125">W przypadku uczestników śledzenia niestandardowego upewnij się, że kod WF nie ujawnia poufnych informacji, które są przechowywane w zmiennych lub argumentach.</span><span class="sxs-lookup"><span data-stu-id="8259f-125">For custom tracking participants ensure that the WF code does not disclose sensitive information that is stored in variables or arguments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8259f-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8259f-126">See also</span></span>

- <span data-ttu-id="8259f-127">[Monitorowanie aplikacji sieci szkieletowej systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="8259f-127">[Windows Server App Fabric Monitoring](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))</span></span>
- <span data-ttu-id="8259f-128">[Monitorowanie aplikacji przy użyciu sieci szkieletowej aplikacji](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="8259f-128">[Monitoring Applications with App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))</span></span>
