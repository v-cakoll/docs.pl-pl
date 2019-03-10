---
title: Rozszerzalność Store
ms.date: 03/30/2017
ms.assetid: 7c3f4a46-4bac-4138-ae6a-a7c7ee0d28f5
ms.openlocfilehash: 46c1ea40925a5c79180171da9a705d7e6b7c8b89
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703286"
---
# <a name="store-extensibility"></a>Rozszerzalność Store

<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Umożliwia użytkownikom promować właściwości niestandardowych, specyficzne dla aplikacji, które mogą być używane do wykonywania zapytań dla wystąpień w bazie danych trwałości. Działanie promocji właściwości powoduje, że wartości, które mają być dostępne w widoku specjalne w bazie danych. Te właściwości o podwyższonym poziomie (właściwości, które mogą być używane w kwerendach użytkownika) może być typów prostych, takich jak Int64, Guid, String i daty/godziny lub serializacji typu binary (byte[]).

<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Klasa ma <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.Promote%2A> metodę, która służy do promowania właściwość jako właściwość, które mogą być używane w zapytaniach. Poniższy przykład jest przykładem rozszerzalność magazynu end-to-end.

1. W tym przykładowym scenariuszu dokument przetwarzania aplikacji (DP) zawiera przepływy pracy, z których każdy korzysta z działań niestandardowych do przetwarzania dokumentu. Te przepływy pracy mają zestaw zmienne stanu, które muszą być widoczne dla użytkownika końcowego. Aby to osiągnąć, aplikacja DP udostępnia rozszerzenie typu <xref:System.Activities.Persistence.PersistenceParticipant>, który jest używany przez działania umożliwiają określanie wartości zmienne stanu.

    ```csharp
    class DocumentStatusExtension : PersistenceParticipant
    {
        public string DocumentId;
        public string ApprovalStatus;
        public string UserName;
        public DateTime LastUpdateTime;
    }
    ```

2. Nowe rozszerzenie jest następnie dodawana do hosta.

    ```csharp
    static Activity workflow = CreateWorkflow();
    WorkflowApplication application = new WorkflowApplication(workflow);
    DocumentStatusExtension documentStatusExtension = new DocumentStatusExtension ();
    application.Extensions.Add(documentStatusExtension);
    ```

     Aby uzyskać więcej informacji na temat dodawania niestandardowego uczestnika stanów trwałych, zobacz [uczestnicy stanów trwałych](persistence-participants.md) próbki.

3. Niestandardowe działania w aplikacji, punkt dystrybucji wypełniania różnych pól Stan w **Execute** metody.

    ```csharp
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

4. Gdy wystąpienie przepływu pracy osiąga punkt trwałości **CollectValues** metody **DocumentStatusExtension** uczestnika stanów trwałych zapisuje te właściwości do danych stanów trwałych Kolekcja.

    ```csharp
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
    > Te właściwości są przekazywane do **SqlWorkflowInstanceStore** przez platformę trwałości za pośrednictwem **SaveWorkflowCommand.InstanceData** kolekcji.

5. Aplikacja DP inicjuje Store wystąpienia przepływu pracy SQL i wywołuje **Podwyższ poziom** metodę, aby podwyższyć poziom tych danych.

    ```csharp
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

    Na podstawie tych informacji podwyższania poziomu **SqlWorkflowInstanceStore** umieszcza właściwości danych w kolumnach tabeli [InstancePromotedProperties](#InstancePromotedProperties) widoku.

6. Aby wysłać zapytanie podzbiór danych z tabeli podwyższania poziomu, aplikacji DP dodaje dostosowany widok na widok podwyższania poziomu.

    ```sql
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

## <a name="InstancePromotedProperties"></a> Widok [System.Activities.DurableInstancing.InstancePromotedProperties]

|Nazwa kolumny|Typ kolumny|Opis|
|-----------------|-----------------|-----------------|
|InstanceId|Identyfikator GUID|Wystąpienie przepływu pracy, który należy do tej promocji.|
|PromotionName|nvarchar(400)|Nazwa sam podwyższenia poziomu.|
|Wartość1, wartość2, Wartość3,..., Value32|sql_variant|Wartość o podwyższonym poziomie samej właściwości. Większość typów pierwotnych danych SQL, z wyjątkiem pliku binarnego obiekty BLOB i ponad 8000 bajtów długości ciągów mieści się w sql_variant.|
|Value35 Value33, Value34,..., Value64|Varbinary(max)|Wartość właściwości o podwyższonym poziomie, które są jawnie zadeklarowane jako varbinary(max).|
