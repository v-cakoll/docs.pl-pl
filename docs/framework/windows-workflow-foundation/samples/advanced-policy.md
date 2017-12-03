---
title: Zaawansowane zasady
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 75a22c88-5e54-4ae8-84cb-fbb22a612f0a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b9752b5779f4fbb525488e88f2f11c98de7b4ba8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="advanced-policy"></a><span data-ttu-id="4cdb4-102">Zaawansowane zasady</span><span class="sxs-lookup"><span data-stu-id="4cdb4-102">Advanced Policy</span></span>
<span data-ttu-id="4cdb4-103">W tym przykładzie rozszerza próbki proste zasady.</span><span class="sxs-lookup"><span data-stu-id="4cdb4-103">This sample extends the Simple Policy sample.</span></span> <span data-ttu-id="4cdb4-104">Oprócz rabat lokalną i reguły biznesowe rabatem w przykładzie proste zasady dodano kilka nowych zasad.</span><span class="sxs-lookup"><span data-stu-id="4cdb4-104">In addition to the residential discount and business discount rules from the Simple Policy example, several new rules have been added.</span></span>  
  
 <span data-ttu-id="4cdb4-105">Dodana reguła wysokiej wartości, co umożliwia większy rabat zamówień wysokiej wartości.</span><span class="sxs-lookup"><span data-stu-id="4cdb4-105">A high-value rule is added, which provides a bigger discount for high-value orders.</span></span> <span data-ttu-id="4cdb4-106">Jest podana wartość priorytetu jest mniejsza niż dwoma poprzednimi zasady tak, aby będzie Zastąp pole Rabat i mieć pierwszeństwo nad zarówno lokalną i reguły biznesowe rabatów.</span><span class="sxs-lookup"><span data-stu-id="4cdb4-106">It is given a priority value less than the previous two rules so that it will overwrite the discount field and take precedence over both the residential and business discount rules.</span></span>  
  
 <span data-ttu-id="4cdb4-107">Oblicz reguły całkowita jest także dodawane, który oblicza łączną liczbę na podstawie poziomu rabatów.</span><span class="sxs-lookup"><span data-stu-id="4cdb4-107">A calculate total rule is also added, which computes the total based on the discount level.</span></span> <span data-ttu-id="4cdb4-108">Pokazuje sposób odwołania do metody zdefiniowanej w działaniu przepływu pracy, jak również sposób użycia innego działania.</span><span class="sxs-lookup"><span data-stu-id="4cdb4-108">It shows how to reference a method defined on the workflow activity, as well as how to use else actions.</span></span> <span data-ttu-id="4cdb4-109">Ta zasada przedstawiono również łańcucha zachowanie, ponieważ będzie ona oceniane w każdej chwili zmiany pola rabatów.</span><span class="sxs-lookup"><span data-stu-id="4cdb4-109">This rule also demonstrates chaining behavior since it will be evaluated anytime the discount field changes.</span></span> <span data-ttu-id="4cdb4-110">Ponadto metoda przypisywanie powoduje wyświetlanie RuleWriteAttribute dla metody CalculateTotal.</span><span class="sxs-lookup"><span data-stu-id="4cdb4-110">Furthermore, method attributing is shown with the RuleWriteAttribute on the CalculateTotal method.</span></span> <span data-ttu-id="4cdb4-111">Powoduje to wpływ na reguły (ErrorTotalRule) do ponownego obliczenia zawsze, gdy metoda jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="4cdb4-111">This causes impacted rules (ErrorTotalRule) to be re-evaluated whenever the method gets executed.</span></span>  
  
 <span data-ttu-id="4cdb4-112">Ostatnia reguła dodaje to taki, który wykryje błędy (w tym przypadku Suma mniejszą od 0).</span><span class="sxs-lookup"><span data-stu-id="4cdb4-112">The last rule added is one that detects errors (in this case, Total less than 0).</span></span> <span data-ttu-id="4cdb4-113">W takim przypadku jest zatrzymywane wykonywanie zasad.</span><span class="sxs-lookup"><span data-stu-id="4cdb4-113">If this occurs, the policy execution is halted.</span></span>  
  
 <span data-ttu-id="4cdb4-114">Na koniec `Console.Writeline` wywołania są dodawane jako akcje do każdej reguły, aby zapewnić lepszą widoczność do wykonywania reguł, podczas pokazywania również, czy istnieje możliwość dostępu do metody statyczne na odwołuje się do typów.</span><span class="sxs-lookup"><span data-stu-id="4cdb4-114">Finally, `Console.Writeline` calls are added as actions to each rule to provide more visibility into rule execution, while also showing that it is possible to access static methods on referenced types.</span></span> <span data-ttu-id="4cdb4-115">Aby uzyskać informacje na reguły, które są wykonywane, można użyć również śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4cdb4-115">You could also use tracking to get visibility into the rules that are executed.</span></span>  
  
 <span data-ttu-id="4cdb4-116">Dostępne są następujące reguły używane w tym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="4cdb4-116">The rules used in this sample are:</span></span>  
  
 <span data-ttu-id="4cdb4-117">**ResidentialDiscountRule:**</span><span class="sxs-lookup"><span data-stu-id="4cdb4-117">**ResidentialDiscountRule:**</span></span>  
  
 <span data-ttu-id="4cdb4-118">Jeśli OrderValue > 500 i CustomerType = lokalną</span><span class="sxs-lookup"><span data-stu-id="4cdb4-118">IF OrderValue > 500 AND CustomerType = Residential</span></span>  
  
 <span data-ttu-id="4cdb4-119">NASTĘPNIE rabat = 5%</span><span class="sxs-lookup"><span data-stu-id="4cdb4-119">THEN Discount = 5%</span></span>  
  
 <span data-ttu-id="4cdb4-120">**BusinessDiscountRule:**</span><span class="sxs-lookup"><span data-stu-id="4cdb4-120">**BusinessDiscountRule:**</span></span>  
  
 <span data-ttu-id="4cdb4-121">Jeśli OrderValue > 10000 i CustomerType = biznesowa</span><span class="sxs-lookup"><span data-stu-id="4cdb4-121">IF OrderValue > 10000 AND CustomerType = Business</span></span>  
  
 <span data-ttu-id="4cdb4-122">NASTĘPNIE rabat = 10%</span><span class="sxs-lookup"><span data-stu-id="4cdb4-122">THEN Discount = 10%</span></span>  
  
 <span data-ttu-id="4cdb4-123">**HighValueDiscountRule:**</span><span class="sxs-lookup"><span data-stu-id="4cdb4-123">**HighValueDiscountRule:**</span></span>  
  
 <span data-ttu-id="4cdb4-124">Jeśli OrderValue > 20000</span><span class="sxs-lookup"><span data-stu-id="4cdb4-124">IF OrderValue > 20000</span></span>  
  
 <span data-ttu-id="4cdb4-125">NASTĘPNIE rabat = 15%</span><span class="sxs-lookup"><span data-stu-id="4cdb4-125">THEN Discount = 15%</span></span>  
  
 <span data-ttu-id="4cdb4-126">**TotalRule:**</span><span class="sxs-lookup"><span data-stu-id="4cdb4-126">**TotalRule:**</span></span>  
  
 <span data-ttu-id="4cdb4-127">Jeśli Discount > 0.</span><span class="sxs-lookup"><span data-stu-id="4cdb4-127">IF Discount > 0</span></span>  
  
 <span data-ttu-id="4cdb4-128">NASTĘPNIE CalculateTotal (OrderValue dyskontowa)</span><span class="sxs-lookup"><span data-stu-id="4cdb4-128">THEN CalculateTotal(OrderValue, Discount)</span></span>  
  
 <span data-ttu-id="4cdb4-129">Suma ELSE = OrderValue</span><span class="sxs-lookup"><span data-stu-id="4cdb4-129">ELSE Total = OrderValue</span></span>  
  
 <span data-ttu-id="4cdb4-130">**ErrorTotalRule:**</span><span class="sxs-lookup"><span data-stu-id="4cdb4-130">**ErrorTotalRule:**</span></span>  
  
 <span data-ttu-id="4cdb4-131">Jeśli całkowita \< 0</span><span class="sxs-lookup"><span data-stu-id="4cdb4-131">IF Total \< 0</span></span>  
  
 <span data-ttu-id="4cdb4-132">NASTĘPNIE błąd = "Uruchamiany ErrorTotalRule;" Zatrzymanie</span><span class="sxs-lookup"><span data-stu-id="4cdb4-132">THEN Error = "Fired ErrorTotalRule"; Halt</span></span>  
  
 <span data-ttu-id="4cdb4-133">Szacowanie reguły i wykonywanie znajdują się również za pośrednictwem śledzenia i śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4cdb4-133">Rule evaluation and execution can also be seen through tracing and tracking.</span></span>  
  
