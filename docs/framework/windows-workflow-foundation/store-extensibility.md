---
title: Rozszerzalność magazynu
ms.date: 03/30/2017
ms.assetid: 7c3f4a46-4bac-4138-ae6a-a7c7ee0d28f5
ms.openlocfilehash: 8cfbf96256d4b8416beb526875a1e9ac09c3bfbb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517923"
---
# <a name="store-extensibility"></a><span data-ttu-id="95325-102">Rozszerzalność magazynu</span><span class="sxs-lookup"><span data-stu-id="95325-102">Store Extensibility</span></span>
<span data-ttu-id="95325-103"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Umożliwia użytkownikom wspierania właściwości niestandardowych, specyficzne dla aplikacji, które mogą być używane w zapytaniu dla wystąpień w bazie danych trwałości.</span><span class="sxs-lookup"><span data-stu-id="95325-103"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> allows users to promote custom, application-specific properties that can be used to query for instances in the persistence database.</span></span> <span data-ttu-id="95325-104">Fakt podwyższania właściwości powoduje, że wartości mają być dostępne w widoku specjalne w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="95325-104">The act of promoting a property causes the value to be available within a special view in the database.</span></span> <span data-ttu-id="95325-105">Te awansowanej właściwości (właściwości, które mogą być używane w zapytaniach użytkownika) mogą być typy proste, takie jak Int64, identyfikator Guid, typ String i DateTime lub serializacji typu binarnego (byte[]).</span><span class="sxs-lookup"><span data-stu-id="95325-105">These promoted properties (properties that can be used in user queries) can be of simple types such as Int64, Guid, String, and DateTime or of a serialized binary type (byte[]).</span></span>  
  
 <span data-ttu-id="95325-106"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Klasa ma <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.Promote%2A> metodę, która służy do promowania właściwości jako właściwość, która może być używane w zapytaniach.</span><span class="sxs-lookup"><span data-stu-id="95325-106">The <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> class has the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.Promote%2A> method that you can use to promote a property as a property that can be used in queries.</span></span> <span data-ttu-id="95325-107">Poniższy przykład jest przykładem end-to-end rozszerzalności magazynu.</span><span class="sxs-lookup"><span data-stu-id="95325-107">The following example is an end-to-end example of store extensibility.</span></span>  
  
1.  <span data-ttu-id="95325-108">W tym przykładowym scenariuszu dokumentu przetwarzania aplikacji (DP) ma przepływów pracy, w każdej z nich używa działań niestandardowych do przetwarzania dokumentu.</span><span class="sxs-lookup"><span data-stu-id="95325-108">In this example scenario, a document processing (DP) application has workflows, each of which uses custom activities for document processing.</span></span> <span data-ttu-id="95325-109">Te przepływy pracy ustawić zmienne stanu, które muszą być widoczne dla użytkownika końcowego.</span><span class="sxs-lookup"><span data-stu-id="95325-109">These workflows have a set of state variables that need to be made visible to the end user.</span></span> <span data-ttu-id="95325-110">Aby to osiągnąć, aplikacja DP udostępnia rozszerzenie wystąpienia typu <xref:System.Activities.Persistence.PersistenceParticipant>, używany do dostarczania zmienne stanu przez działania.</span><span class="sxs-lookup"><span data-stu-id="95325-110">To achieve this, the DP application provides an instance extension of type <xref:System.Activities.Persistence.PersistenceParticipant>, which is used by activities to supply the state variables.</span></span>  
  
    ```  
    class DocumentStatusExtension : PersistenceParticipant  
    {  
        public string DocumentId;  
        public string ApprovalStatus;  
        public string UserName;  
        public DateTime LastUpdateTime;  
    }  
    ```  
  
