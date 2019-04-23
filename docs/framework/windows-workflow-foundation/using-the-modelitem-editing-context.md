---
title: Używanie kontekstu edycyjnego ModelItem
ms.date: 03/30/2017
ms.assetid: 7f9f1ea5-0147-4079-8eca-be94f00d3aa1
ms.openlocfilehash: a2628bbbf2f6684e5d484b05cd5a2ac622f3b664
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59296892"
---
# <a name="using-the-modelitem-editing-context"></a>Używanie kontekstu edycyjnego ModelItem
<xref:System.Activities.Presentation.Model.ModelItem> Kontekstu do edycji jest obiekt, który aplikacja hosta używa do komunikowania się za pomocą projektanta. <xref:System.Activities.Presentation.EditingContext> udostępnia dwie metody <xref:System.Activities.Presentation.EditingContext.Items%2A> i <xref:System.Activities.Presentation.EditingContext.Services%2A>, których można używać  
  
## <a name="the-items-collection"></a>Kolekcja elementów  
 <xref:System.Activities.Presentation.EditingContext.Items%2A> Kolekcji umożliwia dostęp do danych, który jest udostępniany między hostem a projektanta lub danych, która jest dostępna dla wszystkich projektantów. Ta kolekcja zawiera następujące funkcje, dostępne za pośrednictwem <xref:System.Activities.Presentation.ContextItemManager> klasy:  
  
1. <xref:System.Activities.Presentation.ContextItemManager.GetValue%2A>  
  
2. <xref:System.Activities.Presentation.ContextItemManager.Subscribe%2A>  
  
3. <xref:System.Activities.Presentation.ContextItemManager.Unsubscribe%2A>  
  
4. <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A>  
  
## <a name="the-services-collection"></a>Kolekcja usług  
 <xref:System.Activities.Presentation.EditingContext.Services%2A> Kolekcji umożliwia dostęp do usług używanych przez projektanta do interakcji z hostem lub usług korzystających z wszystkich projektantów. Ta kolekcja zawiera następujących metod Uwaga:  
  
1. <xref:System.Activities.Presentation.ServiceManager.Publish%2A>  
  
2. <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A>  
  
3. <xref:System.Activities.Presentation.ServiceManager.Unsubscribe%2A>  
  
4. <xref:System.Activities.Presentation.ServiceManager.GetService%2A>  
  
## <a name="assigning-a-designer-an-activity"></a>Przypisywanie projektanta działań  
 Aby określić projektanta, który używa działania, atrybut projektanta jest używany.  
  
```  
[Designer(typeof(MyClassDesigner))]  
public sealed class MyClass : CodeActivity  
{  
```  
  
## <a name="creating-a-service"></a>Tworzenie usługi  
 Aby utworzyć usługę, która służy jako kanał informacji między projektanta i hosta, interfejs i implementacja musi zostać utworzona. Ten interfejs jest używany przez <xref:System.Activities.Presentation.ServiceManager.Publish%2A> metodę, aby zdefiniować członków usługi i implementację zawiera logikę dla usługi. W poniższym przykładzie kodu są tworzone interfejsu usługi i implementację.  
  
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
 Do projektanta w celu korzystania z usługi, musi najpierw być opublikowane przez hosta, za pomocą <xref:System.Activities.Presentation.ServiceManager.Publish%2A> metody.  
  
```  
this.Context.Services.Publish<IMyService>(new MyServiceImpl);  
```  
  
## <a name="subscribing-to-a-service"></a>Subskrybowanie usługi  
 Projektant uzyskuje dostęp do usługi za pomocą <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A> method in Class metoda <xref:System.Activities.Presentation.WorkflowViewElement.OnModelItemChanged%2A> metody. Poniższy fragment kodu przedstawia sposób subskrybowania usługi.  
  
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
  
## <a name="sharing-data-using-the-items-collection"></a>Udostępnianie danych przy użyciu kolekcji elementów  
 Za pomocą kolekcji elementów jest podobne do kolekcji usługi, chyba że <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A> zamiast publikacji jest używana. Ta kolekcja jest bardziej odpowiednia na potrzeby udostępniania proste dane między projektantów i hosta, a nie złożoną funkcji.  
  
