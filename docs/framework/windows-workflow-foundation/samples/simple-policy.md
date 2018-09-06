---
title: Proste zasady
ms.date: 03/30/2017
ms.assetid: 6a94c834-2e32-4bed-9f47-ae5845eef6ff
ms.openlocfilehash: 7f189e4d1811cb0b7dd9138b944bfd0552481690
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43743749"
---
# <a name="simple-policy"></a><span data-ttu-id="e215b-102">Proste zasady</span><span class="sxs-lookup"><span data-stu-id="e215b-102">Simple Policy</span></span>
<span data-ttu-id="e215b-103">Ten przykład ilustruje sposób używania <xref:System.Workflow.Activities.PolicyActivity> działania w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="e215b-103">This sample shows how to use a <xref:System.Workflow.Activities.PolicyActivity> activity in a workflow.</span></span>  
  
 <span data-ttu-id="e215b-104">Sekwencyjny przepływ pracy w tym przykładzie jest tworzona przy użyciu <xref:System.Workflow.Activities.PolicyActivity> działania.</span><span class="sxs-lookup"><span data-stu-id="e215b-104">The sequential workflow in this sample is created by using a <xref:System.Workflow.Activities.PolicyActivity> activity.</span></span> <span data-ttu-id="e215b-105">Przepływ pracy określa `orderValue`, `customerType`, i `discount` pola, które są używane do definiowania produkt z rabatami przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="e215b-105">The workflow defines `orderValue`, `customerType`, and `discount` fields that are used to define a product discount workflow.</span></span> <span data-ttu-id="e215b-106">Od reguł zdefiniowanych w pliku reguł ustaw wartość Rabat na wersję, która opiera się na `orderValue` i `customerType`.</span><span class="sxs-lookup"><span data-stu-id="e215b-106">The rules defined in the rules file set a discount value that is based on the `orderValue` and `customerType`.</span></span> <span data-ttu-id="e215b-107">`orderValue` i `customerType` są ustawiane w `SimplePolicyWorkflow` definicji klasy i można ją zmienić na zmiany zachowania.</span><span class="sxs-lookup"><span data-stu-id="e215b-107">The `orderValue` and `customerType` are set in the `SimplePolicyWorkflow` class definition and can be changed to alter the behavior.</span></span> <span data-ttu-id="e215b-108">Rabat wynikowe są zapisywane do konsoli w <xref:System.Workflow.Runtime.WorkflowRuntime.WorkflowCompleted> programu obsługi zdarzeń, która jest zdefiniowana w `SimplePolicyWorkflow` klasy.</span><span class="sxs-lookup"><span data-stu-id="e215b-108">The resulting discount is written to the console in the <xref:System.Workflow.Runtime.WorkflowRuntime.WorkflowCompleted> event handler that is defined in the `SimplePolicyWorkflow` class.</span></span>  
  
### <a name="to-build-the-sample"></a><span data-ttu-id="e215b-109">Aby skompilować przykład</span><span class="sxs-lookup"><span data-stu-id="e215b-109">To build the sample</span></span>  
  
1.  <span data-ttu-id="e215b-110">Otwórz rozwiązanie w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e215b-110">Open the solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="e215b-111">Skompiluj rozwiązanie, naciskając klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="e215b-111">Build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="e215b-112">Uruchom rozwiązanie bez debugowania, naciskając klawisze CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="e215b-112">Run the solution without debugging by pressing CTRL+F5.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="e215b-113">Aby uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="e215b-113">To run the sample</span></span>  
  
-   <span data-ttu-id="e215b-114">W oknie wiersza polecenia zestawu SDK Uruchom plik .exe w folderze SimplePolicy\bin\debug (lub folder SimplePolicy\bin wersję przykładu w Visual Basic), który znajduje się poniżej głównego folderu dla przykładu.</span><span class="sxs-lookup"><span data-stu-id="e215b-114">In the SDK Command Prompt window, run the .exe file in the SimplePolicy\bin\debug folder (or the SimplePolicy\bin folder for the Visual Basic version of the sample), which is located below the main folder for the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e215b-115">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="e215b-115">The samples may already be installed on your computer.</span></span> <span data-ttu-id="e215b-116">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne):</span><span class="sxs-lookup"><span data-stu-id="e215b-116">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e215b-117">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="e215b-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e215b-118">W tym przykładzie znajduje się w następującym katalogu:</span><span class="sxs-lookup"><span data-stu-id="e215b-118">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\SimplePolicy`  
  
## <a name="see-also"></a><span data-ttu-id="e215b-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e215b-119">See Also</span></span>  
 <xref:System.Workflow.Activities.Rules.RuleSet>  
 <xref:System.Workflow.Activities.PolicyActivity>  
 [<span data-ttu-id="e215b-120">Zasady zaawansowane</span><span class="sxs-lookup"><span data-stu-id="e215b-120">Advanced Policy</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/advanced-policy.md)
