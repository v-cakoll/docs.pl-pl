---
title: Używanie kontekstu edycyjnego ModelItem
ms.date: 03/30/2017
ms.assetid: 7f9f1ea5-0147-4079-8eca-be94f00d3aa1
ms.openlocfilehash: a47cb53e50d221c0ae07cf0841688fe4f8ced7d4
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988923"
---
# <a name="using-the-modelitem-editing-context"></a><span data-ttu-id="13b33-102">Używanie kontekstu edycyjnego ModelItem</span><span class="sxs-lookup"><span data-stu-id="13b33-102">Using the ModelItem Editing Context</span></span>
<span data-ttu-id="13b33-103">Kontekst <xref:System.Activities.Presentation.Model.ModelItem> edycji jest obiektem, którego aplikacja hosta używa do komunikowania się z projektantem.</span><span class="sxs-lookup"><span data-stu-id="13b33-103">The <xref:System.Activities.Presentation.Model.ModelItem> editing context is the object that the host application uses to communicate with the designer.</span></span> <span data-ttu-id="13b33-104"><xref:System.Activities.Presentation.EditingContext>uwidacznia dwie metody <xref:System.Activities.Presentation.EditingContext.Items%2A> i <xref:System.Activities.Presentation.EditingContext.Services%2A>, które mogą być używane</span><span class="sxs-lookup"><span data-stu-id="13b33-104"><xref:System.Activities.Presentation.EditingContext> exposes two methods, <xref:System.Activities.Presentation.EditingContext.Items%2A> and <xref:System.Activities.Presentation.EditingContext.Services%2A>, which can be used</span></span>  
  
## <a name="the-items-collection"></a><span data-ttu-id="13b33-105">Kolekcja elementów</span><span class="sxs-lookup"><span data-stu-id="13b33-105">The Items collection</span></span>  
 <span data-ttu-id="13b33-106"><xref:System.Activities.Presentation.EditingContext.Items%2A> Kolekcja służy do uzyskiwania dostępu do danych, które są udostępniane między hostem a projektantem, lub danymi, które są dostępne dla wszystkich projektantów.</span><span class="sxs-lookup"><span data-stu-id="13b33-106">The <xref:System.Activities.Presentation.EditingContext.Items%2A> collection is used to access data that is shared between the host and the designer, or data that is available to all designers.</span></span> <span data-ttu-id="13b33-107">Ta kolekcja ma następujące możliwości, do których można uzyskać <xref:System.Activities.Presentation.ContextItemManager> dostęp za pośrednictwem klasy:</span><span class="sxs-lookup"><span data-stu-id="13b33-107">This collection has the following capabilities, accessed via the <xref:System.Activities.Presentation.ContextItemManager> class:</span></span>  
  
1. <xref:System.Activities.Presentation.ContextItemManager.GetValue%2A>  
  
2. <xref:System.Activities.Presentation.ContextItemManager.Subscribe%2A>  
  
3. <xref:System.Activities.Presentation.ContextItemManager.Unsubscribe%2A>  
  
4. <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A>  
  
## <a name="the-services-collection"></a><span data-ttu-id="13b33-108">Kolekcja usług</span><span class="sxs-lookup"><span data-stu-id="13b33-108">The Services collection</span></span>  
 <span data-ttu-id="13b33-109"><xref:System.Activities.Presentation.EditingContext.Services%2A> Kolekcja służy do uzyskiwania dostępu do usług, które są używane przez projektanta do współdziałania z hostem lub usług, których używają wszyscy projektanci.</span><span class="sxs-lookup"><span data-stu-id="13b33-109">The <xref:System.Activities.Presentation.EditingContext.Services%2A> collection is used to access services that the designer uses to interact with the host, or services that all designers use.</span></span> <span data-ttu-id="13b33-110">Ta kolekcja zawiera następujące metody:</span><span class="sxs-lookup"><span data-stu-id="13b33-110">This collection has the following methods of note:</span></span>  
  
1. <xref:System.Activities.Presentation.ServiceManager.Publish%2A>  
  
2. <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A>  
  
3. <xref:System.Activities.Presentation.ServiceManager.Unsubscribe%2A>  
  
4. <xref:System.Activities.Presentation.ServiceManager.GetService%2A>  
  
## <a name="assigning-a-designer-an-activity"></a><span data-ttu-id="13b33-111">Przypisywanie działania projektanta</span><span class="sxs-lookup"><span data-stu-id="13b33-111">Assigning a designer an activity</span></span>  
 <span data-ttu-id="13b33-112">Aby określić projektanta, który jest używany przez działanie, używany jest atrybut projektanta.</span><span class="sxs-lookup"><span data-stu-id="13b33-112">To specify which designer an activity uses, the Designer attribute is used.</span></span>  
  
