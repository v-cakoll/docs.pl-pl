---
title: Dostęp do informacji o tożsamości wewnątrz usługi przepływu pracy
ms.date: 03/30/2017
ms.assetid: 0b832127-b35b-468e-a45f-321381170cbc
ms.openlocfilehash: 7951782946f5b8ef989598d01229dcf193d97689
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2018
ms.locfileid: "46585510"
---
# <a name="accessing-identity-information-inside-a-workflow-service"></a>Dostęp do informacji o tożsamości wewnątrz usługi przepływu pracy
Aby uzyskać dostęp do informacji o tożsamości wewnątrz usługi przepływu pracy, należy zaimplementować <xref:System.ServiceModel.Activities.IReceiveMessageCallback> interfejsu we właściwości niestandardowej wykonywania. W <xref:System.ServiceModel.Activities.IReceiveMessageCallback.OnReceiveMessage(System.ServiceModel.OperationContext,System.Activities.ExecutionProperties)> metoda dostęp można uzyskać <xref:System.ServiceModel.OperationContext.ServiceSecurityContext> uzyskiwania dostępu do tożsamości informacji. W tym temacie opisano wdrażanie tej właściwości wykonywania, a także niestandardowe działanie, które ujawni tę właściwość, aby <xref:System.ServiceModel.Activities.Receive> działania w czasie wykonywania. Niestandardowe działanie wdroży takie samo zachowanie jako <xref:System.Activities.Statements.Sequence> działań, z wyjątkiem że w przypadku <xref:System.ServiceModel.Activities.Receive> znajduje się wewnątrz niej, <xref:System.ServiceModel.Activities.IReceiveMessageCallback> zostaną wywołane i będzie można pobrać informacji o tożsamości.  
  
## <a name="implement-ireceivemessagecallback"></a>Implementowanie IReceiveMessageCallback  
  
1.  Utwórz pustą [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] rozwiązania.  
  
2.  Dodaj nową aplikację konsoli o nazwie `Service` do rozwiązania.  
  
3.  Dodaj odwołania do następujących zestawów:  
  
    1.  System.Runtime.Serialization  
  
    2.  System.ServiceModel  
  
    3.  System.ServiceModel.Activities  
  
4.  Dodaj nową klasę o nazwie `AccessIdentityCallback` i zaimplementować <xref:System.ServiceModel.Activities.IReceiveMessageCallback> jak pokazano w poniższym przykładzie.  
  
    ```csharp  
    class AccessIdentityCallback : IReceiveMessageCallback  
    {  
       public void OnReceiveMessage(System.ServiceModel.OperationContext operationContext, System.Activities.ExecutionProperties activityExecutionProperties)  
       {  
          try  
          {  
             Console.WriteLine("Received a message from a workflow with the following identity");  
             Console.WriteLine("Windows Identity Name: {0}", operationContext.ServiceSecurityContext.WindowsIdentity.Name);  
             Console.WriteLine("Windows Identity User: {0}", operationContext.ServiceSecurityContext.WindowsIdentity.User);  
             Console.WriteLine("Windows Identity IsAuthenticated: {0}", operationContext.ServiceSecurityContext.WindowsIdentity.IsAuthenticated);  
          }            
          catch (Exception ex)  
          {  
             Console.WriteLine("An exception occurred: " + ex.Message);  
          }  
        }  
    }  
    ```  
  
     Ten kod używa <xref:System.ServiceModel.OperationContext> przekazana do metody uzyskiwania dostępu do tożsamości informacji.  
  
## <a name="implement-a-native-activity-to-add-the-ireceivemessagecallback-implementation-to-the-nativeactivitycontext"></a>Implementowanie działania natywnego w celu dodania implementacji IReceiveMessageCallback do NativeActivityContext  
  
1.  Dodaj nową klasę pochodną <xref:System.Activities.NativeActivity> o nazwie `AccessIdentityScope`.  
  
