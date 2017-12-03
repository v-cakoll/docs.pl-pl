---
title: "Działanie externalized zasad w programie .NET Framework 4.5"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 92fd6f92-23a1-4adf-b96a-2754ea93ad3e
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 468d0ca5f4afa4e84b69f58887672ffcf1a14fa6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="externalized-policy-activity-in-net-framework-45"></a>Działanie externalized zasad w programie .NET Framework 4.5
W tym przykładzie przedstawiono sposób działania ExternalizedPolicy4 umożliwia wykonywanie istniejących [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] [!INCLUDE[wf2](../../../../includes/wf2-md.md)] (WF 3.5) <xref:System.Workflow.Activities.Rules.RuleSet> obiekty w [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] [!INCLUDE[wf2](../../../../includes/wf2-md.md)] (WF 4.5) bezpośrednio za pomocą aparatu reguł, który jest dostarczany w wersji 3.5 WF. Za pomocą tego działania, można otwierać i wykonać wszelkie istniejące 3.5 WF <xref:System.Workflow.Activities.Rules.RuleSet>. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Przeczytaj aparatu reguł dołączone jako część programu Windows Workflow Foundation WF 3.5 [wprowadzenie do aparatu reguł systemu Windows Workflow Foundation](http://go.microsoft.com/fwlink/?LinkId=166079). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Migrowanie reguł [!INCLUDE[wf1](../../../../includes/wf1-md.md)] w [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)], przeczytaj wskazówki dotyczące migracji w [wskazówki dotyczące migracji](../../../../docs/framework/windows-workflow-foundation/migration-guidance.md).  
  
## <a name="projects-in-this-sample"></a>Projekty w tym przykładzie  
  
|Nazwa projektu|Opis|Główne pliki|  
|-|-|-|  
|ExternalizedPolicy4|Zawiera działanie ExternalizedPolicy4 i jego projektanta WF 4.5.|**ExternalizedPolicy4.cs**: definicji działania.<br /><br /> **ExternalizedPolicy4Designer.xaml**: niestandardowy projektanta dla działania ExternalizedPolicy4. Używa edytora zasad (<xref:System.Workflow.Activities.Rules.Design.RuleSetDialog>) z aparatu reguł 3.5 WF.|  
|ImperativeCodeClientSample|Przykładowej aplikacji klienta, który konfiguruje i uruchamia przepływ pracy przy użyciu aplikacji ExternalizedPolicy4 przy użyciu imperatywnych kodu C# (Projektant nie jest używany).|**ApplyDiscount.rules**: plik z [!INCLUDE[wf1](../../../../includes/wf1-md.md)] reguły definicje.<br /><br /> **ORDER.cs**: typ, która reprezentuje porządek klienta. Reguły są stosowane do obiektów tego typu.<br /><br /> **Plik program.cs**: konfiguruje i uruchamia przepływ pracy, który ma aktywności Policy4, aby zastosować reguły zdefiniowane w ApplyDiscount.rules do wystąpień obiektów kolejności.<br /><br /> App.config: Plik konfiguracji ze ścieżką pliku reguł.|  
|DesignerClientSample|Przykładowa aplikacja klienta, który konfiguruje i uruchamia przepływ pracy przy użyciu aplikacji ExternalPolicy4 w [!INCLUDE[wf1](../../../../includes/wf1-md.md)] projektanta.|**Sequence1.XAML**: sekwencyjnego przepływu pracy, który używa działania Policy4 do wykonywania reguł.<br /><br /> **Plik program.cs**: jest uruchamiane wystąpienie przepływu pracy zdefiniowane w Sequence1.xaml.|  
  
## <a name="the-externalizedpolicy4-activity"></a>Działanie ExternalizedPolicy4  
 Działanie ExternalizedPolicy4 jest <xref:System.Activities.NativeActivity> , która umożliwia wykonywanie WF 3.5 <xref:System.Workflow.Activities.Rules.RuleSet> obiektów w przepływach pracy WF 4.5. Poniższy przykład jest definicją uproszczonego modelu obiektu publicznego działania.  
  
```  
public class ExternalizedPolicy4Activity<TResult>: CodeActivity  
{  
    public string RulesFilePath   
  
    public string RuleSetName           
  
    [RequiredArgument]  
    public InArgument<T> TargetObject   
  
    [RequiredArgument]  
    public OutArgument<T> ResultObject   
  
    public OutArgument<ValidationErrorCollection> ValidationErrors   
}  
```  
  
|Właściwość|Opis|  
|-|-|  
|RuleSetFilePath|Ścieżka do programu .NET Framework 3.5 <xref:System.Workflow.Activities.Rules.RuleSet> pliku ma zostać obliczone, gdy jest wykonywane działanie.|  
|RuleSetName|Nazwa <xref:System.Workflow.Activities.Rules.RuleSet> do użycia w pliku rules.|  
|TargetObject|Obiekt, w którym <xref:System.Workflow.Activities.Rules.Rule> obiekty w <xref:System.Workflow.Activities.Rules.RuleSet> jest porównywany.|  
|Błędy|Obiekt wynikowy po zastosowaniu zasady (na przykład reguły są stosowane względem argument wejściowy i wynik jest zapisywany w argumencie wynik.|  
|ValidationError|Lista błędy walidacji zwrócone przez aparat reguł 3.5 WF podczas sprawdzania poprawności <xref:System.Workflow.Activities.Rules.RuleSet> względem obiektu docelowego przed realizacją.|  
  
## <a name="externalizedpolicy4-activity-designer"></a>Projektant działań ExternalizedPolicy4  
 Projektant ExternalizedPolicy4 pozwala na skonfigurowanie działania, aby użyć istniejącego RuleSet bez pisania kodu. Wystarczy ustawić ścieżki, w którym znajduje się plik Rules i określ <xref:System.Workflow.Activities.Rules.RuleSet> nazwa, która ma zostać użyta. Można też zmodyfikować <xref:System.Workflow.Activities.Rules.RuleSet>. Po utworzeniu rozwiązania, można je znaleźć w przyborniku w sekcji Microsoft.Samples.Activities.Rules. Projektant służy do wybierania plików Rules i <xref:System.Workflow.Activities.Rules.RuleSet>. Gdy **Edytuj zestaw reguł** kliknięciu przycisku WF 3.5 <xref:System.Workflow.Activities.Rules.Design.RuleSetDialog> jest wyświetlany. To okno dialogowe jest ponownie hostowanej Edytor reguł WF 3.5 i jest używany do wyświetlania i edytowania reguł, które wykonuje działania ExternalizedPolicy4.  
  
## <a name="policy4-and-externalpolicy4"></a>Policy4 i ExternalPolicy4  
 [Działania zasad w programie .NET Framework 4.5](../../../../docs/framework/windows-workflow-foundation/samples/policy-activity-in-net-framework-4-5.md) działania umożliwia tworzenie i wykonywanie zestaw reguł programu .NET Framework 3.5 w przepływie pracy programu WF 4.5. <xref:System.Workflow.Activities.Rules.RuleSet> Jest wbudowany serializacji w działaniu Policy4 definicji XAML. Przykładowe ExternalizedPolicy4 pokazano, jak używać istniejącego zewnętrznych <xref:System.Workflow.Activities.Rules.RuleSet> (zawarte w pliku Rules).  
  
## <a name="using-this-sample"></a>Za pomocą tego przykładu  
 Nie specjalne konfiguracji wymaganej do uruchomienia tego przykładu. Otwórz rozwiązanie w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], i naciśnij klawisz F5, aby uruchomić aplikację.  
  
 Ten przykład zawiera dwie aplikacje klienckie: ImperativeCodeClientSample i DesignerClientSample. Klienta ImperativeCodeClientSample przedstawiono sposób konfigurowania i uruchamiania działania ExternalizedPolicy4 przy użyciu języka C# imperatywnych kodu. DesignerClientSample przedstawiono sposób konfigurowania i uruchamiania działania ExternalizedPolicy4 przy użyciu narzędzia Projektant.  
  
#### <a name="to-run-the-imperativecodeclientsample-application"></a>Aby uruchomić aplikację ImperativeCodeClientSample  
  
1.  Przy użyciu [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz plik rozwiązania Policy4sample.sln.  
  
2.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **ImperativeCodeClientSample** projektu, a następnie wybierz **Ustaw jako projekt startowy**.  
  
3.  Aby uruchomić projekt, naciśnij kombinację klawiszy CTRL + F5.  
  
#### <a name="to-run-the-designerclientsample-application"></a>Aby uruchomić aplikację DesignerClientSample  
  
1.  Przy użyciu [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz plik rozwiązania Policy4sample.sln.  
  
2.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **DesignerClientSample** projektu, a następnie wybierz **Ustaw jako projekt startowy**.  
  
3.  Naciśnij klawisze CTRL + SHIFT + B, aby skompilować projekt.  
  
4.  Naciśnij klawisze CTRL + F5, aby uruchomić projekt.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Rules-ExternalizedPolicy4`