```csharp  
[Designer(typeof(MyClassDesigner))]  
public sealed class MyClass : CodeActivity  
{
}
```  
  
## <a name="creating-a-service"></a><span data-ttu-id="13b33-113">Tworzenie usługi</span><span class="sxs-lookup"><span data-stu-id="13b33-113">Creating a service</span></span>  
 <span data-ttu-id="13b33-114">Aby utworzyć usługę, która służy jako kanał informacji między projektantem a hostem, należy utworzyć interfejs i implementację.</span><span class="sxs-lookup"><span data-stu-id="13b33-114">To create a service that serves as a conduit of information between the designer and the host, an interface and an implementation must be created.</span></span> <span data-ttu-id="13b33-115">Interfejs jest używany przez <xref:System.Activities.Presentation.ServiceManager.Publish%2A> metodę do definiowania członków usługi, a implementacja zawiera logikę dla usługi.</span><span class="sxs-lookup"><span data-stu-id="13b33-115">The interface is used by the <xref:System.Activities.Presentation.ServiceManager.Publish%2A> method to define the members of the service, and the implementation contains the logic for the service.</span></span> <span data-ttu-id="13b33-116">W poniższym przykładzie kodu jest tworzony interfejs usługi i implementacja.</span><span class="sxs-lookup"><span data-stu-id="13b33-116">In the following code example, a service interface and implementation are created.</span></span>  
  
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
  
## <a name="publishing-a-service"></a><span data-ttu-id="13b33-117">Publikowanie usługi</span><span class="sxs-lookup"><span data-stu-id="13b33-117">Publishing a service</span></span>  
 <span data-ttu-id="13b33-118">Aby projektant mógł korzystać z usługi, musi zostać najpierw Opublikowany przez hosta przy użyciu <xref:System.Activities.Presentation.ServiceManager.Publish%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="13b33-118">For a designer to consume a service, it must first be published by the host using the <xref:System.Activities.Presentation.ServiceManager.Publish%2A> method.</span></span>  
  
```csharp  
this.Context.Services.Publish<IMyService>(new MyServiceImpl);  
```  
  
## <a name="subscribing-to-a-service"></a><span data-ttu-id="13b33-119">Subskrybowanie usługi</span><span class="sxs-lookup"><span data-stu-id="13b33-119">Subscribing to a service</span></span>  
 <span data-ttu-id="13b33-120">Projektant uzyskuje dostęp do usługi przy użyciu <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A> metody <xref:System.Activities.Presentation.WorkflowViewElement.OnModelItemChanged%2A> w metodzie.</span><span class="sxs-lookup"><span data-stu-id="13b33-120">The designer obtains access to the service using the <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A> method in the <xref:System.Activities.Presentation.WorkflowViewElement.OnModelItemChanged%2A> method.</span></span> <span data-ttu-id="13b33-121">Poniższy fragment kodu przedstawia sposób subskrybowania usługi.</span><span class="sxs-lookup"><span data-stu-id="13b33-121">The following code snippet demonstrates how to subscribe to a service.</span></span>  
  
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
  
## <a name="sharing-data-using-the-items-collection"></a><span data-ttu-id="13b33-122">Udostępnianie danych przy użyciu kolekcji Items</span><span class="sxs-lookup"><span data-stu-id="13b33-122">Sharing data using the Items collection</span></span>  
 <span data-ttu-id="13b33-123">Używanie kolekcji Items jest podobne do korzystania z kolekcji usług, z tą <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A> różnicą, że jest używana zamiast publikowania.</span><span class="sxs-lookup"><span data-stu-id="13b33-123">Using the Items collection is similar to using the Services collection, except that <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A> is used instead of Publish.</span></span> <span data-ttu-id="13b33-124">Ta kolekcja jest bardziej odpowiednia do udostępniania prostych danych między projektantami i hostem, a nie złożonymi funkcjami.</span><span class="sxs-lookup"><span data-stu-id="13b33-124">This collection is more appropriate for sharing simple data between the designers and the host, rather than complex functionality.</span></span>  
  
## <a name="editingcontext-host-items-and-services"></a><span data-ttu-id="13b33-125">EditingContext elementy i usługi hosta</span><span class="sxs-lookup"><span data-stu-id="13b33-125">EditingContext host items and services</span></span>  
 <span data-ttu-id="13b33-126">.NET Framework zawiera wiele wbudowanych elementów i usług dostępnych za pomocą kontekstu edycji.</span><span class="sxs-lookup"><span data-stu-id="13b33-126">The .NET Framework provides a number of built-in items and services accessed through the editing context.</span></span>  
  
 <span data-ttu-id="13b33-127">Produktów</span><span class="sxs-lookup"><span data-stu-id="13b33-127">Items:</span></span>  
  
