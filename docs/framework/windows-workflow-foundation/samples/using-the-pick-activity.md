---
title: Używanie działania Pick
ms.date: 03/30/2017
ms.assetid: b89be812-a247-4025-b0e3-ffb20db027a6
ms.openlocfilehash: 0b2fbeb9b32406dd913d7e1ee87ac167113d0f28
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59302985"
---
# <a name="using-the-pick-activity"></a><span data-ttu-id="7cb23-102">Używanie działania Pick</span><span class="sxs-lookup"><span data-stu-id="7cb23-102">Using the Pick Activity</span></span>
<span data-ttu-id="7cb23-103">W tym przykładzie przedstawiono sposób użycia <xref:System.Activities.Statements.Pick> działania.</span><span class="sxs-lookup"><span data-stu-id="7cb23-103">This sample demonstrates how to use the <xref:System.Activities.Statements.Pick> activity.</span></span>

 <span data-ttu-id="7cb23-104"><xref:System.Activities.Statements.Pick> Działania zawiera kontrolki oparte na zdarzeniach modelowania.</span><span class="sxs-lookup"><span data-stu-id="7cb23-104">The <xref:System.Activities.Statements.Pick> activity provides event-based control modeling.</span></span> <span data-ttu-id="7cb23-105">Zachowuje się podobnie jak C# `switch` instrukcję, która wykonuje tylko jeden z gałęzi, skorzystaj z `switch` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="7cb23-105">It behaves similar to the C# `switch` statement, which executes only one of the branches in the `switch` statement.</span></span> <span data-ttu-id="7cb23-106">W odróżnieniu od `switch` na podstawie instrukcji, w którym jest wykonywana gałąź na podstawie wartości <xref:System.Activities.Statements.Pick> działanie wykonuje gałęzi, w zależności od sposobu zakończy działanie.</span><span class="sxs-lookup"><span data-stu-id="7cb23-106">Unlike the `switch` statement in which a branch is executed based upon on a value, the <xref:System.Activities.Statements.Pick> activity executes a branch based upon how an activity completes.</span></span>

 <span data-ttu-id="7cb23-107">W tym przykładzie monituje użytkownika o wpisanie nazwy w konsoli w danym okresie czasu.</span><span class="sxs-lookup"><span data-stu-id="7cb23-107">This sample prompts a user to type in their name on the console within a given time period.</span></span> <span data-ttu-id="7cb23-108"><xref:System.Activities.Statements.Pick> Działanie w próbce ma dwie gałęzie, które są wykonywane na podstawie tego, czy użytkownik wpisze w ich imieniu w ciągu 5 sekund, czy nie.</span><span class="sxs-lookup"><span data-stu-id="7cb23-108">The <xref:System.Activities.Statements.Pick> activity in the sample has two branches that are executed based upon whether the user types in their name within 5 seconds or not.</span></span> <span data-ttu-id="7cb23-109">Jeśli użytkownik wpisze w ich imieniu w ciągu 5 sekund, zostanie wykonany pierwszej gałęzi, który zawiera niestandardowy `ReadLine` działanie; w przeciwnym razie innej gałęzi jest wykonywane, który zawiera <xref:System.Activities.Statements.Delay> działania.</span><span class="sxs-lookup"><span data-stu-id="7cb23-109">If the user types in their name within 5 seconds, the first branch is executed, which contains a custom `ReadLine` activity; otherwise the other branch is executed, which contains a <xref:System.Activities.Statements.Delay> activity.</span></span> <span data-ttu-id="7cb23-110">Po wpisaniu nazwy użytkownika w konsoli nazwy użytkownika jest drukowany w konsoli.</span><span class="sxs-lookup"><span data-stu-id="7cb23-110">Once a user’s name is typed in on the console, the user’s name is printed on the console.</span></span> <span data-ttu-id="7cb23-111">Jeśli dane wejściowe nie zostanie wprowadzona w ciągu 5 sekund, operacja przekroczyła limit czasu.</span><span class="sxs-lookup"><span data-stu-id="7cb23-111">If an input is not entered within 5 seconds, the operation is timed out.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="7cb23-112">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="7cb23-112">Demonstrates</span></span>
 <span data-ttu-id="7cb23-113"><xref:System.Activities.Statements.Pick> działanie.</span><span class="sxs-lookup"><span data-stu-id="7cb23-113"><xref:System.Activities.Statements.Pick> activity.</span></span>

