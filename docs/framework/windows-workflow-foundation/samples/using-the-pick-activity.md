---
title: Używanie działania Pick
ms.date: 03/30/2017
ms.assetid: b89be812-a247-4025-b0e3-ffb20db027a6
ms.openlocfilehash: 03b9ff7f552ad0cdcfbe9c46121a2f46f35de52a
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70037881"
---
# <a name="using-the-pick-activity"></a><span data-ttu-id="0f8ee-102">Używanie działania Pick</span><span class="sxs-lookup"><span data-stu-id="0f8ee-102">Using the Pick Activity</span></span>
<span data-ttu-id="0f8ee-103">Ten przykład pokazuje, <xref:System.Activities.Statements.Pick> jak używać działania.</span><span class="sxs-lookup"><span data-stu-id="0f8ee-103">This sample demonstrates how to use the <xref:System.Activities.Statements.Pick> activity.</span></span>

 <span data-ttu-id="0f8ee-104"><xref:System.Activities.Statements.Pick> Działanie zapewnia modelowania kontroli opartej na zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="0f8ee-104">The <xref:System.Activities.Statements.Pick> activity provides event-based control modeling.</span></span> <span data-ttu-id="0f8ee-105">Zachowuje się podobnie do C# `switch` instrukcji, która wykonuje tylko jedną z gałęzi w `switch` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="0f8ee-105">It behaves similar to the C# `switch` statement, which executes only one of the branches in the `switch` statement.</span></span> <span data-ttu-id="0f8ee-106">W przeciwieństwie `switch` do instrukcji <xref:System.Activities.Statements.Pick> , w której rozgałęzienie jest wykonywane na podstawie wartości, działanie wykonuje gałąź w oparciu o zakończenie działania.</span><span class="sxs-lookup"><span data-stu-id="0f8ee-106">Unlike the `switch` statement in which a branch is executed based upon on a value, the <xref:System.Activities.Statements.Pick> activity executes a branch based upon how an activity completes.</span></span>

 <span data-ttu-id="0f8ee-107">Ten przykład poprosi użytkownika o wpisanie nazwy w konsoli w danym okresie czasu.</span><span class="sxs-lookup"><span data-stu-id="0f8ee-107">This sample prompts a user to type in their name on the console within a given time period.</span></span> <span data-ttu-id="0f8ee-108"><xref:System.Activities.Statements.Pick> Działanie w przykładzie ma dwie gałęzie, które są wykonywane w zależności od tego, czy użytkownik wpisze swoją nazwę w ciągu 5 sekund.</span><span class="sxs-lookup"><span data-stu-id="0f8ee-108">The <xref:System.Activities.Statements.Pick> activity in the sample has two branches that are executed based upon whether the user types in their name within 5 seconds or not.</span></span> <span data-ttu-id="0f8ee-109">Jeśli użytkownik wpisze swoją nazwę w ciągu 5 sekund, wykonywana jest pierwsza gałąź, która zawiera działanie niestandardowe `ReadLine` ; w przeciwnym razie inna gałąź jest wykonywana, która <xref:System.Activities.Statements.Delay> zawiera działanie.</span><span class="sxs-lookup"><span data-stu-id="0f8ee-109">If the user types in their name within 5 seconds, the first branch is executed, which contains a custom `ReadLine` activity; otherwise the other branch is executed, which contains a <xref:System.Activities.Statements.Delay> activity.</span></span> <span data-ttu-id="0f8ee-110">Po wpisaniu nazwy użytkownika w konsoli programu nazwa użytkownika jest drukowana w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="0f8ee-110">Once a user’s name is typed in on the console, the user’s name is printed on the console.</span></span> <span data-ttu-id="0f8ee-111">Jeśli dane wejściowe nie zostaną wprowadzone w ciągu 5 sekund, Operacja przekroczyła limit czasu.</span><span class="sxs-lookup"><span data-stu-id="0f8ee-111">If an input is not entered within 5 seconds, the operation is timed out.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="0f8ee-112">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="0f8ee-112">Demonstrates</span></span>
 <span data-ttu-id="0f8ee-113"><xref:System.Activities.Statements.Pick>interakcyjn.</span><span class="sxs-lookup"><span data-stu-id="0f8ee-113"><xref:System.Activities.Statements.Pick> activity.</span></span>

