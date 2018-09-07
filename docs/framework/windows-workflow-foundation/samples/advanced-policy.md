---
title: Zaawansowane zasady
ms.date: 03/30/2017
ms.assetid: 75a22c88-5e54-4ae8-84cb-fbb22a612f0a
ms.openlocfilehash: becdc28affd877239474d6f0f007a480297bccb8
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44083793"
---
# <a name="advanced-policy"></a><span data-ttu-id="4d8c7-102">Zaawansowane zasady</span><span class="sxs-lookup"><span data-stu-id="4d8c7-102">Advanced Policy</span></span>
<span data-ttu-id="4d8c7-103">W tym przykładzie rozszerza przykładowe proste zasady.</span><span class="sxs-lookup"><span data-stu-id="4d8c7-103">This sample extends the Simple Policy sample.</span></span> <span data-ttu-id="4d8c7-104">Oprócz rabat na wersję lokalną i zniżki firm z przykładu proste zasady dodano kilka nowych zasad.</span><span class="sxs-lookup"><span data-stu-id="4d8c7-104">In addition to the residential discount and business discount rules from the Simple Policy example, several new rules have been added.</span></span>  
  
 <span data-ttu-id="4d8c7-105">Dodano regułę o wysokiej wartości, co umożliwia większym rabatem zamówienia o wysokiej wartości.</span><span class="sxs-lookup"><span data-stu-id="4d8c7-105">A high-value rule is added, which provides a bigger discount for high-value orders.</span></span> <span data-ttu-id="4d8c7-106">Otrzymuje wartość priorytetu jest mniejsza niż dwie poprzednie reguły tak, aby będzie Zastąp pole Rabat na wersję i mieć pierwszeństwo nad zarówno lokalną i zniżki biznesowych.</span><span class="sxs-lookup"><span data-stu-id="4d8c7-106">It is given a priority value less than the previous two rules so that it will overwrite the discount field and take precedence over both the residential and business discount rules.</span></span>  
  
 <span data-ttu-id="4d8c7-107">Oblicz całkowity reguły jest także dodawane, który oblicza sumę, zależnie od poziomu rabat w wysokości.</span><span class="sxs-lookup"><span data-stu-id="4d8c7-107">A calculate total rule is also added, which computes the total based on the discount level.</span></span> <span data-ttu-id="4d8c7-108">Pokazuje, jak odwoływać się do metody zdefiniowanej w działaniu przepływu pracy, a także jak używać innego działania.</span><span class="sxs-lookup"><span data-stu-id="4d8c7-108">It shows how to reference a method defined on the workflow activity, as well as how to use else actions.</span></span> <span data-ttu-id="4d8c7-109">Ta zasada przedstawia również, że łańcuch zachowanie, ponieważ będzie on oceniane dowolnym zmiany pola Rabat w wysokości.</span><span class="sxs-lookup"><span data-stu-id="4d8c7-109">This rule also demonstrates chaining behavior since it will be evaluated anytime the discount field changes.</span></span> <span data-ttu-id="4d8c7-110">Ponadto przypisywanie metody jest wyświetlana przy użyciu RuleWriteAttribute metody CalculateTotal.</span><span class="sxs-lookup"><span data-stu-id="4d8c7-110">Furthermore, method attributing is shown with the RuleWriteAttribute on the CalculateTotal method.</span></span> <span data-ttu-id="4d8c7-111">Powoduje to reguły których to dotyczy (ErrorTotalRule), który ma zostać ponownie obliczone zawsze wtedy, gdy pobiera wykonywania metody.</span><span class="sxs-lookup"><span data-stu-id="4d8c7-111">This causes impacted rules (ErrorTotalRule) to be re-evaluated whenever the method gets executed.</span></span>  
  
 <span data-ttu-id="4d8c7-112">Ostatnia reguła dodane to taki, który wykrywa błędy (w tym przypadku Suma mniejszą niż 0).</span><span class="sxs-lookup"><span data-stu-id="4d8c7-112">The last rule added is one that detects errors (in this case, Total less than 0).</span></span> <span data-ttu-id="4d8c7-113">W takiej sytuacji wykonywanie zasadach zostało zatrzymane.</span><span class="sxs-lookup"><span data-stu-id="4d8c7-113">If this occurs, the policy execution is halted.</span></span>  
  
 <span data-ttu-id="4d8c7-114">Na koniec `Console.Writeline` wywołania są dodawane jako akcji do każdej reguły, aby zapewnić lepszą widoczność do wykonywania reguły, podczas wyświetlania również, że możliwe jest dostęp do metod statycznych w przywoływane typy.</span><span class="sxs-lookup"><span data-stu-id="4d8c7-114">Finally, `Console.Writeline` calls are added as actions to each rule to provide more visibility into rule execution, while also showing that it is possible to access static methods on referenced types.</span></span> <span data-ttu-id="4d8c7-115">Można także użyć śledzenia Aby uzyskać wgląd w zasady, które są wykonywane.</span><span class="sxs-lookup"><span data-stu-id="4d8c7-115">You could also use tracking to get visibility into the rules that are executed.</span></span>  
  
 <span data-ttu-id="4d8c7-116">Dostępne są następujące reguły używane w tym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="4d8c7-116">The rules used in this sample are:</span></span>  
  
 <span data-ttu-id="4d8c7-117">**ResidentialDiscountRule:**</span><span class="sxs-lookup"><span data-stu-id="4d8c7-117">**ResidentialDiscountRule:**</span></span>  
  
 <span data-ttu-id="4d8c7-118">Jeśli OrderValue > 500 i CustomerType = zamieszkania</span><span class="sxs-lookup"><span data-stu-id="4d8c7-118">IF OrderValue > 500 AND CustomerType = Residential</span></span>  
  
 <span data-ttu-id="4d8c7-119">NASTĘPNIE rabat w wysokości = 5%</span><span class="sxs-lookup"><span data-stu-id="4d8c7-119">THEN Discount = 5%</span></span>  
  
 <span data-ttu-id="4d8c7-120">**BusinessDiscountRule:**</span><span class="sxs-lookup"><span data-stu-id="4d8c7-120">**BusinessDiscountRule:**</span></span>  
  
 <span data-ttu-id="4d8c7-121">Jeśli OrderValue > 10000 i CustomerType = biznesowych</span><span class="sxs-lookup"><span data-stu-id="4d8c7-121">IF OrderValue > 10000 AND CustomerType = Business</span></span>  
  
 <span data-ttu-id="4d8c7-122">NASTĘPNIE rabat w wysokości 10% =</span><span class="sxs-lookup"><span data-stu-id="4d8c7-122">THEN Discount = 10%</span></span>  
  
 <span data-ttu-id="4d8c7-123">**HighValueDiscountRule:**</span><span class="sxs-lookup"><span data-stu-id="4d8c7-123">**HighValueDiscountRule:**</span></span>  
  
 <span data-ttu-id="4d8c7-124">Jeśli OrderValue > 20000</span><span class="sxs-lookup"><span data-stu-id="4d8c7-124">IF OrderValue > 20000</span></span>  
  
 <span data-ttu-id="4d8c7-125">NASTĘPNIE rabat w wysokości = 15%</span><span class="sxs-lookup"><span data-stu-id="4d8c7-125">THEN Discount = 15%</span></span>  
  
 <span data-ttu-id="4d8c7-126">**TotalRule:**</span><span class="sxs-lookup"><span data-stu-id="4d8c7-126">**TotalRule:**</span></span>  
  
 <span data-ttu-id="4d8c7-127">Jeśli z rabatami > 0</span><span class="sxs-lookup"><span data-stu-id="4d8c7-127">IF Discount > 0</span></span>  
  
 <span data-ttu-id="4d8c7-128">NASTĘPNIE CalculateTotal (OrderValue rabatu)</span><span class="sxs-lookup"><span data-stu-id="4d8c7-128">THEN CalculateTotal(OrderValue, Discount)</span></span>  
  
 <span data-ttu-id="4d8c7-129">ELSE łącznie = OrderValue</span><span class="sxs-lookup"><span data-stu-id="4d8c7-129">ELSE Total = OrderValue</span></span>  
  
 <span data-ttu-id="4d8c7-130">**ErrorTotalRule:**</span><span class="sxs-lookup"><span data-stu-id="4d8c7-130">**ErrorTotalRule:**</span></span>  
  
 <span data-ttu-id="4d8c7-131">Jeśli łączna liczba \< 0</span><span class="sxs-lookup"><span data-stu-id="4d8c7-131">IF Total \< 0</span></span>  
  
 <span data-ttu-id="4d8c7-132">NASTĘPNIE błąd = "Wyzwolone ErrorTotalRule;" Zatrzymanie</span><span class="sxs-lookup"><span data-stu-id="4d8c7-132">THEN Error = "Fired ErrorTotalRule"; Halt</span></span>  
  
 <span data-ttu-id="4d8c7-133">Ocenę reguł i wykonywanie znajdują się również za pośrednictwem śledzenia i śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4d8c7-133">Rule evaluation and execution can also be seen through tracing and tracking.</span></span>  
  
