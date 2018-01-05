---
title: "Za pomocą edycji zakresu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 79306f9e-318b-4687-9863-8b93d1841716
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d6f20ff0577e43106886f5910b8f6a69578d1b3e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="using-editing-scope"></a>Za pomocą edycji zakresu
W tym przykładzie pokazano, jak partii zestaw zmian, dzięki czemu mogą zostać cofnięte w pojedynczą jednostkę atomic. Domyślnie akcje wykonywane przez autora projektanta działania są automatycznie zintegrowane systemu Cofnij/Ponów.  
  
## <a name="demonstrates"></a>Demonstracje  
 Edytowanie zakresu i Cofnij i ponów.  
  
## <a name="discussion"></a>Omówienie  
 W tym przykładzie pokazano, jak zestaw zmian do partii <xref:System.Activities.Presentation.Model.ModelItem> drzewa w pojedynczą jednostkę pracy. Należy pamiętać, że podczas wiązania z <xref:System.Activities.Presentation.Model.ModelItem> wartości bezpośrednio z projektanta WPF, zmiany zostaną zastosowane automatycznie. W przykładzie pokazano, co należy zrobić po wielu do można umieścić w partii zmian za pomocą kodu nadrzędnych, a nie jednej zmiany.  
  
 W tym przykładzie trzy działania są dodawane. Po rozpoczęciu edycji <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> jest wywoływana w wystąpieniu <xref:System.Activities.Presentation.Model.ModelItem>. Zmiany wprowadzone w <xref:System.Activities.Presentation.Model.ModelItem> są przetwarzane wsadowo drzewa w ramach tego zakresu edycji. <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> Polecenie zwraca <xref:System.Activities.Presentation.Model.EditingScope>, które mogą służyć do kontrolowania tego wystąpienia. Albo <xref:System.Activities.Presentation.Model.EditingScope.OnComplete%2A> lub <xref:System.Activities.Presentation.Model.EditingScope.OnRevert%2A> można wywołać w celu zatwierdzenia albo lub Przywróć edycji zakresu.  
  
 Można zagnieżdżać <xref:System.Activities.Presentation.Model.EditingScope> obiektów, co pozwala na wiele zestawów zmian mają być śledzone jako część większych edycji zakresu i można kontrolować osobno. Scenariusz, w którym mogą korzystać z tej funkcji może dochodzić do zmiany z wielu okien dialogowych muszą być zadeklarowane lub przywrócić oddzielnie, wszystkie zmiany są traktowane jako pojedynczej Atomowej operacji. W tym przykładzie są ułożone, przy użyciu zakresów edycji <xref:System.Collections.ObjectModel.ObservableCollection%601> typu <xref:System.Activities.Presentation.Model.ModelEditingScope>. <xref:System.Collections.ObjectModel.ObservableCollection%601> Jest używany, dzięki czemu można zaobserwować głębokość zagnieżdżenia na powierzchnię projektanta.  
  
## <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Kompilacji i uruchomić przykładowy, a następnie użyj przycisków po lewej stronie, aby zmodyfikować przepływ pracy.  
  
2.  Kliknij przycisk **Otwórz edycji zakresu**.  
  
    1.  To polecenie wymaga <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> tworzy zakres edycji i wypchnięcia jej na stosie edycji.  
  
    2.  Trzy działania są dodawane do wybranego <xref:System.Activities.Presentation.Model.ModelItem>. Należy pamiętać, że jeśli edycji zakresu nie był on otwarty z <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A>, trzy nowe działania pojawią się na kanwie projektanta. Ponieważ ta operacja jest nadal oczekujące w <xref:System.Activities.Presentation.Model.EditingScope>, Projektant nie jest jeszcze zaktualizowana.  
  
3.  Naciśnij klawisz **Zamknij zakresu edycji** można zatwierdzić edycji zakresu. Trzy działania są wyświetlane w projektancie.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\UsingEditingScope`
