---
title: Używanie zakresu edycji
ms.date: 03/30/2017
ms.assetid: 79306f9e-318b-4687-9863-8b93d1841716
ms.openlocfilehash: d1e251abf2dd4d3f7ca15d66a4f5ea96e273a351
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623823"
---
# <a name="using-editing-scope"></a>Używanie zakresu edycji
Niniejszy przykład pokazuje jak dzielić na partie zestaw zmian, dzięki czemu mogą zostać cofnięte w pojedynczą jednostkę atomic. Domyślnie akcje wykonywane przez autora projektanta działań są automatycznie zintegrowane system Cofnij/Ponów.  
  
## <a name="demonstrates"></a>Demonstracje  
 Edytowanie zakresu i Cofnij i ponów.  
  
## <a name="discussion"></a>Dyskusja  
 W tym przykładzie pokazano, jak zestaw zmian do partii <xref:System.Activities.Presentation.Model.ModelItem> drzewa w pojedynczą jednostkę pracy. Należy pamiętać, że podczas tworzenia wiązania do <xref:System.Activities.Presentation.Model.ModelItem> wartości bezpośrednio z projektanta WPF, zmiany zostaną zastosowane automatycznie. Niniejszy przykład pokazuje, co należy zrobić po wielu do uwzględnienia w partii zmian przy użyciu kodu imperatywnego, zamiast pojedynczej zmiany.  
  
 W tym przykładzie trzy czynności są dodawane. Po rozpoczęciu edycji <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> jest wywoływana w wystąpieniu <xref:System.Activities.Presentation.Model.ModelItem>. Zmiany wprowadzone do <xref:System.Activities.Presentation.Model.ModelItem> drzewa w ramach tego zakresu edycji są przetwarzane wsadowo. <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> Polecenie <xref:System.Activities.Presentation.Model.EditingScope>, który może służyć do kontrolowania tego wystąpienia. Albo <xref:System.Activities.Presentation.Model.EditingScope.OnComplete%2A> lub <xref:System.Activities.Presentation.Model.EditingScope.OnRevert%2A> może być wywoływana albo zatwierdzenia lub Przywróć zakresu edycji.  
  
 Można także zagnieżdżać <xref:System.Activities.Presentation.Model.EditingScope> obiektów, które umożliwia wielu zestawów zmiany mają być śledzone jako część większych edycji zakres i można sterować oddzielnie. Scenariusz, w którym mogą korzystać z tej funkcji będzie podczas zmiany z wiele okien dialogowych musi być zadeklarowane lub przywrócić oddzielnie, w przypadku wszystkich zmian, które są traktowane jako jednej niepodzielnej operacji. W tym przykładzie są ułożone, za pomocą edycji zakresy <xref:System.Collections.ObjectModel.ObservableCollection%601> typu <xref:System.Activities.Presentation.Model.ModelEditingScope>. <xref:System.Collections.ObjectModel.ObservableCollection%601> Jest używany, dzięki czemu można zaobserwować głębokość zagnieżdżenia na powierzchni projektowej.  
  
## <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1. Tworzenie i uruchamianie aplikacji przykładowej, a następnie użyj przycisków po lewej stronie, aby zmodyfikować przepływ pracy.  
  
2. Kliknij przycisk **Otwórz zakresu edycji**.  
  
    1. To polecenie wymaga <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> , tworzy zakresu edycji i wypycha go na stosie edycji.  
  
    2. Trzy czynności zostaną następnie dodane do wybranych <xref:System.Activities.Presentation.Model.ModelItem>. Należy pamiętać, że jeśli zakresu edycji nie był on otwarty przy użyciu <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A>, trzy nowe działania zostanie wyświetlony na kanwie projektanta. Ponieważ ta operacja jest nadal oczekujące w ramach <xref:System.Activities.Presentation.Model.EditingScope>, Projektant nie jest jeszcze zaktualizowane.  
  
3. Naciśnij klawisz **Zamknij zakresu edycji** zatwierdzić zakresu edycji. Trzy czynności są wyświetlane w projektancie.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\UsingEditingScope`
