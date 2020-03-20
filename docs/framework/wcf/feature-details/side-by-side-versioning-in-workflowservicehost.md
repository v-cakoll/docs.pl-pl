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
# <a name="side-by-side-versioning-in-workflowservicehost"></a><span data-ttu-id="ef58f-102">Równoległe przechowywanie wersji w klasie WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="ef58f-102">Side by Side Versioning in WorkflowServiceHost</span></span>
<span data-ttu-id="ef58f-103">Wersja <xref:System.ServiceModel.Activities.WorkflowServiceHost> side-by-side wprowadzona w programie .NET Framework 4.5 umożliwia obsługę wielu wersji usługi przepływu pracy w jednym punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="ef58f-103">The <xref:System.ServiceModel.Activities.WorkflowServiceHost> side-by-side versioning introduced in .NET Framework 4.5 provides the capability to host multiple versions of a workflow service on a single endpoint.</span></span> <span data-ttu-id="ef58f-104">Dostępne funkcje side-by-side umożliwiają skonfigurowanie usługi przepływu pracy w taki sposób, aby nowe wystąpienia usługi przepływu pracy były tworzone przy użyciu nowej definicji przepływu pracy, podczas uruchamiania wystąpień kompletnych przy użyciu istniejącej definicji.</span><span class="sxs-lookup"><span data-stu-id="ef58f-104">The side-by-side functionality provided allows a workflow service to be configured so that new instances of the workflow service are created using the new workflow definition, while running instances complete using the existing definition.</span></span> <span data-ttu-id="ef58f-105">W tym temacie przedstawiono omówienie wykonywania usługi <xref:System.ServiceModel.Activities.WorkflowServiceHost>przepływu pracy obok siebie przy użyciu programu .</span><span class="sxs-lookup"><span data-stu-id="ef58f-105">This topic provides an overview of workflow service side-by-side execution using <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ef58f-106">Aby pobrać przykład i obejrzeć klip wideo przedstawiający usługę przepływu pracy obok siebie, zobacz [Przechowywanie wersji obok wersji bocznej za pomocą usługi przepływu pracy Xamlx hostowanego](https://go.microsoft.com/fwlink/?LinkId=393746)w sieci Web .</span><span class="sxs-lookup"><span data-stu-id="ef58f-106">To download a sample and watch a video walkthrough of workflow service side-by-side versioning, see [Side by Side Versioning with a Web-Hosted Xamlx Workflow Service](https://go.microsoft.com/fwlink/?LinkId=393746).</span></span>  
  
