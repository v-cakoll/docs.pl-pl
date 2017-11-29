---
title: "Sprawdzanie poprawności działania zewnętrzne"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 49619f59-9819-484a-bcd8-5596308e8551
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e3fdc37e22bf06cdfdad3141af5657a1b20911a2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="external-activity-validation"></a><span data-ttu-id="32945-102">Sprawdzanie poprawności działania zewnętrzne</span><span class="sxs-lookup"><span data-stu-id="32945-102">External Activity Validation</span></span>
<span data-ttu-id="32945-103">W tym przykładzie pokazano, jak dodać logikę weryfikacji wbudowane działania, których nie jesteś Autor.</span><span class="sxs-lookup"><span data-stu-id="32945-103">This sample shows how to add validation logic to a built-in activity that you are not the author of.</span></span> <span data-ttu-id="32945-104">Logikę weryfikacji składa się z wymuszenie wszystkich <xref:System.Activities.Statements.If> przedstawia działań w przepływie pracy, musisz być ich <xref:System.Activities.Statements.If.Then%2A> zestaw właściwości lub ich <xref:System.Activities.Statements.If.Else%2A> zestawu właściwości.</span><span class="sxs-lookup"><span data-stu-id="32945-104">The validation logic consists of enforcing that all <xref:System.Activities.Statements.If> activities present in the workflow either have their <xref:System.Activities.Statements.If.Then%2A> property set or their <xref:System.Activities.Statements.If.Else%2A> property set.</span></span> <span data-ttu-id="32945-105">Ponadto logikę weryfikacji obejmuje sprawdzania wszystkie <xref:System.Activities.Statements.Pick> działania w przepływie pracy mają więcej niż jednej gałęzi i jeśli nie jest wielkość liter, generowany jest ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="32945-105">Also, the validation logic includes checking that all <xref:System.Activities.Statements.Pick> activities present in the workflow have more than one branch, and if that is not the case, a warning is generated.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="32945-106">Szczegóły próbki</span><span class="sxs-lookup"><span data-stu-id="32945-106">Sample details</span></span>  
 <span data-ttu-id="32945-107">Ten przykład tworzy przepływ pracy z wystąpieniem każde działanie do sprawdzania poprawności: <xref:System.Activities.Statements.If> działania i <xref:System.Activities.Statements.Pick> działania.</span><span class="sxs-lookup"><span data-stu-id="32945-107">This sample creates a workflow with an instance of each activity to validate: the <xref:System.Activities.Statements.If> activity and the <xref:System.Activities.Statements.Pick> activity.</span></span> <span data-ttu-id="32945-108">A <xref:System.Activities.Validation.Constraint> jest tworzona dla każdej zachowanie sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="32945-108">A <xref:System.Activities.Validation.Constraint> is created for each validation behavior.</span></span> <span data-ttu-id="32945-109">Ograniczenia utworzone w tym przykładzie są `ConstraintError_IfShouldHaveThenOrElse` i `ConstraintWarning_PickHasOneBranch`.</span><span class="sxs-lookup"><span data-stu-id="32945-109">The constraints created in this sample are `ConstraintError_IfShouldHaveThenOrElse` and `ConstraintWarning_PickHasOneBranch`.</span></span> <span data-ttu-id="32945-110">Następnie tych warunków ograniczających są dodawane do `AdditionalConstraints` Kolekcja <xref:System.Activities.Validation.ValidationSettings> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="32945-110">Next, these constraints are added to the `AdditionalConstraints` collection of a <xref:System.Activities.Validation.ValidationSettings> instance.</span></span> <span data-ttu-id="32945-111">Na koniec `static` <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> metoda <xref:System.Activities.Validation.ActivityValidationServices> jest wywoływane w celu weryfikacji działań w przepływie pracy i weryfikacji wyników wydrukowaniu się do konsoli.</span><span class="sxs-lookup"><span data-stu-id="32945-111">Finally, the `static`<xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> method of <xref:System.Activities.Validation.ActivityValidationServices> is called to validate the activities in the workflow and the validation results are printed out to the console.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="32945-112">Warunki ograniczające zasady można dodać do żadnego działania.</span><span class="sxs-lookup"><span data-stu-id="32945-112">You can add policy constraints to any activity.</span></span> <span data-ttu-id="32945-113">Na przykład można dodać ograniczenia zasad do <xref:System.Activities.Statements.Sequence> lub <xref:System.Activities.Statements.Parallel> działania.</span><span class="sxs-lookup"><span data-stu-id="32945-113">For example, you can add a policy constraint to a <xref:System.Activities.Statements.Sequence> or <xref:System.Activities.Statements.Parallel> activity.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="32945-114">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="32945-114">To use this sample</span></span>  
  
1.  <span data-ttu-id="32945-115">Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik ExternalActivityValidation.sln.</span><span class="sxs-lookup"><span data-stu-id="32945-115">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the ExternalActivityValidation.sln file.</span></span>  
  
2.  <span data-ttu-id="32945-116">Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="32945-116">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="32945-117">Aby uruchomić rozwiązanie, naciśnij klawisze Ctrl + F5.</span><span class="sxs-lookup"><span data-stu-id="32945-117">To run the solution, press Ctrl+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="32945-118">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="32945-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="32945-119">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="32945-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="32945-120">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="32945-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="32945-121">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="32945-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\ExternalActivityValidation`  
  
## <a name="see-also"></a><span data-ttu-id="32945-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="32945-122">See Also</span></span>
