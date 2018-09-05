---
title: Typy ograniczeń
ms.date: 03/30/2017
ms.assetid: b6b246e6-1130-4698-9625-c5c42abcbfed
ms.openlocfilehash: 202a2c7b3a3fc400552e42c8606457964af66af2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43506615"
---
# <a name="constraint-types"></a><span data-ttu-id="d72b1-102">Typy ograniczeń</span><span class="sxs-lookup"><span data-stu-id="d72b1-102">Constraint Types</span></span>
<span data-ttu-id="d72b1-103">W tym przykładzie przedstawiono dwa różne sposoby, aby zastosować ograniczenia do przepływu pracy, jest jednym z wewnątrz działania (Kompilacja) i jest jednym z poza nim (zasady).</span><span class="sxs-lookup"><span data-stu-id="d72b1-103">This sample shows two different ways to apply constraints to a workflow, one is from inside the activity (build) and one is from outside of it (policy).</span></span> <span data-ttu-id="d72b1-104">W tym scenariuszu działanie (z firmy zajmującej się oprogramowaniem firmy 3rth) chce, aby zweryfikować relacji między dwa argumenty.</span><span class="sxs-lookup"><span data-stu-id="d72b1-104">In this scenario, an activity author (from a 3rth-party software company) wants to validate the relationship between two arguments.</span></span> <span data-ttu-id="d72b1-105">W tym przypadku koszt powinna być mniejsza niż lub równa.</span><span class="sxs-lookup"><span data-stu-id="d72b1-105">In this case, the cost should be smaller than or equal to the price.</span></span> <span data-ttu-id="d72b1-106">Jest to ograniczenie kompilacji ogólnej walidacji.</span><span class="sxs-lookup"><span data-stu-id="d72b1-106">This is a general validation build constraint.</span></span>  
  
 <span data-ttu-id="d72b1-107">Następnie wybierz właściciel chce, aby dodać niektóre sprawdzanie poprawności do to ogólne działanie.</span><span class="sxs-lookup"><span data-stu-id="d72b1-107">Then a shop owner wants to add some validation to this generic activity.</span></span> <span data-ttu-id="d72b1-108">W jego przypadku Piotr większość swoich produktów jako 9,99 USD lub mniej.</span><span class="sxs-lookup"><span data-stu-id="d72b1-108">In his case, he wants the majority of its products to be $9.99 or less.</span></span> <span data-ttu-id="d72b1-109">Dlatego używa ograniczenia zasad, który jest w górnej części `CreateProduct` działania.</span><span class="sxs-lookup"><span data-stu-id="d72b1-109">So, he uses a policy constraint that is on top of the `CreateProduct` activity.</span></span>  
  
 <span data-ttu-id="d72b1-110">W przykładzie:</span><span class="sxs-lookup"><span data-stu-id="d72b1-110">In the sample:</span></span>  
  
 <span data-ttu-id="d72b1-111">Tworzenie działania (Kompilacja) musi:</span><span class="sxs-lookup"><span data-stu-id="d72b1-111">The activity author (build) must:</span></span>  
  
-   <span data-ttu-id="d72b1-112">Tworzenie ograniczenia (`PriceGreaterThanCost`).</span><span class="sxs-lookup"><span data-stu-id="d72b1-112">Create a constraint (`PriceGreaterThanCost`).</span></span> <span data-ttu-id="d72b1-113">Jest to, gdzie znajduje się całą logikę weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="d72b1-113">This is where all the validation logic resides.</span></span>  
  
-   <span data-ttu-id="d72b1-114">Zastąp `System.Activities.CodeActivity.OnGetConstraints()` i Dodaj ograniczenie (`PriceGreaterThanCost`) do ograniczenia <xref:System.Collections.IList>.</span><span class="sxs-lookup"><span data-stu-id="d72b1-114">Override `System.Activities.CodeActivity.OnGetConstraints()` and add the constraint (`PriceGreaterThanCost`) to the constraints <xref:System.Collections.IList>.</span></span>  
  
 <span data-ttu-id="d72b1-115">Tworzenie przepływu pracy (zasady) musi:</span><span class="sxs-lookup"><span data-stu-id="d72b1-115">The workflow author (policy) must:</span></span>  
  
-   <span data-ttu-id="d72b1-116">Tworzenie przepływu pracy z wystąpieniem działanie do sprawdzania poprawności (`CreateProduct`).</span><span class="sxs-lookup"><span data-stu-id="d72b1-116">Create a workflow with an instance of the activity to validate (`CreateProduct`).</span></span>  
  
-   <span data-ttu-id="d72b1-117">Tworzenie ograniczenia (`MaxPrice`).</span><span class="sxs-lookup"><span data-stu-id="d72b1-117">Create a constraint (`MaxPrice`).</span></span>  
  
-   <span data-ttu-id="d72b1-118">Tworzenie <xref:System.Activities.Validation.ValidationSettings> wystąpienia (`validationSettings`) i Dodaj ograniczenie (`MaxPrice`) do kolekcji `AdditionalConstraints`.</span><span class="sxs-lookup"><span data-stu-id="d72b1-118">Create a <xref:System.Activities.Validation.ValidationSettings> instance (`validationSettings`) and add the constraint (`MaxPrice`) to the collection `AdditionalConstraints`.</span></span> <span data-ttu-id="d72b1-119">W tym miejscu Autor przepływu pracy można dodać ograniczenia zasad do żadnych działań, takich jak sekwencji lub równolegle.</span><span class="sxs-lookup"><span data-stu-id="d72b1-119">Here the workflow author can add policy constraints to any activity, such as a sequence or parallel.</span></span>  
  
-   <span data-ttu-id="d72b1-120">Wywołaj <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>, co powoduje zwrócenie <xref:System.Activities.Validation.ValidationResults> zbiór <xref:System.Activities.Validation.ValidationError> obiektów.</span><span class="sxs-lookup"><span data-stu-id="d72b1-120">Call <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>, which returns a <xref:System.Activities.Validation.ValidationResults> collection of <xref:System.Activities.Validation.ValidationError> objects.</span></span>  
  
-   <span data-ttu-id="d72b1-121">(Opcjonalnie) Drukuj <xref:System.Activities.Validation.ValidationError> obiektów.</span><span class="sxs-lookup"><span data-stu-id="d72b1-121">(Optional) Print the <xref:System.Activities.Validation.ValidationError> objects.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d72b1-122">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="d72b1-122">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="d72b1-123">Otwórz rozwiązanie przykładowe ConstraintTypes.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d72b1-123">Open the ConstraintTypes.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="d72b1-124">Skompiluj i uruchom rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="d72b1-124">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d72b1-125">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="d72b1-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d72b1-126">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="d72b1-126">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d72b1-127">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="d72b1-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d72b1-128">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="d72b1-128">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Validation\ConstraintLibrary`