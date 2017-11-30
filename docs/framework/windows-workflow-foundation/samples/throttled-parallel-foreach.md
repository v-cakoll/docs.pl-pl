---
title: "Ograniczeniem przepustowości ForEach równoległych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2855b5f-e9a7-433d-96a4-40fc31025215
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7155c4f33cb29c5778e59124dd924005e4ef52f6
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2017
---
# <a name="throttled-parallel-foreach"></a><span data-ttu-id="48474-102">Ograniczeniem przepustowości ForEach równoległych</span><span class="sxs-lookup"><span data-stu-id="48474-102">Throttled Parallel ForEach</span></span>
<span data-ttu-id="48474-103">`ThrottleParallelForEach` Działanie przypomina <!--zz <xref:System.Activities.Statements.ParallelForEach>--> `System.Activities.Statements.ParallelForEach` działania z jednym wyjątkiem jego umożliwia ustawienie współczynnika współbieżności do ograniczenia liczby równoczesnych gałęzi do wykonania.</span><span class="sxs-lookup"><span data-stu-id="48474-103">The `ThrottleParallelForEach` activity is similar to the <!--zz <xref:System.Activities.Statements.ParallelForEach>--> `System.Activities.Statements.ParallelForEach` activity with the one exception that it allows setting a concurrency factor to restrict the number of simultaneous branches to execute.</span></span> <span data-ttu-id="48474-104">`ThrottleParallelForEach` Działania jest pochodną <xref:System.Activities.NativeActivity>, ponieważ należy ją zaplanować inne działania (działań podrzędnych) i ten jest dostępny tylko za pośrednictwem <xref:System.Activities.NativeActivityContext> klasy.</span><span class="sxs-lookup"><span data-stu-id="48474-104">The `ThrottleParallelForEach` activity derives from <xref:System.Activities.NativeActivity>, because it needs to schedule other activities (the child activities) and this is only accessible through the <xref:System.Activities.NativeActivityContext> class.</span></span>  
  
## <a name="projects"></a><span data-ttu-id="48474-105">Projekty</span><span class="sxs-lookup"><span data-stu-id="48474-105">Projects</span></span>  
  
|<span data-ttu-id="48474-106">**ProjectName**</span><span class="sxs-lookup"><span data-stu-id="48474-106">**ProjectName**</span></span>|<span data-ttu-id="48474-107">**Opis**</span><span class="sxs-lookup"><span data-stu-id="48474-107">**Description**</span></span>|<span data-ttu-id="48474-108">**Główne pliki**</span><span class="sxs-lookup"><span data-stu-id="48474-108">**Main Files**</span></span>|  
|-|-|-|  
|<span data-ttu-id="48474-109">ThrottledParallelForEach</span><span class="sxs-lookup"><span data-stu-id="48474-109">ThrottledParallelForEach</span></span>|<span data-ttu-id="48474-110">Zawiera `ThrottledParallelForEach` działanie i jego projektanta.</span><span class="sxs-lookup"><span data-stu-id="48474-110">Contains `ThrottledParallelForEach` activity and its designer.</span></span>|<span data-ttu-id="48474-111">ThrottledParallelForEach.cs</span><span class="sxs-lookup"><span data-stu-id="48474-111">ThrottledParallelForEach.cs</span></span><br /><br /> <span data-ttu-id="48474-112">`ThrottledParallelForEach` Definicji działania.</span><span class="sxs-lookup"><span data-stu-id="48474-112">The `ThrottledParallelForEach` activity definition.</span></span>|  
|<span data-ttu-id="48474-113">CodeTestClient</span><span class="sxs-lookup"><span data-stu-id="48474-113">CodeTestClient</span></span>|<span data-ttu-id="48474-114">Przykładowa aplikacja klienta, który konfiguruje i uruchamia przepływ pracy o `ThrottledParallelForEach` przy użyciu kodu nadrzędnych.</span><span class="sxs-lookup"><span data-stu-id="48474-114">Sample client application that configures and runs a workflow with a `ThrottledParallelForEach` using imperative code.</span></span>|<span data-ttu-id="48474-115">Plik program.CS</span><span class="sxs-lookup"><span data-stu-id="48474-115">Program.cs</span></span><br /><br /> <span data-ttu-id="48474-116">Definiuje i uruchomione jest wystąpienie przykładowy przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="48474-116">Defines and runs an instance of the sample workflow.</span></span>|  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="48474-117">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="48474-117">To use this sample</span></span>  
  
1.  <span data-ttu-id="48474-118">Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik ThrottledParallelForEach.sln.</span><span class="sxs-lookup"><span data-stu-id="48474-118">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the ThrottledParallelForEach.sln file.</span></span>  
  
2.  <span data-ttu-id="48474-119">Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="48474-119">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="48474-120">Aby uruchomić rozwiązanie, naciśnij klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="48474-120">To run the solution, press F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="48474-121">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="48474-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="48474-122">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="48474-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="48474-123">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="48474-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="48474-124">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="48474-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\ThrottledParallelForEach`