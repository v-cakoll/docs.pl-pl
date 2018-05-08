---
title: 'Porady: Tworzenie magazynu wystąpienia niestandardowego'
ms.date: 03/30/2017
ms.assetid: 593c4e9d-8a49-4e12-8257-cee5e6b4c075
ms.openlocfilehash: 96f713765178011b9122afcb31e4721e9184d1d3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-custom-instance-store"></a>Porady: Tworzenie magazynu wystąpienia niestandardowego
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] zawiera <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, magazynie wystąpień, który używa programu SQL Server do utrwalenia danych przepływu pracy. Jeśli aplikacja jest wymagany do utrwalenia danych przepływu pracy na inny nośnik, na przykład innej bazy danych lub systemu plików, można zaimplementować magazynu niestandardowego wystąpienia. Magazynu niestandardowego wystąpienia jest tworzony przez rozszerzenie klasy abstrakcyjnej <xref:System.Runtime.DurableInstancing.InstanceStore> klasy i implementacja metody, które są wymagane do wykonania. Do zakończenia wdrożenia magazynu niestandardowego wystąpienia, zobacz [firmowej procesu zakupu](../../../docs/framework/windows-workflow-foundation/samples/corporate-purchase-process.md) próbki.  
  
## <a name="implementing-the-begintrycommand-method"></a>Implementacja metody BeginTryCommand  
 <xref:System.Runtime.DurableInstancing.InstanceStore.BeginTryCommand%2A> Wysyłany przez aparat trwałości w magazynie wystąpień. Typ `command` parametr wskazuje, które polecenie jest wykonywane; ten parametr może być następujących typów:  
  
-   <xref:System.Activities.DurableInstancing.SaveWorkflowCommand>: Aparat trwałości wysyła tego polecenia w magazynie wystąpień, gdy przepływ pracy ma zostać utrwalony na nośniku. Dane trwałości przepływu pracy jest przekazane do metody w <xref:System.Activities.DurableInstancing.SaveWorkflowCommand.InstanceData%2A> członkiem `command` parametru.  
  
-   <xref:System.Activities.DurableInstancing.LoadWorkflowCommand>: Aparat trwałości wysyła tego polecenia w magazynie wystąpień, gdy przepływ pracy ma być załadowany z nośnika magazynowania. Identyfikator wystąpienia przepływu pracy do załadowania jest przekazane do metody w `instanceId` parametr <xref:System.Runtime.DurableInstancing.InstancePersistenceContext.InstanceView%2A> właściwość `context` parametru.  
  
-   <xref:System.Activities.DurableInstancing.CreateWorkflowOwnerCommand>Wysyła aparat trwałości to polecenie, aby wystąpienie magazynu podczas obliczania <xref:System.ServiceModel.Activities.WorkflowServiceHost> musi być zarejestrowana jako właściciela blokady. Należy podać identyfikator wystąpienia przepływu pracy, bieżący przy użyciu magazynu wystąpienia <xref:System.Runtime.DurableInstancing.InstancePersistenceContext.BindInstanceOwner%2A> metody `context` parametru.  
  
     Poniższy fragment kodu przedstawia sposób wykonania polecenia CreateWorkflowOwner można przypisać właściciela blokady jawne.  
  
    ```  
    XName WFInstanceScopeName = XName.Get(scopeName, "<namespace>");  
    ...  
    CreateWorkflowOwnerCommand createCommand = new CreateWorkflowOwnerCommand()  
    {  
        InstanceOwnerMetadata =  
        {  
            { WorkflowHostTypeName, new InstanceValue(WFInstanceScopeName) },  
        }  
    };  
    InstanceHandle ownerHandle = store.CreateInstanceHandle();  
    store.DefaultInstanceOwner = store.Execute(  
                                   ownerHandle,  
                                   createCommand,  
                                   TimeSpan.FromSeconds(30)).InstanceOwner;  
    childInstance.AddInitialInstanceValues(new Dictionary<XName, object>() { { WorkflowHostTypeName, WFInstanceScopeName } });  
    ```  
  
