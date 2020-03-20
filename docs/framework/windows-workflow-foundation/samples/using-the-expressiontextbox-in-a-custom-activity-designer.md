---
title: Używanie elementu ExpressionTextBox w projektancie działań niestandardowych
ms.date: 03/30/2017
ms.assetid: f82e73e7-a256-4a4d-82b7-c0d62f4ab5e7
ms.openlocfilehash: 6d3df9e18c7239f0e4695509d80edfd02e9a9d6f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182768"
---
# <a name="using-the-expressiontextbox-in-a-custom-activity-designer"></a>Używanie elementu ExpressionTextBox w projektancie działań niestandardowych
W tym przykładzie <xref:System.Activities.Presentation.View.ExpressionTextBox> pokazano, jak używać w projektancie działań niestandardowych. Działanie niestandardowe `MultiAssign`, przypisuje dwie wartości ciągu do dwóch zmiennych ciągu. Niektóre <xref:System.Activities.Presentation.View.ExpressionTextBox> formanty wiążą się z <xref:System.Activities.InArgument>s, a niektóre wiążą się z <xref:System.Activities.OutArgument>s.

## <a name="sample-details"></a>Przykładowe szczegóły
 Jest `ArgumentToExpressionConverter` konwerterem typu używanym podczas wiązania wyrażeń z argumentami. Musi `ConverterParameter` być `In` ustawiona `Out` lub w stosownych przypadkach. `InOut`nie jest obsługiwana.

 Atrybut `UseLocationExpression` jest używany `OutArgument`na s, aby określić, że wyrażenie powinno być wyrażeniem wartości L ("wartość lewa" lub "wartość lokalizacji"). W większości przypadków wyrażenie wartości L jest prawidłowym identyfikatorem języka `OutArgument` Visual Basic używanym do wskazania, że zwracana jest nazwa zmiennej lub argumentu.

 Atrybut `MaxLines` jest ustawiony na jeden w `MinLines` tym przykładzie i nie jest ustawiony. Oznacza to, <xref:System.Activities.Presentation.View.ExpressionTextBox> że jest to stały rozmiar jednego wiersza, niezależnie od ilości tekstu wpisanego przez użytkownika. Aby umożliwić <xref:System.Activities.Presentation.View.ExpressionTextBox> wzrost, aby dopasować `MaxLines` dane `MinLines`wejściowe użytkownika, ustaw więcej niż .

 ExpressionTextBox może być powiązany tylko z argumentami i nie może być powiązany z właściwościami CLR.

#### <a name="to-use-this-sample"></a>Aby użyć tej próbki

1. Za pomocą programu Visual Studio 2010 otwórz plik ExpressionTextBoxSample.sln.

2. Aby utworzyć rozwiązanie, naciśnij klawisze CTRL+SHIFT+B.

#### <a name="to-run-this-sample"></a>Aby uruchomić ten przykład

1. Dodaj nową aplikację konsoli przepływu pracy do rozwiązania.

2. Dodaj odwołanie do projektu **ExpressionTextBoxSample** z nowego projektu aplikacji konsoli przepływu pracy.

3. Skompiluj rozwiązanie.

4. Przeciągnij działanie **MultiAssign** z przybornika i upuść je do przepływu pracy.

> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\ExpressionTextBox`  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Activities.Presentation.View.ExpressionTextBox>
- [Tworzenie aplikacji przy użyciu Projektanta przepływu pracy](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
