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
# <a name="side-by-side-versioning-in-workflowservicehost"></a><span data-ttu-id="c5f52-102">Równoległe przechowywanie wersji w klasie WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="c5f52-102">Side by Side Versioning in WorkflowServiceHost</span></span>
<span data-ttu-id="c5f52-103"><xref:System.ServiceModel.Activities.WorkflowServiceHost> Równoległe przechowywanie wersji wprowadzone w .NET Framework 4,5 zapewnia możliwość hostowania wielu wersji usługi przepływu pracy w jednym punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="c5f52-103">The <xref:System.ServiceModel.Activities.WorkflowServiceHost> side-by-side versioning introduced in .NET Framework 4.5 provides the capability to host multiple versions of a workflow service on a single endpoint.</span></span> <span data-ttu-id="c5f52-104">Zapewniane funkcje równoczesne umożliwiają skonfigurowanie usługi przepływu pracy w taki sposób, że nowe wystąpienia usługi przepływu pracy są tworzone przy użyciu nowej definicji przepływu pracy, podczas gdy uruchomione wystąpienia są kompletne przy użyciu istniejącej definicji.</span><span class="sxs-lookup"><span data-stu-id="c5f52-104">The side-by-side functionality provided allows a workflow service to be configured so that new instances of the workflow service are created using the new workflow definition, while running instances complete using the existing definition.</span></span> <span data-ttu-id="c5f52-105">Ten temat zawiera omówienie wykonywania równoczesnego usługi przepływu pracy przy użyciu programu <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="c5f52-105">This topic provides an overview of workflow service side-by-side execution using <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c5f52-106">Aby pobrać przykład i obejrzeć film wideo dotyczący obsługi wersji równoległych usługi przepływu pracy, zobacz [obok siebie przechowywanie wersji obok sieci Web xamlx Workflow Service](https://go.microsoft.com/fwlink/?LinkId=393746).</span><span class="sxs-lookup"><span data-stu-id="c5f52-106">To download a sample and watch a video walkthrough of workflow service side-by-side versioning, see [Side by Side Versioning with a Web-Hosted Xamlx Workflow Service](https://go.microsoft.com/fwlink/?LinkId=393746).</span></span>  
  
