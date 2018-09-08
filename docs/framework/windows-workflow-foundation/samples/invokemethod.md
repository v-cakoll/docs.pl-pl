---
title: InvokeMethod
ms.date: 03/30/2017
ms.assetid: 04988eb3-65f8-456d-b1bd-509f5d05a57c
ms.openlocfilehash: 861e0cf160aec9814abcf8c27c37ce13a5d88b2a
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44217064"
---
# <a name="invokemethod"></a><span data-ttu-id="862f8-102">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="862f8-102">InvokeMethod</span></span>
<span data-ttu-id="862f8-103">W tym przykładzie pokazano różne sposoby korzystania z <xref:System.Activities.Statements.InvokeMethod> działania w celu wywołania metody klasy.</span><span class="sxs-lookup"><span data-stu-id="862f8-103">This sample shows the different ways of using the <xref:System.Activities.Statements.InvokeMethod> activity to invoke methods of a class.</span></span>  
  
 <span data-ttu-id="862f8-104">Metoda należy do klasy i reprezentuje ograniczonego zestawu operacji.</span><span class="sxs-lookup"><span data-stu-id="862f8-104">A method belongs to a class and represents a contained set of operations.</span></span> <span data-ttu-id="862f8-105"><xref:System.Activities.Statements.InvokeMethod> Działania daje możliwość wywołania metod względem obiektów lub typy, przekazanie parametrów i uzyskać wartość zwracaną.</span><span class="sxs-lookup"><span data-stu-id="862f8-105">The <xref:System.Activities.Statements.InvokeMethod> activity gives you the ability to call methods against objects or types, pass in parameters, and get the return value.</span></span> <span data-ttu-id="862f8-106">Metody może być wywołana synchronicznie lub asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="862f8-106">Methods can be invoked synchronously or asynchronously.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="862f8-107">Przykład szczegółów</span><span class="sxs-lookup"><span data-stu-id="862f8-107">Sample Details</span></span>  
 <span data-ttu-id="862f8-108">W tym przykładzie użyto <xref:System.Activities.Statements.InvokeMethod> działania do wykonania w następujących scenariuszach:</span><span class="sxs-lookup"><span data-stu-id="862f8-108">This sample uses the <xref:System.Activities.Statements.InvokeMethod> activity to perform the following scenarios:</span></span>  
  
1.  <span data-ttu-id="862f8-109">Wywołaj metodę wystąpienia bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="862f8-109">Invoke an instance method without parameters.</span></span>  
  
2.  <span data-ttu-id="862f8-110">Wywołaj metodę wystąpienia, z dwoma parametrami (<xref:System.String> i <xref:System.Int32>).</span><span class="sxs-lookup"><span data-stu-id="862f8-110">Invoke an instance method with two parameters (<xref:System.String> and <xref:System.Int32>).</span></span>  
  
3.  <span data-ttu-id="862f8-111">Wywołaj metodę wystąpienia, z dwoma parametrami (<xref:System.String> i <xref:System.Int32>) i tablicy parametrów typu <xref:System.String>[].</span><span class="sxs-lookup"><span data-stu-id="862f8-111">Invoke an instance method with two parameters (<xref:System.String> and <xref:System.Int32>) and a parameter array of type <xref:System.String>[].</span></span>  
  
4.  <span data-ttu-id="862f8-112">Wywołaj metodę wystąpienia, z dwoma parametrami typu <xref:System.Int32> i wynik o typie <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="862f8-112">Invoke an instance method with two parameters of type <xref:System.Int32> and a result of type <xref:System.Int32>.</span></span> <span data-ttu-id="862f8-113">W tym scenariuszu wartość wyniku jest powiązany ze zmienną i używane w innym działaniu.</span><span class="sxs-lookup"><span data-stu-id="862f8-113">In this scenario, the result value is bound to a variable and used in another activity.</span></span> <span data-ttu-id="862f8-114">Jest wyświetlana w konsoli przy użyciu <xref:System.Activities.Statements.WriteLine> działania.</span><span class="sxs-lookup"><span data-stu-id="862f8-114">It is displayed in the console using the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
5.  <span data-ttu-id="862f8-115">Wywołanie metody statycznej z dwoma parametrami typu <xref:System.String> i <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="862f8-115">Invoke a static method with two parameters of type <xref:System.String> and <xref:System.Int32>.</span></span>  
  
6.  <span data-ttu-id="862f8-116">Wywoływanie metody wystąpienia mającej jeden parametr ogólny typu <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="862f8-116">Invoke an instance method with one generic parameter of type <xref:System.String>.</span></span>  
  
7.  <span data-ttu-id="862f8-117">Wywołanie metody statycznej z dwoma parametrami ogólnego typu <xref:System.String> i <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="862f8-117">Invoke a static method with two generic parameters of type <xref:System.String> and <xref:System.Int32>.</span></span>  
  
