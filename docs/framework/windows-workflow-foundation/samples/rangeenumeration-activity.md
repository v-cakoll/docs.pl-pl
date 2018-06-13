---
title: Działanie RangeEnumeration
ms.date: 03/30/2017
ms.assetid: ca5b78f4-94fa-4aa7-830d-26039ac422c8
ms.openlocfilehash: 9aa04c80f20e2d410fb49e2d07d836c8c5ab1b4d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516581"
---
# <a name="rangeenumeration-activity"></a><span data-ttu-id="63894-102">Działanie RangeEnumeration</span><span class="sxs-lookup"><span data-stu-id="63894-102">RangeEnumeration Activity</span></span>
<span data-ttu-id="63894-103">Ten przykład przedstawia sposób tworzenia działań niestandardowych, który przechodzi przez kolekcję liczb. W poniższej tabeli przedstawiono główne pliki uwzględnione w próbce.</span><span class="sxs-lookup"><span data-stu-id="63894-103">This sample demonstrates how to create a custom activity that iterates over a collection of numbers.The following table details the main files included in the sample.</span></span>  
  
|<span data-ttu-id="63894-104">Nazwa pliku</span><span class="sxs-lookup"><span data-stu-id="63894-104">File name</span></span>|<span data-ttu-id="63894-105">Opis</span><span class="sxs-lookup"><span data-stu-id="63894-105">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="63894-106">RangeEnumeration.cs</span><span class="sxs-lookup"><span data-stu-id="63894-106">RangeEnumeration.cs</span></span>|<span data-ttu-id="63894-107">Definiuje niestandardowe działanie o nazwie `RangeEnumeration` który zastępuje <xref:System.Activities.NativeActivity> klasy i pętlę seria liczb.</span><span class="sxs-lookup"><span data-stu-id="63894-107">Defines a custom activity named `RangeEnumeration` that overrides the <xref:System.Activities.NativeActivity> class and loops through a series of numbers.</span></span>|  
|<span data-ttu-id="63894-108">RangeEnumerationSample.cs</span><span class="sxs-lookup"><span data-stu-id="63894-108">RangeEnumerationSample.cs</span></span>|<span data-ttu-id="63894-109">Aplikacji klienckiej, która używa `RangeEnumeration` działanie Iterowanie przez kolekcję liczb.</span><span class="sxs-lookup"><span data-stu-id="63894-109">A client application that uses the `RangeEnumeration` activity to iterate over a collection of numbers.</span></span>|  
  
 <span data-ttu-id="63894-110">W poniższej tabeli przedstawiono właściwości `RangeEnumeration` działania.</span><span class="sxs-lookup"><span data-stu-id="63894-110">The following table details the properties of the `RangeEnumeration` activity.</span></span>  
  
|<span data-ttu-id="63894-111">Właściwość</span><span class="sxs-lookup"><span data-stu-id="63894-111">Property</span></span>|<span data-ttu-id="63894-112">Opis</span><span class="sxs-lookup"><span data-stu-id="63894-112">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="63894-113">Uruchamianie</span><span class="sxs-lookup"><span data-stu-id="63894-113">Start</span></span>|<span data-ttu-id="63894-114">Liczba całkowita, można uruchomić z pętli.</span><span class="sxs-lookup"><span data-stu-id="63894-114">The integer to start the loop from.</span></span>|  
|<span data-ttu-id="63894-115">Zatrzymywanie</span><span class="sxs-lookup"><span data-stu-id="63894-115">Stop</span></span>|<span data-ttu-id="63894-116">Liczba całkowita, można zatrzymać w pętli.</span><span class="sxs-lookup"><span data-stu-id="63894-116">The integer to stop the loop at.</span></span>|  
|<span data-ttu-id="63894-117">Krok</span><span class="sxs-lookup"><span data-stu-id="63894-117">Step</span></span>|<span data-ttu-id="63894-118">Określa, ile dotyczące iteracji po każdym.</span><span class="sxs-lookup"><span data-stu-id="63894-118">Specifies how much to iterate each time.</span></span>|  
|<span data-ttu-id="63894-119">Treści</span><span class="sxs-lookup"><span data-stu-id="63894-119">Body</span></span>|<span data-ttu-id="63894-120">Określa kod do wykonania podczas każdej iteracji.</span><span class="sxs-lookup"><span data-stu-id="63894-120">Specifies the code to execute during each iteration.</span></span>|  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="63894-121">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="63894-121">To use this sample</span></span>  
  
1.  <span data-ttu-id="63894-122">Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania RangeEnumeration.sln.</span><span class="sxs-lookup"><span data-stu-id="63894-122">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the RangeEnumeration.sln solution file.</span></span>  
  
2.  <span data-ttu-id="63894-123">Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="63894-123">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="63894-124">Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="63894-124">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="63894-125">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="63894-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="63894-126">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="63894-126">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="63894-127">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="63894-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="63894-128">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="63894-128">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\RangeEnumeration`