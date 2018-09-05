---
title: Zabezpieczanie usług przepływu pracy
ms.date: 03/30/2017
ms.assetid: 53f84ad5-1ed1-4114-8d0d-b12e8a021c6e
ms.openlocfilehash: 28c34ecf7d6d781bfa461b2737cb9325a657f47e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43524338"
---
# <a name="securing-workflow-services"></a><span data-ttu-id="e7903-102">Zabezpieczanie usług przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="e7903-102">Securing Workflow Services</span></span>
<span data-ttu-id="e7903-103">Przykładowy kod zabezpieczone usługi przepływu pracy zawiera następujące procedury:</span><span class="sxs-lookup"><span data-stu-id="e7903-103">The Secured Workflow Service sample shows the following procedures:</span></span>  
  
-   <span data-ttu-id="e7903-104">Tworzenie usługi podstawowy przepływ pracy przy użyciu <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply> działań.</span><span class="sxs-lookup"><span data-stu-id="e7903-104">Creating a basic workflow service using the <xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply> activities.</span></span>  
  
-   <span data-ttu-id="e7903-105">Za pomocą konfiguracji usługi Windows Communication Foundation (WCF), aby zdefiniować bezpieczne punkty końcowe do użytku przez usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="e7903-105">Using Windows Communication Foundation (WCF) configuration to define secure endpoints for use by the workflow service.</span></span>  
  
-   <span data-ttu-id="e7903-106">Tworzenie oświadczenia wewnątrz zasad niestandardowych i używanie <xref:System.ServiceModel.ServiceAuthorizationManager> do weryfikacji oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="e7903-106">Creating claims inside a custom policy and using the <xref:System.ServiceModel.ServiceAuthorizationManager> to validate claims.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="e7903-107">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="e7903-107">Demonstrates</span></span>  
 <span data-ttu-id="e7903-108">Przy użyciu zabezpieczeń programu WCF do bezpiecznej komunikacji między klientem a usługą przepływu pracy, autoryzacja oparta na oświadczeniach</span><span class="sxs-lookup"><span data-stu-id="e7903-108">Using WCF security to secure communication between client and Workflow service, Claims based authorization</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="e7903-109">Dyskusja</span><span class="sxs-lookup"><span data-stu-id="e7903-109">Discussion</span></span>  
 <span data-ttu-id="e7903-110">Niniejszy przykład pokazuje użycie WCF infrastruktura zabezpieczeń, aby zabezpieczyć usługi przepływu pracy, tak jak normalne usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="e7903-110">This sample demonstrates the use of WCF security infrastructure to secure a workflow service just like you would with a normal WCF service.</span></span> <span data-ttu-id="e7903-111">W szczególności używa oświadczenia niestandardowego dla autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="e7903-111">Specifically, it uses a custom claim for authorization.</span></span> <span data-ttu-id="e7903-112">W takim przypadku używa <xref:System.ServiceModel.WSHttpBinding> i tryb zabezpieczeń przy użyciu poświadczeń Windows komunikatów.</span><span class="sxs-lookup"><span data-stu-id="e7903-112">In this case, it uses <xref:System.ServiceModel.WSHttpBinding> and message mode security with Windows credentials.</span></span>  
  
 <span data-ttu-id="e7903-113">Niestandardowy <xref:System.IdentityModel.Policy.IAuthorizationPolicy> (`CustomNameCheckerPolicy`) sprawdza, czy nazwa użytkownika Windows klienta i dla określonego znaku.</span><span class="sxs-lookup"><span data-stu-id="e7903-113">The custom <xref:System.IdentityModel.Policy.IAuthorizationPolicy> (`CustomNameCheckerPolicy`) checks the client's Windows username and for a specific character.</span></span> <span data-ttu-id="e7903-114">Jeśli ten znak jest obecny, tworzy i dodaje oświadczenie do <xref:System.IdentityModel.Policy.EvaluationContext>.</span><span class="sxs-lookup"><span data-stu-id="e7903-114">If that character is present, it creates and adds the claim to the <xref:System.IdentityModel.Policy.EvaluationContext>.</span></span> <span data-ttu-id="e7903-115">Dzięki temu zasady niestandardowe osiąga instrukcję, klient ma tego znaku w nazwy użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e7903-115">By doing this, the custom policy is making the statement that the client has this character in the username.</span></span> <span data-ttu-id="e7903-116">To oświadczenie mogą być przeszukiwane przez cały okres istnienia połączenia.</span><span class="sxs-lookup"><span data-stu-id="e7903-116">This claim can be queried throughout the lifetime of the call.</span></span> <span data-ttu-id="e7903-117">Możesz znaleźć tego znaku w `Constants.cs`.</span><span class="sxs-lookup"><span data-stu-id="e7903-117">You can find that character in `Constants.cs`.</span></span>  
  
 <span data-ttu-id="e7903-118">Zasady autoryzacji szuka oświadczenia wewnątrz `SecureWorkFlowAuthZManager`.</span><span class="sxs-lookup"><span data-stu-id="e7903-118">The authorization policy looks for the claim inside the `SecureWorkFlowAuthZManager`.</span></span> <span data-ttu-id="e7903-119">Jeśli uzna, zwraca `true` i zezwolić na przepływ pracy, aby kontynuować.</span><span class="sxs-lookup"><span data-stu-id="e7903-119">If it finds it, it returns `true` and allow the workflow to proceed.</span></span> <span data-ttu-id="e7903-120">W przeciwnym razie zwraca `false`, co powoduje, że komunikat "Odmowa dostępu", zwracane do klienta.</span><span class="sxs-lookup"><span data-stu-id="e7903-120">Otherwise, it returns `false`, which causes an 'Access Denied' message to be returned to the client.</span></span> <span data-ttu-id="e7903-121">Inne oświadczenia są obecne w kontekście i można zbadać również wewnątrz `SecureWorkFlowAuthZManager`.</span><span class="sxs-lookup"><span data-stu-id="e7903-121">Other claims are present in the context and can be examined as well inside the `SecureWorkFlowAuthZManager`.</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="e7903-122">Aby uruchomić ten przykład</span><span class="sxs-lookup"><span data-stu-id="e7903-122">To run this sample</span></span>  
  
