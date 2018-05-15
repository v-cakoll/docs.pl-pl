---
title: OverloadGroups
ms.date: 03/30/2017
ms.assetid: d1d547d2-f5fb-4de3-a959-ee6139a4f1ad
ms.openlocfilehash: 489d27e05c96d3b3893052254a879d1c9d75788c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="overloadgroups"></a><span data-ttu-id="da0d3-102">OverloadGroups</span><span class="sxs-lookup"><span data-stu-id="da0d3-102">OverloadGroups</span></span>
<span data-ttu-id="da0d3-103">W tym przykładzie składa się z działania (`CreateLocation`), który ma dwie właściwości interesujące:</span><span class="sxs-lookup"><span data-stu-id="da0d3-103">This sample consists of an activity (`CreateLocation`), which has two interesting characteristics:</span></span>  
  
1.  <span data-ttu-id="da0d3-104">Niektóre wymagane jej argumentów i niektóre z nich opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="da0d3-104">It has some required arguments and some optional ones.</span></span>  
  
2.  <span data-ttu-id="da0d3-105">Pozwala użytkownikowi na wybranie zapewnienie jeden z dwóch różnych zestawów argumentów.</span><span class="sxs-lookup"><span data-stu-id="da0d3-105">It allows the user to choose to provide one of two different sets of arguments.</span></span>  
  
 <span data-ttu-id="da0d3-106">Te zachowania, są wykonywane za pomocą te dwie funkcje:</span><span class="sxs-lookup"><span data-stu-id="da0d3-106">These behaviors are accomplished by using these two features:</span></span>  
  
-   <span data-ttu-id="da0d3-107">`[isRequired]` weryfikuje, że właściwość określonego działania jest przypisywanie, a jeśli nie, zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="da0d3-107">`[isRequired]` validates that a property of a specific activity is assign, and if not, it throws an exception.</span></span>  
  
-   <span data-ttu-id="da0d3-108">`[OverloadGroup]` umieszcza razem zestaw argumentów, dzięki czemu można wybrać za pomocą jednego zestawu, lub inny użytkownik działania.</span><span class="sxs-lookup"><span data-stu-id="da0d3-108">`[OverloadGroup]` puts together a set of arguments, so that the user of the activity can choose between using one set or another.</span></span> <span data-ttu-id="da0d3-109">Użytkownik nie można używać argumentów z różnych grup przeciążenia, w tym samym wystąpieniu.</span><span class="sxs-lookup"><span data-stu-id="da0d3-109">The user cannot use arguments from different Overload Groups in the same instance.</span></span>  
  
 <span data-ttu-id="da0d3-110">Po skonfigurowaniu różnych przepływów pracy, należy wywołać <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> co powoduje zwrócenie <xref:System.Activities.Validation.ValidationResults> kolekcji <xref:System.Activities.Validation.Constraint>.</span><span class="sxs-lookup"><span data-stu-id="da0d3-110">After setting up different workflows, call <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> which returns a <xref:System.Activities.Validation.ValidationResults> collection of <xref:System.Activities.Validation.Constraint>.</span></span> <span data-ttu-id="da0d3-111">Drukuj <xref:System.Activities.Validation.Constraint> obiekty do konsoli.</span><span class="sxs-lookup"><span data-stu-id="da0d3-111">Print the <xref:System.Activities.Validation.Constraint> objects to the console.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="da0d3-112">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="da0d3-112">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="da0d3-113">Otwórz **OverloadGroups.sln** przykładowe rozwiązanie w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="da0d3-113">Open the **OverloadGroups.sln** sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="da0d3-114">Tworzenie i uruchamianie rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="da0d3-114">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="da0d3-115">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="da0d3-115">The samples may already be installed on your machine.</span></span> <span data-ttu-id="da0d3-116">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="da0d3-116">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="da0d3-117">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="da0d3-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="da0d3-118">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="da0d3-118">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\OverloadGroups`