2.  Dodaj zmienne lokalne, aby śledzić działania podrzędne, zmienne, bieżący indeks działania, a <xref:System.Activities.CompletionCallback> wywołania zwrotnego.  
  
    ```csharp
    public sealed class AccessIdentityScope : NativeActivity  
    {  
        Collection<Activity> children;  
        Collection<Variable> variables;  
        Variable<int> currentIndex;  
        CompletionCallback onChildComplete;  
    }  
    ```  
  
3.  Implementowanie konstruktora  
  
    ```csharp
    public AccessIdentityScope() : base()  
    {  
        this.children = new Collection<Activity>();  
        this.variables = new Collection<Variable>();  
        this.currentIndex = new Variable<int>();  
    }  
    ```  
  
4.  Implementowanie `Activities` i `Variables` właściwości.  
  
    ```csharp
    public Collection<Activity> Activities  
    {  
         get { return this.children; }  
    }  
  
    public Collection<Variable> Variables  
    {  
        get { return this.variables; }  
    }  
    ```  
  
5.  zastąpienie <xref:System.Activities.NativeActivity.CacheMetadata%2A>  
  
    ```csharp
    protected override void CacheMetadata(NativeActivityMetadata metadata)  
    {  
        //call base.CacheMetadata to add the Activities and Variables to this activity's metadata  
        base.CacheMetadata(metadata);  
        //add the private implementation variable: currentIndex   
        metadata.AddImplementationVariable(this.currentIndex);  
    }  
    ```  
  
6.  zastąpienie <xref:System.Activities.NativeActivity.Execute%2A>  
  
    ```csharp
    protected override void Execute(NativeActivityContext context)  
    {  
       // Add the IReceiveMessageCallback implementation as an Execution property   
       context.Properties.Add("AccessIdentityCallback", new AccessIdentityCallback());  
       InternalExecute(context, null);  
    }  
  
    void InternalExecute(NativeActivityContext context, ActivityInstance instance)  
    {  
       //grab the index of the current Activity  
       int currentActivityIndex = this.currentIndex.Get(context);  
       if (currentActivityIndex == Activities.Count)  
       {  
          //if the currentActivityIndex is equal to the count of MySequence's Activities  
          //MySequence is complete  
          return;  
       }  
  
       if (this.onChildComplete == null)  
       {  
          //on completion of the current child, have the runtime call back on this method  
          this.onChildComplete = new CompletionCallback(InternalExecute);  
       }  
  
       //grab the next Activity in MySequence.Activities and schedule it  
       Activity nextChild = Activities[currentActivityIndex];  
       context.ScheduleActivity(nextChild, this.onChildComplete);  
  
       //increment the currentIndex  
       this.currentIndex.Set(context, ++currentActivityIndex);  
    }  
    ```  
  
## <a name="implement-the-workflow-service"></a>Implementowanie usługi przepływu pracy  
  
1.  Otwórz istniejący `Program` klasy.  
  
2.  Definiuj stałe:  
  
    ```csharp
    class Program  
    {  
       const string addr = "http://localhost:8080/Service";  
       static XName contract = XName.Get("IService", "http://tempuri.org");  
    }  
    ```  
  
3.  Dodaj metodę statyczną o nazwie `GetWorkflowService` tworząca usługi przepływu pracy.  
  
    ```csharp
    static Activity GetServiceWorkflow()  
    {  
       Variable<string> echoString = new Variable<string>();  
  
       // Create the Receive activity  
       Receive echoRequest = new Receive  
       {  
          CanCreateInstance = true,  
          ServiceContractName = contract,  
          OperationName = "Echo",  
          Content = new ReceiveParametersContent()  
          {  
             Parameters = { { "echoString", new OutArgument<string>(echoString) } }  
          }  
       };  
  
       return new AccessIdentityScope  
       {  
          Variables = { echoString },  
          Activities =  
          {  
             echoRequest,  
             new WriteLine { Text = new InArgument<string>( (e) => "Received: " + echoString.Get(e) ) },  
             new SendReply  
             {  
                Request = echoRequest,  
                Content = new SendParametersContent()  
                {  
                   Parameters = { { "result", new InArgument<string>(echoString) } }   
                }  
             }  
          }  
       };  
     }  
    ```  
  
