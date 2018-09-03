---
title: OverloadGroups
ms.date: 03/30/2017
ms.assetid: d1d547d2-f5fb-4de3-a959-ee6139a4f1ad
ms.openlocfilehash: 0773e76d36b25ad5485cc8912c7012815412de9f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2018
ms.locfileid: "43469872"
---
# <a name="overloadgroups"></a><span data-ttu-id="0bb18-102">OverloadGroups</span><span class="sxs-lookup"><span data-stu-id="0bb18-102">OverloadGroups</span></span>
<span data-ttu-id="0bb18-103">W tym przykładzie składa się z działania (`CreateLocation`), który ma dwa interesujące cechy:</span><span class="sxs-lookup"><span data-stu-id="0bb18-103">This sample consists of an activity (`CreateLocation`), which has two interesting characteristics:</span></span>  
  
1.  <span data-ttu-id="0bb18-104">Jest to niektóre wymagane argumenty i opcjonalnie niektóre z nich.</span><span class="sxs-lookup"><span data-stu-id="0bb18-104">It has some required arguments and some optional ones.</span></span>  
  
2.  <span data-ttu-id="0bb18-105">Umożliwia użytkownikowi określenie podać jedną z dwóch różnych zestawów argumentów.</span><span class="sxs-lookup"><span data-stu-id="0bb18-105">It allows the user to choose to provide one of two different sets of arguments.</span></span>  
  
 <span data-ttu-id="0bb18-106">Te zachowania, są wykonywane za pomocą te dwie funkcje:</span><span class="sxs-lookup"><span data-stu-id="0bb18-106">These behaviors are accomplished by using these two features:</span></span>  
  
-   <span data-ttu-id="0bb18-107">`[isRequired]` weryfikuje, że właściwość określonego działania jest przypisywanie, a jeśli nie, zgłosi wyjątek.</span><span class="sxs-lookup"><span data-stu-id="0bb18-107">`[isRequired]` validates that a property of a specific activity is assign, and if not, it throws an exception.</span></span>  
  
-   <span data-ttu-id="0bb18-108">`[OverloadGroup]` umieszcza razem zestawu argumentów, tak, aby wybrać przy użyciu jednego zestawu, lub inny użytkownik działania.</span><span class="sxs-lookup"><span data-stu-id="0bb18-108">`[OverloadGroup]` puts together a set of arguments, so that the user of the activity can choose between using one set or another.</span></span> <span data-ttu-id="0bb18-109">Użytkownik nie może używać argumentów z różnych grup przeciążenie to samo wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="0bb18-109">The user cannot use arguments from different Overload Groups in the same instance.</span></span>  
  
 <span data-ttu-id="0bb18-110">Po skonfigurowaniu różnych przepływów pracy, należy wywołać <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> co powoduje zwrócenie <xref:System.Activities.Validation.ValidationResults> zbiór <xref:System.Activities.Validation.Constraint>.</span><span class="sxs-lookup"><span data-stu-id="0bb18-110">After setting up different workflows, call <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> which returns a <xref:System.Activities.Validation.ValidationResults> collection of <xref:System.Activities.Validation.Constraint>.</span></span> <span data-ttu-id="0bb18-111">Drukuj <xref:System.Activities.Validation.Constraint> obiekty do konsoli.</span><span class="sxs-lookup"><span data-stu-id="0bb18-111">Print the <xref:System.Activities.Validation.Constraint> objects to the console.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0bb18-112">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="0bb18-112">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="0bb18-113">Otwórz **OverloadGroups.sln** przykładowe rozwiązanie w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0bb18-113">Open the **OverloadGroups.sln** sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="0bb18-114">Skompiluj i uruchom rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="0bb18-114">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0bb18-115">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="0bb18-115">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0bb18-116">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="0bb18-116">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="0bb18-117">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="0bb18-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0bb18-118">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="0bb18-118">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\OverloadGroups`
