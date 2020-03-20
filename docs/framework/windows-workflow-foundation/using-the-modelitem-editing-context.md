---
title: Używanie kontekstu edycyjnego ModelItem
ms.date: 03/30/2017
ms.assetid: 7f9f1ea5-0147-4079-8eca-be94f00d3aa1
ms.openlocfilehash: e1481d96e39f837d72834222d2839c520e880cc6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142517"
---
# <a name="using-the-modelitem-editing-context"></a><span data-ttu-id="a22ed-102">Używanie kontekstu edycyjnego ModelItem</span><span class="sxs-lookup"><span data-stu-id="a22ed-102">Using the ModelItem Editing Context</span></span>
<span data-ttu-id="a22ed-103">Kontekst <xref:System.Activities.Presentation.Model.ModelItem> edycji jest obiektem używanym przez aplikację hosta do komunikowania się z projektantem.</span><span class="sxs-lookup"><span data-stu-id="a22ed-103">The <xref:System.Activities.Presentation.Model.ModelItem> editing context is the object that the host application uses to communicate with the designer.</span></span> <span data-ttu-id="a22ed-104"><xref:System.Activities.Presentation.EditingContext>ujawnia dwie <xref:System.Activities.Presentation.EditingContext.Items%2A> metody, <xref:System.Activities.Presentation.EditingContext.Services%2A>i , które mogą być stosowane</span><span class="sxs-lookup"><span data-stu-id="a22ed-104"><xref:System.Activities.Presentation.EditingContext> exposes two methods, <xref:System.Activities.Presentation.EditingContext.Items%2A> and <xref:System.Activities.Presentation.EditingContext.Services%2A>, which can be used</span></span>  
  
## <a name="the-items-collection"></a><span data-ttu-id="a22ed-105">Kolekcja Items</span><span class="sxs-lookup"><span data-stu-id="a22ed-105">The Items collection</span></span>  
 <span data-ttu-id="a22ed-106">Kolekcja <xref:System.Activities.Presentation.EditingContext.Items%2A> jest używana do uzyskiwania dostępu do danych, które są współużytkowane przez hosta i projektanta lub danych, które są dostępne dla wszystkich projektantów.</span><span class="sxs-lookup"><span data-stu-id="a22ed-106">The <xref:System.Activities.Presentation.EditingContext.Items%2A> collection is used to access data that is shared between the host and the designer, or data that is available to all designers.</span></span> <span data-ttu-id="a22ed-107">Ta kolekcja ma następujące możliwości, dostępne <xref:System.Activities.Presentation.ContextItemManager> za pośrednictwem klasy:</span><span class="sxs-lookup"><span data-stu-id="a22ed-107">This collection has the following capabilities, accessed via the <xref:System.Activities.Presentation.ContextItemManager> class:</span></span>  
  
1. <xref:System.Activities.Presentation.ContextItemManager.GetValue%2A>  
  
2. <xref:System.Activities.Presentation.ContextItemManager.Subscribe%2A>  
  
3. <xref:System.Activities.Presentation.ContextItemManager.Unsubscribe%2A>  
  
4. <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A>  
  
## <a name="the-services-collection"></a><span data-ttu-id="a22ed-108">Kolekcja Usług</span><span class="sxs-lookup"><span data-stu-id="a22ed-108">The Services collection</span></span>  
 <span data-ttu-id="a22ed-109">Kolekcja <xref:System.Activities.Presentation.EditingContext.Services%2A> jest używana do uzyskiwania dostępu do usług używanych przez projektanta do interakcji z hostem lub usług, których używają wszyscy projektanci.</span><span class="sxs-lookup"><span data-stu-id="a22ed-109">The <xref:System.Activities.Presentation.EditingContext.Services%2A> collection is used to access services that the designer uses to interact with the host, or services that all designers use.</span></span> <span data-ttu-id="a22ed-110">Ta kolekcja ma następujące metody uwagi:</span><span class="sxs-lookup"><span data-stu-id="a22ed-110">This collection has the following methods of note:</span></span>  
  
