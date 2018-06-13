---
title: Śledzenie Visual przepływu pracy
ms.date: 03/30/2017
ms.assetid: 0143448f-2044-40a0-8a3d-941f6d12468b
ms.openlocfilehash: f010bdcf6004e84fd346d0e8649c87c008cad122
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516916"
---
# <a name="visual-workflow-tracking"></a>Śledzenie Visual przepływu pracy
W tym przykładzie pokazano sposób pisania przepływu pracy programu visual śledzenia aplikacji przy użyciu funkcji debugowania dostępnych za pośrednictwem [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)].  
  
## <a name="sample-details"></a>Szczegóły próbki  
 Aplikacja wykonuje prostego schematu blokowego przepływu pracy (zdefiniowany w Workflow.xaml) i ponownie obsługuje projektanta przepływów pracy, aby wyświetlić aktualnie wykonywane przepływu pracy. Jak przepływu pracy jest wykonywane, aktualnie wykonywanego działania jest wyświetlany ze strzałką żółty konspektu i debugowania. Ponadto rekordów śledzenia wygenerowanych przez przepływ pracy również są wyświetlane w oknie aplikacji. Aby uzyskać więcej informacji o śledzeniu w przepływie pracy, zobacz [przepływu pracy śledzenia i śledzenia](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md). Aby uzyskać więcej informacji o ponownym hostingu projektanta przepływów pracy, zobacz [Rehosting projektanta przepływów pracy](../../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md).  
  
 Symulator przepływu pracy polega na przechowywanie dwóch słowników. Jeden zawiera mapowania między obiektem aktualnie wykonywanego działania i XAML numer wiersza, w którym zostanie uruchomiony działania. Drugi zawiera mapowania między identyfikator wystąpienia działania i obiekt działania. Podczas śledzenia rekordy są emitowane przy użyciu niestandardowego profilu, śledzenia aplikacji Określa identyfikator wystąpienia aktualnie wykonywanego działania i mapuje on pliku XAML, który go wystąpienia. Projektant rehosted przepływu pracy jest następnie instrukcją zaznacz działanie na powierzchni projektowej oraz używanie tej samej metody debugera przepływu pracy, w szczególności rysowania żółty obramowania wokół działania i wyświetlanie żółta strzałka lewej strony Projektant.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Otwórz plik WorkflowSimulator.sln z katalogu próbki [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Naciśnij klawisze CTRL + SHIFT + B w celu skompilowania rozwiązania.  
  
3.  Naciśnij klawisze CTRL + F5, aby uruchomić przykład. Plik Workflow.xaml zostaną wyświetlone w oknie projektanta rehosted przepływu pracy.  
  
4.  Kliknij przycisk **pliku** menu i wybierz **uruchomienia przepływu pracy...** .  
  
5.  Powiadomienie aktualnie wykonywanego działania zostanie wyróżniona, jak opisano wcześniej, a rekordy śledzenia są wyświetlane po prawej stronie okna aplikacji.  
  
6.  Po zakończeniu przepływu pracy, można kliknąć dowolną rekordów śledzenia do zbadania działanie (activity) odpowiadający mu.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\VisualWorkflowTracking`