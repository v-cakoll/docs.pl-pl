---
title: "Działanie RangeEnumeration"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ca5b78f4-94fa-4aa7-830d-26039ac422c8
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7dc793d57718dbc68f304d3eb5031a9fa96b00cb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="rangeenumeration-activity"></a><span data-ttu-id="94c12-102">Działanie RangeEnumeration</span><span class="sxs-lookup"><span data-stu-id="94c12-102">RangeEnumeration Activity</span></span>
<span data-ttu-id="94c12-103">Ten przykład przedstawia sposób tworzenia działań niestandardowych, który przechodzi przez kolekcję liczb. W poniższej tabeli przedstawiono główne pliki uwzględnione w próbce.</span><span class="sxs-lookup"><span data-stu-id="94c12-103">This sample demonstrates how to create a custom activity that iterates over a collection of numbers.The following table details the main files included in the sample.</span></span>  
  
|<span data-ttu-id="94c12-104">Nazwa pliku</span><span class="sxs-lookup"><span data-stu-id="94c12-104">File name</span></span>|<span data-ttu-id="94c12-105">Opis</span><span class="sxs-lookup"><span data-stu-id="94c12-105">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="94c12-106">RangeEnumeration.cs</span><span class="sxs-lookup"><span data-stu-id="94c12-106">RangeEnumeration.cs</span></span>|<span data-ttu-id="94c12-107">Definiuje niestandardowe działanie o nazwie `RangeEnumeration` który zastępuje <xref:System.Activities.NativeActivity> klasy i pętlę seria liczb.</span><span class="sxs-lookup"><span data-stu-id="94c12-107">Defines a custom activity named `RangeEnumeration` that overrides the <xref:System.Activities.NativeActivity> class and loops through a series of numbers.</span></span>|  
|<span data-ttu-id="94c12-108">RangeEnumerationSample.cs</span><span class="sxs-lookup"><span data-stu-id="94c12-108">RangeEnumerationSample.cs</span></span>|<span data-ttu-id="94c12-109">Aplikacji klienckiej, która używa `RangeEnumeration` działanie Iterowanie przez kolekcję liczb.</span><span class="sxs-lookup"><span data-stu-id="94c12-109">A client application that uses the `RangeEnumeration` activity to iterate over a collection of numbers.</span></span>|  
  
 <span data-ttu-id="94c12-110">W poniższej tabeli przedstawiono właściwości `RangeEnumeration` działania.</span><span class="sxs-lookup"><span data-stu-id="94c12-110">The following table details the properties of the `RangeEnumeration` activity.</span></span>  
  
|<span data-ttu-id="94c12-111">Właściwość</span><span class="sxs-lookup"><span data-stu-id="94c12-111">Property</span></span>|<span data-ttu-id="94c12-112">Opis</span><span class="sxs-lookup"><span data-stu-id="94c12-112">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="94c12-113">Uruchamianie</span><span class="sxs-lookup"><span data-stu-id="94c12-113">Start</span></span>|<span data-ttu-id="94c12-114">Liczba całkowita, można uruchomić z pętli.</span><span class="sxs-lookup"><span data-stu-id="94c12-114">The integer to start the loop from.</span></span>|  
|<span data-ttu-id="94c12-115">Zatrzymywanie</span><span class="sxs-lookup"><span data-stu-id="94c12-115">Stop</span></span>|<span data-ttu-id="94c12-116">Liczba całkowita, można zatrzymać w pętli.</span><span class="sxs-lookup"><span data-stu-id="94c12-116">The integer to stop the loop at.</span></span>|  
|<span data-ttu-id="94c12-117">Krok</span><span class="sxs-lookup"><span data-stu-id="94c12-117">Step</span></span>|<span data-ttu-id="94c12-118">Określa, ile dotyczące iteracji po każdym.</span><span class="sxs-lookup"><span data-stu-id="94c12-118">Specifies how much to iterate each time.</span></span>|  
|<span data-ttu-id="94c12-119">Treści</span><span class="sxs-lookup"><span data-stu-id="94c12-119">Body</span></span>|<span data-ttu-id="94c12-120">Określa kod do wykonania podczas każdej iteracji.</span><span class="sxs-lookup"><span data-stu-id="94c12-120">Specifies the code to execute during each iteration.</span></span>|  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="94c12-121">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="94c12-121">To use this sample</span></span>  
  
1.  <span data-ttu-id="94c12-122">Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania RangeEnumeration.sln.</span><span class="sxs-lookup"><span data-stu-id="94c12-122">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the RangeEnumeration.sln solution file.</span></span>  
  
2.  <span data-ttu-id="94c12-123">Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="94c12-123">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="94c12-124">Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="94c12-124">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="94c12-125">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="94c12-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="94c12-126">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="94c12-126">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="94c12-127">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="94c12-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="94c12-128">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="94c12-128">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\RangeEnumeration`