---
title: "Przy użyciu działaniu wybierz"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b89be812-a247-4025-b0e3-ffb20db027a6
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 01cad73bfe5e741c104a8c8e5e9d66f7564c7067
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="using-the-pick-activity"></a><span data-ttu-id="15bd8-102">Przy użyciu działaniu wybierz</span><span class="sxs-lookup"><span data-stu-id="15bd8-102">Using the Pick Activity</span></span>
<span data-ttu-id="15bd8-103">W tym przykładzie przedstawiono sposób użycia <xref:System.Activities.Statements.Pick> działania.</span><span class="sxs-lookup"><span data-stu-id="15bd8-103">This sample demonstrates how to use the <xref:System.Activities.Statements.Pick> activity.</span></span>  
  
 <span data-ttu-id="15bd8-104"><xref:System.Activities.Statements.Pick> Działania zawiera kontrolki oparte na zdarzeniu modelowania.</span><span class="sxs-lookup"><span data-stu-id="15bd8-104">The <xref:System.Activities.Statements.Pick> activity provides event-based control modeling.</span></span> <span data-ttu-id="15bd8-105">Działa podobnie do języka C# `switch` instrukcji, która jest wykonywana tylko jednej z gałęzi w `switch` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="15bd8-105">It behaves similar to the C# `switch` statement, which executes only one of the branches in the `switch` statement.</span></span> <span data-ttu-id="15bd8-106">W odróżnieniu od `switch` na podstawie instrukcji, w którym jest wykonywane gałęzi przy użyciu wartości <xref:System.Activities.Statements.Pick> gałąź ustalane na podstawie sposobu kończy działanie wykonuje działania.</span><span class="sxs-lookup"><span data-stu-id="15bd8-106">Unlike the `switch` statement in which a branch is executed based upon on a value, the <xref:System.Activities.Statements.Pick> activity executes a branch based upon how an activity completes.</span></span>  
  
 <span data-ttu-id="15bd8-107">W tym przykładzie monituje użytkownika o wpisanie nazwy na konsoli w danym okresie.</span><span class="sxs-lookup"><span data-stu-id="15bd8-107">This sample prompts a user to type in their name on the console within a given time period.</span></span> <span data-ttu-id="15bd8-108"><xref:System.Activities.Statements.Pick> Działanie w próbce ma dwie gałęzie, które są ustalane na podstawie tego, czy użytkownik wpisze w ich imieniu w ciągu 5 sekund, czy nie.</span><span class="sxs-lookup"><span data-stu-id="15bd8-108">The <xref:System.Activities.Statements.Pick> activity in the sample has two branches that are executed based upon whether the user types in their name within 5 seconds or not.</span></span> <span data-ttu-id="15bd8-109">Jeśli użytkownik wpisze w ich imieniu w ciągu 5 sekund, jest wykonywane pierwszej gałęzi, który zawiera niestandardowy `ReadLine` działanie; w przeciwnym razie innej gałęzi jest wykonywane, który zawiera <xref:System.Activities.Statements.Delay> działania.</span><span class="sxs-lookup"><span data-stu-id="15bd8-109">If the user types in their name within 5 seconds, the first branch is executed, which contains a custom `ReadLine` activity; otherwise the other branch is executed, which contains a <xref:System.Activities.Statements.Delay> activity.</span></span> <span data-ttu-id="15bd8-110">Gdy nazwa użytkownika jest wpisany w konsoli, nazwa użytkownika jest drukowane na konsoli.</span><span class="sxs-lookup"><span data-stu-id="15bd8-110">Once a user’s name is typed in on the console, the user’s name is printed on the console.</span></span> <span data-ttu-id="15bd8-111">Jeśli dane wejściowe nie została wprowadzona w ciągu 5 sekund, jest upłynął limit czasu operacji.</span><span class="sxs-lookup"><span data-stu-id="15bd8-111">If an input is not entered within 5 seconds, the operation is timed out.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="15bd8-112">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="15bd8-112">Demonstrates</span></span>  
 <span data-ttu-id="15bd8-113"><xref:System.Activities.Statements.Pick>działanie.</span><span class="sxs-lookup"><span data-stu-id="15bd8-113"><xref:System.Activities.Statements.Pick> activity.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="15bd8-114">Omówienie</span><span class="sxs-lookup"><span data-stu-id="15bd8-114">Discussion</span></span>  
 <span data-ttu-id="15bd8-115">Przykład zawiera projektanta przepływów pracy i kodowanego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="15bd8-115">The sample includes a Designer workflow and coded workflow.</span></span>  
  
 <span data-ttu-id="15bd8-116">Projektant przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="15bd8-116">Designer Workflow</span></span>  
 <span data-ttu-id="15bd8-117">Wersja projektanta przykładowych pokazano, jak utworzyć przepływ pracy w projektancie.</span><span class="sxs-lookup"><span data-stu-id="15bd8-117">The Designer version of the sample demonstrates how to create a workflow in the designer.</span></span> <span data-ttu-id="15bd8-118">Zawarte są następujące pliki:</span><span class="sxs-lookup"><span data-stu-id="15bd8-118">The following files are included:</span></span>  
  
