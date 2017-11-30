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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: dd6f85dc7961a7c3fd51e67b9fd6e16de9faa41d
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2017
---
# <a name="basic-validation"></a><span data-ttu-id="a66be-102">Podstawowe sprawdzanie poprawności</span><span class="sxs-lookup"><span data-stu-id="a66be-102">Basic Validation</span></span>
<span data-ttu-id="a66be-103">W tym przykładzie składa się z działania `CreateProduct`, która sprawdza, czy jego `Cost` argument jest mniejszy niż lub równy jego `Price` argumentu.</span><span class="sxs-lookup"><span data-stu-id="a66be-103">This sample consists of an activity, `CreateProduct`, which validates that its `Cost` argument is smaller than or equal to its `Price` argument.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="a66be-104">Szczegóły próbki</span><span class="sxs-lookup"><span data-stu-id="a66be-104">Sample Details</span></span>  
 <span data-ttu-id="a66be-105">Istnieją dwa autorów, korzystających z weryfikacji, określony przez autora działania (tworzy logikę weryfikacji dla działania) i autor przepływu pracy, który wywołuje usługi weryfikacji dla określonego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="a66be-105">There are two authors that use validation, the activity author (creates the validation logic for the activity) and the workflow author that calls validation services on a specific workflow.</span></span> <span data-ttu-id="a66be-106">W tym scenariuszu określony przez autora działania chce wymusić, że każde wystąpienie jego działania musi mieć mniejszy lub równy koszt niż cena.</span><span class="sxs-lookup"><span data-stu-id="a66be-106">In this scenario, the activity author wants to enforce that every instance of his activity must have a smaller or equal cost than that of the price.</span></span>  
  
 <span data-ttu-id="a66be-107">Określony przez autora działania (wewnątrz działania), musi:</span><span class="sxs-lookup"><span data-stu-id="a66be-107">The activity author (inside the activity) must:</span></span>  
  
-   <span data-ttu-id="a66be-108">Tworzenie ograniczenia (`PriceGreaterThanCost`).</span><span class="sxs-lookup"><span data-stu-id="a66be-108">Create a constraint (`PriceGreaterThanCost`).</span></span> <span data-ttu-id="a66be-109">Jest to, gdzie znajduje się całą logikę sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="a66be-109">This is where all the validation logic resides.</span></span>  
  
-   <span data-ttu-id="a66be-110">Zastąpienie `System.Activities.CodeActivity.OnGetConstraints()` i Dodaj ograniczenie (`PriceGreaterThanCost`) do ograniczenia <xref:System.Collections.IList>.</span><span class="sxs-lookup"><span data-stu-id="a66be-110">Override `System.Activities.CodeActivity.OnGetConstraints()` and add the constraint (`PriceGreaterThanCost`) to the constraints <xref:System.Collections.IList>.</span></span>  
  
 <span data-ttu-id="a66be-111">Autor przepływu pracy (główny program), musi:</span><span class="sxs-lookup"><span data-stu-id="a66be-111">The workflow author (main program) must:</span></span>  
  
-   <span data-ttu-id="a66be-112">Tworzenie przepływów pracy przy użyciu wystąpienia działania do sprawdzania poprawności (`CreateProduct`).</span><span class="sxs-lookup"><span data-stu-id="a66be-112">Create a workflow with an instance of the activity to validate (`CreateProduct`).</span></span>  
  
-   <span data-ttu-id="a66be-113">Wywołanie <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>, która zwraca <xref:System.Activities.Validation.ValidationResults> kolekcji <xref:System.Activities.Validation.ValidationError>.</span><span class="sxs-lookup"><span data-stu-id="a66be-113">Call <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>, which returns a <xref:System.Activities.Validation.ValidationResults> collection of <xref:System.Activities.Validation.ValidationError>.</span></span>  
  
-   <span data-ttu-id="a66be-114">(Opcjonalnie) Drukuj <xref:System.Activities.Validation.ValidationError> obiektów.</span><span class="sxs-lookup"><span data-stu-id="a66be-114">(Optional) Print the <xref:System.Activities.Validation.ValidationError> objects.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a66be-115">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="a66be-115">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="a66be-116">Otwórz rozwiązanie próbki BasicValidation.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a66be-116">Open the BasicValidation.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="a66be-117">Tworzenie i uruchamianie rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="a66be-117">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a66be-118">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="a66be-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a66be-119">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="a66be-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a66be-120">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="a66be-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a66be-121">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="a66be-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\BasicValidation`