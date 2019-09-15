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
# <a name="using-the-modelitem-editing-context"></a>Używanie kontekstu edycyjnego ModelItem
Kontekst <xref:System.Activities.Presentation.Model.ModelItem> edycji jest obiektem, którego aplikacja hosta używa do komunikowania się z projektantem. <xref:System.Activities.Presentation.EditingContext>uwidacznia dwie metody <xref:System.Activities.Presentation.EditingContext.Items%2A> i <xref:System.Activities.Presentation.EditingContext.Services%2A>, które mogą być używane  
  
## <a name="the-items-collection"></a>Kolekcja elementów  
 <xref:System.Activities.Presentation.EditingContext.Items%2A> Kolekcja służy do uzyskiwania dostępu do danych, które są udostępniane między hostem a projektantem, lub danymi, które są dostępne dla wszystkich projektantów. Ta kolekcja ma następujące możliwości, do których można uzyskać <xref:System.Activities.Presentation.ContextItemManager> dostęp za pośrednictwem klasy:  
  
1. <xref:System.Activities.Presentation.ContextItemManager.GetValue%2A>  
  
2. <xref:System.Activities.Presentation.ContextItemManager.Subscribe%2A>  
  
3. <xref:System.Activities.Presentation.ContextItemManager.Unsubscribe%2A>  
  
4. <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A>  
  
## <a name="the-services-collection"></a>Kolekcja usług  
 <xref:System.Activities.Presentation.EditingContext.Services%2A> Kolekcja służy do uzyskiwania dostępu do usług, które są używane przez projektanta do współdziałania z hostem lub usług, których używają wszyscy projektanci. Ta kolekcja zawiera następujące metody:  
  
1. <xref:System.Activities.Presentation.ServiceManager.Publish%2A>  
  
2. <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A>  
  
3. <xref:System.Activities.Presentation.ServiceManager.Unsubscribe%2A>  
  
4. <xref:System.Activities.Presentation.ServiceManager.GetService%2A>  
  
## <a name="assigning-a-designer-an-activity"></a>Przypisywanie działania projektanta  
 Aby określić projektanta, który jest używany przez działanie, używany jest atrybut projektanta.  
  
```csharp  
[Designer(typeof(MyClassDesigner))]  
public sealed class MyClass : CodeActivity  
{
}
```  
  
## <a name="creating-a-service"></a>Tworzenie usługi  
 Aby utworzyć usługę, która służy jako kanał informacji między projektantem a hostem, należy utworzyć interfejs i implementację. Interfejs jest używany przez <xref:System.Activities.Presentation.ServiceManager.Publish%2A> metodę do definiowania członków usługi, a implementacja zawiera logikę dla usługi. W poniższym przykładzie kodu jest tworzony interfejs usługi i implementacja.  
  
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
 Aby projektant mógł korzystać z usługi, musi zostać najpierw Opublikowany przez hosta przy użyciu <xref:System.Activities.Presentation.ServiceManager.Publish%2A> metody.  
  
```csharp  
this.Context.Services.Publish<IMyService>(new MyServiceImpl);  
```  
  
## <a name="subscribing-to-a-service"></a>Subskrybowanie usługi  
 Projektant uzyskuje dostęp do usługi przy użyciu <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A> metody <xref:System.Activities.Presentation.WorkflowViewElement.OnModelItemChanged%2A> w metodzie. Poniższy fragment kodu przedstawia sposób subskrybowania usługi.  
  
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
  
## <a name="sharing-data-using-the-items-collection"></a>Udostępnianie danych przy użyciu kolekcji Items  
 Używanie kolekcji Items jest podobne do korzystania z kolekcji usług, z tą <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A> różnicą, że jest używana zamiast publikowania. Ta kolekcja jest bardziej odpowiednia do udostępniania prostych danych między projektantami i hostem, a nie złożonymi funkcjami.  
  
## <a name="editingcontext-host-items-and-services"></a>EditingContext elementy i usługi hosta  
 .NET Framework zawiera wiele wbudowanych elementów i usług dostępnych za pomocą kontekstu edycji.  
  
 Produktów  
  
