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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 83e804a3ede525510b5c46b494882656c74591b8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="programming-model-item-tree"></a><span data-ttu-id="f83f9-102">Drzewo elementów modelu programowania</span><span class="sxs-lookup"><span data-stu-id="f83f9-102">Programming Model Item Tree</span></span>
<span data-ttu-id="f83f9-103">W tym przykładzie pokazano, jak przechodzić <xref:System.Activities.Presentation.Model.ModelItem> drzewa używanie powiązania danych deklaratywne z [!INCLUDE[avalon1](../../../../includes/avalon1-md.md)] widok drzewa.</span><span class="sxs-lookup"><span data-stu-id="f83f9-103">This sample demonstrates how to navigate the <xref:System.Activities.Presentation.Model.ModelItem> tree using declarative data binding from the [!INCLUDE[avalon1](../../../../includes/avalon1-md.md)] Tree View.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="f83f9-104">Szczegóły próbki</span><span class="sxs-lookup"><span data-stu-id="f83f9-104">Sample Details</span></span>  
 <span data-ttu-id="f83f9-105"><xref:System.Activities.Presentation.Model.ModelItem> Drzewo jest abstrakcji, która jest używana przez [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] infrastruktury do udostępnienia danych dotyczących podstawowej wystąpienie edytowany.</span><span class="sxs-lookup"><span data-stu-id="f83f9-105">The <xref:System.Activities.Presentation.Model.ModelItem> tree is the abstraction that is used by the [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] infrastructure to expose the data about the underlying instance being edited.</span></span> <span data-ttu-id="f83f9-106">Na rysunku poniżej przedstawiono sceny infrastruktury w różnych warstwach [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f83f9-106">The following illustration is a depiction of the various layers of infrastructure within the [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].</span></span>  
  
 <span data-ttu-id="f83f9-107">![Architektura projektanta przepływów pracy](../../../../docs/framework/windows-workflow-foundation/samples/media/workflowdesignerarch.JPG "WorkflowDesignerArch")</span><span class="sxs-lookup"><span data-stu-id="f83f9-107">![Workflow Designer Architecture](../../../../docs/framework/windows-workflow-foundation/samples/media/workflowdesignerarch.JPG "WorkflowDesignerArch")</span></span>  
  
 <span data-ttu-id="f83f9-108">A <xref:System.Activities.Presentation.Model.ModelItem> składa się z wskaźnik do wartości podstawowej, a także kolekcję <xref:System.Activities.Presentation.Model.ModelProperty> obiektów.</span><span class="sxs-lookup"><span data-stu-id="f83f9-108">A <xref:System.Activities.Presentation.Model.ModelItem> consists of a pointer to the underlying value, as well as a collection of <xref:System.Activities.Presentation.Model.ModelProperty> objects.</span></span> <span data-ttu-id="f83f9-109">A <xref:System.Activities.Presentation.Model.ModelProperty> obiekt z kolei składa się z danych, takie jak nazwa i właściwości, a następnie wskaźnik do wartości, która z kolei jest innego typu <xref:System.Activities.Presentation.Model.ModelItem>.</span><span class="sxs-lookup"><span data-stu-id="f83f9-109">A <xref:System.Activities.Presentation.Model.ModelProperty> object in turn, consists of data such as the name and type of the property and then a pointer to the value, which in turn, is another <xref:System.Activities.Presentation.Model.ModelItem>.</span></span> <span data-ttu-id="f83f9-110">Konwerter wartości służy do modyfikowania niektórych <xref:System.Activities.Presentation.Model.ModelItem>s zwrócony z <xref:System.Activities.Presentation.Model.ModelProperty> aby były wyświetlane prawidłowo w widoku drzewa.</span><span class="sxs-lookup"><span data-stu-id="f83f9-110">A value converter is used to manipulate some of the <xref:System.Activities.Presentation.Model.ModelItem>s returned from a <xref:System.Activities.Presentation.Model.ModelProperty> to make them appear correctly in the tree view.</span></span> <span data-ttu-id="f83f9-111">Próbka następnie pokazano, jak program imperatively przed <xref:System.Activities.Presentation.Model.ModelItem> drzewa przy użyciu składni konieczne, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f83f9-111">The sample then demonstrates how to imperatively program against the <xref:System.Activities.Presentation.Model.ModelItem> tree using the imperative syntax, as seen in the following example.</span></span>  
  
```csharp  
ModelItem mi = wd.Context.Services.GetService<ModelService>().Root;  
ModelProperty mp = mi.Properties["Activities"];  
mp.Collection.Add(new Persist());  
ModelItem justAdded = mp.Collection.Last();  
justAdded.Properties["DisplayName"].SetValue("new name");  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="f83f9-112">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="f83f9-112">To use this sample</span></span>  
  
1.  <span data-ttu-id="f83f9-113">Otwórz rozwiązanie ProgrammingModelItemTree.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f83f9-113">Open the ProgrammingModelItemTree.sln solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="f83f9-114">Skompiluj rozwiązanie, wybierając **Kompiluj rozwiązanie** z **kompilacji** menu.</span><span class="sxs-lookup"><span data-stu-id="f83f9-114">Build the solution by selecting **Build Solution** from the **Build** menu.</span></span>  
  
3.  <span data-ttu-id="f83f9-115">Naciśnij klawisz F5, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="f83f9-115">Press F5 to run the application.</span></span> <span data-ttu-id="f83f9-116">[!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] Następnie zostanie wyświetlony formularz.</span><span class="sxs-lookup"><span data-stu-id="f83f9-116">The [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] form is then displayed.</span></span>  
  
4.  <span data-ttu-id="f83f9-117">Kliknij przycisk **załadować WF** przycisk, aby załadować <xref:System.Activities.Presentation.Model.ModelItem> i powiązać ją z widoku drzewa.</span><span class="sxs-lookup"><span data-stu-id="f83f9-117">Click the **Load WF** button to load the <xref:System.Activities.Presentation.Model.ModelItem> and bind it to the tree view.</span></span>  
  
5.  <span data-ttu-id="f83f9-118">Kliknięcie przycisku **zmiany modelu elementu drzewa** przycisk wykonuje poprzedni kod, aby dodać element do drzewa i ustaw właściwość.</span><span class="sxs-lookup"><span data-stu-id="f83f9-118">Clicking the **Change Model Item Tree** button executes the preceding code to add an item into the tree and set a property.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f83f9-119">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="f83f9-119">The samples may already be installed on your computer.</span></span> <span data-ttu-id="f83f9-120">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="f83f9-120">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f83f9-121">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="f83f9-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f83f9-122">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="f83f9-122">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ProgrammingModelItemTree`  
  
## <a name="see-also"></a><span data-ttu-id="f83f9-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f83f9-123">See Also</span></span>  
 <xref:System.Windows.Data.IValueConverter>
