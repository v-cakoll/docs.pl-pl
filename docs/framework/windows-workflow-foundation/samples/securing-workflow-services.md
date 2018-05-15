---
title: Zabezpieczanie usług przepływu pracy
ms.date: 03/30/2017
ms.assetid: 53f84ad5-1ed1-4114-8d0d-b12e8a021c6e
ms.openlocfilehash: 5dbd724f3a2f8febfc74719584f4d69cbf75b567
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="securing-workflow-services"></a><span data-ttu-id="4abd7-102">Zabezpieczanie usług przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="4abd7-102">Securing Workflow Services</span></span>
<span data-ttu-id="4abd7-103">Przykład zabezpieczone usługi przepływu pracy obejmuje następujące procedury:</span><span class="sxs-lookup"><span data-stu-id="4abd7-103">The Secured Workflow Service sample shows the following procedures:</span></span>  
  
-   <span data-ttu-id="4abd7-104">Tworzenie usługi podstawowy przepływ pracy za pomocą <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply> działań.</span><span class="sxs-lookup"><span data-stu-id="4abd7-104">Creating a basic workflow service using the <xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply> activities.</span></span>  
  
-   <span data-ttu-id="4abd7-105">Za pomocą konfiguracji usługi Windows Communication Foundation (WCF) do definiowania bezpieczne punkty końcowe do użytku przez usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="4abd7-105">Using Windows Communication Foundation (WCF) configuration to define secure endpoints for use by the workflow service.</span></span>  
  
-   <span data-ttu-id="4abd7-106">Tworzenie oświadczeń wewnątrz zasadę niestandardową i korzystanie z <xref:System.ServiceModel.ServiceAuthorizationManager> do sprawdzenia.</span><span class="sxs-lookup"><span data-stu-id="4abd7-106">Creating claims inside a custom policy and using the <xref:System.ServiceModel.ServiceAuthorizationManager> to validate claims.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="4abd7-107">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="4abd7-107">Demonstrates</span></span>  
 <span data-ttu-id="4abd7-108">Przy użyciu zabezpieczeń WCF do zabezpieczania komunikacji między klientem a usługą przepływu pracy, na podstawie oświadczeń autoryzacji</span><span class="sxs-lookup"><span data-stu-id="4abd7-108">Using WCF security to secure communication between client and Workflow service, Claims based authorization</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="4abd7-109">Omówienie</span><span class="sxs-lookup"><span data-stu-id="4abd7-109">Discussion</span></span>  
 <span data-ttu-id="4abd7-110">W tym przykładzie przedstawiono korzystanie z infrastruktury zabezpieczeń WCF do zabezpieczania usługi przepływu pracy, tak jak normalne usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="4abd7-110">This sample demonstrates the use of WCF security infrastructure to secure a workflow service just like you would with a normal WCF service.</span></span> <span data-ttu-id="4abd7-111">W szczególności używa oświadczenia niestandardowego dla autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="4abd7-111">Specifically, it uses a custom claim for authorization.</span></span> <span data-ttu-id="4abd7-112">W takim przypadku używa <xref:System.ServiceModel.WSHttpBinding> i komunikatów tryb zabezpieczeń z poświadczeniami systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="4abd7-112">In this case, it uses <xref:System.ServiceModel.WSHttpBinding> and message mode security with Windows credentials.</span></span>  
  
 <span data-ttu-id="4abd7-113">Niestandardowa <xref:System.IdentityModel.Policy.IAuthorizationPolicy> (`CustomNameCheckerPolicy`) sprawdza nazwa użytkownika systemu Windows klienta i dla określonych znaków.</span><span class="sxs-lookup"><span data-stu-id="4abd7-113">The custom <xref:System.IdentityModel.Policy.IAuthorizationPolicy> (`CustomNameCheckerPolicy`) checks the client's Windows username and for a specific character.</span></span> <span data-ttu-id="4abd7-114">Jeśli ten znak jest obecny, tworzy i dodaje oświadczenie do <xref:System.IdentityModel.Policy.EvaluationContext>.</span><span class="sxs-lookup"><span data-stu-id="4abd7-114">If that character is present, it creates and adds the claim to the <xref:System.IdentityModel.Policy.EvaluationContext>.</span></span> <span data-ttu-id="4abd7-115">Dzięki temu zasady niestandardowe jest wprowadzenie instrukcji który klient ma tego znaku w nazwy użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4abd7-115">By doing this, the custom policy is making the statement that the client has this character in the username.</span></span> <span data-ttu-id="4abd7-116">Tego oświadczenia mogą być przeszukiwane przez cały okres istnienia połączenia.</span><span class="sxs-lookup"><span data-stu-id="4abd7-116">This claim can be queried throughout the lifetime of the call.</span></span> <span data-ttu-id="4abd7-117">Możesz znaleźć tego znaku w `Constants.cs`.</span><span class="sxs-lookup"><span data-stu-id="4abd7-117">You can find that character in `Constants.cs`.</span></span>  
  
 <span data-ttu-id="4abd7-118">Zasady autoryzacji szuka oświadczeń wewnątrz `SecureWorkFlowAuthZManager`.</span><span class="sxs-lookup"><span data-stu-id="4abd7-118">The authorization policy looks for the claim inside the `SecureWorkFlowAuthZManager`.</span></span> <span data-ttu-id="4abd7-119">Jeśli uzna, zwraca `true` i umożliwić przepływu pracy kontynuować.</span><span class="sxs-lookup"><span data-stu-id="4abd7-119">If it finds it, it returns `true` and allow the workflow to proceed.</span></span> <span data-ttu-id="4abd7-120">W przeciwnym razie zwraca `false`, co powoduje, że komunikat "Odmowa dostępu", ma zostać zwrócona do klienta.</span><span class="sxs-lookup"><span data-stu-id="4abd7-120">Otherwise, it returns `false`, which causes an 'Access Denied' message to be returned to the client.</span></span> <span data-ttu-id="4abd7-121">Pozostałe roszczenia znajdują się w kontekście i może sprawdzić, jak również wewnątrz `SecureWorkFlowAuthZManager`.</span><span class="sxs-lookup"><span data-stu-id="4abd7-121">Other claims are present in the context and can be examined as well inside the `SecureWorkFlowAuthZManager`.</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="4abd7-122">Aby uruchomić ten przykład</span><span class="sxs-lookup"><span data-stu-id="4abd7-122">To run this sample</span></span>  
  