## <a name="hosting-multiple-versions-in-a-workflow-service"></a><span data-ttu-id="ef58f-107">Hostowanie wielu wersji w usłudze przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="ef58f-107">Hosting Multiple Versions in a Workflow Service</span></span>  
 <span data-ttu-id="ef58f-108"><xref:System.ServiceModel.Activities.WorkflowServiceHost>zawiera dwie właściwości, które można skonfigurować tak, aby umożliwić wykonywanie wielu <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> wersji <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>przepływu pracy obok siebie: i .</span><span class="sxs-lookup"><span data-stu-id="ef58f-108"><xref:System.ServiceModel.Activities.WorkflowServiceHost> contains two properties that can be configured to allow multiple versions of a workflow to execute side-by-side: <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> and <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span> <span data-ttu-id="ef58f-109"><xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A>zawiera obsługiwane wersje usługi przepływu pracy <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> i służy do jednoznacznej identyfikacji każdej usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="ef58f-109"><xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> contains the supported versions of the workflow service, and <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is used to uniquely identify each workflow service.</span></span> <span data-ttu-id="ef58f-110">Odbywa się to przez <xref:System.Activities.WorkflowIdentity> skojarzenie z usługą przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="ef58f-110">This is done by associating a <xref:System.Activities.WorkflowIdentity> with the workflow service.</span></span> <span data-ttu-id="ef58f-111">A <xref:System.Activities.WorkflowIdentity> zawiera trzy identyfikujące informacje.</span><span class="sxs-lookup"><span data-stu-id="ef58f-111">A <xref:System.Activities.WorkflowIdentity> contains three identifying pieces of information.</span></span> <span data-ttu-id="ef58f-112"><xref:System.Activities.WorkflowIdentity.Name%2A>i <xref:System.Activities.WorkflowIdentity.Version%2A> zawierają nazwę <xref:System.Version> i a i <xref:System.Activities.WorkflowIdentity.Package%2A> są wymagane i jest opcjonalny i może służyć do określenia dodatkowego ciągu zawierającego informacje, takie jak nazwa zestawu lub inne żądane informacje.</span><span class="sxs-lookup"><span data-stu-id="ef58f-112"><xref:System.Activities.WorkflowIdentity.Name%2A> and <xref:System.Activities.WorkflowIdentity.Version%2A> contain a name and a <xref:System.Version> and are required, and <xref:System.Activities.WorkflowIdentity.Package%2A> is optional and can be used to specify an additional string containing information such as assembly name or other desired information.</span></span> <span data-ttu-id="ef58f-113">Każda usługa przepływu pracy <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> zawarta w <xref:System.Activities.WorkflowIdentity>kolekcji musi mieć unikatowy program .</span><span class="sxs-lookup"><span data-stu-id="ef58f-113">Each workflow service contained in the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection must have a unique <xref:System.Activities.WorkflowIdentity>.</span></span> <span data-ttu-id="ef58f-114">A <xref:System.Activities.WorkflowIdentity> jest unikatowa, jeśli którykolwiek z <xref:System.Activities.WorkflowIdentity>jego trzech właściwości różnią się od innego .</span><span class="sxs-lookup"><span data-stu-id="ef58f-114">A <xref:System.Activities.WorkflowIdentity> is unique if any of its three properties are different from another <xref:System.Activities.WorkflowIdentity>.</span></span> <span data-ttu-id="ef58f-115">A `null` <xref:System.Activities.WorkflowIdentity> jest dopuszczalną <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>wartością dla programu , ale tylko jedna `null` <xref:System.Activities.WorkflowIdentity>poprzednia wersja usługi przepływu pracy może mieć plik .</span><span class="sxs-lookup"><span data-stu-id="ef58f-115">A `null` <xref:System.Activities.WorkflowIdentity> is an allowable value for <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, but only one previous version of a workflow service may have a `null` <xref:System.Activities.WorkflowIdentity>.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ef58f-116">A <xref:System.Activities.WorkflowIdentity> nie powinny zawierać żadnych danych osobowych (PII).</span><span class="sxs-lookup"><span data-stu-id="ef58f-116">A <xref:System.Activities.WorkflowIdentity> should not contain any personally identifiable information (PII).</span></span> <span data-ttu-id="ef58f-117"><xref:System.Activities.WorkflowIdentity>składa się z trzech <xref:System.Activities.WorkflowIdentity.Name%2A> <xref:System.String>części: <xref:System.Activities.WorkflowIdentity.Version%2A> <xref:System.Version>a ( <xref:System.Activities.WorkflowIdentity.Package%2A> <xref:System.String>), a ( ) i ( ).</span><span class="sxs-lookup"><span data-stu-id="ef58f-117"><xref:System.Activities.WorkflowIdentity> is composed of three parts: a <xref:System.Activities.WorkflowIdentity.Name%2A> (<xref:System.String>), a <xref:System.Activities.WorkflowIdentity.Version%2A> (<xref:System.Version>), and a <xref:System.Activities.WorkflowIdentity.Package%2A> (<xref:System.String>).</span></span> <span data-ttu-id="ef58f-118">Informacje o <xref:System.Activities.WorkflowIdentity> używane do utworzenia wystąpienia są emitowane do wszystkich skonfigurowanych usług śledzenia w kilku różnych punktach cyklu życia działania przez środowisko wykonawcze.</span><span class="sxs-lookup"><span data-stu-id="ef58f-118">Information about the <xref:System.Activities.WorkflowIdentity> used to create an instance is emitted to any configured tracking services at several different points of the activity life-cycle by the runtime.</span></span> <span data-ttu-id="ef58f-119">WF Tracking nie ma żadnego mechanizmu ukrywania informacji umożliwiających identyfikację użytkownika (poufnych danych użytkownika).</span><span class="sxs-lookup"><span data-stu-id="ef58f-119">WF Tracking does not have any mechanism to hide PII (sensitive user data).</span></span> <span data-ttu-id="ef58f-120">W związku <xref:System.Activities.WorkflowIdentity> z tym wystąpienie nie powinno zawierać żadnych danych umożliwiających identyfikację użytkownika, ponieważ będą emitowane przez środowisko wykonawcze w rekordach śledzenia i mogą być widoczne dla każdego, kto ma dostęp do wyświetlania rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="ef58f-120">Therefore, a <xref:System.Activities.WorkflowIdentity> instance should not contain any PII data as it will be emitted by the runtime in tracking records and may be visible to anyone with access to view the tracking records.</span></span>  
  
