---
title: Używanie obiektu WorkflowIdentity i wersjonowanie
ms.date: 03/30/2017
ms.assetid: b8451735-8046-478f-912b-40870a6c0c3a
ms.openlocfilehash: 97224caa24b38a00a1cbb4fa76781eea3a10faaf
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76787920"
---
# <a name="using-workflowidentity-and-versioning"></a>Używanie obiektu WorkflowIdentity i wersjonowanie

<xref:System.Activities.WorkflowIdentity> umożliwia deweloperom aplikacji przepływu pracy kojarzenie nazw i <xref:System.Version> z definicją przepływu pracy oraz dla tych informacji do skojarzenia z utrwalonym wystąpieniem przepływu pracy. Te informacje o tożsamości mogą być używane przez deweloperów aplikacji przepływu pracy do włączania scenariuszy, takich jak wykonywanie równoczesne wielu wersji definicji przepływu pracy i udostępniają one podstawę do innych funkcji, takich jak aktualizacja dynamiczna. Ten temat zawiera omówienie używania <xref:System.Activities.WorkflowIdentity> z usługą <xref:System.Activities.WorkflowApplication> hosting. Aby uzyskać informacje na temat wykonywania operacji równoległych w definicjach przepływu pracy w usłudze przepływu pracy, zobacz [obok siebie przechowywanie wersji obok siebie w obszarze WorkflowServiceHost](../wcf/feature-details/side-by-side-versioning-in-workflowservicehost.md). Aby uzyskać informacje na temat aktualizacji dynamicznej, zobacz [Aktualizacja dynamiczna](dynamic-update.md).

## <a name="in-this-topic"></a>W tym temacie

