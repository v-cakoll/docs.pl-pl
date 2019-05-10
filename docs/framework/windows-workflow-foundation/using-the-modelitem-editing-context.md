---
title: Używanie kontekstu edycyjnego ModelItem
ms.date: 03/30/2017
ms.assetid: 7f9f1ea5-0147-4079-8eca-be94f00d3aa1
ms.openlocfilehash: 8b2f2b8d4c528de14ea8b37e4eda8190f1757c22
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64664709"
---
# <a name="using-the-modelitem-editing-context"></a><span data-ttu-id="17b16-102">Używanie kontekstu edycyjnego ModelItem</span><span class="sxs-lookup"><span data-stu-id="17b16-102">Using the ModelItem Editing Context</span></span>
<span data-ttu-id="17b16-103"><xref:System.Activities.Presentation.Model.ModelItem> Kontekstu do edycji jest obiekt, który aplikacja hosta używa do komunikowania się za pomocą projektanta.</span><span class="sxs-lookup"><span data-stu-id="17b16-103">The <xref:System.Activities.Presentation.Model.ModelItem> editing context is the object that the host application uses to communicate with the designer.</span></span> <span data-ttu-id="17b16-104"><xref:System.Activities.Presentation.EditingContext> udostępnia dwie metody <xref:System.Activities.Presentation.EditingContext.Items%2A> i <xref:System.Activities.Presentation.EditingContext.Services%2A>, których można używać</span><span class="sxs-lookup"><span data-stu-id="17b16-104"><xref:System.Activities.Presentation.EditingContext> exposes two methods, <xref:System.Activities.Presentation.EditingContext.Items%2A> and <xref:System.Activities.Presentation.EditingContext.Services%2A>, which can be used</span></span>  
  
## <a name="the-items-collection"></a><span data-ttu-id="17b16-105">Kolekcja elementów</span><span class="sxs-lookup"><span data-stu-id="17b16-105">The Items collection</span></span>  
 <span data-ttu-id="17b16-106"><xref:System.Activities.Presentation.EditingContext.Items%2A> Kolekcji umożliwia dostęp do danych, który jest udostępniany między hostem a projektanta lub danych, która jest dostępna dla wszystkich projektantów.</span><span class="sxs-lookup"><span data-stu-id="17b16-106">The <xref:System.Activities.Presentation.EditingContext.Items%2A> collection is used to access data that is shared between the host and the designer, or data that is available to all designers.</span></span> <span data-ttu-id="17b16-107">Ta kolekcja zawiera następujące funkcje, dostępne za pośrednictwem <xref:System.Activities.Presentation.ContextItemManager> klasy:</span><span class="sxs-lookup"><span data-stu-id="17b16-107">This collection has the following capabilities, accessed via the <xref:System.Activities.Presentation.ContextItemManager> class:</span></span>  
  
1. <xref:System.Activities.Presentation.ContextItemManager.GetValue%2A>  
  
2. <xref:System.Activities.Presentation.ContextItemManager.Subscribe%2A>  
  
3. <xref:System.Activities.Presentation.ContextItemManager.Unsubscribe%2A>  
  
4. <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A>  
  
## <a name="the-services-collection"></a><span data-ttu-id="17b16-108">Kolekcja usług</span><span class="sxs-lookup"><span data-stu-id="17b16-108">The Services collection</span></span>  
 <span data-ttu-id="17b16-109"><xref:System.Activities.Presentation.EditingContext.Services%2A> Kolekcji umożliwia dostęp do usług używanych przez projektanta do interakcji z hostem lub usług korzystających z wszystkich projektantów.</span><span class="sxs-lookup"><span data-stu-id="17b16-109">The <xref:System.Activities.Presentation.EditingContext.Services%2A> collection is used to access services that the designer uses to interact with the host, or services that all designers use.</span></span> <span data-ttu-id="17b16-110">Ta kolekcja zawiera następujących metod Uwaga:</span><span class="sxs-lookup"><span data-stu-id="17b16-110">This collection has the following methods of note:</span></span>  
  
1. <xref:System.Activities.Presentation.ServiceManager.Publish%2A>  
  
2. <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A>  
  
3. <xref:System.Activities.Presentation.ServiceManager.Unsubscribe%2A>  
  
4. <xref:System.Activities.Presentation.ServiceManager.GetService%2A>  
  
## <a name="assigning-a-designer-an-activity"></a><span data-ttu-id="17b16-111">Przypisywanie projektanta działań</span><span class="sxs-lookup"><span data-stu-id="17b16-111">Assigning a designer an activity</span></span>  
 <span data-ttu-id="17b16-112">Aby określić projektanta, który używa działania, atrybut projektanta jest używany.</span><span class="sxs-lookup"><span data-stu-id="17b16-112">To specify which designer an activity uses, the Designer attribute is used.</span></span>  
  
