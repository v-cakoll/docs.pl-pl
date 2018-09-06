---
title: Właściwości wykonania
ms.date: 03/30/2017
ms.assetid: 31c009db-397c-4653-87e2-32dc77fa4b13
ms.openlocfilehash: 4906c2ad11c8b5822764435d2b39a5b51f2673ba
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43748197"
---
# <a name="execution-properties"></a>Właściwości wykonania
Ten przykład pokazuje jak zdefiniować i wykonywania właściwości należy użyć działań niestandardowych. W tym przykładzie właściwość wykonywania Określa kolor pierwszego planu przez konsolę. Przykładowy przepływ pracy pokazuje, jak różne ścieżek logicznych wykonywania (gałęzie z <xref:System.Activities.Statements.Parallel> działania) może zachować konsoli różne kolory pomimo przeplatane wykonywanie funkcji działań (w rozgałęzieniach z <xref:System.Activities.Statements.Parallel> działanie).  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Otwórz rozwiązanie przykładowe ExecutionProperties.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
    > [!NOTE]
    >  Wyświetlanie ThreeColors.xaml przed kompilacją rozwiązania wyświetla komunikat o błędzie, ponieważ muszą zostać skompilowane niestandardowe działania, które są używane w tym samym czasie jako rozwiązanie.  
  
2.  Skompiluj i uruchom rozwiązanie.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\ExecutionProperties`