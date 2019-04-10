---
title: Używanie kontekstu edycyjnego ModelItem
ms.date: 03/30/2017
ms.assetid: 7f9f1ea5-0147-4079-8eca-be94f00d3aa1
ms.openlocfilehash: a2628bbbf2f6684e5d484b05cd5a2ac622f3b664
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59296892"
---
# <a name="using-the-modelitem-editing-context"></a><span data-ttu-id="c7a93-102">Używanie kontekstu edycyjnego ModelItem</span><span class="sxs-lookup"><span data-stu-id="c7a93-102">Using the ModelItem Editing Context</span></span>
<span data-ttu-id="c7a93-103"><xref:System.Activities.Presentation.Model.ModelItem> Kontekstu do edycji jest obiekt, który aplikacja hosta używa do komunikowania się za pomocą projektanta.</span><span class="sxs-lookup"><span data-stu-id="c7a93-103">The <xref:System.Activities.Presentation.Model.ModelItem> editing context is the object that the host application uses to communicate with the designer.</span></span> <xref:System.Activities.Presentation.EditingContext> <span data-ttu-id="c7a93-104">udostępnia dwie metody <xref:System.Activities.Presentation.EditingContext.Items%2A> i <xref:System.Activities.Presentation.EditingContext.Services%2A>, których można używać</span><span class="sxs-lookup"><span data-stu-id="c7a93-104">exposes two methods, <xref:System.Activities.Presentation.EditingContext.Items%2A> and <xref:System.Activities.Presentation.EditingContext.Services%2A>, which can be used</span></span>  
  
## <a name="the-items-collection"></a><span data-ttu-id="c7a93-105">Kolekcja elementów</span><span class="sxs-lookup"><span data-stu-id="c7a93-105">The Items collection</span></span>  
 <span data-ttu-id="c7a93-106"><xref:System.Activities.Presentation.EditingContext.Items%2A> Kolekcji umożliwia dostęp do danych, który jest udostępniany między hostem a projektanta lub danych, która jest dostępna dla wszystkich projektantów.</span><span class="sxs-lookup"><span data-stu-id="c7a93-106">The <xref:System.Activities.Presentation.EditingContext.Items%2A> collection is used to access data that is shared between the host and the designer, or data that is available to all designers.</span></span> <span data-ttu-id="c7a93-107">Ta kolekcja zawiera następujące funkcje, dostępne za pośrednictwem <xref:System.Activities.Presentation.ContextItemManager> klasy:</span><span class="sxs-lookup"><span data-stu-id="c7a93-107">This collection has the following capabilities, accessed via the <xref:System.Activities.Presentation.ContextItemManager> class:</span></span>  
  
1. <xref:System.Activities.Presentation.ContextItemManager.GetValue%2A>  
  
2. <xref:System.Activities.Presentation.ContextItemManager.Subscribe%2A>  
  
3. <xref:System.Activities.Presentation.ContextItemManager.Unsubscribe%2A>  
  
4. <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A>  
  
## <a name="the-services-collection"></a><span data-ttu-id="c7a93-108">Kolekcja usług</span><span class="sxs-lookup"><span data-stu-id="c7a93-108">The Services collection</span></span>  
 <span data-ttu-id="c7a93-109"><xref:System.Activities.Presentation.EditingContext.Services%2A> Kolekcji umożliwia dostęp do usług używanych przez projektanta do interakcji z hostem lub usług korzystających z wszystkich projektantów.</span><span class="sxs-lookup"><span data-stu-id="c7a93-109">The <xref:System.Activities.Presentation.EditingContext.Services%2A> collection is used to access services that the designer uses to interact with the host, or services that all designers use.</span></span> <span data-ttu-id="c7a93-110">Ta kolekcja zawiera następujących metod Uwaga:</span><span class="sxs-lookup"><span data-stu-id="c7a93-110">This collection has the following methods of note:</span></span>  
  
1. <xref:System.Activities.Presentation.ServiceManager.Publish%2A>  
  
2. <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A>  
  
3. <xref:System.Activities.Presentation.ServiceManager.Unsubscribe%2A>  
  
4. <xref:System.Activities.Presentation.ServiceManager.GetService%2A>  
  
## <a name="assigning-a-designer-an-activity"></a><span data-ttu-id="c7a93-111">Przypisywanie projektanta działań</span><span class="sxs-lookup"><span data-stu-id="c7a93-111">Assigning a designer an activity</span></span>  
 <span data-ttu-id="c7a93-112">Aby określić projektanta, który używa działania, atrybut projektanta jest używany.</span><span class="sxs-lookup"><span data-stu-id="c7a93-112">To specify which designer an activity uses, the Designer attribute is used.</span></span>  
  