```  
[Designer(typeof(MyClassDesigner))]  
public sealed class MyClass : CodeActivity  
{  
```  
  
## <a name="creating-a-service"></a><span data-ttu-id="17b16-113">Tworzenie usługi</span><span class="sxs-lookup"><span data-stu-id="17b16-113">Creating a service</span></span>  
 <span data-ttu-id="17b16-114">Aby utworzyć usługę, która służy jako kanał informacji między projektanta i hosta, interfejs i implementacja musi zostać utworzona.</span><span class="sxs-lookup"><span data-stu-id="17b16-114">To create a service that serves as a conduit of information between the designer and the host, an interface and an implementation must be created.</span></span> <span data-ttu-id="17b16-115">Ten interfejs jest używany przez <xref:System.Activities.Presentation.ServiceManager.Publish%2A> metodę, aby zdefiniować członków usługi i implementację zawiera logikę dla usługi.</span><span class="sxs-lookup"><span data-stu-id="17b16-115">The interface is used by the <xref:System.Activities.Presentation.ServiceManager.Publish%2A> method to define the members of the service, and the implementation contains the logic for the service.</span></span> <span data-ttu-id="17b16-116">W poniższym przykładzie kodu są tworzone interfejsu usługi i implementację.</span><span class="sxs-lookup"><span data-stu-id="17b16-116">In the following code example, a service interface and implementation are created.</span></span>  
  
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
  
## <a name="publishing-a-service"></a><span data-ttu-id="17b16-117">Usługa publikowania</span><span class="sxs-lookup"><span data-stu-id="17b16-117">Publishing a service</span></span>  
 <span data-ttu-id="17b16-118">Do projektanta w celu korzystania z usługi, musi najpierw być opublikowane przez hosta, za pomocą <xref:System.Activities.Presentation.ServiceManager.Publish%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="17b16-118">For a designer to consume a service, it must first be published by the host using the <xref:System.Activities.Presentation.ServiceManager.Publish%2A> method.</span></span>  
  
```  
this.Context.Services.Publish<IMyService>(new MyServiceImpl);  
```  
  
## <a name="subscribing-to-a-service"></a><span data-ttu-id="17b16-119">Subskrybowanie usługi</span><span class="sxs-lookup"><span data-stu-id="17b16-119">Subscribing to a service</span></span>  
 <span data-ttu-id="17b16-120">Projektant uzyskuje dostęp do usługi za pomocą <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A> method in Class metoda <xref:System.Activities.Presentation.WorkflowViewElement.OnModelItemChanged%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="17b16-120">The designer obtains access to the service using the <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A> method in the <xref:System.Activities.Presentation.WorkflowViewElement.OnModelItemChanged%2A> method.</span></span> <span data-ttu-id="17b16-121">Poniższy fragment kodu przedstawia sposób subskrybowania usługi.</span><span class="sxs-lookup"><span data-stu-id="17b16-121">The following code snippet demonstrates how to subscribe to a service.</span></span>  
  
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
  
## <a name="sharing-data-using-the-items-collection"></a><span data-ttu-id="17b16-122">Udostępnianie danych przy użyciu kolekcji elementów</span><span class="sxs-lookup"><span data-stu-id="17b16-122">Sharing data using the Items collection</span></span>  
 <span data-ttu-id="17b16-123">Za pomocą kolekcji elementów jest podobne do kolekcji usługi, chyba że <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A> zamiast publikacji jest używana.</span><span class="sxs-lookup"><span data-stu-id="17b16-123">Using the Items collection is similar to using the Services collection, except that <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A> is used instead of Publish.</span></span> <span data-ttu-id="17b16-124">Ta kolekcja jest bardziej odpowiednia na potrzeby udostępniania proste dane między projektantów i hosta, a nie złożoną funkcji.</span><span class="sxs-lookup"><span data-stu-id="17b16-124">This collection is more appropriate for sharing simple data between the designers and the host, rather than complex functionality.</span></span>  
  
## <a name="editingcontext-host-items-and-services"></a><span data-ttu-id="17b16-125">EditingContext hosta i usług</span><span class="sxs-lookup"><span data-stu-id="17b16-125">EditingContext host items and services</span></span>  
 <span data-ttu-id="17b16-126">.NET Framework udostępnia wiele wbudowanych elementów i usługi dostępne za pośrednictwem Kontekst edycyjny.</span><span class="sxs-lookup"><span data-stu-id="17b16-126">The .NET Framework provides a number of built-in items and services accessed through the editing context.</span></span>  
  
 <span data-ttu-id="17b16-127">Elementy:</span><span class="sxs-lookup"><span data-stu-id="17b16-127">Items:</span></span>  
  
