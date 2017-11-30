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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 35bff923b0e8d6fe7c01cb7970c7b6ee46488a43
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2017
---
# <a name="rangeenumeration-activity"></a><span data-ttu-id="877f2-102">Działanie RangeEnumeration</span><span class="sxs-lookup"><span data-stu-id="877f2-102">RangeEnumeration Activity</span></span>
<span data-ttu-id="877f2-103">Ten przykład przedstawia sposób tworzenia działań niestandardowych, który przechodzi przez kolekcję liczb. W poniższej tabeli przedstawiono główne pliki uwzględnione w próbce.</span><span class="sxs-lookup"><span data-stu-id="877f2-103">This sample demonstrates how to create a custom activity that iterates over a collection of numbers.The following table details the main files included in the sample.</span></span>  
  
|<span data-ttu-id="877f2-104">Nazwa pliku</span><span class="sxs-lookup"><span data-stu-id="877f2-104">File name</span></span>|<span data-ttu-id="877f2-105">Opis</span><span class="sxs-lookup"><span data-stu-id="877f2-105">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="877f2-106">RangeEnumeration.cs</span><span class="sxs-lookup"><span data-stu-id="877f2-106">RangeEnumeration.cs</span></span>|<span data-ttu-id="877f2-107">Definiuje niestandardowe działanie o nazwie `RangeEnumeration` który zastępuje <xref:System.Activities.NativeActivity> klasy i pętlę seria liczb.</span><span class="sxs-lookup"><span data-stu-id="877f2-107">Defines a custom activity named `RangeEnumeration` that overrides the <xref:System.Activities.NativeActivity> class and loops through a series of numbers.</span></span>|  
|<span data-ttu-id="877f2-108">RangeEnumerationSample.cs</span><span class="sxs-lookup"><span data-stu-id="877f2-108">RangeEnumerationSample.cs</span></span>|<span data-ttu-id="877f2-109">Aplikacji klienckiej, która używa `RangeEnumeration` działanie Iterowanie przez kolekcję liczb.</span><span class="sxs-lookup"><span data-stu-id="877f2-109">A client application that uses the `RangeEnumeration` activity to iterate over a collection of numbers.</span></span>|  
  
 <span data-ttu-id="877f2-110">W poniższej tabeli przedstawiono właściwości `RangeEnumeration` działania.</span><span class="sxs-lookup"><span data-stu-id="877f2-110">The following table details the properties of the `RangeEnumeration` activity.</span></span>  
  
|<span data-ttu-id="877f2-111">Właściwość</span><span class="sxs-lookup"><span data-stu-id="877f2-111">Property</span></span>|<span data-ttu-id="877f2-112">Opis</span><span class="sxs-lookup"><span data-stu-id="877f2-112">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="877f2-113">Uruchamianie</span><span class="sxs-lookup"><span data-stu-id="877f2-113">Start</span></span>|<span data-ttu-id="877f2-114">Liczba całkowita, można uruchomić z pętli.</span><span class="sxs-lookup"><span data-stu-id="877f2-114">The integer to start the loop from.</span></span>|  
|<span data-ttu-id="877f2-115">Zatrzymywanie</span><span class="sxs-lookup"><span data-stu-id="877f2-115">Stop</span></span>|<span data-ttu-id="877f2-116">Liczba całkowita, można zatrzymać w pętli.</span><span class="sxs-lookup"><span data-stu-id="877f2-116">The integer to stop the loop at.</span></span>|  
|<span data-ttu-id="877f2-117">Krok</span><span class="sxs-lookup"><span data-stu-id="877f2-117">Step</span></span>|<span data-ttu-id="877f2-118">Określa, ile dotyczące iteracji po każdym.</span><span class="sxs-lookup"><span data-stu-id="877f2-118">Specifies how much to iterate each time.</span></span>|  
|<span data-ttu-id="877f2-119">Treści</span><span class="sxs-lookup"><span data-stu-id="877f2-119">Body</span></span>|<span data-ttu-id="877f2-120">Określa kod do wykonania podczas każdej iteracji.</span><span class="sxs-lookup"><span data-stu-id="877f2-120">Specifies the code to execute during each iteration.</span></span>|  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="877f2-121">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="877f2-121">To use this sample</span></span>  
  
1.  <span data-ttu-id="877f2-122">Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania RangeEnumeration.sln.</span><span class="sxs-lookup"><span data-stu-id="877f2-122">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the RangeEnumeration.sln solution file.</span></span>  
  
2.  <span data-ttu-id="877f2-123">Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="877f2-123">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="877f2-124">Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="877f2-124">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="877f2-125">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="877f2-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="877f2-126">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="877f2-126">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="877f2-127">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="877f2-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="877f2-128">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="877f2-128">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\RangeEnumeration`