### <a name="rules-for-hosting-multiple-versions-of-a-workflow-service"></a><span data-ttu-id="ef58f-121">Reguły obsługi wielu wersji usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="ef58f-121">Rules for Hosting Multiple Versions of a Workflow Service</span></span>  
 <span data-ttu-id="ef58f-122">Gdy użytkownik dodaje dodatkową wersję <xref:System.ServiceModel.Activities.WorkflowServiceHost>do programu , istnieje kilka warunków, które muszą być spełnione, aby usługa przepływu pracy była hostowana z tym samym zestawem punktów końcowych i opisu.</span><span class="sxs-lookup"><span data-stu-id="ef58f-122">When a user adds an additional version to the <xref:System.ServiceModel.Activities.WorkflowServiceHost>, there are several conditions that must be met in order for a workflow service to be hosted with the same set of endpoints and description.</span></span> <span data-ttu-id="ef58f-123">Jeśli którakolwiek z dodatkowych wersji nie <xref:System.ServiceModel.Activities.WorkflowServiceHost> spełniają tych warunków, zgłasza wyjątek, gdy `Open` jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="ef58f-123">If any of the additional versions fail to meet these conditions, the <xref:System.ServiceModel.Activities.WorkflowServiceHost> throws an exception when `Open` is called.</span></span> <span data-ttu-id="ef58f-124">Każda definicja przepływu pracy dostarczona do hosta jako wersja dodatkowa musi spełniać następujące wymagania (gdzie wersja podstawowa jest definicją usługi przepływu pracy, która jest dostarczana konstruktorowi hosta).</span><span class="sxs-lookup"><span data-stu-id="ef58f-124">Each workflow definition provided to the host as an additional version must meet the following requirements (where the primary version is the workflow service definition that is provided to the host constructor).</span></span> <span data-ttu-id="ef58f-125">Dodatkowa wersja przepływu pracy musi:</span><span class="sxs-lookup"><span data-stu-id="ef58f-125">The additional workflow version must:</span></span>  
  
- <span data-ttu-id="ef58f-126">Mają taką <xref:System.ServiceModel.Activities.WorkflowService.Name%2A> samą wersję jak podstawowa wersja usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="ef58f-126">Have the same the <xref:System.ServiceModel.Activities.WorkflowService.Name%2A> as the primary version of the workflow service.</span></span>  
  
- <span data-ttu-id="ef58f-127">Nie może <xref:System.ServiceModel.Activities.Receive> mieć <xref:System.ServiceModel.Activities.SendReply> żadnych lub <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> działań w jego, które nie są w wersji podstawowej i muszą być zgodne z umową operacji.</span><span class="sxs-lookup"><span data-stu-id="ef58f-127">Must not have any <xref:System.ServiceModel.Activities.Receive> or <xref:System.ServiceModel.Activities.SendReply> activities in its <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> that are not in the primary version, and they must match the operation contract.</span></span>  
  
