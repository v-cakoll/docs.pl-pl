---
title: Używanie zakresu edycji
ms.date: 03/30/2017
ms.assetid: 79306f9e-318b-4687-9863-8b93d1841716
ms.openlocfilehash: 3e99610fda78e50f6d6eb72c38ecc82bdc96b5a2
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715549"
---
# <a name="using-editing-scope"></a>Używanie zakresu edycji
Ten przykład pokazuje, jak utworzyć wsadowy zestaw zmian, aby można je było cofnąć w pojedynczej niepodzielnej jednostce. Domyślnie akcje podejmowane przez autora projektanta działań są automatycznie integrowane z systemem cofania/ponawiania.  
  
## <a name="demonstrates"></a>Przedstawia  
 Edytowanie zakresu i cofanie i ponawianie.  
  
## <a name="discussion"></a>Dyskusji  
 Ten przykład ilustruje sposób tworzenia wsadowego zestawu zmian w drzewie <xref:System.Activities.Presentation.Model.ModelItem> w ramach jednej jednostki pracy. Należy pamiętać, że w przypadku powiązania do <xref:System.Activities.Presentation.Model.ModelItem> wartości bezpośrednio z projektanta WPF zmiany są stosowane automatycznie. Ten przykład pokazuje, co należy zrobić, gdy wiele zmian jest wykonywanych za pomocą bezwzględnego kodu, a nie pojedynczej zmiany.  
  
 W tym przykładzie dodano trzy działania. Po rozpoczęciu edycji <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> jest wywoływana w wystąpieniu <xref:System.Activities.Presentation.Model.ModelItem>. Zmiany wprowadzone w drzewie <xref:System.Activities.Presentation.Model.ModelItem> w tym zakresie edytowania są przetwarzane wsadowo. Polecenie <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> zwraca <xref:System.Activities.Presentation.Model.EditingScope>, którego można użyć do kontrolowania tego wystąpienia. <xref:System.Activities.Presentation.Model.EditingScope.OnComplete%2A> lub <xref:System.Activities.Presentation.Model.EditingScope.OnRevert%2A> można wywołać w celu zatwierdzenia lub przywrócenia zakresu edycji.  
  
 Można również zagnieżdżać <xref:System.Activities.Presentation.Model.EditingScope> obiektów, co pozwala na śledzenie wielu zestawów zmian w ramach większego zakresu edycji i można je kontrolować indywidualnie. Scenariusz, który może używać tej funkcji, będzie miał zastosowanie, gdy zmiany z wielu okien dialogowych muszą zostać zatwierdzone lub cofnięte oddzielnie, przy czym wszystkie zmiany są traktowane jako pojedyncza operacja niepodzielna. W tym przykładzie zakresy edycji są ułożone w stos przy użyciu <xref:System.Collections.ObjectModel.ObservableCollection%601> typu <xref:System.Activities.Presentation.Model.ModelEditingScope>. <xref:System.Collections.ObjectModel.ObservableCollection%601> jest używana, aby głębokość zagnieżdżenia mogła być obserwowana na powierzchni projektanta.  
  
## <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Kompiluj i uruchamiaj przykład, a następnie użyj przycisków po lewej stronie, aby zmodyfikować przepływ pracy.  
  
2. Kliknij pozycję **Otwórz zakres edytowania**.  
  
    1. To polecenie wywołuje <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A>, które tworzy zakres edycji i wypchnięcie go na stos edycji.  
  
    2. Do wybranych <xref:System.Activities.Presentation.Model.ModelItem>są dodawane trzy działania. Należy pamiętać, że jeśli zakres edycji nie został otwarty z <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A>, na kanwie projektanta zostaną wyświetlone trzy nowe działania. Ponieważ ta operacja nadal oczekuje na <xref:System.Activities.Presentation.Model.EditingScope>, Projektant nie został jeszcze zaktualizowany.  
  
3. Naciśnij klawisz **Zamknij edytowanie zakresu** , aby zatwierdzić zakres edycji. W projektancie pojawiają się trzy działania.  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\UsingEditingScope`
