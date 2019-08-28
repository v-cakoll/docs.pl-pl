---
title: Drzewo elementów modelu programowania
ms.date: 03/30/2017
ms.assetid: 0229efde-19ac-4bdc-a187-c6227a7bd1a5
ms.openlocfilehash: f2d89cb2a3b0f6167f043148ea793ec1c264a556
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038173"
---
# <a name="programming-model-item-tree"></a>Drzewo elementów modelu programowania
Ten przykład pokazuje, jak nawigować po <xref:System.Activities.Presentation.Model.ModelItem> drzewie przy użyciu deklaratywnego powiązania danych z widoku drzewa Windows Presentation Foundation (WPF).

## <a name="sample-details"></a>Przykładowe szczegóły
 Drzewo jest abstrakcją używaną [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] przez infrastrukturę do ujawnienia danych o edytowanym wystąpieniu. <xref:System.Activities.Presentation.Model.ModelItem> Poniższa ilustracja przedstawia różne warstwy infrastruktury w ramach programu [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].

 ![Diagram przedstawiający architekturę Projektant przepływu pracy.](./media/programming-model-item-tree/workflow-designer-architecture.jpg)

 A <xref:System.Activities.Presentation.Model.ModelItem> składa się ze wskaźnika do podstawowej wartości, a także do <xref:System.Activities.Presentation.Model.ModelProperty> kolekcji obiektów. Obiekt z kolei składa się z danych, takich jak nazwa i typ właściwości, a następnie wskaźnik do wartości, która z kolei jest inna <xref:System.Activities.Presentation.Model.ModelItem>. <xref:System.Activities.Presentation.Model.ModelProperty> Konwerter wartości służy do manipulowania niektórymi z <xref:System.Activities.Presentation.Model.ModelItem>elementów s zwróconych <xref:System.Activities.Presentation.Model.ModelProperty> z elementu, aby były prawidłowo wyświetlane w widoku drzewa. W przykładzie pokazano, jak bezwzględnie programowo korzystać <xref:System.Activities.Presentation.Model.ModelItem> z drzewa przy użyciu bezwzględnej składni, jak pokazano w poniższym przykładzie.

```csharp
ModelItem mi = wd.Context.Services.GetService<ModelService>().Root;
ModelProperty mp = mi.Properties["Activities"];
mp.Collection.Add(new Persist());
ModelItem justAdded = mp.Collection.Last();
justAdded.Properties["DisplayName"].SetValue("new name");
```

#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu

1. Otwórz rozwiązanie ProgrammingModelItemTree. sln w programie Visual Studio 2010.

2. Skompiluj rozwiązanie, wybierając opcję **Kompiluj rozwiązanie** w menu **kompilacja** .

3. Naciśnij klawisz F5, aby uruchomić aplikację. Zostanie wyświetlony formularz WPF.

4. Kliknij przycisk **Załaduj WF** , aby załadować <xref:System.Activities.Presentation.Model.ModelItem> i powiązać go z widokiem drzewa.

5. Kliknięcie przycisku **Zmień model elementu modelu** wykonuje poprzedni kod, aby dodać element do drzewa i ustawić właściwość.

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ProgrammingModelItemTree`  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Data.IValueConverter>
