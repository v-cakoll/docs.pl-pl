---
title: "Drzewo elementów modelu programowania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0229efde-19ac-4bdc-a187-c6227a7bd1a5
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 18de9d7f9cedc40a6c143a4dae5567c9acf2cf88
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="programming-model-item-tree"></a>Drzewo elementów modelu programowania
W tym przykładzie pokazano, jak przechodzić <xref:System.Activities.Presentation.Model.ModelItem> drzewa używanie powiązania danych deklaratywne z [!INCLUDE[avalon1](../../../../includes/avalon1-md.md)] widok drzewa.  
  
## <a name="sample-details"></a>Szczegóły próbki  
 <xref:System.Activities.Presentation.Model.ModelItem> Drzewo jest abstrakcji, która jest używana przez [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] infrastruktury do udostępnienia danych dotyczących podstawowej wystąpienie edytowany. Na rysunku poniżej przedstawiono sceny infrastruktury w różnych warstwach [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].  
  
 ![Architektura projektanta przepływów pracy](../../../../docs/framework/windows-workflow-foundation/samples/media/workflowdesignerarch.JPG "WorkflowDesignerArch")  
  
 A <xref:System.Activities.Presentation.Model.ModelItem> składa się z wskaźnik do wartości podstawowej, a także kolekcję <xref:System.Activities.Presentation.Model.ModelProperty> obiektów. A <xref:System.Activities.Presentation.Model.ModelProperty> obiekt z kolei składa się z danych, takie jak nazwa i właściwości, a następnie wskaźnik do wartości, która z kolei jest innego typu <xref:System.Activities.Presentation.Model.ModelItem>. Konwerter wartości służy do modyfikowania niektórych <xref:System.Activities.Presentation.Model.ModelItem>s zwrócony z <xref:System.Activities.Presentation.Model.ModelProperty> aby były wyświetlane prawidłowo w widoku drzewa. Próbka następnie pokazano, jak program imperatively przed <xref:System.Activities.Presentation.Model.ModelItem> drzewa przy użyciu składni konieczne, jak pokazano w poniższym przykładzie.  
  
```csharp  
ModelItem mi = wd.Context.Services.GetService<ModelService>().Root;  
ModelProperty mp = mi.Properties["Activities"];  
mp.Collection.Add(new Persist());  
ModelItem justAdded = mp.Collection.Last();  
justAdded.Properties["DisplayName"].SetValue("new name");  
```  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Otwórz rozwiązanie ProgrammingModelItemTree.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Skompiluj rozwiązanie, wybierając **Kompiluj rozwiązanie** z **kompilacji** menu.  
  
3.  Naciśnij klawisz F5, aby uruchomić aplikację. [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] Następnie zostanie wyświetlony formularz.  
  
4.  Kliknij przycisk **załadować WF** przycisk, aby załadować <xref:System.Activities.Presentation.Model.ModelItem> i powiązać ją z widoku drzewa.  
  
5.  Kliknięcie przycisku **zmiany modelu elementu drzewa** przycisk wykonuje poprzedni kod, aby dodać element do drzewa i ustaw właściwość.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ProgrammingModelItemTree`  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Data.IValueConverter>
