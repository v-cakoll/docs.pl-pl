---
title: Za pomocą obiektu WorkflowIdentity i wersjonowanie
ms.date: 03/30/2017
ms.assetid: b8451735-8046-478f-912b-40870a6c0c3a
ms.openlocfilehash: 64abab815c523abce88b00515239155499de9c4c
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708174"
---
# <a name="using-workflowidentity-and-versioning"></a><span data-ttu-id="da48c-102">Za pomocą obiektu WorkflowIdentity i wersjonowanie</span><span class="sxs-lookup"><span data-stu-id="da48c-102">Using WorkflowIdentity and Versioning</span></span>
<span data-ttu-id="da48c-103"><xref:System.Activities.WorkflowIdentity> Umożliwia dla przepływu pracy deweloperów aplikacji, aby skojarzyć nazwę i <xref:System.Version> przy użyciu definicji przepływu pracy i te informacje, które ma zostać skojarzony z istniejącym wystąpieniem przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="da48c-103"><xref:System.Activities.WorkflowIdentity> provides a way for workflow application developers to associate a name and a <xref:System.Version> with a workflow definition, and for this information to be associated with a persisted workflow instance.</span></span> <span data-ttu-id="da48c-104">Informacje o tożsamości może służyć przez deweloperów aplikacji przepływu pracy można obsługiwać scenariusze takie jak side-by-side wykonywanie wielu wersji definicji przepływu pracy i zapewnia podstawę dla innych funkcji, takich jak aktualizacja dynamiczna.</span><span class="sxs-lookup"><span data-stu-id="da48c-104">This identity information can be used by workflow application developers to enable scenarios such as side-by-side execution of multiple versions of a workflow definition, and provides the cornerstone for other functionality such as dynamic update.</span></span> <span data-ttu-id="da48c-105">W tym temacie przedstawiono jako omówienie sposobu użycia <xref:System.Activities.WorkflowIdentity> z <xref:System.Activities.WorkflowApplication> hostingu.</span><span class="sxs-lookup"><span data-stu-id="da48c-105">This topic provides as overview of using <xref:System.Activities.WorkflowIdentity> with <xref:System.Activities.WorkflowApplication> hosting.</span></span> <span data-ttu-id="da48c-106">Aby uzyskać informacji na temat wykonywania side-by-side definicji przepływu pracy w usłudze przepływu pracy, zobacz [równoległe przechowywanie wersji w klasie WorkflowServiceHost](../wcf/feature-details/side-by-side-versioning-in-workflowservicehost.md).</span><span class="sxs-lookup"><span data-stu-id="da48c-106">For information on side-by-side execution of workflow definitions in a workflow service, see [Side by Side Versioning in WorkflowServiceHost](../wcf/feature-details/side-by-side-versioning-in-workflowservicehost.md).</span></span> <span data-ttu-id="da48c-107">Aby uzyskać informacji na temat aktualizacji dynamicznej, zobacz [aktualizacji dynamicznej](dynamic-update.md).</span><span class="sxs-lookup"><span data-stu-id="da48c-107">For information on dynamic update, see [Dynamic Update](dynamic-update.md).</span></span>  
  
## <a name="in-this-topic"></a><span data-ttu-id="da48c-108">W tym temacie:</span><span class="sxs-lookup"><span data-stu-id="da48c-108">In this topic</span></span>  
  