- [Korzystanie z właściwości WorkflowIdentity](using-workflowidentity-and-versioning.md#UsingWorkflowIdentity)

  - [Wykonywanie równoczesne przy użyciu właściwości WorkflowIdentity](using-workflowidentity-and-versioning.md#SxS)

- [Uaktualnianie baz danych trwałości .NET Framework 4 w celu obsługi wersji przepływu pracy](using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases)

  - [Aby uaktualnić schemat bazy danych](using-workflowidentity-and-versioning.md#ToUpgrade)

## <a name="UsingWorkflowIdentity"></a>Korzystanie z właściwości WorkflowIdentity

Aby użyć <xref:System.Activities.WorkflowIdentity>, Utwórz wystąpienie, skonfiguruj je i skojarz z wystąpieniem <xref:System.Activities.WorkflowApplication>. Wystąpienie <xref:System.Activities.WorkflowIdentity> zawiera trzy tożsamości informacji. <xref:System.Activities.WorkflowIdentity.Name%2A> i <xref:System.Activities.WorkflowIdentity.Version%2A> zawierają nazwę i <xref:System.Version> i są wymagane, a <xref:System.Activities.WorkflowIdentity.Package%2A> jest opcjonalne i może służyć do określenia dodatkowego ciągu zawierającego informacje takie jak nazwa zestawu lub inne żądane informacje. <xref:System.Activities.WorkflowIdentity> jest unikatowy, jeśli którykolwiek z jej trzech właściwości różni się od innego <xref:System.Activities.WorkflowIdentity>.

> [!IMPORTANT]
> <xref:System.Activities.WorkflowIdentity> nie powinna zawierać żadnych informacji umożliwiających identyfikację użytkownika. Informacje o <xref:System.Activities.WorkflowIdentity> używanym do tworzenia wystąpienia są emitowane do wszelkich skonfigurowanych usług śledzenia w kilku różnych punktach cyklu życia działania przez środowisko uruchomieniowe. Śledzenie WF nie ma żadnego mechanizmu ukrywania danych osobowych (poufne dane użytkownika). W związku z tym wystąpienie <xref:System.Activities.WorkflowIdentity> nie powinno zawierać żadnych danych osobowych, ponieważ będzie emitowane przez środowisko uruchomieniowe w celu śledzenia rekordów i może być widoczne dla każdego, kto ma dostęp do wyświetlania rekordów śledzenia.

W poniższym przykładzie <xref:System.Activities.WorkflowIdentity> jest tworzony i skojarzony z wystąpieniem przepływu pracy utworzonego przy użyciu `MortgageWorkflow` definicji przepływu pracy.

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

Po ponownym załadowaniu i wznowieniu przepływu pracy należy użyć <xref:System.Activities.WorkflowIdentity>, który jest skonfigurowany tak, aby pasował do <xref:System.Activities.WorkflowIdentity> wystąpienia utrwalonego przepływu pracy.

```csharp
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identityV1);

// Configure the WorkflowApplication with persistence and desired workflow event handlers.
ConfigureWorkflowApplication(wfApp);

// Load the workflow.
wfApp.Load(instanceId);

// Resume the workflow...
```

Jeśli <xref:System.Activities.WorkflowIdentity> używany podczas ponownego ładowania wystąpienia przepływu pracy nie pasuje do utrwalonego <xref:System.Activities.WorkflowIdentity>, zostanie zgłoszony <xref:System.Activities.VersionMismatchException>. W poniższym przykładzie podjęto próbę załadowania w wystąpieniu `MortgageWorkflow`, które było utrwalone w poprzednim przykładzie. Ta próba załadowania została wykonana przy użyciu <xref:System.Activities.WorkflowIdentity> skonfigurowanego dla nowszej wersji przepływu pracy hipotecznej, która nie jest zgodna z utrwalonym wystąpieniem.

```csharp
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow_v2(), identityV2);

// Configure the WorkflowApplication with persistence and desired workflow event handlers.
ConfigureWorkflowApplication(wfApp);

// Attempt to load the workflow instance.
wfApp.Load(instanceId);

// Resume the workflow...
```

Gdy poprzedni kod jest wykonywany, zostanie zgłoszony następujący <xref:System.Activities.VersionMismatchException>.

```output
The WorkflowIdentity ('MortgageWorkflow v1; Version=1.0.0.0') of the loaded instance does not match the WorkflowIdentity ('MortgageWorkflow v2; Version=2.0.0.0') of the provided workflow definition. The instance can be loaded using a different definition, or updated using Dynamic Update.
```

### <a name="SxS"></a>Wykonywanie równoczesne przy użyciu właściwości WorkflowIdentity

<xref:System.Activities.WorkflowIdentity> może służyć do ułatwienia wykonywania wielu wersji przepływu pracy obok siebie. Jednym z typowych scenariuszy jest zmiana wymagań firmy na długotrwały przepływ pracy. Podczas wdrażania zaktualizowanej wersji można uruchomić wiele wystąpień przepływu pracy. Aplikacja hosta może być skonfigurowana do używania zaktualizowanej definicji przepływu pracy podczas uruchamiania nowych wystąpień i jest odpowiedzialna za aplikację hosta, aby zapewnić prawidłową definicję przepływu pracy podczas wznawiania wystąpień. <xref:System.Activities.WorkflowIdentity> może służyć do identyfikowania i dostarczania pasującej definicji przepływu pracy podczas wznawiania wystąpień przepływu pracy.

Aby można było pobrać <xref:System.Activities.WorkflowIdentity> wystąpienia utrwalonego przepływu pracy, używana jest metoda <xref:System.Activities.WorkflowApplication.GetInstance%2A>. Metoda <xref:System.Activities.WorkflowApplication.GetInstance%2A> przyjmuje <xref:System.Activities.WorkflowApplication.Id%2A> wystąpienia utrwalonego przepływu pracy oraz <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, który zawiera utrwalone wystąpienie i zwraca <xref:System.Activities.WorkflowApplicationInstance>. <xref:System.Activities.WorkflowApplicationInstance> zawiera informacje o utrwalonym wystąpieniu przepływu pracy, łącznie ze skojarzonymi <xref:System.Activities.WorkflowIdentity>. Ten skojarzony <xref:System.Activities.WorkflowIdentity> może być używany przez hosta w celu podania prawidłowej definicji przepływu pracy podczas ładowania i wznawiania wystąpienia przepływu pracy.

> [!NOTE]
> <xref:System.Activities.WorkflowIdentity> wartość null jest prawidłowa i może być używana przez hosta do mapowania wystąpień, które zostały utrwalone bez skojarzonego <xref:System.Activities.WorkflowIdentity> do odpowiedniej definicji przepływu pracy. Ten scenariusz może wystąpić, gdy aplikacja przepływu pracy nie została początkowo zapisywana przy użyciu wersji przepływu pracy lub gdy aplikacja jest uaktualniana z .NET Framework 4. Aby uzyskać więcej informacji, zobacz [uaktualnianie baz danych trwałości .NET Framework 4 w celu zapewnienia obsługi wersji przepływu pracy](using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases).

W poniższym przykładzie `Dictionary<WorkflowIdentity, Activity>` jest używany do kojarzenia wystąpień <xref:System.Activities.WorkflowIdentity> z ich pasującymi definicjami przepływów pracy, a przepływ pracy jest uruchamiany przy użyciu definicji przepływu pracy `MortgageWorkflow`, która jest skojarzona z `identityV1` <xref:System.Activities.WorkflowIdentity>.

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

W poniższym przykładzie informacje o utrwalonym wystąpieniu przepływu pracy z poprzedniego przykładu są pobierane przez wywołanie <xref:System.Activities.WorkflowApplication.GetInstance%2A>, a utrwalone informacje <xref:System.Activities.WorkflowIdentity> są używane do pobierania pasującej definicji przepływu pracy. Te informacje służą do konfigurowania <xref:System.Activities.WorkflowApplication>, a następnie ładowania przepływu pracy. Należy zauważyć, że ze względu na to, że jest używane Przeciążenie <xref:System.Activities.WorkflowApplication.Load%2A>, które pobiera <xref:System.Activities.WorkflowApplicationInstance>, <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, który został skonfigurowany na <xref:System.Activities.WorkflowApplicationInstance> jest używany przez <xref:System.Activities.WorkflowApplication>, dlatego nie trzeba konfigurować jego właściwości <xref:System.Activities.WorkflowApplication.InstanceStore%2A>.

> [!NOTE]
> Jeśli właściwość <xref:System.Activities.WorkflowApplication.InstanceStore%2A> jest ustawiona, musi być ustawiona z tym samym wystąpieniem <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> używanym przez <xref:System.Activities.WorkflowApplicationInstance> lub w przeciwnym razie <xref:System.ArgumentException> zostanie wygenerowany z następującym komunikatem: `The instance is configured with a different InstanceStore than this WorkflowApplication.`.

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

## <a name="UpdatingWF4PersistenceDatabases"></a>Uaktualnianie baz danych trwałości .NET Framework 4 w celu obsługi wersji przepływu pracy

Skrypt bazy danych SqlWorkflowInstanceStoreSchemaUpgrade. SQL jest dostarczany w celu uaktualnienia baz danych trwałości utworzonych przy użyciu skryptów bazy danych .NET Framework 4. Ten skrypt aktualizuje bazy danych programu w celu obsługi nowych możliwości przechowywania wersji wprowadzonych w .NET Framework 4,5. Wszystkie wystąpienia utrwalonych przepływów pracy w bazach danych otrzymują domyślne wartości wersji, a następnie mogą uczestniczyć w wykonywaniu równoczesnym i aktualizacji dynamicznej.

Jeśli aplikacja przepływu pracy .NET Framework 4,5 próbuje wykonać wszystkie operacje trwałości korzystające z nowych funkcji przechowywania wersji w bazie danych trwałości, która nie została uaktualniona przy użyciu dostarczonego skryptu, zostanie zgłoszony <xref:System.Runtime.DurableInstancing.InstancePersistenceCommandException> z komunikatem podobnym do poniższego komunikatu.

```output
The SqlWorkflowInstanceStore has a database version of '4.0.0.0'. InstancePersistenceCommand 'System.Activities.DurableInstancing.CreateWorkflowOwnerWithIdentityCommand' cannot be run against this database version.  Please upgrade the database to '4.5.0.0'.
```

### <a name="ToUpgrade"></a>Aby uaktualnić schemat bazy danych

1. Otwórz SQL Server Management Studio i nawiąż połączenie z serwerem bazy danych trwałości, na przykład **.\SQLEXPRESS**.

2. Wybierz polecenie **Otwórz**, **plik** z menu **plik** . Przejdź do następującego folderu: `C:\Windows\Microsoft.NET\Framework\4.0.30319\sql\en`

3. Wybierz **SqlWorkflowInstanceStoreSchemaUpgrade. SQL** , a następnie kliknij przycisk **Otwórz**.

4. Wybierz nazwę bazy danych trwałości z listy rozwijanej **dostępne bazy danych** .

5. Wybierz polecenie **Execute** z menu **zapytanie** .

Po zakończeniu wykonywania zapytania schemat bazy danych zostanie uaktualniony i w razie potrzeby można wyświetlić domyślną tożsamość przepływu pracy przypisaną do wystąpień utrwalonych przepływów pracy. Rozwiń swoją bazę danych trwałości w węźle **bazy danych** **Eksplorator obiektów**, a następnie rozwiń węzeł **widoki** . Kliknij prawym przyciskiem myszy pozycję **System. Activities. DurableInstancing. instances** i wybierz **pozycję Wybierz pierwsze 1000 wierszy**. Przewiń do końca kolumn i zwróć uwagę, że do widoku dodano sześć dodatkowych kolumn: **IdentityName**, **IdentityPackage**, **Build**, **główna**, **pomocnicza**i **poprawka**. Wszystkie utrwalone przepływy pracy będą mieć wartość **null** dla tych pól reprezentujących pustą tożsamość przepływu pracy.
