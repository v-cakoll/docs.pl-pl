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
# <a name="programming-model-item-tree"></a><span data-ttu-id="dbec9-102">Drzewo elementów modelu programowania</span><span class="sxs-lookup"><span data-stu-id="dbec9-102">Programming Model Item Tree</span></span>
<span data-ttu-id="dbec9-103">Ten przykład pokazuje, jak nawigować po <xref:System.Activities.Presentation.Model.ModelItem> drzewie przy użyciu deklaratywnego powiązania danych z widoku drzewa Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="dbec9-103">This sample demonstrates how to navigate the <xref:System.Activities.Presentation.Model.ModelItem> tree using declarative data binding from the Windows Presentation Foundation (WPF) Tree View.</span></span>

## <a name="sample-details"></a><span data-ttu-id="dbec9-104">Przykładowe szczegóły</span><span class="sxs-lookup"><span data-stu-id="dbec9-104">Sample Details</span></span>
 <span data-ttu-id="dbec9-105">Drzewo jest abstrakcją używaną [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] przez infrastrukturę do ujawnienia danych o edytowanym wystąpieniu. <xref:System.Activities.Presentation.Model.ModelItem></span><span class="sxs-lookup"><span data-stu-id="dbec9-105">The <xref:System.Activities.Presentation.Model.ModelItem> tree is the abstraction that is used by the [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] infrastructure to expose the data about the underlying instance being edited.</span></span> <span data-ttu-id="dbec9-106">Poniższa ilustracja przedstawia różne warstwy infrastruktury w ramach programu [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dbec9-106">The following illustration is a depiction of the various layers of infrastructure within the [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].</span></span>

 ![Diagram przedstawiający architekturę Projektant przepływu pracy.](./media/programming-model-item-tree/workflow-designer-architecture.jpg)

 <span data-ttu-id="dbec9-108">A <xref:System.Activities.Presentation.Model.ModelItem> składa się ze wskaźnika do podstawowej wartości, a także do <xref:System.Activities.Presentation.Model.ModelProperty> kolekcji obiektów.</span><span class="sxs-lookup"><span data-stu-id="dbec9-108">A <xref:System.Activities.Presentation.Model.ModelItem> consists of a pointer to the underlying value, as well as a collection of <xref:System.Activities.Presentation.Model.ModelProperty> objects.</span></span> <span data-ttu-id="dbec9-109">Obiekt z kolei składa się z danych, takich jak nazwa i typ właściwości, a następnie wskaźnik do wartości, która z kolei jest inna <xref:System.Activities.Presentation.Model.ModelItem>. <xref:System.Activities.Presentation.Model.ModelProperty></span><span class="sxs-lookup"><span data-stu-id="dbec9-109">A <xref:System.Activities.Presentation.Model.ModelProperty> object in turn, consists of data such as the name and type of the property and then a pointer to the value, which in turn, is another <xref:System.Activities.Presentation.Model.ModelItem>.</span></span> <span data-ttu-id="dbec9-110">Konwerter wartości służy do manipulowania niektórymi z <xref:System.Activities.Presentation.Model.ModelItem>elementów s zwróconych <xref:System.Activities.Presentation.Model.ModelProperty> z elementu, aby były prawidłowo wyświetlane w widoku drzewa.</span><span class="sxs-lookup"><span data-stu-id="dbec9-110">A value converter is used to manipulate some of the <xref:System.Activities.Presentation.Model.ModelItem>s returned from a <xref:System.Activities.Presentation.Model.ModelProperty> to make them appear correctly in the tree view.</span></span> <span data-ttu-id="dbec9-111">W przykładzie pokazano, jak bezwzględnie programowo korzystać <xref:System.Activities.Presentation.Model.ModelItem> z drzewa przy użyciu bezwzględnej składni, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="dbec9-111">The sample then demonstrates how to imperatively program against the <xref:System.Activities.Presentation.Model.ModelItem> tree using the imperative syntax, as seen in the following example.</span></span>

```csharp
ModelItem mi = wd.Context.Services.GetService<ModelService>().Root;
ModelProperty mp = mi.Properties["Activities"];
mp.Collection.Add(new Persist());
ModelItem justAdded = mp.Collection.Last();
justAdded.Properties["DisplayName"].SetValue("new name");
```

#### <a name="to-use-this-sample"></a><span data-ttu-id="dbec9-112">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="dbec9-112">To use this sample</span></span>

1. <span data-ttu-id="dbec9-113">Otwórz rozwiązanie ProgrammingModelItemTree. sln w programie Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="dbec9-113">Open the ProgrammingModelItemTree.sln solution in Visual Studio 2010.</span></span>

2. <span data-ttu-id="dbec9-114">Skompiluj rozwiązanie, wybierając opcję **Kompiluj rozwiązanie** w menu **kompilacja** .</span><span class="sxs-lookup"><span data-stu-id="dbec9-114">Build the solution by selecting **Build Solution** from the **Build** menu.</span></span>

3. <span data-ttu-id="dbec9-115">Naciśnij klawisz F5, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="dbec9-115">Press F5 to run the application.</span></span> <span data-ttu-id="dbec9-116">Zostanie wyświetlony formularz WPF.</span><span class="sxs-lookup"><span data-stu-id="dbec9-116">The WPF form is then displayed.</span></span>

4. <span data-ttu-id="dbec9-117">Kliknij przycisk **Załaduj WF** , aby załadować <xref:System.Activities.Presentation.Model.ModelItem> i powiązać go z widokiem drzewa.</span><span class="sxs-lookup"><span data-stu-id="dbec9-117">Click the **Load WF** button to load the <xref:System.Activities.Presentation.Model.ModelItem> and bind it to the tree view.</span></span>

5. <span data-ttu-id="dbec9-118">Kliknięcie przycisku **Zmień model elementu modelu** wykonuje poprzedni kod, aby dodać element do drzewa i ustawić właściwość.</span><span class="sxs-lookup"><span data-stu-id="dbec9-118">Clicking the **Change Model Item Tree** button executes the preceding code to add an item into the tree and set a property.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="dbec9-119">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="dbec9-119">The samples may already be installed on your computer.</span></span> <span data-ttu-id="dbec9-120">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="dbec9-120">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="dbec9-121">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="dbec9-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="dbec9-122">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="dbec9-122">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ProgrammingModelItemTree`  
  
## <a name="see-also"></a><span data-ttu-id="dbec9-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dbec9-123">See also</span></span>

- <xref:System.Windows.Data.IValueConverter>