## <a name="editingcontext-host-items-and-services"></a>EditingContext hosta i usług  
 .NET Framework udostępnia wiele wbudowanych elementów i usługi dostępne za pośrednictwem Kontekst edycyjny.  
  
 Elementy:  
  
-   <xref:System.Activities.Presentation.Hosting.AssemblyContextControlItem>: Zarządza listę przywoływanych zestawów lokalnych, które będą używane w przepływie pracy formantami (takimi jak Edytor wyrażeń).  
  
-   <xref:System.Activities.Presentation.Hosting.ReadOnlyState>: Wskazuje, czy Projektant znajduje się w stanie tylko do odczytu.  
  
-   <xref:System.Activities.Presentation.View.Selection>: Definiuje kolekcję obiektów, które są obecnie wybrane.  
  
-   <xref:System.Activities.Presentation.Hosting.WorkflowCommandExtensionItem>:  
  
-   <xref:System.Activities.Presentation.WorkflowFileItem>: Zawiera informacje o pliku, na podstawie bieżącej sesji edytowania.  
  
 Usługi:  
  
-   <xref:System.Activities.Presentation.Model.AttachedPropertiesService>: Zezwala na właściwości w celu dodania do bieżącego wystąpienia przy użyciu <xref:System.Activities.Presentation.Model.AttachedPropertiesService.AddProperty%2A>.  
  
-   <xref:System.Activities.Presentation.View.DesignerView>: Umożliwia dostęp do właściwości na kanwie projektanta.  
  
-   <xref:System.Activities.Presentation.IActivityToolboxService>: Zezwala na zawartość przybornika do zaktualizowania.  
  
-   <xref:System.Activities.Presentation.Hosting.ICommandService>: Umożliwia integrację polecenia projektanta (np. Menu kontekstowe) z implementacji usługi dostarczane przez niestandardowe.  
  
-   <xref:System.Activities.Presentation.Debug.IDesignerDebugView>: Oferuje funkcję dla projektanta debugera.  
  
-   <xref:System.Activities.Presentation.View.IExpressionEditorService>: Zapewnia dostęp do okna dialogowego edytora wyrażeń.  
  
-   <xref:System.Activities.Presentation.IIntegratedHelpService>: Zapewnia narzędzia Projektant z funkcjonalnością zintegrowana Pomoc.  
  
-   <xref:System.Activities.Presentation.Validation.IValidationErrorService>: Zapewnia dostęp do błędów sprawdzania poprawności, za pomocą <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A>.  
  
-   <xref:System.Activities.Presentation.IWorkflowDesignerStorageService>: Udostępnia wewnętrzna usługa do przechowywania i pobierania danych. Ta usługa jest używana wewnętrznie przez program .NET Framework i nie jest przeznaczona do użytku zewnętrznego.  
  
-   <xref:System.Activities.Presentation.IXamlLoadErrorService>: Zapewnia dostęp do XAML obciążenia Błąd kolekcji za pomocą <xref:System.Activities.Presentation.IXamlLoadErrorService.ShowXamlLoadErrors%2A>.  
  
-   <xref:System.Activities.Presentation.Services.ModelService>: Używane przez projektanta do interakcji z modelu edytowanym przepływu pracy.  
  
-   <xref:System.Activities.Presentation.Model.ModelTreeManager>: Zapewnia dostęp do katalogu głównego modelu elementu drzewa za pomocą <xref:System.Activities.Presentation.Model.ModelItem.Root%2A>.  
  
-   <xref:System.Activities.Presentation.UndoEngine>: Zapewnia Cofnij i wykonaj ponownie funkcji.  
  
-   <xref:System.Activities.Presentation.Services.ViewService>: Elementy wizualne map podstawowych elementów modelu.  
  
-   <xref:System.Activities.Presentation.View.ViewStateService>: Magazyny widoku stany elementów modelu.  
  
-   <xref:System.Activities.Presentation.View.VirtualizedContainerService>: Umożliwia dostosowywanie zachowania interfejsu użytkownika wirtualnego kontenera.  
  
-   <xref:System.Activities.Presentation.Hosting.WindowHelperService>: Umożliwia rejestrowanie i wyrejestrowywanie delegatów dla powiadomień o zdarzeniach. Umożliwia także właścicielem okna, należy ustawić.
