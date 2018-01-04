---
title: OperationScope
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56206a21-1e63-422d-b92a-e5d8b713e707
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 837be2de516f604dd6869449d99df238fb6dbd24
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="operationscope"></a><span data-ttu-id="b8bf8-102">OperationScope</span><span class="sxs-lookup"><span data-stu-id="b8bf8-102">OperationScope</span></span>
<span data-ttu-id="b8bf8-103">W przykładzie pokazano sposób działania, do obsługi komunikatów <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply> można użyć do udostępnienia istniejących działań niestandardowych jako operacji w usłudze przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="b8bf8-103">This sample demonstrates how the messaging activities, <xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply> can be used to expose an existing custom activity as an operation in a workflow service.</span></span> <span data-ttu-id="b8bf8-104">Ten przykład zawiera nowe niestandardowe działanie o nazwie `OperationScope`.</span><span class="sxs-lookup"><span data-stu-id="b8bf8-104">This sample includes a new custom activity called an `OperationScope`.</span></span> <span data-ttu-id="b8bf8-105">Jest on przeznaczony do jej obsługi ułatwiają tworzenie usługi przepływu pracy zezwolenie użytkownikom na tworzenie treści prace oddzielnie jako działań niestandardowych, a następnie łatwe udostępnianie je jako operacje usługi przy użyciu `OperationScope` działania.</span><span class="sxs-lookup"><span data-stu-id="b8bf8-105">It is intended to ease the development of a workflow service by allowing users to author the body of their operations separately as custom activities and then easily exposing them as service operations using the `OperationScope` activity.</span></span> <span data-ttu-id="b8bf8-106">Na przykład niestandardowy `Add` działania, która przyjmuje dwa `in` argumentów i zwraca jedną `out` argument może być udostępniany jako `Add` operacji w usłudze przepływu pracy, przeciągając go do `OperationScope`.</span><span class="sxs-lookup"><span data-stu-id="b8bf8-106">For example, a custom `Add` activity that takes two `in` arguments and returns one `out` argument could be exposed as an `Add` operation on the workflow service by dropping it into an `OperationScope`.</span></span>  
  
 <span data-ttu-id="b8bf8-107">Zakres działa sprawdzając działania w jego treści.</span><span class="sxs-lookup"><span data-stu-id="b8bf8-107">The scope works by inspecting the activity provided as its body.</span></span> <span data-ttu-id="b8bf8-108">Wszelkie niepowiązane `in` argumenty są uważane za dane wejściowe z komunikatu przychodzącego.</span><span class="sxs-lookup"><span data-stu-id="b8bf8-108">Any unbound `in` arguments are assumed to be inputs from the incoming message.</span></span> <span data-ttu-id="b8bf8-109">Wszystkie `out` argumentów, niezależnie od tego, czy są powiązane są uważane za dane wyjściowe w kolejnych odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="b8bf8-109">All `out` arguments, regardless of whether they are bound, are assumed to be outputs in the subsequent reply message.</span></span> <span data-ttu-id="b8bf8-110">Nazwa operacji narażonych jest pobierana z nazwę wyświetlaną `OperationScope` działania.</span><span class="sxs-lookup"><span data-stu-id="b8bf8-110">The exposed operation’s name is taken from the display name of the `OperationScope` activity.</span></span> <span data-ttu-id="b8bf8-111">W rezultacie jest, że działanie treści jest ujęte w <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply> z parametrami z wiadomości powiązany z argumentów działania.</span><span class="sxs-lookup"><span data-stu-id="b8bf8-111">The end result is that the body activity is wrapped in a <xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply> with the parameters from the messages bound to the arguments of the activity.</span></span>  
  
 <span data-ttu-id="b8bf8-112">Ten przykład przedstawia usługi przepływu pracy przy użyciu punktów końcowych HTTP.</span><span class="sxs-lookup"><span data-stu-id="b8bf8-112">This sample exposes a workflow service using HTTP endpoints.</span></span> <span data-ttu-id="b8bf8-113">Do uruchomienia, muszą zostać dodane odpowiednie listy ACL adresu URL.</span><span class="sxs-lookup"><span data-stu-id="b8bf8-113">To run, proper URL ACLs must be added.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="b8bf8-114">[Konfigurowanie protokołów HTTP i HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353).</span><span class="sxs-lookup"><span data-stu-id="b8bf8-114"> [Configuring HTTP and HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353).</span></span> <span data-ttu-id="b8bf8-115">Wykonując następujące polecenie w wierszu polecenia z podwyższonym poziomem uprawnień dodaje odpowiednich list ACL (Upewnij się, że Twoje domena i nazwa użytkownika są zastępowane dla domeny %\\% UserName %).</span><span class="sxs-lookup"><span data-stu-id="b8bf8-115">Executing the following command at an elevated prompt adds the appropriate ACLs (ensure that your Domain and Username are substituted for %DOMAIN%\\%UserName%).</span></span>  
  
 <span data-ttu-id="b8bf8-116">**netsh http Dodaj adres url urlacl = http: / / +: 8000 / użytkownika domeny % =\\% UserName %**</span><span class="sxs-lookup"><span data-stu-id="b8bf8-116">**netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\\%UserName%**</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="b8bf8-117">Aby uruchomić przykładowy</span><span class="sxs-lookup"><span data-stu-id="b8bf8-117">To run the sample</span></span>  
  
1.  <span data-ttu-id="b8bf8-118">Otwórz rozwiązanie OperationScope.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b8bf8-118">Open the OperationScope.sln solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="b8bf8-119">Ustawianie wielu projektów uruchamiania prawym przyciskiem myszy rozwiązanie w Eksploratorze rozwiązań i wybierając **Ustaw projekty startowe**.</span><span class="sxs-lookup"><span data-stu-id="b8bf8-119">Set multiple start-up projects by right-clicking the solution in Solution Explorer and selecting **Set Startup Projects**.</span></span> <span data-ttu-id="b8bf8-120">Dodawanie scenariuszy i Scenario_Client (w tej kolejności) jako wiele projektów rozruchu.</span><span class="sxs-lookup"><span data-stu-id="b8bf8-120">Add Scenario and Scenario_Client (in that order) as multiple start-up projects.</span></span>  
  
3.  <span data-ttu-id="b8bf8-121">Naciśnij klawisze CTRL + SHIFT + B w celu skompilowania rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="b8bf8-121">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="b8bf8-122">Ten krok jest wymagany do wyświetlania BankService.xaml przepływu pracy z powodu działań niestandardowych `OperationScope`.</span><span class="sxs-lookup"><span data-stu-id="b8bf8-122">This step is required to view the BankService.xaml workflow due to the custom activity `OperationScope`.</span></span>  
  
4.  <span data-ttu-id="b8bf8-123">Naciśnij klawisze CTRL + F5, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="b8bf8-123">Press CTRL+F5 to run the application.</span></span> <span data-ttu-id="b8bf8-124">Konsoli Scenario_Client wyświetla monit o podanie danych wejściowych i odpowiednie dane wyjściowe jest widoczne w konsoli scenariusza.</span><span class="sxs-lookup"><span data-stu-id="b8bf8-124">The Scenario_Client console prompts you for inputs and the corresponding output is seen in the Scenario console.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b8bf8-125">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="b8bf8-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b8bf8-126">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="b8bf8-126">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b8bf8-127">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="b8bf8-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b8bf8-128">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="b8bf8-128">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\OperationScope`