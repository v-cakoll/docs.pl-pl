---
title: "Jeślilub przy użyciu reguł"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c4ad9bb2-9037-413a-8b14-59ed7b927a9e
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ed50cd5f27ab41702b134438693c4d75935cb4fc
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ifelse-with-rules"></a><span data-ttu-id="dae34-102">Jeślilub przy użyciu reguł</span><span class="sxs-lookup"><span data-stu-id="dae34-102">IfElse With Rules</span></span>
<span data-ttu-id="dae34-103">W tym przykładzie pokazano sposób użycia warunek reguły z <xref:System.Workflow.Activities.IfElseActivity> działania.</span><span class="sxs-lookup"><span data-stu-id="dae34-103">This sample shows the use of a rule condition with an <xref:System.Workflow.Activities.IfElseActivity> activity.</span></span>  
  
 <span data-ttu-id="dae34-104">Próbka przechodzi w `OrderValue` parametru z hosta.</span><span class="sxs-lookup"><span data-stu-id="dae34-104">The sample passes in an `OrderValue` parameter from the host.</span></span> <span data-ttu-id="dae34-105">Wartość parametru jest używana w warunku reguły na pierwszej gałęzi <xref:System.Workflow.Activities.IfElseActivity> działania.</span><span class="sxs-lookup"><span data-stu-id="dae34-105">The value of the parameter is used in a rule condition on the first branch of the <xref:System.Workflow.Activities.IfElseActivity> activity.</span></span> <span data-ttu-id="dae34-106">Jeśli wartość jest mniejsza niż 10 000, wykonuje pierwszej gałęzi i <xref:System.Workflow.Activities.CodeActivity> działania w pierwszym oddziału drukuje **uzyskać zatwierdzenia przez menedżera** do konsoli.</span><span class="sxs-lookup"><span data-stu-id="dae34-106">If the value is less than 10,000, the first branch executes, and the <xref:System.Workflow.Activities.CodeActivity> activity in the first branch prints **Get Manager Approval** to the console.</span></span> <span data-ttu-id="dae34-107">Jeśli wartość jest większa niż 10 000, <xref:System.Workflow.Activities.CodeActivity> działania w drugim gałęzi wykonuje i wyświetla **uzyskać zatwierdzenie VP**.</span><span class="sxs-lookup"><span data-stu-id="dae34-107">If the value is greater than 10,000, the <xref:System.Workflow.Activities.CodeActivity> activity in the second branch executes and prints **Get VP Approval**.</span></span>  
  
### <a name="to-build-the-sample"></a><span data-ttu-id="dae34-108">Aby samodzielnie tworzyć przykładowy</span><span class="sxs-lookup"><span data-stu-id="dae34-108">To build the sample</span></span>  
  
1.  <span data-ttu-id="dae34-109">Otwórz rozwiązanie w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dae34-109">Open the solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="dae34-110">Skompiluj rozwiązanie, naciskając klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="dae34-110">Build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="dae34-111">Uruchom rozwiązania bez debugowania, naciskając klawisze CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="dae34-111">Run the solution without debugging by pressing CTRL+F5.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="dae34-112">Aby uruchomić przykładowy</span><span class="sxs-lookup"><span data-stu-id="dae34-112">To run the sample</span></span>  
  
-   <span data-ttu-id="dae34-113">W oknie wiersza polecenia zestawu SDK Uruchom plik .exe w folderze IfElseWithRules\bin\debug (lub folderu IfElseWithRules\bin dla używanej wersji programu Visual Basic przykładu) znajdujący się poniżej głównego folderu przykładowej.</span><span class="sxs-lookup"><span data-stu-id="dae34-113">In the SDK Command Prompt window, run the .exe file in the IfElseWithRules\bin\debug folder (or the IfElseWithRules\bin folder for the Visual Basic version of the sample), which is located below the main folder for the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="dae34-114">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="dae34-114">The samples may already be installed on your computer.</span></span> <span data-ttu-id="dae34-115">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne):</span><span class="sxs-lookup"><span data-stu-id="dae34-115">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="dae34-116">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="dae34-116">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="dae34-117">W tym przykładzie znajduje się w następującym katalogu:</span><span class="sxs-lookup"><span data-stu-id="dae34-117">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\IfElseWithRules`  
  
## <a name="see-also"></a><span data-ttu-id="dae34-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dae34-118">See Also</span></span>  
 <xref:System.Workflow.Activities.Rules>  
 <xref:System.Workflow.Activities.IfElseActivity>  
 <xref:System.Workflow.Activities.CodeActivity>  
 <xref:System.Workflow.Activities.Rules.RuleDefinitions>
