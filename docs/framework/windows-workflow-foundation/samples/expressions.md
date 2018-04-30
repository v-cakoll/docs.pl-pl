---
title: Expressions2
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 43a85905-77b5-4893-bb38-1cb9b293d69d
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c8470a3bb93385724f50e18d25c148ee609c3a77
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="expressions"></a>Wyrażenia
W tym przykładzie pokazano, jak używać wyrażeń podstawowe w przepływie pracy. Składa się z przepływu pracy, który oblicza wynagrodzenie podstawowe statystyki dla dwóch pracowników fikcyjnej firmy. Dwie klasy `Employee` i `SalaryStats`, są zdefiniowane w Employee.cs i SalaryStats.cs. Te klasy są używane w przepływie pracy, który pokazuje, jak wykonywać proste operacje arytmetyczne i ciąg właściwości zmiennych typów złożonych.  
  
 Przepływ pracy obliczania wynagrodzenie jest zdefiniowany zarówno w języku XAML, a w języku C#, aby zademonstrować dwa style tworzenia. Wersja języka XAML znajduje się w SalaryCalculation.xaml i można wyświetlać i edytować w Projektancie przepływów pracy. Wersja języka C# znajduje się w pliku Program.cs. Wyrażenia używane w języku XAML jest zgodny ze składnią języka Visual Basic i użyj <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> i <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> działania wyrażenia do wykonania. Aby uzyskać więcej informacji na temat, zobacz wyrażeń języka Visual Basic [wyrażeń Visual Basic](http://go.microsoft.com/fwlink/?LinkId=165912). Z drugiej strony wyrażenia w języku C# są zapisywane jako wyrażenia lambda i użyj <xref:System.Activities.Expressions.LambdaValue%601> i <xref:System.Activities.Expressions.LambdaReference%601> działania wyrażeń. Wyrażeń jak wyrażenia lambda umożliwia kompilator języka C# w celu zapewnienia wyróżnianie składni i statyczne weryfikacji. Aby uzyskać więcej informacji na temat wyrażeń lambda w języku C#, zobacz [wyrażenia Lambda (C# przewodnik programowania w języku)](http://go.microsoft.com/fwlink/?LinkId=182082). Jeśli przepływ pracy został utworzony w kodzie za pomocą języka Visual Basic, Visual Basic wyrażenia lambda są używane. Aby uzyskać więcej informacji na temat wyrażeń lambda w języku Visual Basic, zobacz [wyrażenia Lambda (Visual Basic)](http://go.microsoft.com/fwlink/?LinkId=152437). Aby uzyskać więcej informacji na temat o tworzeniu przepływów pracy przy użyciu kodu, zobacz [tworzenia przepływów pracy, działań i kod Imperatywne za pomocą wyrażenia](../../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md).  
  
#### <a name="to-run-the-sample"></a>Aby uruchomić przykładowy  
  
1.  Otwórz rozwiązanie Expressions.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Naciśnij klawisze CTRL + SHIFT + B do budowania rozwiązania lub wybierz **Kompiluj rozwiązanie** z **kompilacji** menu.  
  
    > [!NOTE]
    >  Aby otworzyć SalaryCalculation.xaml w projektancie programu Visual Studio, należy najpierw skompilować projekt, aby upewnić się, że `Employee` i `SalaryStats` klasy są dostępne do projektanta.  
  
3.  Gdy kompilacja zakończyła się pomyślnie, naciśnij klawisz F5 lub wybierz **Rozpocznij debugowanie** z **debugowania** menu. Można również nacisnąć klawisze Ctrl + F5 lub wybierz **uruchomić bez debugowania** z **debugowania** menu, aby uruchomić bez debugowania.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Expressions`