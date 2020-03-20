---
title: Równoległe przechowywanie wersji w klasie WorkflowServiceHost
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 60887eed-df40-4412-b812-41e1dd329d15
ms.openlocfilehash: bc662e51c96a06737e1bd6fd78d5f70f3922d080
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184473"
---
# <a name="side-by-side-versioning-in-workflowservicehost"></a>Równoległe przechowywanie wersji w klasie WorkflowServiceHost
Wersja <xref:System.ServiceModel.Activities.WorkflowServiceHost> side-by-side wprowadzona w programie .NET Framework 4.5 umożliwia obsługę wielu wersji usługi przepływu pracy w jednym punkcie końcowym. Dostępne funkcje side-by-side umożliwiają skonfigurowanie usługi przepływu pracy w taki sposób, aby nowe wystąpienia usługi przepływu pracy były tworzone przy użyciu nowej definicji przepływu pracy, podczas uruchamiania wystąpień kompletnych przy użyciu istniejącej definicji. W tym temacie przedstawiono omówienie wykonywania usługi <xref:System.ServiceModel.Activities.WorkflowServiceHost>przepływu pracy obok siebie przy użyciu programu .  
  
> [!NOTE]
> Aby pobrać przykład i obejrzeć klip wideo przedstawiający usługę przepływu pracy obok siebie, zobacz [Przechowywanie wersji obok wersji bocznej za pomocą usługi przepływu pracy Xamlx hostowanego](https://go.microsoft.com/fwlink/?LinkId=393746)w sieci Web .  
  
## <a name="hosting-multiple-versions-in-a-workflow-service"></a>Hostowanie wielu wersji w usłudze przepływu pracy  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost>zawiera dwie właściwości, które można skonfigurować tak, aby umożliwić wykonywanie wielu <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> wersji <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>przepływu pracy obok siebie: i . <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A>zawiera obsługiwane wersje usługi przepływu pracy <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> i służy do jednoznacznej identyfikacji każdej usługi przepływu pracy. Odbywa się to przez <xref:System.Activities.WorkflowIdentity> skojarzenie z usługą przepływu pracy. A <xref:System.Activities.WorkflowIdentity> zawiera trzy identyfikujące informacje. <xref:System.Activities.WorkflowIdentity.Name%2A>i <xref:System.Activities.WorkflowIdentity.Version%2A> zawierają nazwę <xref:System.Version> i a i <xref:System.Activities.WorkflowIdentity.Package%2A> są wymagane i jest opcjonalny i może służyć do określenia dodatkowego ciągu zawierającego informacje, takie jak nazwa zestawu lub inne żądane informacje. Każda usługa przepływu pracy <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> zawarta w <xref:System.Activities.WorkflowIdentity>kolekcji musi mieć unikatowy program . A <xref:System.Activities.WorkflowIdentity> jest unikatowa, jeśli którykolwiek z <xref:System.Activities.WorkflowIdentity>jego trzech właściwości różnią się od innego . A `null` <xref:System.Activities.WorkflowIdentity> jest dopuszczalną <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>wartością dla programu , ale tylko jedna `null` <xref:System.Activities.WorkflowIdentity>poprzednia wersja usługi przepływu pracy może mieć plik .  
  
> [!IMPORTANT]
> A <xref:System.Activities.WorkflowIdentity> nie powinny zawierać żadnych danych osobowych (PII). <xref:System.Activities.WorkflowIdentity>składa się z trzech <xref:System.Activities.WorkflowIdentity.Name%2A> <xref:System.String>części: <xref:System.Activities.WorkflowIdentity.Version%2A> <xref:System.Version>a ( <xref:System.Activities.WorkflowIdentity.Package%2A> <xref:System.String>), a ( ) i ( ). Informacje o <xref:System.Activities.WorkflowIdentity> używane do utworzenia wystąpienia są emitowane do wszystkich skonfigurowanych usług śledzenia w kilku różnych punktach cyklu życia działania przez środowisko wykonawcze. WF Tracking nie ma żadnego mechanizmu ukrywania informacji umożliwiających identyfikację użytkownika (poufnych danych użytkownika). W związku <xref:System.Activities.WorkflowIdentity> z tym wystąpienie nie powinno zawierać żadnych danych umożliwiających identyfikację użytkownika, ponieważ będą emitowane przez środowisko wykonawcze w rekordach śledzenia i mogą być widoczne dla każdego, kto ma dostęp do wyświetlania rekordów śledzenia.  
  
### <a name="rules-for-hosting-multiple-versions-of-a-workflow-service"></a>Reguły obsługi wielu wersji usługi przepływu pracy  
 Gdy użytkownik dodaje dodatkową wersję <xref:System.ServiceModel.Activities.WorkflowServiceHost>do programu , istnieje kilka warunków, które muszą być spełnione, aby usługa przepływu pracy była hostowana z tym samym zestawem punktów końcowych i opisu. Jeśli którakolwiek z dodatkowych wersji nie <xref:System.ServiceModel.Activities.WorkflowServiceHost> spełniają tych warunków, zgłasza wyjątek, gdy `Open` jest wywoływana. Każda definicja przepływu pracy dostarczona do hosta jako wersja dodatkowa musi spełniać następujące wymagania (gdzie wersja podstawowa jest definicją usługi przepływu pracy, która jest dostarczana konstruktorowi hosta). Dodatkowa wersja przepływu pracy musi:  
  
- Mają taką <xref:System.ServiceModel.Activities.WorkflowService.Name%2A> samą wersję jak podstawowa wersja usługi przepływu pracy.  
  
- Nie może <xref:System.ServiceModel.Activities.Receive> mieć <xref:System.ServiceModel.Activities.SendReply> żadnych lub <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> działań w jego, które nie są w wersji podstawowej i muszą być zgodne z umową operacji.  
  
- Mieć unikalny <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>. Jedna i tylko jedna definicja `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>przepływu pracy może mieć .  
  
 Niektóre zmiany są dozwolone. Następujące elementy mogą się różnić między wersjami:  
  
- Może <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> mieć inną nazwę i pakiet niż wersja podstawowa.  
  
- Wartość <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> może być inna niż wersja podstawowa.  
  
- Może <xref:System.ServiceModel.Activities.WorkflowService.ConfigurationName%2A> być inny niż wersja podstawowa.  
  
- Może <xref:System.ServiceModel.Activities.WorkflowService.ImplementedContracts%2A> być inny niż wersja podstawowa.  
  
### <a name="configuring-the-definitionidentity"></a>Konfigurowanie definicjiTototo  
 Gdy usługa przepływu pracy jest tworzona <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> przy użyciu projektanta przepływu pracy, jest ustawiana przy użyciu okna **Właściwości.** Kliknij poza głównym działaniem usługi w projektancie, aby wybrać usługę przepływu pracy, a następnie wybierz **polecenie Okno właściwości** z menu **Widok.** Wybierz **pozycję Obiekt pracyIdentycyjność** z listy rozwijanej, która pojawia się <xref:System.Activities.WorkflowIdentity> obok **DefinitionIdentity** właściwości, a następnie rozwijać i określić żądane właściwości. W poniższym <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> przykładzie jest <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` skonfigurowany <xref:System.Activities.WorkflowIdentity.Version%2A> `1.0.0.0`z i a . <xref:System.Activities.WorkflowIdentity.Package%2A>jest opcjonalny i `null`w tym przykładzie jest .  
  
 ![Zrzut ekranu przedstawiający właściwość DefinitionIdentity.](./media/side-by-side-versioning-in-workflowservicehost/definitionidentity-property.bmp)  
  
 Gdy usługa przepływu pracy jest hostowana <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> samodzielnie, jest konfigurowana podczas konstruowania usługi przepływu pracy. W <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> poniższym przykładzie jest skonfigurowany z tymi samymi <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` wartościami, co w poprzednim przykładzie, z i <xref:System.Activities.WorkflowIdentity.Name%2A> of `1.0.0.0`.  
  
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
  
 A <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> nie jest wymagane, chociaż tylko jedna wersja usługi przepływu pracy może mieć **wartość null**<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.  
  
> [!NOTE]
> Jest to przydatne, jeśli usługa została <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> wdrożona początkowo bez skonfigurowanej, a następnie tworzona jest zaktualizowana wersja.  
  
### <a name="adding-a-new-version-to-a-web-hosted-workflow-service"></a>Dodawanie nowej wersji do usługi przepływu pracy hostowanego w sieci Web  
 Pierwszym krokiem konfigurowania nowej wersji usługi przepływu pracy w usłudze hostowanego w sieci `App_Code` Web jest utworzenie nowego folderu w folderze o takiej samej nazwie jak plik usługi. Jeśli `xamlx` plik usługi ma `MortgageWorkflow.xamlx`nazwę , folder musi `MortgageWorkflow`mieć nazwę . Umieść kopię `xamlx` pliku oryginalnej usługi w tym folderze i zmień jego `MortgageWorkflowV1.xamlx`nazwę na nową nazwę, na przykład . Wykonuj żądane zmiany <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>w usłudze podstawowej, zaktualizuj jej program, a następnie wdruzuj usługę. W poniższym <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> przykładzie został <xref:System.Activities.WorkflowIdentity.Name%2A> zaktualizowany <xref:System.Activities.WorkflowIdentity.Version%2A> o `2.0.0.0`a `MortgageWorkflow` i a z .  
  
 ![Zrzut ekranu przedstawiający definicjętototolejowość pracyIdentycyjność.](./media/side-by-side-versioning-in-workflowservicehost/definitionidentity-workflowidentity.bmp)  
  
 Po ponownym uruchomieniu usługi poprzednia wersja zostanie automatycznie <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> dodana do kolekcji, `App_Code` ponieważ znajduje się w wyznaczonym podfolderze. Należy zauważyć, że jeśli podstawowa wersja `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> usługi przepływu pracy ma poprzednie wersje nie zostaną dodane. Jedna wersja może `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>mieć , ale jeśli istnieje wiele wersji wersji `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> podstawowych nie może być jednym <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> z lub poprzednia wersja nie zostaną dodane do kolekcji.  
  
### <a name="adding-a-new-version-to-a-self-hosted-workflow-service"></a>Dodawanie nowej wersji do usługi samodzielnego hostowania pracy  
 Podczas dodawania nowej wersji do usługi samodzielnego <xref:System.ServiceModel.Activities.WorkflowServiceHost> hostowania przepływu pracy jest skonfigurowany z podstawową wersją usługi przepływu <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> pracy, a poprzednie wersje muszą być jawnie dodane do kolekcji. W poniższym przykładzie jest skonfigurowany z podstawową <xref:System.ServiceModel.Activities.WorkflowServiceHost> usługą przepływu pracy, która używa definicji przepływu `MortgageWorkflowV2` pracy, a usługa przepływu pracy skonfigurowana z definicją `MortgageWorkflowV1` przepływu pracy jest dodawana do <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> kolekcji. Każda usługa przepływu pracy jest <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> skonfigurowana z unikatową, która odzwierciedla wersję definicji przepływu pracy.  
  
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
