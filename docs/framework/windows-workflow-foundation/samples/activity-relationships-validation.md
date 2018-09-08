---
title: Walidacja relacji działań
ms.date: 03/30/2017
ms.assetid: 6f11a34e-ed67-4bce-88ce-7e96bbb4d052
ms.openlocfilehash: 50f08118fb5ad4d9b8fe809e7ab3cc5d57f28149
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44193669"
---
# <a name="activity-relationships-validation"></a><span data-ttu-id="83898-102">Walidacja relacji działań</span><span class="sxs-lookup"><span data-stu-id="83898-102">Activity Relationships Validation</span></span>
<span data-ttu-id="83898-103">W tym przykładzie składa się z trzech działań `CreateCity`, `CreateState`, i `CreateCountry`.</span><span class="sxs-lookup"><span data-stu-id="83898-103">This sample consists of three activities, `CreateCity`, `CreateState`, and `CreateCountry`.</span></span> <span data-ttu-id="83898-104">`CreateCity` musi znajdować się wewnątrz `CreateState` działania i `CreateState` musi znajdować się wewnątrz `CreateCountry` działania.</span><span class="sxs-lookup"><span data-stu-id="83898-104">`CreateCity` must be inside a `CreateState` activity, and `CreateState` must be inside a `CreateCountry` activity.</span></span> <span data-ttu-id="83898-105">Na potrzeby tego przykładu logikę weryfikacji jest w kodzie `CreateState` działania w XAML dla `CreateCity` działania.</span><span class="sxs-lookup"><span data-stu-id="83898-105">For the purpose of this sample, the validation logic is in code for the `CreateState` activity, and in XAML for the `CreateCity` activity.</span></span> <span data-ttu-id="83898-106">Oba ograniczenia mają takie samo zachowanie.</span><span class="sxs-lookup"><span data-stu-id="83898-106">Both constraints have the same behavior.</span></span>  
  
 <span data-ttu-id="83898-107">[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] Udostępnia następujące trzy działań pomocnika, które umożliwiają deweloperom zweryfikować relacji między działaniami:</span><span class="sxs-lookup"><span data-stu-id="83898-107">The [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] provides the following three helper activities that allow the developer to validate relationships between activities:</span></span>  
  
 <xref:System.Activities.Validation.GetParentChain>  
 <span data-ttu-id="83898-108">Zawiera zbiór wszystkich działań, które należą do elementu nadrzędnego bieżącego węzła</span><span class="sxs-lookup"><span data-stu-id="83898-108">Provides the collection of all activities that belong to the parent of the current node</span></span>  
  
 <xref:System.Activities.Validation.GetChildSubtree>  
 <span data-ttu-id="83898-109">Zawiera zbiór wszystkich działań, które należą do podrzędnych drzewa w bieżącego węzła, z wyłączeniem bieżącego węzła</span><span class="sxs-lookup"><span data-stu-id="83898-109">Provides the collection of all activities that belong to the sub-tree of the current node, excluding the current node</span></span>  
  
 <xref:System.Activities.Validation.GetWorkflowTree>  
 <span data-ttu-id="83898-110">Zawiera zbiór wszystkich działań w tym samym drzewie jako bieżącego węzła</span><span class="sxs-lookup"><span data-stu-id="83898-110">Provides the collection of all activities in the same tree as the current node</span></span>  
  
 <span data-ttu-id="83898-111">W tym przykładzie <xref:System.Activities.Statements.ForEach%601> to działanie służy do zaprezentowania zbiorze zwróconym przez <xref:System.Activities.Validation.GetParentChain>.</span><span class="sxs-lookup"><span data-stu-id="83898-111">In the sample, a <xref:System.Activities.Statements.ForEach%601> activity is used to walk through the collection returned by <xref:System.Activities.Validation.GetParentChain>.</span></span> <span data-ttu-id="83898-112">Dla każdego elementu w kolekcji, jego typ jest porównywany z `CreateCountry` (lub `CreateState` Jeśli `CreateCity` jest weryfikowany), a kiedy zostanie znalezione dopasowanie Flaga wynik jest ustawiona na `true`.</span><span class="sxs-lookup"><span data-stu-id="83898-112">For every element in the collection, its type is compared to `CreateCountry` (or `CreateState` if `CreateCity` is being validated), and when a match is found the result flag is set to `true`.</span></span> <span data-ttu-id="83898-113">Na koniec <xref:System.Activities.Validation.AssertValidation> służy do generowania błąd sprawdzania poprawności, jeśli ustawiono flagę wynik `false`.</span><span class="sxs-lookup"><span data-stu-id="83898-113">Finally, an <xref:System.Activities.Validation.AssertValidation> is used to generate a validation error if the result flag is set to `false`.</span></span>  
  
### <a name="to-use-this-sample"></a><span data-ttu-id="83898-114">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="83898-114">To use this sample</span></span>  
  
1.  <span data-ttu-id="83898-115">Otwórz rozwiązanie przykładowe ContainmentValidation.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="83898-115">Open the ContainmentValidation.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="83898-116">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="83898-116">Build the solution.</span></span>  
  
3.  <span data-ttu-id="83898-117">Naciśnij klawisze CTRL + F5, aby uruchomić program.</span><span class="sxs-lookup"><span data-stu-id="83898-117">Press CTRL + F5 to launch the program.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="83898-118">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="83898-118">The samples may already be installed on your computer.</span></span> <span data-ttu-id="83898-119">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne):</span><span class="sxs-lookup"><span data-stu-id="83898-119">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="83898-120">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="83898-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="83898-121">W tym przykładzie znajduje się w następującym katalogu:</span><span class="sxs-lookup"><span data-stu-id="83898-121">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\ActivityRelationships`
