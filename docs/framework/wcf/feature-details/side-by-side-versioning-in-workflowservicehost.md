---
title: Równoległe przechowywanie wersji w klasie WorkflowServiceHost
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 60887eed-df40-4412-b812-41e1dd329d15
ms.openlocfilehash: 0dfb2469ac3f497a40a3008c9933977947685979
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2019
ms.locfileid: "67425501"
---
# <a name="side-by-side-versioning-in-workflowservicehost"></a>Równoległe przechowywanie wersji w klasie WorkflowServiceHost
<xref:System.ServiceModel.Activities.WorkflowServiceHost> Versioning side-by-side wprowadzone w programie .NET Framework 4.5 zapewnia możliwość hostowania wielu wersji usługi przepływu pracy w jednym punkcie końcowym. Side-by-side funkcjonalność umożliwia usługi przepływu pracy, należy skonfigurować tak, aby nowe wystąpienia usługi przepływu pracy są tworzone przy użyciu nową definicję przepływu pracy podczas uruchamiania wystąpienia pełną, przy użyciu istniejącą definicję. Ten temat zawiera omówienie przepływu pracy usługi wykonywania side-by-side przy użyciu <xref:System.ServiceModel.Activities.WorkflowServiceHost>.  
  
> [!NOTE]
>  Aby pobrać próbkę i obejrzyj przewodnik wideo dotyczący przechowywanie wersji side-by-side usługi przepływu pracy, zobacz [równoległe przechowywanie wersji przy użyciu usługi przepływu pracy Xamlx Web-Hosted](https://go.microsoft.com/fwlink/?LinkId=393746).  
  
## <a name="hosting-multiple-versions-in-a-workflow-service"></a>Hostowanie wielu wersji w usłudze przepływu pracy  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost> zawiera dwie właściwości, które można skonfigurować tak, aby umożliwić wielu wersji przepływu pracy do wykonania side-by-side: <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> i <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>. <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> zawiera obsługiwane wersje usługi przepływu pracy i <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> jest używany do jednoznacznego identyfikowania poszczególnych usług przepływu pracy. Jest to realizowane przez skojarzenie <xref:System.Activities.WorkflowIdentity> przy użyciu usługi przepływu pracy. Element <xref:System.Activities.WorkflowIdentity> zawiera trzy identyfikujące informacje. <xref:System.Activities.WorkflowIdentity.Name%2A> i <xref:System.Activities.WorkflowIdentity.Version%2A> zawiera nazwy i <xref:System.Version> i są wymagane, i <xref:System.Activities.WorkflowIdentity.Package%2A> jest opcjonalna i może służyć do określenia dodatkowych ciąg zawierający informacje, takie jak nazwa zestawu lub inne żądane informacje. Każda usługa przepływu pracy zawarte w <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> Kolekcja musi mieć unikatową <xref:System.Activities.WorkflowIdentity>. A <xref:System.Activities.WorkflowIdentity> są unikatowe, jeśli dowolny z jego trzy właściwości różnią się od innego <xref:System.Activities.WorkflowIdentity>. A `null` <xref:System.Activities.WorkflowIdentity> jest dozwoloną wartością <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, ale tylko jednej poprzedniej wersji usługi przepływu pracy mogą mieć `null` <xref:System.Activities.WorkflowIdentity>.  
  
> [!IMPORTANT]
>  Element <xref:System.Activities.WorkflowIdentity> nie może zawierać wszelkie identyfikowalne dane osobowe (PII). <xref:System.Activities.WorkflowIdentity> składa się z trzech części: <xref:System.Activities.WorkflowIdentity.Name%2A> (<xref:System.String>), <xref:System.Activities.WorkflowIdentity.Version%2A> (<xref:System.Version>), a <xref:System.Activities.WorkflowIdentity.Package%2A> (<xref:System.String>). Informacje o <xref:System.Activities.WorkflowIdentity> użyty do utworzenia wystąpienia jest emitowany do żadnych skonfigurowanych śledzenia cyklu życia usługi w wielu różnych punktach działania w czasie wykonywania. WF śledzenia nie ma żadnych mechanizmu, aby ukryć dane osobowe (poufne dane użytkowników). W związku z tym <xref:System.Activities.WorkflowIdentity> wystąpienia nie powinna zawierać wszystkie dane osobowe, ponieważ będzie emitowane przez środowisko uruchomieniowe w rekordy śledzenia i mogą być widoczne dla każda osoba mająca dostęp do wyświetlania rekordów śledzenia.  
  
### <a name="rules-for-hosting-multiple-versions-of-a-workflow-service"></a>Reguły hostowania wielu wersji usługi przepływu pracy  
 Gdy użytkownik doda dodatkowe wersji, aby <xref:System.ServiceModel.Activities.WorkflowServiceHost>, istnieje kilka warunków, które muszą zostać spełnione, aby być obsługiwana za pomocą tego samego zestawu punktów końcowych i opis usługi przepływu pracy. Jeśli dowolne dodatkowe wersje nie spełniają te warunki <xref:System.ServiceModel.Activities.WorkflowServiceHost> zgłasza wyjątek, gdy `Open` jest wywoływana. Każda definicja przepływu pracy do hosta jako dodatkowe wersji musi spełniać następujące wymagania (gdzie wersji podstawowy jest definicji usługi przepływu pracy, który został dostarczony do konstruktora hosta). Wersja dodatkowe przepływu pracy musi:  
  
- Mają taką samą <xref:System.ServiceModel.Activities.WorkflowService.Name%2A> jako głównej wersji usługi przepływu pracy.  
  
- Nie może mieć dowolny <xref:System.ServiceModel.Activities.Receive> lub <xref:System.ServiceModel.Activities.SendReply> działania w jego <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> nie znajdują się w wersji podstawowej i muszą one odpowiadać kontrakt operacji.  
  
- Mieć unikatowy <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>. Może mieć tylko jedną definicję przepływu pracy `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.  
  
 Niektóre zmiany nie są dozwolone. Poniższe elementy może różnić się między wersjami:  
  
- <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> Mogą mieć różne nazwy i pakietu od wersji głównej.  
  
- <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> Wartość może być inny niż w wersji podstawowej.  
  
- <xref:System.ServiceModel.Activities.WorkflowService.ConfigurationName%2A> Może różnić się od wersji głównej.  
  
- <xref:System.ServiceModel.Activities.WorkflowService.ImplementedContracts%2A> Może różnić się od wersji głównej.  
  
### <a name="configuring-the-definitionidentity"></a>Konfigurowanie DefinitionIdentity  
 Podczas tworzenia usługi przepływu pracy za pomocą projektanta przepływów pracy <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> można ustawić przy użyciu **właściwości** okna. Kliknij poza działania głównego usługi w projektancie, aby wybrać usługi przepływu pracy, a następnie wybierz **okno właściwości** z **widoku** menu. Wybierz **obiektu WorkflowIdentity** z listy rozwijanej, która pojawia się obok **DefinitionIdentity** właściwości, a następnie rozwiń węzeł i określ żądany <xref:System.Activities.WorkflowIdentity> właściwości. W poniższym przykładzie <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> skonfigurowano <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` i <xref:System.Activities.WorkflowIdentity.Version%2A> z `1.0.0.0`. <xref:System.Activities.WorkflowIdentity.Package%2A> jest opcjonalny, a w tym przykładzie jest `null`.  
  
 ![Zrzut ekranu pokazujący właściwość DefinitionIdentity.](./media/side-by-side-versioning-in-workflowservicehost/definitionidentity-property.bmp)  
  
 Gdy usługi przepływu pracy jest samodzielnie hostowana, <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> jest skonfigurowany, gdy jest konstruowany usługi przepływu pracy. W poniższym przykładzie <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> skonfigurowano przy użyciu tej samej wartości jak w poprzednim przykładzie <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` i <xref:System.Activities.WorkflowIdentity.Name%2A> z `1.0.0.0`.  
  
```csharp  
WorkflowService service = new WorkflowService  
{  
    Name = "MortgageWorkflowService",  
    Body = new MortgageWorkflow(),  
    DefinitionIdentity = new WorkflowIdentity  
    {  
        Name = "MortgageWorkflow",  
        Version = new Version(1, 0, 0, 0)  
    }  
};  
```  
  
```vb  
Dim service As New WorkflowService  
With service  
    .Name = "MortgageWorkflowService"  
    .Body = New MortgageWorkflow  
    .DefinitionIdentity = New WorkflowIdentity With _  
    { _  
        .Name = "MortgageWorkflow", _  
        .Version = New Version(1, 0, 0, 0) _  
    }  
End With  
```  
  
 A <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> nie jest wymagane, chociaż może mieć tylko jedną wersję usługi przepływu pracy **null**<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.  
  
> [!NOTE]
>  Jest to przydatne, jeśli usługa była wdrożona początkowo bez <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> skonfigurowany, a następnie jest tworzony jest dostępna zaktualizowana wersja.  
  
### <a name="adding-a-new-version-to-a-web-hosted-workflow-service"></a>Dodawanie nowej wersji do usługi hostowanej w sieci Web przepływu pracy  
 Pierwszym etapem konfigurowania nowej wersji usługi przepływu pracy w usłudze hostowanej w sieci web jest utworzenie nowego folderu w `App_Code` folder, który ma taką samą nazwę jak plik usługi. Jeśli usługa `xamlx` nosi nazwę pliku `MortgageWorkflow.xamlx`, musi nosić nazwę folderu, a następnie `MortgageWorkflow`. Umieść kopię oryginalnego usługi `xamlx` pliku do tego folderu i zmień jego nazwę na nową nazwę, taką jak `MortgageWorkflowV1.xamlx`. Wprowadź żądane zmiany do podstawowej usługi, zaktualizuj jego <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, a następnie wdrożyć usługę. W poniższym przykładzie <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> został zaktualizowany o <xref:System.Activities.WorkflowIdentity.Name%2A> z `MortgageWorkflow` i <xref:System.Activities.WorkflowIdentity.Version%2A> z `2.0.0.0`.  
  
 ![Zrzut ekranu pokazujący DefinitionIdentity obiektu WorkflowIdentity.](./media/side-by-side-versioning-in-workflowservicehost/definitionidentity-workflowidentity.bmp)  
  
 Po ponownym uruchomieniu usługi, poprzednia wersja zostaną automatycznie dodane do <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> kolekcji, ponieważ znajduje się w wyznaczonej `App_Code` podfolderu. Należy pamiętać, że jeśli głównej wersji usługi przepływu pracy ma `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> poprzednie wersje nie zostaną dodane. Może mieć jedną wersję `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, ale istnieje wiele wersji głównej wersji nie może być jednym z `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> lub inne poprzednich wersji, nie zostanie dodany do <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> kolekcji.  
  
### <a name="adding-a-new-version-to-a-self-hosted-workflow-service"></a>Dodawanie nowej wersji usługi samodzielnie hostowanej przepływu pracy  
 Podczas dodawania nowej wersji do usługi samodzielnie hostowanej przepływu pracy, <xref:System.ServiceModel.Activities.WorkflowServiceHost> skonfigurowano przy użyciu wersji głównej usługi przepływu pracy i poprzednie wersje, które muszą zostać jawnie dodane do <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> kolekcji. W poniższym przykładzie <xref:System.ServiceModel.Activities.WorkflowServiceHost> jest skonfigurowany przy użyciu usługi podstawowy przepływ pracy, który używa `MortgageWorkflowV2` definicji przepływu pracy i skonfigurowano usługi przepływu pracy `MortgageWorkflowV1` definicji przepływu pracy jest dodawany do <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> kolekcji. Każda usługa przepływu pracy jest skonfigurowany przy użyciu unikatowego <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> , które odzwierciedla wersji definicji przepływu pracy.  
  
```csharp  
// Create the primary version of the workflow service.  
WorkflowService serviceV2 = new WorkflowService  
{  
    Name = "MortgageWorkflowService",  
    Body = new MortgageWorkflowV2(),  
    DefinitionIdentity = new WorkflowIdentity  
    {  
        Name = "MortgageWorkflow",  
        Version = new Version(2, 0, 0, 0)  
    }  
};  
  
// Configure the WorkflowServiceHost with the current version  
// of the workflow service. This code requires Administrator  
// privileges to function correctly. If running from Visual  
// Studio, Visual Studio must be run with Administrator privileges.  
WorkflowServiceHost host = new WorkflowServiceHost(serviceV2,   
    new Uri("http://localhost:8080/MortgageWorkflowService"));  
  
// Create the previous version of the workflow service.  
WorkflowService serviceV1 = new WorkflowService  
{  
    Name = "MortgageWorkflowService",  
    Body = new MortgageWorkflowV1(),  
    DefinitionIdentity = new WorkflowIdentity  
    {  
        Name = "MortgageWorkflow",  
        Version = new Version(1, 0, 0, 0)  
    }  
};  
  
// Add the previous version of the service to the SupportedVersions collection.  
host.SupportedVersions.Add(serviceV1);  
```  
  
```vb  
'Create the primary version of the workflow service  
Dim serviceV2 As New WorkflowService  
With serviceV2  
    .Name = "MortgageWorkflowService"  
    .Body = New MortgageWorkflowV2  
    .DefinitionIdentity = New WorkflowIdentity With _  
    { _  
        .Name = "MortgageWorkflow", _  
        .Version = New Version(2, 0, 0, 0) _  
    }  
End With  
  
'Configure the WorkflowServiceHost with the current version  
'of the workflow service. This code requires Administrator  
'privileges to function correctly. If running from Visual  
'Studio, Visual Studio must be run with Administrator privileges.  
  
Dim host As New WorkflowServiceHost(serviceV2, _  
    New Uri("http://localhost:8080/MortgageWorkflowService"))  
  
'Create the previous version of the workflow service.  
Dim serviceV1 As New WorkflowService  
With serviceV1  
    .Name = "MortgageWorkflowService"  
    .Body = New MortgageWorkflowV1  
    .DefinitionIdentity = New WorkflowIdentity With _  
    { _  
        .Name = "MortgageWorkflow", _  
        .Version = New Version(1, 0, 0, 0) _  
    }  
End With  
  
'Add the previous version of the service to the SupportedVersions collection.  
host.SupportedVersions.Add(serviceV1)  
```
