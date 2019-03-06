---
title: Za pomocą obiektu WorkflowIdentity i wersjonowanie
ms.date: 03/30/2017
ms.assetid: b8451735-8046-478f-912b-40870a6c0c3a
ms.openlocfilehash: ad1d3385801b451795c6be321094851339a55f81
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57373429"
---
# <a name="using-workflowidentity-and-versioning"></a>Za pomocą obiektu WorkflowIdentity i wersjonowanie
<xref:System.Activities.WorkflowIdentity> Umożliwia dla przepływu pracy deweloperów aplikacji, aby skojarzyć nazwę i <xref:System.Version> przy użyciu definicji przepływu pracy i te informacje, które ma zostać skojarzony z istniejącym wystąpieniem przepływu pracy. Informacje o tożsamości może służyć przez deweloperów aplikacji przepływu pracy można obsługiwać scenariusze takie jak side-by-side wykonywanie wielu wersji definicji przepływu pracy i zapewnia podstawę dla innych funkcji, takich jak aktualizacja dynamiczna. W tym temacie przedstawiono jako omówienie sposobu użycia <xref:System.Activities.WorkflowIdentity> z <xref:System.Activities.WorkflowApplication> hostingu. Aby uzyskać informacji na temat wykonywania side-by-side definicji przepływu pracy w usłudze przepływu pracy, zobacz [równoległe przechowywanie wersji w klasie WorkflowServiceHost](../../../docs/framework/wcf/feature-details/side-by-side-versioning-in-workflowservicehost.md). Aby uzyskać informacji na temat aktualizacji dynamicznej, zobacz [aktualizacji dynamicznej](../../../docs/framework/windows-workflow-foundation/dynamic-update.md).  
  
## <a name="in-this-topic"></a>W tym temacie:  
  
