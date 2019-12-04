---
title: Drzewo elementów modelu programowania
ms.date: 03/30/2017
ms.assetid: 0229efde-19ac-4bdc-a187-c6227a7bd1a5
ms.openlocfilehash: efda69ac568b0ad9c5fdcf4d42722c5b7dadd3f3
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715665"
---
# <a name="programming-model-item-tree"></a>Drzewo elementów modelu programowania
Ten przykład pokazuje, jak nawigować po drzewie <xref:System.Activities.Presentation.Model.ModelItem> przy użyciu deklaratywnego powiązania danych z widoku drzewa Windows Presentation Foundation (WPF).

## <a name="sample-details"></a>Przykładowe szczegóły
 Drzewo <xref:System.Activities.Presentation.Model.ModelItem> jest abstrakcją używaną przez infrastrukturę Projektant przepływu pracy systemu Windows, aby uwidocznić dane dotyczące edytowanego wystąpienia. Poniższa ilustracja przedstawia różne warstwy infrastruktury w ramach Projektant przepływu pracy.

 ![Diagram przedstawiający architekturę Projektant przepływu pracy.](./media/programming-model-item-tree/workflow-designer-architecture.jpg)

 <xref:System.Activities.Presentation.Model.ModelItem> składa się ze wskaźnika do podstawowej wartości, a także do kolekcji obiektów <xref:System.Activities.Presentation.Model.ModelProperty>. Obiekt <xref:System.Activities.Presentation.Model.ModelProperty> z kolei składa się z danych, takich jak nazwa i typ właściwości, a następnie wskaźnik do wartości, która z kolei jest kolejną <xref:System.Activities.Presentation.Model.ModelItem>. Konwerter wartości służy do manipulowania niektórymi <xref:System.Activities.Presentation.Model.ModelItem>s zwróconymi z <xref:System.Activities.Presentation.Model.ModelProperty>, aby były prawidłowo wyświetlane w widoku drzewa. W przykładzie pokazano, jak bezwzględnie programowo korzystać z drzewa <xref:System.Activities.Presentation.Model.ModelItem> przy użyciu bezwzględnej składni, jak pokazano w poniższym przykładzie.

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

4. Kliknij przycisk **Załaduj WF** , aby załadować <xref:System.Activities.Presentation.Model.ModelItem> i powiązać je z widokiem drzewa.

5. Kliknięcie przycisku **Zmień model elementu modelu** wykonuje poprzedni kod, aby dodać element do drzewa i ustawić właściwość.

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ProgrammingModelItemTree`  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Data.IValueConverter>
