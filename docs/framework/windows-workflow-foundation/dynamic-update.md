---
title: Aktualizacja dynamiczna
ms.date: 03/30/2017
ms.assetid: 8b6ef19b-9691-4b4b-824c-3c651a9db96e
ms.openlocfilehash: dea930de2103a24aa48b1d0a31a3cbf5fc0ae26c
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43867988"
---
# <a name="dynamic-update"></a><span data-ttu-id="06954-102">Aktualizacja dynamiczna</span><span class="sxs-lookup"><span data-stu-id="06954-102">Dynamic Update</span></span>
<span data-ttu-id="06954-103">Aktualizacja dynamiczna udostępnia mechanizm dla przepływu pracy deweloperów aplikacji, aby zaktualizować definicję przepływu pracy z istniejącym wystąpieniem przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="06954-103">Dynamic update provides a mechanism for workflow application developers to update the workflow definition of a persisted workflow instance.</span></span> <span data-ttu-id="06954-104">Może to być do zaimplementowania poprawki, nowe wymagania, lub aby pomieścić nieoczekiwanych zmian.</span><span class="sxs-lookup"><span data-stu-id="06954-104">This can be to implement a bug fix, new requirements, or to accommodate unexpected changes.</span></span> <span data-ttu-id="06954-105">Ten temat zawiera omówienie funkcji aktualizacji dynamicznej wprowadzona w [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="06954-105">This topic provides an overview of the dynamic update functionality introduced in [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span>  
  
## <a name="dynamic-update"></a><span data-ttu-id="06954-106">Aktualizacja dynamiczna</span><span class="sxs-lookup"><span data-stu-id="06954-106">Dynamic Update</span></span>  
 <span data-ttu-id="06954-107">Aby zastosować aktualizacje dynamiczne do utrwalonego wystąpienia przepływu pracy, <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> utworzono, która zawiera instrukcje dla środowiska uruchomieniowego, które opisują sposób modyfikowania utrwalonego wystąpienia przepływu pracy zgodnie ze zmianami żądaną.</span><span class="sxs-lookup"><span data-stu-id="06954-107">To apply dynamic updates to a persisted workflow instance, a <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> is created that contains instructions for the runtime that describe how to modify the persisted workflow instance to reflect the desired changes.</span></span> <span data-ttu-id="06954-108">Po utworzeniu update map zostanie zastosowany do wystąpienia żądaną utrwalonych przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="06954-108">Once the update map is created, it is applied to the desired persisted workflow instances.</span></span> <span data-ttu-id="06954-109">Po zastosowaniu aktualizacji dynamicznej wystąpienia przepływu pracy może wznowić, przy użyciu nowej definicji zaktualizowany przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="06954-109">Once the dynamic update is applied, the workflow instance may be resumed using the new updated workflow definition.</span></span> <span data-ttu-id="06954-110">Istnieją cztery kroki wymagane do tworzenia i stosowania aktualizacji mapy.</span><span class="sxs-lookup"><span data-stu-id="06954-110">There are four steps required to create and apply an update map.</span></span>  
  
1.  [<span data-ttu-id="06954-111">Przygotowanie definicji przepływu pracy dla aktualizacji dynamicznych</span><span class="sxs-lookup"><span data-stu-id="06954-111">Prepare the workflow definition for dynamic update</span></span>](../../../docs/framework/windows-workflow-foundation/dynamic-update.md#Prepare)  
  
2.  [<span data-ttu-id="06954-112">Aktualizowanie definicji przepływu pracy, aby odzwierciedlić żądane zmiany</span><span class="sxs-lookup"><span data-stu-id="06954-112">Update the workflow definition to reflect the desired changes</span></span>](../../../docs/framework/windows-workflow-foundation/dynamic-update.md#Update)  
  
3.  [<span data-ttu-id="06954-113">Tworzenie update map</span><span class="sxs-lookup"><span data-stu-id="06954-113">Create the update map</span></span>](../../../docs/framework/windows-workflow-foundation/dynamic-update.md#Create)  
  
4.  [<span data-ttu-id="06954-114">Zastosuj mapy aktualizacji do wystąpień żądaną utrwalonych przepływów pracy</span><span class="sxs-lookup"><span data-stu-id="06954-114">Apply the update map to the desired persisted workflow instances</span></span>](../../../docs/framework/windows-workflow-foundation/dynamic-update.md#Apply)  
  
> [!NOTE]
>  <span data-ttu-id="06954-115">Należy pamiętać, że kroki od 1 do 3, które obejmują tworzenie mapy aktualizacji, może być odbywa się niezależnie od zastosowania aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="06954-115">Note that steps 1 through 3, which cover the creation of the update map, may be performed independently of applying the update.</span></span> <span data-ttu-id="06954-116">Typowy scenariusz, to, że przepływ pracy dla deweloperów spowoduje utworzenie aktualizacji mapy w trybie offline, a następnie administrator zastosuje aktualizację w późniejszym czasie.</span><span class="sxs-lookup"><span data-stu-id="06954-116">A common scenario that that the workflow developer will create the update map offline, and then an administrator will apply the update at a later time.</span></span>  
  
 <span data-ttu-id="06954-117">Ten temat zawiera omówienie procesu aktualizacji dynamicznej dodawania nowe działanie do utrwalonego wystąpienia skompilowanych Xaml przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="06954-117">This topic provides an overview of the dynamic update process of adding a new activity to a persisted instance of a compiled Xaml workflow.</span></span>  
  
###  <a name="Prepare"></a> <span data-ttu-id="06954-118">Przygotowanie definicji przepływu pracy dla aktualizacji dynamicznych</span><span class="sxs-lookup"><span data-stu-id="06954-118">Prepare the workflow definition for dynamic update</span></span>  
 <span data-ttu-id="06954-119">Pierwszym krokiem w procesie aktualizacja dynamiczna jest przygotowanie definicji żądanego przepływu pracy dla aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="06954-119">The first step in the dynamic update process is to prepare the desired workflow definition for update.</span></span> <span data-ttu-id="06954-120">Jest to realizowane przez wywołanie <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> metody i przekazywanie w definicji przepływu pracy, aby zmodyfikować.</span><span class="sxs-lookup"><span data-stu-id="06954-120">This is done by calling the <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> method and passing in the workflow definition to modify.</span></span> <span data-ttu-id="06954-121">Ta metoda sprawdza poprawność, a następnie przegląda drzewo przepływu pracy, aby zidentyfikować wszystkie obiekty, takie jak działania publiczne i zmienne, które trzeba oznakowane, więc porównania później z definicji przepływu pracy zmodyfikowane.</span><span class="sxs-lookup"><span data-stu-id="06954-121">This method validates and then walks the workflow tree to identify all of the objects such as public activities and variables that need to be tagged so they can be compared later with the modified workflow definition.</span></span> <span data-ttu-id="06954-122">Po jego ukończeniu drzewa przepływu pracy jest sklonowany i dołączony do oryginalnej definicji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="06954-122">When this is complete, the workflow tree is cloned and attached to the original workflow definition.</span></span> <span data-ttu-id="06954-123">Po utworzeniu update map zaktualizowanej wersji definicji przepływu pracy jest porównywana z oryginalnej definicji przepływu pracy i mapy aktualizacji jest generowana na temat różnic.</span><span class="sxs-lookup"><span data-stu-id="06954-123">When the update map is created, the updated version of the workflow definition is compared with the original workflow definition and the update map is generated based on the differences.</span></span>  
  
 <span data-ttu-id="06954-124">Aby przygotować Xaml przepływu pracy dla aktualizacji dynamicznych, które mogą zostać załadowane do <xref:System.Activities.ActivityBuilder>, a następnie <xref:System.Activities.ActivityBuilder> jest przekazywana do <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="06954-124">To prepare a Xaml workflow for dynamic update it may be loaded into an <xref:System.Activities.ActivityBuilder>, and then the <xref:System.Activities.ActivityBuilder> is passed into <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="06954-125">Aby uzyskać więcej informacji na temat pracy z usługą serializacji przepływów pracy i <xref:System.Activities.ActivityBuilder>, zobacz [serializowanie przepływów pracy i działań do i z XAML](../../../docs/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="06954-125">For more information about working with serialized workflows and <xref:System.Activities.ActivityBuilder>, see [Serializing Workflows and Activities to and from XAML](../../../docs/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml.md).</span></span>  
  
 <span data-ttu-id="06954-126">W poniższym przykładzie `MortgageWorkflow` definicji (składający się z <xref:System.Activities.Statements.Sequence> z kilku działań podrzędnych) jest ładowany do <xref:System.Activities.ActivityBuilder>, a następnie przygotowane na potrzeby aktualizacji dynamicznej.</span><span class="sxs-lookup"><span data-stu-id="06954-126">In the following example, a `MortgageWorkflow` definition (that consists of a <xref:System.Activities.Statements.Sequence> with several child activities) is loaded into an <xref:System.Activities.ActivityBuilder>, and then prepared for dynamic update.</span></span> <span data-ttu-id="06954-127">Po powrocie z metody, <xref:System.Activities.ActivityBuilder> zawiera oryginalnej definicji przepływu pracy, a także kopię.</span><span class="sxs-lookup"><span data-stu-id="06954-127">After the method returns, the <xref:System.Activities.ActivityBuilder> contains the original workflow definition as well as a copy.</span></span>  
  
```csharp  
// Load the MortgageWorkflow definition from Xaml into  
// an ActivityBuilder.  
XamlXmlReaderSettings readerSettings = new XamlXmlReaderSettings()  
{  
    LocalAssembly = Assembly.GetExecutingAssembly()  
};  
  
XamlXmlReader xamlReader = new XamlXmlReader(@"C:\WorkflowDefitinions\MortgageWorkflow.xaml",   
    readerSettings);  
  
ActivityBuilder ab = XamlServices.Load(  
    ActivityXamlServices.CreateBuilderReader(xamlReader)) as ActivityBuilder;  
  
// Prepare the workflow definition for dynamic update.  
DynamicUpdateServices.PrepareForUpdate(ab);  
```  
  
> [!NOTE]
>  <span data-ttu-id="06954-128">Aby pobrać przykładowy kod, który towarzyszy w tym temacie, zobacz [aktualizacja dynamiczna przykładowy kod](https://go.microsoft.com/fwlink/?LinkId=227905).</span><span class="sxs-lookup"><span data-stu-id="06954-128">To download the sample code that accompanies this topic, see [Dynamic Update sample code](https://go.microsoft.com/fwlink/?LinkId=227905).</span></span>  
  
###  <a name="Update"></a> <span data-ttu-id="06954-129">Aktualizowanie definicji przepływu pracy, aby odzwierciedlić żądane zmiany</span><span class="sxs-lookup"><span data-stu-id="06954-129">Update the workflow definition to reflect the desired changes</span></span>  
 <span data-ttu-id="06954-130">Po definicji przepływu pracy zostało przygotowane do aktualizacji, odpowiednich zmian będzie możliwe.</span><span class="sxs-lookup"><span data-stu-id="06954-130">Once the workflow definition has been prepared for updating, the desired changes can be made.</span></span> <span data-ttu-id="06954-131">Możesz można dodać lub usunąć działania, Dodaj, przenieść lub usunąć publiczny zmiennych, Dodaj lub usuń argumenty i wprowadzić zmiany w podpisie działania delegatach.</span><span class="sxs-lookup"><span data-stu-id="06954-131">You can add or remove activities, add, move or delete public variables, add or remove arguments, and make changes to the signature of activity delegates.</span></span> <span data-ttu-id="06954-132">Nie można usunąć uruchomione działanie ani zmienić podpis delegata uruchomione.</span><span class="sxs-lookup"><span data-stu-id="06954-132">You cannot remove a running activity or change the signature of a running delegate.</span></span> <span data-ttu-id="06954-133">Te zmiany mogą być nawiązywane przy użyciu kodu, lub w Projektancie ponownie hostowanej przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="06954-133">These changes may be made using code, or in a re-hosted workflow designer.</span></span> <span data-ttu-id="06954-134">W poniższym przykładzie niestandardową `VerifyAppraisal` dodaniu działania do sekwencji, tworzącą treści `MortgageWorkflow` z poprzedniego przykładu.</span><span class="sxs-lookup"><span data-stu-id="06954-134">In the following example, a custom `VerifyAppraisal` activity is added to the Sequence that makes up the body of the `MortgageWorkflow` from the previous example.</span></span>  
  
```csharp  
// Make desired changes to the definition. In this example, we are  
// inserting a new VerifyAppraisal activity as the 3rd child of the root Sequence.  
VerifyAppraisal va = new VerifyAppraisal  
{  
    Result = new VisualBasicReference<bool>("LoanCriteria")  
};  
  
// Get the Sequence that makes up the body of the workflow.  
Sequence s = ab.Implementation as Sequence;  
  
// Insert the new activity into the Sequence.  
s.Activities.Insert(2, va);  
```  
  
###  <a name="Create"></a> <span data-ttu-id="06954-135">Tworzenie update map</span><span class="sxs-lookup"><span data-stu-id="06954-135">Create the update map</span></span>  
 <span data-ttu-id="06954-136">Po definicji przepływu pracy, który został przygotowany dla aktualizacji został zmodyfikowany, można utworzyć mapy aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="06954-136">Once the workflow definition that was prepared for update has been modified, the update map can be created.</span></span> <span data-ttu-id="06954-137">Aby utworzyć mapę aktualizacja dynamiczna <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="06954-137">To create a dynamic update map, the <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> method is invoked.</span></span> <span data-ttu-id="06954-138">Spowoduje to zwrócenie <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> zawierający informacje środowiska uruchomieniowego trzeba zmodyfikować utrwalonego wystąpienia przepływu pracy, który może być załadowany i wznowiono z użyciem nową definicję przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="06954-138">This returns a <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> that contains the information the runtime needs to modify a persisted workflow instance so that it may be loaded and resumed with the new workflow definition.</span></span> <span data-ttu-id="06954-139">W poniższym przykładzie jest tworzony dynamicznej mapy dla zmodyfikowanego `MortgageWorkflow` definicji z poprzedniego przykładu.</span><span class="sxs-lookup"><span data-stu-id="06954-139">In the following example, a dynamic map is created for the modified `MortgageWorkflow` definition from the previous example.</span></span>  
  
```csharp  
// Create the update map.  
DynamicUpdateMap map = DynamicUpdateServices.CreateUpdateMap(ab);  
```  
  
 <span data-ttu-id="06954-140">Tę mapę aktualizacji natychmiast może służyć do modyfikowania wystąpienia utrwalonych przepływu pracy, lub zazwyczaj można zapisać i później stosowane aktualizacje.</span><span class="sxs-lookup"><span data-stu-id="06954-140">This update map can immediately be used to modify persisted workflow instances, or more typically it can be saved and the updates applied later.</span></span> <span data-ttu-id="06954-141">Jednym ze sposobów, aby zapisać mapy aktualizacji ma serializować go do pliku, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="06954-141">One way to save the update map is to serialize it to a file, as shown in the following example.</span></span>  
  
```csharp  
// Serialize the update map to a file.  
DataContractSerializer serializer = new DataContractSerializer(typeof(DynamicUpdateMap));  
using (FileStream fs = System.IO.File.Open(@"C:\WorkflowDefitinions\MortgageWorkflow.map", FileMode.Create))  
{  
    serializer.WriteObject(fs, map);  
}  
```  
  
 <span data-ttu-id="06954-142">Gdy <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> zwraca definicji sklonowany przepływu pracy i inne informacje aktualizacja dynamiczna, która została dodana w wywołaniu <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> zostanie usunięty, i definicji modyfikacji przepływu pracy jest gotowa do zapisania tak, aby go można korzystać później podczas wznawianie zaktualizować wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="06954-142">When <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> returns, the cloned workflow definition and other dynamic update information that was added in the call to <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> is removed, and the modified workflow definition is ready to be saved so that it can be used later when resuming updated workflow instances.</span></span> <span data-ttu-id="06954-143">W poniższym przykładzie jest zapisywana definicja przepływu pracy zmodyfikowane `MortgageWorkflow_v2.xaml`.</span><span class="sxs-lookup"><span data-stu-id="06954-143">In the following example, the modified workflow definition is saved to `MortgageWorkflow_v2.xaml`.</span></span>  
  
```csharp  
// Save the modified workflow definition.  
StreamWriter sw = File.CreateText(@"C:\WorkflowDefitinions\MortgageWorkflow_v1.1.xaml");  
XamlWriter xw = ActivityXamlServices.CreateBuilderWriter(new XamlXmlWriter(sw, new XamlSchemaContext()));  
XamlServices.Save(xw, ab);  
sw.Close();  
```  
  
###  <a name="Apply"></a> <span data-ttu-id="06954-144">Zastosuj mapy aktualizacji do wystąpień żądaną utrwalonych przepływów pracy</span><span class="sxs-lookup"><span data-stu-id="06954-144">Apply the update map to the desired persisted workflow instances</span></span>  
 <span data-ttu-id="06954-145">Stosowanie aktualizacji mapy może odbywać się w dowolnym momencie po jej utworzeniu.</span><span class="sxs-lookup"><span data-stu-id="06954-145">Applying the update map can be done at any time after creating it.</span></span> <span data-ttu-id="06954-146">Możesz to zrobić, następnie od razu przy użyciu <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> wystąpienia, który został zwrócony przez <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType>, lub można to zrobić później za pomocą zapisana kopia mapowania aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="06954-146">It can be done right away using the <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> instance that was returned by <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType>, or it can be done later using a saved copy of the update map.</span></span> <span data-ttu-id="06954-147">Aby zaktualizować wystąpienia przepływu pracy, załadować go do <xref:System.Activities.WorkflowApplicationInstance> przy użyciu <xref:System.Activities.WorkflowApplication.GetInstance%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="06954-147">To update a workflow instance, load it into a <xref:System.Activities.WorkflowApplicationInstance> using <xref:System.Activities.WorkflowApplication.GetInstance%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="06954-148">Następnie należy utworzyć <xref:System.Activities.WorkflowApplication> przy użyciu definicji przepływu pracy zaktualizowane i żądany <xref:System.Activities.WorkflowIdentity>.</span><span class="sxs-lookup"><span data-stu-id="06954-148">Next, create a <xref:System.Activities.WorkflowApplication> using the updated workflow definition, and the desired <xref:System.Activities.WorkflowIdentity>.</span></span> <span data-ttu-id="06954-149">To <xref:System.Activities.WorkflowIdentity> może być inny niż ten, który został użyty do utrwalenia oryginalny przepływ pracy i jest zazwyczaj w celu odzwierciedlenia czy utrwalonego wystąpienia zostały zmodyfikowane.</span><span class="sxs-lookup"><span data-stu-id="06954-149">This <xref:System.Activities.WorkflowIdentity> may be different than the one that was used to persist the original workflow, and typically is in order to reflect that the persisted instance has been modified.</span></span> <span data-ttu-id="06954-150">Raz <xref:System.Activities.WorkflowApplication> jest utworzony, jest on ładowany za pomocą przeciążenia <xref:System.Activities.WorkflowApplication.Load%2A?displayProperty=nameWithType> przyjmującej <xref:System.Activities.DynamicUpdate.DynamicUpdateMap>, a następnie zostały zwolnione w wyniku wywołania <xref:System.Activities.WorkflowApplication.Unload%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="06954-150">Once the <xref:System.Activities.WorkflowApplication> is created, it is loaded using the overload of <xref:System.Activities.WorkflowApplication.Load%2A?displayProperty=nameWithType> that takes a <xref:System.Activities.DynamicUpdate.DynamicUpdateMap>, and then unloaded with a call to <xref:System.Activities.WorkflowApplication.Unload%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="06954-151">To ma zastosowanie aktualizacja dynamiczna i będzie się powtarzał wystąpienia zaktualizowanego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="06954-151">This applies the dynamic update and persists the updated workflow instance.</span></span>  
  
```csharp  
// Load the serialized update map.  
DynamicUpdateMap map;  
using (FileStream fs = File.Open(@"C:\WorkflowDefitinions\MortgageWorkflow.map", FileMode.Open))  
{  
    DataContractSerializer serializer = new DataContractSerializer(typeof(DynamicUpdateMap));  
    object updateMap = serializer.ReadObject(fs);  
    if (updateMap == null)  
    {  
        throw new ApplicationException("DynamicUpdateMap is null.");  
    }  
  
    map = (DynamicUpdateMap)updateMap;  
}  
  
// Retrieve a list of workflow instance ids that corresponds to the  
// workflow instances to update. This step is the responsibility of  
// the application developer.  
List<Guid> ids = GetPersistedWorkflowIds();  
foreach (Guid id in ids)  
{  
    // Get a proxy to the persisted workflow instance.  
    SqlWorkflowInstanceStore store = new SqlWorkflowInstanceStore(connectionString);  
    WorkflowApplicationInstance instance = WorkflowApplication.GetInstance(id, store);  
  
    // If desired, you can inspect the WorkflowIdentity of the instance  
    // using the DefinitionIdentity property to determine whether to apply  
    // the update.  
    Console.WriteLine(instance.DefinitionIdentity);  
  
    // Create a workflow application. You must specify the updated workflow definition, and  
    // you may provide an updated WorkflowIdentity if desired to reflect the update.  
    WorkflowIdentity identity = new WorkflowIdentity  
    {  
        Name = "MortgageWorkflow v1.1",  
        Version = new Version(1, 1, 0, 0)  
    };  
  
    // Load the persisted workflow instance using the updated workflow definition  
    // and with an updated WorkflowIdentity. In this example the MortgageWorkflow class  
    // contains the updated definition.  
    WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identity);  
  
    // Apply the dynamic update on the loaded instance.                
    wfApp.Load(instance, map);  
  
    // Unload the updated instance.  
    wfApp.Unload();  
}  
```  
  
### <a name="resuming-an-updated-workflow-instance"></a><span data-ttu-id="06954-152">Wznawianie działania wystąpienia przepływu pracy zaktualizowane</span><span class="sxs-lookup"><span data-stu-id="06954-152">Resuming an Updated Workflow Instance</span></span>  
 <span data-ttu-id="06954-153">Po zastosowaniu aktualizacji dynamicznych, może zostać wznowione wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="06954-153">Once dynamic update has been applied, the workflow instance may be resumed.</span></span> <span data-ttu-id="06954-154">Uwaga nowej aktualizacji definicji i <xref:System.Activities.WorkflowIdentity> musi być używana.</span><span class="sxs-lookup"><span data-stu-id="06954-154">Note that the new updated definition and <xref:System.Activities.WorkflowIdentity> must be used.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="06954-155">Aby uzyskać więcej informacji na temat pracy z usługą <xref:System.Activities.WorkflowApplication> i <xref:System.Activities.WorkflowIdentity>, zobacz [przy użyciu obiektu WorkflowIdentity i wersjonowanie](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="06954-155">For more information about working with <xref:System.Activities.WorkflowApplication> and <xref:System.Activities.WorkflowIdentity>, see [Using WorkflowIdentity and Versioning](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md).</span></span>  
  
 <span data-ttu-id="06954-156">W poniższym przykładzie `MortgageWorkflow_v1.1.xaml` przepływu pracy z poprzedniego przykładu został wcześniej skompilowany, a zostanie załadowany i wznowić, przy użyciu definicji przepływu pracy zaktualizowane.</span><span class="sxs-lookup"><span data-stu-id="06954-156">In the following example, the `MortgageWorkflow_v1.1.xaml` workflow from the previous example has been compiled, and is loaded and resumed using the updated workflow definition.</span></span>  
  
```csharp  
// Load the persisted workflow instance using the updated workflow definition  
// and updated WorkflowIdentity.  
WorkflowIdentity identity = new WorkflowIdentity  
{  
    Name = "MortgageWorkflow v1.1",  
    Version = new Version(1, 1, 0, 0)  
};  
  
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identity);  
  
// Configure persistence and desired workflow event handlers.  
// (Omitted for brevity.)  
ConfigureWorkflowApplication(wfApp);  
  
// Load the persisted workflow instance.  
wfApp.Load(InstanceId);  
  
// Resume the workflow.  
// wfApp.ResumeBookmark(...);  
```  
  
> [!NOTE]
>  <span data-ttu-id="06954-157">Aby pobrać przykładowy kod, który towarzyszy w tym temacie, zobacz [aktualizacja dynamiczna przykładowy kod](https://go.microsoft.com/fwlink/?LinkId=227905).</span><span class="sxs-lookup"><span data-stu-id="06954-157">To download the sample code that accompanies this topic, see [Dynamic Update sample code](https://go.microsoft.com/fwlink/?LinkId=227905).</span></span>