- <span data-ttu-id="17b16-128"><xref:System.Activities.Presentation.Hosting.AssemblyContextControlItem>: Zarządza listę przywoływanych zestawów lokalnych, które będą używane w przepływie pracy formantami (takimi jak Edytor wyrażeń).</span><span class="sxs-lookup"><span data-stu-id="17b16-128"><xref:System.Activities.Presentation.Hosting.AssemblyContextControlItem>: Manages the list of referenced local assemblies that will be used inside the workflow for controls (such as the expression editor).</span></span>  
  
- <span data-ttu-id="17b16-129"><xref:System.Activities.Presentation.Hosting.ReadOnlyState>: Wskazuje, czy Projektant znajduje się w stanie tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="17b16-129"><xref:System.Activities.Presentation.Hosting.ReadOnlyState>: Indicates whether the designer is in a read-only state.</span></span>  
  
- <span data-ttu-id="17b16-130"><xref:System.Activities.Presentation.View.Selection>: Definiuje kolekcję obiektów, które są obecnie wybrane.</span><span class="sxs-lookup"><span data-stu-id="17b16-130"><xref:System.Activities.Presentation.View.Selection>: Defines the collection of objects that are currently selected.</span></span>  
  
- <span data-ttu-id="17b16-131"><xref:System.Activities.Presentation.Hosting.WorkflowCommandExtensionItem>:</span><span class="sxs-lookup"><span data-stu-id="17b16-131"><xref:System.Activities.Presentation.Hosting.WorkflowCommandExtensionItem>:</span></span>  
  
- <span data-ttu-id="17b16-132"><xref:System.Activities.Presentation.WorkflowFileItem>: Zawiera informacje o pliku, na podstawie bieżącej sesji edytowania.</span><span class="sxs-lookup"><span data-stu-id="17b16-132"><xref:System.Activities.Presentation.WorkflowFileItem>: Provides information on the file that the current editing session is based on.</span></span>  
  
 <span data-ttu-id="17b16-133">Usługi:</span><span class="sxs-lookup"><span data-stu-id="17b16-133">Services:</span></span>  
  
- <span data-ttu-id="17b16-134"><xref:System.Activities.Presentation.Model.AttachedPropertiesService>: Zezwala na właściwości w celu dodania do bieżącego wystąpienia przy użyciu <xref:System.Activities.Presentation.Model.AttachedPropertiesService.AddProperty%2A>.</span><span class="sxs-lookup"><span data-stu-id="17b16-134"><xref:System.Activities.Presentation.Model.AttachedPropertiesService>: Allows properties to be added to the current instance, using <xref:System.Activities.Presentation.Model.AttachedPropertiesService.AddProperty%2A>.</span></span>  
  
- <span data-ttu-id="17b16-135"><xref:System.Activities.Presentation.View.DesignerView>: Umożliwia dostęp do właściwości na kanwie projektanta.</span><span class="sxs-lookup"><span data-stu-id="17b16-135"><xref:System.Activities.Presentation.View.DesignerView>: Allows access to the properties of the designer canvas.</span></span>  
  
- <span data-ttu-id="17b16-136"><xref:System.Activities.Presentation.IActivityToolboxService>: Zezwala na zawartość przybornika do zaktualizowania.</span><span class="sxs-lookup"><span data-stu-id="17b16-136"><xref:System.Activities.Presentation.IActivityToolboxService>: Allows the contents of the toolbox to be updated.</span></span>  
  
- <span data-ttu-id="17b16-137"><xref:System.Activities.Presentation.Hosting.ICommandService>: Umożliwia integrację polecenia projektanta (np. Menu kontekstowe) z implementacji usługi dostarczane przez niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="17b16-137"><xref:System.Activities.Presentation.Hosting.ICommandService>: Used to integrate designer commands (such as Context Menu) with custom-provided service implementations.</span></span>  
  
- <span data-ttu-id="17b16-138"><xref:System.Activities.Presentation.Debug.IDesignerDebugView>: Oferuje funkcję dla projektanta debugera.</span><span class="sxs-lookup"><span data-stu-id="17b16-138"><xref:System.Activities.Presentation.Debug.IDesignerDebugView>: Provides functionality for the designer debugger.</span></span>  
  
- <span data-ttu-id="17b16-139"><xref:System.Activities.Presentation.View.IExpressionEditorService>: Zapewnia dostęp do okna dialogowego edytora wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="17b16-139"><xref:System.Activities.Presentation.View.IExpressionEditorService>: Provides access to the Expression Editor dialog.</span></span>  
  
- <span data-ttu-id="17b16-140"><xref:System.Activities.Presentation.IIntegratedHelpService>: Zapewnia narzędzia Projektant z funkcjonalnością zintegrowana Pomoc.</span><span class="sxs-lookup"><span data-stu-id="17b16-140"><xref:System.Activities.Presentation.IIntegratedHelpService>: Provides the designer with integrated help functionality.</span></span>  
  