- <span data-ttu-id="ef58f-128">Mieć unikalny <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span><span class="sxs-lookup"><span data-stu-id="ef58f-128">Have a unique <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span> <span data-ttu-id="ef58f-129">Jedna i tylko jedna definicja `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>przepływu pracy może mieć .</span><span class="sxs-lookup"><span data-stu-id="ef58f-129">One and only one workflow definition may have a `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span>  
  
 <span data-ttu-id="ef58f-130">Niektóre zmiany są dozwolone.</span><span class="sxs-lookup"><span data-stu-id="ef58f-130">Some changes are permitted.</span></span> <span data-ttu-id="ef58f-131">Następujące elementy mogą się różnić między wersjami:</span><span class="sxs-lookup"><span data-stu-id="ef58f-131">The following items may be different between the versions:</span></span>  
  
- <span data-ttu-id="ef58f-132">Może <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> mieć inną nazwę i pakiet niż wersja podstawowa.</span><span class="sxs-lookup"><span data-stu-id="ef58f-132">The <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> may have a different Name and Package than the primary version.</span></span>  
  
- <span data-ttu-id="ef58f-133">Wartość <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> może być inna niż wersja podstawowa.</span><span class="sxs-lookup"><span data-stu-id="ef58f-133">The <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> value may be different than the primary version.</span></span>  
  
- <span data-ttu-id="ef58f-134">Może <xref:System.ServiceModel.Activities.WorkflowService.ConfigurationName%2A> być inny niż wersja podstawowa.</span><span class="sxs-lookup"><span data-stu-id="ef58f-134">The <xref:System.ServiceModel.Activities.WorkflowService.ConfigurationName%2A> may be different than the primary version.</span></span>  
  
- <span data-ttu-id="ef58f-135">Może <xref:System.ServiceModel.Activities.WorkflowService.ImplementedContracts%2A> być inny niż wersja podstawowa.</span><span class="sxs-lookup"><span data-stu-id="ef58f-135">The <xref:System.ServiceModel.Activities.WorkflowService.ImplementedContracts%2A> may be different than the primary version.</span></span>  
  