-   [Za pomocą obiektu WorkflowIdentity](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#UsingWorkflowIdentity)  
  
    -   [Wykonanie Side-by-side przy użyciu obiektu WorkflowIdentity](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#SxS)  
  
-   [Uaktualnianie platformy .NET Framework 4 trwałości baz danych w celu obsługi wersji przepływu pracy](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases)  
  
    -   [Aby uaktualnić schemat bazy danych](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#ToUpgrade)  
  
## <a name="UsingWorkflowIdentity"></a> Za pomocą obiektu WorkflowIdentity  
 Aby użyć <xref:System.Activities.WorkflowIdentity>, Utwórz wystąpienie, jest skonfigurowana i skojarz ją z <xref:System.Activities.WorkflowApplication> wystąpienia. A <xref:System.Activities.WorkflowIdentity> wystąpienie zawiera trzy identyfikujące informacje. <xref:System.Activities.WorkflowIdentity.Name%2A> i <xref:System.Activities.WorkflowIdentity.Version%2A> zawiera nazwy i <xref:System.Version> i są wymagane, i <xref:System.Activities.WorkflowIdentity.Package%2A> jest opcjonalna i może służyć do określenia dodatkowych ciąg zawierający informacje, takie jak nazwa zestawu lub inne żądane informacje. A <xref:System.Activities.WorkflowIdentity> są unikatowe, jeśli dowolny z jego trzy właściwości różnią się od innego <xref:System.Activities.WorkflowIdentity>.  
  
> [!IMPORTANT]
>  Element <xref:System.Activities.WorkflowIdentity> nie może zawierać wszelkie identyfikowalne dane osobowe (PII). Informacje o <xref:System.Activities.WorkflowIdentity> użyty do utworzenia wystąpienia jest emitowany do żadnych skonfigurowanych śledzenia cyklu życia usługi w wielu różnych punktach działania w czasie wykonywania. WF śledzenia nie ma żadnych mechanizmu, aby ukryć dane osobowe (poufne dane użytkowników). W związku z tym <xref:System.Activities.WorkflowIdentity> wystąpienia nie powinna zawierać wszystkie dane osobowe, ponieważ będzie emitowane przez środowisko uruchomieniowe w rekordy śledzenia i mogą być widoczne dla każda osoba mająca dostęp do wyświetlania rekordów śledzenia.  
  
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
  
 Podczas ponownego ładowania i wznawianie przepływu pracy, <xref:System.Activities.WorkflowIdentity> skonfigurowanego do dopasowania <xref:System.Activities.WorkflowIdentity> utrwalonych przepływu pracy można użyć wystąpienia.  
  
```csharp  
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identityV1);  
  
// Configure the WorkflowApplication with persistence and desired workflow event handlers.  
ConfigureWorkflowApplication(wfApp);  
  
// Load the workflow.  
wfApp.Load(instanceId);  
  
// Resume the workflow...  
```  
  
 Jeśli <xref:System.Activities.WorkflowIdentity> używany, gdy ponownie załadować wystąpienia przepływu pracy nie odpowiada utrwalonych <xref:System.Activities.WorkflowIdentity>, <xref:System.Activities.VersionMismatchException> zgłaszany. W poniższym przykładzie jest podejmowana próba załadowania `MortgageWorkflow` wystąpienia, który został zachowany w poprzednim przykładzie. Ta próba załadowania zostało nawiązane za pomocą <xref:System.Activities.WorkflowIdentity> skonfigurowany do nowszej wersji hipoteczny przepływu pracy, który nie pasuje do utrwalonego wystąpienia.  
  
```csharp  
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow_v2(), identityV2);  
  
// Configure the WorkflowApplication with persistence and desired workflow event handlers.  
ConfigureWorkflowApplication(wfApp);  
  
// Attempt to load the workflow instance.  
wfApp.Load(instanceId);  
  
// Resume the workflow...  
```  
  
 Po poprzednim kodzie jest wykonywana, sprawdzanie poniżej <xref:System.Activities.VersionMismatchException> zgłaszany.  
  
 **Obiektu WorkflowIdentity ("MortgageWorkflow v1; Wersja = 1.0.0.0') załadować wystąpienia nie jest zgodny obiektu WorkflowIdentity ("MortgageWorkflow v2; Wersja =' 2.0.0.0 lub nowszej) z Podana definicja przepływu pracy. Wystąpienie może być załadowany, przy użyciu różnych definicji lub zaktualizować przy użyciu aktualizacji dynamicznej.**  
### <a name="SxS"></a> Wykonanie Side-by-side przy użyciu obiektu WorkflowIdentity  
 <xref:System.Activities.WorkflowIdentity> może służyć do ułatwienia wykonywania wielu wersji przepływu pracy side-by-side. Jeden typowy scenariusz jest zmiana wymagań biznesowych w przepływie pracy długoterminowych. Wiele wystąpień przepływu pracy może być uruchomiony podczas wdrażania zaktualizowanej wersji. Aplikacja hosta można skonfigurować do użycia definicji przepływu pracy zaktualizowane podczas uruchamiania nowych wystąpień i jest odpowiedzialny za aplikacji hosta w celu umożliwienia definicji przepływu pracy prawidłowe w przypadku wznawiania wystąpień. <xref:System.Activities.WorkflowIdentity> może służyć do identyfikowania i dostarczyć pasujących definicji przepływu pracy, gdy wznowienie wystąpienia przepływu pracy.  
  
 Aby pobrać <xref:System.Activities.WorkflowIdentity> z istniejącym wystąpieniem przepływu pracy, <xref:System.Activities.WorkflowApplication.GetInstance%2A> metoda jest używana. <xref:System.Activities.WorkflowApplication.GetInstance%2A> Metoda przyjmuje <xref:System.Activities.WorkflowApplication.Id%2A> z istniejącym wystąpieniem przepływu pracy i <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> , zawierający utrwalonego wystąpienia, a funkcja zwraca <xref:System.Activities.WorkflowApplicationInstance>. A <xref:System.Activities.WorkflowApplicationInstance> zawiera informacje o istniejącym wystąpieniem przepływu pracy, w tym związanych z nią <xref:System.Activities.WorkflowIdentity>. To skojarzone <xref:System.Activities.WorkflowIdentity> może służyć przez hosta do dostarczania definicji poprawne przepływu pracy podczas ładowania i wznawianie działania wystąpienia przepływu pracy.  
  
> [!NOTE]
>  Wartość null <xref:System.Activities.WorkflowIdentity> jest prawidłowy i może służyć przez hosta do mapy wystąpień, które zostały utrwalone bez skojarzonych <xref:System.Activities.WorkflowIdentity> do definicji prawidłowego przepływu pracy. Ten scenariusz może wystąpić, gdy aplikacja przepływu pracy nie został początkowo zapisany z wersji przepływu pracy lub gdy aplikacja jest uaktualniany z [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]. Aby uzyskać więcej informacji, zobacz [uaktualnianie .NET Framework 4 trwałości baz danych do przechowywania wersji przepływu pracy obsługi](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases).  
  
 W poniższym przykładzie `Dictionary<WorkflowIdentity, Activity>` służy do kojarzenia <xref:System.Activities.WorkflowIdentity> wystąpień przy użyciu ich pasujących definicji przepływu pracy i przepływu pracy została uruchomiona przy użyciu `MortgageWorkflow` definicji przepływu pracy, który jest skojarzony z `identityV1` <xref:System.Activities.WorkflowIdentity>.  
  
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
  
 W poniższym przykładzie, informacje o istniejącym wystąpieniem przepływu pracy z poprzedniego przykładu jest pobierany przez wywołanie <xref:System.Activities.WorkflowApplication.GetInstance%2A>i utrwalonych <xref:System.Activities.WorkflowIdentity> informacje są używane do pobierania zgodnych definicji przepływu pracy. Te informacje są używane do konfigurowania <xref:System.Activities.WorkflowApplication>, a następnie załadowaniu przepływu pracy. Należy pamiętać, że ponieważ <xref:System.Activities.WorkflowApplication.Load%2A> przeciążenia przyjmującego <xref:System.Activities.WorkflowApplicationInstance> jest używany, <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> który został skonfigurowany na <xref:System.Activities.WorkflowApplicationInstance> jest używany przez <xref:System.Activities.WorkflowApplication> i dlatego jego <xref:System.Activities.WorkflowApplication.InstanceStore%2A> właściwości nie musi być skonfigurowany.  
  
> [!NOTE]
>  Jeśli <xref:System.Activities.WorkflowApplication.InstanceStore%2A> właściwość jest ustawiona, musi być ona równa o takiej samej <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> wystąpienia używanego przez <xref:System.Activities.WorkflowApplicationInstance> — w przeciwnym razie <xref:System.ArgumentException> zostanie zgłoszony następujący komunikat o błędzie: `The instance is configured with a different InstanceStore than this WorkflowApplication.`.  
  
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
  
## <a name="UpdatingWF4PersistenceDatabases"></a> Uaktualnianie platformy .NET Framework 4 trwałości baz danych w celu obsługi wersji przepływu pracy  
 Skrypt bazy danych SqlWorkflowInstanceStoreSchemaUpgrade.sql znajduje się do uaktualnienia bazy danych trwałości utworzone za pomocą [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] bazy danych skryptów. Ten skrypt aktualizacji bazy danych do obsługi nowych możliwości przechowywania wersji wprowadzonych w [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Wszystkie wystąpienia przepływu pracy utrwalonych w bazach danych są podane wartości wersji domyślnych, a następnie mogą brać udział w realizacji side-by-side i aktualizacji dynamicznej.  
  
 Jeśli [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] aplikacji przepływu pracy podejmuje wszystkie operacje trwałości korzystać z nowych funkcji przechowywania wersji dla bazy danych trwałości, który nie został uaktualniony przy użyciu dostarczonego skryptu <xref:System.Runtime.DurableInstancing.InstancePersistenceCommandException> generowany jest komunikat podobny do następującego Komunikat.  
  
 **SqlWorkflowInstanceStore ma wersję bazy danych "4.0.0.0". Nie można uruchomić InstancePersistenceCommand "System.Activities.DurableInstancing.CreateWorkflowOwnerWithIdentityCommand" przed tą wersją bazy danych.  Uaktualnij bazę danych do "4.5.0.0".**  
### <a name="ToUpgrade"></a> Aby uaktualnić schemat bazy danych  
  
1.  Otwórz program SQL Server Management Studio i połącz się z serwera bazy danych trwałości, na przykład **. \SQLEXPRESS**.  
  
2.  Wybierz **Otwórz**, **pliku** z **pliku** menu. Przejdź do następującego folderu: `C:\Windows\Microsoft.NET\Framework\4.0.30319\sql\en`  
  
3.  Wybierz **SqlWorkflowInstanceStoreSchemaUpgrade.sql** i kliknij przycisk **Otwórz**.  
  
4.  Wybierz nazwę bazy danych trwałości w **baz danych dostępności** listy rozwijanej.  
  
5.  Wybierz **Execute** z **zapytania** menu.  
  
 Po wykonaniu kwerendy schemat bazy danych jest uaktualniany, a jeśli to konieczne, można wyświetlić domyślną tożsamość przepływ pracy został przypisany do wystąpienia utrwalonych przepływu pracy. Rozwiń węzeł bazy danych trwałości w **baz danych** węźle **Eksplorator obiektów**, a następnie rozwiń węzeł **widoków** węzła. Kliknij prawym przyciskiem myszy **System.Activities.DurableInstancing.Instances** i wybierz polecenie **zaznacz 1000 pierwszych wierszy**. Przewiń do końca kolumn i należy pamiętać, że sześciu dodatkowe kolumny do widoku: **IdentityName**, **IdentityPackage**, **kompilacji**, **głównych**, **pomocnicza**, i **poprawki**. Utrwalonych przepływów pracy będzie mieć wartość **NULL** dla tych pól, reprezentujący identyfikator przepływu pracy o wartości null.