```  
[Designer(typeof(MyClassDesigner))]  
public sealed class MyClass : CodeActivity  
{  
```  
  
## <a name="creating-a-service"></a><span data-ttu-id="c7a93-113">Tworzenie usługi</span><span class="sxs-lookup"><span data-stu-id="c7a93-113">Creating a service</span></span>  
 <span data-ttu-id="c7a93-114">Aby utworzyć usługę, która służy jako kanał informacji między projektanta i hosta, interfejs i implementacja musi zostać utworzona.</span><span class="sxs-lookup"><span data-stu-id="c7a93-114">To create a service that serves as a conduit of information between the designer and the host, an interface and an implementation must be created.</span></span> <span data-ttu-id="c7a93-115">Ten interfejs jest używany przez <xref:System.Activities.Presentation.ServiceManager.Publish%2A> metodę, aby zdefiniować członków usługi i implementację zawiera logikę dla usługi.</span><span class="sxs-lookup"><span data-stu-id="c7a93-115">The interface is used by the <xref:System.Activities.Presentation.ServiceManager.Publish%2A> method to define the members of the service, and the implementation contains the logic for the service.</span></span> <span data-ttu-id="c7a93-116">W poniższym przykładzie kodu są tworzone interfejsu usługi i implementację.</span><span class="sxs-lookup"><span data-stu-id="c7a93-116">In the following code example, a service interface and implementation are created.</span></span>  
  
```  
public interface IMyService  
    {  
        IEnumerable<string> GetValues(string DisplayName);  
    }  
  
    public class MyServiceImpl : IMyService  
    {  
        public IEnumerable<string> GetValues(string DisplayName)  
        {  
            return new string[]  {   
                DisplayName + " One",   
                DisplayName + " Two",  
                "Three " + DisplayName  
            } ;  
        }  
    }  
```  
  
## <a name="publishing-a-service"></a><span data-ttu-id="c7a93-117">Usługa publikowania</span><span class="sxs-lookup"><span data-stu-id="c7a93-117">Publishing a service</span></span>  
 <span data-ttu-id="c7a93-118">Do projektanta w celu korzystania z usługi, musi najpierw być opublikowane przez hosta, za pomocą <xref:System.Activities.Presentation.ServiceManager.Publish%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="c7a93-118">For a designer to consume a service, it must first be published by the host using the <xref:System.Activities.Presentation.ServiceManager.Publish%2A> method.</span></span>  
  
```  
this.Context.Services.Publish<IMyService>(new MyServiceImpl);  
```  
  
## <a name="subscribing-to-a-service"></a><span data-ttu-id="c7a93-119">Subskrybowanie usługi</span><span class="sxs-lookup"><span data-stu-id="c7a93-119">Subscribing to a service</span></span>  
 <span data-ttu-id="c7a93-120">Projektant uzyskuje dostęp do usługi za pomocą <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A> method in Class metoda <xref:System.Activities.Presentation.WorkflowViewElement.OnModelItemChanged%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="c7a93-120">The designer obtains access to the service using the <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A> method in the <xref:System.Activities.Presentation.WorkflowViewElement.OnModelItemChanged%2A> method.</span></span> <span data-ttu-id="c7a93-121">Poniższy fragment kodu przedstawia sposób subskrybowania usługi.</span><span class="sxs-lookup"><span data-stu-id="c7a93-121">The following code snippet demonstrates how to subscribe to a service.</span></span>  
  
```  
protected override void OnModelItemChanged(object newItem)  
{  
    if (!subscribed)  
    {  
        this.Context.Services.Subscribe<IMyService>(  
            servInstance =>  
            {  
                listBox1.ItemsSource = servInstance.GetValues(this.ModelItem.Properties["DisplayName"].ComputedValue.ToString());  
            }  
            );  
        subscribed = true;   
    }  
}  
```  
  
## <a name="sharing-data-using-the-items-collection"></a><span data-ttu-id="c7a93-122">Udostępnianie danych przy użyciu kolekcji elementów</span><span class="sxs-lookup"><span data-stu-id="c7a93-122">Sharing data using the Items collection</span></span>  
 <span data-ttu-id="c7a93-123">Za pomocą kolekcji elementów jest podobne do kolekcji usługi, chyba że <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A> zamiast publikacji jest używana.</span><span class="sxs-lookup"><span data-stu-id="c7a93-123">Using the Items collection is similar to using the Services collection, except that <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A> is used instead of Publish.</span></span> <span data-ttu-id="c7a93-124">Ta kolekcja jest bardziej odpowiednia na potrzeby udostępniania proste dane między projektantów i hosta, a nie złożoną funkcji.</span><span class="sxs-lookup"><span data-stu-id="c7a93-124">This collection is more appropriate for sharing simple data between the designers and the host, rather than complex functionality.</span></span>  
  