### <a name="to-build-the-sample"></a><span data-ttu-id="4cdb4-134">Aby samodzielnie tworzyć przykładowy</span><span class="sxs-lookup"><span data-stu-id="4cdb4-134">To build the sample</span></span>  
  
1.  <span data-ttu-id="4cdb4-135">Otwórz rozwiązanie w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4cdb4-135">Open the solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="4cdb4-136">Skompiluj rozwiązanie, naciskając klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="4cdb4-136">Build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="4cdb4-137">Uruchom rozwiązania bez debugowania, naciskając klawisze CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="4cdb4-137">Run the solution without debugging by pressing CTRL+F5.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="4cdb4-138">Aby uruchomić przykładowy</span><span class="sxs-lookup"><span data-stu-id="4cdb4-138">To run the sample</span></span>  
  
-   <span data-ttu-id="4cdb4-139">W oknie wiersza polecenia zestawu SDK Uruchom plik .exe w folderze AdvancedPolicy\bin\debug (lub w folderze \bin AdvancedPolicy dla używanej wersji programu Visual Basic przykładu) znajdujący się poniżej głównego folderu przykładowej.</span><span class="sxs-lookup"><span data-stu-id="4cdb4-139">In the SDK Command Prompt window, run the .exe file in the AdvancedPolicy\bin\debug folder (or the AdvancedPolicy \bin folder for the Visual Basic version of the sample), which is located below the main folder for the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4cdb4-140">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="4cdb4-140">The samples may already be installed on your computer.</span></span> <span data-ttu-id="4cdb4-141">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne):</span><span class="sxs-lookup"><span data-stu-id="4cdb4-141">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4cdb4-142">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="4cdb4-142">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4cdb4-143">W tym przykładzie znajduje się w następującym katalogu:</span><span class="sxs-lookup"><span data-stu-id="4cdb4-143">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\AdvancedPolicy`  
  
## <a name="see-also"></a><span data-ttu-id="4cdb4-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4cdb4-144">See Also</span></span>  
 <xref:System.Workflow.Activities.Rules.RuleSet>  
 <xref:System.Workflow.Activities.PolicyActivity>  
 [<span data-ttu-id="4cdb4-145">Proste zasad</span><span class="sxs-lookup"><span data-stu-id="4cdb4-145">Simple Policy</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/simple-policy.md)
