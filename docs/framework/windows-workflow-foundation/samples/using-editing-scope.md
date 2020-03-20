---
title: Używanie zakresu edycji
ms.date: 03/30/2017
ms.assetid: 79306f9e-318b-4687-9863-8b93d1841716
ms.openlocfilehash: 13f23289f0b764b80f971d3e514f3b12acfbfffc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142657"
---
# <a name="using-editing-scope"></a>Używanie zakresu edycji
W tym przykładzie pokazano, jak partii zestaw zmian, dzięki czemu można je cofnąć w jednej jednostce atomowej. Domyślnie akcje podejmowane przez autora projektanta działań są automatycznie integrowane z systemem Cofnij/Ponawiaj.  
  
## <a name="demonstrates"></a>Demonstracje  
 Zakres edycji oraz Cofanie i ponawianie.  
  
## <a name="discussion"></a>Dyskusji  
 W tym przykładzie pokazano, jak partii <xref:System.Activities.Presentation.Model.ModelItem> zestaw zmian do drzewa w ciągu jednej jednostki pracy. Należy zauważyć, <xref:System.Activities.Presentation.Model.ModelItem> że podczas wiązania z wartościami bezpośrednio z projektanta WPF zmiany są stosowane automatycznie. W tym przykładzie pokazano, co należy zrobić, gdy wiele zmian, które mają być wsadowe są wprowadzane za pomocą kodu imperatywu, a nie pojedynczej zmiany.  
  
 W tym przykładzie są dodawane trzy działania. Po rozpoczęciu <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> edycji jest wywoływana na wystąpienie <xref:System.Activities.Presentation.Model.ModelItem>. Zmiany wprowadzone <xref:System.Activities.Presentation.Model.ModelItem> w drzewie w tym zakresie edycji są wsadowe. Polecenie <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> zwraca <xref:System.Activities.Presentation.Model.EditingScope>program , który może służyć do sterowania tym wystąpieniem. Albo <xref:System.Activities.Presentation.Model.EditingScope.OnComplete%2A> można <xref:System.Activities.Presentation.Model.EditingScope.OnRevert%2A> wywołać, aby zatwierdzić lub przywrócić zakres edycji.  
  
 Można również <xref:System.Activities.Presentation.Model.EditingScope> zagnieżdżać obiekty, co pozwala na śledzenie wielu zestawów zmian w ramach większego zakresu edycji i może być kontrolowane indywidualnie. Scenariusz, który może korzystać z tej funkcji będzie, gdy zmiany z wielu okien dialogowych muszą być zatwierdzone lub przywrócone oddzielnie, ze wszystkimi zmianami są traktowane jako pojedynczej operacji niepodzielny. W tym przykładzie zakresy edycji są <xref:System.Collections.ObjectModel.ObservableCollection%601> układane przy użyciu typu <xref:System.Activities.Presentation.Model.ModelEditingScope>. Jest <xref:System.Collections.ObjectModel.ObservableCollection%601> używany w taki sposób, aby można było zaobserwować głębokość zagnieżdżania na powierzchni projektanta.  
  
## <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Skompiluj i uruchom przykład, a następnie użyj przycisków po lewej stronie, aby zmodyfikować przepływ pracy.  
  
2. Kliknij **pozycję Otwórz zakres edycji**.  
  
    1. To polecenie <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> wywołuje, który tworzy zakres edycji i wypycha go do stosu edycji.  
  
    2. Trzy działania są następnie dodawane do wybranego <xref:System.Activities.Presentation.Model.ModelItem>. Należy zauważyć, że jeśli zakres edycji nie został otwarty z <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A>, trzy nowe działania pojawią się na kanwie projektanta. Ponieważ ta operacja jest <xref:System.Activities.Presentation.Model.EditingScope>nadal w toku w ramach, projektant nie jest jeszcze zaktualizowany.  
  
3. Naciśnij **pozycję Zamknij zakres edycji,** aby zatwierdzić zakres edycji. Trzy działania pojawiają się w projektancie.  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\UsingEditingScope`
