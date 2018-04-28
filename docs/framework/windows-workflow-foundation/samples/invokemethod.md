---
title: InvokeMethod
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 04988eb3-65f8-456d-b1bd-509f5d05a57c
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f988f206fbd84b7b7d47fb3bd540420601ba30c9
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="invokemethod"></a><span data-ttu-id="168a1-102">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="168a1-102">InvokeMethod</span></span>
<span data-ttu-id="168a1-103">W tym przykładzie przedstawiono różne sposoby używania <xref:System.Activities.Statements.InvokeMethod> działania w celu wywołania metody klasy.</span><span class="sxs-lookup"><span data-stu-id="168a1-103">This sample shows the different ways of using the <xref:System.Activities.Statements.InvokeMethod> activity to invoke methods of a class.</span></span>  
  
 <span data-ttu-id="168a1-104">Metoda należy do klasy i reprezentuje zawartych w niej zestaw operacji.</span><span class="sxs-lookup"><span data-stu-id="168a1-104">A method belongs to a class and represents a contained set of operations.</span></span> <span data-ttu-id="168a1-105"><xref:System.Activities.Statements.InvokeMethod> Działania daje możliwość wywołania metody względem obiektów lub typy, przekazywanie parametrów i uzyskać wartość zwracaną.</span><span class="sxs-lookup"><span data-stu-id="168a1-105">The <xref:System.Activities.Statements.InvokeMethod> activity gives you the ability to call methods against objects or types, pass in parameters, and get the return value.</span></span> <span data-ttu-id="168a1-106">Metody można wywołać synchronicznie lub asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="168a1-106">Methods can be invoked synchronously or asynchronously.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="168a1-107">Szczegóły próbki</span><span class="sxs-lookup"><span data-stu-id="168a1-107">Sample Details</span></span>  
 <span data-ttu-id="168a1-108">W przykładzie użyto <xref:System.Activities.Statements.InvokeMethod> działanie do wykonania w następujących scenariuszach:</span><span class="sxs-lookup"><span data-stu-id="168a1-108">This sample uses the <xref:System.Activities.Statements.InvokeMethod> activity to perform the following scenarios:</span></span>  
  
1.  <span data-ttu-id="168a1-109">Wywołanie metody wystąpienia bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="168a1-109">Invoke an instance method without parameters.</span></span>  
  
2.  <span data-ttu-id="168a1-110">Wywołanie metody wystąpienia z dwoma parametrami (<xref:System.String> i <xref:System.Int32>).</span><span class="sxs-lookup"><span data-stu-id="168a1-110">Invoke an instance method with two parameters (<xref:System.String> and <xref:System.Int32>).</span></span>  
  
3.  <span data-ttu-id="168a1-111">Wywołanie metody wystąpienia z dwoma parametrami (<xref:System.String> i <xref:System.Int32>) i tablicy parametrów typu <xref:System.String>[].</span><span class="sxs-lookup"><span data-stu-id="168a1-111">Invoke an instance method with two parameters (<xref:System.String> and <xref:System.Int32>) and a parameter array of type <xref:System.String>[].</span></span>  
  
4.  <span data-ttu-id="168a1-112">Wywołanie metody wystąpienia z dwoma parametrami typu <xref:System.Int32> i wyniku typu <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="168a1-112">Invoke an instance method with two parameters of type <xref:System.Int32> and a result of type <xref:System.Int32>.</span></span> <span data-ttu-id="168a1-113">W tym scenariuszu wartość wyniku jest powiązany ze zmienną i używane w innym działaniu.</span><span class="sxs-lookup"><span data-stu-id="168a1-113">In this scenario, the result value is bound to a variable and used in another activity.</span></span> <span data-ttu-id="168a1-114">Jest wyświetlana w konsoli przy użyciu <xref:System.Activities.Statements.WriteLine> działania.</span><span class="sxs-lookup"><span data-stu-id="168a1-114">It is displayed in the console using the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
5.  <span data-ttu-id="168a1-115">Wywołanie metody statycznej z dwoma parametrami typu <xref:System.String> i <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="168a1-115">Invoke a static method with two parameters of type <xref:System.String> and <xref:System.Int32>.</span></span>  
  
6.  <span data-ttu-id="168a1-116">Wywołanie metody wystąpienia z jednym parametrem ogólnego typu <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="168a1-116">Invoke an instance method with one generic parameter of type <xref:System.String>.</span></span>  
  
7.  <span data-ttu-id="168a1-117">Wywołanie metody statycznej z dwa parametry ogólne typu <xref:System.String> i <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="168a1-117">Invoke a static method with two generic parameters of type <xref:System.String> and <xref:System.Int32>.</span></span>  
  
