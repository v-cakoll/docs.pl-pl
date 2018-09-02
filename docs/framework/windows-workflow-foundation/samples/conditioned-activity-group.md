---
title: Grupa działań objętych warunkami
ms.date: 03/30/2017
ms.assetid: f76ef924-34ce-48ae-8c8d-48faf9697754
ms.openlocfilehash: 144a6c76ea6314c553e201fe4e2364890d869f34
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43418172"
---
# <a name="conditioned-activity-group"></a><span data-ttu-id="3d3b0-102">Grupa działań objętych warunkami</span><span class="sxs-lookup"><span data-stu-id="3d3b0-102">Conditioned Activity Group</span></span>
<span data-ttu-id="3d3b0-103">W przykładzie pokazano aplikacji rezerwacji podróży.</span><span class="sxs-lookup"><span data-stu-id="3d3b0-103">The sample demonstrates a travel booking application.</span></span> <span data-ttu-id="3d3b0-104"><xref:System.Workflow.Activities.ConditionedActivityGroup> (CAG) ma dwa działania kodu: działanie Car i działania linii lotniczych.</span><span class="sxs-lookup"><span data-stu-id="3d3b0-104">The <xref:System.Workflow.Activities.ConditionedActivityGroup> (CAG) has two code activities: a Car activity and an Airline activity.</span></span> <span data-ttu-id="3d3b0-105">W `SimpleCAGWorkflow` konstruktora obiektu ArrayList "travelNeedType" jest wypełniana przy użyciu typów rezerwacje podróży, które są wymagane.</span><span class="sxs-lookup"><span data-stu-id="3d3b0-105">In the `SimpleCAGWorkflow` constructor, a "travelNeedType" ArrayList object is populated with the types of travel bookings that are required.</span></span> <span data-ttu-id="3d3b0-106">Zakomentowując jedną lub obie `travelNeeds.Add` instrukcji odpowiednio zmodyfikować zachowanie CAG.</span><span class="sxs-lookup"><span data-stu-id="3d3b0-106">By commenting out one or both of the `travelNeeds.Add` statements, you modify the CAG behavior accordingly.</span></span> <span data-ttu-id="3d3b0-107">Działania samochodu i linie lotnicze mają swoje <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty> wypełniony warunek <xref:System.Workflow.Activities.CodeCondition>.</span><span class="sxs-lookup"><span data-stu-id="3d3b0-107">Both the Car and Airline activities have their <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty> condition populated with a <xref:System.Workflow.Activities.CodeCondition>.</span></span> <span data-ttu-id="3d3b0-108">Działanie samochód jest wykonywane tylko wtedy, gdy `travelNeeds` kolekcja ma `TravelNeeds.Car` wejścia i linii lotniczych, działanie jest wykonywane tylko wtedy, gdy `travelNeeds` kolekcja ma `TravelNeeds.Airline` wpisu.</span><span class="sxs-lookup"><span data-stu-id="3d3b0-108">The Car activity executes only if the `travelNeeds` collection has a `TravelNeeds.Car` entry, and the Airline activity executes only if the `travelNeeds` collection has a `TravelNeeds.Airline` entry.</span></span>  
  
 <span data-ttu-id="3d3b0-109">Wykonanie każdego działania usuwa odpowiadający mu wpis z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="3d3b0-109">The execution of each activity removes the corresponding entry from the collection.</span></span> <span data-ttu-id="3d3b0-110">Wartość domyślna <xref:System.Workflow.Activities.ConditionedActivityGroup.UntilCondition%2A> warunek określa, że CAG powinno powodować wyjście, gdy żadne elementy podrzędne są wykonywane lub gotowe do wykonania (na podstawie ich <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty> warunki).</span><span class="sxs-lookup"><span data-stu-id="3d3b0-110">The default <xref:System.Workflow.Activities.ConditionedActivityGroup.UntilCondition%2A> condition specifies that the CAG should exit when no children are executing or are ready for execution (based on their <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty> conditions).</span></span> <span data-ttu-id="3d3b0-111">W tym przykładzie, oznacza to, że CAG kończy działanie po `travelNeeds` kolekcja jest pusta.</span><span class="sxs-lookup"><span data-stu-id="3d3b0-111">In this sample, this means that the CAG exits when the `travelNeeds` collection is empty.</span></span>  
  
### <a name="to-build-the-sample"></a><span data-ttu-id="3d3b0-112">Aby skompilować przykład</span><span class="sxs-lookup"><span data-stu-id="3d3b0-112">To build the sample</span></span>  
  
1.  <span data-ttu-id="3d3b0-113">Otwórz rozwiązanie w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3d3b0-113">Open the solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="3d3b0-114">Skompiluj rozwiązanie, naciskając klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="3d3b0-114">Build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="3d3b0-115">Uruchom rozwiązanie bez debugowania, naciskając klawisze CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="3d3b0-115">Run the solution without debugging by pressing CTRL+F5.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="3d3b0-116">Aby uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="3d3b0-116">To run the sample</span></span>  
  
-   <span data-ttu-id="3d3b0-117">W oknie wiersza polecenia zestawu SDK Uruchom plik .exe w folderze SimpleCAG\bin\debug (lub folder SimpleCAG\bin wersję przykładu w Visual Basic), który znajduje się poniżej głównego folderu dla przykładu.</span><span class="sxs-lookup"><span data-stu-id="3d3b0-117">In the SDK Command Prompt window, run the .exe file in the SimpleCAG\bin\debug folder (or the SimpleCAG\bin folder for the Visual Basic version of the sample), which is located below the main folder for the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3d3b0-118">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="3d3b0-118">The samples may already be installed on your computer.</span></span> <span data-ttu-id="3d3b0-119">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne):</span><span class="sxs-lookup"><span data-stu-id="3d3b0-119">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="3d3b0-120">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="3d3b0-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3d3b0-121">W tym przykładzie znajduje się w następującym katalogu:</span><span class="sxs-lookup"><span data-stu-id="3d3b0-121">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\SimpleCAG`  
  
## <a name="see-also"></a><span data-ttu-id="3d3b0-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3d3b0-122">See Also</span></span>  
 <xref:System.Workflow.Activities.ConditionedActivityGroup>  
 <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty>  
 <xref:System.Workflow.Activities.CodeCondition>  
 <xref:System.Workflow.Activities.ConditionedActivityGroup.UntilCondition%2A>
