---
title: Używanie elementu ExpressionTextBox w projektancie działań niestandardowych
ms.date: 03/30/2017
ms.assetid: f82e73e7-a256-4a4d-82b7-c0d62f4ab5e7
ms.openlocfilehash: 6b581b42c882c12425a17b9a518f8957ca10898a
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715536"
---
# <a name="using-the-expressiontextbox-in-a-custom-activity-designer"></a>Używanie elementu ExpressionTextBox w projektancie działań niestandardowych
Ten przykład pokazuje, jak używać <xref:System.Activities.Presentation.View.ExpressionTextBox> w projektancie działań niestandardowych. Działanie niestandardowe `MultiAssign`, przypisuje dwie wartości ciągu do dwóch zmiennych ciągu. Niektóre formanty <xref:System.Activities.Presentation.View.ExpressionTextBox> są powiązane z <xref:System.Activities.InArgument>s, a niektóre z nich wiążą <xref:System.Activities.OutArgument>s.

## <a name="sample-details"></a>Przykładowe szczegóły
 `ArgumentToExpressionConverter` jest konwerterem typów używanym podczas wiązania wyrażeń z argumentami. `ConverterParameter` musi być ustawiona na odpowiednio `In` lub `Out`. `InOut` nie jest obsługiwana.

 Atrybut `UseLocationExpression` jest używany w `OutArgument`s, aby określić, że wyrażenie powinno być wyrażeniem L-wartością ("lewa wartość" lub "wartość lokalizacji"). W większości przypadków wyrażenie L-wartości jest prawidłowym identyfikatorem Visual Basic używanym do wskazania, że `OutArgument` zwracana jest nazwa zmiennej lub argumentu.

 Atrybut `MaxLines` jest ustawiony na jeden w tym przykładzie, a `MinLines` nie jest ustawiona. Oznacza to, że <xref:System.Activities.Presentation.View.ExpressionTextBox> jest stałym rozmiarem jednego wiersza, niezależnie od ilości tekstu wpisanego przez użytkownika. Aby umożliwić powiększanie <xref:System.Activities.Presentation.View.ExpressionTextBox> w celu dopasowania danych wejściowych użytkownika, ustaw `MaxLines` większe niż `MinLines`.

 Element ExpressionTextBox może być powiązany tylko z argumentami i nie można go powiązać z właściwościami środowiska CLR.

#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu

1. Za pomocą programu Visual Studio 2010 Otwórz plik ExpressionTextBoxSample. sln.

2. Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.

#### <a name="to-run-this-sample"></a>Aby uruchomić ten przykład

1. Dodaj nową aplikację konsoli przepływu pracy do rozwiązania.

2. Dodaj odwołanie do projektu **ExpressionTextBoxSample** z nowego projektu aplikacji konsolowej przepływu pracy.

3. Skompiluj rozwiązanie.

4. Przeciągnij działanie **wieloprzypisane** z przybornika i upuść je w przepływie pracy.

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\ExpressionTextBox`  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Activities.Presentation.View.ExpressionTextBox>
- [Tworzenie aplikacji przy użyciu Projektanta przepływu pracy](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