4.  W istniejącym `Main` metody hosta usługi przepływu pracy.  
  
    ```csharp
    static void Main(string[] args)  
    {  
       string addr = "http://localhost:8080/Service";  
  
       using (WorkflowServiceHost host = new WorkflowServiceHost(GetServiceWorkflow()))  
       {  
          WSHttpBinding binding = new WSHttpBinding(SecurityMode.Message);  
          host.AddServiceEndpoint(contract, binding, addr);  
  
          host.Open();  
          Console.WriteLine("Service waiting at: " + addr);  
          Console.WriteLine("Press [ENTER] to exit");  
          Console.ReadLine();  
          host.Close();  
       }  
    }  
    ```  
  
## <a name="implement-a-workflow-client"></a>Implementacja klienta przepływu pracy  
  
1.  Utwórz nowy projekt aplikacji konsoli o nazwie `Client`.  
  
2.  Dodaj odwołania do następujących zestawów:  
  
    1.  System.Activities  
  
    2.  System.ServiceModel  
  
    3.  System.ServiceModel.Activities  
  
3.  Otwórz wygenerowany plik Program.cs i Dodaj statyczną metodę o nazwie `GetClientWorkflow` Tworzenie przepływu pracy klienta.  
  
    ```csharp
    static Activity GetClientWorkflow()  
    {  
       Variable<string> echoString = new Variable<string>();  
  
       Endpoint clientEndpoint = new Endpoint  
       {  
          Binding = new WSHttpBinding(SecurityMode.Message),  
          AddressUri = new Uri("http://localhost:8080/Service")  
       };  
  
       Send echoRequest = new Send  
       {  
          Endpoint = clientEndpoint,  
          ServiceContractName = XName.Get("IService", "http://tempuri.org"),  
          OperationName = "Echo",  
          Content = new SendParametersContent()  
          {  
             Parameters = { { "echoString", new InArgument<string>("Hello, World") } }
          }  
       };  
  
       return new Sequence  
       {  
          Variables = { echoString },  
          Activities =  
          {
             new CorrelationScope  
             {  
                Body = new Sequence  
                {  
                   Activities =
                   {  
                      echoRequest,  
                      new ReceiveReply  
                      {  
                         Request = echoRequest,  
                         Content = new ReceiveParametersContent  
                         {  
                            Parameters = { { "result", new OutArgument<string>(echoString) } }  
                         }  
                      }  
                   }  
                }  
             },
             new WriteLine { Text = new InArgument<string>( (e) => "Received Text: " + echoString.Get(e) ) },
             }  
          };  
       }  
    }  
    ```  
  
4.  Dodaj następujący kod hostingu, aby `Main()` metody.  
  
    ```csharp
    static void Main(string[] args)  
    {  
       Activity workflow = GetClientWorkflow();  
       WorkflowInvoker.Invoke(workflow);  
       WorkflowInvoker.Invoke(workflow);  
       Console.WriteLine("Press [ENTER] to exit");  
       Console.ReadLine();  
    }  
    ```  
  
## <a name="example"></a>Przykład
 Oto Pełna lista źródła kod używany w tym temacie.  
  
