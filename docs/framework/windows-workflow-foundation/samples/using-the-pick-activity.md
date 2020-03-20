---
title: Używanie działania Pick
ms.date: 03/30/2017
ms.assetid: b89be812-a247-4025-b0e3-ffb20db027a6
ms.openlocfilehash: 7ca4527cc1d5bc90ed1ec4df3eef6cf2d8b93b4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142618"
---
# <a name="using-the-pick-activity"></a><span data-ttu-id="31f37-102">Używanie działania Pick</span><span class="sxs-lookup"><span data-stu-id="31f37-102">Using the Pick Activity</span></span>
<span data-ttu-id="31f37-103">W tym przykładzie pokazano, jak używać <xref:System.Activities.Statements.Pick> działania.</span><span class="sxs-lookup"><span data-stu-id="31f37-103">This sample demonstrates how to use the <xref:System.Activities.Statements.Pick> activity.</span></span>

 <span data-ttu-id="31f37-104">Działanie <xref:System.Activities.Statements.Pick> zapewnia modelowanie kontroli oparte na zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="31f37-104">The <xref:System.Activities.Statements.Pick> activity provides event-based control modeling.</span></span> <span data-ttu-id="31f37-105">Zachowuje się podobnie do `switch` instrukcji C#, która wykonuje tylko jedną `switch` z gałęzi w instrukcji.</span><span class="sxs-lookup"><span data-stu-id="31f37-105">It behaves similar to the C# `switch` statement, which executes only one of the branches in the `switch` statement.</span></span> <span data-ttu-id="31f37-106">W `switch` przeciwieństwie do instrukcji, w której gałąź jest wykonywana na podstawie wartości, <xref:System.Activities.Statements.Pick> działanie wykonuje gałąź na podstawie sposobu zakończenia działania.</span><span class="sxs-lookup"><span data-stu-id="31f37-106">Unlike the `switch` statement in which a branch is executed based upon on a value, the <xref:System.Activities.Statements.Pick> activity executes a branch based upon how an activity completes.</span></span>

 <span data-ttu-id="31f37-107">Ten przykład monituje użytkownika o wpisanie jego nazwy na konsoli w danym okresie czasu.</span><span class="sxs-lookup"><span data-stu-id="31f37-107">This sample prompts a user to type in their name on the console within a given time period.</span></span> <span data-ttu-id="31f37-108">Działanie <xref:System.Activities.Statements.Pick> w próbce ma dwie gałęzie, które są wykonywane na podstawie tego, czy użytkownik typów w ich nazwie w ciągu 5 sekund, czy nie.</span><span class="sxs-lookup"><span data-stu-id="31f37-108">The <xref:System.Activities.Statements.Pick> activity in the sample has two branches that are executed based upon whether the user types in their name within 5 seconds or not.</span></span> <span data-ttu-id="31f37-109">Jeśli użytkownik wpisuje w ich nazwie w ciągu 5 sekund, `ReadLine` pierwsza gałąź jest wykonywana, która zawiera działanie niestandardowe; w przeciwnym razie wykonywana jest <xref:System.Activities.Statements.Delay> inna gałąź, która zawiera działanie.</span><span class="sxs-lookup"><span data-stu-id="31f37-109">If the user types in their name within 5 seconds, the first branch is executed, which contains a custom `ReadLine` activity; otherwise the other branch is executed, which contains a <xref:System.Activities.Statements.Delay> activity.</span></span> <span data-ttu-id="31f37-110">Po wpisaniu nazwy użytkownika na konsoli, nazwa użytkownika jest drukowana na konsoli.</span><span class="sxs-lookup"><span data-stu-id="31f37-110">Once a user’s name is typed in on the console, the user’s name is printed on the console.</span></span> <span data-ttu-id="31f37-111">Jeśli dane wejściowe nie zostanie wprowadzone w ciągu 5 sekund, upłynie limit czasu operacji.</span><span class="sxs-lookup"><span data-stu-id="31f37-111">If an input is not entered within 5 seconds, the operation is timed out.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="31f37-112">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="31f37-112">Demonstrates</span></span>
 <span data-ttu-id="31f37-113"><xref:System.Activities.Statements.Pick>Działania.</span><span class="sxs-lookup"><span data-stu-id="31f37-113"><xref:System.Activities.Statements.Pick> activity.</span></span>

