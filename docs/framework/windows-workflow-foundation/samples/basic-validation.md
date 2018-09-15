---
title: Podstawowe sprawdzanie poprawności
ms.date: 03/30/2017
ms.assetid: ba1343cc-aaab-4ade-b0c0-1dd5063bf4ad
ms.openlocfilehash: 74d99e2d426e9ea5701fad80418fdf019112cc9e
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/15/2018
ms.locfileid: "45645817"
---
# <a name="basic-validation"></a><span data-ttu-id="c6b84-102">Podstawowe sprawdzanie poprawności</span><span class="sxs-lookup"><span data-stu-id="c6b84-102">Basic Validation</span></span>
<span data-ttu-id="c6b84-103">W tym przykładzie składa się z działań `CreateProduct`, która sprawdza, czy jego `Cost` argument jest mniejszy niż lub równa jego `Price` argumentu.</span><span class="sxs-lookup"><span data-stu-id="c6b84-103">This sample consists of an activity, `CreateProduct`, which validates that its `Cost` argument is smaller than or equal to its `Price` argument.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="c6b84-104">Przykład szczegółów</span><span class="sxs-lookup"><span data-stu-id="c6b84-104">Sample Details</span></span>  
 <span data-ttu-id="c6b84-105">Istnieją dwa autorów, którzy sprawdzania poprawności, autor działania (tworzy logikę weryfikacji dla działania) i autor przepływu pracy, który wywołuje usług weryfikacji dla określonego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="c6b84-105">There are two authors that use validation, the activity author (creates the validation logic for the activity) and the workflow author that calls validation services on a specific workflow.</span></span> <span data-ttu-id="c6b84-106">W tym scenariuszu działanie chce, aby wymusić na to, że każde wystąpienie swojej działalności, musi mieć mniejszy lub równy koszt niż cena.</span><span class="sxs-lookup"><span data-stu-id="c6b84-106">In this scenario, the activity author wants to enforce that every instance of his activity must have a smaller or equal cost than that of the price.</span></span>  
  
 <span data-ttu-id="c6b84-107">Tworzenie działania (wewnątrz działania) musi:</span><span class="sxs-lookup"><span data-stu-id="c6b84-107">The activity author (inside the activity) must:</span></span>  
  
-   <span data-ttu-id="c6b84-108">Tworzenie ograniczenia (`PriceGreaterThanCost`).</span><span class="sxs-lookup"><span data-stu-id="c6b84-108">Create a constraint (`PriceGreaterThanCost`).</span></span> <span data-ttu-id="c6b84-109">Jest to, gdzie znajduje się całą logikę weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="c6b84-109">This is where all the validation logic resides.</span></span>  
  
-   <span data-ttu-id="c6b84-110">Zastąp `System.Activities.CodeActivity.OnGetConstraints()` i Dodaj ograniczenie (`PriceGreaterThanCost`) do ograniczenia <xref:System.Collections.IList>.</span><span class="sxs-lookup"><span data-stu-id="c6b84-110">Override `System.Activities.CodeActivity.OnGetConstraints()` and add the constraint (`PriceGreaterThanCost`) to the constraints <xref:System.Collections.IList>.</span></span>  
  
 <span data-ttu-id="c6b84-111">Tworzenie przepływu pracy (główny program) musi:</span><span class="sxs-lookup"><span data-stu-id="c6b84-111">The workflow author (main program) must:</span></span>  
  
-   <span data-ttu-id="c6b84-112">Tworzenie przepływu pracy z wystąpieniem działanie do sprawdzania poprawności (`CreateProduct`).</span><span class="sxs-lookup"><span data-stu-id="c6b84-112">Create a workflow with an instance of the activity to validate (`CreateProduct`).</span></span>  
  
-   <span data-ttu-id="c6b84-113">Wywołaj <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>, co powoduje zwrócenie <xref:System.Activities.Validation.ValidationResults> zbiór <xref:System.Activities.Validation.ValidationError>.</span><span class="sxs-lookup"><span data-stu-id="c6b84-113">Call <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>, which returns a <xref:System.Activities.Validation.ValidationResults> collection of <xref:System.Activities.Validation.ValidationError>.</span></span>  
  
-   <span data-ttu-id="c6b84-114">(Opcjonalnie) Drukuj <xref:System.Activities.Validation.ValidationError> obiektów.</span><span class="sxs-lookup"><span data-stu-id="c6b84-114">(Optional) Print the <xref:System.Activities.Validation.ValidationError> objects.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c6b84-115">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="c6b84-115">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="c6b84-116">Otwórz rozwiązanie przykładowe BasicValidation.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c6b84-116">Open the BasicValidation.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="c6b84-117">Skompiluj i uruchom rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="c6b84-117">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c6b84-118">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="c6b84-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c6b84-119">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="c6b84-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c6b84-120">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="c6b84-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c6b84-121">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="c6b84-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\BasicValidation`