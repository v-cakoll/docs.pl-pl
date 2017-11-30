---
title: "Przy użyciu działań kolekcji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e1977cf8-1695-4071-b946-7046fe39601e
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: aa7b3b6815adfba9367585174b242aa7410d578e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="using-collection-activities"></a><span data-ttu-id="4ffd3-102">Przy użyciu działań kolekcji</span><span class="sxs-lookup"><span data-stu-id="4ffd3-102">Using Collection Activities</span></span>
<span data-ttu-id="4ffd3-103">W tym przykładzie przedstawiono sposób użycia działań kolekcji (<xref:System.Activities.Statements.AddToCollection%601>, <xref:System.Activities.Statements.ClearCollection%601>, <xref:System.Activities.Statements.ExistsInCollection%601>, i <xref:System.Activities.Statements.RemoveFromCollection%601>) z klasy, która implementuje <xref:System.Collections.ICollection> interfejs oraz sposobu tworzenia działań niestandardowych, który przechodzi przez kolekcję do wydrukować zawartość każdego elementu w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="4ffd3-103">This sample demonstrates how to use the collection activities (<xref:System.Activities.Statements.AddToCollection%601>, <xref:System.Activities.Statements.ClearCollection%601>, <xref:System.Activities.Statements.ExistsInCollection%601>, and <xref:System.Activities.Statements.RemoveFromCollection%601>) with a class that implements the <xref:System.Collections.ICollection> interface and how to create a custom activity that iterates over a collection to print out the contents of each element in the collection.</span></span> <span data-ttu-id="4ffd3-104">Działania niestandardowe, nosi nazwę `PrintCollection`, drukuje do konsoli elementu członkami kolekcji o nazwie `Numbers`.</span><span class="sxs-lookup"><span data-stu-id="4ffd3-104">The custom activity, which is named `PrintCollection`, prints to the console the item members of a collection named `Numbers`.</span></span>  
  
 <span data-ttu-id="4ffd3-105">W poniższej tabeli opisano cztery działania, które zapewniają manipulowania kolekcji dla przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="4ffd3-105">The following table describes the four activities that provide collection manipulation for workflows.</span></span>  
  
|<span data-ttu-id="4ffd3-106">Nazwa działania</span><span class="sxs-lookup"><span data-stu-id="4ffd3-106">Activity name</span></span>|<span data-ttu-id="4ffd3-107">Opis</span><span class="sxs-lookup"><span data-stu-id="4ffd3-107">Description</span></span>|  
|-------------------|-----------------|  
|<xref:System.Activities.Statements.AddToCollection%601>|<span data-ttu-id="4ffd3-108">Dodaje element do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="4ffd3-108">Adds an item to a collection.</span></span>|  
|<xref:System.Activities.Statements.ClearCollection%601>|<span data-ttu-id="4ffd3-109">Usuwa wszystkie elementy w kolekcji</span><span class="sxs-lookup"><span data-stu-id="4ffd3-109">Clears all items in a collection</span></span>|  
|<xref:System.Activities.Statements.ExistsInCollection%601>|<span data-ttu-id="4ffd3-110">Zwraca `true` Jeśli określony element istnieje w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="4ffd3-110">Returns `true` if specified item exists in collection.</span></span>|  
|<xref:System.Activities.Statements.RemoveFromCollection%601>|<span data-ttu-id="4ffd3-111">Usuwa element z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="4ffd3-111">Removes an item from a collection.</span></span>|  
  
 <span data-ttu-id="4ffd3-112">Próbka składa się z dwóch rozwiązań, co w katalogu CodedWorkflow, a drugą w katalogu DesignerWorkflow.</span><span class="sxs-lookup"><span data-stu-id="4ffd3-112">The sample consists of two solutions, one under the CodedWorkflow directory and the other under the DesignerWorkflow directory.</span></span> <span data-ttu-id="4ffd3-113">Pokazują one dwa różne sposoby używania działań dla tych samych celów.</span><span class="sxs-lookup"><span data-stu-id="4ffd3-113">They demonstrate two different ways of using the activities for the same purposes.</span></span>  
  