8.  <span data-ttu-id="862f8-118">Wywołaj metodę wystąpienia, która ma jeden parametr przekazywany przez odwołanie typu <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="862f8-118">Invoke an instance method that has one parameter passed by reference of type <xref:System.String>.</span></span> <span data-ttu-id="862f8-119">W tym scenariuszu parametr odwołania jest powiązany ze zmienną (`outParam`) i używane w innym działaniu.</span><span class="sxs-lookup"><span data-stu-id="862f8-119">In this scenario, the reference parameter is bound to a variable (`outParam`) and used in another activity.</span></span> <span data-ttu-id="862f8-120">Jest wyświetlana w konsoli przy użyciu <xref:System.Activities.Statements.WriteLine> działania.</span><span class="sxs-lookup"><span data-stu-id="862f8-120">It is displayed on the console using the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
9. <span data-ttu-id="862f8-121">Wywołaj metodę asynchroniczną wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="862f8-121">Invoke an asynchronous instance method.</span></span>  
  
10. <span data-ttu-id="862f8-122">Wywołania na dwa sposoby na tym samym wystąpieniu obiektu przy użyciu dwóch <xref:System.Activities.Statements.InvokeMethod> działań.</span><span class="sxs-lookup"><span data-stu-id="862f8-122">Invoke two different methods on the same instance of an object using two <xref:System.Activities.Statements.InvokeMethod> activities.</span></span>  
  
11. <span data-ttu-id="862f8-123">Store wartość w wystąpieniu obiektu.</span><span class="sxs-lookup"><span data-stu-id="862f8-123">Store a value in an instance of an object.</span></span>  
  
12. <span data-ttu-id="862f8-124">Pobierz wartość z wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="862f8-124">Retrieve a value from an instance of an object.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="862f8-125">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="862f8-125">To use this sample</span></span>  
 <span data-ttu-id="862f8-126">W tym przykładzie jest dostępna w dwóch wersjach.</span><span class="sxs-lookup"><span data-stu-id="862f8-126">This sample is provided in two versions.</span></span> <span data-ttu-id="862f8-127">Pierwsza wersja ten przykład pokazuje użycie <xref:System.Activities.Statements.InvokeMethod> za pomocą języka C# kodu za pomocą modelu programowania Windows Workflow Foundation (WF) i można go znaleźć w folderze CodedWorkflow\CS.</span><span class="sxs-lookup"><span data-stu-id="862f8-127">The first version of this sample demonstrates the usage of <xref:System.Activities.Statements.InvokeMethod> through C# code using the Windows Workflow Foundation (WF) programming model and can be found under the CodedWorkflow\CS folder.</span></span> <span data-ttu-id="862f8-128">Druga wersja prezentuje sposób użycia <xref:System.Activities.Statements.InvokeMethod> przy użyciu XAML i można go znaleźć w folderze DesignerWorkflow\CS.</span><span class="sxs-lookup"><span data-stu-id="862f8-128">The second version demonstrates the usage of <xref:System.Activities.Statements.InvokeMethod> using XAML and can be found under the DesignerWorkflow\CS folder.</span></span>  
  
#### <a name="to-run-the-coded-workflow-sample"></a><span data-ttu-id="862f8-129">Aby uruchomić przykład kodowane przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="862f8-129">To run the coded workflow sample</span></span>  
  
1.  <span data-ttu-id="862f8-130">Za pomocą [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania InvokeMethodUsage.sln w folderze CodedWorkflow\CS.</span><span class="sxs-lookup"><span data-stu-id="862f8-130">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the InvokeMethodUsage.sln solution file in the CodedWorkflow\CS folder.</span></span>  
  
2.  <span data-ttu-id="862f8-131">Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="862f8-131">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="862f8-132">Aby uruchomić rozwiązanie, naciśnij kombinację klawiszy CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="862f8-132">To run the solution, press CTRL+F5.</span></span>  
  
#### <a name="to-run-the-designer-workflow-sample"></a><span data-ttu-id="862f8-133">Aby uruchomić przykład projektanta przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="862f8-133">To run the designer workflow sample</span></span>  
  
1.  <span data-ttu-id="862f8-134">Za pomocą [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania InvokeMethodUsage.sln w folderze DesignerWorkflow\CS.</span><span class="sxs-lookup"><span data-stu-id="862f8-134">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the InvokeMethodUsage.sln solution file in the DesignerWorkflow\CS folder.</span></span>  
  
2.  <span data-ttu-id="862f8-135">Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="862f8-135">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="862f8-136">Aby uruchomić rozwiązanie, naciśnij kombinację klawiszy CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="862f8-136">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="862f8-137">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="862f8-137">The samples may already be installed on your machine.</span></span> <span data-ttu-id="862f8-138">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="862f8-138">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="862f8-139">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="862f8-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="862f8-140">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="862f8-140">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InvokeMethod`