-   [<span data-ttu-id="da48c-109">Za pomocą obiektu WorkflowIdentity</span><span class="sxs-lookup"><span data-stu-id="da48c-109">Using WorkflowIdentity</span></span>](using-workflowidentity-and-versioning.md#UsingWorkflowIdentity)  
  
    -   [<span data-ttu-id="da48c-110">Wykonanie Side-by-side przy użyciu obiektu WorkflowIdentity</span><span class="sxs-lookup"><span data-stu-id="da48c-110">Side-by-side Execution using WorkflowIdentity</span></span>](using-workflowidentity-and-versioning.md#SxS)  
  
-   [<span data-ttu-id="da48c-111">Uaktualnianie platformy .NET Framework 4 trwałości baz danych w celu obsługi wersji przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="da48c-111">Upgrading .NET Framework 4 Persistence Databases to Support Workflow Versioning</span></span>](using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases)  
  
    -   [<span data-ttu-id="da48c-112">Aby uaktualnić schemat bazy danych</span><span class="sxs-lookup"><span data-stu-id="da48c-112">To upgrade the database schema</span></span>](using-workflowidentity-and-versioning.md#ToUpgrade)  
  
## <a name="UsingWorkflowIdentity"></a> <span data-ttu-id="da48c-113">Za pomocą obiektu WorkflowIdentity</span><span class="sxs-lookup"><span data-stu-id="da48c-113">Using WorkflowIdentity</span></span>  
 <span data-ttu-id="da48c-114">Aby użyć <xref:System.Activities.WorkflowIdentity>, Utwórz wystąpienie, jest skonfigurowana i skojarz ją z <xref:System.Activities.WorkflowApplication> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="da48c-114">To use <xref:System.Activities.WorkflowIdentity>, create an instance, configure it, and associate it with a <xref:System.Activities.WorkflowApplication> instance.</span></span> <span data-ttu-id="da48c-115">A <xref:System.Activities.WorkflowIdentity> wystąpienie zawiera trzy identyfikujące informacje.</span><span class="sxs-lookup"><span data-stu-id="da48c-115">A <xref:System.Activities.WorkflowIdentity> instance contains three identifying pieces of information.</span></span> <span data-ttu-id="da48c-116"><xref:System.Activities.WorkflowIdentity.Name%2A> i <xref:System.Activities.WorkflowIdentity.Version%2A> zawiera nazwy i <xref:System.Version> i są wymagane, i <xref:System.Activities.WorkflowIdentity.Package%2A> jest opcjonalna i może służyć do określenia dodatkowych ciąg zawierający informacje, takie jak nazwa zestawu lub inne żądane informacje.</span><span class="sxs-lookup"><span data-stu-id="da48c-116"><xref:System.Activities.WorkflowIdentity.Name%2A> and <xref:System.Activities.WorkflowIdentity.Version%2A> contain a name and a <xref:System.Version> and are required, and <xref:System.Activities.WorkflowIdentity.Package%2A> is optional and can be used to specify an additional string containing information such as assembly name or other desired information.</span></span> <span data-ttu-id="da48c-117">A <xref:System.Activities.WorkflowIdentity> są unikatowe, jeśli dowolny z jego trzy właściwości różnią się od innego <xref:System.Activities.WorkflowIdentity>.</span><span class="sxs-lookup"><span data-stu-id="da48c-117">A <xref:System.Activities.WorkflowIdentity> is unique if any of its three properties are different from another <xref:System.Activities.WorkflowIdentity>.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="da48c-118">Element <xref:System.Activities.WorkflowIdentity> nie może zawierać wszelkie identyfikowalne dane osobowe (PII).</span><span class="sxs-lookup"><span data-stu-id="da48c-118">A <xref:System.Activities.WorkflowIdentity> should not contain any personally identifiable information (PII).</span></span> <span data-ttu-id="da48c-119">Informacje o <xref:System.Activities.WorkflowIdentity> użyty do utworzenia wystąpienia jest emitowany do żadnych skonfigurowanych śledzenia cyklu życia usługi w wielu różnych punktach działania w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="da48c-119">Information about the <xref:System.Activities.WorkflowIdentity> used to create an instance is emitted to any configured tracking services at several different points of the activity life-cycle by the runtime.</span></span> <span data-ttu-id="da48c-120">WF śledzenia nie ma żadnych mechanizmu, aby ukryć dane osobowe (poufne dane użytkowników).</span><span class="sxs-lookup"><span data-stu-id="da48c-120">WF Tracking does not have any mechanism to hide PII (sensitive user data).</span></span> <span data-ttu-id="da48c-121">W związku z tym <xref:System.Activities.WorkflowIdentity> wystąpienia nie powinna zawierać wszystkie dane osobowe, ponieważ będzie emitowane przez środowisko uruchomieniowe w rekordy śledzenia i mogą być widoczne dla każda osoba mająca dostęp do wyświetlania rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="da48c-121">Therefore, a <xref:System.Activities.WorkflowIdentity> instance should not contain any PII data as it will be emitted by the runtime in tracking records and may be visible to anyone with access to view the tracking records.</span></span>  
  
 <span data-ttu-id="da48c-122">W poniższym przykładzie <xref:System.Activities.WorkflowIdentity> skojarzonego z wystąpieniem przepływu pracy utworzony za pomocą `MortgageWorkflow` definicji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="da48c-122">In the following example, a <xref:System.Activities.WorkflowIdentity> is created and associated with an instance of a workflow created using a `MortgageWorkflow` workflow definition.</span></span>  
  
```csharp  
WorkflowIdentity identityV1 = new WorkflowIdentity  
{  
    Name = "MortgageWorkflow v1",  
    Version = new Version(1, 0, 0, 0)  
};  
  
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identity);  
  
// Configure the WorkflowApplication with persistence and desired workflow event handlers.  
ConfigureWorkflowApplication(wfApp);  
  
// Run the workflow.  
wfApp.Run();  
```  
  
 <span data-ttu-id="da48c-123">Podczas ponownego ładowania i wznawianie przepływu pracy, <xref:System.Activities.WorkflowIdentity> skonfigurowanego do dopasowania <xref:System.Activities.WorkflowIdentity> utrwalonych przepływu pracy można użyć wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="da48c-123">When reloading and resuming a workflow, a <xref:System.Activities.WorkflowIdentity> that is configured to match the <xref:System.Activities.WorkflowIdentity> of the persisted workflow instance must be used.</span></span>  
  
```csharp  
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identityV1);  
  
// Configure the WorkflowApplication with persistence and desired workflow event handlers.  
ConfigureWorkflowApplication(wfApp);  
  
// Load the workflow.  
wfApp.Load(instanceId);  
  
// Resume the workflow...  
```  
  
 <span data-ttu-id="da48c-124">Jeśli <xref:System.Activities.WorkflowIdentity> używany, gdy ponownie załadować wystąpienia przepływu pracy nie odpowiada utrwalonych <xref:System.Activities.WorkflowIdentity>, <xref:System.Activities.VersionMismatchException> zgłaszany.</span><span class="sxs-lookup"><span data-stu-id="da48c-124">If the <xref:System.Activities.WorkflowIdentity> used when reloading the workflow instance does not match the persisted <xref:System.Activities.WorkflowIdentity>, a <xref:System.Activities.VersionMismatchException> is thrown.</span></span> <span data-ttu-id="da48c-125">W poniższym przykładzie jest podejmowana próba załadowania `MortgageWorkflow` wystąpienia, który został zachowany w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="da48c-125">In the following example a load attempt is made on the `MortgageWorkflow` instance that was persisted in the previous example.</span></span> <span data-ttu-id="da48c-126">Ta próba załadowania zostało nawiązane za pomocą <xref:System.Activities.WorkflowIdentity> skonfigurowany do nowszej wersji hipoteczny przepływu pracy, który nie pasuje do utrwalonego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="da48c-126">This load attempt is made using a <xref:System.Activities.WorkflowIdentity> configured for a newer version of the mortgage workflow that does not match the persisted instance.</span></span>  
  
```csharp  
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow_v2(), identityV2);  
  
// Configure the WorkflowApplication with persistence and desired workflow event handlers.  
ConfigureWorkflowApplication(wfApp);  
  
// Attempt to load the workflow instance.  
wfApp.Load(instanceId);  
  
// Resume the workflow...  
```  
  
 <span data-ttu-id="da48c-127">Po poprzednim kodzie jest wykonywana, sprawdzanie poniżej <xref:System.Activities.VersionMismatchException> zgłaszany.</span><span class="sxs-lookup"><span data-stu-id="da48c-127">When the previous code is executed, the following <xref:System.Activities.VersionMismatchException> is thrown.</span></span>  
  
 <span data-ttu-id="da48c-128">**Obiektu WorkflowIdentity ("MortgageWorkflow v1; Wersja = 1.0.0.0') załadować wystąpienia nie jest zgodny obiektu WorkflowIdentity ("MortgageWorkflow v2; Wersja =' 2.0.0.0 lub nowszej) z Podana definicja przepływu pracy. Wystąpienie może być załadowany, przy użyciu różnych definicji lub zaktualizować przy użyciu aktualizacji dynamicznej.**</span><span class="sxs-lookup"><span data-stu-id="da48c-128">**The WorkflowIdentity ('MortgageWorkflow v1; Version=1.0.0.0') of the loaded instance does not match the WorkflowIdentity ('MortgageWorkflow v2; Version=2.0.0.0') of the provided workflow definition. The instance can be loaded using a different definition, or updated using Dynamic Update.**</span></span>  
### <a name="SxS"></a> <span data-ttu-id="da48c-129">Wykonanie Side-by-side przy użyciu obiektu WorkflowIdentity</span><span class="sxs-lookup"><span data-stu-id="da48c-129">Side-by-side Execution using WorkflowIdentity</span></span>  
 <span data-ttu-id="da48c-130"><xref:System.Activities.WorkflowIdentity> może służyć do ułatwienia wykonywania wielu wersji przepływu pracy side-by-side.</span><span class="sxs-lookup"><span data-stu-id="da48c-130"><xref:System.Activities.WorkflowIdentity> can be used to facilitate the execution of multiple versions of a workflow side-by-side.</span></span> <span data-ttu-id="da48c-131">Jeden typowy scenariusz jest zmiana wymagań biznesowych w przepływie pracy długoterminowych.</span><span class="sxs-lookup"><span data-stu-id="da48c-131">One common scenario is changing business requirements on a long-running workflow.</span></span> <span data-ttu-id="da48c-132">Wiele wystąpień przepływu pracy może być uruchomiony podczas wdrażania zaktualizowanej wersji.</span><span class="sxs-lookup"><span data-stu-id="da48c-132">Many instances of a workflow could be running when an updated version is deployed.</span></span> <span data-ttu-id="da48c-133">Aplikacja hosta można skonfigurować do użycia definicji przepływu pracy zaktualizowane podczas uruchamiania nowych wystąpień i jest odpowiedzialny za aplikacji hosta w celu umożliwienia definicji przepływu pracy prawidłowe w przypadku wznawiania wystąpień.</span><span class="sxs-lookup"><span data-stu-id="da48c-133">The host application can be configured to use the updated workflow definition when starting new instances, and it is the responsibility of the host application to provide the correct workflow definition when resuming instances.</span></span> <span data-ttu-id="da48c-134"><xref:System.Activities.WorkflowIdentity> może służyć do identyfikowania i dostarczyć pasujących definicji przepływu pracy, gdy wznowienie wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="da48c-134"><xref:System.Activities.WorkflowIdentity> can be used to identify and supply the matching workflow definition when resuming workflow instances.</span></span>  
  
 <span data-ttu-id="da48c-135">Aby pobrać <xref:System.Activities.WorkflowIdentity> z istniejącym wystąpieniem przepływu pracy, <xref:System.Activities.WorkflowApplication.GetInstance%2A> metoda jest używana.</span><span class="sxs-lookup"><span data-stu-id="da48c-135">To retrieve the <xref:System.Activities.WorkflowIdentity> of a persisted workflow instance, the <xref:System.Activities.WorkflowApplication.GetInstance%2A> method is used.</span></span> <span data-ttu-id="da48c-136"><xref:System.Activities.WorkflowApplication.GetInstance%2A> Metoda przyjmuje <xref:System.Activities.WorkflowApplication.Id%2A> z istniejącym wystąpieniem przepływu pracy i <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> , zawierający utrwalonego wystąpienia, a funkcja zwraca <xref:System.Activities.WorkflowApplicationInstance>.</span><span class="sxs-lookup"><span data-stu-id="da48c-136">The <xref:System.Activities.WorkflowApplication.GetInstance%2A> method takes the <xref:System.Activities.WorkflowApplication.Id%2A> of the persisted workflow instance and the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> that contains the persisted instance and returns a <xref:System.Activities.WorkflowApplicationInstance>.</span></span> <span data-ttu-id="da48c-137">A <xref:System.Activities.WorkflowApplicationInstance> zawiera informacje o istniejącym wystąpieniem przepływu pracy, w tym związanych z nią <xref:System.Activities.WorkflowIdentity>.</span><span class="sxs-lookup"><span data-stu-id="da48c-137">A <xref:System.Activities.WorkflowApplicationInstance> contains information about a persisted workflow instance, including its associated <xref:System.Activities.WorkflowIdentity>.</span></span> <span data-ttu-id="da48c-138">To skojarzone <xref:System.Activities.WorkflowIdentity> może służyć przez hosta do dostarczania definicji poprawne przepływu pracy podczas ładowania i wznawianie działania wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="da48c-138">This associated <xref:System.Activities.WorkflowIdentity> can be used by the host to supply the correct workflow definition when loading and resuming the workflow instance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="da48c-139">Wartość null <xref:System.Activities.WorkflowIdentity> jest prawidłowy i może służyć przez hosta do mapy wystąpień, które zostały utrwalone bez skojarzonych <xref:System.Activities.WorkflowIdentity> do definicji prawidłowego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="da48c-139">A null <xref:System.Activities.WorkflowIdentity> is valid, and can be used by the host to map instances that were persisted with no associated <xref:System.Activities.WorkflowIdentity> to the proper workflow definition.</span></span> <span data-ttu-id="da48c-140">Ten scenariusz może wystąpić, gdy aplikacja przepływu pracy nie został początkowo zapisany z wersji przepływu pracy lub gdy aplikacja jest uaktualniany z [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="da48c-140">This scenario can occur when a workflow application was not initially written with workflow versioning, or when an application is upgraded from [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].</span></span> <span data-ttu-id="da48c-141">Aby uzyskać więcej informacji, zobacz [uaktualnianie .NET Framework 4 trwałości baz danych do przechowywania wersji przepływu pracy obsługi](using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases).</span><span class="sxs-lookup"><span data-stu-id="da48c-141">For more information, see [Upgrading .NET Framework 4 Persistence Databases to Support Workflow Versioning](using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases).</span></span>  
  
 <span data-ttu-id="da48c-142">W poniższym przykładzie `Dictionary<WorkflowIdentity, Activity>` służy do kojarzenia <xref:System.Activities.WorkflowIdentity> wystąpień przy użyciu ich pasujących definicji przepływu pracy i przepływu pracy została uruchomiona przy użyciu `MortgageWorkflow` definicji przepływu pracy, który jest skojarzony z `identityV1` <xref:System.Activities.WorkflowIdentity>.</span><span class="sxs-lookup"><span data-stu-id="da48c-142">In the following example a `Dictionary<WorkflowIdentity, Activity>` is used to associate <xref:System.Activities.WorkflowIdentity> instances with their matching workflow definitions, and a workflow is started using the `MortgageWorkflow` workflow definition, which is associated with the `identityV1` <xref:System.Activities.WorkflowIdentity>.</span></span>  
  
```csharp  
WorkflowIdentity identityV1 = new WorkflowIdentity  
{  
    Name = "MortgageWorkflow v1",  
    Version = new Version(1, 0, 0, 0)  
};  
  
WorkflowIdentity identityV2 = new WorkflowIdentity  
{  
    Name = "MortgageWorkflow v2",  
    Version = new Version(2, 0, 0, 0)  
};  
  
Dictionary<WorkflowIdentity, Activity> WorkflowVersionMap = new Dictionary<WorkflowIdentity, Activity>();  
WorkflowVersionMap.Add(identityV1, new MortgageWorkflow());  
WorkflowVersionMap.Add(identityV2, new MortgageWorkflow_v2());  
  
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identityV1);  
  
// Configure the WorkflowApplication with persistence and desired workflow event handlers.  
ConfigureWorkflowApplication(wfApp);  
  
// Run the workflow.  
wfApp.Run();  
```  
  
 <span data-ttu-id="da48c-143">W poniższym przykładzie, informacje o istniejącym wystąpieniem przepływu pracy z poprzedniego przykładu jest pobierany przez wywołanie <xref:System.Activities.WorkflowApplication.GetInstance%2A>i utrwalonych <xref:System.Activities.WorkflowIdentity> informacje są używane do pobierania zgodnych definicji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="da48c-143">In the following example, information about the persisted workflow instance from the previous example is retrieved by calling <xref:System.Activities.WorkflowApplication.GetInstance%2A>, and the persisted <xref:System.Activities.WorkflowIdentity> information is used to retrieve the matching workflow definition.</span></span> <span data-ttu-id="da48c-144">Te informacje są używane do konfigurowania <xref:System.Activities.WorkflowApplication>, a następnie załadowaniu przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="da48c-144">This information is used to configure the <xref:System.Activities.WorkflowApplication>, and then the workflow is loaded.</span></span> <span data-ttu-id="da48c-145">Należy pamiętać, że ponieważ <xref:System.Activities.WorkflowApplication.Load%2A> przeciążenia przyjmującego <xref:System.Activities.WorkflowApplicationInstance> jest używany, <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> który został skonfigurowany na <xref:System.Activities.WorkflowApplicationInstance> jest używany przez <xref:System.Activities.WorkflowApplication> i dlatego jego <xref:System.Activities.WorkflowApplication.InstanceStore%2A> właściwości nie musi być skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="da48c-145">Note that because the <xref:System.Activities.WorkflowApplication.Load%2A> overload that takes the <xref:System.Activities.WorkflowApplicationInstance> is used, the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> that was configured on the <xref:System.Activities.WorkflowApplicationInstance> is used by the <xref:System.Activities.WorkflowApplication> and therefore its <xref:System.Activities.WorkflowApplication.InstanceStore%2A> property does not need to be configured.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="da48c-146">Jeśli <xref:System.Activities.WorkflowApplication.InstanceStore%2A> właściwość jest ustawiona, musi być ona równa o takiej samej <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> wystąpienia używanego przez <xref:System.Activities.WorkflowApplicationInstance> — w przeciwnym razie <xref:System.ArgumentException> zostanie zgłoszony następujący komunikat o błędzie: `The instance is configured with a different InstanceStore than this WorkflowApplication.`.</span><span class="sxs-lookup"><span data-stu-id="da48c-146">If the <xref:System.Activities.WorkflowApplication.InstanceStore%2A> property is set, it must be set with the same <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> instance used by the <xref:System.Activities.WorkflowApplicationInstance> or else an <xref:System.ArgumentException> will be thrown with the following message: `The instance is configured with a different InstanceStore than this WorkflowApplication.`.</span></span>  
  
```csharp  
// Get the WorkflowApplicationInstance of the desired workflow from the specified  
// SqlWorkflowInstanceStore.  
WorkflowApplicationInstance instance = WorkflowApplication.GetInstance(instanceId, store);  
  
// Use the persisted WorkflowIdentity to retrieve the correct workflow  
// definition from the dictionary.  
Activity definition = WorkflowVersionMap[instance.DefinitionIdentity];  
  
WorkflowApplication wfApp = new WorkflowApplication(definition, instance.DefinitionIdentity);  
  
// Configure the WorkflowApplication with persistence and desired workflow event handlers.  
ConfigureWorkflowApplication(wfApp);  
  
// Load the persisted workflow instance.  
wfApp.Load(instance);  
  
// Resume the workflow...  
```  
  
## <a name="UpdatingWF4PersistenceDatabases"></a> <span data-ttu-id="da48c-147">Uaktualnianie platformy .NET Framework 4 trwałości baz danych w celu obsługi wersji przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="da48c-147">Upgrading .NET Framework 4 Persistence Databases to Support Workflow Versioning</span></span>  
 <span data-ttu-id="da48c-148">Skrypt bazy danych SqlWorkflowInstanceStoreSchemaUpgrade.sql znajduje się do uaktualnienia bazy danych trwałości utworzone za pomocą [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] bazy danych skryptów.</span><span class="sxs-lookup"><span data-stu-id="da48c-148">A SqlWorkflowInstanceStoreSchemaUpgrade.sql database script is provided to upgrade persistence databases created using the [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] database scripts.</span></span> <span data-ttu-id="da48c-149">Ten skrypt aktualizacji bazy danych do obsługi nowych możliwości przechowywania wersji wprowadzonych w [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="da48c-149">This script updates the databases to support the new versioning capabilities introduced in [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span> <span data-ttu-id="da48c-150">Wszystkie wystąpienia przepływu pracy utrwalonych w bazach danych są podane wartości wersji domyślnych, a następnie mogą brać udział w realizacji side-by-side i aktualizacji dynamicznej.</span><span class="sxs-lookup"><span data-stu-id="da48c-150">Any persisted workflow instances in the databases are given default versioning values, and can then participate in side-by-side execution and dynamic update.</span></span>  
  
 <span data-ttu-id="da48c-151">Jeśli [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] aplikacji przepływu pracy podejmuje wszystkie operacje trwałości korzystać z nowych funkcji przechowywania wersji dla bazy danych trwałości, który nie został uaktualniony przy użyciu dostarczonego skryptu <xref:System.Runtime.DurableInstancing.InstancePersistenceCommandException> generowany jest komunikat podobny do następującego Komunikat.</span><span class="sxs-lookup"><span data-stu-id="da48c-151">If a [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] workflow application attempts any persistence operations that use the new versioning features on a persistence database which has not been upgraded using the provided script, an <xref:System.Runtime.DurableInstancing.InstancePersistenceCommandException> is thrown with a message similar to the following message.</span></span>  
  
 <span data-ttu-id="da48c-152">**SqlWorkflowInstanceStore ma wersję bazy danych "4.0.0.0". Nie można uruchomić InstancePersistenceCommand "System.Activities.DurableInstancing.CreateWorkflowOwnerWithIdentityCommand" przed tą wersją bazy danych.  Uaktualnij bazę danych do "4.5.0.0".**</span><span class="sxs-lookup"><span data-stu-id="da48c-152">**The SqlWorkflowInstanceStore has a database version of '4.0.0.0'. InstancePersistenceCommand 'System.Activities.DurableInstancing.CreateWorkflowOwnerWithIdentityCommand' cannot be run against this database version.  Please upgrade the database to '4.5.0.0'.**</span></span>  
### <a name="ToUpgrade"></a> <span data-ttu-id="da48c-153">Aby uaktualnić schemat bazy danych</span><span class="sxs-lookup"><span data-stu-id="da48c-153">To upgrade the database schema</span></span>  
  
1.  <span data-ttu-id="da48c-154">Otwórz program SQL Server Management Studio i połącz się z serwera bazy danych trwałości, na przykład **. \SQLEXPRESS**.</span><span class="sxs-lookup"><span data-stu-id="da48c-154">Open SQL Server Management Studio and connect to the persistence database server, for example **.\SQLEXPRESS**.</span></span>  
  
2.  <span data-ttu-id="da48c-155">Wybierz **Otwórz**, **pliku** z **pliku** menu.</span><span class="sxs-lookup"><span data-stu-id="da48c-155">Choose **Open**, **File** from the **File** menu.</span></span> <span data-ttu-id="da48c-156">Przejdź do następującego folderu: `C:\Windows\Microsoft.NET\Framework\4.0.30319\sql\en`</span><span class="sxs-lookup"><span data-stu-id="da48c-156">Browse to the following folder: `C:\Windows\Microsoft.NET\Framework\4.0.30319\sql\en`</span></span>  
  
3.  <span data-ttu-id="da48c-157">Wybierz **SqlWorkflowInstanceStoreSchemaUpgrade.sql** i kliknij przycisk **Otwórz**.</span><span class="sxs-lookup"><span data-stu-id="da48c-157">Select **SqlWorkflowInstanceStoreSchemaUpgrade.sql** and click **Open**.</span></span>  
  
4.  <span data-ttu-id="da48c-158">Wybierz nazwę bazy danych trwałości w **baz danych dostępności** listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="da48c-158">Select the name of the persistence database in the **Available Databases** drop-down.</span></span>  
  
5.  <span data-ttu-id="da48c-159">Wybierz **Execute** z **zapytania** menu.</span><span class="sxs-lookup"><span data-stu-id="da48c-159">Choose **Execute** from the **Query** menu.</span></span>  
  
 <span data-ttu-id="da48c-160">Po wykonaniu kwerendy schemat bazy danych jest uaktualniany, a jeśli to konieczne, można wyświetlić domyślną tożsamość przepływ pracy został przypisany do wystąpienia utrwalonych przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="da48c-160">When the query completes, the database schema is upgraded, and if desired, you can view the default workflow identity that was assigned to the persisted workflow instances.</span></span> <span data-ttu-id="da48c-161">Rozwiń węzeł bazy danych trwałości w **baz danych** węźle **Eksplorator obiektów**, a następnie rozwiń węzeł **widoków** węzła.</span><span class="sxs-lookup"><span data-stu-id="da48c-161">Expand your persistence database in the **Databases** node of the **Object Explorer**, and then expand the **Views** node.</span></span> <span data-ttu-id="da48c-162">Kliknij prawym przyciskiem myszy **System.Activities.DurableInstancing.Instances** i wybierz polecenie **zaznacz 1000 pierwszych wierszy**.</span><span class="sxs-lookup"><span data-stu-id="da48c-162">Right-click **System.Activities.DurableInstancing.Instances** and choose **Select Top 1000 Rows**.</span></span> <span data-ttu-id="da48c-163">Przewiń do końca kolumn i należy pamiętać, że sześciu dodatkowe kolumny do widoku: **IdentityName**, **IdentityPackage**, **kompilacji**, **głównych**, **pomocnicza**, i **poprawki**.</span><span class="sxs-lookup"><span data-stu-id="da48c-163">Scroll to end of the columns and note that there are six additional columns added to the view: **IdentityName**, **IdentityPackage**, **Build**, **Major**, **Minor**, and **Revision**.</span></span> <span data-ttu-id="da48c-164">Utrwalonych przepływów pracy będzie mieć wartość **NULL** dla tych pól, reprezentujący identyfikator przepływu pracy o wartości null.</span><span class="sxs-lookup"><span data-stu-id="da48c-164">Any persisted workflows will have a value of **NULL** for these fields, representing a null workflow identity.</span></span>
