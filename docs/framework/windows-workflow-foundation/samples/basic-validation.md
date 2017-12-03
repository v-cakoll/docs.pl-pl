---
title: "Podstawowe sprawdzanie poprawności"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba1343cc-aaab-4ade-b0c0-1dd5063bf4ad
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 99af85c87f52447f9be7a01c1ab2549158844677
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="basic-validation"></a><span data-ttu-id="8e1d9-102">Podstawowe sprawdzanie poprawności</span><span class="sxs-lookup"><span data-stu-id="8e1d9-102">Basic Validation</span></span>
<span data-ttu-id="8e1d9-103">W tym przykładzie składa się z działania `CreateProduct`, która sprawdza, czy jego `Cost` argument jest mniejszy niż lub równy jego `Price` argumentu.</span><span class="sxs-lookup"><span data-stu-id="8e1d9-103">This sample consists of an activity, `CreateProduct`, which validates that its `Cost` argument is smaller than or equal to its `Price` argument.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="8e1d9-104">Szczegóły próbki</span><span class="sxs-lookup"><span data-stu-id="8e1d9-104">Sample Details</span></span>  
 <span data-ttu-id="8e1d9-105">Istnieją dwa autorów, korzystających z weryfikacji, określony przez autora działania (tworzy logikę weryfikacji dla działania) i autor przepływu pracy, który wywołuje usługi weryfikacji dla określonego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="8e1d9-105">There are two authors that use validation, the activity author (creates the validation logic for the activity) and the workflow author that calls validation services on a specific workflow.</span></span> <span data-ttu-id="8e1d9-106">W tym scenariuszu określony przez autora działania chce wymusić, że każde wystąpienie jego działania musi mieć mniejszy lub równy koszt niż cena.</span><span class="sxs-lookup"><span data-stu-id="8e1d9-106">In this scenario, the activity author wants to enforce that every instance of his activity must have a smaller or equal cost than that of the price.</span></span>  
  
 <span data-ttu-id="8e1d9-107">Określony przez autora działania (wewnątrz działania), musi:</span><span class="sxs-lookup"><span data-stu-id="8e1d9-107">The activity author (inside the activity) must:</span></span>  
  
-   <span data-ttu-id="8e1d9-108">Tworzenie ograniczenia (`PriceGreaterThanCost`).</span><span class="sxs-lookup"><span data-stu-id="8e1d9-108">Create a constraint (`PriceGreaterThanCost`).</span></span> <span data-ttu-id="8e1d9-109">Jest to, gdzie znajduje się całą logikę sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="8e1d9-109">This is where all the validation logic resides.</span></span>  
  
-   <span data-ttu-id="8e1d9-110">Zastąpienie `System.Activities.CodeActivity.OnGetConstraints()` i Dodaj ograniczenie (`PriceGreaterThanCost`) do ograniczenia <xref:System.Collections.IList>.</span><span class="sxs-lookup"><span data-stu-id="8e1d9-110">Override `System.Activities.CodeActivity.OnGetConstraints()` and add the constraint (`PriceGreaterThanCost`) to the constraints <xref:System.Collections.IList>.</span></span>  
  
 <span data-ttu-id="8e1d9-111">Autor przepływu pracy (główny program), musi:</span><span class="sxs-lookup"><span data-stu-id="8e1d9-111">The workflow author (main program) must:</span></span>  
  
-   <span data-ttu-id="8e1d9-112">Tworzenie przepływów pracy przy użyciu wystąpienia działania do sprawdzania poprawności (`CreateProduct`).</span><span class="sxs-lookup"><span data-stu-id="8e1d9-112">Create a workflow with an instance of the activity to validate (`CreateProduct`).</span></span>  
  
-   <span data-ttu-id="8e1d9-113">Wywołanie <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>, która zwraca <xref:System.Activities.Validation.ValidationResults> kolekcji <xref:System.Activities.Validation.ValidationError>.</span><span class="sxs-lookup"><span data-stu-id="8e1d9-113">Call <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>, which returns a <xref:System.Activities.Validation.ValidationResults> collection of <xref:System.Activities.Validation.ValidationError>.</span></span>  
  
-   <span data-ttu-id="8e1d9-114">(Opcjonalnie) Drukuj <xref:System.Activities.Validation.ValidationError> obiektów.</span><span class="sxs-lookup"><span data-stu-id="8e1d9-114">(Optional) Print the <xref:System.Activities.Validation.ValidationError> objects.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8e1d9-115">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="8e1d9-115">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="8e1d9-116">Otwórz rozwiązanie próbki BasicValidation.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8e1d9-116">Open the BasicValidation.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="8e1d9-117">Tworzenie i uruchamianie rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="8e1d9-117">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8e1d9-118">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="8e1d9-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8e1d9-119">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="8e1d9-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="8e1d9-120">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="8e1d9-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8e1d9-121">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="8e1d9-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\BasicValidation`