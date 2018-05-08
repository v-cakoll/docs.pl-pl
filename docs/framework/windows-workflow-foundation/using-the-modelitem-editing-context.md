---
title: Przy użyciu ModelItem edycji kontekstu
ms.date: 03/30/2017
ms.assetid: 7f9f1ea5-0147-4079-8eca-be94f00d3aa1
ms.openlocfilehash: 17334b5571148e494067683bdf96ebc4be4ea995
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="using-the-modelitem-editing-context"></a>Przy użyciu ModelItem edycji kontekstu
<xref:System.Activities.Presentation.Model.ModelItem> Edycji kontekstu jest obiekt, który aplikacja hosta używa do komunikacji przy użyciu projektanta. <xref:System.Activities.Presentation.EditingContext> udostępnia dwie metody <xref:System.Activities.Presentation.EditingContext.Items%2A> i <xref:System.Activities.Presentation.EditingContext.Services%2A>, której można użyć  
  
## <a name="the-items-collection"></a>Kolekcja elementów  
 <xref:System.Activities.Presentation.EditingContext.Items%2A> Kolekcji umożliwia dostęp do danych, które są współużytkowane przez hosta i Projektant lub danych, która jest dostępna dla wszystkich projektantów. Ta kolekcja ma następujące możliwości dostępne za pośrednictwem <xref:System.Activities.Presentation.ContextItemManager> klasy:  
  
1.  <xref:System.Activities.Presentation.ContextItemManager.GetValue%2A>  
  
2.  <xref:System.Activities.Presentation.ContextItemManager.Subscribe%2A>  
  
3.  <xref:System.Activities.Presentation.ContextItemManager.Unsubscribe%2A>  
  
4.  <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A>  
  
## <a name="the-services-collection"></a>Kolekcja usług  
 <xref:System.Activities.Presentation.EditingContext.Services%2A> Umożliwia dostęp do usług używanych w projektancie do interakcji z hostem lub usługi, które wszystkie projektanci używali kolekcji. Ta kolekcja ma Uwaga z następujących metod:  
  
1.  <xref:System.Activities.Presentation.ServiceManager.Publish%2A>  
  
2.  <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A>  
  
3.  <xref:System.Activities.Presentation.ServiceManager.Unsubscribe%2A>  
  
4.  <xref:System.Activities.Presentation.ServiceManager.GetService%2A>  
  
## <a name="assigning-a-designer-an-activity"></a>Przypisywanie projektanta działania  
 Aby określić, które projektanta używa działania, atrybut projektanta jest używany.  
  
```  
[Designer(typeof(MyClassDesigner))]  
public sealed class MyClass : CodeActivity  
{  
```  
  
## <a name="creating-a-service"></a>Tworzenie usługi  
 Aby utworzyć usługę, która służy jako kanał informacji między projektanta i hosta, należy utworzyć interfejs i implementacji. Ten interfejs jest używany przez <xref:System.Activities.Presentation.ServiceManager.Publish%2A> metodę, aby zdefiniować elementów członkowskich usługi i implementację zawiera logikę dla usługi. W poniższym przykładzie kodu interfejsu usługi i implementacji są tworzone.  
  
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
  
## <a name="publishing-a-service"></a>Usługa publikowania  
 Projektanta korzystać z usługi, musi najpierw być opublikowane przez hosta przy użyciu <xref:System.Activities.Presentation.ServiceManager.Publish%2A> metody.  
  
```  
this.Context.Services.Publish<IMyService>(new MyServiceImpl);  
```  
  
## <a name="subscribing-to-a-service"></a>Subskrybowanie usługi  
 Projektant uzyskuje dostęp do usługi przy użyciu <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A> metoda <xref:System.Activities.Presentation.WorkflowViewElement.OnModelItemChanged%2A> metody. Poniższy fragment kodu przedstawia sposób subskrybowania usługi.  
  
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
  
## <a name="sharing-data-using-the-items-collection"></a>Udostępnianie danych za pomocą kolekcji elementów  
 Za pomocą kolekcji elementów jest podobny do sposobu używania kolekcji usług, z wyjątkiem <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A> jest używana zamiast funkcji publikowania. Ta kolekcja jest bardziej odpowiednie dla udostępniania proste danych między projektantów i hosta, a nie złożonych funkcji.  
  