1. <xref:System.Activities.Presentation.ServiceManager.Publish%2A>  
  
2. <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A>  
  
3. <xref:System.Activities.Presentation.ServiceManager.Unsubscribe%2A>  
  
4. <xref:System.Activities.Presentation.ServiceManager.GetService%2A>  
  
## <a name="assigning-a-designer-an-activity"></a><span data-ttu-id="a22ed-111">Przypisywanie projektantowi działania</span><span class="sxs-lookup"><span data-stu-id="a22ed-111">Assigning a designer an activity</span></span>  
 <span data-ttu-id="a22ed-112">Aby określić, który projektant używa działania, używany jest atrybut Projektant.</span><span class="sxs-lookup"><span data-stu-id="a22ed-112">To specify which designer an activity uses, the Designer attribute is used.</span></span>  
  
```csharp  
[Designer(typeof(MyClassDesigner))]  
public sealed class MyClass : CodeActivity  
{
}
```  
  
## <a name="creating-a-service"></a><span data-ttu-id="a22ed-113">Tworzenie usługi</span><span class="sxs-lookup"><span data-stu-id="a22ed-113">Creating a service</span></span>  
 <span data-ttu-id="a22ed-114">Aby utworzyć usługę, która służy jako kanał informacji między projektantem a hostem, należy utworzyć interfejs i implementację.</span><span class="sxs-lookup"><span data-stu-id="a22ed-114">To create a service that serves as a conduit of information between the designer and the host, an interface and an implementation must be created.</span></span> <span data-ttu-id="a22ed-115">Interfejs jest używany <xref:System.Activities.Presentation.ServiceManager.Publish%2A> przez metodę do definiowania elementów członkowskich usługi, a implementacja zawiera logikę usługi.</span><span class="sxs-lookup"><span data-stu-id="a22ed-115">The interface is used by the <xref:System.Activities.Presentation.ServiceManager.Publish%2A> method to define the members of the service, and the implementation contains the logic for the service.</span></span> <span data-ttu-id="a22ed-116">W poniższym przykładzie kodu tworzony jest interfejs i implementacja usługi.</span><span class="sxs-lookup"><span data-stu-id="a22ed-116">In the following code example, a service interface and implementation are created.</span></span>  
  
```csharp  
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
  
## <a name="publishing-a-service"></a><span data-ttu-id="a22ed-117">Publikowanie usługi</span><span class="sxs-lookup"><span data-stu-id="a22ed-117">Publishing a service</span></span>  
 <span data-ttu-id="a22ed-118">Dla projektanta do korzystania z usługi, musi najpierw zostać <xref:System.Activities.Presentation.ServiceManager.Publish%2A> opublikowane przez hosta przy użyciu metody.</span><span class="sxs-lookup"><span data-stu-id="a22ed-118">For a designer to consume a service, it must first be published by the host using the <xref:System.Activities.Presentation.ServiceManager.Publish%2A> method.</span></span>  
  
```csharp  
this.Context.Services.Publish<IMyService>(new MyServiceImpl);  
```  
  
## <a name="subscribing-to-a-service"></a><span data-ttu-id="a22ed-119">Subskrybowanie usługi</span><span class="sxs-lookup"><span data-stu-id="a22ed-119">Subscribing to a service</span></span>  
 <span data-ttu-id="a22ed-120">Projektant uzyskuje dostęp do usługi <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A> przy użyciu <xref:System.Activities.Presentation.WorkflowViewElement.OnModelItemChanged%2A> metody w metodzie.</span><span class="sxs-lookup"><span data-stu-id="a22ed-120">The designer obtains access to the service using the <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A> method in the <xref:System.Activities.Presentation.WorkflowViewElement.OnModelItemChanged%2A> method.</span></span> <span data-ttu-id="a22ed-121">Poniższy fragment kodu pokazuje, jak subskrybować usługę.</span><span class="sxs-lookup"><span data-stu-id="a22ed-121">The following code snippet demonstrates how to subscribe to a service.</span></span>  
  
```csharp  
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
  