-   <xref:System.Activities.DurableInstancing.DeleteWorkflowOwnerCommand>: Aparat trwałości wysyła tego polecenia w magazynie wystąpień, gdy właściciel blokady Identyfikatora wystąpienia może być usunięty z magazynu wystąpień. Jak <xref:System.Activities.DurableInstancing.CreateWorkflowOwnerCommand>, identyfikator właściciela blokady powinny być dostarczone przez aplikację.  
  
     Poniższy fragment kodu pokazano, jak zwolnić blokady przy użyciu <xref:System.Activities.DurableInstancing.DeleteWorkflowOwnerCommand>.  
  
    ```  
    static void FreeHandleAndDeleteOwner(InstanceStore store, InstanceHandle handle)  
    {  
        handle.Free();  
        handle = store.CreateInstanceHandle(store.DefaultInstanceOwner);  
        try  
        {  
            // We need this sleep so that we dont prematurely delete the owner, we need time to update the database.  
            Thread.Sleep(10000);  
            store.Execute(handle, new DeleteWorkflowOwnerCommand(), TimeSpan.FromSeconds(10));  
        }  
        catch (InstancePersistenceCommandException ex) { Log.Inform(ex.Message); }  
        catch (InstanceOwnerException ex) { Log.Inform(ex.Message); }  
        catch (OperationCanceledException ex) { Log.Inform(ex.Message); }  
        catch (Exception ex) { Log.Inform(ex.Message); }  
        finally  
        {  
            handle.Free();  
            store.DefaultInstanceOwner = null;  
        }  
    }  
    ```  
  
     Powyższej metody powinna być wywoływana w bloku Try/Catch, po uruchomieniu wystąpienia podrzędnych.  
  
    ```  
    try  
    {  
        childInstance.Run();  
    }  
    catch (Exception)  
    {  
        throw ;  
    }  
    finally  
    {  
        FreeHandleAndDeleteOwner(store, ownerHandle);  
    }  
    ```  
  
-   <xref:System.Activities.DurableInstancing.LoadWorkflowByInstanceKeyCommand>: Gdy wystąpienia przepływu pracy ma być ładowane przy użyciu klucza wystąpienia przepływu pracy aparat trwałości wysyła do tego polecenia w magazynie wystąpień. Identyfikator klucza wystąpienia można ustalić przy użyciu <xref:System.Activities.DurableInstancing.LoadWorkflowByInstanceKeyCommand.LookupInstanceKey%2A> parametru polecenia.  
  
-   <xref:System.Activities.DurableInstancing.QueryActivatableWorkflowsCommand>: Aparat trwałości wysyła tego polecenia w magazynie wystąpień, pobrać parametrów aktywacji utrwalonych przepływów pracy, aby można było utworzyć hosta przepływu pracy, który można następnie załadować przepływów pracy. To polecenie jest wysyłane przez aparat w odpowiedzi na wystąpienia wywoływanie magazynu <xref:System.Activities.DurableInstancing.HasActivatableWorkflowEvent> do hosta, gdy klient zlokalizuje wystąpienie, które może zostać uaktywniony. W magazynie wystąpień powinien sondowania w celu ustalenia, czy są przepływy pracy, które można aktywować.  
  