## <a name="editingcontext-host-items-and-services"></a><span data-ttu-id="c7a93-125">EditingContext hosta i usług</span><span class="sxs-lookup"><span data-stu-id="c7a93-125">EditingContext host items and services</span></span>  
 <span data-ttu-id="c7a93-126">.NET Framework udostępnia wiele wbudowanych elementów i usługi dostępne za pośrednictwem Kontekst edycyjny.</span><span class="sxs-lookup"><span data-stu-id="c7a93-126">The .NET Framework provides a number of built-in items and services accessed through the editing context.</span></span>  
  
 <span data-ttu-id="c7a93-127">Elementy:</span><span class="sxs-lookup"><span data-stu-id="c7a93-127">Items:</span></span>  
  
-   <xref:System.Activities.Presentation.Hosting.AssemblyContextControlItem><span data-ttu-id="c7a93-128">: Zarządza listę przywoływanych zestawów lokalnych, które będą używane w przepływie pracy formantami (takimi jak Edytor wyrażeń).</span><span class="sxs-lookup"><span data-stu-id="c7a93-128">: Manages the list of referenced local assemblies that will be used inside the workflow for controls (such as the expression editor).</span></span>  
  
-   <xref:System.Activities.Presentation.Hosting.ReadOnlyState><span data-ttu-id="c7a93-129">: Wskazuje, czy Projektant znajduje się w stanie tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="c7a93-129">: Indicates whether the designer is in a read-only state.</span></span>  
  
-   <xref:System.Activities.Presentation.View.Selection><span data-ttu-id="c7a93-130">: Definiuje kolekcję obiektów, które są obecnie wybrane.</span><span class="sxs-lookup"><span data-stu-id="c7a93-130">: Defines the collection of objects that are currently selected.</span></span>  
  
-   <xref:System.Activities.Presentation.Hosting.WorkflowCommandExtensionItem><span data-ttu-id="c7a93-131">:</span><span class="sxs-lookup"><span data-stu-id="c7a93-131">:</span></span>  
  
-   <xref:System.Activities.Presentation.WorkflowFileItem><span data-ttu-id="c7a93-132">: Zawiera informacje o pliku, na podstawie bieżącej sesji edytowania.</span><span class="sxs-lookup"><span data-stu-id="c7a93-132">: Provides information on the file that the current editing session is based on.</span></span>  
  
 <span data-ttu-id="c7a93-133">Usługi:</span><span class="sxs-lookup"><span data-stu-id="c7a93-133">Services:</span></span>  
  
-   <xref:System.Activities.Presentation.Model.AttachedPropertiesService><span data-ttu-id="c7a93-134">: Zezwala na właściwości w celu dodania do bieżącego wystąpienia przy użyciu <xref:System.Activities.Presentation.Model.AttachedPropertiesService.AddProperty%2A>.</span><span class="sxs-lookup"><span data-stu-id="c7a93-134">: Allows properties to be added to the current instance, using <xref:System.Activities.Presentation.Model.AttachedPropertiesService.AddProperty%2A>.</span></span>  
  
-   <xref:System.Activities.Presentation.View.DesignerView><span data-ttu-id="c7a93-135">: Umożliwia dostęp do właściwości na kanwie projektanta.</span><span class="sxs-lookup"><span data-stu-id="c7a93-135">: Allows access to the properties of the designer canvas.</span></span>  
  
-   <xref:System.Activities.Presentation.IActivityToolboxService><span data-ttu-id="c7a93-136">: Zezwala na zawartość przybornika do zaktualizowania.</span><span class="sxs-lookup"><span data-stu-id="c7a93-136">: Allows the contents of the toolbox to be updated.</span></span>  
  
-   <xref:System.Activities.Presentation.Hosting.ICommandService><span data-ttu-id="c7a93-137">: Umożliwia integrację polecenia projektanta (np. Menu kontekstowe) z implementacji usługi dostarczane przez niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="c7a93-137">: Used to integrate designer commands (such as Context Menu) with custom-provided service implementations.</span></span>  
  
-   <xref:System.Activities.Presentation.Debug.IDesignerDebugView><span data-ttu-id="c7a93-138">: Oferuje funkcję dla projektanta debugera.</span><span class="sxs-lookup"><span data-stu-id="c7a93-138">: Provides functionality for the designer debugger.</span></span>  
  
