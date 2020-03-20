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
# <a name="programming-model-item-tree"></a><span data-ttu-id="799fb-102">Drzewo elementów modelu programowania</span><span class="sxs-lookup"><span data-stu-id="799fb-102">Programming Model Item Tree</span></span>
<span data-ttu-id="799fb-103">W tym przykładzie pokazano, jak poruszać się po <xref:System.Activities.Presentation.Model.ModelItem> drzewie przy użyciu deklaratywnego powiązania danych z widoku drzewa programu Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="799fb-103">This sample demonstrates how to navigate the <xref:System.Activities.Presentation.Model.ModelItem> tree using declarative data binding from the Windows Presentation Foundation (WPF) Tree View.</span></span>

## <a name="sample-details"></a><span data-ttu-id="799fb-104">Przykładowe szczegóły</span><span class="sxs-lookup"><span data-stu-id="799fb-104">Sample Details</span></span>
 <span data-ttu-id="799fb-105">Drzewo <xref:System.Activities.Presentation.Model.ModelItem> jest abstrakcja, który jest używany przez infrastrukturę Projektanta przepływu pracy systemu Windows, aby udostępnić dane dotyczące wystąpienia źródłowego są edytowane.</span><span class="sxs-lookup"><span data-stu-id="799fb-105">The <xref:System.Activities.Presentation.Model.ModelItem> tree is the abstraction that is used by the Windows Workflow Designer infrastructure to expose the data about the underlying instance being edited.</span></span> <span data-ttu-id="799fb-106">Poniższa ilustracja przedstawia różne warstwy infrastruktury w projektancie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="799fb-106">The following illustration is a depiction of the various layers of infrastructure within the Workflow Designer.</span></span>

 ![Diagram przedstawiający architekturę projektanta przepływu pracy.](./media/programming-model-item-tree/workflow-designer-architecture.jpg)

 <span data-ttu-id="799fb-108">A <xref:System.Activities.Presentation.Model.ModelItem> składa się ze wskaźnika do wartości podstawowej, a także kolekcji <xref:System.Activities.Presentation.Model.ModelProperty> obiektów.</span><span class="sxs-lookup"><span data-stu-id="799fb-108">A <xref:System.Activities.Presentation.Model.ModelItem> consists of a pointer to the underlying value, as well as a collection of <xref:System.Activities.Presentation.Model.ModelProperty> objects.</span></span> <span data-ttu-id="799fb-109">Obiekt <xref:System.Activities.Presentation.Model.ModelProperty> z kolei składa się z danych, takich jak nazwa i typ właściwości, a następnie <xref:System.Activities.Presentation.Model.ModelItem>wskaźnik do wartości, która z kolei jest inny .</span><span class="sxs-lookup"><span data-stu-id="799fb-109">A <xref:System.Activities.Presentation.Model.ModelProperty> object in turn, consists of data such as the name and type of the property and then a pointer to the value, which in turn, is another <xref:System.Activities.Presentation.Model.ModelItem>.</span></span> <span data-ttu-id="799fb-110">Konwerter wartości służy do <xref:System.Activities.Presentation.Model.ModelItem>manipulowania niektórymi <xref:System.Activities.Presentation.Model.ModelProperty> s zwróconych z a, aby były wyświetlane poprawnie w widoku drzewa.</span><span class="sxs-lookup"><span data-stu-id="799fb-110">A value converter is used to manipulate some of the <xref:System.Activities.Presentation.Model.ModelItem>s returned from a <xref:System.Activities.Presentation.Model.ModelProperty> to make them appear correctly in the tree view.</span></span> <span data-ttu-id="799fb-111">Następnie w przykładzie pokazano, jak <xref:System.Activities.Presentation.Model.ModelItem> należy bezwzględnie zaprogramować względem drzewa przy użyciu składni imperatywnej, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="799fb-111">The sample then demonstrates how to imperatively program against the <xref:System.Activities.Presentation.Model.ModelItem> tree using the imperative syntax, as seen in the following example.</span></span>

```csharp
ModelItem mi = wd.Context.Services.GetService<ModelService>().Root;
ModelProperty mp = mi.Properties["Activities"];
mp.Collection.Add(new Persist());
ModelItem justAdded = mp.Collection.Last();
justAdded.Properties["DisplayName"].SetValue("new name");
```

#### <a name="to-use-this-sample"></a><span data-ttu-id="799fb-112">Aby użyć tej próbki</span><span class="sxs-lookup"><span data-stu-id="799fb-112">To use this sample</span></span>

1. <span data-ttu-id="799fb-113">Otwórz rozwiązanie ProgrammingModelItemTree.sln w programie Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="799fb-113">Open the ProgrammingModelItemTree.sln solution in Visual Studio 2010.</span></span>

2. <span data-ttu-id="799fb-114">Skompiluj rozwiązanie, wybierając **rozwiązanie kompilacji** z menu **Kompilacja.**</span><span class="sxs-lookup"><span data-stu-id="799fb-114">Build the solution by selecting **Build Solution** from the **Build** menu.</span></span>

3. <span data-ttu-id="799fb-115">Naciśnij klawisz F5, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="799fb-115">Press F5 to run the application.</span></span> <span data-ttu-id="799fb-116">Następnie wyświetlany jest formularz WPF.</span><span class="sxs-lookup"><span data-stu-id="799fb-116">The WPF form is then displayed.</span></span>

4. <span data-ttu-id="799fb-117">Kliknij przycisk **Załaduj WF,** aby załadować <xref:System.Activities.Presentation.Model.ModelItem> i powiązać go z widokiem drzewa.</span><span class="sxs-lookup"><span data-stu-id="799fb-117">Click the **Load WF** button to load the <xref:System.Activities.Presentation.Model.ModelItem> and bind it to the tree view.</span></span>

5. <span data-ttu-id="799fb-118">Kliknięcie przycisku **Zmień drzewo elementów modelu** wykonuje poprzedni kod, aby dodać element do drzewa i ustawić właściwość.</span><span class="sxs-lookup"><span data-stu-id="799fb-118">Clicking the **Change Model Item Tree** button executes the preceding code to add an item into the tree and set a property.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="799fb-119">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="799fb-119">The samples may already be installed on your computer.</span></span> <span data-ttu-id="799fb-120">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="799fb-120">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="799fb-121">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="799fb-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="799fb-122">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="799fb-122">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ProgrammingModelItemTree`  
  
## <a name="see-also"></a><span data-ttu-id="799fb-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="799fb-123">See also</span></span>

- <xref:System.Windows.Data.IValueConverter>
