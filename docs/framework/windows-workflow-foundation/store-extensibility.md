---
title: Rozszerzalność magazynu
ms.date: 03/30/2017
ms.assetid: 7c3f4a46-4bac-4138-ae6a-a7c7ee0d28f5
ms.openlocfilehash: 8cfbf96256d4b8416beb526875a1e9ac09c3bfbb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="store-extensibility"></a>Rozszerzalność magazynu
<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Umożliwia użytkownikom wspierania właściwości niestandardowych, specyficzne dla aplikacji, które mogą być używane w zapytaniu dla wystąpień w bazie danych trwałości. Fakt podwyższania właściwości powoduje, że wartości mają być dostępne w widoku specjalne w bazie danych. Te awansowanej właściwości (właściwości, które mogą być używane w zapytaniach użytkownika) mogą być typy proste, takie jak Int64, identyfikator Guid, typ String i DateTime lub serializacji typu binarnego (byte[]).  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Klasa ma <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.Promote%2A> metodę, która służy do promowania właściwości jako właściwość, która może być używane w zapytaniach. Poniższy przykład jest przykładem end-to-end rozszerzalności magazynu.  
  
1.  W tym przykładowym scenariuszu dokumentu przetwarzania aplikacji (DP) ma przepływów pracy, w każdej z nich używa działań niestandardowych do przetwarzania dokumentu. Te przepływy pracy ustawić zmienne stanu, które muszą być widoczne dla użytkownika końcowego. Aby to osiągnąć, aplikacja DP udostępnia rozszerzenie wystąpienia typu <xref:System.Activities.Persistence.PersistenceParticipant>, używany do dostarczania zmienne stanu przez działania.  
  
    ```  
    class DocumentStatusExtension : PersistenceParticipant  
    {  
        public string DocumentId;  
        public string ApprovalStatus;  
        public string UserName;  
        public DateTime LastUpdateTime;  
    }  
    ```  
  
2.  Nowe rozszerzenie jest następnie dodawana do hosta.  
  
    ```  
    static Activity workflow = CreateWorkflow();  
    WorkflowApplication application = new WorkflowApplication(workflow);  
    DocumentStatusExtension documentStatusExtension = new DocumentStatusExtension ();  
    application.Extensions.Add(documentStatusExtension);  
    ```  
  
     Aby uzyskać więcej informacji o dodawaniu uczestnika trwałości niestandardowych, zobacz [uczestników trwałości](../../../docs/framework/windows-workflow-foundation/persistence-participants.md) próbki.  
  
3.  Działania niestandardowe w aplikacji DP wypełniania różnych pól stanu w **Execute** metody.  
  
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
  
4.  Gdy wystąpienia przepływu pracy osiągnie punkt trwałości **obiektu CollectValues** metody **DocumentStatusExtension** uczestnika trwałości zapisuje te właściwości do danych trwałości Kolekcja.  
  
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
    >  Te właściwości są przekazywane do **SqlWorkflowInstanceStore** przez platformę trwałości za pośrednictwem **SaveWorkflowCommand.InstanceData** kolekcji.  
  
5.  Aplikacja DP inicjuje w magazynie wystąpień przepływu pracy SQL i wywołuje **Podnieś poziom** metodę, aby podwyższyć poziom tych danych.  
  
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
  
     Na podstawie tych informacji podwyższania poziomu **SqlWorkflowInstanceStore** umieszcza właściwości danych w kolumnach [InstancePromotedProperties](#InstancePromotedProperties) widoku.
  
6.  Aby odpytać podzbiór danych z tabeli podwyższania poziomu, aplikacji DP dodaje dostosowany widok na widok podwyższania poziomu.  
  
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
  
##  <a name="InstancePromotedProperties"></a> Widok [System.Activities.DurableInstancing.InstancePromotedProperties]  
  
|Nazwa kolumny|Typ kolumny|Opis|  
|-----------------|-----------------|-----------------|  
|Identyfikator wystąpienia|Identyfikator GUID|Wystąpienie przepływu pracy, której należy ten podwyższania poziomu.|  
|PromotionName|Nvarchar(400)|Nazwa samej promocji.|  
|Wartość1, wartość2, Wartość3,..., Value32|sql_variant|Wartość awansowana samej właściwości. Większość typów pierwotnych danych SQL, z wyjątkiem binarnych obiektów blob i ciągi ponad 8000 bajtów długości można zmieścić w sql_variant.|  
|Value35 Value33, Value34,..., Value64|Varbinary(max)|Wartość awansowanej właściwości, które są jawnie deklarowane jako varbinary(max).|
