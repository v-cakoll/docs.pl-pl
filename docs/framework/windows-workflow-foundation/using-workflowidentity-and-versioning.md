---
title: "Za pomocą właściwości WorkflowIdentity i kontroli wersji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b8451735-8046-478f-912b-40870a6c0c3a
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 033392276fb233bc1baa6c2af372a844e06a7d62
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="using-workflowidentity-and-versioning"></a>Za pomocą właściwości WorkflowIdentity i kontroli wersji
<xref:System.Activities.WorkflowIdentity>zapewnia sposób przepływu pracy z deweloperami aplikacji, aby skojarzyć nazwę i <xref:System.Version> z definicją przepływu pracy, a te informacje mają być skojarzone z wystąpieniem przepływu pracy utrwalonych. Informacje o tożsamości mogą posłużyć deweloperzy aplikacji przepływu pracy na potrzeby scenariuszy, takich jak side-by-side wykonywanie wielu wersji definicji przepływu pracy i udostępnia inne funkcje, takie jak aktualizacja dynamiczna podstawy. W tym temacie przedstawiono jako omówienie używania <xref:System.Activities.WorkflowIdentity> z <xref:System.Activities.WorkflowApplication> hosting. Aby uzyskać informacje na wykonanie side-by-side definicji przepływu pracy w usłudze przepływu pracy, zobacz [równoległe przechowywanie wersji w klasie WorkflowServiceHost](../../../docs/framework/wcf/feature-details/side-by-side-versioning-in-workflowservicehost.md). Uzyskać informacji dotyczących aktualizacji dynamicznej, zobacz [aktualizacji dynamicznej](../../../docs/framework/windows-workflow-foundation/dynamic-update.md).  
  
## <a name="in-this-topic"></a>W tym temacie:  
  
