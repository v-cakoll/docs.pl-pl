---
title: Używanie elementu ExpressionTextBox w projektancie działań niestandardowych
ms.date: 03/30/2017
ms.assetid: f82e73e7-a256-4a4d-82b7-c0d62f4ab5e7
ms.openlocfilehash: bfac07d64cd5e30c3475d4e269c16597905ea829
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045357"
---
# <a name="using-the-expressiontextbox-in-a-custom-activity-designer"></a>Używanie elementu ExpressionTextBox w projektancie działań niestandardowych
Ten przykład pokazuje, <xref:System.Activities.Presentation.View.ExpressionTextBox> jak używać w niestandardowym projektancie działań. Działanie niestandardowe, `MultiAssign`, przypisuje dwie wartości ciągu do dwóch zmiennych ciągu. Niektóre <xref:System.Activities.Presentation.View.ExpressionTextBox> formanty są powiązane <xref:System.Activities.InArgument>z s i z pewnymi powiązaniami z <xref:System.Activities.OutArgument>.

## <a name="sample-details"></a>Przykładowe szczegóły
 `ArgumentToExpressionConverter` Jest konwerterem typów używanym podczas wiązania wyrażeń z argumentami. Wartość musi być ustawiona na `In` lub `Out` odpowiednio. `ConverterParameter` `InOut`nie jest obsługiwana.

 Ten `UseLocationExpression` atrybut jest używany w `OutArgument`s, aby określić, że wyrażenie powinno być wyrażeniem L-wartości ("lewa wartość" lub "wartość lokalizacji"). W większości przypadków wyrażenie L-wartości jest prawidłowym identyfikatorem Visual Basic używanym do wskazania, że `OutArgument` zwracana jest nazwa zmiennej lub argumentu.

 Atrybut jest ustawiony na jeden w tym przykładzie i `MinLines` nie jest ustawiony. `MaxLines` Oznacza to, że <xref:System.Activities.Presentation.View.ExpressionTextBox> jest to stały rozmiar jednego wiersza niezależnie od ilości tekstu wpisanego przez użytkownika. Aby umożliwić <xref:System.Activities.Presentation.View.ExpressionTextBox> powiększanie się w celu dopasowania danych przez użytkownika, `MinLines`ustaw wartość `MaxLines` większą niż.

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
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\ExpressionTextBox`  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Activities.Presentation.View.ExpressionTextBox>
- [Tworzenie aplikacji przy użyciu Projektanta przepływu pracy](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
