---
title: Wizualne śledzenie przepływu pracy
ms.date: 03/30/2017
ms.assetid: 0143448f-2044-40a0-8a3d-941f6d12468b
ms.openlocfilehash: c89a63ac80b4705fff5c7714e7f40646c5b5d26d
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703585"
---
# <a name="visual-workflow-tracking"></a>Wizualne śledzenie przepływu pracy
W tym przykładzie przedstawiono sposób pisania przepływu pracy visual śledzenia aplikacji przy użyciu funkcji debugowania dostępnych za pośrednictwem [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)].

## <a name="sample-details"></a>Przykład szczegółów
 Aplikacja wykonuje przepływ pracy prosty schemat blokowy (zdefiniowanymi w Workflow.xaml) i ponownie obsługuje projektanta przepływów pracy, aby wyświetlić aktualnie wykonywanej przepływu pracy. Przepływ pracy jest wykonywane, aktualnie wykonywanego działania jest wyświetlana żółta strzałka konspekt i debugowania. Ponadto rekordów śledzenia generowane przez przepływ pracy również są wyświetlane w oknie aplikacji. Aby uzyskać więcej informacji na temat śledzenia przepływu pracy, zobacz [przepływu pracy i śledzenie](../workflow-tracking-and-tracing.md). Aby dowiedzieć się więcej o ponowne hostowanie projektanta przepływu pracy, zobacz [Rehostowanie projektanta przepływu pracy](../rehosting-the-workflow-designer.md).

 Symulator przepływu pracy polega na przechowywanie dwóch słowników. Jedna z nich zawiera mapowanie między aktualnie wykonywany obiekt działania i XAML numer wiersza, w którym zostanie utworzone wystąpienie działania. Drugi zawiera mapowanie między identyfikator wystąpienia działania i obiekt działania. Gdy są emitowane rekordów śledzenia przy użyciu niestandardowego śledzenia profilu aplikacji z Identyfikatorem wystąpienia aktualnie wykonywanego działania, a mapuje go pliku XAML, który on uruchomiony. Rehostowanym projektancie przepływu pracy jest następnie zgodnie z instrukcjami otrzymywanymi zaznacz działań na powierzchni projektanta i używać tej samej metody co debuger przepływu pracy, w szczególności rysowania żółte obramowanie wokół działania i wyświetlanie żółtą strzałką z lewej strony Projektant.

#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu

1.  Otwórz plik WorkflowSimulator.sln katalog przykładu w programie Visual Studio 2010.

2.  Naciśnij klawisze CTRL + SHIFT + B, aby skompilować rozwiązanie.

3.  Naciśnij klawisze CTRL + F5, aby uruchomić przykład. Spowoduje to wyświetlenie pliku Workflow.xaml w oknie projektanta rehostowanym przepływu pracy.

4.  Kliknij przycisk **pliku** menu, a następnie wybierz **Uruchom przepływ pracy...** .

5.  Ogłoszenie aktualnie wykonywanej działanie zostanie wyróżniona, zgodnie z opisem w poprzedniej sekcji i rekordów śledzenia są wyświetlane po prawej stronie okna aplikacji.

6.  Po ukończeniu przepływu pracy, możesz kliknąć dowolny z rekordów śledzenia, aby sprawdzić działanie, które odnosi się do informacji.

> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\VisualWorkflowTracking`