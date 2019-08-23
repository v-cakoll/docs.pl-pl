---
title: Równoległe przechowywanie wersji w klasie WorkflowServiceHost
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 60887eed-df40-4412-b812-41e1dd329d15
ms.openlocfilehash: ba0bcdf152ab0ee6632ae472db0bc81496cb6381
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969221"
---
# <a name="side-by-side-versioning-in-workflowservicehost"></a>Równoległe przechowywanie wersji w klasie WorkflowServiceHost
<xref:System.ServiceModel.Activities.WorkflowServiceHost> Równoległe przechowywanie wersji wprowadzone w .NET Framework 4,5 zapewnia możliwość hostowania wielu wersji usługi przepływu pracy w jednym punkcie końcowym. Zapewniane funkcje równoczesne umożliwiają skonfigurowanie usługi przepływu pracy w taki sposób, że nowe wystąpienia usługi przepływu pracy są tworzone przy użyciu nowej definicji przepływu pracy, podczas gdy uruchomione wystąpienia są kompletne przy użyciu istniejącej definicji. Ten temat zawiera omówienie wykonywania równoczesnego usługi przepływu pracy przy użyciu programu <xref:System.ServiceModel.Activities.WorkflowServiceHost>.  
  
> [!NOTE]
> Aby pobrać przykład i obejrzeć film wideo dotyczący obsługi wersji równoległych usługi przepływu pracy, zobacz [obok siebie przechowywanie wersji obok sieci Web xamlx Workflow Service](https://go.microsoft.com/fwlink/?LinkId=393746).  
  
## <a name="hosting-multiple-versions-in-a-workflow-service"></a>Hostowanie wielu wersji w usłudze przepływu pracy  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost>zawiera dwie właściwości, które można skonfigurować tak, aby umożliwić wykonywanie wielu wersji przepływu pracy obok siebie: <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> i. <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A>zawiera obsługiwane wersje usługi przepływu pracy i <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> służy do jednoznacznej identyfikacji każdej usługi przepływu pracy. Jest to realizowane przez skojarzenie <xref:System.Activities.WorkflowIdentity> z usługą przepływu pracy. A <xref:System.Activities.WorkflowIdentity> zawiera trzy identyfikujące informacje. <xref:System.Activities.WorkflowIdentity.Name%2A>i <xref:System.Activities.WorkflowIdentity.Version%2A> zawiera nazwę <xref:System.Version> i <xref:System.Activities.WorkflowIdentity.Package%2A> i są wymagane i jest opcjonalne i może służyć do określenia dodatkowego ciągu zawierającego informacje takie jak nazwa zestawu lub inne żądane informacje. Każda usługa przepływu pracy znajdująca <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> się w kolekcji musi mieć <xref:System.Activities.WorkflowIdentity>unikatową wartość. Jest <xref:System.Activities.WorkflowIdentity> unikatowa, jeśli którykolwiek z jego trzech właściwości różni się od <xref:System.Activities.WorkflowIdentity>innego. A `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> `null` jest wartością dozwoloną dla, ale tylko jedna Poprzednia <xref:System.Activities.WorkflowIdentity>wersja usługi przepływu pracy może mieć. <xref:System.Activities.WorkflowIdentity>  
  
> [!IMPORTANT]
> A <xref:System.Activities.WorkflowIdentity> nie powinna zawierać żadnych informacji umożliwiających identyfikację użytkownika. <xref:System.Activities.WorkflowIdentity>składa się z trzech części: <xref:System.Activities.WorkflowIdentity.Name%2A> a<xref:System.String>(), <xref:System.Activities.WorkflowIdentity.Version%2A> a<xref:System.Version>() i <xref:System.Activities.WorkflowIdentity.Package%2A> a (<xref:System.String>). Informacje o <xref:System.Activities.WorkflowIdentity> użytym do utworzenia wystąpienia są emitowane do wszelkich skonfigurowanych usług śledzenia w kilku różnych punktach cyklu życia działania przez środowisko uruchomieniowe. Śledzenie WF nie ma żadnego mechanizmu ukrywania danych osobowych (poufne dane użytkownika). W związku z tym wystąpienieniepowinnozawieraćżadnychdanychosobowych,ponieważbędzieemitowaneprzezśrodowiskouruchomieniowewceluśledzeniarekordówimożebyćwidocznedlakażdego,ktomadostępdowyświetlaniarekordówśledzenia.<xref:System.Activities.WorkflowIdentity>  
  
### <a name="rules-for-hosting-multiple-versions-of-a-workflow-service"></a>Reguły hostingu wielu wersji usługi przepływu pracy  
 Gdy użytkownik dodaje do programu <xref:System.ServiceModel.Activities.WorkflowServiceHost>dodatkową wersję, istnieje kilka warunków, które muszą zostać spełnione, aby usługa przepływu pracy była hostowana z tym samym zestawem punktów końcowych i opisem. Jeśli jakakolwiek z dodatkowych wersji nie spełni tych warunków, <xref:System.ServiceModel.Activities.WorkflowServiceHost> zgłasza wyjątek, gdy `Open` jest wywoływany. Każda definicja przepływu pracy podana dla hosta jako dodatkowa wersja musi spełniać następujące wymagania (w przypadku których podstawowa wersja jest definicją usługi przepływu pracy dostarczoną do konstruktora hosta). Dodatkowa wersja przepływu pracy musi:  
  
- Być taka sama <xref:System.ServiceModel.Activities.WorkflowService.Name%2A> jak podstawowa wersja usługi przepływu pracy.  
  
- Nie może zawierać żadnych <xref:System.ServiceModel.Activities.Receive> działań <xref:System.ServiceModel.Activities.SendReply> ani w <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> nich, które nie znajdują się w wersji głównej, i muszą być zgodne z kontraktem operacji.  
  
- Mieć unikatową <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>wartość. Jeden i tylko jedna definicja przepływu pracy może mieć `null`. <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>  
  
 Niektóre zmiany są dozwolone. Następujące elementy mogą się różnić między wersjami:  
  
- <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> Może mieć inną nazwę i pakiet niż wersja podstawowa.  
  
- <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> Wartość może być inna niż wersja podstawowa.  
  
- <xref:System.ServiceModel.Activities.WorkflowService.ConfigurationName%2A> Może być inna niż wersja podstawowa.  
  
- <xref:System.ServiceModel.Activities.WorkflowService.ImplementedContracts%2A> Może być inna niż wersja podstawowa.  
  
### <a name="configuring-the-definitionidentity"></a>Konfigurowanie DefinitionIdentity  
 Gdy usługa przepływu pracy jest tworzona przy użyciu projektanta przepływu pracy, <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> jest ustawiana za pomocą okna **Właściwości** . Kliknij poza działaniem głównym usługi w projektancie, aby wybrać usługę przepływu pracy, a następnie wybierz **okno właściwości** z menu **Widok** . Z listy rozwijanej wybierz pozycję **Właściwości WorkflowIdentity** , która pojawia się obok właściwości **DefinitionIdentity** , a następnie rozwiń i określ żądane <xref:System.Activities.WorkflowIdentity> właściwości. W poniższym <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> przykładzie jest skonfigurowany `MortgageWorkflow` <xref:System.Activities.WorkflowIdentity.Name%2A> z i <xref:System.Activities.WorkflowIdentity.Version%2A> z.`1.0.0.0` <xref:System.Activities.WorkflowIdentity.Package%2A>jest opcjonalny i w tym przykładzie `null`.  
  
 ![Zrzut ekranu przedstawiający Właściwość DefinitionIdentity.](./media/side-by-side-versioning-in-workflowservicehost/definitionidentity-property.bmp)  
  
 Gdy usługa przepływu pracy jest samoobsługowa, <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> jest konfigurowana podczas konstruowania usługi przepływu pracy. W poniższym <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> przykładzie jest skonfigurowany z tymi samymi wartościami jak w poprzednim przykładzie, `MortgageWorkflow` <xref:System.Activities.WorkflowIdentity.Name%2A> z i <xref:System.Activities.WorkflowIdentity.Name%2A> `1.0.0.0`a.  
  
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
  
 Element <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> nie jest wymagany, ale tylko jedna wersja usługi przepływu pracy może mieć **wartość null**<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.  
  
> [!NOTE]
> Jest to przydatne, jeśli usługa została wdrożona początkowo bez <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> skonfigurowanej, a następnie tworzona jest zaktualizowana wersja.  
  
### <a name="adding-a-new-version-to-a-web-hosted-workflow-service"></a>Dodawanie nowej wersji do usługi przepływu pracy hostowanej w sieci Web  
 Pierwszym krokiem w konfigurowaniu nowej wersji usługi przepływu pracy w usłudze hostowanej w sieci Web jest utworzenie nowego folderu w `App_Code` folderze, który ma taką samą nazwę jak plik usługi. Jeśli `xamlx` plik usługi ma nazwę `MortgageWorkflow.xamlx`, folder musi mieć nazwę `MortgageWorkflow`. Umieść kopię `xamlx` pliku pierwotnej usługi w tym folderze i zmień jego nazwę na nową nazwę, `MortgageWorkflowV1.xamlx`na przykład. Wprowadź odpowiednie zmiany w usłudze głównej, zaktualizuj ją <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, a następnie wdróż usługę. W poniższym <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> przykładzie został zaktualizowany `MortgageWorkflow` <xref:System.Activities.WorkflowIdentity.Name%2A> z i <xref:System.Activities.WorkflowIdentity.Version%2A> a.`2.0.0.0`  
  
 ![Zrzut ekranu pokazujący DefinitionIdentity właściwości WorkflowIdentity.](./media/side-by-side-versioning-in-workflowservicehost/definitionidentity-workflowidentity.bmp)  
  
 Po ponownym uruchomieniu usługi Poprzednia wersja zostanie automatycznie dodana do <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> kolekcji, ponieważ znajduje się ona w wydzielonym `App_Code` podfolderze. Należy pamiętać, że jeśli podstawowa wersja usługi `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> przepływu pracy nie zostanie dodana do poprzednich wersji. Jedna wersja `null`może mieć <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, ale jeśli istnieje wiele wersji, wersja podstawowa nie może `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> być tą, a w przeciwnym razie poprzednie wersje nie zostaną dodane do <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> kolekcji.  
  
### <a name="adding-a-new-version-to-a-self-hosted-workflow-service"></a>Dodawanie nowej wersji do samodzielnej usługi przepływu pracy  
 Podczas dodawania nowej wersji do samodzielnej usługi <xref:System.ServiceModel.Activities.WorkflowServiceHost> przepływu pracy konfiguracja jest konfigurowana z podstawową wersją usługi przepływu pracy, a wcześniejsze wersje muszą zostać jawnie dodane <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> do kolekcji. W poniższym przykładzie <xref:System.ServiceModel.Activities.WorkflowServiceHost> jest konfigurowana za pomocą podstawowej usługi `MortgageWorkflowV2` przepływu pracy korzystającej z definicji przepływu pracy, a usługa `MortgageWorkflowV1` przepływu pracy skonfigurowana za pomocą definicji przepływu pracy jest dodawana do <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> kolekcji. Dla każdej usługi przepływu pracy jest skonfigurowany unikatowy <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> , który odzwierciedla wersję definicji przepływu pracy.  
  
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
