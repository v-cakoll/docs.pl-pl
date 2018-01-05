---
title: "Przy użyciu ModelItem edycji kontekstu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7f9f1ea5-0147-4079-8eca-be94f00d3aa1
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5d52c0a2305a3f38cf9a228f211021006ee8b131
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="using-the-modelitem-editing-context"></a><span data-ttu-id="1988b-102">Przy użyciu ModelItem edycji kontekstu</span><span class="sxs-lookup"><span data-stu-id="1988b-102">Using the ModelItem Editing Context</span></span>
<span data-ttu-id="1988b-103"><xref:System.Activities.Presentation.Model.ModelItem> Edycji kontekstu jest obiekt, który aplikacja hosta używa do komunikacji przy użyciu projektanta.</span><span class="sxs-lookup"><span data-stu-id="1988b-103">The <xref:System.Activities.Presentation.Model.ModelItem> editing context is the object that the host application uses to communicate with the designer.</span></span> <span data-ttu-id="1988b-104"><xref:System.Activities.Presentation.EditingContext>udostępnia dwie metody <xref:System.Activities.Presentation.EditingContext.Items%2A> i <xref:System.Activities.Presentation.EditingContext.Services%2A>, której można użyć</span><span class="sxs-lookup"><span data-stu-id="1988b-104"><xref:System.Activities.Presentation.EditingContext> exposes two methods, <xref:System.Activities.Presentation.EditingContext.Items%2A> and <xref:System.Activities.Presentation.EditingContext.Services%2A>, which can be used</span></span>  
  
## <a name="the-items-collection"></a><span data-ttu-id="1988b-105">Kolekcja elementów</span><span class="sxs-lookup"><span data-stu-id="1988b-105">The Items collection</span></span>  
 <span data-ttu-id="1988b-106"><xref:System.Activities.Presentation.EditingContext.Items%2A> Kolekcji umożliwia dostęp do danych, które są współużytkowane przez hosta i Projektant lub danych, która jest dostępna dla wszystkich projektantów.</span><span class="sxs-lookup"><span data-stu-id="1988b-106">The <xref:System.Activities.Presentation.EditingContext.Items%2A> collection is used to access data that is shared between the host and the designer, or data that is available to all designers.</span></span> <span data-ttu-id="1988b-107">Ta kolekcja ma następujące możliwości dostępne za pośrednictwem <xref:System.Activities.Presentation.ContextItemManager> klasy:</span><span class="sxs-lookup"><span data-stu-id="1988b-107">This collection has the following capabilities, accessed via the <xref:System.Activities.Presentation.ContextItemManager> class:</span></span>  
  
1.  <xref:System.Activities.Presentation.ContextItemManager.GetValue%2A>  
  
2.  <xref:System.Activities.Presentation.ContextItemManager.Subscribe%2A>  
  
3.  <xref:System.Activities.Presentation.ContextItemManager.Unsubscribe%2A>  
  
4.  <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A>  
  
## <a name="the-services-collection"></a><span data-ttu-id="1988b-108">Kolekcja usług</span><span class="sxs-lookup"><span data-stu-id="1988b-108">The Services collection</span></span>  
 <span data-ttu-id="1988b-109"><xref:System.Activities.Presentation.EditingContext.Services%2A> Umożliwia dostęp do usług używanych w projektancie do interakcji z hostem lub usługi, które wszystkie projektanci używali kolekcji.</span><span class="sxs-lookup"><span data-stu-id="1988b-109">The <xref:System.Activities.Presentation.EditingContext.Services%2A> collection is used to access services that the designer uses to interact with the host, or services that all designers use.</span></span> <span data-ttu-id="1988b-110">Ta kolekcja ma Uwaga z następujących metod:</span><span class="sxs-lookup"><span data-stu-id="1988b-110">This collection has the following methods of note:</span></span>  
  
1.  <xref:System.Activities.Presentation.ServiceManager.Publish%2A>  
  
2.  <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A>  
  
3.  <xref:System.Activities.Presentation.ServiceManager.Unsubscribe%2A>  
  
4.  <xref:System.Activities.Presentation.ServiceManager.GetService%2A>  
  
## <a name="assigning-a-designer-an-activity"></a><span data-ttu-id="1988b-111">Przypisywanie projektanta działania</span><span class="sxs-lookup"><span data-stu-id="1988b-111">Assigning a designer an activity</span></span>  
 <span data-ttu-id="1988b-112">Aby określić, które projektanta używa działania, atrybut projektanta jest używany.</span><span class="sxs-lookup"><span data-stu-id="1988b-112">To specify which designer an activity uses, the Designer attribute is used.</span></span>  
  
```  
[Designer(typeof(MyClassDesigner))]  
public sealed class MyClass : CodeActivity  
{  
```  
  
