---
title: Używanie obiektu WorkflowIdentity i wersjonowanie
ms.date: 03/30/2017
ms.assetid: b8451735-8046-478f-912b-40870a6c0c3a
ms.openlocfilehash: 6b769224edcd9dfc51879c2c99e061a0e3f77e8d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958391"
---
# <a name="using-workflowidentity-and-versioning"></a>Używanie obiektu WorkflowIdentity i wersjonowanie

<xref:System.Activities.WorkflowIdentity>umożliwia deweloperom aplikacji przepływu pracy kojarzenie nazw i <xref:System.Version> z definicją przepływu pracy oraz dla tych informacji, które mają być skojarzone z utrwalonym wystąpieniem przepływu pracy. Te informacje o tożsamości mogą być używane przez deweloperów aplikacji przepływu pracy do włączania scenariuszy, takich jak wykonywanie równoczesne wielu wersji definicji przepływu pracy i udostępniają one podstawę do innych funkcji, takich jak aktualizacja dynamiczna. Ten temat zawiera omówienie korzystania <xref:System.Activities.WorkflowIdentity> z programu z <xref:System.Activities.WorkflowApplication> obsługą programu. Aby uzyskać informacje na temat wykonywania operacji równoległych w definicjach przepływu pracy w usłudze przepływu pracy, zobacz [obok siebie przechowywanie wersji obok siebie w obszarze WorkflowServiceHost](../wcf/feature-details/side-by-side-versioning-in-workflowservicehost.md). Aby uzyskać informacje na temat aktualizacji dynamicznej, zobacz [Aktualizacja dynamiczna](dynamic-update.md).

## <a name="in-this-topic"></a>W tym temacie:

