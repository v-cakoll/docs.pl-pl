---
title: "Przygotowane grupy działań"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f76ef924-34ce-48ae-8c8d-48faf9697754
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ab8f47601f84267d1ac357b313fa5d2215a586d8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="conditioned-activity-group"></a><span data-ttu-id="1a205-102">Przygotowane grupy działań</span><span class="sxs-lookup"><span data-stu-id="1a205-102">Conditioned Activity Group</span></span>
<span data-ttu-id="1a205-103">W przykładzie pokazano aplikacji rezerwacji podróży.</span><span class="sxs-lookup"><span data-stu-id="1a205-103">The sample demonstrates a travel booking application.</span></span> <span data-ttu-id="1a205-104"><xref:System.Workflow.Activities.ConditionedActivityGroup> (Innego niż CAG) udostępnia dwa działania kodu: działanie Car i działania linii lotniczych.</span><span class="sxs-lookup"><span data-stu-id="1a205-104">The <xref:System.Workflow.Activities.ConditionedActivityGroup> (CAG) has two code activities: a Car activity and an Airline activity.</span></span> <span data-ttu-id="1a205-105">W `SimpleCAGWorkflow` konstruktora, obiektu ArrayList "travelNeedType" jest wypełniana typów rezerwacje podróży, które są wymagane.</span><span class="sxs-lookup"><span data-stu-id="1a205-105">In the `SimpleCAGWorkflow` constructor, a "travelNeedType" ArrayList object is populated with the types of travel bookings that are required.</span></span> <span data-ttu-id="1a205-106">Przez dodawanie komentarza do jednej lub obu `travelNeeds.Add` instrukcje, odpowiednio zmodyfikować zachowanie innego niż CAG.</span><span class="sxs-lookup"><span data-stu-id="1a205-106">By commenting out one or both of the `travelNeeds.Add` statements, you modify the CAG behavior accordingly.</span></span> <span data-ttu-id="1a205-107">Działania samochodu i linii lotniczych mają ich <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty> warunku wypełniane przy użyciu <xref:System.Workflow.Activities.CodeCondition>.</span><span class="sxs-lookup"><span data-stu-id="1a205-107">Both the Car and Airline activities have their <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty> condition populated with a <xref:System.Workflow.Activities.CodeCondition>.</span></span> <span data-ttu-id="1a205-108">Wykonuje działanie samochodu tylko wtedy, gdy `travelNeeds` kolekcja ma `TravelNeeds.Car` wpisu i lotniczego wykonuje działanie tylko wtedy, gdy `travelNeeds` kolekcja ma `TravelNeeds.Airline` wpisu.</span><span class="sxs-lookup"><span data-stu-id="1a205-108">The Car activity executes only if the `travelNeeds` collection has a `TravelNeeds.Car` entry, and the Airline activity executes only if the `travelNeeds` collection has a `TravelNeeds.Airline` entry.</span></span>  
  
 <span data-ttu-id="1a205-109">Wykonanie wszystkich czynności usuwa odpowiadający mu wpis z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="1a205-109">The execution of each activity removes the corresponding entry from the collection.</span></span> <span data-ttu-id="1a205-110">Wartość domyślna <xref:System.Workflow.Activities.ConditionedActivityGroup.UntilCondition%2A> warunek określa, czy innego niż CAG powinny być kończone, gdy bez żadnych elementów podrzędnych są wykonywane lub są gotowe do wykonania (na podstawie ich <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty> warunków).</span><span class="sxs-lookup"><span data-stu-id="1a205-110">The default <xref:System.Workflow.Activities.ConditionedActivityGroup.UntilCondition%2A> condition specifies that the CAG should exit when no children are executing or are ready for execution (based on their <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty> conditions).</span></span> <span data-ttu-id="1a205-111">W tym przykładzie, oznacza to, innego niż CAG opuszcza, kiedy `travelNeeds` kolekcja jest pusta.</span><span class="sxs-lookup"><span data-stu-id="1a205-111">In this sample, this means that the CAG exits when the `travelNeeds` collection is empty.</span></span>  
  
### <a name="to-build-the-sample"></a><span data-ttu-id="1a205-112">Aby samodzielnie tworzyć przykładowy</span><span class="sxs-lookup"><span data-stu-id="1a205-112">To build the sample</span></span>  
  
1.  <span data-ttu-id="1a205-113">Otwórz rozwiązanie w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1a205-113">Open the solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="1a205-114">Skompiluj rozwiązanie, naciskając klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="1a205-114">Build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="1a205-115">Uruchom rozwiązania bez debugowania, naciskając klawisze CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="1a205-115">Run the solution without debugging by pressing CTRL+F5.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="1a205-116">Aby uruchomić przykładowy</span><span class="sxs-lookup"><span data-stu-id="1a205-116">To run the sample</span></span>  
  
-   <span data-ttu-id="1a205-117">W oknie wiersza polecenia zestawu SDK Uruchom plik .exe w folderze SimpleCAG\bin\debug (lub folderu SimpleCAG\bin dla używanej wersji programu Visual Basic przykładu) znajdujący się poniżej głównego folderu przykładowej.</span><span class="sxs-lookup"><span data-stu-id="1a205-117">In the SDK Command Prompt window, run the .exe file in the SimpleCAG\bin\debug folder (or the SimpleCAG\bin folder for the Visual Basic version of the sample), which is located below the main folder for the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1a205-118">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="1a205-118">The samples may already be installed on your computer.</span></span> <span data-ttu-id="1a205-119">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne):</span><span class="sxs-lookup"><span data-stu-id="1a205-119">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="1a205-120">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="1a205-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1a205-121">W tym przykładzie znajduje się w następującym katalogu:</span><span class="sxs-lookup"><span data-stu-id="1a205-121">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\SimpleCAG`  
  
## <a name="see-also"></a><span data-ttu-id="1a205-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1a205-122">See Also</span></span>  
 <xref:System.Workflow.Activities.ConditionedActivityGroup>  
 <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty>  
 <xref:System.Workflow.Activities.CodeCondition>  
 <xref:System.Workflow.Activities.ConditionedActivityGroup.UntilCondition%2A>
