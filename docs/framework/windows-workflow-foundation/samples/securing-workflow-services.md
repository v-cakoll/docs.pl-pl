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
# <a name="securing-workflow-services"></a>Zabezpieczanie usług przepływu pracy
Przykładowy kod zabezpieczone usługi przepływu pracy zawiera następujące procedury:  
  
-   Tworzenie usługi podstawowy przepływ pracy przy użyciu <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply> działań.  
  
-   Za pomocą konfiguracji usługi Windows Communication Foundation (WCF), aby zdefiniować bezpieczne punkty końcowe do użytku przez usługi przepływu pracy.  
  
-   Tworzenie oświadczenia wewnątrz zasad niestandardowych i używanie <xref:System.ServiceModel.ServiceAuthorizationManager> do weryfikacji oświadczeń.  
  
## <a name="demonstrates"></a>Demonstracje  
 Przy użyciu zabezpieczeń programu WCF do bezpiecznej komunikacji między klientem a usługą przepływu pracy, autoryzacja oparta na oświadczeniach  
  
## <a name="discussion"></a>Dyskusja  
 Niniejszy przykład pokazuje użycie WCF infrastruktura zabezpieczeń, aby zabezpieczyć usługi przepływu pracy, tak jak normalne usługi WCF. W szczególności używa oświadczenia niestandardowego dla autoryzacji. W takim przypadku używa <xref:System.ServiceModel.WSHttpBinding> i tryb zabezpieczeń przy użyciu poświadczeń Windows komunikatów.  
  
 Niestandardowy <xref:System.IdentityModel.Policy.IAuthorizationPolicy> (`CustomNameCheckerPolicy`) sprawdza, czy nazwa użytkownika Windows klienta i dla określonego znaku. Jeśli ten znak jest obecny, tworzy i dodaje oświadczenie do <xref:System.IdentityModel.Policy.EvaluationContext>. Dzięki temu zasady niestandardowe osiąga instrukcję, klient ma tego znaku w nazwy użytkownika. To oświadczenie mogą być przeszukiwane przez cały okres istnienia połączenia. Możesz znaleźć tego znaku w `Constants.cs`.  
  
 Zasady autoryzacji szuka oświadczenia wewnątrz `SecureWorkFlowAuthZManager`. Jeśli uzna, zwraca `true` i zezwolić na przepływ pracy, aby kontynuować. W przeciwnym razie zwraca `false`, co powoduje, że komunikat "Odmowa dostępu", zwracane do klienta. Inne oświadczenia są obecne w kontekście i można zbadać również wewnątrz `SecureWorkFlowAuthZManager`.  
  
#### <a name="to-run-this-sample"></a>Aby uruchomić ten przykład  
  
1.  Uruchom [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] z uprawnieniami administratora.  
  
2.  Ładowanie SecuringWorkflowServices.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
3.  Naciśnij klawisze CTRL + SHIFT + B, aby skompilować rozwiązanie.  
  
4.  Ustaw projekt usługi jako projekt startowy rozwiązania.  
  
5.  Naciśnij klawisze CTRL + F5, aby uruchomić usługę bez debugowania.  
  
6.  Ustaw projekt klienta jako projekt startowy rozwiązania.  
  
7.  Naciśnij klawisze CTRL + F5, aby uruchomić klienta bez debugowania.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\SecuringWorkflowServices`