## <a name="creating-a-service"></a><span data-ttu-id="1988b-113">Tworzenie usługi</span><span class="sxs-lookup"><span data-stu-id="1988b-113">Creating a service</span></span>  
 <span data-ttu-id="1988b-114">Aby utworzyć usługę, która służy jako kanał informacji między projektanta i hosta, należy utworzyć interfejs i implementacji.</span><span class="sxs-lookup"><span data-stu-id="1988b-114">To create a service that serves as a conduit of information between the designer and the host, an interface and an implementation must be created.</span></span> <span data-ttu-id="1988b-115">Ten interfejs jest używany przez <xref:System.Activities.Presentation.ServiceManager.Publish%2A> metodę, aby zdefiniować elementów członkowskich usługi i implementację zawiera logikę dla usługi.</span><span class="sxs-lookup"><span data-stu-id="1988b-115">The interface is used by the <xref:System.Activities.Presentation.ServiceManager.Publish%2A> method to define the members of the service, and the implementation contains the logic for the service.</span></span> <span data-ttu-id="1988b-116">W poniższym przykładzie kodu interfejsu usługi i implementacji są tworzone.</span><span class="sxs-lookup"><span data-stu-id="1988b-116">In the following code example, a service interface and implementation are created.</span></span>  
  
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
  
## <a name="publishing-a-service"></a><span data-ttu-id="1988b-117">Usługa publikowania</span><span class="sxs-lookup"><span data-stu-id="1988b-117">Publishing a service</span></span>  
 <span data-ttu-id="1988b-118">Projektanta korzystać z usługi, musi najpierw być opublikowane przez hosta przy użyciu <xref:System.Activities.Presentation.ServiceManager.Publish%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="1988b-118">For a designer to consume a service, it must first be published by the host using the <xref:System.Activities.Presentation.ServiceManager.Publish%2A> method.</span></span>  
  
```  
this.Context.Services.Publish<IMyService>(new MyServiceImpl);  
```  
  
## <a name="subscribing-to-a-service"></a><span data-ttu-id="1988b-119">Subskrybowanie usługi</span><span class="sxs-lookup"><span data-stu-id="1988b-119">Subscribing to a service</span></span>  
 <span data-ttu-id="1988b-120">Projektant uzyskuje dostęp do usługi przy użyciu <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A> metoda <xref:System.Activities.Presentation.WorkflowViewElement.OnModelItemChanged%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="1988b-120">The designer obtains access to the service using the <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A> method in the <xref:System.Activities.Presentation.WorkflowViewElement.OnModelItemChanged%2A> method.</span></span> <span data-ttu-id="1988b-121">Poniższy fragment kodu przedstawia sposób subskrybowania usługi.</span><span class="sxs-lookup"><span data-stu-id="1988b-121">The following code snippet demonstrates how to subscribe to a service.</span></span>  
  
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
  
## <a name="sharing-data-using-the-items-collection"></a><span data-ttu-id="1988b-122">Udostępnianie danych za pomocą kolekcji elementów</span><span class="sxs-lookup"><span data-stu-id="1988b-122">Sharing data using the Items collection</span></span>  
 <span data-ttu-id="1988b-123">Za pomocą kolekcji elementów jest podobny do sposobu używania kolekcji usług, z wyjątkiem <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A> jest używana zamiast funkcji publikowania.</span><span class="sxs-lookup"><span data-stu-id="1988b-123">Using the Items collection is similar to using the Services collection, except that <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A> is used instead of Publish.</span></span> <span data-ttu-id="1988b-124">Ta kolekcja jest bardziej odpowiednie dla udostępniania proste danych między projektantów i hosta, a nie złożonych funkcji.</span><span class="sxs-lookup"><span data-stu-id="1988b-124">This collection is more appropriate for sharing simple data between the designers and the host, rather than complex functionality.</span></span>  
  
## <a name="editingcontext-host-items-and-services"></a><span data-ttu-id="1988b-125">Obiekty hosta EditingContext i usługi</span><span class="sxs-lookup"><span data-stu-id="1988b-125">EditingContext host items and services</span></span>  
 <span data-ttu-id="1988b-126">.Net Framework udostępnia szereg wbudowanych elementów i usługi dostępne za pośrednictwem Kontekst edycyjny.</span><span class="sxs-lookup"><span data-stu-id="1988b-126">The .Net Framework provides a number of built-in items and services accessed through the editing context.</span></span>  
  
 <span data-ttu-id="1988b-127">Elementy:</span><span class="sxs-lookup"><span data-stu-id="1988b-127">Items:</span></span>  
  