|<span data-ttu-id="4ffd3-114">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="4ffd3-114">Solution</span></span>|<span data-ttu-id="4ffd3-115">Opis</span><span class="sxs-lookup"><span data-stu-id="4ffd3-115">Description</span></span>|<span data-ttu-id="4ffd3-116">Główne pliki</span><span class="sxs-lookup"><span data-stu-id="4ffd3-116">Main Files</span></span>|  
|-|-|-|  
|<span data-ttu-id="4ffd3-117">CodedWorkflow</span><span class="sxs-lookup"><span data-stu-id="4ffd3-117">CodedWorkflow</span></span>|<span data-ttu-id="4ffd3-118">Aplikacja kliencka przykładowych pokazano, jak można wywołać działania kolekcji programowo.</span><span class="sxs-lookup"><span data-stu-id="4ffd3-118">Sample client application that demonstrates how to invoke the collection activities programmatically.</span></span>|<span data-ttu-id="4ffd3-119">**PrintCollection.cs**: działanie pomocnika drukowanie do konsoli każdego elementu w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="4ffd3-119">**PrintCollection.cs**: helper activity to print out to the console every item in a collection.</span></span><br /><br /> <span data-ttu-id="4ffd3-120">**Plik program.cs**: programowane kompilacje działania sequence, zawiera szereg działań kolekcji, która go uruchomi.</span><span class="sxs-lookup"><span data-stu-id="4ffd3-120">**Program.cs**: programmatically builds a sequence activity that contains a series of collection activities, and executes it.</span></span>|  
|<span data-ttu-id="4ffd3-121">DesignerWorkflow</span><span class="sxs-lookup"><span data-stu-id="4ffd3-121">DesignerWorkflow</span></span>|<span data-ttu-id="4ffd3-122">Aplikacja kliencka przykładowych pokazano, jak używać działań kolekcji deklaratywnie w Projektancie przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="4ffd3-122">Sample client application that demonstrates how to use the collection activities declaratively in the workflow designer.</span></span>|<span data-ttu-id="4ffd3-123">**CollectionWorkflow.xaml**: deklaratywnie utworzone za pomocą projektanta, który korzysta z kolekcji działań przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="4ffd3-123">**CollectionWorkflow.xaml**: a workflow created declaratively with the designer that uses the collection activities.</span></span><br /><br /> <span data-ttu-id="4ffd3-124">**PrintCollection.cs**: działanie pomocnika drukowanie do konsoli każdego elementu w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="4ffd3-124">**PrintCollection.cs**: helper activity to print out to the console every item in a collection.</span></span><br /><br /> <span data-ttu-id="4ffd3-125">**Plik program.cs**: wywołuje przepływu pracy opisanego w CollectionWorkflow.xaml.</span><span class="sxs-lookup"><span data-stu-id="4ffd3-125">**Program.cs**: invokes the workflow described in CollectionWorkflow.xaml.</span></span>|  
  
 <span data-ttu-id="4ffd3-126">W pokazu elementu członkami kolekcji `Numbers` są drukowane na konsoli przy użyciu niestandardowy działanie o nazwie `PrintCollection`.</span><span class="sxs-lookup"><span data-stu-id="4ffd3-126">In the demonstration, the item members of collection `Numbers` are printed on the console using a custom-defined activity called `PrintCollection`.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="4ffd3-127">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="4ffd3-127">To use this sample</span></span>  
  
1.  <span data-ttu-id="4ffd3-128">Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania Collection.sln.</span><span class="sxs-lookup"><span data-stu-id="4ffd3-128">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the Collection.sln solution file.</span></span>  
  
2.  <span data-ttu-id="4ffd3-129">Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="4ffd3-129">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="4ffd3-130">Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="4ffd3-130">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4ffd3-131">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="4ffd3-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4ffd3-132">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="4ffd3-132">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4ffd3-133">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="4ffd3-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4ffd3-134">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="4ffd3-134">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Collection`  
  
## <a name="see-also"></a><span data-ttu-id="4ffd3-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4ffd3-135">See Also</span></span>
