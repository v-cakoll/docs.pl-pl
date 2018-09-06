---
title: Działanie NoPersistScope
ms.date: 03/30/2017
ms.assetid: 9a0baeb7-a05c-4fac-b905-252758cb71bb
ms.openlocfilehash: 6543756594b6734aec39bf22c5ab6215605341b1
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "44038786"
---
# <a name="nopersistscope-activity"></a>Działanie NoPersistScope
W tym przykładzie pokazano, jak do manipulowania nieprzeznaczone i możliwe do rozporządzania stan w przepływie pracy. Jest ważne, że przepływy pracy nie należy próbować utrwalanie stanu nie można serializować, i jest również ważne dla obiekty możliwe do rozporządzania na oczyszczenie po wyczerpaniu w przepływie pracy.  
  
## <a name="demonstrates"></a>Demonstracje  
 `NoPersistScope` niestandardowe działanie i projektanta.  
  
## <a name="using-the-nopersistzone-activity"></a>Przy użyciu działania NoPersistZone  
 Po uruchomieniu przykładowego przepływu pracy o nazwie niestandardowe działanie `CreateTextWriter` tworzy obiekt typu <xref:System.IO.TextWriter> i zapisuje je w zmiennej przepływu pracy. <xref:System.IO.TextWriter> jest <xref:System.IDisposable> obiektu. To <xref:System.IO.TextWriter>, który jest skonfigurowany do zapisu w pliku o nazwie "out.txt" w katalogu, w którym jest uruchamiany przykładu, jest używany przez <xref:System.Activities.Statements.WriteLine> działania informujące o dowolny tekst, wpisz w konsoli.  
  
 Logika echo jest uruchamiany w ramach `NoPersistScope` działanie (której kod jest również częścią tego przykładu), co uniemożliwia przepływu pracy jest trwały. Jeśli wpiszesz `unload` w konsoli programu host próbuje utrwalić wystąpienia przepływu pracy, ale ponieważ przepływ pracy pozostaje w ramach limitu czasu tej operacji `NoPersistScope`. Niestandardowe działanie, nazywany również korzysta z przepływu pracy `Dispose` można zlikwidować <xref:System.IO.TextWriter> obiektu po zakończeniu przepływu pracy przy jej użyciu. `Dispose` Działania jest umieszczana w <xref:System.Activities.Statements.TryCatch.Finally%2A> bloku <xref:System.Activities.Statements.TryCatch> działania, w którym <xref:System.IO.TextWriter> zmienna jest zadeklarowana, aby upewnić się, że działa, nawet jeśli wystąpi wyjątek podczas wykonywania bloku Try.  
  
 Można wpisać w `exit` ukończenia wystąpienia przepływu pracy i zakończyć program.  
  
#### <a name="to-run-the-sample"></a>Aby uruchomić przykład  
  
1.  Otwórz rozwiązanie NoPersistZone.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B, lub wybierz **Kompiluj rozwiązanie** z **kompilacji** menu.  
  
3.  Gdy kompilacja zakończyła się pomyślnie, naciśnij klawisz F5 lub wybierz **Rozpocznij debugowanie** z **debugowania** menu Alternatywnie, naciśnij klawisze CTRL + F5 lub wybierz **Rozpocznij bez debugowania** z **Debugowania** menu, aby uruchomić bez debugowania.  
  
#### <a name="to-cleanup-optional"></a>Aby oczyścić (opcjonalnie)  
  
1.  Aby usunąć Store wystąpienia SQL, należy uruchomić Cleanup.cmd.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NoPersistScope`