- <span data-ttu-id="13b33-128"><xref:System.Activities.Presentation.Hosting.AssemblyContextControlItem>: Zarządza listą przywoływanych zestawów lokalnych, które będą używane w przepływie pracy dla kontrolek (takich jak Edytor wyrażeń).</span><span class="sxs-lookup"><span data-stu-id="13b33-128"><xref:System.Activities.Presentation.Hosting.AssemblyContextControlItem>: Manages the list of referenced local assemblies that will be used inside the workflow for controls (such as the expression editor).</span></span>  
  
- <span data-ttu-id="13b33-129"><xref:System.Activities.Presentation.Hosting.ReadOnlyState>: Wskazuje, czy projektant jest w stanie tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="13b33-129"><xref:System.Activities.Presentation.Hosting.ReadOnlyState>: Indicates whether the designer is in a read-only state.</span></span>  
  
- <span data-ttu-id="13b33-130"><xref:System.Activities.Presentation.View.Selection>: Definiuje kolekcję obiektów, które są obecnie zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="13b33-130"><xref:System.Activities.Presentation.View.Selection>: Defines the collection of objects that are currently selected.</span></span>  
  
- <span data-ttu-id="13b33-131"><xref:System.Activities.Presentation.Hosting.WorkflowCommandExtensionItem>:</span><span class="sxs-lookup"><span data-stu-id="13b33-131"><xref:System.Activities.Presentation.Hosting.WorkflowCommandExtensionItem>:</span></span>  
  
- <span data-ttu-id="13b33-132"><xref:System.Activities.Presentation.WorkflowFileItem>: Zawiera informacje dotyczące pliku, na którym jest oparta bieżąca sesja edycji.</span><span class="sxs-lookup"><span data-stu-id="13b33-132"><xref:System.Activities.Presentation.WorkflowFileItem>: Provides information on the file that the current editing session is based on.</span></span>  
  
 <span data-ttu-id="13b33-133">Services</span><span class="sxs-lookup"><span data-stu-id="13b33-133">Services:</span></span>  
  
- <span data-ttu-id="13b33-134"><xref:System.Activities.Presentation.Model.AttachedPropertiesService>: Zezwala na dodawanie właściwości do bieżącego wystąpienia przy użyciu <xref:System.Activities.Presentation.Model.AttachedPropertiesService.AddProperty%2A>.</span><span class="sxs-lookup"><span data-stu-id="13b33-134"><xref:System.Activities.Presentation.Model.AttachedPropertiesService>: Allows properties to be added to the current instance, using <xref:System.Activities.Presentation.Model.AttachedPropertiesService.AddProperty%2A>.</span></span>  
  
- <span data-ttu-id="13b33-135"><xref:System.Activities.Presentation.View.DesignerView>: Zezwala na dostęp do właściwości kanwy projektanta.</span><span class="sxs-lookup"><span data-stu-id="13b33-135"><xref:System.Activities.Presentation.View.DesignerView>: Allows access to the properties of the designer canvas.</span></span>  
  
- <span data-ttu-id="13b33-136"><xref:System.Activities.Presentation.IActivityToolboxService>: Zezwala na aktualizowanie zawartości przybornika.</span><span class="sxs-lookup"><span data-stu-id="13b33-136"><xref:System.Activities.Presentation.IActivityToolboxService>: Allows the contents of the toolbox to be updated.</span></span>  
  
- <span data-ttu-id="13b33-137"><xref:System.Activities.Presentation.Hosting.ICommandService>: Służy do integrowania poleceń projektanta (takich jak menu kontekstowe) z implementacjami usług udostępnianymi niestandardowo.</span><span class="sxs-lookup"><span data-stu-id="13b33-137"><xref:System.Activities.Presentation.Hosting.ICommandService>: Used to integrate designer commands (such as Context Menu) with custom-provided service implementations.</span></span>  
  
- <span data-ttu-id="13b33-138"><xref:System.Activities.Presentation.Debug.IDesignerDebugView>: Oferuje funkcje debugera projektanta.</span><span class="sxs-lookup"><span data-stu-id="13b33-138"><xref:System.Activities.Presentation.Debug.IDesignerDebugView>: Provides functionality for the designer debugger.</span></span>  
  
- <span data-ttu-id="13b33-139"><xref:System.Activities.Presentation.View.IExpressionEditorService>: Zapewnia dostęp do okna dialogowego edytora wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="13b33-139"><xref:System.Activities.Presentation.View.IExpressionEditorService>: Provides access to the Expression Editor dialog.</span></span>  
  
