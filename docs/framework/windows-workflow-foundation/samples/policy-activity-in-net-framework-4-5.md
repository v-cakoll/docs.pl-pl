---
title: "Zasady działania w programie .NET Framework 4.5"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8e375e0c-d7c1-4d69-88ab-36d52db0aa7e
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 66968503d2f481647d999854358a246b4d963475
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="policy-activity-in-net-framework-45"></a>Zasady działania w programie .NET Framework 4.5
Umożliwia działanie Policy4 [!INCLUDE[wf2](../../../../includes/wf2-md.md)] w [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] (WF 3.5) <xref:System.Workflow.Activities.Rules.RuleSet> obiekty mają być używane w [!INCLUDE[wf2](../../../../includes/wf2-md.md)] w [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF 4.5) bezpośrednio za pomocą aparatu reguł, który jest dostarczany w wersji 3.5 WF. Za pomocą tego działania, można tworzyć i wykonywać WF 3.5 <xref:System.Workflow.Activities.Rules.RuleSet>. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]WF 3.5 aparatu reguł dołączone jako część programu Windows Workflow Foundation, przeczytaj wprowadzenie do aparatu reguł systemu Windows Workflow Foundation. Aby uzyskać więcej informacji na temat migracji reguł WF w [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)], przeczytaj [wskazówki dotyczące migracji](../../../../docs/framework/windows-workflow-foundation/migration-guidance.md).  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Rules-Policy4`  
  
## <a name="projects-in-this-sample"></a>Projekty w tym przykładzie  
  
|Nazwa projektu|Opis|Główne pliki|  
|------------------|-----------------|----------------|  
|Policy4|Zawiera działanie Policy4 i jego [!INCLUDE[wf1](../../../../includes/wf1-md.md)] projektanta.|**Policy4.cs**: Policy4 definicji działania.<br /><br /> **PolicyDesigner.xaml**: niestandardowy projektanta dla działania Policy4. Używa edytora zasad ([klasy RuleSetDialog](http://go.microsoft.com/fwlink/?LinkId=150378)) z [!INCLUDE[wf1](../../../../includes/wf1-md.md)] aparatu reguł.|  
|ImperativeCodeClientSample|Przykładowa aplikacja klienta, który konfiguruje i uruchamia przepływ pracy przy użyciu aplikacji Policy4 przy użyciu imperatywnych kodu C# (nie [!INCLUDE[wf1](../../../../includes/wf1-md.md)] projektowania).|**ApplyDiscount.rules**: plik z [!INCLUDE[wf1](../../../../includes/wf1-md.md)] reguły definicje.<br /><br /> **ORDER.cs**: typ, która reprezentuje porządek klienta. Reguły są stosowane do obiektów tego typu.<br /><br /> **Plik program.cs**: konfiguruje i uruchamia przepływ pracy, który ma aktywności Policy4, aby zastosować reguły zdefiniowane w ApplyDiscount.rules do wystąpień obiektów kolejności.<br /><br /> **App.config**: plik konfiguracji ze ścieżką pliku reguł.|  
|DesignerClientSample|Przykładowa aplikacja klienta, który konfiguruje i uruchamia przepływ pracy przy użyciu aplikacji Policy4 w [!INCLUDE[wf1](../../../../includes/wf1-md.md)] projektanta.|**Sequence1.XAML**: sekwencyjnego przepływu pracy, który używa działania Policy4 do wykonywania reguł.<br /><br /> `Program.cs`: Uruchomione jest wystąpienie przepływu pracy zdefiniowane w Sequence1.xaml.|  
  
## <a name="the-policy4-activity"></a>Działanie Policy4  
 Działanie Policy4 jest klasą pochodzącą z <xref:System.Activities.NativeActivity%601> umożliwiająca przepływów pracy można wykonać [!INCLUDE[wf1](../../../../includes/wf1-md.md)] zestawów reguł. Poniższy przykładowy kod jest uproszczone definicja publicznego OM działania.  
  
```csharp  
public class Policy4Activity<TResult>: NativeActivity<TResult>  
{  
    public RuleSet RuleSet  
  
    [IsRequired]  
    public InArgument Input  
  
    public OutArgument<ValidationErrorCollection> ValidationErrors  
}  
```  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|Zestaw reguł|WF [klasy RuleSet](http://go.microsoft.com/fwlink/?LinkId=150379) programu .NET Framework 3.5 ma zostać obliczone, gdy jest wykonywane działanie.|  
|TargetObject|Obiekt, względem którego reguły w [klasy RuleSet](http://go.microsoft.com/fwlink/?LinkId=150379) są oceniane.|  
|ValidationError|Lista błędy walidacji zwrócone przez [!INCLUDE[wf1](../../../../includes/wf1-md.md)] aparat reguł dla programu .NET Framework 3.5 podczas sprawdzania poprawności [klasy RuleSet](http://go.microsoft.com/fwlink/?LinkId=150379) względem obiektu docelowego przed wykonaniem.|  
  
## <a name="policy4-activity-designer"></a>Projektant działań Policy4  
 Projektant Policy4 dodaje możliwości, aby skonfigurować działanie Policy4 bez konieczności pisania kodu. Po utworzeniu rozwiązania, można je znaleźć w przyborniku w sekcji **Microsoft.Samples.Activities.Rules**.  
  
 Projektant WF umożliwia konfigurowanie obiektu docelowego i zestaw reguł. Gdy **Edytuj zestaw reguł** kliknięciu przycisku WF [klasy RuleSetDialog](http://go.microsoft.com/fwlink/?LinkId=150378) dla [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] jest wyświetlany. To okno dialogowe jest ponownie hostowanej [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] Edytor reguł. Edytor do tworzenia i edycji reguły, które wykonuje działania Policy4.  
  
## <a name="using-this-sample"></a>Za pomocą tego przykładu  
 Do uruchomienia tego przykładu jest wymagane nie specjalne Konfigurowanie. Po prostu otwórz rozwiązanie w programie Visual Studio, a następnie naciśnij klawisz F5, aby uruchomić aplikację.  
  
 Ten przykład zawiera dwie aplikacje klienckie: ImperativeCodeClientSample i DesignerClientSample. Klienta ImperativeCodeClientSample przedstawiono sposób konfigurowania i uruchamiania działania Policy40 przy użyciu języka C# imperatywnych kodu. DesignerClientSample przedstawiono sposób konfigurowania i uruchamiania działania Policy4 przy użyciu narzędzia Projektant.  
  
#### <a name="to-run-the-imperativecodeclientsample-client-application"></a>Aby uruchomić aplikację kliencką ImperativeCodeClientSample  
  
1.  Przy użyciu [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz plik rozwiązania Policy4Sample.sln.  
  
2.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **ImperativeCodeClientSample** projektu, a następnie wybierz **Ustaw jako projekt startowy**.  
  
3.  Aby uruchomić projekt, naciśnij kombinację klawiszy CTRL + F5.  
  
#### <a name="to-run-the-imperativecodeclientsample-client-application"></a>Aby uruchomić aplikację kliencką ImperativeCodeClientSample  
  
1.  Przy użyciu [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz plik rozwiązania Policy4Sample.sln.  
  
2.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **DesignerClientSample** projektu.  
  
    -   Wybierz **Ustaw jako projekt startowy**.  
  
3.  Aby skompilować projekt, naciśnij kombinację klawiszy CTRL + SHIFT + B.  
  
4.  Aby uruchomić projekt, naciśnij kombinację klawiszy CTRL + F5.