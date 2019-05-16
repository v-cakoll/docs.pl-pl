---
title: Działanie ThrottledParallelForEach
ms.date: 03/30/2017
ms.assetid: f2855b5f-e9a7-433d-96a4-40fc31025215
ms.openlocfilehash: 2694173e203fae9b620e9594d6d4a494bdedafef
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65637760"
---
# <a name="throttled-parallel-foreach"></a><span data-ttu-id="aefd3-102">Działanie ThrottledParallelForEach</span><span class="sxs-lookup"><span data-stu-id="aefd3-102">Throttled Parallel ForEach</span></span>

<span data-ttu-id="aefd3-103">`ThrottleParallelForEach` Działanie jest podobne do <xref:System.Activities.Statements.ParallelForEach%601> działania z jednym wyjątkiem że umożliwia ustawienie współczynnika współbieżności Aby ograniczyć liczbę jednoczesnych gałęzi do wykonania.</span><span class="sxs-lookup"><span data-stu-id="aefd3-103">The `ThrottleParallelForEach` activity is similar to the <xref:System.Activities.Statements.ParallelForEach%601> activity with the one exception that it allows setting a concurrency factor to restrict the number of simultaneous branches to execute.</span></span> <span data-ttu-id="aefd3-104">`ThrottleParallelForEach` Pochodzi od klasy działania <xref:System.Activities.NativeActivity>, ponieważ należy ją zaplanować inne działania (działania podrzędne), a ten jest dostępny tylko za pośrednictwem <xref:System.Activities.NativeActivityContext> klasy.</span><span class="sxs-lookup"><span data-stu-id="aefd3-104">The `ThrottleParallelForEach` activity derives from <xref:System.Activities.NativeActivity>, because it needs to schedule other activities (the child activities) and this is only accessible through the <xref:System.Activities.NativeActivityContext> class.</span></span>

## <a name="projects"></a><span data-ttu-id="aefd3-105">Projekty</span><span class="sxs-lookup"><span data-stu-id="aefd3-105">Projects</span></span>

|<span data-ttu-id="aefd3-106">**ProjectName**</span><span class="sxs-lookup"><span data-stu-id="aefd3-106">**ProjectName**</span></span>|<span data-ttu-id="aefd3-107">**Opis**</span><span class="sxs-lookup"><span data-stu-id="aefd3-107">**Description**</span></span>|<span data-ttu-id="aefd3-108">**Pliki główne**</span><span class="sxs-lookup"><span data-stu-id="aefd3-108">**Main Files**</span></span>|
|-|-|-|
|<span data-ttu-id="aefd3-109">ThrottledParallelForEach</span><span class="sxs-lookup"><span data-stu-id="aefd3-109">ThrottledParallelForEach</span></span>|<span data-ttu-id="aefd3-110">Zawiera `ThrottledParallelForEach` działanie i jego projektanta.</span><span class="sxs-lookup"><span data-stu-id="aefd3-110">Contains `ThrottledParallelForEach` activity and its designer.</span></span>|<span data-ttu-id="aefd3-111">ThrottledParallelForEach.cs</span><span class="sxs-lookup"><span data-stu-id="aefd3-111">ThrottledParallelForEach.cs</span></span><br /><br /> <span data-ttu-id="aefd3-112">`ThrottledParallelForEach` Definicji działania.</span><span class="sxs-lookup"><span data-stu-id="aefd3-112">The `ThrottledParallelForEach` activity definition.</span></span>|
|<span data-ttu-id="aefd3-113">CodeTestClient</span><span class="sxs-lookup"><span data-stu-id="aefd3-113">CodeTestClient</span></span>|<span data-ttu-id="aefd3-114">Przykładowa aplikacja kliencka, która umożliwia skonfigurowanie i uruchamia przepływ pracy o `ThrottledParallelForEach` przy użyciu kodu imperatywnego.</span><span class="sxs-lookup"><span data-stu-id="aefd3-114">Sample client application that configures and runs a workflow with a `ThrottledParallelForEach` using imperative code.</span></span>|<span data-ttu-id="aefd3-115">Program.cs</span><span class="sxs-lookup"><span data-stu-id="aefd3-115">Program.cs</span></span><br /><br /> <span data-ttu-id="aefd3-116">Definiuje i jest uruchamiane wystąpienie przykładowy przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="aefd3-116">Defines and runs an instance of the sample workflow.</span></span>|

## <a name="to-use-this-sample"></a><span data-ttu-id="aefd3-117">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="aefd3-117">To use this sample</span></span>

1. <span data-ttu-id="aefd3-118">Za pomocą programu Visual Studio 2010, otwórz plik ThrottledParallelForEach.sln.</span><span class="sxs-lookup"><span data-stu-id="aefd3-118">Using Visual Studio 2010, open the ThrottledParallelForEach.sln file.</span></span>

2. <span data-ttu-id="aefd3-119">Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="aefd3-119">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="aefd3-120">Aby uruchomić rozwiązanie, naciśnij klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="aefd3-120">To run the solution, press F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="aefd3-121">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="aefd3-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="aefd3-122">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="aefd3-122">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="aefd3-123">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="aefd3-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="aefd3-124">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="aefd3-124">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\ThrottledParallelForEach`
