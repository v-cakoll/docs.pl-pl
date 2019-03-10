---
title: Aktualizacja dynamiczna
ms.date: 03/30/2017
ms.assetid: 8b6ef19b-9691-4b4b-824c-3c651a9db96e
ms.openlocfilehash: a1d5337bf69cb87d790ce4074cde4c18c989a4d8
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57724482"
---
# <a name="dynamic-update"></a>Aktualizacja dynamiczna

Aktualizacja dynamiczna udostępnia mechanizm dla przepływu pracy deweloperów aplikacji, aby zaktualizować definicję przepływu pracy z istniejącym wystąpieniem przepływu pracy. Może to być do zaimplementowania poprawki, nowe wymagania, lub aby pomieścić nieoczekiwanych zmian. Ten temat zawiera omówienie funkcji aktualizacji dynamicznej wprowadzona w [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].

## <a name="dynamic-update"></a>Aktualizacja dynamiczna

Aby zastosować aktualizacje dynamiczne do utrwalonego wystąpienia przepływu pracy, <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> utworzono, która zawiera instrukcje dla środowiska uruchomieniowego, które opisują sposób modyfikowania utrwalonego wystąpienia przepływu pracy zgodnie ze zmianami żądaną. Po utworzeniu update map zostanie zastosowany do wystąpienia żądaną utrwalonych przepływu pracy. Po zastosowaniu aktualizacji dynamicznej wystąpienia przepływu pracy może wznowić, przy użyciu nowej definicji zaktualizowany przepływ pracy. Istnieją cztery kroki wymagane do tworzenia i stosowania aktualizacji mapy.

