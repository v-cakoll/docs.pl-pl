---
title: Działanie RangeEnumeration
ms.date: 03/30/2017
ms.assetid: ca5b78f4-94fa-4aa7-830d-26039ac422c8
ms.openlocfilehash: c9cf522227620422b414adc26cbc0bf338bf57d4
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43556295"
---
# <a name="rangeenumeration-activity"></a><span data-ttu-id="0a266-102">Działanie RangeEnumeration</span><span class="sxs-lookup"><span data-stu-id="0a266-102">RangeEnumeration Activity</span></span>
<span data-ttu-id="0a266-103">W tym przykładzie pokazano, jak utworzyć niestandardowe działanie, który iteruje po kolekcji liczb. W poniższej tabeli przedstawiono główne pliki zawarte w przykładzie.</span><span class="sxs-lookup"><span data-stu-id="0a266-103">This sample demonstrates how to create a custom activity that iterates over a collection of numbers.The following table details the main files included in the sample.</span></span>  
  
|<span data-ttu-id="0a266-104">Nazwa pliku</span><span class="sxs-lookup"><span data-stu-id="0a266-104">File name</span></span>|<span data-ttu-id="0a266-105">Opis</span><span class="sxs-lookup"><span data-stu-id="0a266-105">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0a266-106">RangeEnumeration.cs</span><span class="sxs-lookup"><span data-stu-id="0a266-106">RangeEnumeration.cs</span></span>|<span data-ttu-id="0a266-107">Definiuje niestandardowe działanie o nazwie `RangeEnumeration` , zastępuje <xref:System.Activities.NativeActivity> klasy i pętle w kolejnych seriach liczb.</span><span class="sxs-lookup"><span data-stu-id="0a266-107">Defines a custom activity named `RangeEnumeration` that overrides the <xref:System.Activities.NativeActivity> class and loops through a series of numbers.</span></span>|  
|<span data-ttu-id="0a266-108">RangeEnumerationSample.cs</span><span class="sxs-lookup"><span data-stu-id="0a266-108">RangeEnumerationSample.cs</span></span>|<span data-ttu-id="0a266-109">Aplikacja kliencka, która używa `RangeEnumeration` działania do iteracji przez kolekcję liczb.</span><span class="sxs-lookup"><span data-stu-id="0a266-109">A client application that uses the `RangeEnumeration` activity to iterate over a collection of numbers.</span></span>|  
  
 <span data-ttu-id="0a266-110">W poniższej tabeli przedstawiono właściwości `RangeEnumeration` działania.</span><span class="sxs-lookup"><span data-stu-id="0a266-110">The following table details the properties of the `RangeEnumeration` activity.</span></span>  
  
|<span data-ttu-id="0a266-111">Właściwość</span><span class="sxs-lookup"><span data-stu-id="0a266-111">Property</span></span>|<span data-ttu-id="0a266-112">Opis</span><span class="sxs-lookup"><span data-stu-id="0a266-112">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="0a266-113">Uruchamianie</span><span class="sxs-lookup"><span data-stu-id="0a266-113">Start</span></span>|<span data-ttu-id="0a266-114">Liczba całkowita, aby rozpocząć pętli z.</span><span class="sxs-lookup"><span data-stu-id="0a266-114">The integer to start the loop from.</span></span>|  
|<span data-ttu-id="0a266-115">Zatrzymywanie</span><span class="sxs-lookup"><span data-stu-id="0a266-115">Stop</span></span>|<span data-ttu-id="0a266-116">Liczba całkowita, aby zatrzymać pętlę w.</span><span class="sxs-lookup"><span data-stu-id="0a266-116">The integer to stop the loop at.</span></span>|  
|<span data-ttu-id="0a266-117">Krok</span><span class="sxs-lookup"><span data-stu-id="0a266-117">Step</span></span>|<span data-ttu-id="0a266-118">Określa, ile iteracyjne każdorazowo.</span><span class="sxs-lookup"><span data-stu-id="0a266-118">Specifies how much to iterate each time.</span></span>|  
|<span data-ttu-id="0a266-119">Treść</span><span class="sxs-lookup"><span data-stu-id="0a266-119">Body</span></span>|<span data-ttu-id="0a266-120">Określa kod, do wykonania podczas każdej iteracji.</span><span class="sxs-lookup"><span data-stu-id="0a266-120">Specifies the code to execute during each iteration.</span></span>|  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="0a266-121">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="0a266-121">To use this sample</span></span>  
  
1.  <span data-ttu-id="0a266-122">Za pomocą [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania RangeEnumeration.sln.</span><span class="sxs-lookup"><span data-stu-id="0a266-122">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the RangeEnumeration.sln solution file.</span></span>  
  
2.  <span data-ttu-id="0a266-123">Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="0a266-123">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="0a266-124">Aby uruchomić rozwiązanie, naciśnij kombinację klawiszy CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="0a266-124">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0a266-125">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="0a266-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0a266-126">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="0a266-126">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="0a266-127">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="0a266-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0a266-128">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="0a266-128">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\RangeEnumeration`