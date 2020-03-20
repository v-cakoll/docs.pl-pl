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
# <a name="using-the-modelitem-editing-context"></a>Używanie kontekstu edycyjnego ModelItem
Kontekst <xref:System.Activities.Presentation.Model.ModelItem> edycji jest obiektem używanym przez aplikację hosta do komunikowania się z projektantem. <xref:System.Activities.Presentation.EditingContext>ujawnia dwie <xref:System.Activities.Presentation.EditingContext.Items%2A> metody, <xref:System.Activities.Presentation.EditingContext.Services%2A>i , które mogą być stosowane  
  
## <a name="the-items-collection"></a>Kolekcja Items  
 Kolekcja <xref:System.Activities.Presentation.EditingContext.Items%2A> jest używana do uzyskiwania dostępu do danych, które są współużytkowane przez hosta i projektanta lub danych, które są dostępne dla wszystkich projektantów. Ta kolekcja ma następujące możliwości, dostępne <xref:System.Activities.Presentation.ContextItemManager> za pośrednictwem klasy:  
  
1. <xref:System.Activities.Presentation.ContextItemManager.GetValue%2A>  
  
2. <xref:System.Activities.Presentation.ContextItemManager.Subscribe%2A>  
  
3. <xref:System.Activities.Presentation.ContextItemManager.Unsubscribe%2A>  
  
4. <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A>  
  
## <a name="the-services-collection"></a>Kolekcja Usług  
 Kolekcja <xref:System.Activities.Presentation.EditingContext.Services%2A> jest używana do uzyskiwania dostępu do usług używanych przez projektanta do interakcji z hostem lub usług, których używają wszyscy projektanci. Ta kolekcja ma następujące metody uwagi:  
  
1. <xref:System.Activities.Presentation.ServiceManager.Publish%2A>  
  
2. <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A>  
  
3. <xref:System.Activities.Presentation.ServiceManager.Unsubscribe%2A>  
  
4. <xref:System.Activities.Presentation.ServiceManager.GetService%2A>  
  
## <a name="assigning-a-designer-an-activity"></a>Przypisywanie projektantowi działania  
 Aby określić, który projektant używa działania, używany jest atrybut Projektant.  
  
```csharp  
[Designer(typeof(MyClassDesigner))]  
public sealed class MyClass : CodeActivity  
{
}
```  
  
## <a name="creating-a-service"></a>Tworzenie usługi  
 Aby utworzyć usługę, która służy jako kanał informacji między projektantem a hostem, należy utworzyć interfejs i implementację. Interfejs jest używany <xref:System.Activities.Presentation.ServiceManager.Publish%2A> przez metodę do definiowania elementów członkowskich usługi, a implementacja zawiera logikę usługi. W poniższym przykładzie kodu tworzony jest interfejs i implementacja usługi.  
  
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
  
## <a name="publishing-a-service"></a>Publikowanie usługi  
 Dla projektanta do korzystania z usługi, musi najpierw zostać <xref:System.Activities.Presentation.ServiceManager.Publish%2A> opublikowane przez hosta przy użyciu metody.  
  
```csharp  
this.Context.Services.Publish<IMyService>(new MyServiceImpl);  
```  
  
## <a name="subscribing-to-a-service"></a>Subskrybowanie usługi  
 Projektant uzyskuje dostęp do usługi <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A> przy użyciu <xref:System.Activities.Presentation.WorkflowViewElement.OnModelItemChanged%2A> metody w metodzie. Poniższy fragment kodu pokazuje, jak subskrybować usługę.  
  
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
  
## <a name="sharing-data-using-the-items-collection"></a>Udostępnianie danych przy użyciu kolekcji Elementy  
 Za pomocą Items kolekcji jest podobny do <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A> korzystania z usług kolekcji, z tą różnicą, że jest używany zamiast Publikowania. Ta kolekcja jest bardziej odpowiednie do udostępniania prostych danych między projektantami i hosta, a nie złożonych funkcji.  
  