## <a name="discussion"></a><span data-ttu-id="31f37-114">Dyskusji</span><span class="sxs-lookup"><span data-stu-id="31f37-114">Discussion</span></span>
 <span data-ttu-id="31f37-115">Przykład zawiera przepływ pracy projektanta i kodowany przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="31f37-115">The sample includes a Designer workflow and coded workflow.</span></span>

 <span data-ttu-id="31f37-116">Projekt projektanta Przepływ pracy Wersja projektanta przykładu pokazuje, jak utworzyć przepływ pracy w projektancie.</span><span class="sxs-lookup"><span data-stu-id="31f37-116">Designer Workflow The Designer version of the sample demonstrates how to create a workflow in the designer.</span></span> <span data-ttu-id="31f37-117">Następujące pliki są zawarte:</span><span class="sxs-lookup"><span data-stu-id="31f37-117">The following files are included:</span></span>

- <span data-ttu-id="31f37-118">Program.cs : Zawiera `Main` funkcję, która wykonuje przykładowy przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="31f37-118">Program.cs : Includes the `Main` function that executes the sample workflow.</span></span>

- <span data-ttu-id="31f37-119">ReadString.cs: działanie niestandardowe, które odczytuje niektóre dane wejściowe z konsoli.</span><span class="sxs-lookup"><span data-stu-id="31f37-119">ReadString.cs: A custom activity that reads some input from the console.</span></span>

- <span data-ttu-id="31f37-120">Sequence1.xaml: Przepływ pracy utworzony przy użyciu projektanta, który używa pobrania.</span><span class="sxs-lookup"><span data-stu-id="31f37-120">Sequence1.xaml: A workflow created using the designer that uses Pick.</span></span>

 <span data-ttu-id="31f37-121">Kodowany przepływ pracy Zakodowana wersja przykładu pokazuje, jak utworzyć przepływ pracy w projektancie.</span><span class="sxs-lookup"><span data-stu-id="31f37-121">Coded Workflow The coded version of the sample demonstrates how to create a workflow in the designer.</span></span> <span data-ttu-id="31f37-122">Następujące pliki są zawarte:</span><span class="sxs-lookup"><span data-stu-id="31f37-122">The following files are included:</span></span>

- <span data-ttu-id="31f37-123">Program.cs : Zawiera `Main` funkcję, która wykonuje przykładowy przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="31f37-123">Program.cs : Includes the `Main` function that executes the sample workflow.</span></span>

- <span data-ttu-id="31f37-124">ReadString.cs: działanie niestandardowe, które odczytuje niektóre dane wejściowe z konsoli.</span><span class="sxs-lookup"><span data-stu-id="31f37-124">ReadString.cs: A custom activity that reads some input from the console.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="31f37-125">Aby użyć tej próbki</span><span class="sxs-lookup"><span data-stu-id="31f37-125">To use this sample</span></span>

1. <span data-ttu-id="31f37-126">Za pomocą programu Visual Studio 2010 otwórz plik rozwiązania Pick.sln.</span><span class="sxs-lookup"><span data-stu-id="31f37-126">Using Visual Studio 2010, open the Pick.sln solution file.</span></span>

2. <span data-ttu-id="31f37-127">Aby utworzyć rozwiązanie, naciśnij klawisze CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="31f37-127">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="31f37-128">Aby uruchomić rozwiązanie, naciśnij klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="31f37-128">To run the solution, press F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="31f37-129">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="31f37-129">The samples may already be installed on your machine.</span></span> <span data-ttu-id="31f37-130">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="31f37-130">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="31f37-131">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="31f37-131">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="31f37-132">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="31f37-132">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Pick`
