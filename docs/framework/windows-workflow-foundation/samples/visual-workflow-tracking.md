---
title: Wizualne śledzenie przepływu pracy
ms.date: 03/30/2017
ms.assetid: 0143448f-2044-40a0-8a3d-941f6d12468b
ms.openlocfilehash: 22c91a12bba148e1fa823bb2bf9b3eaf16704c46
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182747"
---
# <a name="visual-workflow-tracking"></a>Wizualne śledzenie przepływu pracy
W tym przykładzie pokazano, jak napisać wizualną aplikację śledzenia przepływu [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)]pracy przy użyciu funkcji debugowania dostępnych za pośrednictwem pliku .

## <a name="sample-details"></a>Przykładowe szczegóły
 Aplikacja wykonuje prosty przepływ pracy schematu blokowego (zdefiniowany w pliku Workflow.xaml) i ponownie hostuje projektanta przepływu pracy, aby wyświetlić aktualnie wykonywany przepływ pracy. Podczas wykonywania przepływu pracy aktualnie wykonywane działanie jest wyświetlane z żółtym konturem i strzałką debugowania. Ponadto rekordy śledzenia generowane przez przepływ pracy są również wyświetlane w oknie aplikacji. Aby uzyskać więcej informacji na temat śledzenia przepływu pracy, zobacz [Śledzenie przepływu pracy i śledzenie](../workflow-tracking-and-tracing.md). Aby uzyskać więcej informacji na temat ponownego hostowania projektanta przepływów pracy, zobacz [Ponowne hostowanie projektanta przepływu pracy](../rehosting-the-workflow-designer.md).

 Symulator przepływu pracy działa, zachowując dwa słowniki. Jeden zawiera mapowanie między aktualnie wykonywanym obiektem działania a numerem wiersza XAML, w którym działanie jest tworzone. Drugi zawiera mapowanie między identyfikatorem wystąpienia działania a obiektem działania. Gdy rekordy śledzenia są emitowane przy użyciu niestandardowego profilu śledzenia, aplikacja określa identyfikator wystąpienia aktualnie wykonywanego działania i mapuje go z powrotem do pliku XAML, który go skonkrzewnieniu. Projektant ponownego hostowania przepływu pracy jest następnie instruowany, aby podświetlić działanie na powierzchni projektanta i użyć tej samej metody co debuger przepływu pracy, w szczególności rysując żółte obramowanie wokół działania i wyświetlając żółtą strzałkę wzdłuż lewej strony Projektant.

#### <a name="to-use-this-sample"></a>Aby użyć tej próbki

1. Otwórz plik WorkflowSimulator.sln z przykładowego katalogu w programie Visual Studio 2010.

2. Naciśnij kombinację klawiszy CTRL+SHIFT+B w celu skompilowania rozwiązania.

3. Naciśnij klawisze CTRL + F5, aby uruchomić próbkę. Spowoduje to wyświetlenie pliku Workflow.xaml w oknie projektanta ponownego hostu przepływu pracy.

4. Kliknij menu **Plik** i wybierz polecenie **Uruchom przepływ pracy...**.

5. Zwróć uwagę, że aktualnie wykonywane działanie jest wyróżnione w sposób opisany wcześniej, a rekordy śledzenia są wyświetlane po prawej stronie okna aplikacji.

6. Po zakończeniu przepływu pracy można kliknąć dowolny z rekordów śledzenia, aby sprawdzić, które działanie odpowiada.

> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Application\VisualWorkflowTracking`