-   <xref:System.Activities.DurableInstancing.TryLoadRunnableWorkflowCommand>: Aparat trwałości wysyła tego polecenia w magazynie wystąpień, aby załadować wystąpienia przepływu pracy do uruchomienia. To polecenie jest wysyłane przez aparat w odpowiedzi na wystąpienia wywoływanie magazynu <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> do hosta, gdy klient zlokalizuje wystąpienie, które mogą być uruchamiane. W magazynie wystąpień powinien sondować przepływy pracy, które mogą być uruchamiane. Poniższy fragment kodu przedstawia sondowanie w magazynie wystąpień przepływów pracy, które można uruchomić lub aktywowane.  
  
    ```  
    public void PollForEvents()  
    {  
        InstanceOwner[] storeOwners = this.GetInstanceOwners();  
  
        foreach (InstanceOwner owner in storeOwners)  
        {  
            foreach (InstancePersistenceEvent ppEvent in this.GetEvents(owner))  
            {  
                if (ppEvent.Equals(HasRunnableWorkflowEvent.Value))  
                {  
                    bool hasRunnable = GetRunnableEvents(this.StoreId, owner.InstanceOwnerId, isActivable);  
                    if (hasRunnable)  
                    {  
                        this.SignalEvent(ppEvent, owner);  
                    }  
                    else  
                    {  
                        this.ResetEvent(ppEvent, owner);  
                    }  
                }  
                else if(ppEvent.Equals(HasActivatableWorkflowEvent.Value))  
                {  
                   bool hasActivable = GetActivableEvents(this.StoreId, owner.InstanceOwnerId);  
                   if (hasActivable)  
                    {  
                        this.SignalEvent(ppEvent, owner);  
                    }  
                    else  
                    {  
                        this.ResetEvent(ppEvent, owner);  
                    }  
                }  
            }  
        }  
    }  
    ```  
  
     W powyższym fragment kodu, w magazynie wystąpień kwerendy dostępnych zdarzeń i sprawdza, czy każdy z nich do określenia, czy jest <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> zdarzeń. Jeśli został znaleziony, <xref:System.Runtime.DurableInstancing.InstanceStore.SignalEvent%2A> jest wywoływana w celu wysłania polecenia w magazynie wystąpień hosta.  Poniższy fragment kodu przedstawia implementację programu obsługi dla tego polecenia.  
  
    ```  
    If (command is TryLoadRunnableWorkflowCommand)  
    {  
        Owner owner;  
        CheckOwner(context, command.Name, out owner);                          
        // Checking instance.Owner is like an InstanceLockQueryResult.  
        context.QueriedInstanceStore(new InstanceLockQueryResult(context.InstanceView.InstanceId, context.InstanceView.InstanceOwner.InstanceOwnerId));  
  
        XName ownerService = null;  
        InstanceValue value;  
        Instance runnableInstance = default(Instance);  
        bool foundRunnableInstance = false;  
  
        value = QueryPropertyBag(WorkflowNamespace.WorkflowHostType, owner.Data);  
        if (value != null && value.Value is XName)  
        {  
            ownerService = (XName)value.Value;  
        }  
  
        foreach (KeyValuePair<Guid, Instance> instance in MemoryStore.instances)  
        {  
            if (instance.Value.Owner != Guid.Empty || instance.Value.Completed)  
            {  
                continue;  
            }  
  
            if (ownerService != null)  
            {  
                value = QueryPropertyBag(WorkflowNamespace.WorkflowHostType, instance.Value.Metadata);  
                if (value == null || ((XName)value.Value) != ownerService)  
                {  
                    continue;  
                }  
            }  
  
            value = QueryPropertyBag(WorkflowServiceNamespace.SuspendReason, instance.Value.Metadata);  
            if (value != null && value.Value != null && value.Value is string)  
            {  
                continue;  
            }  
  
            value = QueryPropertyBag(WorkflowNamespace.Status, instance.Value.Data);  
            if (value != null && value.Value is string && ((string)value.Value) == "Executing")  
            {  
                runnableInstance = instance.Value;  
                foundRunnableInstance = true;  
            }  
  
            if (!foundRunnableInstance)  
            {  
                value = QueryPropertyBag(XNamespace.Get("urn:schemas-microsoft-com:System.Activities/4.0/properties").GetName("TimerExpirationTime"), instance.Value.Data);  
                if (value != null && value.Value is DateTime && ((DateTime)value.Value) <= DateTime.UtcNow)  
                {                          
                    runnableInstance = instance.Value;  
                    foundRunnableInstance = true;  
                }  
            }  
  
            if (foundRunnableInstance)  
            {  
                runnableInstance.LockVersion++;  
                runnableInstance.Owner = context.InstanceView.InstanceOwner.InstanceOwnerId;  
                MemoryStore.instances[instance.Key] = runnableInstance;  
                context.BindInstance(instance.Key);  
                context.BindAcquiredLock(runnableInstance.LockVersion);  
  
                Dictionary<Guid, IDictionary<XName, InstanceValue>> associatedKeys = new Dictionary<Guid, IDictionary<XName, InstanceValue>>();  
                Dictionary<Guid, IDictionary<XName, InstanceValue>> completedKeys = new Dictionary<Guid, IDictionary<XName, InstanceValue>>();  
                foreach (KeyValuePair<Guid, Key> keyEntry in MemoryStore.keys)  
                {  
                if (keyEntry.Value.Instance == context.InstanceView.InstanceId)  
                {  
                    if (keyEntry.Value.Completed)  
                    {  
                        completedKeys.Add(keyEntry.Key, DeserializePropertyBag(keyEntry.Value.Metadata));  
                    }  
                    else  
                    {  
                        associatedKeys.Add(keyEntry.Key, DeserializePropertyBag(keyEntry.Value.Metadata));  
                    }  
                }  
            }  
  
            context.LoadedInstance(InstanceState.Initialized, DeserializePropertyBag(runnableInstance.Data), DeserializePropertyBag(runnableInstance.Metadata), associatedKeys, completedKeys);  
            break;  
        }  
    }  
    ```  
  
     W powyższym fragment kodu do uruchomienia wystąpień wyszukuje w magazynie wystąpień. Jeśli wystąpienie zostanie wykryte, jest on powiązany z kontekstu wykonywania i załadowane.  
  
