---
title: "Właściwości wykonania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 31c009db-397c-4653-87e2-32dc77fa4b13
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ab7c81f051e6e65509d232479fd9f4ebe00ac99d
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2017
---
# <a name="execution-properties"></a>Właściwości wykonania
W tym przykładzie pokazano, jak zdefiniować i wykonanie właściwości należy użyć niestandardowego działania. W tym przykładzie właściwość wykonywania Określa kolor pierwszego planu konsoli. Przykładowy przepływ pracy przedstawia sposób różnych ścieżek logicznych wykonywania (gałęzi z <xref:System.Activities.Statements.Parallel> działania) można zachować konsoli różnych kolorów pomimo przeplotem wykonywania działań (przez oddziały <xref:System.Activities.Statements.Parallel> działania).  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Otwórz rozwiązanie próbki ExecutionProperties.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
    > [!NOTE]
    >  Wyświetlanie ThreeColors.xaml przed kompilacją rozwiązania jest wyświetlany błąd, ponieważ muszą zostać skompilowane działań niestandardowych używane w tym samym czasie jako rozwiązanie.  
  
2.  Tworzenie i uruchamianie rozwiązania.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\ExecutionProperties`