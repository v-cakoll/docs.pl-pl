---
title: Działanie IfElse za pomocą reguł
ms.date: 03/30/2017
ms.assetid: c4ad9bb2-9037-413a-8b14-59ed7b927a9e
ms.openlocfilehash: 31906f04149a0ca7659201965ca565c7fa2af305
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43500532"
---
# <a name="ifelse-with-rules"></a><span data-ttu-id="339b8-102">Działanie IfElse za pomocą reguł</span><span class="sxs-lookup"><span data-stu-id="339b8-102">IfElse With Rules</span></span>
<span data-ttu-id="339b8-103">W tym przykładzie przedstawiono użycie warunku reguły z <xref:System.Workflow.Activities.IfElseActivity> działania.</span><span class="sxs-lookup"><span data-stu-id="339b8-103">This sample shows the use of a rule condition with an <xref:System.Workflow.Activities.IfElseActivity> activity.</span></span>  
  
 <span data-ttu-id="339b8-104">Przykład przekazuje `OrderValue` parametru z hosta.</span><span class="sxs-lookup"><span data-stu-id="339b8-104">The sample passes in an `OrderValue` parameter from the host.</span></span> <span data-ttu-id="339b8-105">Wartość parametru jest używana w warunku reguły w pierwszej gałęzi <xref:System.Workflow.Activities.IfElseActivity> działania.</span><span class="sxs-lookup"><span data-stu-id="339b8-105">The value of the parameter is used in a rule condition on the first branch of the <xref:System.Workflow.Activities.IfElseActivity> activity.</span></span> <span data-ttu-id="339b8-106">Jeśli wartość jest mniejsza niż 10 000, wykonuje pierwszej gałęzi i <xref:System.Workflow.Activities.CodeActivity> drukuje działania w pierwszej gałęzi **Pobierz menedżera o zatwierdzenie** do konsoli.</span><span class="sxs-lookup"><span data-stu-id="339b8-106">If the value is less than 10,000, the first branch executes, and the <xref:System.Workflow.Activities.CodeActivity> activity in the first branch prints **Get Manager Approval** to the console.</span></span> <span data-ttu-id="339b8-107">Jeśli wartość jest większa niż 10 000, <xref:System.Workflow.Activities.CodeActivity> działania w drugim gałęzi wykonuje i drukuje **Rozpoczynanie zatwierdzenia VP**.</span><span class="sxs-lookup"><span data-stu-id="339b8-107">If the value is greater than 10,000, the <xref:System.Workflow.Activities.CodeActivity> activity in the second branch executes and prints **Get VP Approval**.</span></span>  
  
### <a name="to-build-the-sample"></a><span data-ttu-id="339b8-108">Aby skompilować przykład</span><span class="sxs-lookup"><span data-stu-id="339b8-108">To build the sample</span></span>  
  
1.  <span data-ttu-id="339b8-109">Otwórz rozwiązanie w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="339b8-109">Open the solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="339b8-110">Skompiluj rozwiązanie, naciskając klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="339b8-110">Build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="339b8-111">Uruchom rozwiązanie bez debugowania, naciskając klawisze CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="339b8-111">Run the solution without debugging by pressing CTRL+F5.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="339b8-112">Aby uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="339b8-112">To run the sample</span></span>  
  
-   <span data-ttu-id="339b8-113">W oknie wiersza polecenia zestawu SDK Uruchom plik .exe w folderze IfElseWithRules\bin\debug (lub folder IfElseWithRules\bin wersję przykładu w Visual Basic), który znajduje się poniżej głównego folderu dla przykładu.</span><span class="sxs-lookup"><span data-stu-id="339b8-113">In the SDK Command Prompt window, run the .exe file in the IfElseWithRules\bin\debug folder (or the IfElseWithRules\bin folder for the Visual Basic version of the sample), which is located below the main folder for the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="339b8-114">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="339b8-114">The samples may already be installed on your computer.</span></span> <span data-ttu-id="339b8-115">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne):</span><span class="sxs-lookup"><span data-stu-id="339b8-115">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="339b8-116">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="339b8-116">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="339b8-117">W tym przykładzie znajduje się w następującym katalogu:</span><span class="sxs-lookup"><span data-stu-id="339b8-117">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\IfElseWithRules`  
  
## <a name="see-also"></a><span data-ttu-id="339b8-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="339b8-118">See Also</span></span>  
 <xref:System.Workflow.Activities.Rules>  
 <xref:System.Workflow.Activities.IfElseActivity>  
 <xref:System.Workflow.Activities.CodeActivity>  
 <xref:System.Workflow.Activities.Rules.RuleDefinitions>
