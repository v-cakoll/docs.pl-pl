---
title: "Dostęp do informacji o tożsamości wewnątrz usługi przepływu pracy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b832127-b35b-468e-a45f-321381170cbc
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d8e0ce4a171e9bc57ef28aef1fe2761907acc73c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="accessing-identity-information-inside-a-workflow-service"></a><span data-ttu-id="f776a-102">Dostęp do informacji o tożsamości wewnątrz usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="f776a-102">Accessing Identity Information inside a Workflow Service</span></span>
<span data-ttu-id="f776a-103">Aby uzyskać dostęp do informacji o tożsamości wewnątrz usługi przepływu pracy, musisz zaimplementować <xref:System.ServiceModel.Activities.IReceiveMessageCallback> interfejsu we właściwości niestandardowej wykonywania.</span><span class="sxs-lookup"><span data-stu-id="f776a-103">To access identity information inside a workflow service, you must implement the <xref:System.ServiceModel.Activities.IReceiveMessageCallback> interface in a custom execution property.</span></span> <span data-ttu-id="f776a-104">W <xref:System.ServiceModel.Activities.IReceiveMessageCallback.OnReceiveMessage(System.ServiceModel.OperationContext,System.Activities.ExecutionProperties)> można uzyskać dostępu do metody <xref:System.ServiceModel.OperationContext.ServiceSecurityContext> do dostępu do informacji o tożsamości.</span><span class="sxs-lookup"><span data-stu-id="f776a-104">In the <xref:System.ServiceModel.Activities.IReceiveMessageCallback.OnReceiveMessage(System.ServiceModel.OperationContext,System.Activities.ExecutionProperties)> method you can access the <xref:System.ServiceModel.OperationContext.ServiceSecurityContext> to access identity information.</span></span> <span data-ttu-id="f776a-105">Ten temat przeprowadzi Cię przez wdrożenie tej właściwości wykonywania, a także działania niestandardowego, który będzie powierzchni tę właściwość, aby <xref:System.ServiceModel.Activities.Receive> działania w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="f776a-105">This topic will walk you through implementing this execution property, as well as a custom activity that will surface this property to the <xref:System.ServiceModel.Activities.Receive> activity at runtime.</span></span>  <span data-ttu-id="f776a-106">Działania niestandardowego zostaną zaimplementowane zachowania <!--zz <xref:System.ServiceModel.Activities.Sequence>--> `System.ServiceModel.Activities.Sequence` działania, z wyjątkiem że w przypadku <xref:System.ServiceModel.Activities.Receive> znajduje się wewnątrz niej, <xref:System.ServiceModel.Activities.IReceiveMessageCallback> będą wywoływane i będzie można pobrać informacji o tożsamości.</span><span class="sxs-lookup"><span data-stu-id="f776a-106">The custom activity will implement the same behavior as a <!--zz <xref:System.ServiceModel.Activities.Sequence>--> `System.ServiceModel.Activities.Sequence` activity, except that when a <xref:System.ServiceModel.Activities.Receive> is placed inside of it, the <xref:System.ServiceModel.Activities.IReceiveMessageCallback> will be called and the identity information will be retrieved.</span></span>  
  
### <a name="implement-ireceivemessagecallback"></a><span data-ttu-id="f776a-107">Implementowanie IReceiveMessageCallback</span><span class="sxs-lookup"><span data-stu-id="f776a-107">Implement IReceiveMessageCallback</span></span>  
  
