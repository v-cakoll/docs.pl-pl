---
title: Proste zasad
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a94c834-2e32-4bed-9f47-ae5845eef6ff
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6a2798c753e1fc526b2f95801d49108a2aba9e8a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="simple-policy"></a><span data-ttu-id="43ca0-102">Proste zasad</span><span class="sxs-lookup"><span data-stu-id="43ca0-102">Simple Policy</span></span>
<span data-ttu-id="43ca0-103">Ten przykład przedstawia sposób użycia <xref:System.Workflow.Activities.PolicyActivity> działania w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="43ca0-103">This sample shows how to use a <xref:System.Workflow.Activities.PolicyActivity> activity in a workflow.</span></span>  
  
 <span data-ttu-id="43ca0-104">Sekwencyjny przepływ pracy, w tym przykładzie jest tworzona przy użyciu <xref:System.Workflow.Activities.PolicyActivity> działania.</span><span class="sxs-lookup"><span data-stu-id="43ca0-104">The sequential workflow in this sample is created by using a <xref:System.Workflow.Activities.PolicyActivity> activity.</span></span> <span data-ttu-id="43ca0-105">Przepływ pracy definiuje `orderValue`, `customerType`, i `discount` pola, które są używane do definiowania produktu discount przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="43ca0-105">The workflow defines `orderValue`, `customerType`, and `discount` fields that are used to define a product discount workflow.</span></span> <span data-ttu-id="43ca0-106">Od reguł zdefiniowanych w pliku reguł wartość Rabat na podstawie `orderValue` i `customerType`.</span><span class="sxs-lookup"><span data-stu-id="43ca0-106">The rules defined in the rules file set a discount value that is based on the `orderValue` and `customerType`.</span></span> <span data-ttu-id="43ca0-107">`orderValue` i `customerType` są ustawione w `SimplePolicyWorkflow` definicji klasy i można ich zmieniać do zmiany zachowania.</span><span class="sxs-lookup"><span data-stu-id="43ca0-107">The `orderValue` and `customerType` are set in the `SimplePolicyWorkflow` class definition and can be changed to alter the behavior.</span></span> <span data-ttu-id="43ca0-108">Wynikowa rabat są zapisywane do konsoli w <xref:System.Workflow.Runtime.WorkflowRuntime.WorkflowCompleted> obsługi zdarzeń, który jest zdefiniowany w `SimplePolicyWorkflow` klasy.</span><span class="sxs-lookup"><span data-stu-id="43ca0-108">The resulting discount is written to the console in the <xref:System.Workflow.Runtime.WorkflowRuntime.WorkflowCompleted> event handler that is defined in the `SimplePolicyWorkflow` class.</span></span>  
  
### <a name="to-build-the-sample"></a><span data-ttu-id="43ca0-109">Aby samodzielnie tworzyć przykładowy</span><span class="sxs-lookup"><span data-stu-id="43ca0-109">To build the sample</span></span>  
  
1.  <span data-ttu-id="43ca0-110">Otwórz rozwiązanie w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="43ca0-110">Open the solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="43ca0-111">Skompiluj rozwiązanie, naciskając klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="43ca0-111">Build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="43ca0-112">Uruchom rozwiązania bez debugowania, naciskając klawisze CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="43ca0-112">Run the solution without debugging by pressing CTRL+F5.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="43ca0-113">Aby uruchomić przykładowy</span><span class="sxs-lookup"><span data-stu-id="43ca0-113">To run the sample</span></span>  
  
-   <span data-ttu-id="43ca0-114">W oknie wiersza polecenia zestawu SDK Uruchom plik .exe w folderze SimplePolicy\bin\debug (lub folderu SimplePolicy\bin dla używanej wersji programu Visual Basic przykładu) znajdujący się poniżej głównego folderu przykładowej.</span><span class="sxs-lookup"><span data-stu-id="43ca0-114">In the SDK Command Prompt window, run the .exe file in the SimplePolicy\bin\debug folder (or the SimplePolicy\bin folder for the Visual Basic version of the sample), which is located below the main folder for the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="43ca0-115">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="43ca0-115">The samples may already be installed on your computer.</span></span> <span data-ttu-id="43ca0-116">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne):</span><span class="sxs-lookup"><span data-stu-id="43ca0-116">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="43ca0-117">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="43ca0-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="43ca0-118">W tym przykładzie znajduje się w następującym katalogu:</span><span class="sxs-lookup"><span data-stu-id="43ca0-118">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\SimplePolicy`  
  
## <a name="see-also"></a><span data-ttu-id="43ca0-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="43ca0-119">See Also</span></span>  
 <xref:System.Workflow.Activities.Rules.RuleSet>  
 <xref:System.Workflow.Activities.PolicyActivity>  
 [<span data-ttu-id="43ca0-120">Zaawansowane zasady</span><span class="sxs-lookup"><span data-stu-id="43ca0-120">Advanced Policy</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/advanced-policy.md)