-   [Za pomocą właściwości WorkflowIdentity](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#UsingWorkflowIdentity)  
  
    -   [Wykonanie Side-by-side za pomocą właściwości WorkflowIdentity](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#SxS)  
  
-   [Uaktualnianie .NET Framework 4 trwałości baz danych obsługi przechowywania wersji przepływu pracy](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases)  
  
    -   [Aby uaktualnić schemat bazy danych](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#ToUpgrade)  
  
##  <a name="UsingWorkflowIdentity"></a>Za pomocą właściwości WorkflowIdentity  
 Aby użyć <xref:System.Activities.WorkflowIdentity>, Utwórz wystąpienie jest skonfigurowana i skojarzyć go z <xref:System.Activities.WorkflowApplication> wystąpienia. A <xref:System.Activities.WorkflowIdentity> wystąpienie zawiera trzy identyfikujące informacje. <xref:System.Activities.WorkflowIdentity.Name%2A>i <xref:System.Activities.WorkflowIdentity.Version%2A> zawiera nazwy i <xref:System.Version> i są wymagane, i <xref:System.Activities.WorkflowIdentity.Package%2A> jest opcjonalna i może służyć do określenia dodatkowych ciąg zawierający informacje, takie jak nazwa zestawu lub inne potrzebne informacje. A <xref:System.Activities.WorkflowIdentity> jest unikatowa, jeśli żadnego z trzech właściwości różnią się od siebie <xref:System.Activities.WorkflowIdentity>.  
  
> [!IMPORTANT]
>  A <xref:System.Activities.WorkflowIdentity> nie powinna zawierać żadnych informacji osobistych (dane osobowe). Informacje o <xref:System.Activities.WorkflowIdentity> użyty do utworzenia wystąpienia jest emitowany do żadnych skonfigurowanych śledzenia cyklu życia usług w wielu różnych punktach działania w czasie wykonywania. WF śledzenia nie ma żadnych mechanizmu, aby ukryć dane osobowe (poufne dane użytkowników). W związku z tym <xref:System.Activities.WorkflowIdentity> wystąpienia nie powinna zawierać żadnych danych dane osobowe, ponieważ zostanie wyemitowany przez środowisko uruchomieniowe w śledzenia rekordów i mogą być widoczne dla każda osoba mająca dostęp do wyświetlania rekordów śledzenia.  
  
 W poniższym przykładzie <xref:System.Activities.WorkflowIdentity> skojarzonego z wystąpieniem przepływu pracy utworzony za pomocą `MortgageWorkflow` definicji przepływu pracy.  
  
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
  
 Po ponownym załadowaniu i wznawianie przepływu pracy, <xref:System.Activities.WorkflowIdentity> skonfigurowanego do dopasowania <xref:System.Activities.WorkflowIdentity> utrwalonego przepływu pracy można użyć wystąpienia.  
  
```csharp  
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identityV1);  
  
// Configure the WorkflowApplication with persistence and desired workflow event handlers.  
ConfigureWorkflowApplication(wfApp);  
  
// Load the workflow.  
wfApp.Load(instanceId);  
  
// Resume the workflow...  
```  
  
 Jeśli <xref:System.Activities.WorkflowIdentity> używany, gdy ponowne ładowanie wystąpienia przepływu pracy jest niezgodny utrwalonego <xref:System.Activities.WorkflowIdentity>, <xref:System.Activities.VersionMismatchException> jest generowany. W poniższym przykładzie jest podejmowana próba załadowania `MortgageWorkflow` wystąpienie, które zostało utrwalone w poprzednim przykładzie. Ta próba załadowania jest wprowadzone za pomocą <xref:System.Activities.WorkflowIdentity> skonfigurowany do nowszej wersji przepływu pracy hipoteczne, który jest niezgodny z trwałego wystąpienia.  
  
```csharp  
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow_v2(), identityV2);  
  
// Configure the WorkflowApplication with persistence and desired workflow event handlers.  
ConfigureWorkflowApplication(wfApp);  
  
// Attempt to load the workflow instance.  
wfApp.Load(instanceId);  
  
// Resume the workflow...  
```  
  
 Jeśli poprzedni kod jest wykonywana, następujące <xref:System.Activities.VersionMismatchException> jest generowany.  
  
 **Wartość właściwości WorkflowIdentity ("MortgageWorkflow v1; Wersja = 1.0.0.0') załadowanego wystąpienia nie pasuje wartość właściwości WorkflowIdentity ("MortgageWorkflow v2; Wersja = 2.0.0.0') definicji podana przepływu pracy. Wystąpienie można załadować przy użyciu innej definicji lub zaktualizować za pomocą aktualizacji dynamicznej.**  
###  <a name="SxS"></a>Wykonanie Side-by-side za pomocą właściwości WorkflowIdentity  
 <xref:System.Activities.WorkflowIdentity>można ułatwić wykonywanie wielu wersji przepływu pracy side-by-side. Typowy scenariusz jeden zmienia wymagań biznesowych w przepływie pracy długotrwałe. Wiele wystąpień przepływu pracy może być uruchomiony po wdrożeniu zaktualizowanej wersji. Aplikacja hosta można skonfigurować do używania definicji zaktualizowany przepływ pracy, podczas uruchamiania nowych wystąpień i jest zobowiązany do definicji przepływu pracy poprawne podczas wznawiania wystąpień aplikacji hosta. <xref:System.Activities.WorkflowIdentity>może służyć do identyfikowania i podać pasującego definicji przepływu pracy, podczas wznawiania wystąpienia przepływu pracy.  
  
 Aby pobrać <xref:System.Activities.WorkflowIdentity> wystąpienia utrwalonego przepływu pracy, <xref:System.Activities.WorkflowApplication.GetInstance%2A> metoda jest używana. <xref:System.Activities.WorkflowApplication.GetInstance%2A> Ma metodę <xref:System.Activities.WorkflowApplication.Id%2A> wystąpienia utrwalonego przepływu pracy i <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> który zawiera trwałego wystąpienia i zwraca <xref:System.Activities.WorkflowApplicationInstance>. A <xref:System.Activities.WorkflowApplicationInstance> zawiera informacje dotyczące wystąpienia utrwalonego przepływu pracy, włącznie z jego skojarzony <xref:System.Activities.WorkflowIdentity>. To skojarzone <xref:System.Activities.WorkflowIdentity> hosta można podać definicji przepływu pracy poprawne podczas ładowania i wznawianie działania wystąpienia przepływu pracy.  
  
> [!NOTE]
>  Wartość null <xref:System.Activities.WorkflowIdentity> jest prawidłowy i może służyć przez hosta do mapowania wystąpień, które zostały utrwalone bez skojarzonych <xref:System.Activities.WorkflowIdentity> do definicji przepływu pracy właściwe. Ten scenariusz może mieć miejsce, gdy aplikacja przepływu pracy nie został początkowo zapisany z wersji przepływu pracy lub gdy aplikacja jest uaktualniana [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][.NET Framework 4 trwałości baz danych obsługi przechowywania wersji przepływu pracy uaktualniania](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases).  
  
 W poniższym przykładzie `Dictionary<WorkflowIdentity, Activity>` służy do kojarzenia <xref:System.Activities.WorkflowIdentity> wystąpień z ich pasującego definicji przepływu pracy i przepływu pracy została uruchomiona przy użyciu `MortgageWorkflow` definicji przepływu pracy, który jest skojarzony z `identityV1` <xref:System.Activities.WorkflowIdentity>.  
  
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
  
 W poniższym przykładzie informacji na temat wystąpienia przepływu pracy utrwalonych z poprzedniego przykładu jest pobranej poprzez wywołanie <xref:System.Activities.WorkflowApplication.GetInstance%2A>i utrwalonego <xref:System.Activities.WorkflowIdentity> informacji służy do pobierania pasującego definicji przepływu pracy. Te informacje jest używany do konfigurowania <xref:System.Activities.WorkflowApplication>, a następnie przepływ pracy został załadowany. Należy pamiętać, że ponieważ <xref:System.Activities.WorkflowApplication.Load%2A> przeciążenia, które przyjmuje <xref:System.Activities.WorkflowApplicationInstance> jest używana, <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> który został skonfigurowany na <xref:System.Activities.WorkflowApplicationInstance> jest używany przez <xref:System.Activities.WorkflowApplication> i dlatego jego <xref:System.Activities.WorkflowApplication.InstanceStore%2A> właściwości nie musi być skonfigurowany.  
  
> [!NOTE]
>  Jeśli <xref:System.Activities.WorkflowApplication.InstanceStore%2A> jest ustawiona właściwość, należy ją ustawić taką samą <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> wystąpienie używane przez <xref:System.Activities.WorkflowApplicationInstance> w przeciwnym razie <xref:System.ArgumentException> zostanie zgłoszony następujący komunikat o błędzie: `The instance is configured with a different InstanceStore than this WorkflowApplication.`.  
  
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
  
##  <a name="UpdatingWF4PersistenceDatabases"></a>Uaktualnianie .NET Framework 4 trwałości baz danych obsługi przechowywania wersji przepływu pracy  
 Podano SqlWorkflowInstanceStoreSchemaUpgrade.sql skryptu bazy danych do uaktualnienia trwałości baz danych utworzonych przy użyciu [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] bazy danych skryptów. Ten skrypt aktualizacji bazy danych do obsługi nowych funkcji przechowywania wersji wprowadzone w systemie [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Żadnych wystąpień utrwalonych przepływów pracy w bazach danych są podane wartości domyślne przechowywanie wersji, a następnie mogą uczestniczyć w realizacji side-by-side i aktualizacji dynamicznej.  
  
 Jeśli [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] aplikacji przepływu pracy próbuje korzystać z nowych funkcji przechowywania wersji w bazie danych trwałości, który nie został uaktualniony używając udostępnionego skryptu, wszystkie operacje utrwalania <xref:System.Runtime.DurableInstancing.InstancePersistenceCommandException> jest generowany komunikat podobny do następującego Komunikat.  
  
 **Obiekt SqlWorkflowInstanceStore ma bazę danych w wersji "4.0.0.0". Nie można uruchomić polecenia InstancePersistenceCommand "System.Activities.DurableInstancing.CreateWorkflowOwnerWithIdentityCommand" przed tą wersją bazy danych.  Uaktualnij bazę danych do "4.5.0.0".**  
###  <a name="ToUpgrade"></a>Aby uaktualnić schemat bazy danych  
  
1.  Otwórz program SQL Server Management Studio i połącz się trwałości serwera bazy danych, na przykład **. \SQLEXPRESS**.  
  
2.  Wybierz **Otwórz**, **pliku** z **pliku** menu. Przejdź do folderu:`C:\Windows\Microsoft.NET\Framework\4.0.30319\sql\en`  
  
3.  Wybierz **SqlWorkflowInstanceStoreSchemaUpgrade.sql** i kliknij przycisk **Otwórz**.  
  
4.  Wybierz nazwę bazy danych trwałości w **dostępnych baz danych** listy rozwijanej.  
  
5.  Wybierz **Execute** z **zapytania** menu.  
  
 Po wykonaniu kwerendy schemat bazy danych jest uaktualniony, a w razie potrzeby można wyświetlić domyślną tożsamością przepływu pracy została przypisana do wystąpień utrwalonych przepływów pracy. Rozwiń węzeł bazy danych trwałości w **baz danych** węzła **Eksplorator obiektów**, a następnie rozwiń węzeł **widoków** węzła. Kliknij prawym przyciskiem myszy **System.Activities.DurableInstancing.Instances** i wybierz polecenie **zaznacz 1000 pierwszych wierszy**. Przewiń do końca kolumn i pamiętaj, że jest sześciu dodatkowych kolumn do widoku: **IdentityName**, **IdentityPackage**, **kompilacji**, **głównych** , **Pomocnicza**, i **poprawki**. Utrwalonych przepływów pracy będzie mieć wartość **NULL** dla tych pól reprezentujących tożsamości null przepływu pracy.
