---
title: Używanie zakresu edycji
ms.date: 03/30/2017
ms.assetid: 79306f9e-318b-4687-9863-8b93d1841716
ms.openlocfilehash: 386c94e5c6761bb704efc9e48723d0e91a4aaf6b
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70037800"
---
# <a name="using-editing-scope"></a>Używanie zakresu edycji
Ten przykład pokazuje, jak utworzyć wsadowy zestaw zmian, aby można je było cofnąć w pojedynczej niepodzielnej jednostce. Domyślnie akcje podejmowane przez autora projektanta działań są automatycznie integrowane z systemem cofania/ponawiania.  
  
## <a name="demonstrates"></a>Demonstracje  
 Edytowanie zakresu i cofanie i ponawianie.  
  
## <a name="discussion"></a>Dyskusji  
 Ten przykład pokazuje, jak wsadowo zestaw zmian <xref:System.Activities.Presentation.Model.ModelItem> w drzewie w ramach pojedynczej jednostki pracy. Należy pamiętać, że podczas <xref:System.Activities.Presentation.Model.ModelItem> tworzenia powiązań z wartościami bezpośrednio z projektanta WPF zmiany są stosowane automatycznie. Ten przykład pokazuje, co należy zrobić, gdy wiele zmian jest wykonywanych za pomocą bezwzględnego kodu, a nie pojedynczej zmiany.  
  
 W tym przykładzie dodano trzy działania. Po rozpoczęciu <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> edycji jest wywoływana w <xref:System.Activities.Presentation.Model.ModelItem>wystąpieniu. Zmiany wprowadzone <xref:System.Activities.Presentation.Model.ModelItem> w drzewie w tym zakresie edycji są przetwarzane wsadowo. Polecenie zwraca element <xref:System.Activities.Presentation.Model.EditingScope>, który może służyć do kontrolowania tego wystąpienia. <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> <xref:System.Activities.Presentation.Model.EditingScope.OnComplete%2A> Lub<xref:System.Activities.Presentation.Model.EditingScope.OnRevert%2A> można wywołać w celu zatwierdzenia lub przywrócenia zakresu edycji.  
  
 Można również zagnieżdżać <xref:System.Activities.Presentation.Model.EditingScope> obiekty, co pozwala na śledzenie wielu zestawów zmian w ramach większego zakresu edycji i może być sterowane pojedynczo. Scenariusz, który może używać tej funkcji, będzie miał zastosowanie, gdy zmiany z wielu okien dialogowych muszą zostać zatwierdzone lub cofnięte oddzielnie, przy czym wszystkie zmiany są traktowane jako pojedyncza operacja niepodzielna. W tym przykładzie zakresy edycji są ułożone przy użyciu <xref:System.Collections.ObjectModel.ObservableCollection%601> typu. <xref:System.Activities.Presentation.Model.ModelEditingScope> <xref:System.Collections.ObjectModel.ObservableCollection%601> Jest używany, aby głębokość zagnieżdżenia mogła być obserwowana na powierzchni projektanta.  
  
## <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Kompiluj i uruchamiaj przykład, a następnie użyj przycisków po lewej stronie, aby zmodyfikować przepływ pracy.  
  
2. Kliknij pozycję **Otwórz zakres edytowania**.  
  
    1. To polecenie wywołuje <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> , aby utworzyć zakres edycji i wypchnąć go na stos edycji.  
  
    2. Następnie zostaną dodane trzy działania do wybranego <xref:System.Activities.Presentation.Model.ModelItem>. Należy pamiętać, że jeśli zakres edycji nie został otwarty za <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A>pomocą programu, na kanwie projektanta zostaną wyświetlone trzy nowe działania. Ponieważ ta operacja nadal oczekuje w programie <xref:System.Activities.Presentation.Model.EditingScope>, Projektant nie został jeszcze zaktualizowany.  
  
3. Naciśnij klawisz **Zamknij edytowanie zakresu** , aby zatwierdzić zakres edycji. W projektancie pojawiają się trzy działania.  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\UsingEditingScope`
