---
title: Przygotowane grupy działań
ms.date: 03/30/2017
ms.assetid: f76ef924-34ce-48ae-8c8d-48faf9697754
ms.openlocfilehash: 3560542b912f9697ec2e77c8d5c82e148a41d485
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="conditioned-activity-group"></a><span data-ttu-id="27369-102">Przygotowane grupy działań</span><span class="sxs-lookup"><span data-stu-id="27369-102">Conditioned Activity Group</span></span>
<span data-ttu-id="27369-103">W przykładzie pokazano aplikacji rezerwacji podróży.</span><span class="sxs-lookup"><span data-stu-id="27369-103">The sample demonstrates a travel booking application.</span></span> <span data-ttu-id="27369-104"><xref:System.Workflow.Activities.ConditionedActivityGroup> (Innego niż CAG) udostępnia dwa działania kodu: działanie Car i działania linii lotniczych.</span><span class="sxs-lookup"><span data-stu-id="27369-104">The <xref:System.Workflow.Activities.ConditionedActivityGroup> (CAG) has two code activities: a Car activity and an Airline activity.</span></span> <span data-ttu-id="27369-105">W `SimpleCAGWorkflow` konstruktora, obiektu ArrayList "travelNeedType" jest wypełniana typów rezerwacje podróży, które są wymagane.</span><span class="sxs-lookup"><span data-stu-id="27369-105">In the `SimpleCAGWorkflow` constructor, a "travelNeedType" ArrayList object is populated with the types of travel bookings that are required.</span></span> <span data-ttu-id="27369-106">Przez dodawanie komentarza do jednej lub obu `travelNeeds.Add` instrukcje, odpowiednio zmodyfikować zachowanie innego niż CAG.</span><span class="sxs-lookup"><span data-stu-id="27369-106">By commenting out one or both of the `travelNeeds.Add` statements, you modify the CAG behavior accordingly.</span></span> <span data-ttu-id="27369-107">Działania samochodu i linii lotniczych mają ich <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty> warunku wypełniane przy użyciu <xref:System.Workflow.Activities.CodeCondition>.</span><span class="sxs-lookup"><span data-stu-id="27369-107">Both the Car and Airline activities have their <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty> condition populated with a <xref:System.Workflow.Activities.CodeCondition>.</span></span> <span data-ttu-id="27369-108">Wykonuje działanie samochodu tylko wtedy, gdy `travelNeeds` kolekcja ma `TravelNeeds.Car` wpisu i lotniczego wykonuje działanie tylko wtedy, gdy `travelNeeds` kolekcja ma `TravelNeeds.Airline` wpisu.</span><span class="sxs-lookup"><span data-stu-id="27369-108">The Car activity executes only if the `travelNeeds` collection has a `TravelNeeds.Car` entry, and the Airline activity executes only if the `travelNeeds` collection has a `TravelNeeds.Airline` entry.</span></span>  
  
 <span data-ttu-id="27369-109">Wykonanie wszystkich czynności usuwa odpowiadający mu wpis z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="27369-109">The execution of each activity removes the corresponding entry from the collection.</span></span> <span data-ttu-id="27369-110">Wartość domyślna <xref:System.Workflow.Activities.ConditionedActivityGroup.UntilCondition%2A> warunek określa, czy innego niż CAG powinny być kończone, gdy bez żadnych elementów podrzędnych są wykonywane lub są gotowe do wykonania (na podstawie ich <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty> warunków).</span><span class="sxs-lookup"><span data-stu-id="27369-110">The default <xref:System.Workflow.Activities.ConditionedActivityGroup.UntilCondition%2A> condition specifies that the CAG should exit when no children are executing or are ready for execution (based on their <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty> conditions).</span></span> <span data-ttu-id="27369-111">W tym przykładzie, oznacza to, innego niż CAG opuszcza, kiedy `travelNeeds` kolekcja jest pusta.</span><span class="sxs-lookup"><span data-stu-id="27369-111">In this sample, this means that the CAG exits when the `travelNeeds` collection is empty.</span></span>  
  
### <a name="to-build-the-sample"></a><span data-ttu-id="27369-112">Aby samodzielnie tworzyć przykładowy</span><span class="sxs-lookup"><span data-stu-id="27369-112">To build the sample</span></span>  
  
1.  <span data-ttu-id="27369-113">Otwórz rozwiązanie w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="27369-113">Open the solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="27369-114">Skompiluj rozwiązanie, naciskając klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="27369-114">Build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="27369-115">Uruchom rozwiązania bez debugowania, naciskając klawisze CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="27369-115">Run the solution without debugging by pressing CTRL+F5.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="27369-116">Aby uruchomić przykładowy</span><span class="sxs-lookup"><span data-stu-id="27369-116">To run the sample</span></span>  
  
-   <span data-ttu-id="27369-117">W oknie wiersza polecenia zestawu SDK Uruchom plik .exe w folderze SimpleCAG\bin\debug (lub folderu SimpleCAG\bin dla używanej wersji programu Visual Basic przykładu) znajdujący się poniżej głównego folderu przykładowej.</span><span class="sxs-lookup"><span data-stu-id="27369-117">In the SDK Command Prompt window, run the .exe file in the SimpleCAG\bin\debug folder (or the SimpleCAG\bin folder for the Visual Basic version of the sample), which is located below the main folder for the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="27369-118">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="27369-118">The samples may already be installed on your computer.</span></span> <span data-ttu-id="27369-119">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne):</span><span class="sxs-lookup"><span data-stu-id="27369-119">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="27369-120">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="27369-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="27369-121">W tym przykładzie znajduje się w następującym katalogu:</span><span class="sxs-lookup"><span data-stu-id="27369-121">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\SimpleCAG`  
  
## <a name="see-also"></a><span data-ttu-id="27369-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="27369-122">See Also</span></span>  
 <xref:System.Workflow.Activities.ConditionedActivityGroup>  
 <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty>  
 <xref:System.Workflow.Activities.CodeCondition>  
 <xref:System.Workflow.Activities.ConditionedActivityGroup.UntilCondition%2A>
