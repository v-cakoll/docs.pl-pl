---
title: Witaj świecie niestandardowego działania
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 72b1dd0a-9aad-47d5-95a9-a1024ee1d0a1
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fa441a3019b0ef6df31dc0a46be7ea7e8e00a4b8
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="hello-world-custom-activity"></a><span data-ttu-id="4f726-102">Witaj świecie niestandardowego działania</span><span class="sxs-lookup"><span data-stu-id="4f726-102">Hello World Custom Activity</span></span>
<span data-ttu-id="4f726-103">W przykładzie pokazano kilka najważniejsze funkcje programu Windows Workflow Foundation (WF), łącznie ze sposobem tworzenia prostych działań niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="4f726-103">This sample demonstrates several key features of Windows Workflow Foundation (WF), including how to create a simple custom activity.</span></span> <span data-ttu-id="4f726-104">Niektóre funkcje zostało to pokazane w tym przykładzie tworzenia działań niestandardowych w języku C# i za pomocą `in` i `out` argumentów (<xref:System.Activities.InArgument> i <xref:System.Activities.OutArgument>).</span><span class="sxs-lookup"><span data-stu-id="4f726-104">Some of the features demonstrated in this sample are creating a custom activity in C# and using `in` and `out` arguments (<xref:System.Activities.InArgument> and <xref:System.Activities.OutArgument>).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4f726-105">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="4f726-105">The samples may already be installed on your computer.</span></span> <span data-ttu-id="4f726-106">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="4f726-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4f726-107">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="4f726-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4f726-108">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="4f726-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\HelloWorld`  
  
## <a name="creating-a-workflow-in-code"></a><span data-ttu-id="4f726-109">Tworzenie przepływu pracy w kodzie</span><span class="sxs-lookup"><span data-stu-id="4f726-109">Creating a Workflow in Code</span></span>  
 <span data-ttu-id="4f726-110">W tym przykładzie dwa działania niestandardowe są tworzone przy użyciu kodu C#.</span><span class="sxs-lookup"><span data-stu-id="4f726-110">In this sample, two custom activities are created using C# code.</span></span> <span data-ttu-id="4f726-111">Zarówno działań niestandardowych dziedziczy pośrednio ani bezpośrednio po <xref:System.Activities.Activity%601> aby zwracać pojedynczą wartość.</span><span class="sxs-lookup"><span data-stu-id="4f726-111">Both custom activities inherit directly or indirectly from <xref:System.Activities.Activity%601> to return a single value.</span></span> <span data-ttu-id="4f726-112">Zaletą używania ogólnego zwracanej wartości, zamiast dziedziczenia z nieogólnego <xref:System.Activities.Activity> klasa, jest to, że niektóre działania (takie jak <xref:System.Activities.Statements.Assign>) mogą uzyskiwać dostęp wartość zwracana, gdy jest używany jako część składa działania.</span><span class="sxs-lookup"><span data-stu-id="4f726-112">The advantage of using the generic return value, instead of inheriting from the non-generic <xref:System.Activities.Activity> class, is that some activities (such as <xref:System.Activities.Statements.Assign>) are able to access the return value when used as part of a composed activity.</span></span>  
  
 <span data-ttu-id="4f726-113">AppendString</span><span class="sxs-lookup"><span data-stu-id="4f726-113">AppendString</span></span>  
 <span data-ttu-id="4f726-114">To działanie dziedziczy <xref:System.Activities.Activity%601>i używa <xref:System.Activities.Statements.Assign> działanie, które łączy dwa ciągi ze sobą.</span><span class="sxs-lookup"><span data-stu-id="4f726-114">This activity inherits from <xref:System.Activities.Activity%601>, and uses an <xref:System.Activities.Statements.Assign> activity that concatenates two strings together.</span></span>  
  
 <span data-ttu-id="4f726-115">Dołączenie wartości ciągu</span><span class="sxs-lookup"><span data-stu-id="4f726-115">Prepend String</span></span>  
 <span data-ttu-id="4f726-116">To działanie dziedziczy bezpośrednio <xref:System.Activities.CodeActivity%601>i tworzy podobne funkcje `AppendString` działalność, która używa logiki zaimplementowano w kodzie nie eksportami istniejące działania.</span><span class="sxs-lookup"><span data-stu-id="4f726-116">This activity inherits directly from <xref:System.Activities.CodeActivity%601>, and creates similar functionality to the `AppendString` activity, which uses logic implemented in code rather than being composed of a pre-existing activity.</span></span>  
  
 <span data-ttu-id="4f726-117">Następujące pliki znajdują się w tym projekcie.</span><span class="sxs-lookup"><span data-stu-id="4f726-117">The following files are included in this project.</span></span>  
  
 <span data-ttu-id="4f726-118">AppendString.cs</span><span class="sxs-lookup"><span data-stu-id="4f726-118">AppendString.cs</span></span>  
 <span data-ttu-id="4f726-119">Niestandardowe działanie, które dołącza ciągi ze sobą.</span><span class="sxs-lookup"><span data-stu-id="4f726-119">The custom activity that appends strings together.</span></span> <span data-ttu-id="4f726-120">On przyjmuje w ciągu i łączy go z ciągiem literału tekst "hello world mówi" do formularza pełny komunikat jako dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="4f726-120">It takes in a string and combines it with a literal text string " says hello world" to form a complete message as output.</span></span>  
  
 <span data-ttu-id="4f726-121">PrependString.cs</span><span class="sxs-lookup"><span data-stu-id="4f726-121">PrependString.cs</span></span>  
 <span data-ttu-id="4f726-122">To działanie prefiksy wstępnie zdefiniowanych ciąg wejściowy ciąg.</span><span class="sxs-lookup"><span data-stu-id="4f726-122">This activity prefixes a predefined string to an input string.</span></span>  
  
 <span data-ttu-id="4f726-123">Sequence1.XAML</span><span class="sxs-lookup"><span data-stu-id="4f726-123">Sequence1.xaml</span></span>  
 <span data-ttu-id="4f726-124">Przepływ pracy, który używa `AppendString` i `PrependString` działań niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="4f726-124">A workflow that uses the `AppendString` and `PrependString` custom activities.</span></span>  
  
 <span data-ttu-id="4f726-125">Program.cs</span><span class="sxs-lookup"><span data-stu-id="4f726-125">Program.cs</span></span>  
 <span data-ttu-id="4f726-126">Program, który uruchamia przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="4f726-126">A program that runs the workflow.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="4f726-127">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="4f726-127">To use this sample</span></span>  
  
1.  <span data-ttu-id="4f726-128">Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania HelloWorld.sln.</span><span class="sxs-lookup"><span data-stu-id="4f726-128">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the HelloWorld.sln solution file.</span></span>  
  
2.  <span data-ttu-id="4f726-129">Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="4f726-129">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="4f726-130">Aby uruchomić rozwiązanie, naciśnij klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="4f726-130">To run the solution, press F5.</span></span>