-   <xref:System.Activities.Presentation.View.IExpressionEditorService><span data-ttu-id="c7a93-139">: Zapewnia dostęp do okna dialogowego edytora wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="c7a93-139">: Provides access to the Expression Editor dialog.</span></span>  
  
-   <xref:System.Activities.Presentation.IIntegratedHelpService><span data-ttu-id="c7a93-140">: Zapewnia narzędzia Projektant z funkcjonalnością zintegrowana Pomoc.</span><span class="sxs-lookup"><span data-stu-id="c7a93-140">: Provides the designer with integrated help functionality.</span></span>  
  
-   <xref:System.Activities.Presentation.Validation.IValidationErrorService><span data-ttu-id="c7a93-141">: Zapewnia dostęp do błędów sprawdzania poprawności, za pomocą <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A>.</span><span class="sxs-lookup"><span data-stu-id="c7a93-141">: Provides access to validation errors using <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A>.</span></span>  
  
-   <xref:System.Activities.Presentation.IWorkflowDesignerStorageService><span data-ttu-id="c7a93-142">: Udostępnia wewnętrzna usługa do przechowywania i pobierania danych.</span><span class="sxs-lookup"><span data-stu-id="c7a93-142">: Provides an internal service to store and retrieve data.</span></span> <span data-ttu-id="c7a93-143">Ta usługa jest używana wewnętrznie przez program .NET Framework i nie jest przeznaczona do użytku zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="c7a93-143">This service is used internally by the .NET Framework, and is not intended for external use.</span></span>  
  
-   <xref:System.Activities.Presentation.IXamlLoadErrorService><span data-ttu-id="c7a93-144">: Zapewnia dostęp do XAML obciążenia Błąd kolekcji za pomocą <xref:System.Activities.Presentation.IXamlLoadErrorService.ShowXamlLoadErrors%2A>.</span><span class="sxs-lookup"><span data-stu-id="c7a93-144">: Provides access to the XAML load error collection using <xref:System.Activities.Presentation.IXamlLoadErrorService.ShowXamlLoadErrors%2A>.</span></span>  
  
-   <xref:System.Activities.Presentation.Services.ModelService><span data-ttu-id="c7a93-145">: Używane przez projektanta do interakcji z modelu edytowanym przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="c7a93-145">: Used by the designer to interact with the model of the workflow being edited.</span></span>  
  
-   <xref:System.Activities.Presentation.Model.ModelTreeManager><span data-ttu-id="c7a93-146">: Zapewnia dostęp do katalogu głównego modelu elementu drzewa za pomocą <xref:System.Activities.Presentation.Model.ModelItem.Root%2A>.</span><span class="sxs-lookup"><span data-stu-id="c7a93-146">: Provides access to the root of the model item tree using <xref:System.Activities.Presentation.Model.ModelItem.Root%2A>.</span></span>  
  
-   <xref:System.Activities.Presentation.UndoEngine><span data-ttu-id="c7a93-147">: Zapewnia Cofnij i wykonaj ponownie funkcji.</span><span class="sxs-lookup"><span data-stu-id="c7a93-147">: Provides undo and redo functionality.</span></span>  
  
-   <xref:System.Activities.Presentation.Services.ViewService><span data-ttu-id="c7a93-148">: Elementy wizualne map podstawowych elementów modelu.</span><span class="sxs-lookup"><span data-stu-id="c7a93-148">: Maps visual elements to underlying model items.</span></span>  
  
-   <xref:System.Activities.Presentation.View.ViewStateService><span data-ttu-id="c7a93-149">: Magazyny widoku stany elementów modelu.</span><span class="sxs-lookup"><span data-stu-id="c7a93-149">: Stores view states for model items.</span></span>  
  
-   <xref:System.Activities.Presentation.View.VirtualizedContainerService><span data-ttu-id="c7a93-150">: Umożliwia dostosowywanie zachowania interfejsu użytkownika wirtualnego kontenera.</span><span class="sxs-lookup"><span data-stu-id="c7a93-150">: Used to customize the virtual container UI behavior.</span></span>  
  
-   <xref:System.Activities.Presentation.Hosting.WindowHelperService><span data-ttu-id="c7a93-151">: Umożliwia rejestrowanie i wyrejestrowywanie delegatów dla powiadomień o zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="c7a93-151">: Used to register and unregister delegates for event notifications.</span></span> <span data-ttu-id="c7a93-152">Umożliwia także właścicielem okna, należy ustawić.</span><span class="sxs-lookup"><span data-stu-id="c7a93-152">Also allows a window owner to be set.</span></span>