-   <span data-ttu-id="15bd8-119">Plik program.CS: Zawiera `Main` funkcji, która wykonuje przykładowego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="15bd8-119">Program.cs : Includes the `Main` function that executes the sample workflow.</span></span>  
  
-   <span data-ttu-id="15bd8-120">ReadString.cs: Niestandardowe działanie, które odczytuje niektóre dane wejściowe z konsoli.</span><span class="sxs-lookup"><span data-stu-id="15bd8-120">ReadString.cs: A custom activity that reads some input from the console.</span></span>  
  
-   <span data-ttu-id="15bd8-121">Sequence1.XAML: Przepływ pracy utworzony za pomocą projektanta, który używa pobrania.</span><span class="sxs-lookup"><span data-stu-id="15bd8-121">Sequence1.xaml: A workflow created using the designer that uses Pick.</span></span>  
  
 <span data-ttu-id="15bd8-122">Kodowane przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="15bd8-122">Coded Workflow</span></span>  
 <span data-ttu-id="15bd8-123">Kodowane wersją przykładu przedstawia sposób tworzenia przepływu pracy w projektancie.</span><span class="sxs-lookup"><span data-stu-id="15bd8-123">The coded version of the sample demonstrates how to create a workflow in the designer.</span></span> <span data-ttu-id="15bd8-124">Zawarte są następujące pliki:</span><span class="sxs-lookup"><span data-stu-id="15bd8-124">The following files are included:</span></span>  
  
-   <span data-ttu-id="15bd8-125">Plik program.CS: Zawiera `Main` funkcji, która wykonuje przykładowego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="15bd8-125">Program.cs : Includes the `Main` function that executes the sample workflow.</span></span>  
  
-   <span data-ttu-id="15bd8-126">ReadString.cs: Niestandardowe działanie, które odczytuje niektóre dane wejściowe z konsoli.</span><span class="sxs-lookup"><span data-stu-id="15bd8-126">ReadString.cs: A custom activity that reads some input from the console.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="15bd8-127">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="15bd8-127">To use this sample</span></span>  
  
1.  <span data-ttu-id="15bd8-128">Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania Pick.sln.</span><span class="sxs-lookup"><span data-stu-id="15bd8-128">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the Pick.sln solution file.</span></span>  
  
2.  <span data-ttu-id="15bd8-129">Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="15bd8-129">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="15bd8-130">Aby uruchomić rozwiązanie, naciśnij klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="15bd8-130">To run the solution, press F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="15bd8-131">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="15bd8-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="15bd8-132">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="15bd8-132">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="15bd8-133">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="15bd8-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="15bd8-134">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="15bd8-134">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Pick`