## <a name="discussion"></a><span data-ttu-id="0f8ee-114">Dyskusji</span><span class="sxs-lookup"><span data-stu-id="0f8ee-114">Discussion</span></span>
 <span data-ttu-id="0f8ee-115">Przykład zawiera przepływ pracy projektanta i kodowany przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="0f8ee-115">The sample includes a Designer workflow and coded workflow.</span></span>

 <span data-ttu-id="0f8ee-116">Przepływ pracy projektanta wersja projektanta przykład pokazuje, jak utworzyć przepływ pracy w projektancie.</span><span class="sxs-lookup"><span data-stu-id="0f8ee-116">Designer Workflow The Designer version of the sample demonstrates how to create a workflow in the designer.</span></span> <span data-ttu-id="0f8ee-117">Dostępne są następujące pliki:</span><span class="sxs-lookup"><span data-stu-id="0f8ee-117">The following files are included:</span></span>

- <span data-ttu-id="0f8ee-118">Program.cs: `Main` Zawiera funkcję, która wykonuje przykładowy przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="0f8ee-118">Program.cs : Includes the `Main` function that executes the sample workflow.</span></span>

- <span data-ttu-id="0f8ee-119">ReadString.cs: Niestandardowe działanie, które odczytuje niektóre dane wejściowe z konsoli.</span><span class="sxs-lookup"><span data-stu-id="0f8ee-119">ReadString.cs: A custom activity that reads some input from the console.</span></span>

- <span data-ttu-id="0f8ee-120">Sequence1. XAML: Przepływ pracy utworzony przy użyciu projektanta, który używa funkcji pobrania.</span><span class="sxs-lookup"><span data-stu-id="0f8ee-120">Sequence1.xaml: A workflow created using the designer that uses Pick.</span></span>

 <span data-ttu-id="0f8ee-121">Kodowany przepływ pracy zakodowana wersja przykładu pokazuje, jak utworzyć przepływ pracy w projektancie.</span><span class="sxs-lookup"><span data-stu-id="0f8ee-121">Coded Workflow The coded version of the sample demonstrates how to create a workflow in the designer.</span></span> <span data-ttu-id="0f8ee-122">Dostępne są następujące pliki:</span><span class="sxs-lookup"><span data-stu-id="0f8ee-122">The following files are included:</span></span>

- <span data-ttu-id="0f8ee-123">Program.cs: `Main` Zawiera funkcję, która wykonuje przykładowy przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="0f8ee-123">Program.cs : Includes the `Main` function that executes the sample workflow.</span></span>

- <span data-ttu-id="0f8ee-124">ReadString.cs: Niestandardowe działanie, które odczytuje niektóre dane wejściowe z konsoli.</span><span class="sxs-lookup"><span data-stu-id="0f8ee-124">ReadString.cs: A custom activity that reads some input from the console.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="0f8ee-125">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="0f8ee-125">To use this sample</span></span>

1. <span data-ttu-id="0f8ee-126">Za pomocą programu Visual Studio 2010 Otwórz plik rozwiązania do pobrania. sln.</span><span class="sxs-lookup"><span data-stu-id="0f8ee-126">Using Visual Studio 2010, open the Pick.sln solution file.</span></span>

2. <span data-ttu-id="0f8ee-127">Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="0f8ee-127">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="0f8ee-128">Aby uruchomić rozwiązanie, naciśnij klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="0f8ee-128">To run the solution, press F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0f8ee-129">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="0f8ee-129">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0f8ee-130">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="0f8ee-130">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="0f8ee-131">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="0f8ee-131">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0f8ee-132">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="0f8ee-132">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Pick`
