---
title: Dla działania
ms.date: 03/30/2017
ms.assetid: 2ea751b4-36f0-48aa-a115-70a2ab89f6d8
ms.openlocfilehash: 7a7023abb9057ab4b25552fbf9a81cd2ae2b4e88
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43801849"
---
# <a name="for-activity"></a><span data-ttu-id="cf5dc-102">Dla działania</span><span class="sxs-lookup"><span data-stu-id="cf5dc-102">For Activity</span></span>
<span data-ttu-id="cf5dc-103">Przykład dla pokazuje, jak utworzyć niestandardowe działanie, która dziedziczy z <xref:System.Activities.NativeActivity>i korzystać z niego w przepływie pracy można wykonać przykład rzeczywistych.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-103">The For sample demonstrates how to build a custom activity that inherits from <xref:System.Activities.NativeActivity>, and use it in a workflow to execute a real world example.</span></span> <span data-ttu-id="cf5dc-104">Niestandardowe działanie zawarte w tej funkcji próbki, takich jak C# `for` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-104">The custom activity included in this sample functions like the C# `for` statement.</span></span> <span data-ttu-id="cf5dc-105">T</span><span class="sxs-lookup"><span data-stu-id="cf5dc-105">T</span></span>  
  
 <span data-ttu-id="cf5dc-106">`For` Niestandardowe działanie ma właściwości o nazwie `InitAction`, `IterationAction`, `Condition`, i `Body` odpowiadają inicjowania instrukcji, instrukcja iteracyjne, warunek kontynuacji i odpowiednio treść instrukcji znaleziono w standard języka C# `For` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-106">The `For` custom activity has properties named `InitAction`, `IterationAction`, `Condition`, and `Body` that correspond to the initialization statement, iterative statement, continuation condition, and body statement respectively found in the standard C# `For` statement.</span></span>  
  
 <span data-ttu-id="cf5dc-107">W poniższej tabeli opisano pliki klucza w próbce.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-107">The following table describes the key files in the sample.</span></span>  
  
|<span data-ttu-id="cf5dc-108">Plik</span><span class="sxs-lookup"><span data-stu-id="cf5dc-108">File</span></span>|<span data-ttu-id="cf5dc-109">Opis</span><span class="sxs-lookup"><span data-stu-id="cf5dc-109">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="cf5dc-110">For.CS</span><span class="sxs-lookup"><span data-stu-id="cf5dc-110">For.cs</span></span>|<span data-ttu-id="cf5dc-111">Definicja klasy `For` działania niestandardowe, które rozszerza <xref:System.Activities.NativeActivity> klasy w celu zapewnienia funkcji języka C# `For` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-111">Class definition for the `For` custom activity, which extends the <xref:System.Activities.NativeActivity> class to provide the functionality of the C# `For` statement.</span></span>|  
|<span data-ttu-id="cf5dc-112">Program.cs</span><span class="sxs-lookup"><span data-stu-id="cf5dc-112">Program.cs</span></span>|<span data-ttu-id="cf5dc-113">Aplikacja kliencka, która wykonuje podstawowe prace kolekcji za pomocą niestandardowej `For` działania.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-113">A client application that performs basic iterative work on a collection using the custom `For` activity.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="cf5dc-114">Korzystając z `For` działania niestandardowego, upewnij się, że `Condition` ustawiono właściwość; w przeciwnym razie mogą wystąpić wejścia w nieskończoną pętlę.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-114">When using the `For` custom activity, ensure that the `Condition` property is set; otherwise an infinite loop could occur.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="cf5dc-115">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="cf5dc-115">Demonstrates</span></span>  
 <span data-ttu-id="cf5dc-116">Utwórz niestandardowe działanie, która dziedziczy <xref:System.Activities.NativeActivity>.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-116">Create a custom activity that inherits from <xref:System.Activities.NativeActivity>.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="cf5dc-117">Dyskusja</span><span class="sxs-lookup"><span data-stu-id="cf5dc-117">Discussion</span></span>  
 <span data-ttu-id="cf5dc-118">W poniższej tabeli opisano właściwości działań zawarty w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-118">The following table describes the properties of the activity included in this sample.</span></span>  
  
 <span data-ttu-id="cf5dc-119">InitAction</span><span class="sxs-lookup"><span data-stu-id="cf5dc-119">InitAction</span></span>  
 <span data-ttu-id="cf5dc-120">Inicjowanie — instrukcja</span><span class="sxs-lookup"><span data-stu-id="cf5dc-120">Initialization statement</span></span>  
  
 <span data-ttu-id="cf5dc-121">IterationAction</span><span class="sxs-lookup"><span data-stu-id="cf5dc-121">IterationAction</span></span>  
 <span data-ttu-id="cf5dc-122">Iteracyjne — instrukcja</span><span class="sxs-lookup"><span data-stu-id="cf5dc-122">Iterative statement</span></span>  
  
 <span data-ttu-id="cf5dc-123">Warunek</span><span class="sxs-lookup"><span data-stu-id="cf5dc-123">Condition</span></span>  
 <span data-ttu-id="cf5dc-124">Instrukcja kontynuacji</span><span class="sxs-lookup"><span data-stu-id="cf5dc-124">Continuation statement</span></span>  
  
 <span data-ttu-id="cf5dc-125">Treść</span><span class="sxs-lookup"><span data-stu-id="cf5dc-125">Body</span></span>  
 <span data-ttu-id="cf5dc-126">Treść instrukcji</span><span class="sxs-lookup"><span data-stu-id="cf5dc-126">Body statement</span></span>  
  
 <span data-ttu-id="cf5dc-127">Działanie dziedziczy <xref:System.Activities.NativeActivity> do uzyskania dostępu do funkcji środowiska uruchomieniowego, takich jak dodatkowe działania, aby uruchomić, planowania, przy użyciu jednej z `ScheduleActivity` metody <xref:System.Activities.NativeActivityContext>.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-127">The activity inherits from <xref:System.Activities.NativeActivity> to gain access to runtime features such as scheduling additional activities to run, using one of the `ScheduleActivity` methods of <xref:System.Activities.NativeActivityContext>.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="cf5dc-128">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="cf5dc-128">To use this sample</span></span>  
  
1.  <span data-ttu-id="cf5dc-129">Za pomocą [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania For.sln.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-129">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the For.sln solution file.</span></span>  
  
2.  <span data-ttu-id="cf5dc-130">Skompiluj rozwiązanie, naciskając klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-130">Build the solution, by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="cf5dc-131">Uruchom rozwiązanie, naciskając klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-131">Run the solution, by pressing F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="cf5dc-132">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="cf5dc-133">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="cf5dc-133">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="cf5dc-134">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cf5dc-135">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="cf5dc-135">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\For`