## <a name="hosting-multiple-versions-in-a-workflow-service"></a><span data-ttu-id="c5f52-107">Hostowanie wielu wersji w usłudze przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="c5f52-107">Hosting Multiple Versions in a Workflow Service</span></span>  
 <span data-ttu-id="c5f52-108"><xref:System.ServiceModel.Activities.WorkflowServiceHost>zawiera dwie właściwości, które można skonfigurować tak, aby umożliwić wykonywanie wielu wersji przepływu pracy obok siebie: <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> i. <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A></span><span class="sxs-lookup"><span data-stu-id="c5f52-108"><xref:System.ServiceModel.Activities.WorkflowServiceHost> contains two properties that can be configured to allow multiple versions of a workflow to execute side-by-side: <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> and <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span> <span data-ttu-id="c5f52-109"><xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A>zawiera obsługiwane wersje usługi przepływu pracy i <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> służy do jednoznacznej identyfikacji każdej usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="c5f52-109"><xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> contains the supported versions of the workflow service, and <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is used to uniquely identify each workflow service.</span></span> <span data-ttu-id="c5f52-110">Jest to realizowane przez skojarzenie <xref:System.Activities.WorkflowIdentity> z usługą przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="c5f52-110">This is done by associating a <xref:System.Activities.WorkflowIdentity> with the workflow service.</span></span> <span data-ttu-id="c5f52-111">A <xref:System.Activities.WorkflowIdentity> zawiera trzy identyfikujące informacje.</span><span class="sxs-lookup"><span data-stu-id="c5f52-111">A <xref:System.Activities.WorkflowIdentity> contains three identifying pieces of information.</span></span> <span data-ttu-id="c5f52-112"><xref:System.Activities.WorkflowIdentity.Name%2A>i <xref:System.Activities.WorkflowIdentity.Version%2A> zawiera nazwę <xref:System.Version> i <xref:System.Activities.WorkflowIdentity.Package%2A> i są wymagane i jest opcjonalne i może służyć do określenia dodatkowego ciągu zawierającego informacje takie jak nazwa zestawu lub inne żądane informacje.</span><span class="sxs-lookup"><span data-stu-id="c5f52-112"><xref:System.Activities.WorkflowIdentity.Name%2A> and <xref:System.Activities.WorkflowIdentity.Version%2A> contain a name and a <xref:System.Version> and are required, and <xref:System.Activities.WorkflowIdentity.Package%2A> is optional and can be used to specify an additional string containing information such as assembly name or other desired information.</span></span> <span data-ttu-id="c5f52-113">Każda usługa przepływu pracy znajdująca <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> się w kolekcji musi mieć <xref:System.Activities.WorkflowIdentity>unikatową wartość.</span><span class="sxs-lookup"><span data-stu-id="c5f52-113">Each workflow service contained in the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection must have a unique <xref:System.Activities.WorkflowIdentity>.</span></span> <span data-ttu-id="c5f52-114">Jest <xref:System.Activities.WorkflowIdentity> unikatowa, jeśli którykolwiek z jego trzech właściwości różni się od <xref:System.Activities.WorkflowIdentity>innego.</span><span class="sxs-lookup"><span data-stu-id="c5f52-114">A <xref:System.Activities.WorkflowIdentity> is unique if any of its three properties are different from another <xref:System.Activities.WorkflowIdentity>.</span></span> <span data-ttu-id="c5f52-115">A `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> `null` jest wartością dozwoloną dla, ale tylko jedna Poprzednia <xref:System.Activities.WorkflowIdentity>wersja usługi przepływu pracy może mieć. <xref:System.Activities.WorkflowIdentity></span><span class="sxs-lookup"><span data-stu-id="c5f52-115">A `null` <xref:System.Activities.WorkflowIdentity> is an allowable value for <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, but only one previous version of a workflow service may have a `null` <xref:System.Activities.WorkflowIdentity>.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c5f52-116">A <xref:System.Activities.WorkflowIdentity> nie powinna zawierać żadnych informacji umożliwiających identyfikację użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c5f52-116">A <xref:System.Activities.WorkflowIdentity> should not contain any personally identifiable information (PII).</span></span> <span data-ttu-id="c5f52-117"><xref:System.Activities.WorkflowIdentity>składa się z trzech części: <xref:System.Activities.WorkflowIdentity.Name%2A> a<xref:System.String>(), <xref:System.Activities.WorkflowIdentity.Version%2A> a<xref:System.Version>() i <xref:System.Activities.WorkflowIdentity.Package%2A> a (<xref:System.String>).</span><span class="sxs-lookup"><span data-stu-id="c5f52-117"><xref:System.Activities.WorkflowIdentity> is composed of three parts: a <xref:System.Activities.WorkflowIdentity.Name%2A> (<xref:System.String>), a <xref:System.Activities.WorkflowIdentity.Version%2A> (<xref:System.Version>), and a <xref:System.Activities.WorkflowIdentity.Package%2A> (<xref:System.String>).</span></span> <span data-ttu-id="c5f52-118">Informacje o <xref:System.Activities.WorkflowIdentity> użytym do utworzenia wystąpienia są emitowane do wszelkich skonfigurowanych usług śledzenia w kilku różnych punktach cyklu życia działania przez środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="c5f52-118">Information about the <xref:System.Activities.WorkflowIdentity> used to create an instance is emitted to any configured tracking services at several different points of the activity life-cycle by the runtime.</span></span> <span data-ttu-id="c5f52-119">Śledzenie WF nie ma żadnego mechanizmu ukrywania danych osobowych (poufne dane użytkownika).</span><span class="sxs-lookup"><span data-stu-id="c5f52-119">WF Tracking does not have any mechanism to hide PII (sensitive user data).</span></span> <span data-ttu-id="c5f52-120">W związku z tym wystąpienieniepowinnozawieraćżadnychdanychosobowych,ponieważbędzieemitowaneprzezśrodowiskouruchomieniowewceluśledzeniarekordówimożebyćwidocznedlakażdego,ktomadostępdowyświetlaniarekordówśledzenia.<xref:System.Activities.WorkflowIdentity></span><span class="sxs-lookup"><span data-stu-id="c5f52-120">Therefore, a <xref:System.Activities.WorkflowIdentity> instance should not contain any PII data as it will be emitted by the runtime in tracking records and may be visible to anyone with access to view the tracking records.</span></span>  
  
### <a name="rules-for-hosting-multiple-versions-of-a-workflow-service"></a><span data-ttu-id="c5f52-121">Reguły hostingu wielu wersji usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="c5f52-121">Rules for Hosting Multiple Versions of a Workflow Service</span></span>  
 <span data-ttu-id="c5f52-122">Gdy użytkownik dodaje do programu <xref:System.ServiceModel.Activities.WorkflowServiceHost>dodatkową wersję, istnieje kilka warunków, które muszą zostać spełnione, aby usługa przepływu pracy była hostowana z tym samym zestawem punktów końcowych i opisem.</span><span class="sxs-lookup"><span data-stu-id="c5f52-122">When a user adds an additional version to the <xref:System.ServiceModel.Activities.WorkflowServiceHost>, there are several conditions that must be met in order for a workflow service to be hosted with the same set of endpoints and description.</span></span> <span data-ttu-id="c5f52-123">Jeśli jakakolwiek z dodatkowych wersji nie spełni tych warunków, <xref:System.ServiceModel.Activities.WorkflowServiceHost> zgłasza wyjątek, gdy `Open` jest wywoływany.</span><span class="sxs-lookup"><span data-stu-id="c5f52-123">If any of the additional versions fail to meet these conditions, the <xref:System.ServiceModel.Activities.WorkflowServiceHost> throws an exception when `Open` is called.</span></span> <span data-ttu-id="c5f52-124">Każda definicja przepływu pracy podana dla hosta jako dodatkowa wersja musi spełniać następujące wymagania (w przypadku których podstawowa wersja jest definicją usługi przepływu pracy dostarczoną do konstruktora hosta).</span><span class="sxs-lookup"><span data-stu-id="c5f52-124">Each workflow definition provided to the host as an additional version must meet the following requirements (where the primary version is the workflow service definition that is provided to the host constructor).</span></span> <span data-ttu-id="c5f52-125">Dodatkowa wersja przepływu pracy musi:</span><span class="sxs-lookup"><span data-stu-id="c5f52-125">The additional workflow version must:</span></span>  
  
- <span data-ttu-id="c5f52-126">Być taka sama <xref:System.ServiceModel.Activities.WorkflowService.Name%2A> jak podstawowa wersja usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="c5f52-126">Have the same the <xref:System.ServiceModel.Activities.WorkflowService.Name%2A> as the primary version of the workflow service.</span></span>  
  
- <span data-ttu-id="c5f52-127">Nie może zawierać żadnych <xref:System.ServiceModel.Activities.Receive> działań <xref:System.ServiceModel.Activities.SendReply> ani w <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> nich, które nie znajdują się w wersji głównej, i muszą być zgodne z kontraktem operacji.</span><span class="sxs-lookup"><span data-stu-id="c5f52-127">Must not have any <xref:System.ServiceModel.Activities.Receive> or <xref:System.ServiceModel.Activities.SendReply> activities in its <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> that are not in the primary version, and they must match the operation contract.</span></span>  
  
- <span data-ttu-id="c5f52-128">Mieć unikatową <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>wartość.</span><span class="sxs-lookup"><span data-stu-id="c5f52-128">Have a unique <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span> <span data-ttu-id="c5f52-129">Jeden i tylko jedna definicja przepływu pracy może mieć `null`. <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A></span><span class="sxs-lookup"><span data-stu-id="c5f52-129">One and only one workflow definition may have a `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span>  
  
 <span data-ttu-id="c5f52-130">Niektóre zmiany są dozwolone.</span><span class="sxs-lookup"><span data-stu-id="c5f52-130">Some changes are permitted.</span></span> <span data-ttu-id="c5f52-131">Następujące elementy mogą się różnić między wersjami:</span><span class="sxs-lookup"><span data-stu-id="c5f52-131">The following items may be different between the versions:</span></span>  
  
