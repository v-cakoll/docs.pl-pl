---
title: Uwidacznianie i wywoływanie działań ActivityActions
ms.date: 03/30/2017
ms.assetid: 97ce4797-426e-463d-9cc4-1261afad6df4
ms.openlocfilehash: 99207c33d82ec9028da2355cc792c366dc5e0cc6
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2018
ms.locfileid: "47398566"
---
# <a name="exposing-and-invoking-activityactions"></a>Uwidacznianie i wywoływanie działań ActivityActions
W tym przykładzie pokazano, jak tworzyć niestandardowe działanie, które ma <xref:System.Activities.ActivityAction>. Ilustruje też sposób użycia tego działania, zapewniając implementację <xref:System.Activities.ActivityAction>.  
  
 <xref:System.Activities.ActivityAction> Umożliwia autorowi działania do udostępnienia "otworów" przy użyciu określonej sygnatury niestandardowe zachowanie, na którym użytkownik działania można podłączyć. Na przykład <xref:System.Activities.Statements.ForEach%601> działania (który działa przez kolekcję elementów), ma <xref:System.Activities.ActivityAction> umożliwiająca użytkownikowi działanie wtyczki zachowanie, które działa w bieżącym elemencie iteracji.  
  
## <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Otwórz **ActivityAction.sln** przykładowe rozwiązanie w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Skompiluj i uruchom rozwiązanie.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\ActivityAction`