- <xref:System.Activities.Presentation.Hosting.AssemblyContextControlItem>: Zarządza listą przywoływanych zestawów lokalnych, które będą używane w przepływie pracy dla kontrolek (takich jak Edytor wyrażeń).  
  
- <xref:System.Activities.Presentation.Hosting.ReadOnlyState>: Wskazuje, czy projektant jest w stanie tylko do odczytu.  
  
- <xref:System.Activities.Presentation.View.Selection>: Definiuje kolekcję obiektów, które są obecnie zaznaczone.  
  
- <xref:System.Activities.Presentation.Hosting.WorkflowCommandExtensionItem>:  
  
- <xref:System.Activities.Presentation.WorkflowFileItem>: Zawiera informacje dotyczące pliku, na którym jest oparta bieżąca sesja edycji.  
  
 Services  
  
- <xref:System.Activities.Presentation.Model.AttachedPropertiesService>: Zezwala na dodawanie właściwości do bieżącego wystąpienia przy użyciu <xref:System.Activities.Presentation.Model.AttachedPropertiesService.AddProperty%2A>.  
  
- <xref:System.Activities.Presentation.View.DesignerView>: Zezwala na dostęp do właściwości kanwy projektanta.  
  
- <xref:System.Activities.Presentation.IActivityToolboxService>: Zezwala na aktualizowanie zawartości przybornika.  
  
- <xref:System.Activities.Presentation.Hosting.ICommandService>: Służy do integrowania poleceń projektanta (takich jak menu kontekstowe) z implementacjami usług udostępnianymi niestandardowo.  
  
- <xref:System.Activities.Presentation.Debug.IDesignerDebugView>: Oferuje funkcje debugera projektanta.  
  
- <xref:System.Activities.Presentation.View.IExpressionEditorService>: Zapewnia dostęp do okna dialogowego edytora wyrażeń.  
  
- <xref:System.Activities.Presentation.IIntegratedHelpService>: Oferuje projektanta z zintegrowaną funkcją pomocy.  
  
- <xref:System.Activities.Presentation.Validation.IValidationErrorService>: Zapewnia dostęp do błędów walidacji <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A>przy użyciu.  
  
- <xref:System.Activities.Presentation.IWorkflowDesignerStorageService>: Zapewnia usługę wewnętrzną do przechowywania i pobierania danych. Ta usługa jest używana wewnętrznie przez .NET Framework i nie jest przeznaczona do użytku zewnętrznego.  
  
- <xref:System.Activities.Presentation.IXamlLoadErrorService>: Zapewnia dostęp do kolekcji błędów ładowania XAML przy użyciu <xref:System.Activities.Presentation.IXamlLoadErrorService.ShowXamlLoadErrors%2A>.  
  
- <xref:System.Activities.Presentation.Services.ModelService>: Używany przez projektanta do współpracy z modelem edytowanego przepływu pracy.  
  
- <xref:System.Activities.Presentation.Model.ModelTreeManager>: Zapewnia dostęp do katalogu głównego drzewa elementów modelu przy użyciu <xref:System.Activities.Presentation.Model.ModelItem.Root%2A>.  
  
- <xref:System.Activities.Presentation.UndoEngine>: Zapewnia funkcję cofania i ponawiania.  
  
- <xref:System.Activities.Presentation.Services.ViewService>: Mapuje elementy wizualne na bazowe elementy modelu.  
  
- <xref:System.Activities.Presentation.View.ViewStateService>: Przechowuje Stany widoku dla elementów modelu.  
  
- <xref:System.Activities.Presentation.View.VirtualizedContainerService>: Służy do dostosowywania zachowania interfejsu użytkownika kontenera wirtualnego.  
  
- <xref:System.Activities.Presentation.Hosting.WindowHelperService>: Służy do rejestrowania i wyrejestrowania delegatów dla powiadomień o zdarzeniach. Umożliwia również ustawienie właściciela okna.