8.  <span data-ttu-id="168a1-118">Wywołanie metody wystąpienia, który ma jeden parametr przekazywany przez odwołanie typu <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="168a1-118">Invoke an instance method that has one parameter passed by reference of type <xref:System.String>.</span></span> <span data-ttu-id="168a1-119">W tym scenariuszu wiązania parametru odwołanie do zmiennej (`outParam`) i używane w innym działaniu.</span><span class="sxs-lookup"><span data-stu-id="168a1-119">In this scenario, the reference parameter is bound to a variable (`outParam`) and used in another activity.</span></span> <span data-ttu-id="168a1-120">Pojawi się przy użyciu konsoli <xref:System.Activities.Statements.WriteLine> działania.</span><span class="sxs-lookup"><span data-stu-id="168a1-120">It is displayed on the console using the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
9. <span data-ttu-id="168a1-121">Wywołanie metody asynchronicznej wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="168a1-121">Invoke an asynchronous instance method.</span></span>  
  
10. <span data-ttu-id="168a1-122">Wywołanie dwie różne metody dla tego samego wystąpienia obiektu za pomocą dwóch <xref:System.Activities.Statements.InvokeMethod> działań.</span><span class="sxs-lookup"><span data-stu-id="168a1-122">Invoke two different methods on the same instance of an object using two <xref:System.Activities.Statements.InvokeMethod> activities.</span></span>  
  
11. <span data-ttu-id="168a1-123">Zapisywanie wartości w wystąpieniu obiektu.</span><span class="sxs-lookup"><span data-stu-id="168a1-123">Store a value in an instance of an object.</span></span>  
  
12. <span data-ttu-id="168a1-124">Pobierz wartość z wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="168a1-124">Retrieve a value from an instance of an object.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="168a1-125">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="168a1-125">To use this sample</span></span>  
 <span data-ttu-id="168a1-126">W tym przykładzie znajduje się w dwóch wersjach.</span><span class="sxs-lookup"><span data-stu-id="168a1-126">This sample is provided in two versions.</span></span> <span data-ttu-id="168a1-127">Pierwszą wersję w tym przykładzie przedstawiono użycie <xref:System.Activities.Statements.InvokeMethod> za pomocą języka C# w kodzie za pomocą modelu programowania Windows Workflow Foundation (WF) i znajduje się w folderze CodedWorkflow\CS.</span><span class="sxs-lookup"><span data-stu-id="168a1-127">The first version of this sample demonstrates the usage of <xref:System.Activities.Statements.InvokeMethod> through C# code using the Windows Workflow Foundation (WF) programming model and can be found under the CodedWorkflow\CS folder.</span></span> <span data-ttu-id="168a1-128">Druga wersja przedstawiono użycie <xref:System.Activities.Statements.InvokeMethod> przy użyciu kodu XAML i znajduje się w folderze DesignerWorkflow\CS.</span><span class="sxs-lookup"><span data-stu-id="168a1-128">The second version demonstrates the usage of <xref:System.Activities.Statements.InvokeMethod> using XAML and can be found under the DesignerWorkflow\CS folder.</span></span>  
  
#### <a name="to-run-the-coded-workflow-sample"></a><span data-ttu-id="168a1-129">Aby uruchomić przykład kodowane przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="168a1-129">To run the coded workflow sample</span></span>  
  
1.  <span data-ttu-id="168a1-130">Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania InvokeMethodUsage.sln w folderze CodedWorkflow\CS.</span><span class="sxs-lookup"><span data-stu-id="168a1-130">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the InvokeMethodUsage.sln solution file in the CodedWorkflow\CS folder.</span></span>  
  
2.  <span data-ttu-id="168a1-131">Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="168a1-131">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="168a1-132">Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="168a1-132">To run the solution, press CTRL+F5.</span></span>  
  
#### <a name="to-run-the-designer-workflow-sample"></a><span data-ttu-id="168a1-133">Aby uruchomić przykład projektanta przepływów pracy</span><span class="sxs-lookup"><span data-stu-id="168a1-133">To run the designer workflow sample</span></span>  
  
1.  <span data-ttu-id="168a1-134">Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania InvokeMethodUsage.sln w folderze DesignerWorkflow\CS.</span><span class="sxs-lookup"><span data-stu-id="168a1-134">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the InvokeMethodUsage.sln solution file in the DesignerWorkflow\CS folder.</span></span>  
  
2.  <span data-ttu-id="168a1-135">Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="168a1-135">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="168a1-136">Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="168a1-136">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="168a1-137">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="168a1-137">The samples may already be installed on your machine.</span></span> <span data-ttu-id="168a1-138">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="168a1-138">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="168a1-139">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="168a1-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="168a1-140">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="168a1-140">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InvokeMethod`