## <a name="editingcontext-host-items-and-services"></a>EdytowanieKontekst elementów i usług hosta  
 .NET Framework zawiera szereg wbudowanych elementów i usług dostępnych za pośrednictwem kontekstu edycji.  
  
 Elementy:  
  
- <xref:System.Activities.Presentation.Hosting.AssemblyContextControlItem>: Zarządza listą przywołytych zestawów lokalnych, które będą używane wewnątrz przepływu pracy dla formantów (takich jak edytor wyrażeń).  
  
- <xref:System.Activities.Presentation.Hosting.ReadOnlyState>: Wskazuje, czy projektant jest w stanie tylko do odczytu.  
  
- <xref:System.Activities.Presentation.View.Selection>: Definiuje kolekcję aktualnie zaznaczonych obiektów.  
  
- <xref:System.Activities.Presentation.Hosting.WorkflowCommandExtensionItem>:  
  
- <xref:System.Activities.Presentation.WorkflowFileItem>: Zawiera informacje o pliku, na podstawie których jest oparta bieżąca sesja edycji.  
  
 Usługi:  
  
- <xref:System.Activities.Presentation.Model.AttachedPropertiesService>: Umożliwia dodawanie właściwości do bieżącego <xref:System.Activities.Presentation.Model.AttachedPropertiesService.AddProperty%2A>wystąpienia za pomocą .  
  
- <xref:System.Activities.Presentation.View.DesignerView>: Umożliwia dostęp do właściwości kanwy projektanta.  
  
- <xref:System.Activities.Presentation.IActivityToolboxService>: Umożliwia aktualizowanie zawartości przybornika.  
  
- <xref:System.Activities.Presentation.Hosting.ICommandService>: Służy do integrowania poleceń projektanta (takich jak menu kontekstowe) z implementacjami usług świadczonych na zamówienie.  
  
- <xref:System.Activities.Presentation.Debug.IDesignerDebugView>: Zapewnia funkcjonalność debugera projektanta.  
  
- <xref:System.Activities.Presentation.View.IExpressionEditorService>: Zapewnia dostęp do okna dialogowego Edytora wyrażeń.  
  
- <xref:System.Activities.Presentation.IIntegratedHelpService>: Zapewnia projektantowi zintegrowaną funkcję pomocy.  
  
- <xref:System.Activities.Presentation.Validation.IValidationErrorService>: Zapewnia dostęp do <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A>błędów sprawdzania poprawności przy użyciu .  
  
- <xref:System.Activities.Presentation.IWorkflowDesignerStorageService>: Zapewnia wewnętrzną usługę do przechowywania i pobierania danych. Ta usługa jest używana wewnętrznie przez platformę .NET Framework i nie jest przeznaczona do użytku zewnętrznego.  
  
- <xref:System.Activities.Presentation.IXamlLoadErrorService>: Zapewnia dostęp do kolekcji błędów obciążenia XAML przy użyciu <xref:System.Activities.Presentation.IXamlLoadErrorService.ShowXamlLoadErrors%2A>.  
  
- <xref:System.Activities.Presentation.Services.ModelService>: Używany przez projektanta do interakcji z modelem edytowanego przepływu pracy.  
  
- <xref:System.Activities.Presentation.Model.ModelTreeManager>: Zapewnia dostęp do katalogu głównego <xref:System.Activities.Presentation.Model.ModelItem.Root%2A>drzewa elementów modelu przy użyciu .  
  
- <xref:System.Activities.Presentation.UndoEngine>: Zapewnia funkcje cofania i ponawiania.  
  
- <xref:System.Activities.Presentation.Services.ViewService>: Mapowanie elementów wizualnych do podstawowych elementów modelu.  
  
- <xref:System.Activities.Presentation.View.ViewStateService>: Przechowuje stany widoku dla elementów modelu.  
  
- <xref:System.Activities.Presentation.View.VirtualizedContainerService>: Służy do dostosowywania zachowania interfejsu użytkownika kontenera wirtualnego.  
  
- <xref:System.Activities.Presentation.Hosting.WindowHelperService>: Służy do rejestrowania i wyrejestrowania delegatów do powiadomień o zdarzeniach. Umożliwia również ustawienie właściciela okna.
