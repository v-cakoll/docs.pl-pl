---
title: "Za pomocą klasy WorkflowInvoker"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a966164-3990-4e78-8aa2-c6797ebbee94
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4265cd7fb0f894cc9cefd793727ebb513d3021c8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="using-the-workflowinvoker-class"></a><span data-ttu-id="ff195-102">Za pomocą klasy WorkflowInvoker</span><span class="sxs-lookup"><span data-stu-id="ff195-102">Using the WorkflowInvoker Class</span></span>
<span data-ttu-id="ff195-103">W tym przykładzie przedstawiono sposób użycia <xref:System.Activities.WorkflowInvoker> klasy można wywołać działania, tak jakby był on metodę.</span><span class="sxs-lookup"><span data-stu-id="ff195-103">This sample demonstrates how to use the <xref:System.Activities.WorkflowInvoker> class to invoke an activity as if it were a method.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="ff195-104">Szczegóły próbki</span><span class="sxs-lookup"><span data-stu-id="ff195-104">Sample Details</span></span>  
 <span data-ttu-id="ff195-105">Przy użyciu <xref:System.Activities.WorkflowInvoker> klasy jest najprostszym sposobem wykonania działania.</span><span class="sxs-lookup"><span data-stu-id="ff195-105">Using the <xref:System.Activities.WorkflowInvoker> class is the simplest way to execute an activity.</span></span> <span data-ttu-id="ff195-106">Jest przeznaczony do bezpośredniego uruchamiania działania, jak w przypadku wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="ff195-106">It is designed for directly running an activity as if it were a method call.</span></span> <span data-ttu-id="ff195-107">Jest lekki, wysokiej wydajności, łatwy w użyciu interfejsu API w scenariuszach, w którym wykonania działania nie wymaga infrastrukturę kontroli innych zmian hostingu.</span><span class="sxs-lookup"><span data-stu-id="ff195-107">It is a lightweight, high-performing, easy to use API for use in scenarios where an activity’s execution does not require the control infrastructure provided by other hosting variations.</span></span>  
  
 <span data-ttu-id="ff195-108">W przykładzie użyto niestandardowego działania, która jest pochodną <xref:System.Activities.CodeActivity%601>< Int32\> o nazwie `Add` dodaje dwa <xref:System.Activities.InArgument%601>, `X` i `Y`i zwraca `Result` <xref:System.Activities.OutArgument%601>.</span><span class="sxs-lookup"><span data-stu-id="ff195-108">The sample uses a custom activity that derives from <xref:System.Activities.CodeActivity%601><Int32\> named `Add` that adds two <xref:System.Activities.InArgument%601>, `X` and `Y`, and returns a `Result`<xref:System.Activities.OutArgument%601>.</span></span> <span data-ttu-id="ff195-109">(<xref:System.Activities.CodeActivity%601>\<T > jest pochodną <xref:System.Activities.Activity%601>< T\>, który ma <xref:System.Activities.OutArgument%601> \<T > o nazwie `Result`.) A `Dictionary` \<string, object > służy do przekazania argumenty do wywoływanego przez działania <xref:System.Activities.WorkflowInvoker>.</span><span class="sxs-lookup"><span data-stu-id="ff195-109">(<xref:System.Activities.CodeActivity%601>\<T> derives from <xref:System.Activities.Activity%601><T\>, which has an <xref:System.Activities.OutArgument%601>\<T> named `Result`.) A `Dictionary`\<string, object> is used to pass arguments into an activity being invoked through <xref:System.Activities.WorkflowInvoker>.</span></span> <span data-ttu-id="ff195-110">Klucz słownika odpowiada nazwa argumentu wywoływanego działania.</span><span class="sxs-lookup"><span data-stu-id="ff195-110">The key of the dictionary corresponds to the name of an argument on the invoked activity.</span></span> <span data-ttu-id="ff195-111">Argument identyfikowane za pomocą klucza jest powiązana wartość skojarzoną z określonym kluczem.</span><span class="sxs-lookup"><span data-stu-id="ff195-111">The value associated with a particular key is bound to the argument identified by the key.</span></span>  
  
 <span data-ttu-id="ff195-112">Wywołania próbki <xref:System.Activities.WorkflowInvoker.Invoke%2A> i przekazuje słownik, który zawiera wartości `X` i `Y`.</span><span class="sxs-lookup"><span data-stu-id="ff195-112">The sample calls <xref:System.Activities.WorkflowInvoker.Invoke%2A> and passes a dictionary that contains values for `X` and `Y`.</span></span> <span data-ttu-id="ff195-113"><xref:System.Activities.WorkflowInvoker> Klasy wiąże tych wartości `Add` działania przez argumenty, wykonuje działanie i zwraca wynik.</span><span class="sxs-lookup"><span data-stu-id="ff195-113">The <xref:System.Activities.WorkflowInvoker> class binds these values to the `Add` activity’s arguments, executes the activity, and returns the result.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="ff195-114">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="ff195-114">To use this sample</span></span>  
  
1.  <span data-ttu-id="ff195-115">Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania Invoker.sln.</span><span class="sxs-lookup"><span data-stu-id="ff195-115">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the Invoker.sln solution file.</span></span>  
  
2.  <span data-ttu-id="ff195-116">Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="ff195-116">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="ff195-117">Aby uruchomić rozwiązanie, naciśnij klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="ff195-117">To run the solution, press F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ff195-118">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="ff195-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ff195-119">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="ff195-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ff195-120">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="ff195-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ff195-121">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="ff195-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\WorkflowInvoker`