- [Korzystanie z właściwości WorkflowIdentity](using-workflowidentity-and-versioning.md#UsingWorkflowIdentity)

  - [Wykonywanie równoczesne przy użyciu właściwości WorkflowIdentity](using-workflowidentity-and-versioning.md#SxS)

- [Uaktualnianie baz danych trwałości .NET Framework 4 w celu obsługi wersji przepływu pracy](using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases)

  - [Aby uaktualnić schemat bazy danych](using-workflowidentity-and-versioning.md#ToUpgrade)

## <a name="UsingWorkflowIdentity"></a>Korzystanie z właściwości WorkflowIdentity

Aby użyć <xref:System.Activities.WorkflowIdentity>, Utwórz wystąpienie, skonfiguruj je i skojarz <xref:System.Activities.WorkflowApplication> z wystąpieniem. <xref:System.Activities.WorkflowIdentity> Wystąpienie zawiera trzy tożsamości informacji. <xref:System.Activities.WorkflowIdentity.Name%2A>i <xref:System.Activities.WorkflowIdentity.Version%2A> zawiera nazwę <xref:System.Version> i <xref:System.Activities.WorkflowIdentity.Package%2A> i są wymagane i jest opcjonalne i może służyć do określenia dodatkowego ciągu zawierającego informacje takie jak nazwa zestawu lub inne żądane informacje. Jest <xref:System.Activities.WorkflowIdentity> unikatowa, jeśli którykolwiek z jego trzech właściwości różni się od <xref:System.Activities.WorkflowIdentity>innego.

> [!IMPORTANT]
> A <xref:System.Activities.WorkflowIdentity> nie powinna zawierać żadnych informacji umożliwiających identyfikację użytkownika. Informacje o <xref:System.Activities.WorkflowIdentity> użytym do utworzenia wystąpienia są emitowane do wszelkich skonfigurowanych usług śledzenia w kilku różnych punktach cyklu życia działania przez środowisko uruchomieniowe. Śledzenie WF nie ma żadnego mechanizmu ukrywania danych osobowych (poufne dane użytkownika). W związku z tym wystąpienieniepowinnozawieraćżadnychdanychosobowych,ponieważbędzieemitowaneprzezśrodowiskouruchomieniowewceluśledzeniarekordówimożebyćwidocznedlakażdego,ktomadostępdowyświetlaniarekordówśledzenia.<xref:System.Activities.WorkflowIdentity>

W poniższym przykładzie <xref:System.Activities.WorkflowIdentity> jest tworzona i skojarzona z wystąpieniem przepływu pracy utworzonego `MortgageWorkflow` przy użyciu definicji przepływu pracy.

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

Po ponownym załadowaniu i wznowieniu przepływu pracy <xref:System.Activities.WorkflowIdentity> , który jest skonfigurowany do <xref:System.Activities.WorkflowIdentity> dopasowania do wystąpienia utrwalonego przepływu pracy, musi być używany.

```csharp
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identityV1);

// Configure the WorkflowApplication with persistence and desired workflow event handlers.
ConfigureWorkflowApplication(wfApp);

// Load the workflow.
wfApp.Load(instanceId);

// Resume the workflow...
```

Jeśli używany podczas ponownego ładowania wystąpienia przepływu pracy nie <xref:System.Activities.VersionMismatchException> jest zgodny z utrwalonym <xref:System.Activities.WorkflowIdentity>, zostanie zgłoszony. <xref:System.Activities.WorkflowIdentity> W poniższym przykładzie podjęto próbę `MortgageWorkflow` załadowania wystąpienia, które było utrwalone w poprzednim przykładzie. Ta próba załadowania została wykonana przy <xref:System.Activities.WorkflowIdentity> użyciu skonfigurowanej dla nowszej wersji przepływu pracy hipotecznej, która nie jest zgodna z utrwalonym wystąpieniem.

```csharp
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow_v2(), identityV2);

// Configure the WorkflowApplication with persistence and desired workflow event handlers.
ConfigureWorkflowApplication(wfApp);

// Attempt to load the workflow instance.
wfApp.Load(instanceId);

// Resume the workflow...
```

Gdy poprzedni kod jest wykonywany, zgłaszane są następujące <xref:System.Activities.VersionMismatchException> elementy.

```
The WorkflowIdentity ('MortgageWorkflow v1; Version=1.0.0.0') of the loaded instance does not match the WorkflowIdentity ('MortgageWorkflow v2; Version=2.0.0.0') of the provided workflow definition. The instance can be loaded using a different definition, or updated using Dynamic Update.
```

### <a name="SxS"></a>Wykonywanie równoczesne przy użyciu właściwości WorkflowIdentity

<xref:System.Activities.WorkflowIdentity>może służyć do ułatwienia wykonywania wielu wersji przepływu pracy obok siebie. Jednym z typowych scenariuszy jest zmiana wymagań firmy na długotrwały przepływ pracy. Podczas wdrażania zaktualizowanej wersji można uruchomić wiele wystąpień przepływu pracy. Aplikacja hosta może być skonfigurowana do używania zaktualizowanej definicji przepływu pracy podczas uruchamiania nowych wystąpień i jest odpowiedzialna za aplikację hosta, aby zapewnić prawidłową definicję przepływu pracy podczas wznawiania wystąpień. <xref:System.Activities.WorkflowIdentity>może służyć do identyfikowania i dostarczania pasującej definicji przepływu pracy podczas wznawiania wystąpień przepływu pracy.

Aby można było <xref:System.Activities.WorkflowIdentity> pobrać wystąpienie utrwalonego przepływu pracy <xref:System.Activities.WorkflowApplication.GetInstance%2A> , metoda jest używana. Metoda przyjmuje wystąpienie utrwalonego <xref:System.Activities.WorkflowApplicationInstance>przepływu pracy i zawierawystąpienieutrwalaneizwracawartość.<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> <xref:System.Activities.WorkflowApplication.Id%2A> <xref:System.Activities.WorkflowApplication.GetInstance%2A> A <xref:System.Activities.WorkflowApplicationInstance> zawiera informacje o utrwalonym wystąpieniu przepływu pracy, w tym <xref:System.Activities.WorkflowIdentity>jego skojarzone. Ta skojarzona <xref:System.Activities.WorkflowIdentity> może być używana przez hosta w celu dostarczenia prawidłowej definicji przepływu pracy podczas ładowania i wznawiania wystąpienia przepływu pracy.

> [!NOTE]
> Wartość null <xref:System.Activities.WorkflowIdentity> jest prawidłowa i może być używana przez hosta w celu mapowania wystąpień, które zostały utrwalone bez skojarzonych <xref:System.Activities.WorkflowIdentity> z prawidłową definicją przepływu pracy. Ten scenariusz może wystąpić, gdy aplikacja przepływu pracy nie została początkowo zapisywana przy użyciu wersji przepływu pracy lub gdy aplikacja jest uaktualniana z programu [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]. Aby uzyskać więcej informacji, zobacz [uaktualnianie baz danych trwałości .NET Framework 4 w celu zapewnienia obsługi wersji przepływu pracy](using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases).

W poniższym przykładzie `Dictionary<WorkflowIdentity, Activity>` jest używany do kojarzenia <xref:System.Activities.WorkflowIdentity> wystąpień z pasującymi definicjami przepływów pracy, a `MortgageWorkflow` przepływ pracy jest uruchamiany przy użyciu definicji `identityV1` przepływu pracy, która jest skojarzona z <xref:System.Activities.WorkflowIdentity>.

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

W poniższym przykładzie informacje o utrwalonym wystąpieniu przepływu pracy z poprzedniego przykładu są pobierane przez wywołanie <xref:System.Activities.WorkflowApplication.GetInstance%2A>, a utrwalone <xref:System.Activities.WorkflowIdentity> informacje są używane do pobierania pasującej definicji przepływu pracy. Te informacje służą do konfigurowania <xref:System.Activities.WorkflowApplication>, a następnie ładowania przepływu pracy. Należy zauważyć, że <xref:System.Activities.WorkflowApplication.Load%2A> ponieważ Przeciążenie, które <xref:System.Activities.WorkflowApplicationInstance> pobiera, jest używane <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> , który <xref:System.Activities.WorkflowApplication> został skonfigurowany na <xref:System.Activities.WorkflowApplicationInstance> , jest używany przez i dlatego jego <xref:System.Activities.WorkflowApplication.InstanceStore%2A> właściwości nie trzeba konfigurować.

> [!NOTE]
> `The instance is configured with a different InstanceStore than this WorkflowApplication.` <xref:System.ArgumentException> <xref:System.Activities.WorkflowApplicationInstance> <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Jeśli właściwość jest ustawiona, musi być ustawiona z tym samym wystąpieniem, które jest używane przez lub w przeciwnym razie zostanie wygenerowany z następującym komunikatem:. <xref:System.Activities.WorkflowApplication.InstanceStore%2A>

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

Do uaktualniania baz danych trwałości utworzonych przy użyciu [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] skryptów bazy danych jest dostępny skrypt usługi SqlWorkflowInstanceStoreSchemaUpgrade. SQL. Ten skrypt aktualizuje bazy danych programu w celu obsługi nowych możliwości przechowywania wersji wprowadzonych w .NET Framework 4,5. Wszystkie wystąpienia utrwalonych przepływów pracy w bazach danych otrzymują domyślne wartości wersji, a następnie mogą uczestniczyć w wykonywaniu równoczesnym i aktualizacji dynamicznej.

Jeśli aplikacja przepływu pracy .NET Framework 4,5 próbuje wykonać wszystkie operacje trwałości korzystające z nowych funkcji przechowywania wersji w bazie danych trwałości, która nie została uaktualniona przy użyciu dostarczonego skryptu, <xref:System.Runtime.DurableInstancing.InstancePersistenceCommandException> zgłaszany jest komunikat podobny do następujący komunikat.

```
The SqlWorkflowInstanceStore has a database version of '4.0.0.0'. InstancePersistenceCommand 'System.Activities.DurableInstancing.CreateWorkflowOwnerWithIdentityCommand' cannot be run against this database version.  Please upgrade the database to '4.5.0.0'.
```

### <a name="ToUpgrade"></a>Aby uaktualnić schemat bazy danych

1. Otwórz SQL Server Management Studio i nawiąż połączenie z serwerem bazy danych trwałości, na przykład **.\SQLEXPRESS**.

2. Wybierz polecenie **Otwórz**, **plik** z menu **plik** . Przejdź do następującego folderu:`C:\Windows\Microsoft.NET\Framework\4.0.30319\sql\en`

3. Wybierz **SqlWorkflowInstanceStoreSchemaUpgrade. SQL** , a następnie kliknij przycisk **Otwórz**.

4. Wybierz nazwę bazy danych trwałości z listy rozwijanej **dostępne bazy danych** .

5. Wybierz polecenie **Execute** z menu **zapytanie** .

Po zakończeniu wykonywania zapytania schemat bazy danych zostanie uaktualniony i w razie potrzeby można wyświetlić domyślną tożsamość przepływu pracy przypisaną do wystąpień utrwalonych przepływów pracy. Rozwiń swoją bazę danych trwałości w węźle **bazy danych** **Eksplorator obiektów**, a następnie rozwiń węzeł **widoki** . Kliknij prawym przyciskiem myszy pozycję **System. Activities. DurableInstancing. instances** i wybierz **pozycję Wybierz pierwsze 1000 wierszy**. Przewiń do końca kolumn i zwróć uwagę, że do widoku dodano sześć dodatkowych kolumn: **IdentityName**, **IdentityPackage**, **Build**, **główna**, **pomocnicza**i **poprawka**. Wszystkie utrwalone przepływy pracy będą mieć wartość **null** dla tych pól reprezentujących pustą tożsamość przepływu pracy.
