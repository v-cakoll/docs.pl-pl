---
title: Aktualizacja dynamiczna
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8b6ef19b-9691-4b4b-824c-3c651a9db96e
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0bd320b9875f7ed2d5acb124feb4b7d3bb82d62e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="dynamic-update"></a><span data-ttu-id="b8ea5-102">Aktualizacja dynamiczna</span><span class="sxs-lookup"><span data-stu-id="b8ea5-102">Dynamic Update</span></span>
<span data-ttu-id="b8ea5-103">Aktualizacja dynamiczna udostępnia mechanizm dla przepływu pracy deweloperami aplikacji, aby zaktualizować wystąpienia przepływu pracy utrwalonych definicji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="b8ea5-103">Dynamic update provides a mechanism for workflow application developers to update the workflow definition of a persisted workflow instance.</span></span> <span data-ttu-id="b8ea5-104">Może to być do zaimplementowania poprawkę, nowe wymagania, lub aby pomieścić nieoczekiwane zmiany.</span><span class="sxs-lookup"><span data-stu-id="b8ea5-104">This can be to implement a bug fix, new requirements, or to accommodate unexpected changes.</span></span> <span data-ttu-id="b8ea5-105">Ten temat zawiera omówienie funkcji aktualizacji dynamicznej wprowadzona w systemie [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b8ea5-105">This topic provides an overview of the dynamic update functionality introduced in [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span>  
  
## <a name="dynamic-update"></a><span data-ttu-id="b8ea5-106">Aktualizacja dynamiczna</span><span class="sxs-lookup"><span data-stu-id="b8ea5-106">Dynamic Update</span></span>  
 <span data-ttu-id="b8ea5-107">Aby zastosować aktualizacje dynamiczne do wystąpienia przepływu pracy utrwalonych, <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> jest tworzony, który zawiera instrukcje dotyczące środowiska uruchomieniowego, których opisano sposób zmodyfikowania wystąpienia utrwalonych przepływów pracy, aby odzwierciedlić żądane zmiany.</span><span class="sxs-lookup"><span data-stu-id="b8ea5-107">To apply dynamic updates to a persisted workflow instance, a <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> is created that contains instructions for the runtime that describe how to modify the persisted workflow instance to reflect the desired changes.</span></span> <span data-ttu-id="b8ea5-108">Po utworzeniu mapy aktualizacji jest stosowana do wystąpień żądaną utrwalonych przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="b8ea5-108">Once the update map is created, it is applied to the desired persisted workflow instances.</span></span> <span data-ttu-id="b8ea5-109">Po zastosowaniu aktualizacji dynamicznych, wystąpienie przepływu pracy może zostać wznowione przy użyciu nowej definicji zaktualizowany przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="b8ea5-109">Once the dynamic update is applied, the workflow instance may be resumed using the new updated workflow definition.</span></span> <span data-ttu-id="b8ea5-110">Istnieją cztery kroki wymagane do tworzenia i stosowania mapy aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="b8ea5-110">There are four steps required to create and apply an update map.</span></span>  
  
1.  [<span data-ttu-id="b8ea5-111">Przygotowanie definicji przepływu pracy dla aktualizacji dynamicznej</span><span class="sxs-lookup"><span data-stu-id="b8ea5-111">Prepare the workflow definition for dynamic update</span></span>](../../../docs/framework/windows-workflow-foundation/dynamic-update.md#Prepare)  
  
2.  [<span data-ttu-id="b8ea5-112">Aktualizacja definicji przepływu pracy w celu odzwierciedlenia żądane zmiany</span><span class="sxs-lookup"><span data-stu-id="b8ea5-112">Update the workflow definition to reflect the desired changes</span></span>](../../../docs/framework/windows-workflow-foundation/dynamic-update.md#Update)  
  
3.  [<span data-ttu-id="b8ea5-113">Tworzenie mapy aktualizacji</span><span class="sxs-lookup"><span data-stu-id="b8ea5-113">Create the update map</span></span>](../../../docs/framework/windows-workflow-foundation/dynamic-update.md#Create)  
  
4.  [<span data-ttu-id="b8ea5-114">Dotyczą mapy aktualizacji wystąpień żądaną utrwalonych przepływów pracy</span><span class="sxs-lookup"><span data-stu-id="b8ea5-114">Apply the update map to the desired persisted workflow instances</span></span>](../../../docs/framework/windows-workflow-foundation/dynamic-update.md#Apply)  
  
> [!NOTE]
>  <span data-ttu-id="b8ea5-115">Należy pamiętać, że kroki od 1 do 3, który obejmuje tworzenie mapy aktualizacji, może być wykonana niezależnie od stosowania aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="b8ea5-115">Note that steps 1 through 3, which cover the creation of the update map, may be performed independently of applying the update.</span></span> <span data-ttu-id="b8ea5-116">Typowy scenariusz, mapujące czy przepływu pracy deweloperów utworzy aktualizacji w trybie offline, a następnie administrator zastosuje aktualizacji w późniejszym czasie.</span><span class="sxs-lookup"><span data-stu-id="b8ea5-116">A common scenario that that the workflow developer will create the update map offline, and then an administrator will apply the update at a later time.</span></span>  
  
 <span data-ttu-id="b8ea5-117">Ten temat zawiera omówienie procesu aktualizacji dynamicznej dodawania nowego działania do trwałego wystąpienia przepływu pracy skompilowanego pliku Xaml.</span><span class="sxs-lookup"><span data-stu-id="b8ea5-117">This topic provides an overview of the dynamic update process of adding a new activity to a persisted instance of a compiled Xaml workflow.</span></span>  
  
###  <a name="Prepare"></a><span data-ttu-id="b8ea5-118">Przygotowanie definicji przepływu pracy dla aktualizacji dynamicznej</span><span class="sxs-lookup"><span data-stu-id="b8ea5-118">Prepare the workflow definition for dynamic update</span></span>  
 <span data-ttu-id="b8ea5-119">Pierwszym krokiem w procesie aktualizacja dynamiczna jest przygotowanie definicji przepływu pracy odpowiednie dla aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="b8ea5-119">The first step in the dynamic update process is to prepare the desired workflow definition for update.</span></span> <span data-ttu-id="b8ea5-120">Jest to realizowane przez wywołanie <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> — metoda i przekazywanie w definicji przepływu pracy do zmodyfikowania.</span><span class="sxs-lookup"><span data-stu-id="b8ea5-120">This is done by calling the <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> method and passing in the workflow definition to modify.</span></span> <span data-ttu-id="b8ea5-121">Ta metoda sprawdza i następnie przegląda drzewo przepływu pracy, aby zidentyfikować wszystkie obiekty, takie jak działania publicznego i zmienne, które muszą być oznakowane tak porównać później przy użyciu definicji przepływu pracy zmodyfikowane.</span><span class="sxs-lookup"><span data-stu-id="b8ea5-121">This method validates and then walks the workflow tree to identify all of the objects such as public activities and variables that need to be tagged so they can be compared later with the modified workflow definition.</span></span> <span data-ttu-id="b8ea5-122">Po jego ukończeniu drzewa przepływu pracy jest sklonować i dołączone do oryginalnej definicji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="b8ea5-122">When this is complete, the workflow tree is cloned and attached to the original workflow definition.</span></span> <span data-ttu-id="b8ea5-123">Podczas tworzenia mapy aktualizacji zaktualizowanej wersji definicji przepływu pracy jest porównywana z oryginalnej definicji przepływu pracy i Mapa aktualizacji jest generowany w oparciu o różnice.</span><span class="sxs-lookup"><span data-stu-id="b8ea5-123">When the update map is created, the updated version of the workflow definition is compared with the original workflow definition and the update map is generated based on the differences.</span></span>  
  
 <span data-ttu-id="b8ea5-124">Aby przygotować Xaml przepływu pracy dla aktualizacji dynamicznych, które mogą zostać załadowane do <xref:System.Activities.ActivityBuilder>, a następnie <xref:System.Activities.ActivityBuilder> została przekazana do <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b8ea5-124">To prepare a Xaml workflow for dynamic update it may be loaded into an <xref:System.Activities.ActivityBuilder>, and then the <xref:System.Activities.ActivityBuilder> is passed into <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b8ea5-125">Aby uzyskać więcej informacji na temat pracy z serializacji przepływów pracy i <xref:System.Activities.ActivityBuilder>, zobacz [serializacji przepływów pracy i działań do i z XAML](../../../docs/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="b8ea5-125">For more information about working with serialized workflows and <xref:System.Activities.ActivityBuilder>, see [Serializing Workflows and Activities to and from XAML](../../../docs/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml.md).</span></span>  
  
 <span data-ttu-id="b8ea5-126">W poniższym przykładzie `MortgageWorkflow` definicji (składający się z <xref:System.Activities.Statements.Sequence> z kilku działań podrzędnych) jest ładowany do <xref:System.Activities.ActivityBuilder>i następnie przygotowane do aktualizacji dynamicznej.</span><span class="sxs-lookup"><span data-stu-id="b8ea5-126">In the following example, a `MortgageWorkflow` definition (that consists of a <xref:System.Activities.Statements.Sequence> with several child activities) is loaded into an <xref:System.Activities.ActivityBuilder>, and then prepared for dynamic update.</span></span> <span data-ttu-id="b8ea5-127">Po metoda zwraca, <xref:System.Activities.ActivityBuilder> zawiera oryginalnej definicji przepływu pracy, jak również kopię.</span><span class="sxs-lookup"><span data-stu-id="b8ea5-127">After the method returns, the <xref:System.Activities.ActivityBuilder> contains the original workflow definition as well as a copy.</span></span>  
  
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
>  <span data-ttu-id="b8ea5-128">Aby pobrać przykładowy kod, który towarzyszy w tym temacie, zobacz [aktualizacja dynamiczna przykładowy kod](http://go.microsoft.com/fwlink/?LinkId=227905).</span><span class="sxs-lookup"><span data-stu-id="b8ea5-128">To download the sample code that accompanies this topic, see [Dynamic Update sample code](http://go.microsoft.com/fwlink/?LinkId=227905).</span></span>  
  
###  <a name="Update"></a><span data-ttu-id="b8ea5-129">Aktualizacja definicji przepływu pracy w celu odzwierciedlenia żądane zmiany</span><span class="sxs-lookup"><span data-stu-id="b8ea5-129">Update the workflow definition to reflect the desired changes</span></span>  
 <span data-ttu-id="b8ea5-130">Po definicji przepływu pracy zostało przygotowane do aktualizacji, odpowiednich zmian będzie możliwe.</span><span class="sxs-lookup"><span data-stu-id="b8ea5-130">Once the workflow definition has been prepared for updating, the desired changes can be made.</span></span> <span data-ttu-id="b8ea5-131">Możesz można dodać lub usunąć działania, Dodaj przenieść lub usunąć zmiennych publicznych, Dodaj lub usuń argumenty i wprowadzić zmiany w podpisie delegatów działania.</span><span class="sxs-lookup"><span data-stu-id="b8ea5-131">You can add or remove activities, add, move or delete public variables, add or remove arguments, and make changes to the signature of activity delegates.</span></span> <span data-ttu-id="b8ea5-132">Nie można usunąć uruchomionego działania lub zmienianie podpisu delegata uruchomionych.</span><span class="sxs-lookup"><span data-stu-id="b8ea5-132">You cannot remove a running activity or change the signature of a running delegate.</span></span> <span data-ttu-id="b8ea5-133">Te zmiany mogą być nawiązywane przy użyciu kodu, lub w Projektancie ponownie hostowanej przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="b8ea5-133">These changes may be made using code, or in a re-hosted workflow designer.</span></span> <span data-ttu-id="b8ea5-134">W poniższym przykładzie niestandardowego `VerifyAppraisal` działania jest dodawany do sekwencji tworzącą treści `MortgageWorkflow` z poprzedniego przykładu.</span><span class="sxs-lookup"><span data-stu-id="b8ea5-134">In the following example, a custom `VerifyAppraisal` activity is added to the Sequence that makes up the body of the `MortgageWorkflow` from the previous example.</span></span>  
  
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
  
###  <a name="Create"></a><span data-ttu-id="b8ea5-135">Tworzenie mapy aktualizacji</span><span class="sxs-lookup"><span data-stu-id="b8ea5-135">Create the update map</span></span>  
 <span data-ttu-id="b8ea5-136">Po zmodyfikowaniu definicji przepływu pracy, który został przygotowany dla aktualizacji można utworzyć mapy aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="b8ea5-136">Once the workflow definition that was prepared for update has been modified, the update map can be created.</span></span> <span data-ttu-id="b8ea5-137">Aby utworzyć mapę aktualizacji dynamicznej, <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="b8ea5-137">To create a dynamic update map, the <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> method is invoked.</span></span> <span data-ttu-id="b8ea5-138">To polecenie zwróci <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> zawierający informacje środowiska uruchomieniowego musi zmodyfikować wystąpienia utrwalonego przepływu pracy, dzięki czemu mogą być ładowane i przywrócone definicję nowego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="b8ea5-138">This returns a <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> that contains the information the runtime needs to modify a persisted workflow instance so that it may be loaded and resumed with the new workflow definition.</span></span> <span data-ttu-id="b8ea5-139">W poniższym przykładzie jest tworzony dynamicznej mapy dla zmodyfikowanych `MortgageWorkflow` definicji z poprzedniego przykładu.</span><span class="sxs-lookup"><span data-stu-id="b8ea5-139">In the following example, a dynamic map is created for the modified `MortgageWorkflow` definition from the previous example.</span></span>  
  
```csharp  
// Create the update map.  
DynamicUpdateMap map = DynamicUpdateServices.CreateUpdateMap(ab);  
```  
  
 <span data-ttu-id="b8ea5-140">Ta mapa aktualizacji natychmiast może służyć do modyfikowania wystąpień utrwalonych przepływów pracy, lub więcej zwykle można zapisywać i później stosowane aktualizacje.</span><span class="sxs-lookup"><span data-stu-id="b8ea5-140">This update map can immediately be used to modify persisted workflow instances, or more typically it can be saved and the updates applied later.</span></span> <span data-ttu-id="b8ea5-141">Jednym ze sposobów zapisać mapy aktualizacji jest serializować go do pliku, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b8ea5-141">One way to save the update map is to serialize it to a file, as shown in the following example.</span></span>  
  
```csharp  
// Serialize the update map to a file.  
DataContractSerializer serializer = new DataContractSerializer(typeof(DynamicUpdateMap));  
using (FileStream fs = System.IO.File.Open(@"C:\WorkflowDefitinions\MortgageWorkflow.map", FileMode.Create))  
{  
    serializer.WriteObject(fs, map);  
}  
```  
  
 <span data-ttu-id="b8ea5-142">Gdy <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> zwraca definicji przepływu pracy sklonowany i inne informacje aktualizacji dynamicznej, która została dodana w wywołaniu <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> zostanie usunięty, i definicji przepływu pracy modyfikacji jest gotowy do zapisane, dzięki czemu można później po zaktualizowaniu wznawianie wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="b8ea5-142">When <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> returns, the cloned workflow definition and other dynamic update information that was added in the call to <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> is removed, and the modified workflow definition is ready to be saved so that it can be used later when resuming updated workflow instances.</span></span> <span data-ttu-id="b8ea5-143">W poniższym przykładzie są zapisywane definicji przepływu pracy zmodyfikowanych `MortgageWorkflow_v2.xaml`.</span><span class="sxs-lookup"><span data-stu-id="b8ea5-143">In the following example, the modified workflow definition is saved to `MortgageWorkflow_v2.xaml`.</span></span>  
  
```csharp  
// Save the modified workflow definition.  
StreamWriter sw = File.CreateText(@"C:\WorkflowDefitinions\MortgageWorkflow_v1.1.xaml");  
XamlWriter xw = ActivityXamlServices.CreateBuilderWriter(new XamlXmlWriter(sw, new XamlSchemaContext()));  
XamlServices.Save(xw, ab);  
sw.Close();  
```  
  
###  <a name="Apply"></a><span data-ttu-id="b8ea5-144">Dotyczą mapy aktualizacji wystąpień żądaną utrwalonych przepływów pracy</span><span class="sxs-lookup"><span data-stu-id="b8ea5-144">Apply the update map to the desired persisted workflow instances</span></span>  
 <span data-ttu-id="b8ea5-145">Stosowanie mapy aktualizacji może odbywać się w dowolnym momencie po jej utworzeniu.</span><span class="sxs-lookup"><span data-stu-id="b8ea5-145">Applying the update map can be done at any time after creating it.</span></span> <span data-ttu-id="b8ea5-146">Mogą to robić, od razu przy użyciu <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> wystąpienia, który został zwrócony przez <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType>, lub możesz zrobić, później za pomocą kopii zapisanych mapy aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="b8ea5-146">It can be done right away using the <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> instance that was returned by <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType>, or it can be done later using a saved copy of the update map.</span></span> <span data-ttu-id="b8ea5-147">Aby zaktualizować wystąpienia przepływu pracy, załadować go do <xref:System.Activities.WorkflowApplicationInstance> przy użyciu <xref:System.Activities.WorkflowApplication.GetInstance%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b8ea5-147">To update a workflow instance, load it into a <xref:System.Activities.WorkflowApplicationInstance> using <xref:System.Activities.WorkflowApplication.GetInstance%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b8ea5-148">Następnie należy utworzyć <xref:System.Activities.WorkflowApplication> przy użyciu definicji zaktualizowany przepływ pracy i żądaną <xref:System.Activities.WorkflowIdentity>.</span><span class="sxs-lookup"><span data-stu-id="b8ea5-148">Next, create a <xref:System.Activities.WorkflowApplication> using the updated workflow definition, and the desired <xref:System.Activities.WorkflowIdentity>.</span></span> <span data-ttu-id="b8ea5-149">To <xref:System.Activities.WorkflowIdentity> może być inny niż ten, który został użyty do utrwalenia oryginalnego przepływu pracy i jest zwykle w celu odzwierciedlenia zmodyfikowano trwałego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="b8ea5-149">This <xref:System.Activities.WorkflowIdentity> may be different than the one that was used to persist the original workflow, and typically is in order to reflect that the persisted instance has been modified.</span></span> <span data-ttu-id="b8ea5-150">Raz <xref:System.Activities.WorkflowApplication> jest utworzona, jest on ładowany za pomocą przeciążenia <xref:System.Activities.WorkflowApplication.Load%2A?displayProperty=nameWithType> pobierającej <xref:System.Activities.DynamicUpdate.DynamicUpdateMap>i następnie zwalnianie wywołaniem <xref:System.Activities.WorkflowApplication.Unload%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b8ea5-150">Once the <xref:System.Activities.WorkflowApplication> is created, it is loaded using the overload of <xref:System.Activities.WorkflowApplication.Load%2A?displayProperty=nameWithType> that takes a <xref:System.Activities.DynamicUpdate.DynamicUpdateMap>, and then unloaded with a call to <xref:System.Activities.WorkflowApplication.Unload%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b8ea5-151">To ma zastosowanie aktualizacja dynamiczna i będzie się powtarzał wystąpienia zaktualizowany przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="b8ea5-151">This applies the dynamic update and persists the updated workflow instance.</span></span>  
  
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
  
### <a name="resuming-an-updated-workflow-instance"></a><span data-ttu-id="b8ea5-152">Wznawianie wystąpienia zaktualizowany przepływ pracy</span><span class="sxs-lookup"><span data-stu-id="b8ea5-152">Resuming an Updated Workflow Instance</span></span>  
 <span data-ttu-id="b8ea5-153">Po zastosowaniu aktualizacji dynamicznej, może zostać wznowione wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="b8ea5-153">Once dynamic update has been applied, the workflow instance may be resumed.</span></span> <span data-ttu-id="b8ea5-154">Uwaga nowej aktualizacji definicji i <xref:System.Activities.WorkflowIdentity> musi być używany.</span><span class="sxs-lookup"><span data-stu-id="b8ea5-154">Note that the new updated definition and <xref:System.Activities.WorkflowIdentity> must be used.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b8ea5-155">Aby uzyskać więcej informacji na temat pracy z <xref:System.Activities.WorkflowApplication> i <xref:System.Activities.WorkflowIdentity>, zobacz[za pomocą właściwości WorkflowIdentity and Versioning](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="b8ea5-155">For more information about working with <xref:System.Activities.WorkflowApplication> and <xref:System.Activities.WorkflowIdentity>, see[Using WorkflowIdentity and Versioning](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md).</span></span>  
  
 <span data-ttu-id="b8ea5-156">W poniższym przykładzie `MortgageWorkflow_v1.1.xaml` przepływu pracy z poprzedniego przykładu został skompilowany i jest załadowany i został wznowiony przy użyciu definicji zaktualizowany przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="b8ea5-156">In the following example, the `MortgageWorkflow_v1.1.xaml` workflow from the previous example has been compiled, and is loaded and resumed using the updated workflow definition.</span></span>  
  
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
>  <span data-ttu-id="b8ea5-157">Aby pobrać przykładowy kod, który towarzyszy w tym temacie, zobacz [aktualizacja dynamiczna przykładowy kod](http://go.microsoft.com/fwlink/?LinkId=227905).</span><span class="sxs-lookup"><span data-stu-id="b8ea5-157">To download the sample code that accompanies this topic, see [Dynamic Update sample code](http://go.microsoft.com/fwlink/?LinkId=227905).</span></span>