## <a name="discussion"></a><span data-ttu-id="7cb23-114">Dyskusja</span><span class="sxs-lookup"><span data-stu-id="7cb23-114">Discussion</span></span>
 <span data-ttu-id="7cb23-115">Przykład obejmuje projektanta przepływu pracy i kodowany przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="7cb23-115">The sample includes a Designer workflow and coded workflow.</span></span>

 <span data-ttu-id="7cb23-116">Projektanta Workflow Designer wersję przykładu przedstawia sposób tworzenia przepływu pracy w projektancie.</span><span class="sxs-lookup"><span data-stu-id="7cb23-116">Designer Workflow The Designer version of the sample demonstrates how to create a workflow in the designer.</span></span> <span data-ttu-id="7cb23-117">Uwzględnione są następujące pliki:</span><span class="sxs-lookup"><span data-stu-id="7cb23-117">The following files are included:</span></span>

-   <span data-ttu-id="7cb23-118">Program.cs : Obejmuje `Main` funkcja, która wykonuje przykładowy przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="7cb23-118">Program.cs : Includes the `Main` function that executes the sample workflow.</span></span>

-   <span data-ttu-id="7cb23-119">ReadString.cs: Niestandardowe działanie, które odczytuje dane wejściowe z konsoli.</span><span class="sxs-lookup"><span data-stu-id="7cb23-119">ReadString.cs: A custom activity that reads some input from the console.</span></span>

-   <span data-ttu-id="7cb23-120">Sequence1.XAML: Przepływ pracy utworzony za pomocą projektanta, który używa wybierz.</span><span class="sxs-lookup"><span data-stu-id="7cb23-120">Sequence1.xaml: A workflow created using the designer that uses Pick.</span></span>

 <span data-ttu-id="7cb23-121">Kodowane przepływu pracy kodowane wersję przykładu przedstawia sposób tworzenia przepływu pracy w projektancie.</span><span class="sxs-lookup"><span data-stu-id="7cb23-121">Coded Workflow The coded version of the sample demonstrates how to create a workflow in the designer.</span></span> <span data-ttu-id="7cb23-122">Uwzględnione są następujące pliki:</span><span class="sxs-lookup"><span data-stu-id="7cb23-122">The following files are included:</span></span>

-   <span data-ttu-id="7cb23-123">Program.cs : Obejmuje `Main` funkcja, która wykonuje przykładowy przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="7cb23-123">Program.cs : Includes the `Main` function that executes the sample workflow.</span></span>

-   <span data-ttu-id="7cb23-124">ReadString.cs: Niestandardowe działanie, które odczytuje dane wejściowe z konsoli.</span><span class="sxs-lookup"><span data-stu-id="7cb23-124">ReadString.cs: A custom activity that reads some input from the console.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="7cb23-125">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="7cb23-125">To use this sample</span></span>

1. <span data-ttu-id="7cb23-126">Za pomocą programu Visual Studio 2010, otwórz plik rozwiązania Pick.sln.</span><span class="sxs-lookup"><span data-stu-id="7cb23-126">Using Visual Studio 2010, open the Pick.sln solution file.</span></span>

2. <span data-ttu-id="7cb23-127">Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="7cb23-127">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="7cb23-128">Aby uruchomić rozwiązanie, naciśnij klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="7cb23-128">To run the solution, press F5.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="7cb23-129">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="7cb23-129">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7cb23-130">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="7cb23-130">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7cb23-131">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="7cb23-131">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7cb23-132">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="7cb23-132">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Pick`