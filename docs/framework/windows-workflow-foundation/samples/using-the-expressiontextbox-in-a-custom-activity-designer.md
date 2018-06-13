---
title: Przy użyciu ExpressionTextBox w Projektancie działań niestandardowych
ms.date: 03/30/2017
ms.assetid: f82e73e7-a256-4a4d-82b7-c0d62f4ab5e7
ms.openlocfilehash: ad0c29e2661c82e663fd6b68fdcd74f542ef28b1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516789"
---
# <a name="using-the-expressiontextbox-in-a-custom-activity-designer"></a>Przy użyciu ExpressionTextBox w Projektancie działań niestandardowych
Ten przykład przedstawia sposób użycia <xref:System.Activities.Presentation.View.ExpressionTextBox> w Projektancie działania niestandardowego. To niestandardowe działanie `MultiAssign`, przypisuje dwóch wartości ciągu do dwóch zmiennych ciągu. Niektóre <xref:System.Activities.Presentation.View.ExpressionTextBox> powiązania kontrolki <xref:System.Activities.InArgument>s, a niektóre powiązać <xref:System.Activities.OutArgument>s.  
  
## <a name="sample-details"></a>Szczegóły próbki  
 `ArgumentToExpressionConverter` Jest używany podczas tworzenia wiązania wyrażenia argumentów konwerter typów. `ConverterParameter` Musi mieć ustawioną `In` lub `Out` odpowiednio. `InOut` nie jest obsługiwane.  
  
 `UseLocationExpression` Atrybut jest stosowany na `OutArgument`s, aby określić, czy wyrażenie powinno być wyrażeniem L-wartość ("po lewej stronie" lub "lokalizacji wartości"). W większości przypadków wyrażenia wartości L jest prawidłowym identyfikatorem języka Visual Basic, używany w celu wskazania, że `OutArgument` zwracana jest nazwa zmiennej lub argumentu.  
  
 `MaxLines` Atrybut ma ustawioną w tym przykładzie i `MinLines` nie jest ustawiona. Oznacza to, że <xref:System.Activities.Presentation.View.ExpressionTextBox> ma stały rozmiar jednej linii, niezależnie od ilości tekstu przez użytkownika. Aby umożliwić <xref:System.Activities.Presentation.View.ExpressionTextBox> aby dopasowany do wprowadzenia danych przez użytkownika, należy ustawić `MaxLines` większa niż `MinLines`.  
  
 ExpressionTextBox może być powiązana tylko z argumentów i nie można powiązać właściwości CLR.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik ExpressionTextBoxSample.sln.  
  
2.  Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.  
  
#### <a name="to-run-this-sample"></a>Aby uruchomić ten przykład  
  
1.  Dodaj nową aplikację konsoli przepływu pracy do rozwiązania.  
  
2.  Dodaj odwołanie do **ExpressionTextBoxSample** projektu z nowego projektu aplikacji Konsolowej przepływu pracy.  
  
3.  Skompiluj rozwiązanie.  
  
4.  Przeciągnij **MultiAssign** działania z przybornika i upuść ją do przepływu pracy.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\ExpressionTextBox`  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Activities.Presentation.View.ExpressionTextBox>  
 [Tworzenie aplikacji przy użyciu Projektanta przepływu pracy](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
