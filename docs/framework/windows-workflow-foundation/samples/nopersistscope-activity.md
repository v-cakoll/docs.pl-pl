---
title: "Działanie NoPersistScope"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a0baeb7-a05c-4fac-b905-252758cb71bb
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8813739f9e2f22cb94ed353f73a64562d3aeaa84
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="nopersistscope-activity"></a>Działanie NoPersistScope
W tym przykładzie pokazano, jak do manipulowania nie można serializować i możliwe do rozporządzania stanu w przepływie pracy. Jest ważne, przepływy pracy nie należy próbować zachować nie można serializować stanu, a także jest ważna w przypadku obiekty możliwe do rozporządzania na oczyszczenie po są one używane w przepływie pracy.  
  
## <a name="demonstrates"></a>Demonstracje  
 `NoPersistScope`Niestandardowe działania i projektanta.  
  
## <a name="using-the-nopersistzone-activity"></a>Za pomocą działania NoPersistZone  
 Po uruchomieniu przykładowego przepływu pracy działania niestandardowego o nazwie `CreateTextWriter` tworzy obiekt typu <xref:System.IO.TextWriter> i zapisuje je w zmiennej przepływu pracy. <xref:System.IO.TextWriter>jest <xref:System.IDisposable> obiektu. To <xref:System.IO.TextWriter>, która jest skonfigurowana do zapisu w pliku o nazwie "out.txt" w katalogu, w której jest uruchamiana próbki, jest używany przez <xref:System.Activities.Statements.WriteLine> działania echa dowolny tekst, wpisz w konsoli.  
  
 Logika echo jest uruchamiany w ramach `NoPersistScope` działania (dla kodu jest również częścią tego przykładu), co zapobiega przepływu pracy są zachowywane. W przypadku wpisania w `unload` za pomocą konsoli hosta próby potrzebna na utrwalenie wystąpienia przepływu pracy, ale ponieważ przepływ pracy pozostaje w ramach limitu czasu tej operacji `NoPersistScope`. Przepływ pracy używa również niestandardowego działania o nazwie `Dispose` można zlikwidować <xref:System.IO.TextWriter> obiekt po zakończeniu przepływu pracy przy jej użyciu. `Dispose` Działanie znajduje się w obrębie <xref:System.Activities.Statements.TryCatch.Finally%2A> zablokować z <xref:System.Activities.Statements.TryCatch> działania, w którym <xref:System.IO.TextWriter> zmienna została zadeklarowana, aby upewnić się, że działa nawet wtedy, gdy wystąpią Wystąpił wyjątek podczas wykonywania bloku Try.  
  
 Można wpisać w `exit` aby zakończyć wystąpienia przepływu pracy i zamknąć program.  
  
#### <a name="to-run-the-sample"></a>Aby uruchomić przykładowy  
  
1.  Otwórz rozwiązanie NoPersistZone.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Skompiluj rozwiązanie, naciśnij kombinację klawiszy CTRL + SHIFT + B lub wybierz **Kompiluj rozwiązanie** z **kompilacji** menu.  
  
3.  Gdy kompilacja zakończyła się pomyślnie, naciśnij klawisz F5 lub wybierz **Rozpocznij debugowanie** z **debugowania** menu można również nacisnąć klawisze CTRL + F5 lub wybierz **uruchomić bez debugowania** z **Debugowania** menu, aby uruchomić bez debugowania.  
  
#### <a name="to-cleanup-optional"></a>Do oczyszczania (opcjonalnie)  
  
1.  Aby usunąć magazyn wystąpienia SQL, uruchom Cleanup.cmd.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NoPersistScope`  
  
## <a name="see-also"></a>Zobacz też