```csharp
// AccessIdentityCallback.cs  
//----------------------------------------------------------------  
// Copyright (c) Microsoft Corporation.  All rights reserved.  
//----------------------------------------------------------------  
  
using System;  
using System.ServiceModel;  
using System.ServiceModel.Activities;  
  
namespace Microsoft.Samples.AccessingOperationContext.Service  
{  
    class AccessIdentityCallback : IReceiveMessageCallback  
    {  
        public const string HeaderName = "InstanceIdHeader";  
        public const string HeaderNS = "http://Microsoft.Samples.AccessingOperationContext";  
  
        public void OnReceiveMessage(System.ServiceModel.OperationContext operationContext, System.Activities.ExecutionProperties activityExecutionProperties)  
        {  
            try  
            {  
                // Guid instanceId = operationContext.IncomingMessageHeaders.GetHeader<Guid>(HeaderName, HeaderNS);  
                Console.WriteLine("Received a message from a workflow with the following identity" ); // with instanceId = {0}", instanceId);  
                Console.WriteLine("Windows Identity Name: {0}", operationContext.ServiceSecurityContext.WindowsIdentity.Name);  
                Console.WriteLine("Windows Identity User: {0}", operationContext.ServiceSecurityContext.WindowsIdentity.User);  
                Console.WriteLine("Windows Identity IsAuthenticated: {0}", operationContext.ServiceSecurityContext.WindowsIdentity.IsAuthenticated);  
            }  
            catch (MessageHeaderException)  
            {  
                Console.WriteLine("This message must not be from a workflow.");  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine("An exception occurred: " + ex.Message);  
            }  
        }  
    }  
}  
```
  
```csharp
// AccessIdentityScope.cs  
//----------------------------------------------------------------  
// Copyright (c) Microsoft Corporation.  All rights reserved.  
//----------------------------------------------------------------  
  
using System.Activities;  
using System.Collections.ObjectModel;  
  
namespace Microsoft.Samples.AccessingOperationContext.Service  
{  
    public sealed class AccessIdentityScope : NativeActivity  
    {  
        Collection<Activity> children;  
        Collection<Variable> variables;  
        Variable<int> currentIndex;  
        CompletionCallback onChildComplete;  
  
        public AccessIdentityScope()  
            : base()  
        {  
            this.children = new Collection<Activity>();  
            this.variables = new Collection<Variable>();  
            this.currentIndex = new Variable<int>();  
        }  
  
        public Collection<Activity> Activities  
        {  
            get  
            {  
                return this.children;  
            }  
        }  
  
        public Collection<Variable> Variables  
        {  
            get  
            {  
                return this.variables;  
            }  
        }  
  
        protected override void CacheMetadata(NativeActivityMetadata metadata)  
        {  
            //call base.CacheMetadata to add the Activities and Variables to this activity's metadata  
            base.CacheMetadata(metadata);  
            //add the private implementation variable: currentIndex
            metadata.AddImplementationVariable(this.currentIndex);  
        }
  
        protected override void Execute(  
            NativeActivityContext context)  
        {  
            context.Properties.Add("AccessIdentityCallback", new AccessIdentityCallback());  
            InternalExecute(context, null);  
        }  
  
        void InternalExecute(NativeActivityContext context, ActivityInstance instance)  
        {  
            //grab the index of the current Activity  
            int currentActivityIndex = this.currentIndex.Get(context);  
            if (currentActivityIndex == Activities.Count)  
            {  
                //if the currentActivityIndex is equal to the count of MySequence's Activities  
                //MySequence is complete  
                return;  
            }  
  
            if (this.onChildComplete == null)  
            {  
                //on completion of the current child, have the runtime call back on this method  
                this.onChildComplete = new CompletionCallback(InternalExecute);  
            }  
  
            //grab the next Activity in MySequence.Activities and schedule it  
            Activity nextChild = Activities[currentActivityIndex];  
            context.ScheduleActivity(nextChild, this.onChildComplete);  
  
            //increment the currentIndex  
            this.currentIndex.Set(context, ++currentActivityIndex);  
        }  
    }  
}  
```
  
