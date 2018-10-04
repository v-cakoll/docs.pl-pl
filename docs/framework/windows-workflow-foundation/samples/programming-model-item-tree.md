---
title: Drzewo elementów modelu programowania
ms.date: 03/30/2017
ms.assetid: 0229efde-19ac-4bdc-a187-c6227a7bd1a5
ms.openlocfilehash: f6f625ae7cd5251f7d7935d018142b32ea71b13f
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48776509"
---
# <a name="programming-model-item-tree"></a>Drzewo elementów modelu programowania
W tym przykładzie pokazano, jak nawigować po <xref:System.Activities.Presentation.Model.ModelItem> drzewa za pomocą powiązania dane deklaratywne w widoku drzewa Windows Presentation Foundation (WPF).

## <a name="sample-details"></a>Przykład szczegółów
 <xref:System.Activities.Presentation.Model.ModelItem> Drzewo jest abstrakcji, która jest używana przez [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] infrastruktury w celu ujawnienia danych o wystąpieniu bazowego, edytowany. Na poniższej ilustracji jest sceny z różnych warstw infrastruktury w [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].

 ![Architektura projektanta przepływu pracy](../../../../docs/framework/windows-workflow-foundation/samples/media/workflowdesignerarch.JPG "WorkflowDesignerArch")

 A <xref:System.Activities.Presentation.Model.ModelItem> składa się z wskaźnik do podstawowej wartości, a także kolekcję <xref:System.Activities.Presentation.Model.ModelProperty> obiektów. A <xref:System.Activities.Presentation.Model.ModelProperty> obiekt z kolei składa się z danych, takie jak nazwa i typ właściwości, a następnie wskaźnik do wartości, która z kolei jest kolejnym <xref:System.Activities.Presentation.Model.ModelItem>. Konwerter wartości służy do modyfikowania niektórych <xref:System.Activities.Presentation.Model.ModelItem>s zwróciło <xref:System.Activities.Presentation.Model.ModelProperty> aby były one są prawidłowo wyświetlane w widoku drzewa. Przykład następnie pokazano, jak programować obowiązkowo przy użyciu <xref:System.Activities.Presentation.Model.ModelItem> drzewa za pomocą składnia imperatywna, jak pokazano w poniższym przykładzie.

```csharp
ModelItem mi = wd.Context.Services.GetService<ModelService>().Root;
ModelProperty mp = mi.Properties["Activities"];
mp.Collection.Add(new Persist());
ModelItem justAdded = mp.Collection.Last();
justAdded.Properties["DisplayName"].SetValue("new name");
```

#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu

1.  Otwórz rozwiązanie ProgrammingModelItemTree.sln w programie Visual Studio 2010.

2.  Skompiluj rozwiązanie, wybierając **Kompiluj rozwiązanie** z **kompilacji** menu.

3.  Naciśnij klawisz F5, aby uruchomić aplikację. [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] Następnie zostanie wyświetlony formularz.

4.  Kliknij przycisk **obciążenia WF** przycisk, aby załadować <xref:System.Activities.Presentation.Model.ModelItem> i powiąż go w widoku drzewa.

5.  Klikając **drzewo elementów modelu zmiany** przycisk wykonuje poprzedni kod, aby dodać element do drzewa i ustawić właściwość.

> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ProgrammingModelItemTree`  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Data.IValueConverter>