1.  <span data-ttu-id="e7903-123">Uruchom [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="e7903-123">Run [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with administrator privileges.</span></span>  
  
2.  <span data-ttu-id="e7903-124">Ładowanie SecuringWorkflowServices.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e7903-124">Load SecuringWorkflowServices.sln in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
3.  <span data-ttu-id="e7903-125">Naciśnij klawisze CTRL + SHIFT + B, aby skompilować rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="e7903-125">Press CTRL+SHIFT+B to compile the solution.</span></span>  
  
4.  <span data-ttu-id="e7903-126">Ustaw projekt usługi jako projekt startowy rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="e7903-126">Set the Service project as the start-up project for the solution.</span></span>  
  
5.  <span data-ttu-id="e7903-127">Naciśnij klawisze CTRL + F5, aby uruchomić usługę bez debugowania.</span><span class="sxs-lookup"><span data-stu-id="e7903-127">Press CTRL+F5 to start the service without debugging.</span></span>  
  
6.  <span data-ttu-id="e7903-128">Ustaw projekt klienta jako projekt startowy rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="e7903-128">Set the Client project as the start-up project for the solution.</span></span>  
  
7.  <span data-ttu-id="e7903-129">Naciśnij klawisze CTRL + F5, aby uruchomić klienta bez debugowania.</span><span class="sxs-lookup"><span data-stu-id="e7903-129">Press CTRL+F5 to start the client without debugging.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e7903-130">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="e7903-130">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e7903-131">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="e7903-131">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e7903-132">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="e7903-132">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e7903-133">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="e7903-133">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\SecuringWorkflowServices`