1. [Przygotowanie definicji przepływu pracy dla aktualizacji dynamicznych](dynamic-update.md#Prepare)

2. [Aktualizowanie definicji przepływu pracy, aby odzwierciedlić żądane zmiany](dynamic-update.md#Update)

3. [Tworzenie update map](dynamic-update.md#Create)

4. [Zastosuj mapy aktualizacji do wystąpień żądaną utrwalonych przepływów pracy](dynamic-update.md#Apply)

> [!NOTE]
> Należy pamiętać, że kroki od 1 do 3, które obejmują tworzenie mapy aktualizacji, może być odbywa się niezależnie od zastosowania aktualizacji. Typowy scenariusz, że przepływ pracy dla deweloperów utworzy aktualizacji mapy w trybie offline, a następnie administrator zastosuje aktualizację w późniejszym czasie.

Ten temat zawiera omówienie procesu aktualizacji dynamicznej dodawania nowe działanie do utrwalonego wystąpienia skompilowanych Xaml przepływu pracy.

### <a name="Prepare"></a> Przygotowanie definicji przepływu pracy dla aktualizacji dynamicznych

Pierwszym krokiem w procesie aktualizacja dynamiczna jest przygotowanie definicji żądanego przepływu pracy dla aktualizacji. Jest to realizowane przez wywołanie <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> metody i przekazywanie w definicji przepływu pracy, aby zmodyfikować. Ta metoda sprawdza poprawność, a następnie przegląda drzewo przepływu pracy, aby zidentyfikować wszystkie obiekty, takie jak działania publiczne i zmienne, które trzeba oznakowane, więc porównania później z definicji przepływu pracy zmodyfikowane. Po jego ukończeniu drzewa przepływu pracy jest sklonowany i dołączony do oryginalnej definicji przepływu pracy. Po utworzeniu update map zaktualizowanej wersji definicji przepływu pracy jest porównywana z oryginalnej definicji przepływu pracy i mapy aktualizacji jest generowana na temat różnic.

Aby przygotować Xaml przepływu pracy dla aktualizacji dynamicznych, które mogą zostać załadowane do <xref:System.Activities.ActivityBuilder>, a następnie <xref:System.Activities.ActivityBuilder> jest przekazywana do <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType>.

> [!NOTE]
> Aby uzyskać więcej informacji na temat pracy z usługą serializacji przepływów pracy i <xref:System.Activities.ActivityBuilder>, zobacz [serializowanie przepływów pracy i działań do i z XAML](serializing-workflows-and-activities-to-and-from-xaml.md).

W poniższym przykładzie `MortgageWorkflow` definicji (składający się z <xref:System.Activities.Statements.Sequence> z kilku działań podrzędnych) jest ładowany do <xref:System.Activities.ActivityBuilder>, a następnie przygotowane na potrzeby aktualizacji dynamicznej. Po powrocie z metody, <xref:System.Activities.ActivityBuilder> zawiera oryginalnej definicji przepływu pracy, a także kopię.

```csharp
// Load the MortgageWorkflow definition from Xaml into
// an ActivityBuilder.
XamlXmlReaderSettings readerSettings = new XamlXmlReaderSettings()
{
    LocalAssembly = Assembly.GetExecutingAssembly()
};

XamlXmlReader xamlReader = new XamlXmlReader(@"C:\WorkflowDefinitions\MortgageWorkflow.xaml",
    readerSettings);

ActivityBuilder ab = XamlServices.Load(
    ActivityXamlServices.CreateBuilderReader(xamlReader)) as ActivityBuilder;

// Prepare the workflow definition for dynamic update.
DynamicUpdateServices.PrepareForUpdate(ab);
```

> [!NOTE]
> Aby pobrać przykładowy kod, który towarzyszy w tym temacie, zobacz [aktualizacja dynamiczna przykładowy kod](https://go.microsoft.com/fwlink/?LinkId=227905).

### <a name="Update"></a> Aktualizowanie definicji przepływu pracy, aby odzwierciedlić żądane zmiany

Po definicji przepływu pracy zostało przygotowane do aktualizacji, odpowiednich zmian będzie możliwe. Możesz można dodać lub usunąć działania, Dodaj, przenieść lub usunąć publiczny zmiennych, Dodaj lub usuń argumenty i wprowadzić zmiany w podpisie działania delegatach. Nie można usunąć uruchomione działanie ani zmienić podpis delegata uruchomione. Te zmiany mogą być nawiązywane przy użyciu kodu, lub w Projektancie ponownie hostowanej przepływu pracy. W poniższym przykładzie niestandardową `VerifyAppraisal` dodaniu działania do sekwencji, tworzącą treści `MortgageWorkflow` z poprzedniego przykładu.

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

### <a name="Create"></a> Tworzenie update map

Po definicji przepływu pracy, który został przygotowany dla aktualizacji został zmodyfikowany, można utworzyć mapy aktualizacji. Aby utworzyć mapę aktualizacja dynamiczna <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> metoda jest wywoływana. Spowoduje to zwrócenie <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> zawierający informacje środowiska uruchomieniowego trzeba zmodyfikować utrwalonego wystąpienia przepływu pracy, który może być załadowany i wznowiono z użyciem nową definicję przepływu pracy. W poniższym przykładzie jest tworzony dynamicznej mapy dla zmodyfikowanego `MortgageWorkflow` definicji z poprzedniego przykładu.

```csharp
// Create the update map.
DynamicUpdateMap map = DynamicUpdateServices.CreateUpdateMap(ab);
```

Tę mapę aktualizacji natychmiast może służyć do modyfikowania wystąpienia utrwalonych przepływu pracy, lub zazwyczaj można zapisać i później stosowane aktualizacje. Jednym ze sposobów, aby zapisać mapy aktualizacji ma serializować go do pliku, jak pokazano w poniższym przykładzie.

```csharp
// Serialize the update map to a file.
DataContractSerializer serializer = new DataContractSerializer(typeof(DynamicUpdateMap));
using (FileStream fs = System.IO.File.Open(@"C:\WorkflowDefinitions\MortgageWorkflow.map", FileMode.Create))
{
    serializer.WriteObject(fs, map);
}
```

Gdy <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> zwraca definicji sklonowany przepływu pracy i inne informacje aktualizacja dynamiczna, która została dodana w wywołaniu <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> zostanie usunięty, i definicji modyfikacji przepływu pracy jest gotowa do zapisania tak, aby go można korzystać później podczas wznawianie zaktualizować wystąpienia przepływu pracy. W poniższym przykładzie jest zapisywana definicja przepływu pracy zmodyfikowane `MortgageWorkflow_v2.xaml`.

```csharp
// Save the modified workflow definition.
StreamWriter sw = File.CreateText(@"C:\WorkflowDefinitions\MortgageWorkflow_v1.1.xaml");
XamlWriter xw = ActivityXamlServices.CreateBuilderWriter(new XamlXmlWriter(sw, new XamlSchemaContext()));
XamlServices.Save(xw, ab);
sw.Close();
```

### <a name="Apply"></a> Zastosuj mapy aktualizacji do wystąpień żądaną utrwalonych przepływów pracy

Stosowanie aktualizacji mapy może odbywać się w dowolnym momencie po jej utworzeniu. Możesz to zrobić, następnie od razu przy użyciu <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> wystąpienia, który został zwrócony przez <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType>, lub można to zrobić później za pomocą zapisana kopia mapowania aktualizacji. Aby zaktualizować wystąpienia przepływu pracy, załadować go do <xref:System.Activities.WorkflowApplicationInstance> przy użyciu <xref:System.Activities.WorkflowApplication.GetInstance%2A?displayProperty=nameWithType>. Następnie należy utworzyć <xref:System.Activities.WorkflowApplication> przy użyciu definicji przepływu pracy zaktualizowane i żądany <xref:System.Activities.WorkflowIdentity>. To <xref:System.Activities.WorkflowIdentity> może być inny niż ten, który został użyty do utrwalenia oryginalny przepływ pracy i jest zazwyczaj w celu odzwierciedlenia czy utrwalonego wystąpienia zostały zmodyfikowane. Raz <xref:System.Activities.WorkflowApplication> jest utworzony, jest on ładowany za pomocą przeciążenia <xref:System.Activities.WorkflowApplication.Load%2A?displayProperty=nameWithType> przyjmującej <xref:System.Activities.DynamicUpdate.DynamicUpdateMap>, a następnie zostały zwolnione w wyniku wywołania <xref:System.Activities.WorkflowApplication.Unload%2A?displayProperty=nameWithType>. To ma zastosowanie aktualizacja dynamiczna i będzie się powtarzał wystąpienia zaktualizowanego przepływu pracy.

```csharp
// Load the serialized update map.
DynamicUpdateMap map;
using (FileStream fs = File.Open(@"C:\WorkflowDefinitions\MortgageWorkflow.map", FileMode.Open))
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

### <a name="resuming-an-updated-workflow-instance"></a>Wznawianie działania wystąpienia przepływu pracy zaktualizowane

Po zastosowaniu aktualizacji dynamicznych, może zostać wznowione wystąpienia przepływu pracy. Uwaga nowej aktualizacji definicji i <xref:System.Activities.WorkflowIdentity> musi być używana.

> [!NOTE]
> Aby uzyskać więcej informacji na temat pracy z usługą <xref:System.Activities.WorkflowApplication> i <xref:System.Activities.WorkflowIdentity>, zobacz [przy użyciu obiektu WorkflowIdentity i wersjonowanie](using-workflowidentity-and-versioning.md).

W poniższym przykładzie `MortgageWorkflow_v1.1.xaml` przepływu pracy z poprzedniego przykładu został wcześniej skompilowany, a zostanie załadowany i wznowić, przy użyciu definicji przepływu pracy zaktualizowane.

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
> Aby pobrać przykładowy kod, który towarzyszy w tym temacie, zobacz [aktualizacja dynamiczna przykładowy kod](https://go.microsoft.com/fwlink/?LinkId=227905).