## <a name="editingcontext-host-items-and-services"></a>Obiekty hosta EditingContext i usługi  
 .Net Framework udostępnia szereg wbudowanych elementów i usługi dostępne za pośrednictwem Kontekst edycyjny.  
  
 Elementy:  
  
-   <xref:System.Activities.Presentation.Hosting.AssemblyContextControlItem>: Służą do zarządzania listą zestawów występujących w odwołaniach lokalne, które będą używane w przepływie pracy (takie jak Edytor wyrażeń).  
  
-   <xref:System.Activities.Presentation.Hosting.ReadOnlyState>: Wskazuje, czy projektant jest w stanie tylko do odczytu.  
  
-   <xref:System.Activities.Presentation.View.Selection>: Określa kolekcję obiektów, które są aktualnie wybrane.  
  
-   <xref:System.Activities.Presentation.Hosting.WorkflowCommandExtensionItem>:  
  
-   <xref:System.Activities.Presentation.WorkflowFileItem>: Zawiera informacje o pliku, na podstawie bieżącej sesji edytowania.  
  
 Usługi:  
  
-   <xref:System.Activities.Presentation.Model.AttachedPropertiesService>: Umożliwia właściwości mają zostać dodane do bieżącego wystąpienia przy użyciu <xref:System.Activities.Presentation.Model.AttachedPropertiesService.AddProperty%2A>.  
  
-   <xref:System.Activities.Presentation.View.DesignerView>: Zezwala na dostęp do właściwości obszaru projektowania.  
  
-   <xref:System.Activities.Presentation.IActivityToolboxService>: Umożliwia zawartości przybornika do zaktualizowania.  
  
-   <xref:System.Activities.Presentation.Hosting.ICommandService>: Używany do integrowania projektanta poleceń (np. Menu kontekstowe) z implementacji usługi dostarczane przez niestandardowe.  
  
-   <xref:System.Activities.Presentation.Debug.IDesignerDebugView>: Zawiera funkcje projektanta debugera.  
  
-   <xref:System.Activities.Presentation.View.IExpressionEditorService>: Zapewnia dostęp do okna dialogowego edytora wyrażeń.  
  
-   <xref:System.Activities.Presentation.IIntegratedHelpService>: Zawiera projektanta z funkcji zintegrowanego pomocy.  
  
-   <xref:System.Activities.Presentation.Validation.IValidationErrorService>: Zapewnia dostęp do błędy sprawdzania poprawności przy użyciu <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A>.  
  
-   <xref:System.Activities.Presentation.IWorkflowDesignerStorageService>: Zawiera wewnętrzny usługi do przechowywania i pobierania danych. Ta usługa jest używana wewnętrznie przez programu .net Framework i nie jest przeznaczona do użytku zewnętrznego.  
  
-   <xref:System.Activities.Presentation.IXamlLoadErrorService>: Zapewnia dostęp do pliku XAML obciążenia Błąd kolekcji przy użyciu <xref:System.Activities.Presentation.IXamlLoadErrorService.ShowXamlLoadErrors%2A>.  
  
-   <xref:System.Activities.Presentation.Services.ModelService>: Służy do interakcji z modelu przepływu pracy edytowany przez projektanta.  
  
-   <xref:System.Activities.Presentation.Model.ModelTreeManager>: Zapewnia dostęp do katalogu głównego model element drzewa przy użyciu <xref:System.Activities.Presentation.Model.ModelItem.Root%2A>.  
  
-   <xref:System.Activities.Presentation.UndoEngine>: Zawiera cofania i ponawiania funkcji.  
  
-   <xref:System.Activities.Presentation.Services.ViewService>: Mapuje elementy wizualne na podstawowe elementy modelu.  
  
-   <xref:System.Activities.Presentation.View.ViewStateService>: Magazyny wyświetlanie stanów elementów modelu.  
  
-   <xref:System.Activities.Presentation.View.VirtualizedContainerService>: Pozwala dostosować zachowanie interfejsu użytkownika wirtualnego kontenera.  
  
-   <xref:System.Activities.Presentation.Hosting.WindowHelperService>: Używany do rejestrowania i wyrejestrowania delegatów powiadomień o zdarzeniach. Umożliwia właścicielowi okna można ustawić.