2.  <span data-ttu-id="95325-111">Nowe rozszerzenie jest następnie dodawana do hosta.</span><span class="sxs-lookup"><span data-stu-id="95325-111">The new extension is then added to the host.</span></span>  
  
    ```  
    static Activity workflow = CreateWorkflow();  
    WorkflowApplication application = new WorkflowApplication(workflow);  
    DocumentStatusExtension documentStatusExtension = new DocumentStatusExtension ();  
    application.Extensions.Add(documentStatusExtension);  
    ```  
  
     <span data-ttu-id="95325-112">Aby uzyskać więcej informacji o dodawaniu uczestnika trwałości niestandardowych, zobacz [uczestników trwałości](../../../docs/framework/windows-workflow-foundation/persistence-participants.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="95325-112">For more details about adding a custom persistence participant, see the [Persistence Participants](../../../docs/framework/windows-workflow-foundation/persistence-participants.md) sample.</span></span>  
  
3.  <span data-ttu-id="95325-113">Działania niestandardowe w aplikacji DP wypełniania różnych pól stanu w **Execute** metody.</span><span class="sxs-lookup"><span data-stu-id="95325-113">The custom activities in the DP application populate various status fields in the **Execute** method.</span></span>  
  
    ```  
    public override void Execute(CodeActivityContext context)  
    {  
        // ...  
        context.GetExtension<DocumentStatusExtension>().DocumentId = Guid.NewGuid();  
        context.GetExtension<DocumentStatusExtension>().UserName = "John Smith";  
        context.GetExtension<DocumentStatusExtension>().ApprovalStatus = "Approved";  
        context.GetExtension<DocumentStatusExtension>().LastUpdateTime = DateTime.Now();  
        // ...  
    }  
    ```  
  
4.  <span data-ttu-id="95325-114">Gdy wystąpienia przepływu pracy osiągnie punkt trwałości **obiektu CollectValues** metody **DocumentStatusExtension** uczestnika trwałości zapisuje te właściwości do danych trwałości Kolekcja.</span><span class="sxs-lookup"><span data-stu-id="95325-114">When a workflow instance reaches a persistence point, the **CollectValues** method of the **DocumentStatusExtension** persistence participant saves these properties into the persistence data collection.</span></span>  
  
    ```  
    class DocumentStatusExtension : PersistenceParticipant  
    {  
        const XNamespace xNS = XNamespace.Get("http://contoso.com/DocumentStatus");  
  
        protected override void CollectValues(out IDictionary<XName, object> readWriteValues, out IDictionary<XName, object> writeOnlyValues)  
        {  
            readWriteValues = new Dictionary<XName, object>();  
            readWriteValues.Add(xNS.GetName("UserName"), this.UserName);  
            readWriteValues.Add(xNS.GetName("ApprovalStatus"), this.ApprovalStatus);  
            readWriteValues.Add(xNS.GetName("DocumentId"), this.DocumentId);  
            readWriteValues.Add(xNS.GetName("LastModifiedTime"), this.LastUpdateTime);  
  
            writeOnlyValues = null;  
        }  
        // ...  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="95325-115">Te właściwości są przekazywane do **SqlWorkflowInstanceStore** przez platformę trwałości za pośrednictwem **SaveWorkflowCommand.InstanceData** kolekcji.</span><span class="sxs-lookup"><span data-stu-id="95325-115">All these properties are passed to **SqlWorkflowInstanceStore** by the persistence framework through the **SaveWorkflowCommand.InstanceData** collection.</span></span>  
  
5.  <span data-ttu-id="95325-116">Aplikacja DP inicjuje w magazynie wystąpień przepływu pracy SQL i wywołuje **Podnieś poziom** metodę, aby podwyższyć poziom tych danych.</span><span class="sxs-lookup"><span data-stu-id="95325-116">The DP application initializes the SQL Workflow Instance Store and invokes the **Promote** method to promote this data.</span></span>  
  
    ```  
    SqlWorkflowInstanceStore store = new SqlWorkflowInstanceStore(connectionString);  
  
    List<XName> variantProperties = new List<XName>()   
    {   
        xNS.GetName("UserName"),   
        xNS.GetName("ApprovalStatus"),   
        xNS.GetName("DocumentId"),   
        xNS.GetName("LastModifiedTime")   
    };  
  
    store.Promote("DocumentStatus", variantProperties, null);  
    ```  
  
     <span data-ttu-id="95325-117">Na podstawie tych informacji podwyższania poziomu **SqlWorkflowInstanceStore** umieszcza właściwości danych w kolumnach [InstancePromotedProperties](#InstancePromotedProperties) widoku.</span><span class="sxs-lookup"><span data-stu-id="95325-117">Based on this promotion information, **SqlWorkflowInstanceStore** places the data properties in the columns of the [InstancePromotedProperties](#InstancePromotedProperties) view.</span></span>
  
6.  <span data-ttu-id="95325-118">Aby odpytać podzbiór danych z tabeli podwyższania poziomu, aplikacji DP dodaje dostosowany widok na widok podwyższania poziomu.</span><span class="sxs-lookup"><span data-stu-id="95325-118">To query a subset of the data from the promotion table, the DP application adds a customized view on top of the promotion view.</span></span>  
  
    ```  
    create view [dbo].[DocumentStatus] with schemabinding  
    as  
        select  P.[InstanceId] as [InstanceId],  
            P.Value1 as [UserName],  
            P.Value2 as [ApprovalStatus],  
            P.Value3 as [DocumentId],  
            P.Value4 as [LastUpdatedTime]  
    from [System.Activities.DurableInstancing].[InstancePromotedProperties] as P  
    where P.PromotionName = N'DocumentStatus'  
    go  
    ```  
  
##  <a name="InstancePromotedProperties"></a> <span data-ttu-id="95325-119">Widok [System.Activities.DurableInstancing.InstancePromotedProperties]</span><span class="sxs-lookup"><span data-stu-id="95325-119">[System.Activities.DurableInstancing.InstancePromotedProperties] view</span></span>  
  
|<span data-ttu-id="95325-120">Nazwa kolumny</span><span class="sxs-lookup"><span data-stu-id="95325-120">Column Name</span></span>|<span data-ttu-id="95325-121">Typ kolumny</span><span class="sxs-lookup"><span data-stu-id="95325-121">Column Type</span></span>|<span data-ttu-id="95325-122">Opis</span><span class="sxs-lookup"><span data-stu-id="95325-122">Description</span></span>|  
|-----------------|-----------------|-----------------|  
|<span data-ttu-id="95325-123">Identyfikator wystąpienia</span><span class="sxs-lookup"><span data-stu-id="95325-123">InstanceId</span></span>|<span data-ttu-id="95325-124">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="95325-124">GUID</span></span>|<span data-ttu-id="95325-125">Wystąpienie przepływu pracy, której należy ten podwyższania poziomu.</span><span class="sxs-lookup"><span data-stu-id="95325-125">The workflow instance that this promotion belongs to.</span></span>|  
|<span data-ttu-id="95325-126">PromotionName</span><span class="sxs-lookup"><span data-stu-id="95325-126">PromotionName</span></span>|<span data-ttu-id="95325-127">Nvarchar(400)</span><span class="sxs-lookup"><span data-stu-id="95325-127">nvarchar(400)</span></span>|<span data-ttu-id="95325-128">Nazwa samej promocji.</span><span class="sxs-lookup"><span data-stu-id="95325-128">The name of the promotion itself.</span></span>|  
|<span data-ttu-id="95325-129">Wartość1, wartość2, Wartość3,..., Value32</span><span class="sxs-lookup"><span data-stu-id="95325-129">Value1, Value2, Value3,..,Value32</span></span>|<span data-ttu-id="95325-130">sql_variant</span><span class="sxs-lookup"><span data-stu-id="95325-130">sql_variant</span></span>|<span data-ttu-id="95325-131">Wartość awansowana samej właściwości.</span><span class="sxs-lookup"><span data-stu-id="95325-131">The value of the promoted property itself.</span></span> <span data-ttu-id="95325-132">Większość typów pierwotnych danych SQL, z wyjątkiem binarnych obiektów blob i ciągi ponad 8000 bajtów długości można zmieścić w sql_variant.</span><span class="sxs-lookup"><span data-stu-id="95325-132">Most SQL primitive data types except binary blobs and strings over 8000 bytes in length can fit in sql_variant.</span></span>|  
|<span data-ttu-id="95325-133">Value35 Value33, Value34,..., Value64</span><span class="sxs-lookup"><span data-stu-id="95325-133">Value33, Value34, Value35, …, Value64</span></span>|<span data-ttu-id="95325-134">Varbinary(max)</span><span class="sxs-lookup"><span data-stu-id="95325-134">varbinary(max)</span></span>|<span data-ttu-id="95325-135">Wartość awansowanej właściwości, które są jawnie deklarowane jako varbinary(max).</span><span class="sxs-lookup"><span data-stu-id="95325-135">The value of promoted properties that are explicitly declared as varbinary(max).</span></span>|