```csharp
// Service.cs  
//----------------------------------------------------------------  
// Copyright (c) Microsoft Corporation.  All rights reserved.  
//----------------------------------------------------------------  
  
using System;  
using System.Activities;  
using System.Activities.Statements;  
using System.ServiceModel;  
using System.ServiceModel.Activities;  
using System.Xml.Linq;  
  
namespace Microsoft.Samples.AccessingOperationContext.Service  
{      
    class Program  
    {  
        const string addr = "http://localhost:8080/Service";  
        static XName contract = XName.Get("IService", "http://tempuri.org");  
  
        static void Main(string[] args)  
        {  
            string addr = "http://localhost:8080/Service";  
  
            using (WorkflowServiceHost host = new WorkflowServiceHost(GetServiceWorkflow()))  
            {  
                WSHttpBinding binding = new WSHttpBinding(SecurityMode.Message);  
                host.AddServiceEndpoint(contract, binding, addr);  
  
                host.Open();  
                Console.WriteLine("Service waiting at: " + addr);  
                Console.WriteLine("Press [ENTER] to exit");  
                Console.ReadLine();  
                host.Close();  
            }  
  
        }  
  
        static Activity GetServiceWorkflow()  
        {  
            Variable<string> echoString = new Variable<string>();  
  
            Receive echoRequest = new Receive  
            {  
                CanCreateInstance = true,  
                ServiceContractName = contract,  
                OperationName = "Echo",  
                Content = new ReceiveParametersContent()  
                {  
                    Parameters = { { "echoString", new OutArgument<string>(echoString) } }  
                }  
            };  
  
            return new AccessIdentityScope  
            {  
                Variables = { echoString },  
                Activities =  
                {  
                    echoRequest,  
                    new WriteLine { Text = new InArgument<string>( (e) => "Received: " + echoString.Get(e) ) },  
                    new SendReply  
                    {  
                        Request = echoRequest,  
                        Content = new SendParametersContent()  
                        {  
                            Parameters = { { "result", new InArgument<string>(echoString) } }   
                        }  
                    }  
                }  
            };  
        }  
    }  
}  
```
  
```csharp
// client.cs
//----------------------------------------------------------------  
// Copyright (c) Microsoft Corporation.  All rights reserved.  
//----------------------------------------------------------------  
  
using System;  
using System.Activities;  
using System.Activities.Statements;  
using System.ServiceModel;  
using System.ServiceModel.Activities;  
using System.Xml.Linq;  
  
namespace Microsoft.Samples.AccessingOperationContext.Client  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            Activity workflow = GetClientWorkflow();  
            WorkflowInvoker.Invoke(workflow);  
            WorkflowInvoker.Invoke(workflow);  
            Console.WriteLine("Press [ENTER] to exit");  
            Console.ReadLine();  
        }  
  
        static Activity GetClientWorkflow()  
        {  
            Variable<string> echoString = new Variable<string>();  
  
            Endpoint clientEndpoint = new Endpoint  
            {  
                Binding = new WSHttpBinding(SecurityMode.Message),  
                AddressUri = new Uri("http://localhost:8080/Service")  
            };  
  
            Send echoRequest = new Send  
            {  
                Endpoint = clientEndpoint,  
                ServiceContractName = XName.Get("IService", "http://tempuri.org"),  
                OperationName = "Echo",  
                Content = new SendParametersContent()  
                {  
                    Parameters = { { "echoString", new InArgument<string>("Hello, World") } }   
                }  
            };  
  
            return new Sequence  
            {  
                Variables = { echoString },  
                Activities =  
                {
                    new CorrelationScope  
                    {  
                        Body = new Sequence  
                        {  
                            Activities =
                            {  
                                echoRequest,  
                                new ReceiveReply  
                                {  
                                    Request = echoRequest,  
                                    Content = new ReceiveParametersContent  
                                    {  
                                        Parameters = { { "result", new OutArgument<string>(echoString) } }  
                                    }  
                                }  
                            }  
                        }  
                    },
                    new WriteLine { Text = new InArgument<string>( (e) => "Received Text: " + echoString.Get(e) ) },
                }  
            };  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Uzyskiwanie dostępu do elementu OperationContext](../../../../docs/framework/windows-workflow-foundation/samples/accessing-operationcontext.md)  
 [Tworzenie przepływów pracy, działań i wyrażeń przy użyciu kodu imperatywnego](../../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md)