- <span data-ttu-id="c5f52-132"><xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> Może mieć inną nazwę i pakiet niż wersja podstawowa.</span><span class="sxs-lookup"><span data-stu-id="c5f52-132">The <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> may have a different Name and Package than the primary version.</span></span>  
  
- <span data-ttu-id="c5f52-133"><xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> Wartość może być inna niż wersja podstawowa.</span><span class="sxs-lookup"><span data-stu-id="c5f52-133">The <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> value may be different than the primary version.</span></span>  
  
- <span data-ttu-id="c5f52-134"><xref:System.ServiceModel.Activities.WorkflowService.ConfigurationName%2A> Może być inna niż wersja podstawowa.</span><span class="sxs-lookup"><span data-stu-id="c5f52-134">The <xref:System.ServiceModel.Activities.WorkflowService.ConfigurationName%2A> may be different than the primary version.</span></span>  
  
- <span data-ttu-id="c5f52-135"><xref:System.ServiceModel.Activities.WorkflowService.ImplementedContracts%2A> Może być inna niż wersja podstawowa.</span><span class="sxs-lookup"><span data-stu-id="c5f52-135">The <xref:System.ServiceModel.Activities.WorkflowService.ImplementedContracts%2A> may be different than the primary version.</span></span>  
  
### <a name="configuring-the-definitionidentity"></a><span data-ttu-id="c5f52-136">Konfigurowanie DefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="c5f52-136">Configuring the DefinitionIdentity</span></span>  
 <span data-ttu-id="c5f52-137">Gdy usługa przepływu pracy jest tworzona przy użyciu projektanta przepływu pracy, <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> jest ustawiana za pomocą okna **Właściwości** .</span><span class="sxs-lookup"><span data-stu-id="c5f52-137">When a workflow service is created using the workflow designer, the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is set using the **Properties** window.</span></span> <span data-ttu-id="c5f52-138">Kliknij poza działaniem głównym usługi w projektancie, aby wybrać usługę przepływu pracy, a następnie wybierz **okno właściwości** z menu **Widok** .</span><span class="sxs-lookup"><span data-stu-id="c5f52-138">Click outside of the service’s root activity in the designer to select the workflow service, and choose **Properties Window** from the **View** menu.</span></span> <span data-ttu-id="c5f52-139">Z listy rozwijanej wybierz pozycję **Właściwości WorkflowIdentity** , która pojawia się obok właściwości **DefinitionIdentity** , a następnie rozwiń i określ żądane <xref:System.Activities.WorkflowIdentity> właściwości.</span><span class="sxs-lookup"><span data-stu-id="c5f52-139">Select **WorkflowIdentity** from the drop-down list that appears beside the **DefinitionIdentity** property, and then expand and specify the desired <xref:System.Activities.WorkflowIdentity> properties.</span></span> <span data-ttu-id="c5f52-140">W poniższym <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> przykładzie jest skonfigurowany `MortgageWorkflow` <xref:System.Activities.WorkflowIdentity.Name%2A> z i <xref:System.Activities.WorkflowIdentity.Version%2A> z.`1.0.0.0`</span><span class="sxs-lookup"><span data-stu-id="c5f52-140">In the following example the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is configured with the <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` and a <xref:System.Activities.WorkflowIdentity.Version%2A> of `1.0.0.0`.</span></span> <span data-ttu-id="c5f52-141"><xref:System.Activities.WorkflowIdentity.Package%2A>jest opcjonalny i w tym przykładzie `null`.</span><span class="sxs-lookup"><span data-stu-id="c5f52-141"><xref:System.Activities.WorkflowIdentity.Package%2A> is optional and in this example is `null`.</span></span>  
  
 ![Zrzut ekranu przedstawiający Właściwość DefinitionIdentity.](./media/side-by-side-versioning-in-workflowservicehost/definitionidentity-property.bmp)  
  
 <span data-ttu-id="c5f52-143">Gdy usługa przepływu pracy jest samoobsługowa, <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> jest konfigurowana podczas konstruowania usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="c5f52-143">When a workflow service is self-hosted, the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is configured when the workflow service is constructed.</span></span> <span data-ttu-id="c5f52-144">W poniższym <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> przykładzie jest skonfigurowany z tymi samymi wartościami jak w poprzednim przykładzie, `MortgageWorkflow` <xref:System.Activities.WorkflowIdentity.Name%2A> z i <xref:System.Activities.WorkflowIdentity.Name%2A> `1.0.0.0`a.</span><span class="sxs-lookup"><span data-stu-id="c5f52-144">In the following example, the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is configured with the same values as the previous example, with the <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` and a <xref:System.Activities.WorkflowIdentity.Name%2A> of `1.0.0.0`.</span></span>  
  
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
  
 <span data-ttu-id="c5f52-145">Element <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> nie jest wymagany, ale tylko jedna wersja usługi przepływu pracy może mieć **wartość null**<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span><span class="sxs-lookup"><span data-stu-id="c5f52-145">A <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is not required, although only one version of the workflow service may have a **null**<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c5f52-146">Jest to przydatne, jeśli usługa została wdrożona początkowo bez <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> skonfigurowanej, a następnie tworzona jest zaktualizowana wersja.</span><span class="sxs-lookup"><span data-stu-id="c5f52-146">This is useful if the service was deployed initially without a <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> configured, and then an updated version is created.</span></span>  
  
