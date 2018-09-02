---
title: Usługa przybornika
ms.date: 03/30/2017
ms.assetid: 742212d0-445e-41ed-9739-9ee848ce7f1b
ms.openlocfilehash: 0b21f10c763f3f82591f947eb4cc48cf90f4ac79
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43406465"
---
# <a name="toolbox-service"></a><span data-ttu-id="c9bcd-102">Usługa przybornika</span><span class="sxs-lookup"><span data-stu-id="c9bcd-102">Toolbox Service</span></span>
<span data-ttu-id="c9bcd-103">W tym przykładzie pokazano, jak zaktualizować [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] przybornika działań na podstawie kontekstu przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="c9bcd-103">This sample demonstrates how to update the [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] Toolbox activities based on the context of the workflow.</span></span> <span data-ttu-id="c9bcd-104">Przykładowy zawiera przepływ pracy, który zmiany zawartości przybornika oparte na tego, czy wybrano działań niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="c9bcd-104">The sample contains a workflow that changes the toolbox contents based on whether a custom activity is selected.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="c9bcd-105">Dyskusja</span><span class="sxs-lookup"><span data-stu-id="c9bcd-105">Discussion</span></span>  
 <span data-ttu-id="c9bcd-106">Podczas tworzenia przepływu pracy, klienci mają zazwyczaj ich przybornika, aby być kontekstowa.</span><span class="sxs-lookup"><span data-stu-id="c9bcd-106">During workflow authoring, customers generally want their Toolbox to be context sensitive.</span></span> <span data-ttu-id="c9bcd-107">Na przykład użytkownik może chcieć upewnij się, że przybornika określonego działania jest dodawany do przepływu pracy, zawiera kilka dodatkowych działań.</span><span class="sxs-lookup"><span data-stu-id="c9bcd-107">For example, the user may want to ensure that the Toolbox shows a few additional activities when a specific activity is added to the workflow.</span></span> <span data-ttu-id="c9bcd-108">Jeśli działania są usuwane z przepływu pracy, przyborniku powinien reagować odpowiednio w zależności od wymagań domeny.</span><span class="sxs-lookup"><span data-stu-id="c9bcd-108">If the activities are removed from the workflow, the toolbox should react appropriately based on the domain requirements.</span></span>  
  
 <span data-ttu-id="c9bcd-109">W Projektancie ponownie hostowanej przepływu pracy możesz kontrolować kontrolki przybornika i upewnij się, że na podstawie zmian modelu w przepływie pracy, host wyzwala odpowiednie zmiany w kontrolki przybornika.</span><span class="sxs-lookup"><span data-stu-id="c9bcd-109">In a re-hosted workflow designer, you control the Toolbox control and can ensure that based on the Model changes in the workflow, the host triggers appropriate changes in the Toolbox control.</span></span> <span data-ttu-id="c9bcd-110">Jednak w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], przybornik nie są kontrolowane przez użytkownika i w związku z tym interfejsem jest wymagany do modyfikowania jego zawartości.</span><span class="sxs-lookup"><span data-stu-id="c9bcd-110">However, in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], the toolbox is not controlled by the user and thus an interface is required to modify its contents.</span></span> <span data-ttu-id="c9bcd-111">`IActivityToolboxService` jest ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="c9bcd-111">`IActivityToolboxService` is that interface.</span></span>  
  
 <span data-ttu-id="c9bcd-112">Interfejs API udostępnia następujące cztery metody.</span><span class="sxs-lookup"><span data-stu-id="c9bcd-112">The API provides the following four methods.</span></span>  
  
```  
public interface IActivityToolboxService   
{   
        void AddCategory(string categoryName);   
        void RemoveCategory(string categoryName);   
        void AddItem(string qualifiedTypeName, string categoryName);   
        void RemoveItem(string qualifiedTypeName, string categoryName);   
        IList<string> EnumCategories();   
        IList<string> EnumItems(string categoryName);   
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c9bcd-113">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="c9bcd-113">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="c9bcd-114">Za pomocą [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania WorkflowSimulator.sln.</span><span class="sxs-lookup"><span data-stu-id="c9bcd-114">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the WorkflowSimulator.sln solution file.</span></span>  
  
2.  <span data-ttu-id="c9bcd-115">Skompiluj rozwiązanie, naciskając klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="c9bcd-115">Build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="c9bcd-116">Otwórz plik Workflow.xaml.</span><span class="sxs-lookup"><span data-stu-id="c9bcd-116">Open the Workflow.xaml file.</span></span>  
  
4.  <span data-ttu-id="c9bcd-117">Dodaj **CustomActivity** , przeciągając i upuszczając go z przybornika.</span><span class="sxs-lookup"><span data-stu-id="c9bcd-117">Add a **CustomActivity** by dragging and dropping it from the toolbox.</span></span> <span data-ttu-id="c9bcd-118">Należy zauważyć, że wywoływana dodatkowych kategorii przybornika: **nową kategorię WF** z działaniem dodatkowe **przypisać**.</span><span class="sxs-lookup"><span data-stu-id="c9bcd-118">Notice that an additional Toolbox category called: **New WF Category** with an additional activity **Assign**.</span></span>  
  
5.  <span data-ttu-id="c9bcd-119">Teraz, usuń zaznaczenie **CustomActivity** , przeciągając innego działania do niego.</span><span class="sxs-lookup"><span data-stu-id="c9bcd-119">Now unselect the **CustomActivity** by dragging another activity into it.</span></span>  
  
6.  <span data-ttu-id="c9bcd-120">Element **przypisać** w kategorii **nową kategorię WF** w przyborniku zostało usunięte.</span><span class="sxs-lookup"><span data-stu-id="c9bcd-120">The item **Assign** in the category **New WF Category** under Toolbox is now removed.</span></span> <span data-ttu-id="c9bcd-121">Ponadto ponieważ istnieje więcej elementów w kategorii, kategorii spowoduje usunięcie również.</span><span class="sxs-lookup"><span data-stu-id="c9bcd-121">Also, because there are no more items left in the category, the category is removed as well.</span></span>  
  
7.  <span data-ttu-id="c9bcd-122">Wybierz **CustomActivity** ponownie i kategorii i **przypisać** działanie zostanie ponownie dodany.</span><span class="sxs-lookup"><span data-stu-id="c9bcd-122">Select the **CustomActivity** again and the category and **Assign** activity is added back.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c9bcd-123">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="c9bcd-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c9bcd-124">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="c9bcd-124">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c9bcd-125">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="c9bcd-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c9bcd-126">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="c9bcd-126">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\IActivityToolboxService`
