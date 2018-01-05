---
title: "Równoległe przechowywanie wersji w klasie WorkflowServiceHost"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 60887eed-df40-4412-b812-41e1dd329d15
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: db8f79fcdc1398b891933f5fef9f07410e5de11e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="side-by-side-versioning-in-workflowservicehost"></a>Równoległe przechowywanie wersji w klasie WorkflowServiceHost
<xref:System.ServiceModel.Activities.WorkflowServiceHost> Wprowadzone w systemie kontroli wersji side-by-side [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)] oferuje możliwość obsługi wielu wersji usługi przepływu pracy w jednym punkcie końcowym. Funkcjonalność side-by-side umożliwia usłudze przepływu pracy można skonfigurować tak, aby nowe wystąpienia usługi przepływu pracy są tworzone przy użyciu nowych definicji przepływu pracy, podczas uruchamiania wystąpienia pełną przy użyciu istniejącej definicji. Ten temat zawiera omówienie sposobu użycia wykonywania side-by-side usługi przepływu pracy <xref:System.ServiceModel.Activities.WorkflowServiceHost>.  
  
> [!NOTE]
>  Aby pobrać przykład i obejrzyj przewodnik wideo dotyczący versioning side-by-side usługi przepływu pracy, zobacz [równoległe przechowywanie wersji usługi przepływu pracy Xamlx Web-Hosted](http://go.microsoft.com/fwlink/?LinkId=393746).  
  
## <a name="hosting-multiple-versions-in-a-workflow-service"></a>Obsługa wielu wersji w usłudze przepływu pracy  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost>zawiera dwie właściwości, które można skonfigurować tak, aby umożliwić wiele wersji przepływu pracy można wykonać side-by-side: <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> i <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>. <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A>zawiera obsługiwane wersje usługi przepływu pracy i <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> jest używany do jednoznacznego identyfikowania poszczególnych usług przepływu pracy. Odbywa się przez skojarzenie <xref:System.Activities.WorkflowIdentity> w usłudze przepływu pracy. A <xref:System.Activities.WorkflowIdentity> zawiera trzy identyfikujące informacje. <xref:System.Activities.WorkflowIdentity.Name%2A>i <xref:System.Activities.WorkflowIdentity.Version%2A> zawiera nazwy i <xref:System.Version> i są wymagane, i <xref:System.Activities.WorkflowIdentity.Package%2A> jest opcjonalna i może służyć do określenia dodatkowych ciąg zawierający informacje, takie jak nazwa zestawu lub inne potrzebne informacje. Każda usługa przepływu pracy zawarte w <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> , Kolekcja musi mieć unikatową <xref:System.Activities.WorkflowIdentity>. A <xref:System.Activities.WorkflowIdentity> jest unikatowa, jeśli żadnego z trzech właściwości różnią się od siebie <xref:System.Activities.WorkflowIdentity>. A `null` <xref:System.Activities.WorkflowIdentity> jest dozwolona wartość dla <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, ale mogą mieć tylko jeden z poprzedniej wersji usługi przepływu pracy `null` <xref:System.Activities.WorkflowIdentity>.  
  
> [!IMPORTANT]
>  A <xref:System.Activities.WorkflowIdentity> nie powinna zawierać żadnych informacji osobistych (dane osobowe). <xref:System.Activities.WorkflowIdentity>składa się z trzech części: <xref:System.Activities.WorkflowIdentity.Name%2A> (<xref:System.String>), <xref:System.Activities.WorkflowIdentity.Version%2A> (<xref:System.Version>), a <xref:System.Activities.WorkflowIdentity.Package%2A> (<xref:System.String>). Informacje o <xref:System.Activities.WorkflowIdentity> użyty do utworzenia wystąpienia jest emitowany do żadnych skonfigurowanych śledzenia cyklu życia usług w wielu różnych punktach działania w czasie wykonywania. WF śledzenia nie ma żadnych mechanizmu, aby ukryć dane osobowe (poufne dane użytkowników). W związku z tym <xref:System.Activities.WorkflowIdentity> wystąpienia nie powinna zawierać żadnych danych dane osobowe, ponieważ zostanie wyemitowany przez środowisko uruchomieniowe w śledzenia rekordów i mogą być widoczne dla każda osoba mająca dostęp do wyświetlania rekordów śledzenia.  
  
### <a name="rules-for-hosting-multiple-versions-of-a-workflow-service"></a>Reguły do obsługi wielu wersji usługi przepływu pracy  
 Gdy użytkownik dodaje dodatkowe wersji do <xref:System.ServiceModel.Activities.WorkflowServiceHost>, istnieje kilka warunków, które muszą zostać spełnione, usługi przepływu pracy ma być obsługiwana z tego samego zestawu punktów końcowych i opis. Jeśli dodatkowe wersje nie spełniają tych warunków <xref:System.ServiceModel.Activities.WorkflowServiceHost> zgłasza wyjątek podczas `Open` jest wywoływana. Każdej definicji przepływu pracy do hosta jako dodatkową wersję musi spełniać następujące wymagania (gdzie głównej wersji jest definicji usługi przepływu pracy, który został dostarczony do konstruktora hosta). Wersja dodatkowe przepływu pracy musi:  
  
-   Tej samej <xref:System.ServiceModel.Activities.WorkflowService.Name%2A> jako głównej wersji usługi przepływu pracy.  
  
-   Nie może mieć <xref:System.ServiceModel.Activities.Receive> lub <xref:System.ServiceModel.Activities.SendReply> działania w jego <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> nie znajdują się w wersji podstawowej i muszą one odpowiadać kontrakt operacji.  
  
-   Ma unikatową <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>. Może mieć tylko jeden definicji przepływu pracy `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.  
  
 Niektóre zmiany są dozwolone. Następujące elementy mogą się różnić między wersjami:  
  
-   <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> Może mieć różne nazwy i pakietu od wersji głównej.  
  
-   <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> Wartość mogą różnić się od wersji głównej.  
  
-   <xref:System.ServiceModel.Activities.WorkflowService.ConfigurationName%2A> Mogą różnić się od wersji głównej.  
  
-   <xref:System.ServiceModel.Activities.WorkflowService.ImplementedContracts%2A> Mogą różnić się od wersji głównej.  
  
### <a name="configuring-the-definitionidentity"></a>Konfigurowanie właściwością definitionidentity o wartości  
 Podczas tworzenia usługi przepływu pracy za pomocą projektanta przepływów pracy <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> jest ustawiany za pomocą **właściwości** okna. Kliknij przycisk poza działania głównego usługi w projektancie, aby wybrać usługi przepływu pracy, a następnie wybierz **okna właściwości** z **widoku** menu. Wybierz **właściwości WorkflowIdentity** z listy rozwijanej obok **właściwością definitionidentity o wartości** właściwości, a następnie rozwiń węzeł i określić żądaną <xref:System.Activities.WorkflowIdentity> właściwości. W poniższym przykładzie <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> skonfigurowano <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` i <xref:System.Activities.WorkflowIdentity.Version%2A> z `1.0.0.0`. <xref:System.Activities.WorkflowIdentity.Package%2A>jest opcjonalna i w tym przykładzie `null`.  
  
 ![Właściwością definitionidentity o wartości](../../../../docs/framework/wcf/feature-details/media/workflowservicedefinitionidentityv1.bmp "WorkflowServiceDefinitionIdentityv1")  
  
 Gdy usługi przepływu pracy jest samodzielnie hostowana, <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> jest skonfigurowana, gdy jest tworzony usługi przepływu pracy. W poniższym przykładzie <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> jest konfigurowana przy użyciu tej samej wartości, co w poprzednim przykładzie <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` i <xref:System.Activities.WorkflowIdentity.Name%2A> z `1.0.0.0`.  
  
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
  
 A <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> nie jest wymagana, chociaż może mieć tylko jedną wersję usługi przepływu pracy **null**<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.  
  
> [!NOTE]
>  Jest to przydatne, jeśli usługa została wdrożona początkowo bez <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> skonfigurowany, a tworzona jest zaktualizowana wersja.  
  
### <a name="adding-a-new-version-to-a-web-hosted-workflow-service"></a>Dodawanie nowej wersji do usługi sieci Web hostowanych przepływu pracy  
 Pierwszym etapem konfigurowania nowej wersji usługi przepływu pracy za pośrednictwem usługi sieci web hostowanych jest można utworzyć nowego folderu w `App_Code` folderu, który ma taką samą nazwę jak plik usługi. Jeśli usługi `xamlx` nosi nazwę pliku `MortgageWorkflow.xamlx`, a następnie folder musi mieć nazwę `MortgageWorkflow`. Umieść kopię oryginalnej usługi `xamlx` pliku do tego folderu i zmień jego nazwę na nową nazwę, taką jak `MortgageWorkflowV1.xamlx`. Wprowadź żądane zmiany do głównej usługi, zaktualizuj jego <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, a następnie wdrożyć usługę. W poniższym przykładzie <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> został zaktualizowany o <xref:System.Activities.WorkflowIdentity.Name%2A> z `MortageWorkflow` i <xref:System.Activities.WorkflowIdentity.Version%2A> z `2.0.0.0`.  
  
 ![Właściwością definitionidentity o wartości](../../../../docs/framework/wcf/feature-details/media/workflowservicedefinitionidentityv2.bmp "WorkflowServiceDefinitionIdentityv2")  
  
 Po ponownym uruchomieniu usługi poprzedniej wersji zostanie automatycznie dodany do <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> kolekcji, ponieważ znajduje się w wyznaczonym `App_Code` podfolderu. Należy pamiętać, że jeśli głównej wersji usługi przepływu pracy `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> poprzednie wersje nie zostaną dodane. Może mieć jedną wersję `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, ale jeśli istnieje wiele wersji głównej wersji nie może być jednym z `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> lub #else poprzednich wersji, nie zostanie dodany do <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> kolekcji.  
  
### <a name="adding-a-new-version-to-a-self-hosted-workflow-service"></a>Dodawanie nowej wersji do usługi hostowanej własnym przepływu pracy  
 Podczas dodawania nowej wersji do usługi hostowanej własnym przepływu pracy, <xref:System.ServiceModel.Activities.WorkflowServiceHost> jest skonfigurowane przy użyciu głównej wersji usługi przepływu pracy i poprzednich wersjach należy jawnie dodać do <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> kolekcji. W poniższym przykładzie <xref:System.ServiceModel.Activities.WorkflowServiceHost> jest skonfigurowany z usługą podstawowy przepływ pracy, który używa `MortgageWorkflowV2` definicji przepływu pracy i skonfigurowano usługi przepływu pracy `MortgageWorkflowV1` definicji przepływu pracy jest dodawany do <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> kolekcji. Każda usługa przepływu pracy jest skonfigurowana przy użyciu unikatowego <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> , które odzwierciedla wersji definicji przepływu pracy.  
  
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