- <span data-ttu-id="17b16-141"><xref:System.Activities.Presentation.Validation.IValidationErrorService>: Zapewnia dostęp do błędów sprawdzania poprawności, za pomocą <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A>.</span><span class="sxs-lookup"><span data-stu-id="17b16-141"><xref:System.Activities.Presentation.Validation.IValidationErrorService>: Provides access to validation errors using <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A>.</span></span>  
  
- <span data-ttu-id="17b16-142"><xref:System.Activities.Presentation.IWorkflowDesignerStorageService>: Udostępnia wewnętrzna usługa do przechowywania i pobierania danych.</span><span class="sxs-lookup"><span data-stu-id="17b16-142"><xref:System.Activities.Presentation.IWorkflowDesignerStorageService>: Provides an internal service to store and retrieve data.</span></span> <span data-ttu-id="17b16-143">Ta usługa jest używana wewnętrznie przez program .NET Framework i nie jest przeznaczona do użytku zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="17b16-143">This service is used internally by the .NET Framework, and is not intended for external use.</span></span>  
  
- <span data-ttu-id="17b16-144"><xref:System.Activities.Presentation.IXamlLoadErrorService>: Zapewnia dostęp do XAML obciążenia Błąd kolekcji za pomocą <xref:System.Activities.Presentation.IXamlLoadErrorService.ShowXamlLoadErrors%2A>.</span><span class="sxs-lookup"><span data-stu-id="17b16-144"><xref:System.Activities.Presentation.IXamlLoadErrorService>: Provides access to the XAML load error collection using <xref:System.Activities.Presentation.IXamlLoadErrorService.ShowXamlLoadErrors%2A>.</span></span>  
  
- <span data-ttu-id="17b16-145"><xref:System.Activities.Presentation.Services.ModelService>: Używane przez projektanta do interakcji z modelu edytowanym przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="17b16-145"><xref:System.Activities.Presentation.Services.ModelService>: Used by the designer to interact with the model of the workflow being edited.</span></span>  
  
- <span data-ttu-id="17b16-146"><xref:System.Activities.Presentation.Model.ModelTreeManager>: Zapewnia dostęp do katalogu głównego modelu elementu drzewa za pomocą <xref:System.Activities.Presentation.Model.ModelItem.Root%2A>.</span><span class="sxs-lookup"><span data-stu-id="17b16-146"><xref:System.Activities.Presentation.Model.ModelTreeManager>: Provides access to the root of the model item tree using <xref:System.Activities.Presentation.Model.ModelItem.Root%2A>.</span></span>  
  
- <span data-ttu-id="17b16-147"><xref:System.Activities.Presentation.UndoEngine>: Zapewnia Cofnij i wykonaj ponownie funkcji.</span><span class="sxs-lookup"><span data-stu-id="17b16-147"><xref:System.Activities.Presentation.UndoEngine>: Provides undo and redo functionality.</span></span>  
  
- <span data-ttu-id="17b16-148"><xref:System.Activities.Presentation.Services.ViewService>: Elementy wizualne map podstawowych elementów modelu.</span><span class="sxs-lookup"><span data-stu-id="17b16-148"><xref:System.Activities.Presentation.Services.ViewService>: Maps visual elements to underlying model items.</span></span>  
  
- <span data-ttu-id="17b16-149"><xref:System.Activities.Presentation.View.ViewStateService>: Magazyny widoku stany elementów modelu.</span><span class="sxs-lookup"><span data-stu-id="17b16-149"><xref:System.Activities.Presentation.View.ViewStateService>: Stores view states for model items.</span></span>  
  
- <span data-ttu-id="17b16-150"><xref:System.Activities.Presentation.View.VirtualizedContainerService>: Umożliwia dostosowywanie zachowania interfejsu użytkownika wirtualnego kontenera.</span><span class="sxs-lookup"><span data-stu-id="17b16-150"><xref:System.Activities.Presentation.View.VirtualizedContainerService>: Used to customize the virtual container UI behavior.</span></span>  
  
- <span data-ttu-id="17b16-151"><xref:System.Activities.Presentation.Hosting.WindowHelperService>: Umożliwia rejestrowanie i wyrejestrowywanie delegatów dla powiadomień o zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="17b16-151"><xref:System.Activities.Presentation.Hosting.WindowHelperService>: Used to register and unregister delegates for event notifications.</span></span> <span data-ttu-id="17b16-152">Umożliwia także właścicielem okna, należy ustawić.</span><span class="sxs-lookup"><span data-stu-id="17b16-152">Also allows a window owner to be set.</span></span>