## <a name="using-a-custom-instance-store"></a>Za pomocą magazynu niestandardowego wystąpienia  
 Aby zaimplementować magazynu niestandardowego wystąpienia, przypisz wystąpienie w magazynie wystąpień, aby <xref:System.Activities.WorkflowApplication.InstanceStore%2A>i wdrożenie <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> metody.  Zobacz [porady: tworzenie i uruchamianie długiego przepływu pracy z](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md) samouczka, aby uzyskać szczegóły.  
  
## <a name="a-sample-instance-store"></a>Magazyn wystąpienia próbki  
 Poniższy przykładowy kod jest pełne wystąpienie Implementacja magazynu, z [firmowej procesu zakupu](../../../docs/framework/windows-workflow-foundation/samples/corporate-purchase-process.md) próbki. Ten magazyn wystąpienia utrzymuje dane przepływu pracy w pliku za pomocą XML.  
  
```  
using System;  
using System.Activities.DurableInstancing;  
using System.Collections.Generic;  
using System.IO;  
using System.Runtime.DurableInstancing;  
using System.Runtime.Serialization;  
using System.ServiceModel.Persistence;  
using System.Xml;  
using System.Xml.Linq;  
  
namespace Microsoft.Samples.WF.PurchaseProcess  
{  
  
    public class XmlWorkflowInstanceStore : InstanceStore  
    {  
        Guid ownerInstanceID;  
  
        public XmlWorkflowInstanceStore() : this(Guid.NewGuid())  
        {  
  
        }  
  
        public XmlWorkflowInstanceStore(Guid id)  
        {  
            ownerInstanceID = id;  
        }  
  
        //Synchronous version of the Begin/EndTryCommand functions  
        protected override bool TryCommand(InstancePersistenceContext context, InstancePersistenceCommand command, TimeSpan timeout)  
        {  
            return EndTryCommand(BeginTryCommand(context, command, timeout, null, null));  
        }  
  
        //The persistence engine will send a variety of commands to the configured InstanceStore,  
        //such as CreateWorkflowOwnerCommand, SaveWorkflowCommand, and LoadWorkflowCommand.  
        //This method is where we will handle those commands  
        protected override IAsyncResult BeginTryCommand(InstancePersistenceContext context, InstancePersistenceCommand command, TimeSpan timeout, AsyncCallback callback, object state)  
        {  
            IDictionary<XName, InstanceValue> data = null;  
  
            //The CreateWorkflowOwner command instructs the instance store to create a new instance owner bound to the instanace handle  
            if (command is CreateWorkflowOwnerCommand)  
            {  
                context.BindInstanceOwner(ownerInstanceID, Guid.NewGuid());  
            }  
            //The SaveWorkflow command instructs the instance store to modify the instance bound to the instance handle or an instance key  
            else if (command is SaveWorkflowCommand)  
            {  
                SaveWorkflowCommand saveCommand = (SaveWorkflowCommand)command;  
                data = saveCommand.InstanceData;  
  
                Save(data);  
            }  
            //The LoadWorkflow command instructs the instance store to lock and load the instance bound to the identifier in the instance handle  
            else if (command is LoadWorkflowCommand)  
            {  
                string fileName = IOHelper.GetFileName(this.ownerInstanceID);  
  
                try  
                {  
                    using (FileStream inputStream = new FileStream(fileName, FileMode.Open))  
                    {  
                        data = LoadInstanceDataFromFile(inputStream);  
                        //load the data into the persistence Context  
                        context.LoadedInstance(InstanceState.Initialized, data, null, null, null);  
                    }  
                }  
                catch (Exception exception)  
                {  
                    throw new PersistenceException(exception.Message);  
                }  
            }  
  
            return new CompletedAsyncResult<bool>(true, callback, state);  
        }  
  
        protected override bool EndTryCommand(IAsyncResult result)  
        {  
            return CompletedAsyncResult<bool>.End(result);  
        }  
  
        //Reads data from xml file and creates a dictionary based off of that.  
        IDictionary<XName, InstanceValue> LoadInstanceDataFromFile(Stream inputStream)  
        {  
            IDictionary<XName, InstanceValue> data = new Dictionary<XName, InstanceValue>();  
  
            NetDataContractSerializer s = new NetDataContractSerializer();  
  
            XmlReader rdr = XmlReader.Create(inputStream);  
            XmlDocument doc = new XmlDocument();  
            doc.Load(rdr);  
  
            XmlNodeList instances = doc.GetElementsByTagName("InstanceValue");  
            foreach (XmlElement instanceElement in instances)  
            {  
                XmlElement keyElement = (XmlElement)instanceElement.SelectSingleNode("descendant::key");  
                XName key = (XName)DeserializeObject(s, keyElement);  
  
                XmlElement valueElement = (XmlElement)instanceElement.SelectSingleNode("descendant::value");  
                object value = DeserializeObject(s, valueElement);  
                InstanceValue instVal = new InstanceValue(value);  
  
                data.Add(key, instVal);  
            }  
  
            return data;  
        }  
  
        object DeserializeObject(NetDataContractSerializer serializer, XmlElement element)  
        {  
            object deserializedObject = null;  
  
            MemoryStream stm = new MemoryStream();  
            XmlDictionaryWriter wtr = XmlDictionaryWriter.CreateTextWriter(stm);  
            element.WriteContentTo(wtr);  
            wtr.Flush();  
            stm.Position = 0;  
  
            deserializedObject = serializer.Deserialize(stm);  
  
            return deserializedObject;  
        }  
  
        //Saves the persistence data to an xml file.  
        void Save(IDictionary<XName, InstanceValue> instanceData)  
        {  
            string fileName = IOHelper.GetFileName(this.ownerInstanceID);  
            XmlDocument doc = new XmlDocument();  
            doc.LoadXml("<InstanceValues/>");  
  
            foreach (KeyValuePair<XName,InstanceValue> valPair in instanceData)  
            {  
                XmlElement newInstance = doc.CreateElement("InstanceValue");  
  
                XmlElement newKey = SerializeObject("key", valPair.Key, doc);  
                newInstance.AppendChild(newKey);  
  
                XmlElement newValue = SerializeObject("value", valPair.Value.Value, doc);  
                newInstance.AppendChild(newValue);  
  
                doc.DocumentElement.AppendChild(newInstance);  
            }  
            doc.Save(fileName);  
       }  
  
        XmlElement SerializeObject(string elementName, object o, XmlDocument doc)  
        {  
            NetDataContractSerializer s = new NetDataContractSerializer();  
            XmlElement newElement = doc.CreateElement(elementName);  
            MemoryStream stm = new MemoryStream();  
  
            s.Serialize(stm, o);  
            stm.Position = 0;  
            StreamReader rdr = new StreamReader(stm);  
            newElement.InnerXml = rdr.ReadToEnd();  
  
            return newElement;  
        }  
    }  
}  
```
