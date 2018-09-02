---
title: Używanie działania Pick
ms.date: 03/30/2017
ms.assetid: b89be812-a247-4025-b0e3-ffb20db027a6
ms.openlocfilehash: 193b60bff7b08c0de9a0957668483eb73be97274
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43452609"
---
# <a name="using-the-pick-activity"></a><span data-ttu-id="990db-102">Używanie działania Pick</span><span class="sxs-lookup"><span data-stu-id="990db-102">Using the Pick Activity</span></span>
<span data-ttu-id="990db-103">W tym przykładzie przedstawiono sposób użycia <xref:System.Activities.Statements.Pick> działania.</span><span class="sxs-lookup"><span data-stu-id="990db-103">This sample demonstrates how to use the <xref:System.Activities.Statements.Pick> activity.</span></span>  
  
 <span data-ttu-id="990db-104"><xref:System.Activities.Statements.Pick> Działania zawiera kontrolki oparte na zdarzeniach modelowania.</span><span class="sxs-lookup"><span data-stu-id="990db-104">The <xref:System.Activities.Statements.Pick> activity provides event-based control modeling.</span></span> <span data-ttu-id="990db-105">Zachowuje się podobnie jak C# `switch` instrukcję, która wykonuje tylko jeden z gałęzi, skorzystaj z `switch` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="990db-105">It behaves similar to the C# `switch` statement, which executes only one of the branches in the `switch` statement.</span></span> <span data-ttu-id="990db-106">W odróżnieniu od `switch` na podstawie instrukcji, w którym jest wykonywana gałąź na podstawie wartości <xref:System.Activities.Statements.Pick> działanie wykonuje gałęzi, w zależności od sposobu zakończy działanie.</span><span class="sxs-lookup"><span data-stu-id="990db-106">Unlike the `switch` statement in which a branch is executed based upon on a value, the <xref:System.Activities.Statements.Pick> activity executes a branch based upon how an activity completes.</span></span>  
  
 <span data-ttu-id="990db-107">W tym przykładzie monituje użytkownika o wpisanie nazwy w konsoli w danym okresie czasu.</span><span class="sxs-lookup"><span data-stu-id="990db-107">This sample prompts a user to type in their name on the console within a given time period.</span></span> <span data-ttu-id="990db-108"><xref:System.Activities.Statements.Pick> Działanie w próbce ma dwie gałęzie, które są wykonywane na podstawie tego, czy użytkownik wpisze w ich imieniu w ciągu 5 sekund, czy nie.</span><span class="sxs-lookup"><span data-stu-id="990db-108">The <xref:System.Activities.Statements.Pick> activity in the sample has two branches that are executed based upon whether the user types in their name within 5 seconds or not.</span></span> <span data-ttu-id="990db-109">Jeśli użytkownik wpisze w ich imieniu w ciągu 5 sekund, zostanie wykonany pierwszej gałęzi, który zawiera niestandardowy `ReadLine` działanie; w przeciwnym razie innej gałęzi jest wykonywane, który zawiera <xref:System.Activities.Statements.Delay> działania.</span><span class="sxs-lookup"><span data-stu-id="990db-109">If the user types in their name within 5 seconds, the first branch is executed, which contains a custom `ReadLine` activity; otherwise the other branch is executed, which contains a <xref:System.Activities.Statements.Delay> activity.</span></span> <span data-ttu-id="990db-110">Po wpisaniu nazwy użytkownika w konsoli nazwy użytkownika jest drukowany w konsoli.</span><span class="sxs-lookup"><span data-stu-id="990db-110">Once a user’s name is typed in on the console, the user’s name is printed on the console.</span></span> <span data-ttu-id="990db-111">Jeśli dane wejściowe nie zostanie wprowadzona w ciągu 5 sekund, operacja przekroczyła limit czasu.</span><span class="sxs-lookup"><span data-stu-id="990db-111">If an input is not entered within 5 seconds, the operation is timed out.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="990db-112">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="990db-112">Demonstrates</span></span>  
 <span data-ttu-id="990db-113"><xref:System.Activities.Statements.Pick> działanie.</span><span class="sxs-lookup"><span data-stu-id="990db-113"><xref:System.Activities.Statements.Pick> activity.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="990db-114">Dyskusja</span><span class="sxs-lookup"><span data-stu-id="990db-114">Discussion</span></span>  
 <span data-ttu-id="990db-115">Przykład obejmuje projektanta przepływu pracy i kodowany przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="990db-115">The sample includes a Designer workflow and coded workflow.</span></span>  
  
 <span data-ttu-id="990db-116">Projektant przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="990db-116">Designer Workflow</span></span>  
 <span data-ttu-id="990db-117">Projektant wersję przykładu przedstawia sposób tworzenia przepływu pracy w projektancie.</span><span class="sxs-lookup"><span data-stu-id="990db-117">The Designer version of the sample demonstrates how to create a workflow in the designer.</span></span> <span data-ttu-id="990db-118">Uwzględnione są następujące pliki:</span><span class="sxs-lookup"><span data-stu-id="990db-118">The following files are included:</span></span>  
  
-   <span data-ttu-id="990db-119">Plik program.CS: Zawiera `Main` funkcja, która wykonuje przykładowy przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="990db-119">Program.cs : Includes the `Main` function that executes the sample workflow.</span></span>  
  
-   <span data-ttu-id="990db-120">ReadString.cs: Niestandardowe działanie, które odczytuje dane wejściowe z konsoli.</span><span class="sxs-lookup"><span data-stu-id="990db-120">ReadString.cs: A custom activity that reads some input from the console.</span></span>  
  
-   <span data-ttu-id="990db-121">Sequence1.XAML: Przepływ pracy przy użyciu projektanta, który używa wybierz.</span><span class="sxs-lookup"><span data-stu-id="990db-121">Sequence1.xaml: A workflow created using the designer that uses Pick.</span></span>  
  
 <span data-ttu-id="990db-122">Kodowane przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="990db-122">Coded Workflow</span></span>  
 <span data-ttu-id="990db-123">Kodowane wersję przykładu przedstawia sposób tworzenia przepływu pracy w projektancie.</span><span class="sxs-lookup"><span data-stu-id="990db-123">The coded version of the sample demonstrates how to create a workflow in the designer.</span></span> <span data-ttu-id="990db-124">Uwzględnione są następujące pliki:</span><span class="sxs-lookup"><span data-stu-id="990db-124">The following files are included:</span></span>  
  
-   <span data-ttu-id="990db-125">Plik program.CS: Zawiera `Main` funkcja, która wykonuje przykładowy przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="990db-125">Program.cs : Includes the `Main` function that executes the sample workflow.</span></span>  
  
-   <span data-ttu-id="990db-126">ReadString.cs: Niestandardowe działanie, które odczytuje dane wejściowe z konsoli.</span><span class="sxs-lookup"><span data-stu-id="990db-126">ReadString.cs: A custom activity that reads some input from the console.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="990db-127">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="990db-127">To use this sample</span></span>  
  
1.  <span data-ttu-id="990db-128">Za pomocą [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania Pick.sln.</span><span class="sxs-lookup"><span data-stu-id="990db-128">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the Pick.sln solution file.</span></span>  
  
2.  <span data-ttu-id="990db-129">Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="990db-129">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="990db-130">Aby uruchomić rozwiązanie, naciśnij klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="990db-130">To run the solution, press F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="990db-131">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="990db-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="990db-132">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="990db-132">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="990db-133">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="990db-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="990db-134">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="990db-134">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Pick`