-   <span data-ttu-id="1988b-128"><xref:System.Activities.Presentation.Hosting.AssemblyContextControlItem>: Służą do zarządzania listą zestawów występujących w odwołaniach lokalne, które będą używane w przepływie pracy (takie jak Edytor wyrażeń).</span><span class="sxs-lookup"><span data-stu-id="1988b-128"><xref:System.Activities.Presentation.Hosting.AssemblyContextControlItem>: Manages the list of referenced local assemblies that will be used inside the workflow for controls (such as the expression editor).</span></span>  
  
-   <span data-ttu-id="1988b-129"><xref:System.Activities.Presentation.Hosting.ReadOnlyState>: Wskazuje, czy projektant jest w stanie tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="1988b-129"><xref:System.Activities.Presentation.Hosting.ReadOnlyState>: Indicates whether the designer is in a read-only state.</span></span>  
  
-   <span data-ttu-id="1988b-130"><xref:System.Activities.Presentation.View.Selection>: Określa kolekcję obiektów, które są aktualnie wybrane.</span><span class="sxs-lookup"><span data-stu-id="1988b-130"><xref:System.Activities.Presentation.View.Selection>: Defines the collection of objects that are currently selected.</span></span>  
  
-   <span data-ttu-id="1988b-131"><xref:System.Activities.Presentation.Hosting.WorkflowCommandExtensionItem>:</span><span class="sxs-lookup"><span data-stu-id="1988b-131"><xref:System.Activities.Presentation.Hosting.WorkflowCommandExtensionItem>:</span></span>  
  
-   <span data-ttu-id="1988b-132"><xref:System.Activities.Presentation.WorkflowFileItem>: Zawiera informacje o pliku, na podstawie bieżącej sesji edytowania.</span><span class="sxs-lookup"><span data-stu-id="1988b-132"><xref:System.Activities.Presentation.WorkflowFileItem>: Provides information on the file that the current editing session is based on.</span></span>  
  
 <span data-ttu-id="1988b-133">Usługi:</span><span class="sxs-lookup"><span data-stu-id="1988b-133">Services:</span></span>  
  
-   <span data-ttu-id="1988b-134"><xref:System.Activities.Presentation.Model.AttachedPropertiesService>: Umożliwia właściwości mają zostać dodane do bieżącego wystąpienia przy użyciu <xref:System.Activities.Presentation.Model.AttachedPropertiesService.AddProperty%2A>.</span><span class="sxs-lookup"><span data-stu-id="1988b-134"><xref:System.Activities.Presentation.Model.AttachedPropertiesService>: Allows properties to be added to the current instance, using <xref:System.Activities.Presentation.Model.AttachedPropertiesService.AddProperty%2A>.</span></span>  
  
-   <span data-ttu-id="1988b-135"><xref:System.Activities.Presentation.View.DesignerView>: Zezwala na dostęp do właściwości obszaru projektowania.</span><span class="sxs-lookup"><span data-stu-id="1988b-135"><xref:System.Activities.Presentation.View.DesignerView>: Allows access to the properties of the designer canvas.</span></span>  
  
-   <span data-ttu-id="1988b-136"><xref:System.Activities.Presentation.IActivityToolboxService>: Umożliwia zawartości przybornika do zaktualizowania.</span><span class="sxs-lookup"><span data-stu-id="1988b-136"><xref:System.Activities.Presentation.IActivityToolboxService>: Allows the contents of the toolbox to be updated.</span></span>  
  
-   <span data-ttu-id="1988b-137"><xref:System.Activities.Presentation.Hosting.ICommandService>: Używany do integrowania projektanta poleceń (np. Menu kontekstowe) z implementacji usługi dostarczane przez niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="1988b-137"><xref:System.Activities.Presentation.Hosting.ICommandService>: Used to integrate designer commands (such as Context Menu) with custom-provided service implementations.</span></span>  
  
-   <span data-ttu-id="1988b-138"><xref:System.Activities.Presentation.Debug.IDesignerDebugView>: Zawiera funkcje projektanta debugera.</span><span class="sxs-lookup"><span data-stu-id="1988b-138"><xref:System.Activities.Presentation.Debug.IDesignerDebugView>: Provides functionality for the designer debugger.</span></span>  
  
-   <span data-ttu-id="1988b-139"><xref:System.Activities.Presentation.View.IExpressionEditorService>: Zapewnia dostęp do okna dialogowego edytora wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="1988b-139"><xref:System.Activities.Presentation.View.IExpressionEditorService>: Provides access to the Expression Editor dialog.</span></span>  
  
-   <span data-ttu-id="1988b-140"><xref:System.Activities.Presentation.IIntegratedHelpService>: Zawiera projektanta z funkcji zintegrowanego pomocy.</span><span class="sxs-lookup"><span data-stu-id="1988b-140"><xref:System.Activities.Presentation.IIntegratedHelpService>: Provides the designer with integrated help functionality.</span></span>  
  
