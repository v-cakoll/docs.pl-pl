---
title: Przykładowe działanie compensable
ms.date: 03/30/2017
ms.assetid: 58f4898c-b2b8-44a4-9a73-3bef4da6d5ba
ms.openlocfilehash: 8008eaaca062723cab1efabfb1b25018353c73b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33514009"
---
# <a name="compensable-activity-sample"></a>Przykładowe działanie compensable
W tym przykładzie przedstawiono sposób użycia `CompensableActivity` działania do definiowania zadań do wykonania dla danej akcji podczas wykonywania normalnych i pracy, które są niezbędne do wykonania tej akcji, odpowiednio w razie potrzeby w późniejszym czasie.  Pierwsza część próbki pokazuje, jak można zdefiniować jednostki pracy compensable w systemie Windows Workflow Foundation (WF) przy użyciu `CompensableActivity` działania i jak są wykonywane w przebiegu powiodło się.  Druga część próbki pokazuje, jak tej samej jednostki pracy compensable automatycznie zajmie się kompensacji gdy nieoczekiwane zdarzenie zostaje trafiony i wystąpienia przepływu pracy zostało anulowane.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Za pomocą programu Visual Studio 2010, otwórz CompensableActivity.sln.  
  
2.  Skompiluj rozwiązanie, naciskając klawisze CTRL + SHIFT + B.  
  
3.  Uruchom aplikację, naciskając klawisz F5.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\BasicCompensableActivity`