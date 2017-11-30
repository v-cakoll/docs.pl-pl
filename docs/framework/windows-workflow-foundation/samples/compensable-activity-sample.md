---
title: "Przykładowe działanie compensable"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 58f4898c-b2b8-44a4-9a73-3bef4da6d5ba
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4ad3de1b3e9361e5de4803e06c8d257fbb9de76e
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2017
---
# <a name="compensable-activity-sample"></a>Przykładowe działanie compensable
W tym przykładzie przedstawiono sposób użycia `CompensableActivity` działania do definiowania zadań do wykonania dla danej akcji podczas wykonywania normalnych i pracy, które są niezbędne do wykonania tej akcji, odpowiednio w razie potrzeby w późniejszym czasie.  Pierwsza część próbki pokazuje, jak można zdefiniować jednostki pracy compensable w [!INCLUDE[wf](../../../../includes/wf-md.md)] przy użyciu `CompensableActivity` działania i jak są wykonywane w przebiegu powiodło się.  Druga część próbki pokazuje, jak tej samej jednostki pracy compensable automatycznie zajmie się kompensacji gdy nieoczekiwane zdarzenie zostaje trafiony i wystąpienia przepływu pracy zostało anulowane.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Za pomocą programu Visual Studio 2010, otwórz CompensableActivity.sln.  
  
2.  Skompiluj rozwiązanie, naciskając klawisze CTRL + SHIFT + B.  
  
3.  Uruchom aplikację, naciskając klawisz F5.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\BasicCompensableActivity`