## <a name="sharing-data-using-the-items-collection"></a><span data-ttu-id="a22ed-122">Udostępnianie danych przy użyciu kolekcji Elementy</span><span class="sxs-lookup"><span data-stu-id="a22ed-122">Sharing data using the Items collection</span></span>  
 <span data-ttu-id="a22ed-123">Za pomocą Items kolekcji jest podobny do <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A> korzystania z usług kolekcji, z tą różnicą, że jest używany zamiast Publikowania.</span><span class="sxs-lookup"><span data-stu-id="a22ed-123">Using the Items collection is similar to using the Services collection, except that <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A> is used instead of Publish.</span></span> <span data-ttu-id="a22ed-124">Ta kolekcja jest bardziej odpowiednie do udostępniania prostych danych między projektantami i hosta, a nie złożonych funkcji.</span><span class="sxs-lookup"><span data-stu-id="a22ed-124">This collection is more appropriate for sharing simple data between the designers and the host, rather than complex functionality.</span></span>  
  
## <a name="editingcontext-host-items-and-services"></a><span data-ttu-id="a22ed-125">EdytowanieKontekst elementów i usług hosta</span><span class="sxs-lookup"><span data-stu-id="a22ed-125">EditingContext host items and services</span></span>  
 <span data-ttu-id="a22ed-126">.NET Framework zawiera szereg wbudowanych elementów i usług dostępnych za pośrednictwem kontekstu edycji.</span><span class="sxs-lookup"><span data-stu-id="a22ed-126">The .NET Framework provides a number of built-in items and services accessed through the editing context.</span></span>  
  
 <span data-ttu-id="a22ed-127">Elementy:</span><span class="sxs-lookup"><span data-stu-id="a22ed-127">Items:</span></span>  
  
- <span data-ttu-id="a22ed-128"><xref:System.Activities.Presentation.Hosting.AssemblyContextControlItem>: Zarządza listą przywołytych zestawów lokalnych, które będą używane wewnątrz przepływu pracy dla formantów (takich jak edytor wyrażeń).</span><span class="sxs-lookup"><span data-stu-id="a22ed-128"><xref:System.Activities.Presentation.Hosting.AssemblyContextControlItem>: Manages the list of referenced local assemblies that will be used inside the workflow for controls (such as the expression editor).</span></span>  
  
- <span data-ttu-id="a22ed-129"><xref:System.Activities.Presentation.Hosting.ReadOnlyState>: Wskazuje, czy projektant jest w stanie tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="a22ed-129"><xref:System.Activities.Presentation.Hosting.ReadOnlyState>: Indicates whether the designer is in a read-only state.</span></span>  
  
- <span data-ttu-id="a22ed-130"><xref:System.Activities.Presentation.View.Selection>: Definiuje kolekcję aktualnie zaznaczonych obiektów.</span><span class="sxs-lookup"><span data-stu-id="a22ed-130"><xref:System.Activities.Presentation.View.Selection>: Defines the collection of objects that are currently selected.</span></span>  
  
- <span data-ttu-id="a22ed-131"><xref:System.Activities.Presentation.Hosting.WorkflowCommandExtensionItem>:</span><span class="sxs-lookup"><span data-stu-id="a22ed-131"><xref:System.Activities.Presentation.Hosting.WorkflowCommandExtensionItem>:</span></span>  
  
- <span data-ttu-id="a22ed-132"><xref:System.Activities.Presentation.WorkflowFileItem>: Zawiera informacje o pliku, na podstawie których jest oparta bieżąca sesja edycji.</span><span class="sxs-lookup"><span data-stu-id="a22ed-132"><xref:System.Activities.Presentation.WorkflowFileItem>: Provides information on the file that the current editing session is based on.</span></span>  
  
 <span data-ttu-id="a22ed-133">Usługi:</span><span class="sxs-lookup"><span data-stu-id="a22ed-133">Services:</span></span>  
  
