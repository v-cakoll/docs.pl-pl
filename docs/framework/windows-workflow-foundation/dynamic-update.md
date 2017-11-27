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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1d8aff19cc087cf4aea2befb7a39533422aeabd8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="dynamic-update"></a>Aktualizacja dynamiczna
Aktualizacja dynamiczna udostępnia mechanizm dla przepływu pracy deweloperami aplikacji, aby zaktualizować wystąpienia przepływu pracy utrwalonych definicji przepływu pracy. Może to być do zaimplementowania poprawkę, nowe wymagania, lub aby pomieścić nieoczekiwane zmiany. Ten temat zawiera omówienie funkcji aktualizacji dynamicznej wprowadzona w systemie [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].  
  
## <a name="dynamic-update"></a>Aktualizacja dynamiczna  
 Aby zastosować aktualizacje dynamiczne do wystąpienia przepływu pracy utrwalonych, <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> jest tworzony, który zawiera instrukcje dotyczące środowiska uruchomieniowego, których opisano sposób zmodyfikowania wystąpienia utrwalonych przepływów pracy, aby odzwierciedlić żądane zmiany. Po utworzeniu mapy aktualizacji jest stosowana do wystąpień żądaną utrwalonych przepływów pracy. Po zastosowaniu aktualizacji dynamicznych, wystąpienie przepływu pracy może zostać wznowione przy użyciu nowej definicji zaktualizowany przepływ pracy. Istnieją cztery kroki wymagane do tworzenia i stosowania mapy aktualizacji.  
  
