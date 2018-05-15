---
title: Dla działania
ms.date: 03/30/2017
ms.assetid: 2ea751b4-36f0-48aa-a115-70a2ab89f6d8
ms.openlocfilehash: c79f295e7880f845c606a55f9c56ad65350f9c52
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="for-activity"></a><span data-ttu-id="fd45a-102">Dla działania</span><span class="sxs-lookup"><span data-stu-id="fd45a-102">For Activity</span></span>
<span data-ttu-id="fd45a-103">Przykładowe For demonstruje sposób tworzenia działań niestandardowych, która dziedziczy <xref:System.Activities.NativeActivity>i używać go w przepływie pracy można wykonać przykład rzeczywistych.</span><span class="sxs-lookup"><span data-stu-id="fd45a-103">The For sample demonstrates how to build a custom activity that inherits from <xref:System.Activities.NativeActivity>, and use it in a workflow to execute a real world example.</span></span> <span data-ttu-id="fd45a-104">Niestandardowe działania zawarte w tej funkcji próbki, takich jak C# `for` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="fd45a-104">The custom activity included in this sample functions like the C# `for` statement.</span></span> <span data-ttu-id="fd45a-105">T</span><span class="sxs-lookup"><span data-stu-id="fd45a-105">T</span></span>  
  
 <span data-ttu-id="fd45a-106">`For` Działania niestandardowego ma właściwości o nazwie `InitAction`, `IterationAction`, `Condition`, i `Body` odpowiadają inicjowania instrukcji, instrukcji iteracji, warunek kontynuacji i odpowiednio body — instrukcja znaleziono w standardowej C# `For` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="fd45a-106">The `For` custom activity has properties named `InitAction`, `IterationAction`, `Condition`, and `Body` that correspond to the initialization statement, iterative statement, continuation condition, and body statement respectively found in the standard C# `For` statement.</span></span>  
  
 <span data-ttu-id="fd45a-107">W poniższej tabeli opisano pliki klucza w próbce.</span><span class="sxs-lookup"><span data-stu-id="fd45a-107">The following table describes the key files in the sample.</span></span>  
  
|<span data-ttu-id="fd45a-108">Plik</span><span class="sxs-lookup"><span data-stu-id="fd45a-108">File</span></span>|<span data-ttu-id="fd45a-109">Opis</span><span class="sxs-lookup"><span data-stu-id="fd45a-109">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="fd45a-110">For.CS</span><span class="sxs-lookup"><span data-stu-id="fd45a-110">For.cs</span></span>|<span data-ttu-id="fd45a-111">Definicja klasy `For` działań niestandardowych, które rozszerza <xref:System.Activities.NativeActivity> klasę, aby umożliwić korzystanie z funkcji języka C# `For` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="fd45a-111">Class definition for the `For` custom activity, which extends the <xref:System.Activities.NativeActivity> class to provide the functionality of the C# `For` statement.</span></span>|  
|<span data-ttu-id="fd45a-112">Program.cs</span><span class="sxs-lookup"><span data-stu-id="fd45a-112">Program.cs</span></span>|<span data-ttu-id="fd45a-113">Aplikacji klienckiej, która wykonuje podstawowe pracy iteracji w kolekcji przy użyciu niestandardowego `For` działania.</span><span class="sxs-lookup"><span data-stu-id="fd45a-113">A client application that performs basic iterative work on a collection using the custom `For` activity.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="fd45a-114">Korzystając z `For` działań niestandardowych, upewnij się, że `Condition` ustawiono właściwość; w przeciwnym razie mogą wystąpić Pętla nieskończona.</span><span class="sxs-lookup"><span data-stu-id="fd45a-114">When using the `For` custom activity, ensure that the `Condition` property is set; otherwise an infinite loop could occur.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="fd45a-115">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="fd45a-115">Demonstrates</span></span>  
 <span data-ttu-id="fd45a-116">Tworzenie niestandardowego działania, która dziedziczy <xref:System.Activities.NativeActivity>.</span><span class="sxs-lookup"><span data-stu-id="fd45a-116">Create a custom activity that inherits from <xref:System.Activities.NativeActivity>.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="fd45a-117">Omówienie</span><span class="sxs-lookup"><span data-stu-id="fd45a-117">Discussion</span></span>  
 <span data-ttu-id="fd45a-118">W poniższej tabeli opisano właściwości działań zawarty w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="fd45a-118">The following table describes the properties of the activity included in this sample.</span></span>  
  
 <span data-ttu-id="fd45a-119">InitAction</span><span class="sxs-lookup"><span data-stu-id="fd45a-119">InitAction</span></span>  
 <span data-ttu-id="fd45a-120">Inicjowanie — instrukcja</span><span class="sxs-lookup"><span data-stu-id="fd45a-120">Initialization statement</span></span>  
  
 <span data-ttu-id="fd45a-121">IterationAction</span><span class="sxs-lookup"><span data-stu-id="fd45a-121">IterationAction</span></span>  
 <span data-ttu-id="fd45a-122">Iteracyjny — instrukcja</span><span class="sxs-lookup"><span data-stu-id="fd45a-122">Iterative statement</span></span>  
  
 <span data-ttu-id="fd45a-123">Warunek</span><span class="sxs-lookup"><span data-stu-id="fd45a-123">Condition</span></span>  
 <span data-ttu-id="fd45a-124">Kontynuacja — instrukcja</span><span class="sxs-lookup"><span data-stu-id="fd45a-124">Continuation statement</span></span>  
  
 <span data-ttu-id="fd45a-125">Treści</span><span class="sxs-lookup"><span data-stu-id="fd45a-125">Body</span></span>  
 <span data-ttu-id="fd45a-126">Treść instrukcji</span><span class="sxs-lookup"><span data-stu-id="fd45a-126">Body statement</span></span>  
  
 <span data-ttu-id="fd45a-127">Działanie dziedziczy <xref:System.Activities.NativeActivity> do uzyskania dostępu do środowiska wykonawczego funkcje, takie jak planowanie dodatkowe działania, aby uruchomić, przy użyciu jednej z `ScheduleActivity` metody <xref:System.Activities.NativeActivityContext>.</span><span class="sxs-lookup"><span data-stu-id="fd45a-127">The activity inherits from <xref:System.Activities.NativeActivity> to gain access to runtime features such as scheduling additional activities to run, using one of the `ScheduleActivity` methods of <xref:System.Activities.NativeActivityContext>.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="fd45a-128">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="fd45a-128">To use this sample</span></span>  
  
1.  <span data-ttu-id="fd45a-129">Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania For.sln.</span><span class="sxs-lookup"><span data-stu-id="fd45a-129">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the For.sln solution file.</span></span>  
  
2.  <span data-ttu-id="fd45a-130">Skompiluj rozwiązanie, naciskając klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="fd45a-130">Build the solution, by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="fd45a-131">Uruchom rozwiązanie, naciskając klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="fd45a-131">Run the solution, by pressing F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fd45a-132">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="fd45a-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="fd45a-133">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="fd45a-133">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="fd45a-134">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="fd45a-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fd45a-135">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="fd45a-135">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\For`