- <span data-ttu-id="a22ed-134"><xref:System.Activities.Presentation.Model.AttachedPropertiesService>: Umożliwia dodawanie właściwości do bieżącego <xref:System.Activities.Presentation.Model.AttachedPropertiesService.AddProperty%2A>wystąpienia za pomocą .</span><span class="sxs-lookup"><span data-stu-id="a22ed-134"><xref:System.Activities.Presentation.Model.AttachedPropertiesService>: Allows properties to be added to the current instance, using <xref:System.Activities.Presentation.Model.AttachedPropertiesService.AddProperty%2A>.</span></span>  
  
- <span data-ttu-id="a22ed-135"><xref:System.Activities.Presentation.View.DesignerView>: Umożliwia dostęp do właściwości kanwy projektanta.</span><span class="sxs-lookup"><span data-stu-id="a22ed-135"><xref:System.Activities.Presentation.View.DesignerView>: Allows access to the properties of the designer canvas.</span></span>  
  
- <span data-ttu-id="a22ed-136"><xref:System.Activities.Presentation.IActivityToolboxService>: Umożliwia aktualizowanie zawartości przybornika.</span><span class="sxs-lookup"><span data-stu-id="a22ed-136"><xref:System.Activities.Presentation.IActivityToolboxService>: Allows the contents of the toolbox to be updated.</span></span>  
  
- <span data-ttu-id="a22ed-137"><xref:System.Activities.Presentation.Hosting.ICommandService>: Służy do integrowania poleceń projektanta (takich jak menu kontekstowe) z implementacjami usług świadczonych na zamówienie.</span><span class="sxs-lookup"><span data-stu-id="a22ed-137"><xref:System.Activities.Presentation.Hosting.ICommandService>: Used to integrate designer commands (such as Context Menu) with custom-provided service implementations.</span></span>  
  
- <span data-ttu-id="a22ed-138"><xref:System.Activities.Presentation.Debug.IDesignerDebugView>: Zapewnia funkcjonalność debugera projektanta.</span><span class="sxs-lookup"><span data-stu-id="a22ed-138"><xref:System.Activities.Presentation.Debug.IDesignerDebugView>: Provides functionality for the designer debugger.</span></span>  
  
- <span data-ttu-id="a22ed-139"><xref:System.Activities.Presentation.View.IExpressionEditorService>: Zapewnia dostęp do okna dialogowego Edytora wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="a22ed-139"><xref:System.Activities.Presentation.View.IExpressionEditorService>: Provides access to the Expression Editor dialog.</span></span>  
  
- <span data-ttu-id="a22ed-140"><xref:System.Activities.Presentation.IIntegratedHelpService>: Zapewnia projektantowi zintegrowaną funkcję pomocy.</span><span class="sxs-lookup"><span data-stu-id="a22ed-140"><xref:System.Activities.Presentation.IIntegratedHelpService>: Provides the designer with integrated help functionality.</span></span>  
  
- <span data-ttu-id="a22ed-141"><xref:System.Activities.Presentation.Validation.IValidationErrorService>: Zapewnia dostęp do <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A>błędów sprawdzania poprawności przy użyciu .</span><span class="sxs-lookup"><span data-stu-id="a22ed-141"><xref:System.Activities.Presentation.Validation.IValidationErrorService>: Provides access to validation errors using <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A>.</span></span>  
  
