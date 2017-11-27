---
title: "Udostępnianie i wywoływanie ActivityActions"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97ce4797-426e-463d-9cc4-1261afad6df4
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8a87e4463689e9301045a55b16af46cb037c1fa5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
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
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\ActivityAction`  
  
## <a name="see-also"></a>Zobacz też
