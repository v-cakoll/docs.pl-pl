---
title: Udostępnianie i wywoływanie ActivityActions
ms.date: 03/30/2017
ms.assetid: 97ce4797-426e-463d-9cc4-1261afad6df4
ms.openlocfilehash: 2d369ec4b028b047ce02016dd511c1c088b46a91
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33513155"
---
# <a name="exposing-and-invoking-activityactions"></a>Udostępnianie i wywoływanie ActivityActions
W tym przykładzie pokazano, jak tworzenie działań niestandardowych, które ma <xref:System.Activities.ActivityAction>. Również przedstawia sposób użycia tego działania, dostarczając implementację <xref:System.Activities.ActivityAction>.  
  
 <xref:System.Activities.ActivityAction> Umożliwia autorowi działania ujawnia "dziury" z określonych podpisów gdzie działania użytkownika można dodać niestandardowe zachowanie. Na przykład <!--zz <xref:System.Activities.Statements.ForEach>--> `System.Activities.Statements.ForEach` działania (które działa przez kolekcję elementów), ma <xref:System.Activities.ActivityAction> umożliwiająca użytkownikowi działanie Dołącz zachowanie, który działa w bieżącym elemencie iteracji.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Otwórz **ActivityAction.sln** przykładowe rozwiązanie w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Tworzenie i uruchamianie rozwiązania.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\ActivityAction`