1.  <span data-ttu-id="4abd7-123">Uruchom [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="4abd7-123">Run [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with administrator privileges.</span></span>  
  
2.  <span data-ttu-id="4abd7-124">Ładowanie SecuringWorkflowServices.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4abd7-124">Load SecuringWorkflowServices.sln in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
3.  <span data-ttu-id="4abd7-125">Naciśnij klawisze CTRL + SHIFT + B do skompilowania rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="4abd7-125">Press CTRL+SHIFT+B to compile the solution.</span></span>  
  
4.  <span data-ttu-id="4abd7-126">Ustaw projekt usługi jako projekt uruchamiania dla rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="4abd7-126">Set the Service project as the start-up project for the solution.</span></span>  
  
5.  <span data-ttu-id="4abd7-127">Naciśnij klawisze CTRL + F5, aby uruchomić usługę bez debugowania.</span><span class="sxs-lookup"><span data-stu-id="4abd7-127">Press CTRL+F5 to start the service without debugging.</span></span>  
  
6.  <span data-ttu-id="4abd7-128">Ustaw projekt klienta jako projekt uruchamiania dla rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="4abd7-128">Set the Client project as the start-up project for the solution.</span></span>  
  
7.  <span data-ttu-id="4abd7-129">Naciśnij klawisze CTRL + F5, aby uruchomić klienta bez debugowania.</span><span class="sxs-lookup"><span data-stu-id="4abd7-129">Press CTRL+F5 to start the client without debugging.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4abd7-130">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="4abd7-130">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4abd7-131">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="4abd7-131">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4abd7-132">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="4abd7-132">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4abd7-133">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="4abd7-133">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\SecuringWorkflowServices`