- <span data-ttu-id="13b33-140"><xref:System.Activities.Presentation.IIntegratedHelpService>: Oferuje projektanta z zintegrowaną funkcją pomocy.</span><span class="sxs-lookup"><span data-stu-id="13b33-140"><xref:System.Activities.Presentation.IIntegratedHelpService>: Provides the designer with integrated help functionality.</span></span>  
  
- <span data-ttu-id="13b33-141"><xref:System.Activities.Presentation.Validation.IValidationErrorService>: Zapewnia dostęp do błędów walidacji <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A>przy użyciu.</span><span class="sxs-lookup"><span data-stu-id="13b33-141"><xref:System.Activities.Presentation.Validation.IValidationErrorService>: Provides access to validation errors using <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A>.</span></span>  
  
- <span data-ttu-id="13b33-142"><xref:System.Activities.Presentation.IWorkflowDesignerStorageService>: Zapewnia usługę wewnętrzną do przechowywania i pobierania danych.</span><span class="sxs-lookup"><span data-stu-id="13b33-142"><xref:System.Activities.Presentation.IWorkflowDesignerStorageService>: Provides an internal service to store and retrieve data.</span></span> <span data-ttu-id="13b33-143">Ta usługa jest używana wewnętrznie przez .NET Framework i nie jest przeznaczona do użytku zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="13b33-143">This service is used internally by the .NET Framework, and is not intended for external use.</span></span>  
  
- <span data-ttu-id="13b33-144"><xref:System.Activities.Presentation.IXamlLoadErrorService>: Zapewnia dostęp do kolekcji błędów ładowania XAML przy użyciu <xref:System.Activities.Presentation.IXamlLoadErrorService.ShowXamlLoadErrors%2A>.</span><span class="sxs-lookup"><span data-stu-id="13b33-144"><xref:System.Activities.Presentation.IXamlLoadErrorService>: Provides access to the XAML load error collection using <xref:System.Activities.Presentation.IXamlLoadErrorService.ShowXamlLoadErrors%2A>.</span></span>  
  
- <span data-ttu-id="13b33-145"><xref:System.Activities.Presentation.Services.ModelService>: Używany przez projektanta do współpracy z modelem edytowanego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="13b33-145"><xref:System.Activities.Presentation.Services.ModelService>: Used by the designer to interact with the model of the workflow being edited.</span></span>  
  
- <span data-ttu-id="13b33-146"><xref:System.Activities.Presentation.Model.ModelTreeManager>: Zapewnia dostęp do katalogu głównego drzewa elementów modelu przy użyciu <xref:System.Activities.Presentation.Model.ModelItem.Root%2A>.</span><span class="sxs-lookup"><span data-stu-id="13b33-146"><xref:System.Activities.Presentation.Model.ModelTreeManager>: Provides access to the root of the model item tree using <xref:System.Activities.Presentation.Model.ModelItem.Root%2A>.</span></span>  
  
- <span data-ttu-id="13b33-147"><xref:System.Activities.Presentation.UndoEngine>: Zapewnia funkcję cofania i ponawiania.</span><span class="sxs-lookup"><span data-stu-id="13b33-147"><xref:System.Activities.Presentation.UndoEngine>: Provides undo and redo functionality.</span></span>  
  
- <span data-ttu-id="13b33-148"><xref:System.Activities.Presentation.Services.ViewService>: Mapuje elementy wizualne na bazowe elementy modelu.</span><span class="sxs-lookup"><span data-stu-id="13b33-148"><xref:System.Activities.Presentation.Services.ViewService>: Maps visual elements to underlying model items.</span></span>  
  
- <span data-ttu-id="13b33-149"><xref:System.Activities.Presentation.View.ViewStateService>: Przechowuje Stany widoku dla elementów modelu.</span><span class="sxs-lookup"><span data-stu-id="13b33-149"><xref:System.Activities.Presentation.View.ViewStateService>: Stores view states for model items.</span></span>  
  
- <span data-ttu-id="13b33-150"><xref:System.Activities.Presentation.View.VirtualizedContainerService>: Służy do dostosowywania zachowania interfejsu użytkownika kontenera wirtualnego.</span><span class="sxs-lookup"><span data-stu-id="13b33-150"><xref:System.Activities.Presentation.View.VirtualizedContainerService>: Used to customize the virtual container UI behavior.</span></span>  
  
- <span data-ttu-id="13b33-151"><xref:System.Activities.Presentation.Hosting.WindowHelperService>: Służy do rejestrowania i wyrejestrowania delegatów dla powiadomień o zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="13b33-151"><xref:System.Activities.Presentation.Hosting.WindowHelperService>: Used to register and unregister delegates for event notifications.</span></span> <span data-ttu-id="13b33-152">Umożliwia również ustawienie właściciela okna.</span><span class="sxs-lookup"><span data-stu-id="13b33-152">Also allows a window owner to be set.</span></span>
