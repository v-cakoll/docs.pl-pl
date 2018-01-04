---
title: "Sprawdzanie poprawności relacje działania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6f11a34e-ed67-4bce-88ce-7e96bbb4d052
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 93cb5e93791c001e3795408a4c6b77be772f26e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="activity-relationships-validation"></a><span data-ttu-id="27270-102">Sprawdzanie poprawności relacje działania</span><span class="sxs-lookup"><span data-stu-id="27270-102">Activity Relationships Validation</span></span>
<span data-ttu-id="27270-103">Ten przykład zawiera trzy działań `CreateCity`, `CreateState`, i `CreateCountry`.</span><span class="sxs-lookup"><span data-stu-id="27270-103">This sample consists of three activities, `CreateCity`, `CreateState`, and `CreateCountry`.</span></span> <span data-ttu-id="27270-104">`CreateCity`musi znajdować się wewnątrz `CreateState` działania, a `CreateState` musi znajdować się wewnątrz `CreateCountry` działania.</span><span class="sxs-lookup"><span data-stu-id="27270-104">`CreateCity` must be inside a `CreateState` activity, and `CreateState` must be inside a `CreateCountry` activity.</span></span> <span data-ttu-id="27270-105">Na potrzeby tej próbki, logikę weryfikacji jest w kodzie `CreateState` działania, a w języku XAML dla `CreateCity` działania.</span><span class="sxs-lookup"><span data-stu-id="27270-105">For the purpose of this sample, the validation logic is in code for the `CreateState` activity, and in XAML for the `CreateCity` activity.</span></span> <span data-ttu-id="27270-106">Zarówno ograniczeń ma takie samo zachowanie.</span><span class="sxs-lookup"><span data-stu-id="27270-106">Both constraints have the same behavior.</span></span>  
  
 <span data-ttu-id="27270-107">[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] Udostępnia następujące trzy działania pomocnika, które umożliwiają deweloperom zweryfikować relacje między działaniami:</span><span class="sxs-lookup"><span data-stu-id="27270-107">The [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] provides the following three helper activities that allow the developer to validate relationships between activities:</span></span>  
  
 <xref:System.Activities.Validation.GetParentChain>  
 <span data-ttu-id="27270-108">Zapewnia zbiór wszystkich działań, które należą do obiektu nadrzędnego bieżącego węzła</span><span class="sxs-lookup"><span data-stu-id="27270-108">Provides the collection of all activities that belong to the parent of the current node</span></span>  
  
 <xref:System.Activities.Validation.GetChildSubtree>  
 <span data-ttu-id="27270-109">Zapewnia zbiór wszystkich działań, które należą do poddrzewa bieżącego węzła, z wyłączeniem bieżącego węzła</span><span class="sxs-lookup"><span data-stu-id="27270-109">Provides the collection of all activities that belong to the sub-tree of the current node, excluding the current node</span></span>  
  
 <xref:System.Activities.Validation.GetWorkflowTree>  
 <span data-ttu-id="27270-110">Zapewnia zbiór wszystkich działań w tym samym drzewie jako bieżącego węzła</span><span class="sxs-lookup"><span data-stu-id="27270-110">Provides the collection of all activities in the same tree as the current node</span></span>  
  
 <span data-ttu-id="27270-111">W przykładzie <xref:System.Activities.Statements.ForEach%601> to działanie służy do przeprowadzenie kolekcji zwróconej przez <xref:System.Activities.Validation.GetParentChain>.</span><span class="sxs-lookup"><span data-stu-id="27270-111">In the sample, a <xref:System.Activities.Statements.ForEach%601> activity is used to walk through the collection returned by <xref:System.Activities.Validation.GetParentChain>.</span></span> <span data-ttu-id="27270-112">Dla każdego elementu w kolekcji, jego typ jest porównywany z `CreateCountry` (lub `CreateState` Jeśli `CreateCity` jest sprawdzana), a gdy dopasowanie znajduje się wynik flaga jest ustawiona na `true`.</span><span class="sxs-lookup"><span data-stu-id="27270-112">For every element in the collection, its type is compared to `CreateCountry` (or `CreateState` if `CreateCity` is being validated), and when a match is found the result flag is set to `true`.</span></span> <span data-ttu-id="27270-113">Na koniec <xref:System.Activities.Validation.AssertValidation> służy do generowania błąd sprawdzania poprawności, jeśli ustawiono flagę wynik `false`.</span><span class="sxs-lookup"><span data-stu-id="27270-113">Finally, an <xref:System.Activities.Validation.AssertValidation> is used to generate a validation error if the result flag is set to `false`.</span></span>  
  
### <a name="to-use-this-sample"></a><span data-ttu-id="27270-114">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="27270-114">To use this sample</span></span>  
  
1.  <span data-ttu-id="27270-115">Otwórz rozwiązanie próbki ContainmentValidation.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="27270-115">Open the ContainmentValidation.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="27270-116">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="27270-116">Build the solution.</span></span>  
  
3.  <span data-ttu-id="27270-117">Naciśnij klawisze CTRL + F5, aby uruchomić program.</span><span class="sxs-lookup"><span data-stu-id="27270-117">Press CTRL + F5 to launch the program.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="27270-118">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="27270-118">The samples may already be installed on your computer.</span></span> <span data-ttu-id="27270-119">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne):</span><span class="sxs-lookup"><span data-stu-id="27270-119">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="27270-120">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="27270-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="27270-121">W tym przykładzie znajduje się w następującym katalogu:</span><span class="sxs-lookup"><span data-stu-id="27270-121">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\ActivityRelationships`
