---
title: Drzewo elementów modelu programowania
ms.date: 03/30/2017
ms.assetid: 0229efde-19ac-4bdc-a187-c6227a7bd1a5
ms.openlocfilehash: f14b140fdac95f3763cc5625841a725793876fa4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142696"
---
# <a name="programming-model-item-tree"></a>Drzewo elementów modelu programowania
W tym przykładzie pokazano, jak poruszać się po <xref:System.Activities.Presentation.Model.ModelItem> drzewie przy użyciu deklaratywnego powiązania danych z widoku drzewa programu Windows Presentation Foundation (WPF).

## <a name="sample-details"></a>Przykładowe szczegóły
 Drzewo <xref:System.Activities.Presentation.Model.ModelItem> jest abstrakcja, który jest używany przez infrastrukturę Projektanta przepływu pracy systemu Windows, aby udostępnić dane dotyczące wystąpienia źródłowego są edytowane. Poniższa ilustracja przedstawia różne warstwy infrastruktury w projektancie przepływu pracy.

 ![Diagram przedstawiający architekturę projektanta przepływu pracy.](./media/programming-model-item-tree/workflow-designer-architecture.jpg)

 A <xref:System.Activities.Presentation.Model.ModelItem> składa się ze wskaźnika do wartości podstawowej, a także kolekcji <xref:System.Activities.Presentation.Model.ModelProperty> obiektów. Obiekt <xref:System.Activities.Presentation.Model.ModelProperty> z kolei składa się z danych, takich jak nazwa i typ właściwości, a następnie <xref:System.Activities.Presentation.Model.ModelItem>wskaźnik do wartości, która z kolei jest inny . Konwerter wartości służy do <xref:System.Activities.Presentation.Model.ModelItem>manipulowania niektórymi <xref:System.Activities.Presentation.Model.ModelProperty> s zwróconych z a, aby były wyświetlane poprawnie w widoku drzewa. Następnie w przykładzie pokazano, jak <xref:System.Activities.Presentation.Model.ModelItem> należy bezwzględnie zaprogramować względem drzewa przy użyciu składni imperatywnej, jak pokazano w poniższym przykładzie.

```csharp
ModelItem mi = wd.Context.Services.GetService<ModelService>().Root;
ModelProperty mp = mi.Properties["Activities"];
mp.Collection.Add(new Persist());
ModelItem justAdded = mp.Collection.Last();
justAdded.Properties["DisplayName"].SetValue("new name");
```

#### <a name="to-use-this-sample"></a>Aby użyć tej próbki

1. Otwórz rozwiązanie ProgrammingModelItemTree.sln w programie Visual Studio 2010.

2. Skompiluj rozwiązanie, wybierając **rozwiązanie kompilacji** z menu **Kompilacja.**

3. Naciśnij klawisz F5, aby uruchomić aplikację. Następnie wyświetlany jest formularz WPF.

4. Kliknij przycisk **Załaduj WF,** aby załadować <xref:System.Activities.Presentation.Model.ModelItem> i powiązać go z widokiem drzewa.

5. Kliknięcie przycisku **Zmień drzewo elementów modelu** wykonuje poprzedni kod, aby dodać element do drzewa i ustawić właściwość.

> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ProgrammingModelItemTree`  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Data.IValueConverter>
