---
title: Drzewo elementów modelu programowania
ms.date: 03/30/2017
ms.assetid: 0229efde-19ac-4bdc-a187-c6227a7bd1a5
ms.openlocfilehash: 1aaa1aa9922a7f57138782effe9492ec84198c8a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62004977"
---
# <a name="programming-model-item-tree"></a><span data-ttu-id="368e5-102">Drzewo elementów modelu programowania</span><span class="sxs-lookup"><span data-stu-id="368e5-102">Programming Model Item Tree</span></span>
<span data-ttu-id="368e5-103">W tym przykładzie pokazano, jak nawigować po <xref:System.Activities.Presentation.Model.ModelItem> drzewa za pomocą powiązania dane deklaratywne w widoku drzewa Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="368e5-103">This sample demonstrates how to navigate the <xref:System.Activities.Presentation.Model.ModelItem> tree using declarative data binding from the Windows Presentation Foundation (WPF) Tree View.</span></span>

## <a name="sample-details"></a><span data-ttu-id="368e5-104">Przykład szczegółów</span><span class="sxs-lookup"><span data-stu-id="368e5-104">Sample Details</span></span>
 <span data-ttu-id="368e5-105"><xref:System.Activities.Presentation.Model.ModelItem> Drzewo jest abstrakcji, która jest używana przez [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] infrastruktury w celu ujawnienia danych o wystąpieniu bazowego, edytowany.</span><span class="sxs-lookup"><span data-stu-id="368e5-105">The <xref:System.Activities.Presentation.Model.ModelItem> tree is the abstraction that is used by the [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] infrastructure to expose the data about the underlying instance being edited.</span></span> <span data-ttu-id="368e5-106">Na poniższej ilustracji jest sceny z różnych warstw infrastruktury w [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="368e5-106">The following illustration is a depiction of the various layers of infrastructure within the [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].</span></span>

 ![Diagram przedstawiający architekturę projektanta przepływów pracy.](./media/programming-model-item-tree/workflow-designer-architecture.jpg)

 <span data-ttu-id="368e5-108">A <xref:System.Activities.Presentation.Model.ModelItem> składa się z wskaźnik do podstawowej wartości, a także kolekcję <xref:System.Activities.Presentation.Model.ModelProperty> obiektów.</span><span class="sxs-lookup"><span data-stu-id="368e5-108">A <xref:System.Activities.Presentation.Model.ModelItem> consists of a pointer to the underlying value, as well as a collection of <xref:System.Activities.Presentation.Model.ModelProperty> objects.</span></span> <span data-ttu-id="368e5-109">A <xref:System.Activities.Presentation.Model.ModelProperty> obiekt z kolei składa się z danych, takie jak nazwa i typ właściwości, a następnie wskaźnik do wartości, która z kolei jest kolejnym <xref:System.Activities.Presentation.Model.ModelItem>.</span><span class="sxs-lookup"><span data-stu-id="368e5-109">A <xref:System.Activities.Presentation.Model.ModelProperty> object in turn, consists of data such as the name and type of the property and then a pointer to the value, which in turn, is another <xref:System.Activities.Presentation.Model.ModelItem>.</span></span> <span data-ttu-id="368e5-110">Konwerter wartości służy do modyfikowania niektórych <xref:System.Activities.Presentation.Model.ModelItem>s zwróciło <xref:System.Activities.Presentation.Model.ModelProperty> aby były one są prawidłowo wyświetlane w widoku drzewa.</span><span class="sxs-lookup"><span data-stu-id="368e5-110">A value converter is used to manipulate some of the <xref:System.Activities.Presentation.Model.ModelItem>s returned from a <xref:System.Activities.Presentation.Model.ModelProperty> to make them appear correctly in the tree view.</span></span> <span data-ttu-id="368e5-111">Przykład następnie pokazano, jak programować obowiązkowo przy użyciu <xref:System.Activities.Presentation.Model.ModelItem> drzewa za pomocą składnia imperatywna, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="368e5-111">The sample then demonstrates how to imperatively program against the <xref:System.Activities.Presentation.Model.ModelItem> tree using the imperative syntax, as seen in the following example.</span></span>

```csharp
ModelItem mi = wd.Context.Services.GetService<ModelService>().Root;
ModelProperty mp = mi.Properties["Activities"];
mp.Collection.Add(new Persist());
ModelItem justAdded = mp.Collection.Last();
justAdded.Properties["DisplayName"].SetValue("new name");
```

#### <a name="to-use-this-sample"></a><span data-ttu-id="368e5-112">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="368e5-112">To use this sample</span></span>

1. <span data-ttu-id="368e5-113">Otwórz rozwiązanie ProgrammingModelItemTree.sln w programie Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="368e5-113">Open the ProgrammingModelItemTree.sln solution in Visual Studio 2010.</span></span>

2. <span data-ttu-id="368e5-114">Skompiluj rozwiązanie, wybierając **Kompiluj rozwiązanie** z **kompilacji** menu.</span><span class="sxs-lookup"><span data-stu-id="368e5-114">Build the solution by selecting **Build Solution** from the **Build** menu.</span></span>

3. <span data-ttu-id="368e5-115">Naciśnij klawisz F5, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="368e5-115">Press F5 to run the application.</span></span> <span data-ttu-id="368e5-116">[!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] Następnie zostanie wyświetlony formularz.</span><span class="sxs-lookup"><span data-stu-id="368e5-116">The [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] form is then displayed.</span></span>

4. <span data-ttu-id="368e5-117">Kliknij przycisk **obciążenia WF** przycisk, aby załadować <xref:System.Activities.Presentation.Model.ModelItem> i powiąż go w widoku drzewa.</span><span class="sxs-lookup"><span data-stu-id="368e5-117">Click the **Load WF** button to load the <xref:System.Activities.Presentation.Model.ModelItem> and bind it to the tree view.</span></span>

5. <span data-ttu-id="368e5-118">Klikając **drzewo elementów modelu zmiany** przycisk wykonuje poprzedni kod, aby dodać element do drzewa i ustawić właściwość.</span><span class="sxs-lookup"><span data-stu-id="368e5-118">Clicking the **Change Model Item Tree** button executes the preceding code to add an item into the tree and set a property.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="368e5-119">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="368e5-119">The samples may already be installed on your computer.</span></span> <span data-ttu-id="368e5-120">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="368e5-120">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="368e5-121">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="368e5-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="368e5-122">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="368e5-122">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ProgrammingModelItemTree`  
  
## <a name="see-also"></a><span data-ttu-id="368e5-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="368e5-123">See also</span></span>

- <xref:System.Windows.Data.IValueConverter>