### <a name="configuring-the-definitionidentity"></a><span data-ttu-id="ef58f-136">Konfigurowanie definicjiTototo</span><span class="sxs-lookup"><span data-stu-id="ef58f-136">Configuring the DefinitionIdentity</span></span>  
 <span data-ttu-id="ef58f-137">Gdy usługa przepływu pracy jest tworzona <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> przy użyciu projektanta przepływu pracy, jest ustawiana przy użyciu okna **Właściwości.**</span><span class="sxs-lookup"><span data-stu-id="ef58f-137">When a workflow service is created using the workflow designer, the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is set using the **Properties** window.</span></span> <span data-ttu-id="ef58f-138">Kliknij poza głównym działaniem usługi w projektancie, aby wybrać usługę przepływu pracy, a następnie wybierz **polecenie Okno właściwości** z menu **Widok.**</span><span class="sxs-lookup"><span data-stu-id="ef58f-138">Click outside of the service’s root activity in the designer to select the workflow service, and choose **Properties Window** from the **View** menu.</span></span> <span data-ttu-id="ef58f-139">Wybierz **pozycję Obiekt pracyIdentycyjność** z listy rozwijanej, która pojawia się <xref:System.Activities.WorkflowIdentity> obok **DefinitionIdentity** właściwości, a następnie rozwijać i określić żądane właściwości.</span><span class="sxs-lookup"><span data-stu-id="ef58f-139">Select **WorkflowIdentity** from the drop-down list that appears beside the **DefinitionIdentity** property, and then expand and specify the desired <xref:System.Activities.WorkflowIdentity> properties.</span></span> <span data-ttu-id="ef58f-140">W poniższym <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> przykładzie jest <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` skonfigurowany <xref:System.Activities.WorkflowIdentity.Version%2A> `1.0.0.0`z i a .</span><span class="sxs-lookup"><span data-stu-id="ef58f-140">In the following example the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is configured with the <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` and a <xref:System.Activities.WorkflowIdentity.Version%2A> of `1.0.0.0`.</span></span> <span data-ttu-id="ef58f-141"><xref:System.Activities.WorkflowIdentity.Package%2A>jest opcjonalny i `null`w tym przykładzie jest .</span><span class="sxs-lookup"><span data-stu-id="ef58f-141"><xref:System.Activities.WorkflowIdentity.Package%2A> is optional and in this example is `null`.</span></span>  
  
 ![Zrzut ekranu przedstawiający właściwość DefinitionIdentity.](./media/side-by-side-versioning-in-workflowservicehost/definitionidentity-property.bmp)  
  
 <span data-ttu-id="ef58f-143">Gdy usługa przepływu pracy jest hostowana <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> samodzielnie, jest konfigurowana podczas konstruowania usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="ef58f-143">When a workflow service is self-hosted, the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is configured when the workflow service is constructed.</span></span> <span data-ttu-id="ef58f-144">W <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> poniższym przykładzie jest skonfigurowany z tymi samymi <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` wartościami, co w poprzednim przykładzie, z i <xref:System.Activities.WorkflowIdentity.Name%2A> of `1.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="ef58f-144">In the following example, the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is configured with the same values as the previous example, with the <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` and a <xref:System.Activities.WorkflowIdentity.Name%2A> of `1.0.0.0`.</span></span>  
  
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
  
 <span data-ttu-id="ef58f-145">A <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> nie jest wymagane, chociaż tylko jedna wersja usługi przepływu pracy może mieć **wartość null**<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span><span class="sxs-lookup"><span data-stu-id="ef58f-145">A <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is not required, although only one version of the workflow service may have a **null**<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ef58f-146">Jest to przydatne, jeśli usługa została <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> wdrożona początkowo bez skonfigurowanej, a następnie tworzona jest zaktualizowana wersja.</span><span class="sxs-lookup"><span data-stu-id="ef58f-146">This is useful if the service was deployed initially without a <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> configured, and then an updated version is created.</span></span>  
  
### <a name="adding-a-new-version-to-a-web-hosted-workflow-service"></a><span data-ttu-id="ef58f-147">Dodawanie nowej wersji do usługi przepływu pracy hostowanego w sieci Web</span><span class="sxs-lookup"><span data-stu-id="ef58f-147">Adding a New Version to a Web-hosted Workflow Service</span></span>  
 <span data-ttu-id="ef58f-148">Pierwszym krokiem konfigurowania nowej wersji usługi przepływu pracy w usłudze hostowanego w sieci `App_Code` Web jest utworzenie nowego folderu w folderze o takiej samej nazwie jak plik usługi.</span><span class="sxs-lookup"><span data-stu-id="ef58f-148">The first step in configuring a new version of a workflow service in a web-hosted service is to create a new folder in the `App_Code` folder that has the same name as the service file.</span></span> <span data-ttu-id="ef58f-149">Jeśli `xamlx` plik usługi ma `MortgageWorkflow.xamlx`nazwę , folder musi `MortgageWorkflow`mieć nazwę .</span><span class="sxs-lookup"><span data-stu-id="ef58f-149">If the service’s `xamlx` file is named `MortgageWorkflow.xamlx`, then the folder must be named `MortgageWorkflow`.</span></span> <span data-ttu-id="ef58f-150">Umieść kopię `xamlx` pliku oryginalnej usługi w tym folderze i zmień jego `MortgageWorkflowV1.xamlx`nazwę na nową nazwę, na przykład .</span><span class="sxs-lookup"><span data-stu-id="ef58f-150">Place a copy of the original service’s `xamlx` file into this folder and rename it to a new name, such as `MortgageWorkflowV1.xamlx`.</span></span> <span data-ttu-id="ef58f-151">Wykonuj żądane zmiany <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>w usłudze podstawowej, zaktualizuj jej program, a następnie wdruzuj usługę.</span><span class="sxs-lookup"><span data-stu-id="ef58f-151">Make the desired changes to the primary service, update its <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, and then deploy the service.</span></span> <span data-ttu-id="ef58f-152">W poniższym <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> przykładzie został <xref:System.Activities.WorkflowIdentity.Name%2A> zaktualizowany <xref:System.Activities.WorkflowIdentity.Version%2A> o `2.0.0.0`a `MortgageWorkflow` i a z .</span><span class="sxs-lookup"><span data-stu-id="ef58f-152">In the following example the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> has been updated with a <xref:System.Activities.WorkflowIdentity.Name%2A> of `MortgageWorkflow` and a <xref:System.Activities.WorkflowIdentity.Version%2A> of `2.0.0.0`.</span></span>  
  
 ![Zrzut ekranu przedstawiający definicjętototolejowość pracyIdentycyjność.](./media/side-by-side-versioning-in-workflowservicehost/definitionidentity-workflowidentity.bmp)  
  
 <span data-ttu-id="ef58f-154">Po ponownym uruchomieniu usługi poprzednia wersja zostanie automatycznie <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> dodana do kolekcji, `App_Code` ponieważ znajduje się w wyznaczonym podfolderze.</span><span class="sxs-lookup"><span data-stu-id="ef58f-154">When the service restarts, the previous version will automatically be added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection because it is located in the designated `App_Code` subfolder.</span></span> <span data-ttu-id="ef58f-155">Należy zauważyć, że jeśli podstawowa wersja `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> usługi przepływu pracy ma poprzednie wersje nie zostaną dodane.</span><span class="sxs-lookup"><span data-stu-id="ef58f-155">Note that if the primary version of the workflow service has a `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> the previous versions will not be added.</span></span> <span data-ttu-id="ef58f-156">Jedna wersja może `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>mieć , ale jeśli istnieje wiele wersji wersji `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> podstawowych nie może być jednym <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> z lub poprzednia wersja nie zostaną dodane do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="ef58f-156">One version may have a `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, but if there are multiple versions the primary version must not be the one with the `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> or else the previous versions will not be added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection.</span></span>  
  
### <a name="adding-a-new-version-to-a-self-hosted-workflow-service"></a><span data-ttu-id="ef58f-157">Dodawanie nowej wersji do usługi samodzielnego hostowania pracy</span><span class="sxs-lookup"><span data-stu-id="ef58f-157">Adding a New Version to a Self-hosted Workflow Service</span></span>  
 <span data-ttu-id="ef58f-158">Podczas dodawania nowej wersji do usługi samodzielnego <xref:System.ServiceModel.Activities.WorkflowServiceHost> hostowania przepływu pracy jest skonfigurowany z podstawową wersją usługi przepływu <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> pracy, a poprzednie wersje muszą być jawnie dodane do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="ef58f-158">When adding a new version to a self-hosted workflow service, the <xref:System.ServiceModel.Activities.WorkflowServiceHost> is configured with the primary version of the workflow service, and previous versions must be explicitly added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection.</span></span> <span data-ttu-id="ef58f-159">W poniższym przykładzie jest skonfigurowany z podstawową <xref:System.ServiceModel.Activities.WorkflowServiceHost> usługą przepływu pracy, która używa definicji przepływu `MortgageWorkflowV2` pracy, a usługa przepływu pracy skonfigurowana z definicją `MortgageWorkflowV1` przepływu pracy jest dodawana do <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="ef58f-159">In the following example, a <xref:System.ServiceModel.Activities.WorkflowServiceHost> is configured with a primary workflow service that uses a `MortgageWorkflowV2` workflow definition, and a workflow service configured with a `MortgageWorkflowV1` workflow definition is added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection.</span></span> <span data-ttu-id="ef58f-160">Każda usługa przepływu pracy jest <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> skonfigurowana z unikatową, która odzwierciedla wersję definicji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="ef58f-160">Each workflow service is configured with a unique <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> that reflects the version of the workflow definition.</span></span>  
  
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