1.  [Przygotowanie definicji przepływu pracy dla aktualizacji dynamicznej](../../../docs/framework/windows-workflow-foundation/dynamic-update.md#Prepare)  
  
2.  [Aktualizacja definicji przepływu pracy w celu odzwierciedlenia żądane zmiany](../../../docs/framework/windows-workflow-foundation/dynamic-update.md#Update)  
  
3.  [Tworzenie mapy aktualizacji](../../../docs/framework/windows-workflow-foundation/dynamic-update.md#Create)  
  
4.  [Dotyczą mapy aktualizacji wystąpień żądaną utrwalonych przepływów pracy](../../../docs/framework/windows-workflow-foundation/dynamic-update.md#Apply)  
  
> [!NOTE]
>  Należy pamiętać, że kroki od 1 do 3, który obejmuje tworzenie mapy aktualizacji, może być wykonana niezależnie od stosowania aktualizacji. Typowy scenariusz, mapujące czy przepływu pracy deweloperów utworzy aktualizacji w trybie offline, a następnie administrator zastosuje aktualizacji w późniejszym czasie.  
  
 Ten temat zawiera omówienie procesu aktualizacji dynamicznej dodawania nowego działania do trwałego wystąpienia przepływu pracy skompilowanego pliku Xaml.  
  
###  <a name="Prepare"></a>Przygotowanie definicji przepływu pracy dla aktualizacji dynamicznej  
 Pierwszym krokiem w procesie aktualizacja dynamiczna jest przygotowanie definicji przepływu pracy odpowiednie dla aktualizacji. Jest to realizowane przez wywołanie <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> — metoda i przekazywanie w definicji przepływu pracy do zmodyfikowania. Ta metoda sprawdza i następnie przegląda drzewo przepływu pracy, aby zidentyfikować wszystkie obiekty, takie jak działania publicznego i zmienne, które muszą być oznakowane tak porównać później przy użyciu definicji przepływu pracy zmodyfikowane. Po jego ukończeniu drzewa przepływu pracy jest sklonować i dołączone do oryginalnej definicji przepływu pracy. Podczas tworzenia mapy aktualizacji zaktualizowanej wersji definicji przepływu pracy jest porównywana z oryginalnej definicji przepływu pracy i Mapa aktualizacji jest generowany w oparciu o różnice.  
  
 Aby przygotować Xaml przepływu pracy dla aktualizacji dynamicznych, które mogą zostać załadowane do <xref:System.Activities.ActivityBuilder>, a następnie <xref:System.Activities.ActivityBuilder> została przekazana do <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType>.  
  
> [!NOTE]
>  Aby uzyskać więcej informacji na temat pracy z serializacji przepływów pracy i <xref:System.Activities.ActivityBuilder>, zobacz [serializacji przepływów pracy i działań do i z XAML](../../../docs/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml.md).  
  
 W poniższym przykładzie `MortgageWorkflow` definicji (składający się z <xref:System.Activities.Statements.Sequence> z kilku działań podrzędnych) jest ładowany do <xref:System.Activities.ActivityBuilder>i następnie przygotowane do aktualizacji dynamicznej. Po metoda zwraca, <xref:System.Activities.ActivityBuilder> zawiera oryginalnej definicji przepływu pracy, jak również kopię.  
  
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
>  Aby pobrać przykładowy kod, który towarzyszy w tym temacie, zobacz [aktualizacja dynamiczna przykładowy kod](http://go.microsoft.com/fwlink/?LinkId=227905).  
  
###  <a name="Update"></a>Aktualizacja definicji przepływu pracy w celu odzwierciedlenia żądane zmiany  
 Po definicji przepływu pracy zostało przygotowane do aktualizacji, odpowiednich zmian będzie możliwe. Możesz można dodać lub usunąć działania, Dodaj przenieść lub usunąć zmiennych publicznych, Dodaj lub usuń argumenty i wprowadzić zmiany w podpisie delegatów działania. Nie można usunąć uruchomionego działania lub zmienianie podpisu delegata uruchomionych. Te zmiany mogą być nawiązywane przy użyciu kodu, lub w Projektancie ponownie hostowanej przepływu pracy. W poniższym przykładzie niestandardowego `VerifyAppraisal` działania jest dodawany do sekwencji tworzącą treści `MortgageWorkflow` z poprzedniego przykładu.  
  
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
  
###  <a name="Create"></a>Tworzenie mapy aktualizacji  
 Po zmodyfikowaniu definicji przepływu pracy, który został przygotowany dla aktualizacji można utworzyć mapy aktualizacji. Aby utworzyć mapę aktualizacji dynamicznej, <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> wywołania metody. To polecenie zwróci <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> zawierający informacje środowiska uruchomieniowego musi zmodyfikować wystąpienia utrwalonego przepływu pracy, dzięki czemu mogą być ładowane i przywrócone definicję nowego przepływu pracy. W poniższym przykładzie jest tworzony dynamicznej mapy dla zmodyfikowanych `MortgageWorkflow` definicji z poprzedniego przykładu.  
  
```csharp  
// Create the update map.  
DynamicUpdateMap map = DynamicUpdateServices.CreateUpdateMap(ab);  
```  
  
 Ta mapa aktualizacji natychmiast może służyć do modyfikowania wystąpień utrwalonych przepływów pracy, lub więcej zwykle można zapisywać i później stosowane aktualizacje. Jednym ze sposobów zapisać mapy aktualizacji jest serializować go do pliku, jak pokazano w poniższym przykładzie.  
  
```csharp  
// Serialize the update map to a file.  
DataContractSerializer serializer = new DataContractSerializer(typeof(DynamicUpdateMap));  
using (FileStream fs = System.IO.File.Open(@"C:\WorkflowDefitinions\MortgageWorkflow.map", FileMode.Create))  
{  
    serializer.WriteObject(fs, map);  
}  
```  
  
 Gdy <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> zwraca definicji przepływu pracy sklonowany i inne informacje aktualizacji dynamicznej, która została dodana w wywołaniu <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> zostanie usunięty, i definicji przepływu pracy modyfikacji jest gotowy do zapisane, dzięki czemu można później po zaktualizowaniu wznawianie wystąpienia przepływu pracy. W poniższym przykładzie są zapisywane definicji przepływu pracy zmodyfikowanych `MortgageWorkflow_v2.xaml`.  
  
```csharp  
// Save the modified workflow definition.  
StreamWriter sw = File.CreateText(@"C:\WorkflowDefitinions\MortgageWorkflow_v1.1.xaml");  
XamlWriter xw = ActivityXamlServices.CreateBuilderWriter(new XamlXmlWriter(sw, new XamlSchemaContext()));  
XamlServices.Save(xw, ab);  
sw.Close();  
```  
  
###  <a name="Apply"></a>Dotyczą mapy aktualizacji wystąpień żądaną utrwalonych przepływów pracy  
 Stosowanie mapy aktualizacji może odbywać się w dowolnym momencie po jej utworzeniu. Mogą to robić, od razu przy użyciu <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> wystąpienia, który został zwrócony przez <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType>, lub możesz zrobić, później za pomocą kopii zapisanych mapy aktualizacji. Aby zaktualizować wystąpienia przepływu pracy, załadować go do <xref:System.Activities.WorkflowApplicationInstance> przy użyciu <xref:System.Activities.WorkflowApplication.GetInstance%2A?displayProperty=nameWithType>. Następnie należy utworzyć <xref:System.Activities.WorkflowApplication> przy użyciu definicji zaktualizowany przepływ pracy i żądaną <xref:System.Activities.WorkflowIdentity>. To <xref:System.Activities.WorkflowIdentity> może być inny niż ten, który został użyty do utrwalenia oryginalnego przepływu pracy i jest zwykle w celu odzwierciedlenia zmodyfikowano trwałego wystąpienia. Raz <xref:System.Activities.WorkflowApplication> jest utworzona, jest on ładowany za pomocą przeciążenia <xref:System.Activities.WorkflowApplication.Load%2A?displayProperty=nameWithType> pobierającej <xref:System.Activities.DynamicUpdate.DynamicUpdateMap>i następnie zwalnianie wywołaniem <xref:System.Activities.WorkflowApplication.Unload%2A?displayProperty=nameWithType>. To ma zastosowanie aktualizacja dynamiczna i będzie się powtarzał wystąpienia zaktualizowany przepływ pracy.  
  
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
  
### <a name="resuming-an-updated-workflow-instance"></a>Wznawianie wystąpienia zaktualizowany przepływ pracy  
 Po zastosowaniu aktualizacji dynamicznej, może zostać wznowione wystąpienia przepływu pracy. Uwaga nowej aktualizacji definicji i <xref:System.Activities.WorkflowIdentity> musi być używany.  
  
> [!NOTE]
>  Aby uzyskać więcej informacji na temat pracy z <xref:System.Activities.WorkflowApplication> i <xref:System.Activities.WorkflowIdentity>, zobacz[za pomocą właściwości WorkflowIdentity and Versioning](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md).  
  
 W poniższym przykładzie `MortgageWorkflow_v1.1.xaml` przepływu pracy z poprzedniego przykładu został skompilowany i jest załadowany i został wznowiony przy użyciu definicji zaktualizowany przepływ pracy.  
  
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
>  Aby pobrać przykładowy kod, który towarzyszy w tym temacie, zobacz [aktualizacja dynamiczna przykładowy kod](http://go.microsoft.com/fwlink/?LinkId=227905).
