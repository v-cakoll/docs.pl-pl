---
title: "Za pomocą działania InvokeMethod"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b6643550-d043-4ac7-8069-9c55ebbb4233
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5dd488a01e00af0661ee7ee110c79d2c56a0b777
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="using-the-invokemethod-activity"></a><span data-ttu-id="4d595-102">Za pomocą działania InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="4d595-102">Using the InvokeMethod Activity</span></span>
<span data-ttu-id="4d595-103">W tym przykładzie przedstawiono sposób użycia <!--zz <xref:System.Activities.Statements.InvokeMethod%601> --> [ <code>System.Activities.Statements.InvokeMethod\\`1</code> ](https://msdn.microsoft.com/library/dd647677.aspx) działania w celu wywołania metody publiczne klas publicznych.</span><span class="sxs-lookup"><span data-stu-id="4d595-103">This sample demonstrates how to use the <!--zz <xref:System.Activities.Statements.InvokeMethod%601> -->[<code>System.Activities.Statements.InvokeMethod\\`1</code>](https://msdn.microsoft.com/library/dd647677.aspx) activity to invoke public methods in public classes.</span></span> <span data-ttu-id="4d595-104"><!--zz <xref:System.Activities.Statements.InvokeMethod%601> --> [ <code>System.Activities.Statements.InvokeMethod\\`1</code> ](https://msdn.microsoft.com/library/dd647677.aspx) Działanie zezwala przepływu pracy do wywołania metody obiektów, przekazywanie parametrów przechowywana wartość zwracana, określić typy metod ogólnych i określ, czy metoda jest synchroniczne lub asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="4d595-104">The <!--zz <xref:System.Activities.Statements.InvokeMethod%601> -->[<code>System.Activities.Statements.InvokeMethod\\`1</code>](https://msdn.microsoft.com/library/dd647677.aspx) activity allows a workflow to call methods against objects, pass in parameters, get the return value, specify types for generic methods, and specify whether the method is synchronous or asynchronous.</span></span> 
  
 <span data-ttu-id="4d595-105">Dostępna jest wersja nieogólnego <xref:System.Activities.Statements.InvokeMethod> działania, których wartość zwracana jest wartość <xref:System.Activities.Statements.InvokeMethod.Result%2A> właściwości i rodzajowy wersja <!--zz <xref:System.Activities.Statements.InvokeMethod%601> --> [ <code>System.Activities.Statements.InvokeMethod\`1</code> ](https://msdn.microsoft.com/library/dd647677.aspx) działania, w której jest zwracana wartość zwracana za pomocą <!--zz <xref:System.Activities.Statements.InvokeMethod.Result%601.Result%2A> --> [ <code>System.Activities.Statements.InvokeMethod\`1.Result</code> ](https://msdn.microsoft.com/library/dd987724.aspx) właściwości typu `TResult`.</span><span class="sxs-lookup"><span data-stu-id="4d595-105">There is a non-generic version of the <xref:System.Activities.Statements.InvokeMethod> activity where the return value is set to the <xref:System.Activities.Statements.InvokeMethod.Result%2A> property and a generic version of the <!--zz <xref:System.Activities.Statements.InvokeMethod%601> -->[<code>System.Activities.Statements.InvokeMethod\`1</code>](https://msdn.microsoft.com/library/dd647677.aspx) activity where the return value is returned through the <!--zz <xref:System.Activities.Statements.InvokeMethod.Result%601.Result%2A> -->[<code>System.Activities.Statements.InvokeMethod\`1.Result</code>](https://msdn.microsoft.com/library/dd987724.aspx) property of type `TResult`.</span></span>  
  
 <span data-ttu-id="4d595-106">W tym przykładzie pokazano, jak wywołać metodę różnego.</span><span class="sxs-lookup"><span data-stu-id="4d595-106">This sample demonstrates how to call various method types.</span></span> <span data-ttu-id="4d595-107">Poniższe szczegóły listy typów metody zostało to pokazane w tym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="4d595-107">The following list details the method types demonstrated in this sample:</span></span>  
  
-   <span data-ttu-id="4d595-108">Wywołanie metody wystąpienia bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="4d595-108">Invoke an instance method without parameters.</span></span>  
  
-   <span data-ttu-id="4d595-109">Wywołanie metody wystąpienia z dwoma parametrami (System.String i System.Int32).</span><span class="sxs-lookup"><span data-stu-id="4d595-109">Invoke an instance method with two parameters (System.String and System.Int32).</span></span>  
  
-   <span data-ttu-id="4d595-110">Wywołanie metody wystąpienia z dwóch parametrów (System.String i System.Int32) i tablicy parametrów typu System.String [].</span><span class="sxs-lookup"><span data-stu-id="4d595-110">Invoke an instance method with two parameters (System.String and System.Int32) and a parameter array of type System.String[].</span></span>  
  
-   <span data-ttu-id="4d595-111">Wywołanie metody wystąpienia z dwoma parametrami (dwie liczb System.Int32) i wyniku typu System.Int32.</span><span class="sxs-lookup"><span data-stu-id="4d595-111">Invoke an instance method with two parameters (two System.Int32 numbers) and a result of type System.Int32.</span></span>  
  
     <span data-ttu-id="4d595-112">Wartość zwracana jest powiązany ze zmienną i wydrukować przy użyciu konsoli <xref:System.Activities.Statements.WriteLine> działania.</span><span class="sxs-lookup"><span data-stu-id="4d595-112">The return value is bound to a variable and printed to the console using the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
-   <span data-ttu-id="4d595-113">Wywołanie metody statycznej z dwoma parametrami (System.String i System.Int32).</span><span class="sxs-lookup"><span data-stu-id="4d595-113">Invoke a static method with two parameters (System.String and System.Int32).</span></span>  
  
-   <span data-ttu-id="4d595-114">Wywołanie metody wystąpienia z jednego parametru ogólnego (System.String).</span><span class="sxs-lookup"><span data-stu-id="4d595-114">Invoke an instance method with one generic parameter (System.String).</span></span>  
  
-   <span data-ttu-id="4d595-115">Wywołanie metody statycznej z dwa parametry ogólne (System.String i System.Int32).</span><span class="sxs-lookup"><span data-stu-id="4d595-115">Invoke a static method with two generic parameters (System.String and System.Int32).</span></span>  
  
-   <span data-ttu-id="4d595-116">Wywołanie metody wystąpienia, który ma jeden parametr przekazywany przez odwołanie (System.String).</span><span class="sxs-lookup"><span data-stu-id="4d595-116">Invoke an instance method that has one parameter passed by reference (System.String).</span></span>  
  
     <span data-ttu-id="4d595-117">Parametr przywoływanego jest powiązany ze zmienną i wydrukować przy użyciu konsoli <xref:System.Activities.Statements.WriteLine> działania.</span><span class="sxs-lookup"><span data-stu-id="4d595-117">The referenced parameter is bound to a variable and printed to the console using the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
-   <span data-ttu-id="4d595-118">Wywołanie metody asynchronicznej wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="4d595-118">Invoke an asynchronous instance method.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="4d595-119">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="4d595-119">To use this sample</span></span>  
  
1.  <span data-ttu-id="4d595-120">Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania InvokeMethodUsage.sln.</span><span class="sxs-lookup"><span data-stu-id="4d595-120">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the InvokeMethodUsage.sln solution file.</span></span>  
  
2.  <span data-ttu-id="4d595-121">Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="4d595-121">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="4d595-122">Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="4d595-122">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4d595-123">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="4d595-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4d595-124">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="4d595-124">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4d595-125">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="4d595-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4d595-126">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="4d595-126">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InvokeMethod`  
  
## <a name="see-also"></a><span data-ttu-id="4d595-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4d595-127">See Also</span></span>