- <span data-ttu-id="a22ed-142"><xref:System.Activities.Presentation.IWorkflowDesignerStorageService>: Zapewnia wewnętrzną usługę do przechowywania i pobierania danych.</span><span class="sxs-lookup"><span data-stu-id="a22ed-142"><xref:System.Activities.Presentation.IWorkflowDesignerStorageService>: Provides an internal service to store and retrieve data.</span></span> <span data-ttu-id="a22ed-143">Ta usługa jest używana wewnętrznie przez platformę .NET Framework i nie jest przeznaczona do użytku zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="a22ed-143">This service is used internally by the .NET Framework, and is not intended for external use.</span></span>  
  
- <span data-ttu-id="a22ed-144"><xref:System.Activities.Presentation.IXamlLoadErrorService>: Zapewnia dostęp do kolekcji błędów obciążenia XAML przy użyciu <xref:System.Activities.Presentation.IXamlLoadErrorService.ShowXamlLoadErrors%2A>.</span><span class="sxs-lookup"><span data-stu-id="a22ed-144"><xref:System.Activities.Presentation.IXamlLoadErrorService>: Provides access to the XAML load error collection using <xref:System.Activities.Presentation.IXamlLoadErrorService.ShowXamlLoadErrors%2A>.</span></span>  
  
- <span data-ttu-id="a22ed-145"><xref:System.Activities.Presentation.Services.ModelService>: Używany przez projektanta do interakcji z modelem edytowanego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="a22ed-145"><xref:System.Activities.Presentation.Services.ModelService>: Used by the designer to interact with the model of the workflow being edited.</span></span>  
  
- <span data-ttu-id="a22ed-146"><xref:System.Activities.Presentation.Model.ModelTreeManager>: Zapewnia dostęp do katalogu głównego <xref:System.Activities.Presentation.Model.ModelItem.Root%2A>drzewa elementów modelu przy użyciu .</span><span class="sxs-lookup"><span data-stu-id="a22ed-146"><xref:System.Activities.Presentation.Model.ModelTreeManager>: Provides access to the root of the model item tree using <xref:System.Activities.Presentation.Model.ModelItem.Root%2A>.</span></span>  
  
- <span data-ttu-id="a22ed-147"><xref:System.Activities.Presentation.UndoEngine>: Zapewnia funkcje cofania i ponawiania.</span><span class="sxs-lookup"><span data-stu-id="a22ed-147"><xref:System.Activities.Presentation.UndoEngine>: Provides undo and redo functionality.</span></span>  
  
- <span data-ttu-id="a22ed-148"><xref:System.Activities.Presentation.Services.ViewService>: Mapowanie elementów wizualnych do podstawowych elementów modelu.</span><span class="sxs-lookup"><span data-stu-id="a22ed-148"><xref:System.Activities.Presentation.Services.ViewService>: Maps visual elements to underlying model items.</span></span>  
  
- <span data-ttu-id="a22ed-149"><xref:System.Activities.Presentation.View.ViewStateService>: Przechowuje stany widoku dla elementów modelu.</span><span class="sxs-lookup"><span data-stu-id="a22ed-149"><xref:System.Activities.Presentation.View.ViewStateService>: Stores view states for model items.</span></span>  
  
- <span data-ttu-id="a22ed-150"><xref:System.Activities.Presentation.View.VirtualizedContainerService>: Służy do dostosowywania zachowania interfejsu użytkownika kontenera wirtualnego.</span><span class="sxs-lookup"><span data-stu-id="a22ed-150"><xref:System.Activities.Presentation.View.VirtualizedContainerService>: Used to customize the virtual container UI behavior.</span></span>  
  
- <span data-ttu-id="a22ed-151"><xref:System.Activities.Presentation.Hosting.WindowHelperService>: Służy do rejestrowania i wyrejestrowania delegatów do powiadomień o zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="a22ed-151"><xref:System.Activities.Presentation.Hosting.WindowHelperService>: Used to register and unregister delegates for event notifications.</span></span> <span data-ttu-id="a22ed-152">Umożliwia również ustawienie właściciela okna.</span><span class="sxs-lookup"><span data-stu-id="a22ed-152">Also allows a window owner to be set.</span></span>