-   <span data-ttu-id="1988b-141"><xref:System.Activities.Presentation.Validation.IValidationErrorService>: Zapewnia dostęp do błędy sprawdzania poprawności przy użyciu <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A>.</span><span class="sxs-lookup"><span data-stu-id="1988b-141"><xref:System.Activities.Presentation.Validation.IValidationErrorService>: Provides access to validation errors using <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A>.</span></span>  
  
-   <span data-ttu-id="1988b-142"><xref:System.Activities.Presentation.IWorkflowDesignerStorageService>: Zawiera wewnętrzny usługi do przechowywania i pobierania danych.</span><span class="sxs-lookup"><span data-stu-id="1988b-142"><xref:System.Activities.Presentation.IWorkflowDesignerStorageService>: Provides an internal service to store and retrieve data.</span></span> <span data-ttu-id="1988b-143">Ta usługa jest używana wewnętrznie przez programu .net Framework i nie jest przeznaczona do użytku zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="1988b-143">This service is used internally by the .Net Framework, and is not intended for external use.</span></span>  
  
-   <span data-ttu-id="1988b-144"><xref:System.Activities.Presentation.IXamlLoadErrorService>: Zapewnia dostęp do pliku XAML obciążenia Błąd kolekcji przy użyciu <xref:System.Activities.Presentation.IXamlLoadErrorService.ShowXamlLoadErrors%2A>.</span><span class="sxs-lookup"><span data-stu-id="1988b-144"><xref:System.Activities.Presentation.IXamlLoadErrorService>: Provides access to the XAML load error collection using <xref:System.Activities.Presentation.IXamlLoadErrorService.ShowXamlLoadErrors%2A>.</span></span>  
  
-   <span data-ttu-id="1988b-145"><xref:System.Activities.Presentation.Services.ModelService>: Służy do interakcji z modelu przepływu pracy edytowany przez projektanta.</span><span class="sxs-lookup"><span data-stu-id="1988b-145"><xref:System.Activities.Presentation.Services.ModelService>: Used by the designer to interact with the model of the workflow being edited.</span></span>  
  
-   <span data-ttu-id="1988b-146"><xref:System.Activities.Presentation.Model.ModelTreeManager>: Zapewnia dostęp do katalogu głównego model element drzewa przy użyciu <xref:System.Activities.Presentation.Model.ModelItem.Root%2A>.</span><span class="sxs-lookup"><span data-stu-id="1988b-146"><xref:System.Activities.Presentation.Model.ModelTreeManager>: Provides access to the root of the model item tree using <xref:System.Activities.Presentation.Model.ModelItem.Root%2A>.</span></span>  
  
-   <span data-ttu-id="1988b-147"><xref:System.Activities.Presentation.UndoEngine>: Zawiera cofania i ponawiania funkcji.</span><span class="sxs-lookup"><span data-stu-id="1988b-147"><xref:System.Activities.Presentation.UndoEngine>: Provides undo and redo functionality.</span></span>  
  
-   <span data-ttu-id="1988b-148"><xref:System.Activities.Presentation.Services.ViewService>: Mapuje elementy wizualne na podstawowe elementy modelu.</span><span class="sxs-lookup"><span data-stu-id="1988b-148"><xref:System.Activities.Presentation.Services.ViewService>: Maps visual elements to underlying model items.</span></span>  
  
-   <span data-ttu-id="1988b-149"><xref:System.Activities.Presentation.View.ViewStateService>: Magazyny wyświetlanie stanów elementów modelu.</span><span class="sxs-lookup"><span data-stu-id="1988b-149"><xref:System.Activities.Presentation.View.ViewStateService>: Stores view states for model items.</span></span>  
  
-   <span data-ttu-id="1988b-150"><xref:System.Activities.Presentation.View.VirtualizedContainerService>: Pozwala dostosować zachowanie interfejsu użytkownika wirtualnego kontenera.</span><span class="sxs-lookup"><span data-stu-id="1988b-150"><xref:System.Activities.Presentation.View.VirtualizedContainerService>: Used to customize the virtual container UI behavior.</span></span>  
  
-   <span data-ttu-id="1988b-151"><xref:System.Activities.Presentation.Hosting.WindowHelperService>: Używany do rejestrowania i wyrejestrowania delegatów powiadomień o zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="1988b-151"><xref:System.Activities.Presentation.Hosting.WindowHelperService>: Used to register and unregister delegates for event notifications.</span></span> <span data-ttu-id="1988b-152">Umożliwia właścicielowi okna można ustawić.</span><span class="sxs-lookup"><span data-stu-id="1988b-152">Also allows a window owner to be set.</span></span>
