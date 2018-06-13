---
title: Zabezpieczanie usług przepływu pracy
ms.date: 03/30/2017
ms.assetid: 53f84ad5-1ed1-4114-8d0d-b12e8a021c6e
ms.openlocfilehash: 5dbd724f3a2f8febfc74719584f4d69cbf75b567
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33806672"
---
# <a name="securing-workflow-services"></a>Zabezpieczanie usług przepływu pracy
Przykład zabezpieczone usługi przepływu pracy obejmuje następujące procedury:  
  
-   Tworzenie usługi podstawowy przepływ pracy za pomocą <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply> działań.  
  
-   Za pomocą konfiguracji usługi Windows Communication Foundation (WCF) do definiowania bezpieczne punkty końcowe do użytku przez usługi przepływu pracy.  
  
-   Tworzenie oświadczeń wewnątrz zasadę niestandardową i korzystanie z <xref:System.ServiceModel.ServiceAuthorizationManager> do sprawdzenia.  
  
## <a name="demonstrates"></a>Demonstracje  
 Przy użyciu zabezpieczeń WCF do zabezpieczania komunikacji między klientem a usługą przepływu pracy, na podstawie oświadczeń autoryzacji  
  
## <a name="discussion"></a>Omówienie  
 W tym przykładzie przedstawiono korzystanie z infrastruktury zabezpieczeń WCF do zabezpieczania usługi przepływu pracy, tak jak normalne usługi WCF. W szczególności używa oświadczenia niestandardowego dla autoryzacji. W takim przypadku używa <xref:System.ServiceModel.WSHttpBinding> i komunikatów tryb zabezpieczeń z poświadczeniami systemu Windows.  
  
 Niestandardowa <xref:System.IdentityModel.Policy.IAuthorizationPolicy> (`CustomNameCheckerPolicy`) sprawdza nazwa użytkownika systemu Windows klienta i dla określonych znaków. Jeśli ten znak jest obecny, tworzy i dodaje oświadczenie do <xref:System.IdentityModel.Policy.EvaluationContext>. Dzięki temu zasady niestandardowe jest wprowadzenie instrukcji który klient ma tego znaku w nazwy użytkownika. Tego oświadczenia mogą być przeszukiwane przez cały okres istnienia połączenia. Możesz znaleźć tego znaku w `Constants.cs`.  
  
 Zasady autoryzacji szuka oświadczeń wewnątrz `SecureWorkFlowAuthZManager`. Jeśli uzna, zwraca `true` i umożliwić przepływu pracy kontynuować. W przeciwnym razie zwraca `false`, co powoduje, że komunikat "Odmowa dostępu", ma zostać zwrócona do klienta. Pozostałe roszczenia znajdują się w kontekście i może sprawdzić, jak również wewnątrz `SecureWorkFlowAuthZManager`.  
  
#### <a name="to-run-this-sample"></a>Aby uruchomić ten przykład  
  
1.  Uruchom [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] z uprawnieniami administratora.  
  
2.  Ładowanie SecuringWorkflowServices.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
3.  Naciśnij klawisze CTRL + SHIFT + B do skompilowania rozwiązania.  
  
4.  Ustaw projekt usługi jako projekt uruchamiania dla rozwiązania.  
  
5.  Naciśnij klawisze CTRL + F5, aby uruchomić usługę bez debugowania.  
  
6.  Ustaw projekt klienta jako projekt uruchamiania dla rozwiązania.  
  
7.  Naciśnij klawisze CTRL + F5, aby uruchomić klienta bez debugowania.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\SecuringWorkflowServices`
