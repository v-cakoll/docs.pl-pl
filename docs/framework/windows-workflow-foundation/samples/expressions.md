---
title: Expressions2
ms.date: 03/30/2017
ms.assetid: 43a85905-77b5-4893-bb38-1cb9b293d69d
ms.openlocfilehash: e852b62e6d0b6b4b3ddc19b197902de5325310a1
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43799294"
---
# <a name="expressions"></a>Wyrażenia
W tym przykładzie pokazano, jak użyć podstawowa wyrażeń w przepływie pracy. Składa się z przepływu pracy, który oblicza statystyki wynagrodzenia podstawowego dla dwóch pracowników fikcyjnej firmy. Dwie klasy `Employee` i `SalaryStats`, są definiowane w Employee.cs i SalaryStats.cs. Te klasy są używane w przepływie pracy, który pokazuje, jak wykonywać proste operacje arytmetyczne i ciągu dla właściwości zmiennych typów złożonych.  
  
 Przepływ pracy obliczeń wynagrodzenia zdefiniowano zarówno w XAML i C#, aby zademonstrować dwa style tworzenia pakietów administracyjnych. Wersja XAML znajduje się w SalaryCalculation.xaml i można wyświetlać i edytować w Projektancie przepływu pracy. Wersja języka C# znajduje się w pliku Program.cs. Wyrażenia używane w XAML odpowiada składni języka Visual Basic, a następnie użyj <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> i <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> wyrażenia działań do wykonania. Aby uzyskać więcej informacji na temat języka Visual Basic, zobacz wyrażenia [wyrażeń języka Visual Basic](https://go.microsoft.com/fwlink/?LinkId=165912). Z drugiej strony, są zapisywane w postaci wyrażenia lambda wyrażenia w języku C# i użyj <xref:System.Activities.Expressions.LambdaValue%601> i <xref:System.Activities.Expressions.LambdaReference%601> wyrażenia działań. Pisanie wyrażeń jak wyrażenia lambda umożliwia kompilator języka C#, aby zapewnić, wyróżnianie składni i statyczne weryfikacji. Aby uzyskać więcej informacji na temat wyrażeń lambda w języku C#, zobacz [wyrażenia Lambda (C# Programming Guide)](https://go.microsoft.com/fwlink/?LinkId=182082). Jeśli przepływ pracy został utworzony w kodzie przy użyciu języka Visual Basic, Visual Basic, wyrażenia lambda są używane. Aby uzyskać więcej informacji na temat wyrażeń lambda w języku Visual Basic, zobacz [wyrażenia Lambda (Visual Basic)](https://go.microsoft.com/fwlink/?LinkId=152437). Aby uzyskać informacje o tworzeniu przepływów pracy przy użyciu kodu, zobacz [tworzenia przepływów pracy, działań i wyrażeń przy użyciu technologii kodu](../../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md).  
  
#### <a name="to-run-the-sample"></a>Aby uruchomić przykład  
  
1.  Otwórz rozwiązanie Expressions.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Naciśnij klawisze CTRL + SHIFT + B, aby skompilować rozwiązanie lub wybierz **Kompiluj rozwiązanie** z **kompilacji** menu.  
  
    > [!NOTE]
    >  Aby otworzyć SalaryCalculation.xaml w Projektancie Visual Studio, należy najpierw skompilować projekt, aby upewnić się, że `Employee` i `SalaryStats` klasy są dostępne do projektanta.  
  
3.  Gdy kompilacja zakończyła się pomyślnie, naciśnij klawisz F5 lub wybierz **Rozpocznij debugowanie** z **debugowania** menu. Można również nacisnąć klawisze Ctrl + F5 lub wybierz **Rozpocznij bez debugowania** z **debugowania** menu, aby uruchomić bez debugowania.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Expressions`