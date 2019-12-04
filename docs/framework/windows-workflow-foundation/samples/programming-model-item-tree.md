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
# <a name="programming-model-item-tree"></a><span data-ttu-id="34750-102">Drzewo elementów modelu programowania</span><span class="sxs-lookup"><span data-stu-id="34750-102">Programming Model Item Tree</span></span>
<span data-ttu-id="34750-103">Ten przykład pokazuje, jak nawigować po drzewie <xref:System.Activities.Presentation.Model.ModelItem> przy użyciu deklaratywnego powiązania danych z widoku drzewa Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="34750-103">This sample demonstrates how to navigate the <xref:System.Activities.Presentation.Model.ModelItem> tree using declarative data binding from the Windows Presentation Foundation (WPF) Tree View.</span></span>

## <a name="sample-details"></a><span data-ttu-id="34750-104">Przykładowe szczegóły</span><span class="sxs-lookup"><span data-stu-id="34750-104">Sample Details</span></span>
 <span data-ttu-id="34750-105">Drzewo <xref:System.Activities.Presentation.Model.ModelItem> jest abstrakcją używaną przez infrastrukturę Projektant przepływu pracy systemu Windows, aby uwidocznić dane dotyczące edytowanego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="34750-105">The <xref:System.Activities.Presentation.Model.ModelItem> tree is the abstraction that is used by the Windows Workflow Designer infrastructure to expose the data about the underlying instance being edited.</span></span> <span data-ttu-id="34750-106">Poniższa ilustracja przedstawia różne warstwy infrastruktury w ramach Projektant przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="34750-106">The following illustration is a depiction of the various layers of infrastructure within the Workflow Designer.</span></span>

 ![Diagram przedstawiający architekturę Projektant przepływu pracy.](./media/programming-model-item-tree/workflow-designer-architecture.jpg)

 <span data-ttu-id="34750-108"><xref:System.Activities.Presentation.Model.ModelItem> składa się ze wskaźnika do podstawowej wartości, a także do kolekcji obiektów <xref:System.Activities.Presentation.Model.ModelProperty>.</span><span class="sxs-lookup"><span data-stu-id="34750-108">A <xref:System.Activities.Presentation.Model.ModelItem> consists of a pointer to the underlying value, as well as a collection of <xref:System.Activities.Presentation.Model.ModelProperty> objects.</span></span> <span data-ttu-id="34750-109">Obiekt <xref:System.Activities.Presentation.Model.ModelProperty> z kolei składa się z danych, takich jak nazwa i typ właściwości, a następnie wskaźnik do wartości, która z kolei jest kolejną <xref:System.Activities.Presentation.Model.ModelItem>.</span><span class="sxs-lookup"><span data-stu-id="34750-109">A <xref:System.Activities.Presentation.Model.ModelProperty> object in turn, consists of data such as the name and type of the property and then a pointer to the value, which in turn, is another <xref:System.Activities.Presentation.Model.ModelItem>.</span></span> <span data-ttu-id="34750-110">Konwerter wartości służy do manipulowania niektórymi <xref:System.Activities.Presentation.Model.ModelItem>s zwróconymi z <xref:System.Activities.Presentation.Model.ModelProperty>, aby były prawidłowo wyświetlane w widoku drzewa.</span><span class="sxs-lookup"><span data-stu-id="34750-110">A value converter is used to manipulate some of the <xref:System.Activities.Presentation.Model.ModelItem>s returned from a <xref:System.Activities.Presentation.Model.ModelProperty> to make them appear correctly in the tree view.</span></span> <span data-ttu-id="34750-111">W przykładzie pokazano, jak bezwzględnie programowo korzystać z drzewa <xref:System.Activities.Presentation.Model.ModelItem> przy użyciu bezwzględnej składni, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="34750-111">The sample then demonstrates how to imperatively program against the <xref:System.Activities.Presentation.Model.ModelItem> tree using the imperative syntax, as seen in the following example.</span></span>

```csharp
ModelItem mi = wd.Context.Services.GetService<ModelService>().Root;
ModelProperty mp = mi.Properties["Activities"];
mp.Collection.Add(new Persist());
ModelItem justAdded = mp.Collection.Last();
justAdded.Properties["DisplayName"].SetValue("new name");
```

#### <a name="to-use-this-sample"></a><span data-ttu-id="34750-112">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="34750-112">To use this sample</span></span>

1. <span data-ttu-id="34750-113">Otwórz rozwiązanie ProgrammingModelItemTree. sln w programie Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="34750-113">Open the ProgrammingModelItemTree.sln solution in Visual Studio 2010.</span></span>

2. <span data-ttu-id="34750-114">Skompiluj rozwiązanie, wybierając opcję **Kompiluj rozwiązanie** w menu **kompilacja** .</span><span class="sxs-lookup"><span data-stu-id="34750-114">Build the solution by selecting **Build Solution** from the **Build** menu.</span></span>

3. <span data-ttu-id="34750-115">Naciśnij klawisz F5, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="34750-115">Press F5 to run the application.</span></span> <span data-ttu-id="34750-116">Zostanie wyświetlony formularz WPF.</span><span class="sxs-lookup"><span data-stu-id="34750-116">The WPF form is then displayed.</span></span>

4. <span data-ttu-id="34750-117">Kliknij przycisk **Załaduj WF** , aby załadować <xref:System.Activities.Presentation.Model.ModelItem> i powiązać je z widokiem drzewa.</span><span class="sxs-lookup"><span data-stu-id="34750-117">Click the **Load WF** button to load the <xref:System.Activities.Presentation.Model.ModelItem> and bind it to the tree view.</span></span>

5. <span data-ttu-id="34750-118">Kliknięcie przycisku **Zmień model elementu modelu** wykonuje poprzedni kod, aby dodać element do drzewa i ustawić właściwość.</span><span class="sxs-lookup"><span data-stu-id="34750-118">Clicking the **Change Model Item Tree** button executes the preceding code to add an item into the tree and set a property.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="34750-119">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="34750-119">The samples may already be installed on your computer.</span></span> <span data-ttu-id="34750-120">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="34750-120">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="34750-121">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="34750-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="34750-122">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="34750-122">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ProgrammingModelItemTree`  
  
## <a name="see-also"></a><span data-ttu-id="34750-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="34750-123">See also</span></span>

- <xref:System.Windows.Data.IValueConverter>