### <a name="adding-a-new-version-to-a-web-hosted-workflow-service"></a><span data-ttu-id="c5f52-147">Dodawanie nowej wersji do usługi przepływu pracy hostowanej w sieci Web</span><span class="sxs-lookup"><span data-stu-id="c5f52-147">Adding a New Version to a Web-hosted Workflow Service</span></span>  
 <span data-ttu-id="c5f52-148">Pierwszym krokiem w konfigurowaniu nowej wersji usługi przepływu pracy w usłudze hostowanej w sieci Web jest utworzenie nowego folderu w `App_Code` folderze, który ma taką samą nazwę jak plik usługi.</span><span class="sxs-lookup"><span data-stu-id="c5f52-148">The first step in configuring a new version of a workflow service in a web-hosted service is to create a new folder in the `App_Code` folder that has the same name as the service file.</span></span> <span data-ttu-id="c5f52-149">Jeśli `xamlx` plik usługi ma nazwę `MortgageWorkflow.xamlx`, folder musi mieć nazwę `MortgageWorkflow`.</span><span class="sxs-lookup"><span data-stu-id="c5f52-149">If the service’s `xamlx` file is named `MortgageWorkflow.xamlx`, then the folder must be named `MortgageWorkflow`.</span></span> <span data-ttu-id="c5f52-150">Umieść kopię `xamlx` pliku pierwotnej usługi w tym folderze i zmień jego nazwę na nową nazwę, `MortgageWorkflowV1.xamlx`na przykład.</span><span class="sxs-lookup"><span data-stu-id="c5f52-150">Place a copy of the original service’s `xamlx` file into this folder and rename it to a new name, such as `MortgageWorkflowV1.xamlx`.</span></span> <span data-ttu-id="c5f52-151">Wprowadź odpowiednie zmiany w usłudze głównej, zaktualizuj ją <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, a następnie wdróż usługę.</span><span class="sxs-lookup"><span data-stu-id="c5f52-151">Make the desired changes to the primary service, update its <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, and then deploy the service.</span></span> <span data-ttu-id="c5f52-152">W poniższym <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> przykładzie został zaktualizowany `MortgageWorkflow` <xref:System.Activities.WorkflowIdentity.Name%2A> z i <xref:System.Activities.WorkflowIdentity.Version%2A> a.`2.0.0.0`</span><span class="sxs-lookup"><span data-stu-id="c5f52-152">In the following example the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> has been updated with a <xref:System.Activities.WorkflowIdentity.Name%2A> of `MortgageWorkflow` and a <xref:System.Activities.WorkflowIdentity.Version%2A> of `2.0.0.0`.</span></span>  
  
 ![Zrzut ekranu pokazujący DefinitionIdentity właściwości WorkflowIdentity.](./media/side-by-side-versioning-in-workflowservicehost/definitionidentity-workflowidentity.bmp)  
  
 <span data-ttu-id="c5f52-154">Po ponownym uruchomieniu usługi Poprzednia wersja zostanie automatycznie dodana do <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> kolekcji, ponieważ znajduje się ona w wydzielonym `App_Code` podfolderze.</span><span class="sxs-lookup"><span data-stu-id="c5f52-154">When the service restarts, the previous version will automatically be added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection because it is located in the designated `App_Code` subfolder.</span></span> <span data-ttu-id="c5f52-155">Należy pamiętać, że jeśli podstawowa wersja usługi `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> przepływu pracy nie zostanie dodana do poprzednich wersji.</span><span class="sxs-lookup"><span data-stu-id="c5f52-155">Note that if the primary version of the workflow service has a `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> the previous versions will not be added.</span></span> <span data-ttu-id="c5f52-156">Jedna wersja `null`może mieć <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, ale jeśli istnieje wiele wersji, wersja podstawowa nie może `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> być tą, a w przeciwnym razie poprzednie wersje nie zostaną dodane do <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="c5f52-156">One version may have a `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, but if there are multiple versions the primary version must not be the one with the `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> or else the previous versions will not be added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection.</span></span>  
  
### <a name="adding-a-new-version-to-a-self-hosted-workflow-service"></a><span data-ttu-id="c5f52-157">Dodawanie nowej wersji do samodzielnej usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="c5f52-157">Adding a New Version to a Self-hosted Workflow Service</span></span>  
 <span data-ttu-id="c5f52-158">Podczas dodawania nowej wersji do samodzielnej usługi <xref:System.ServiceModel.Activities.WorkflowServiceHost> przepływu pracy konfiguracja jest konfigurowana z podstawową wersją usługi przepływu pracy, a wcześniejsze wersje muszą zostać jawnie dodane <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="c5f52-158">When adding a new version to a self-hosted workflow service, the <xref:System.ServiceModel.Activities.WorkflowServiceHost> is configured with the primary version of the workflow service, and previous versions must be explicitly added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection.</span></span> <span data-ttu-id="c5f52-159">W poniższym przykładzie <xref:System.ServiceModel.Activities.WorkflowServiceHost> jest konfigurowana za pomocą podstawowej usługi `MortgageWorkflowV2` przepływu pracy korzystającej z definicji przepływu pracy, a usługa `MortgageWorkflowV1` przepływu pracy skonfigurowana za pomocą definicji przepływu pracy jest dodawana do <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="c5f52-159">In the following example, a <xref:System.ServiceModel.Activities.WorkflowServiceHost> is configured with a primary workflow service that uses a `MortgageWorkflowV2` workflow definition, and a workflow service configured with a `MortgageWorkflowV1` workflow definition is added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection.</span></span> <span data-ttu-id="c5f52-160">Dla każdej usługi przepływu pracy jest skonfigurowany unikatowy <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> , który odzwierciedla wersję definicji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="c5f52-160">Each workflow service is configured with a unique <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> that reflects the version of the workflow definition.</span></span>  
  
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