### <a name="to-build-the-sample"></a><span data-ttu-id="4d8c7-134">Aby skompilować przykład</span><span class="sxs-lookup"><span data-stu-id="4d8c7-134">To build the sample</span></span>  
  
1.  <span data-ttu-id="4d8c7-135">Otwórz rozwiązanie w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4d8c7-135">Open the solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="4d8c7-136">Skompiluj rozwiązanie, naciskając klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="4d8c7-136">Build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="4d8c7-137">Uruchom rozwiązanie bez debugowania, naciskając klawisze CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="4d8c7-137">Run the solution without debugging by pressing CTRL+F5.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="4d8c7-138">Aby uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="4d8c7-138">To run the sample</span></span>  
  
-   <span data-ttu-id="4d8c7-139">W oknie wiersza polecenia zestawu SDK Uruchom plik .exe w folderze AdvancedPolicy\bin\debug (lub folder \bin AdvancedPolicy wersję przykładu w Visual Basic), który znajduje się poniżej głównego folderu dla przykładu.</span><span class="sxs-lookup"><span data-stu-id="4d8c7-139">In the SDK Command Prompt window, run the .exe file in the AdvancedPolicy\bin\debug folder (or the AdvancedPolicy \bin folder for the Visual Basic version of the sample), which is located below the main folder for the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4d8c7-140">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="4d8c7-140">The samples may already be installed on your computer.</span></span> <span data-ttu-id="4d8c7-141">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne):</span><span class="sxs-lookup"><span data-stu-id="4d8c7-141">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4d8c7-142">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="4d8c7-142">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4d8c7-143">W tym przykładzie znajduje się w następującym katalogu:</span><span class="sxs-lookup"><span data-stu-id="4d8c7-143">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\AdvancedPolicy`  
  
## <a name="see-also"></a><span data-ttu-id="4d8c7-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4d8c7-144">See Also</span></span>  
 <xref:System.Workflow.Activities.Rules.RuleSet>  
 <xref:System.Workflow.Activities.PolicyActivity>  
 [<span data-ttu-id="4d8c7-145">Proste zasady</span><span class="sxs-lookup"><span data-stu-id="4d8c7-145">Simple Policy</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/simple-policy.md)
