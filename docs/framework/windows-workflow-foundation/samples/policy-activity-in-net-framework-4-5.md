---
title: Działanie zasad w programie .NET Framework 4.5
ms.date: 03/30/2017
ms.assetid: 8e375e0c-d7c1-4d69-88ab-36d52db0aa7e
ms.openlocfilehash: 9d8983f2f1d3f75beffeacfff4b673f6c23c4204
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44337801"
---
# <a name="policy-activity-in-net-framework-45"></a>Działanie zasad w programie .NET Framework 4.5
Działanie Policy4 zezwala na Windows Workflow Foundation w [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] (WF 3.5) <xref:System.Workflow.Activities.Rules.RuleSet> obiektów, które ma być używany w programie Windows Workflow Foundation w [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF 4.5) bezpośrednio przy użyciu aparatu reguł, który jest dostarczany w WF 3.5. Za pomocą tego działania, można tworzyć i wykonywać WF 3.5 <xref:System.Workflow.Activities.Rules.RuleSet>. Aby uzyskać więcej informacji na temat aparatu reguł 3.5 WF wchodzącego w skład Windows Workflow Foundation przeczytaj wprowadzenie do aparatu reguł programu Windows Workflow Foundation. Aby uzyskać więcej informacji o migrowaniu reguły WF w [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)], przeczytaj [wskazówek dotyczących migracji](../../../../docs/framework/windows-workflow-foundation/migration-guidance.md).  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Rules-Policy4`  
  
## <a name="projects-in-this-sample"></a>Projekty w tym przykładzie  
  
|Nazwa projektu|Opis|Pliki główne|  
|------------------|-----------------|----------------|  
|Policy4|Zawiera działanie Policy4 i jego [!INCLUDE[wf1](../../../../includes/wf1-md.md)] projektanta.|**Policy4.cs**: Policy4 definicji działania.<br /><br /> **PolicyDesigner.xaml**: niestandardowego projektanta Policy4 działania. Użyto Edytora reguł ([klasy RuleSetDialog](https://go.microsoft.com/fwlink/?LinkId=150378)) z [!INCLUDE[wf1](../../../../includes/wf1-md.md)] aparat reguł.|  
|ImperativeCodeClientSample|Przykładowa aplikacja kliencka, która umożliwia skonfigurowanie i uruchamia przepływ pracy przy użyciu aplikacji Policy4 przy użyciu kodu C# imperatywnego (nie [!INCLUDE[wf1](../../../../includes/wf1-md.md)] użyty).|**ApplyDiscount.rules**: plik z [!INCLUDE[wf1](../../../../includes/wf1-md.md)] reguły definicji.<br /><br /> **ORDER.cs**: typ, który reprezentuje zamówienia klienta. Reguły są stosowane do obiektów tego typu.<br /><br /> **Plik program.cs**: konfiguruje i uruchamia przepływ pracy, który ma działanie Policy4 można zastosować reguł zdefiniowanych w ApplyDiscount.rules do wystąpień obiektów zamówienia.<br /><br /> **App.config**: plik konfiguracji ze ścieżką do pliku reguł.|  
|DesignerClientSample|Przykładowa aplikacja kliencka, która umożliwia skonfigurowanie i uruchamia przepływ pracy przy użyciu aplikacji Policy4 w [!INCLUDE[wf1](../../../../includes/wf1-md.md)] projektanta.|**Sequence1.XAML**: sekwencyjny przepływ pracy, który używa działania Policy4 podczas przeprowadzania oceny reguł.<br /><br /> `Program.cs`: Uruchamia wystąpienie przepływu pracy zdefiniowane w Sequence1.xaml.|  
  
## <a name="the-policy4-activity"></a>Działanie Policy4  
 Działanie Policy4 jest klasa, która pochodzi od klasy <xref:System.Activities.NativeActivity%601> umożliwiająca przepływy pracy do wykonania [!INCLUDE[wf1](../../../../includes/wf1-md.md)] zestawów reguł. Poniższy przykład kodu jest uproszczone definicji publicznego OM działania.  
  
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
|Zestaw reguł|WF [klasy RuleSet](https://go.microsoft.com/fwlink/?LinkId=150379) programu .NET Framework 3.5 do obliczenia, gdy jest wykonywane działanie.|  
|TargetObject|Obiekt, względem którego reguły w [klasy RuleSet](https://go.microsoft.com/fwlink/?LinkId=150379) są oceniane.|  
|ValidationError|Lista błędów sprawdzania poprawności zwrócony przez [!INCLUDE[wf1](../../../../includes/wf1-md.md)] aparat reguł programu .NET Framework 3.5 podczas sprawdzania poprawności [klasy zestaw reguł](https://go.microsoft.com/fwlink/?LinkId=150379) względem obiektu docelowego, przed wykonaniem.|  
  
## <a name="policy4-activity-designer"></a>Policy4, Projektant działań  
 Projektant Policy4 dodaje możliwości, aby skonfigurować działanie Policy4 bez konieczności pisania kodu. Po utworzeniu rozwiązania, można je znaleźć w przyborniku w sekcji **Microsoft.Samples.Activities.Rules**.  
  
 Projektant programu WF umożliwia konfigurowanie obiektu docelowego i zestaw reguł. Gdy **Edytuj zestaw reguł** przycisku, WF [klasy RuleSetDialog](https://go.microsoft.com/fwlink/?LinkId=150378) dla [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] jest wyświetlana. To okno dialogowe jest ponownie hostowanej [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] edytora reguł. Edytor do tworzenia i edytowania reguły, które wykonuje działania Policy4.  
  
## <a name="using-this-sample"></a>Za pomocą tego przykładu  
 Nie specjalne Konfigurowanie jest wymagany do uruchomienia tego przykładu. Po prostu otwórz rozwiązanie w programie Visual Studio, a następnie naciśnij klawisz F5, aby uruchomić aplikację.  
  
 Ten przykład zawiera dwie aplikacje klienckie: ImperativeCodeClientSample i DesignerClientSample. Klient ImperativeCodeClientSample pokazuje, jak skonfigurować i uruchomić działanie Policy40 przy użyciu kodu imperatywnego C#. DesignerClientSample pokazuje, jak skonfigurować i uruchomić działanie Policy4 za pomocą projektanta.  
  
#### <a name="to-run-the-imperativecodeclientsample-client-application"></a>Aby uruchomić aplikacji klienckiej ImperativeCodeClientSample  
  
1.  Za pomocą [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz plik rozwiązania Policy4Sample.sln.  
  
2.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **ImperativeCodeClientSample** projektu, a następnie wybierz pozycję **Ustaw jako projekt startowy**.  
  
3.  Aby uruchomić projekt, naciśnij kombinację klawiszy CTRL + F5.  
  
#### <a name="to-run-the-imperativecodeclientsample-client-application"></a>Aby uruchomić aplikacji klienckiej ImperativeCodeClientSample  
  
1.  Za pomocą [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz plik rozwiązania Policy4Sample.sln.  
  
2.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **DesignerClientSample** projektu.  
  
    -   Wybierz **Ustaw jako projekt startowy**.  
  
3.  Aby skompilować projekt, naciśnij klawisze CTRL + SHIFT + B.  
  
4.  Aby uruchomić projekt, naciśnij kombinację klawiszy CTRL + F5.