1.  <span data-ttu-id="f776a-108">Utwórz pustą [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="f776a-108">Create an empty [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] solution.</span></span>  
  
2.  <span data-ttu-id="f776a-109">Dodaj nową aplikację konsoli o nazwie `Service` do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="f776a-109">Add a new console application called `Service` to the solution.</span></span>  
  
3.  <span data-ttu-id="f776a-110">Dodaj odwołania do następujących zestawów:</span><span class="sxs-lookup"><span data-stu-id="f776a-110">Add references to the following assemblies:</span></span>  
  
    1.  <span data-ttu-id="f776a-111">System.Runtime.Serialization</span><span class="sxs-lookup"><span data-stu-id="f776a-111">System.Runtime.Serialization</span></span>  
  
    2.  <span data-ttu-id="f776a-112">System.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f776a-112">System.ServiceModel</span></span>  
  
    3.  <span data-ttu-id="f776a-113">System.ServiceModel.Activities</span><span class="sxs-lookup"><span data-stu-id="f776a-113">System.ServiceModel.Activities</span></span>  
  
4.  <span data-ttu-id="f776a-114">Dodaj nową klasę o nazwie `AccessIdentityCallback` i wdrożenie <xref:System.ServiceModel.Activities.IReceiveMessageCallback> jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f776a-114">Add a new class called `AccessIdentityCallback` and implement <xref:System.ServiceModel.Activities.IReceiveMessageCallback> as shown in the following example.</span></span>  
  
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
  
     <span data-ttu-id="f776a-115">Ten kod zawiera <xref:System.ServiceModel.OperationContext> przekazany do metody do dostępu do informacji o tożsamości.</span><span class="sxs-lookup"><span data-stu-id="f776a-115">This code uses the <xref:System.ServiceModel.OperationContext> passed into the method to access identity information.</span></span>  
  
### <a name="implement-a-native-activity-to-add-the-ireceivemessagecallback-implementation-to-the-nativeactivitycontext"></a><span data-ttu-id="f776a-116">Implementowanie działania natywnego, aby dodać implementację IReceiveMessageCallback NativeActivityContext</span><span class="sxs-lookup"><span data-stu-id="f776a-116">Implement a Native activity to add the IReceiveMessageCallback implementation to the NativeActivityContext</span></span>  
  
1.  <span data-ttu-id="f776a-117">Dodaj nową klasę pochodną <xref:System.Activities.NativeActivity> o nazwie `AccessIdentityScope`.</span><span class="sxs-lookup"><span data-stu-id="f776a-117">Add a new class derived from <xref:System.Activities.NativeActivity> called `AccessIdentityScope`.</span></span>  
  
2.  <span data-ttu-id="f776a-118">Dodaj zmiennych lokalnych do śledzenia działań podrzędnych, zmienne, bieżącego indeksu działania, a <xref:System.Activities.CompletionCallback> wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="f776a-118">Add local variables to keep track of child activities, variables, current activity index, and a <xref:System.Activities.CompletionCallback> callback.</span></span>  
  
    ```  
    public sealed class AccessIdentityScope : NativeActivity  
    {  
        Collection<Activity> children;  
        Collection<Variable> variables;  
        Variable<int> currentIndex;  
        CompletionCallback onChildComplete;  
    }  
    ```  
  
3.  <span data-ttu-id="f776a-119">Implementuje konstruktora</span><span class="sxs-lookup"><span data-stu-id="f776a-119">Implement the constructor</span></span>  
  
    ```  
    public AccessIdentityScope() : base()  
    {  
        this.children = new Collection<Activity>();  
        this.variables = new Collection<Variable>();  
        this.currentIndex = new Variable<int>();  
    }  
    ```  
  
4.  <span data-ttu-id="f776a-120">Implementowanie `Activities` i `Variables` właściwości.</span><span class="sxs-lookup"><span data-stu-id="f776a-120">Implement the `Activities` and `Variables` properties.</span></span>  
  
    ```  
    public Collection<Activity> Activities  
    {  
         get { return this.children; }  
    }  
  
    public Collection<Variable> Variables  
    {  
        get { return this.variables; }  
    }  
    ```  
  
5.  <span data-ttu-id="f776a-121">Zastąpienie<xref:System.Activities.NativeActivity.CacheMetadata%2A></span><span class="sxs-lookup"><span data-stu-id="f776a-121">Override <xref:System.Activities.NativeActivity.CacheMetadata%2A></span></span>  
  
    ```  
    protected override void CacheMetadata(NativeActivityMetadata metadata)  
    {  
        //call base.CacheMetadata to add the Activities and Variables to this activity's metadata  
        base.CacheMetadata(metadata);  
        //add the private implementation variable: currentIndex   
        metadata.AddImplementationVariable(this.currentIndex);  
    }  
    ```  
  
6.  <span data-ttu-id="f776a-122">Zastąpienie<xref:System.Activities.NativeActivity.Execute%2A></span><span class="sxs-lookup"><span data-stu-id="f776a-122">Override <xref:System.Activities.NativeActivity.Execute%2A></span></span>  
  
    ```  
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
  
### <a name="implement-the-workflow-service"></a><span data-ttu-id="f776a-123">Wdrożenie usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="f776a-123">Implement the workflow service</span></span>  
  
1.  <span data-ttu-id="f776a-124">Otwórz istniejącą `Program` klasy.</span><span class="sxs-lookup"><span data-stu-id="f776a-124">Open the existing `Program` class.</span></span>  
  
2.  <span data-ttu-id="f776a-125">Zdefiniuj następujące ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="f776a-125">Define the following constants:</span></span>  
  
    ```  
    class Program  
    {  
       const string addr = "http://localhost:8080/Service";  
       static XName contract = XName.Get("IService", "http://tempuri.org");  
    }  
    ```  
  
3.  <span data-ttu-id="f776a-126">Dodaj metody statycznej o nazwie `GetWorkflowService` tworzącą usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="f776a-126">Add a static method called `GetWorkflowService` that creates the workflow service.</span></span>  
  
    ```  
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
  
4.  <span data-ttu-id="f776a-127">W istniejących `Main` metody hosta usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="f776a-127">In the existing `Main` method, host the workflow service.</span></span>  
  
    ```  
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
  
### <a name="implement-a-workflow-client"></a><span data-ttu-id="f776a-128">Implementacja klienta przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="f776a-128">Implement a workflow client</span></span>  
  
1.  <span data-ttu-id="f776a-129">Utwórz nowy projekt aplikacji konsoli o nazwie `Client`.</span><span class="sxs-lookup"><span data-stu-id="f776a-129">Create a new console application project called `Client`.</span></span>  
  
2.  <span data-ttu-id="f776a-130">Dodaj odwołania do następujących zestawów:</span><span class="sxs-lookup"><span data-stu-id="f776a-130">Add references to the following assemblies:</span></span>  
  
    1.  <span data-ttu-id="f776a-131">Elementu System.Activities</span><span class="sxs-lookup"><span data-stu-id="f776a-131">System.Activities</span></span>  
  
    2.  <span data-ttu-id="f776a-132">System.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f776a-132">System.ServiceModel</span></span>  
  
    3.  <span data-ttu-id="f776a-133">System.ServiceModel.Activities</span><span class="sxs-lookup"><span data-stu-id="f776a-133">System.ServiceModel.Activities</span></span>  
  
3.  <span data-ttu-id="f776a-134">Otwórz wygenerowany plik Program.cs i Dodaj metody statycznej o nazwie `GetClientWorkflow` Aby utworzyć przepływ pracy klienta.</span><span class="sxs-lookup"><span data-stu-id="f776a-134">Open the generated Program.cs file and add a static method called `GetClientWorkflow` to create the client workflow.</span></span>  
  
    ```  
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
  
4.  <span data-ttu-id="f776a-135">Dodaj następujący kod hostingu do `Main()` metody.</span><span class="sxs-lookup"><span data-stu-id="f776a-135">Add the following hosting code to the `Main()` method.</span></span>  
  
    ```  
    static void Main(string[] args)  
    {  
       Activity workflow = GetClientWorkflow();  
       WorkflowInvoker.Invoke(workflow);  
       WorkflowInvoker.Invoke(workflow);  
       Console.WriteLine("Press [ENTER] to exit");  
       Console.ReadLine();  
    }  
    ```  
  
## <a name="example"></a><span data-ttu-id="f776a-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="f776a-136">Example</span></span>  
 <span data-ttu-id="f776a-137">Poniżej przedstawiono pełną listę źródło kod używany w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="f776a-137">Here is a complete listing of the source code used in this topic.</span></span>  
  
```  
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
  
```  
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
  
```  
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
  
```  
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
  
## <a name="see-also"></a><span data-ttu-id="f776a-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f776a-138">See Also</span></span>  
 [<span data-ttu-id="f776a-139">Usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="f776a-139">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [<span data-ttu-id="f776a-140">Uzyskiwanie dostępu do elementu OperationContext</span><span class="sxs-lookup"><span data-stu-id="f776a-140">Accessing OperationContext</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/accessing-operationcontext.md)  
 [<span data-ttu-id="f776a-141">Tworzenie przepływów pracy, działań i wyrażenia przy użyciu kodu Imperatywne</span><span class="sxs-lookup"><span data-stu-id="f776a-141">Authoring Workflows, Activities, and Expressions Using Imperative Code</span></span>](../../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md)
