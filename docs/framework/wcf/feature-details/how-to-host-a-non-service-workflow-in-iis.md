---
title: 'Porady: hosta z systemem innym niż usługi przepływu pracy w programie IIS'
ms.date: 03/30/2017
ms.assetid: f362562c-767d-401b-8257-916616568fd4
ms.openlocfilehash: 70fd6aca94f2addd7ee568e897171ae1da86db67
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-host-a-non-service-workflow-in-iis"></a><span data-ttu-id="e21a0-102">Porady: hosta z systemem innym niż usługi przepływu pracy w programie IIS</span><span class="sxs-lookup"><span data-stu-id="e21a0-102">How to: Host a non-service workflow in IIS</span></span>
<span data-ttu-id="e21a0-103">Przepływy pracy, które nie są usługi przepływu pracy może być obsługiwany w środowisku usług IIS / WAS.</span><span class="sxs-lookup"><span data-stu-id="e21a0-103">Workflows that are not workflow services can be hosted under IIS/WAS.</span></span> <span data-ttu-id="e21a0-104">Jest to przydatne, gdy trzeba hosta przepływu pracy napisane przez innej osoby.</span><span class="sxs-lookup"><span data-stu-id="e21a0-104">This is useful when you need to host a workflow written by somebody else.</span></span> <span data-ttu-id="e21a0-105">Na przykład, jeśli rehost projektanta przepływów pracy, a użytkownicy mogą tworzyć własne przepływy pracy.</span><span class="sxs-lookup"><span data-stu-id="e21a0-105">For example, if you rehost the workflow designer and allow users to create their own workflows.</span></span>  <span data-ttu-id="e21a0-106">Hosting przepływy pracy-service w usługach IIS zapewnia obsługę funkcji, takich jak proces zamykania odtwarzania, bezczynności, monitorowanie kondycji procesu i aktywacji opartej na komunikat.</span><span class="sxs-lookup"><span data-stu-id="e21a0-106">Hosting non-service workflows in IIS provides support for features like process recycling, idle shutdown, process health monitoring, and message-based activation.</span></span> <span data-ttu-id="e21a0-107">Przepływ pracy usług hostowanych w usługach IIS zawiera <xref:System.ServiceModel.Activities.Receive> działań i są aktywowany, gdy wiadomość zostanie odebrana przez usługi IIS.</span><span class="sxs-lookup"><span data-stu-id="e21a0-107">Workflow services hosted in IIS contain <xref:System.ServiceModel.Activities.Receive> activities and are activated when a message is received by IIS.</span></span> <span data-ttu-id="e21a0-108">Non-service przepływy pracy nie zawierają działania obsługi wiadomości i domyślnie nie można aktywować, wysyłając wiadomość.</span><span class="sxs-lookup"><span data-stu-id="e21a0-108">Non-service workflows do not contain messaging activities, and by default cannot be activated by sending a message.</span></span>  <span data-ttu-id="e21a0-109">Musi pochodzić z klasy <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> i zdefiniowanie kontraktu usługi, który zawiera operacje można utworzyć wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="e21a0-109">You must derive a class from <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> and define a service contract that contains operations to create an instance of the workflow.</span></span> <span data-ttu-id="e21a0-110">Ten temat przeprowadzi Cię przez proces tworzenia prostych przepływu pracy, definiowanie kontraktu usługi, klient może używać do aktywowania przepływu pracy i wyprowadzanie klasy z <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> który używa kontraktu usługi do nasłuchiwania przepływu pracy tworzenia żądań.</span><span class="sxs-lookup"><span data-stu-id="e21a0-110">This topic will walk you through creating a simple workflow, defining a service contract a client can use to activate the workflow, and deriving a class from <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> which uses the service contract to listen for workflow creating requests.</span></span>  
  
### <a name="create-a-simple-workflow"></a><span data-ttu-id="e21a0-111">Tworzenie prostego przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="e21a0-111">Create a simple workflow</span></span>  
  
1.  <span data-ttu-id="e21a0-112">Utwórz nową [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] puste rozwiązanie o nazwie `CreationEndpointTest`.</span><span class="sxs-lookup"><span data-stu-id="e21a0-112">Create a new [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] empty solution called `CreationEndpointTest`.</span></span>  
  
2.  <span data-ttu-id="e21a0-113">Dodaj nowy projekt aplikacji usługi przepływu pracy WCF o nazwie `SimpleWorkflow` do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="e21a0-113">Add a new WCF Workflow Service Application project called `SimpleWorkflow` to the solution.</span></span> <span data-ttu-id="e21a0-114">Zostanie otwarty w Projektancie przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="e21a0-114">The workflow designer will open.</span></span>  
  
3.  <span data-ttu-id="e21a0-115">Usunięcie ReceiveRequest i SendResponse działań.</span><span class="sxs-lookup"><span data-stu-id="e21a0-115">Delete the ReceiveRequest and SendResponse activities.</span></span> <span data-ttu-id="e21a0-116">Te działania są, co sprawia, że przepływ pracy usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="e21a0-116">These activities are what makes a workflow a workflow service.</span></span> <span data-ttu-id="e21a0-117">Ponieważ firma Microsoft nie działają z usługą przepływu pracy, firma Microsoft nie jest już potrzebne.</span><span class="sxs-lookup"><span data-stu-id="e21a0-117">Since we are not working with a workflow service, we no longer need them.</span></span>  
  
4.  <span data-ttu-id="e21a0-118">Ustaw wartość DisplayName dla działania sequence "Sekwencyjnego przepływu pracy".</span><span class="sxs-lookup"><span data-stu-id="e21a0-118">Set the DisplayName for the sequence activity to "Sequential Workflow".</span></span>  
  
5.  <span data-ttu-id="e21a0-119">Zmień nazwę Service1.xamlx na Workflow1.xamlx.</span><span class="sxs-lookup"><span data-stu-id="e21a0-119">Rename Service1.xamlx to Workflow1.xamlx.</span></span>  
  
6.  <span data-ttu-id="e21a0-120">Kliknij projektanta poza działania sequence, a następnie ustawić właściwości nazwy i ConfigurationName "Workflow1"</span><span class="sxs-lookup"><span data-stu-id="e21a0-120">Click the designer outside of the sequence activity, and set the Name and ConfigurationName properties to "Workflow1"</span></span>  
  
7.  <span data-ttu-id="e21a0-121">Przeciągnij <xref:System.Activities.Statements.WriteLine> działania do <xref:System.Activities.Statements.Sequence>.</span><span class="sxs-lookup"><span data-stu-id="e21a0-121">Drag a <xref:System.Activities.Statements.WriteLine> activity into the <xref:System.Activities.Statements.Sequence>.</span></span> <span data-ttu-id="e21a0-122"><xref:System.Activities.Statements.WriteLine> Działania można znaleźć w **podstawowych** sekcji przybornika.</span><span class="sxs-lookup"><span data-stu-id="e21a0-122">The <xref:System.Activities.Statements.WriteLine> activity can be found in the **Primitives** section of the toolbox.</span></span> <span data-ttu-id="e21a0-123">Ustaw <xref:System.Activities.Statements.WriteLine.Text%2A> właściwość <xref:System.Activities.Statements.WriteLine> do działania "Hello, world".</span><span class="sxs-lookup"><span data-stu-id="e21a0-123">Set the <xref:System.Activities.Statements.WriteLine.Text%2A> property of the <xref:System.Activities.Statements.WriteLine> activity to "Hello, world".</span></span>  
  
     <span data-ttu-id="e21a0-124">Przepływ pracy powinna wyglądać podobnie jak na poniższym diagramie.</span><span class="sxs-lookup"><span data-stu-id="e21a0-124">The workflow should now look like the following diagram.</span></span>  
  
     <span data-ttu-id="e21a0-125">![Proste przepływu pracy](../../../../docs/framework/wcf/feature-details/media/simpleworkflow.png "SimpleWorkflow")</span><span class="sxs-lookup"><span data-stu-id="e21a0-125">![A simple workflow](../../../../docs/framework/wcf/feature-details/media/simpleworkflow.png "SimpleWorkflow")</span></span>  
  
### <a name="create-the-workflow-creation-service-contract"></a><span data-ttu-id="e21a0-126">Tworzenie kontraktu usługi tworzenia przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="e21a0-126">Create the workflow creation service contract</span></span>  
  
1.  <span data-ttu-id="e21a0-127">Dodawanie nowego projektu biblioteki klas o nazwie `Shared` do `CreationEndpointTest` rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="e21a0-127">Add a new class library project called `Shared` to the `CreationEndpointTest` solution.</span></span>  
  
2.  <span data-ttu-id="e21a0-128">Dodaj odwołanie do System.ServiceModel.dll, System.Configuration i System.ServiceModel.Activities do `Shared` projektu.</span><span class="sxs-lookup"><span data-stu-id="e21a0-128">Add a reference to System.ServiceModel.dll, System.Configuration, and System.ServiceModel.Activities to the `Shared` project.</span></span>  
  
3.  <span data-ttu-id="e21a0-129">Zmień nazwę pliku Class1.cs IWorkflowCreation.cs i następujący kod do pliku.</span><span class="sxs-lookup"><span data-stu-id="e21a0-129">Rename the Class1.cs file to IWorkflowCreation.cs and the following code to the file.</span></span>  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using System.ServiceModel;  
  
    namespace Shared  
    {  
        //service contract exposed from the endpoint  
        [ServiceContract(Name = "IWorkflowCreation")]  
        public interface IWorkflowCreation  
        {  
            [OperationContract(Name = "Create")]  
            Guid Create(IDictionary<string, object> inputs);  
  
            [OperationContract(Name = "CreateWithInstanceId", IsOneWay = true)]  
            void CreateWithInstanceId(IDictionary<string, object> inputs, Guid instanceId);  
        }  
    }  
    ```  
  
     <span data-ttu-id="e21a0-130">Ten kontrakt definiuje dwie operacje zarówno Tworzenie nowego wystąpienia przepływu pracy z systemem innym niż usługi utworzony.</span><span class="sxs-lookup"><span data-stu-id="e21a0-130">This contract defines two operations both create a new instance of the non-service workflow you just created.</span></span> <span data-ttu-id="e21a0-131">Jeden tworzy nowe wystąpienie z Identyfikatorem wystąpienia wygenerowany i innych pozwala na określenie Identyfikatora wystąpienia dla nowego wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="e21a0-131">One creates a new instance with a generated instance ID and the other allows you to specify the instance ID for the new workflow instance.</span></span>  <span data-ttu-id="e21a0-132">Obie metody umożliwiają przekazania parametrów do nowego wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="e21a0-132">Both methods allow you to pass in parameters to the new workflow instance.</span></span> <span data-ttu-id="e21a0-133">Ten kontrakt będzie udostępniany przez <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> umożliwiają klientom tworzenie nowego wystąpienia przepływu pracy z systemem innym niż usługa.</span><span class="sxs-lookup"><span data-stu-id="e21a0-133">This contract will be exposed by the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> to allow clients to create new instances of a non-service workflow.</span></span>  
  
### <a name="derive-a-class-from-workflowhostingendpoint"></a><span data-ttu-id="e21a0-134">Wyprowadzenia klasy z WorkflowHostingEndpoint</span><span class="sxs-lookup"><span data-stu-id="e21a0-134">Derive a class from WorkflowHostingEndpoint</span></span>  
  
1.  <span data-ttu-id="e21a0-135">Dodaj nową klasę o nazwie `CreationEndpoint` pochodną <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> do `Shared` projektu.</span><span class="sxs-lookup"><span data-stu-id="e21a0-135">Add a new class called `CreationEndpoint` derived from <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> to the `Shared` project.</span></span>  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Diagnostics;  
    using System.Globalization;  
    using System.ServiceModel;  
    using System.ServiceModel.Activities;  
    using System.ServiceModel.Channels;  
  
    namespace Shared  
    {  
        public class CreationEndpoint : WorkflowHostingEndpoint  
        {  
        }  
    }  
    ```  
  
2.  <span data-ttu-id="e21a0-136">Dodaj lokalne statycznego <xref:System.Uri> zmiennej o nazwie `defaultBaseUri` do `CreationEndpoint` klasy.</span><span class="sxs-lookup"><span data-stu-id="e21a0-136">Add a local static <xref:System.Uri> variable called `defaultBaseUri` to the `CreationEndpoint` class.</span></span>  
  
    ```  
    public class CreationEndpoint : WorkflowHostingEndpoint  
    {  
        static Uri defaultBaseUri;  
    }  
    ```  
  
3.  <span data-ttu-id="e21a0-137">Dodaj następujący Konstruktor do `CreationEndpoint` klasy.</span><span class="sxs-lookup"><span data-stu-id="e21a0-137">Add the following constructor to the `CreationEndpoint` class.</span></span> <span data-ttu-id="e21a0-138">Zwróć uwagę, określono `IWorkflowCreation` kontraktu usługi w wywołaniu konstruktora podstawowego.</span><span class="sxs-lookup"><span data-stu-id="e21a0-138">Notice we specify the `IWorkflowCreation` service contract in the call to the base constructor.</span></span>  
  
    ```  
    public CreationEndpoint(Binding binding, EndpointAddress address)  
       : base(typeof(IWorkflowCreation), binding, address)  
       {  
       }  
    ```  
  
4.  <span data-ttu-id="e21a0-139">Dodaj następujący Konstruktor domyślny do `CreationEndpoint` klasy.</span><span class="sxs-lookup"><span data-stu-id="e21a0-139">Add the following default constructor to the `CreationEndpoint` class.</span></span>  
  
    ```  
    public CreationEndpoint()  
       : this(GetDefaultBinding(),  
       new EndpointAddress(new Uri(DefaultBaseUri, new Uri(Guid.NewGuid().ToString(), UriKind.Relative))))  
       {  
       }  
    ```  
  
5.  <span data-ttu-id="e21a0-140">Dodawanie statycznego `DefaultBaseUri` właściwości `CreationEndpoint` klasy.</span><span class="sxs-lookup"><span data-stu-id="e21a0-140">Add a static `DefaultBaseUri` property to the `CreationEndpoint` class.</span></span> <span data-ttu-id="e21a0-141">Ta właściwość będzie służyć do przechowywania domyślny podstawowy identyfikator URI, jeśli nie jest dostępne.</span><span class="sxs-lookup"><span data-stu-id="e21a0-141">This property will be used to hold a default base URI if one is not provided.</span></span>  
  
    ```  
    static Uri DefaultBaseUri  
    {  
       get  
       {  
          if (defaultBaseUri == null)  
          {  
             defaultBaseUri = new Uri(string.Format(CultureInfo.InvariantCulture, "net.pipe://localhost/workflowCreationEndpoint/{0}/{1}",  
                Process.GetCurrentProcess().Id,  
                AppDomain.CurrentDomain.Id));  
          }  
          return defaultBaseUri;  
       }  
     }  
    ```  
  
6.  <span data-ttu-id="e21a0-142">Utwórz następującą metodę można uzyskać domyślnego powiązania do użycia podczas tworzenia punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="e21a0-142">Create the following method to get the default binding to use for the creation endpoint.</span></span>  
  
    ```  
    //defaults to NetNamedPipeBinding  
    public static Binding GetDefaultBinding()  
    {  
       return new NetNamedPipeBinding(NetNamedPipeSecurityMode.None) { TransactionFlow = true };  
    }  
    ```  
  
7.  <span data-ttu-id="e21a0-143">Zastąpienie <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetInstanceId%2A> metodę, aby zwracać identyfikator wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="e21a0-143">Override the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetInstanceId%2A> method to return the workflow instance ID.</span></span> <span data-ttu-id="e21a0-144">Jeśli `Action` kończy się nagłówka "Utwórz" zwraca pusty identyfikator GUID, jeśli `Action` nagłówka kończy się wyrazem "CreateWithInstanceId" return identyfikator GUID przekazany do metody.</span><span class="sxs-lookup"><span data-stu-id="e21a0-144">If the `Action` header ends with "Create" return an empty GUID, if the `Action` header ends with "CreateWithInstanceId" return the GUID passed into the method.</span></span> <span data-ttu-id="e21a0-145">W przeciwnym razie throw <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="e21a0-145">Otherwise, throw an <xref:System.InvalidOperationException>.</span></span> <span data-ttu-id="e21a0-146">Te `Action` nagłówki odpowiadają tych dwóch operacji zdefiniowanej w `IWorkflowCreation` kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="e21a0-146">These `Action` headers correspond to the two operations defined in the `IWorkflowCreation` service contract.</span></span>  
  
    ```  
    protected override Guid OnGetInstanceId(object[] inputs, OperationContext operationContext)  
    {  
       //Create was called by client  
       if (operationContext.IncomingMessageHeaders.Action.EndsWith("Create"))  
       {  
          return Guid.Empty;  
       }  
       //CreateWithInstanceId was called by client  
       else if (operationContext.IncomingMessageHeaders.Action.EndsWith("CreateWithInstanceId"))  
       {  
          return (Guid)inputs[1];  
       }  
       else  
       {  
          throw new InvalidOperationException("Invalid Action: " + operationContext.IncomingMessageHeaders.Action);  
       }  
    }  
    ```  
  
8.  <span data-ttu-id="e21a0-147">Zastąpienie <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetCreationContext%2A> metodę w celu utworzenia <xref:System.ServiceModel.Activities.WorkflowCreationContext> i dodać żadnych argumentów dla przepływu pracy, wysyła do klienta, identyfikator wystąpienia, a następnie wróć <xref:System.ServiceModel.Activities.WorkflowCreationContext>.</span><span class="sxs-lookup"><span data-stu-id="e21a0-147">Override the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetCreationContext%2A> method to create a <xref:System.ServiceModel.Activities.WorkflowCreationContext> and add any arguments for the workflow, send the instance ID to the client, and then return the <xref:System.ServiceModel.Activities.WorkflowCreationContext>.</span></span>  
  
    ```  
    protected override WorkflowCreationContext OnGetCreationContext(object[] inputs, OperationContext operationContext, Guid instanceId, WorkflowHostingResponseContext responseContext)  
    {  
       WorkflowCreationContext creationContext = new WorkflowCreationContext();  
       if (operationContext.IncomingMessageHeaders.Action.EndsWith("Create") || (operationContext.IncomingMessageHeaders.Action.EndsWith("CreateWithInstanceId")))  
       {  
          Dictionary<string, object> arguments = (Dictionary<string, object>)inputs[0];  
          if (arguments != null && arguments.Count > 0)  
          {  
             foreach (KeyValuePair<string, object> pair in arguments)  
             {  
                //arguments to pass to the workflow  
                creationContext.WorkflowArguments.Add(pair.Key, pair.Value);  
             }  
          }  
          //reply to client with instanceId  
          responseContext.SendResponse(instanceId, null);  
       }  
       else  
       {  
          throw new InvalidOperationException("Invalid Action: " + operationContext.IncomingMessageHeaders.Action);  
       }  
       return creationContext;  
    }  
    ```  
  
### <a name="create-a-standard-endpoint-element-to-allow-you-to-configure-the-workflowcreationendpoint"></a><span data-ttu-id="e21a0-148">Utwórz element standardowy punkt końcowy pozwala skonfigurować WorkflowCreationEndpoint</span><span class="sxs-lookup"><span data-stu-id="e21a0-148">Create a standard endpoint element to allow you to configure the WorkflowCreationEndpoint</span></span>  
  
1.  <span data-ttu-id="e21a0-149">Dodaj odwołanie do Shared w `CreationEndpoint` projektu</span><span class="sxs-lookup"><span data-stu-id="e21a0-149">Add a reference to Shared in the `CreationEndpoint` project</span></span>  
  
2.  <span data-ttu-id="e21a0-150">Dodaj nową klasę o nazwie `CreationEndpointElement`, pochodną <xref:System.ServiceModel.Configuration.StandardEndpointElement> do `CreationEndpoint` projektu.</span><span class="sxs-lookup"><span data-stu-id="e21a0-150">Add a new class called `CreationEndpointElement`, derived from <xref:System.ServiceModel.Configuration.StandardEndpointElement> to the `CreationEndpoint` project.</span></span> <span data-ttu-id="e21a0-151">Ta klasa reprezentuje `CreationEndpoint` w pliku web.config.</span><span class="sxs-lookup"><span data-stu-id="e21a0-151">This class will represent a `CreationEndpoint` in a web.config file.</span></span>  
  
    ```  
    using System;  
    using System.Configuration;  
    using System.ServiceModel.Activities;  
    using System.ServiceModel.Configuration;  
    using System.ServiceModel.Description;  
    using Shared;  
  
    namespace CreationEndpointTest  
    {  
        //config element for CreationEndpoint  
        public class CreationEndpointElement : StandardEndpointElement  
        {  
       }  
    ```  
  
3.  <span data-ttu-id="e21a0-152">Dodaj właściwość o nazwie `EndpointType` jak zwracany typ punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="e21a0-152">Add a property called `EndpointType` to return the type of the endpoint.</span></span>  
  
    ```  
    protected override Type EndpointType  
    {  
       get { return typeof(CreationEndpoint); }  
    }  
    ```  
  
4.  <span data-ttu-id="e21a0-153">Zastąpienie <xref:System.ServiceModel.Configuration.StandardEndpointElement.CreateServiceEndpoint%2A> — metoda i zwracają nowe `CreationEndpoint`.</span><span class="sxs-lookup"><span data-stu-id="e21a0-153">Override the <xref:System.ServiceModel.Configuration.StandardEndpointElement.CreateServiceEndpoint%2A> method and return a new `CreationEndpoint`.</span></span>  
  
    ```  
    protected override ServiceEndpoint CreateServiceEndpoint(ContractDescription contractDescription)  
    {  
       return new CreationEndpoint();  
    }  
    ```  
  
5.  <span data-ttu-id="e21a0-154">Przeciążenia <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnApplyConfiguration%2A>, <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnApplyConfiguration%2A>, <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnInitializeAndValidate%2A>, i <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnInitializeAndValidate%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="e21a0-154">Overload the <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnApplyConfiguration%2A>, <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnApplyConfiguration%2A>, <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnInitializeAndValidate%2A>, and <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnInitializeAndValidate%2A> methods.</span></span> <span data-ttu-id="e21a0-155">Te metody wystarczy, że ma zostać zdefiniowana, nie trzeba dodać kod do nich.</span><span class="sxs-lookup"><span data-stu-id="e21a0-155">These methods just need to be defined, you do not need to add any code to them.</span></span>  
  
    ```  
    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ChannelEndpointElement channelEndpointElement)  
    {  
    }  
  
    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ServiceEndpointElement serviceEndpointElement)  
    {  
    }  
  
    protected override void OnInitializeAndValidate(ChannelEndpointElement channelEndpointElement)  
    {  
    }  
  
    protected override void OnInitializeAndValidate(ServiceEndpointElement serviceEndpointElement)  
    {  
    }  
    ```  
  
6.  <span data-ttu-id="e21a0-156">Dodaj klasę kolekcji dla `CreationEndpoint` do pliku CreationEndpointElement.cs w `CreationEndpoint` projektu.</span><span class="sxs-lookup"><span data-stu-id="e21a0-156">Add the collection class for `CreationEndpoint` to the CreationEndpointElement.cs file in the `CreationEndpoint` project.</span></span> <span data-ttu-id="e21a0-157">Ta klasa jest używana przez konfigurację, aby pomieścić szereg `CreationEndpoint` wystąpień w pliku web.config.</span><span class="sxs-lookup"><span data-stu-id="e21a0-157">This class is used by configuration to hold a number of `CreationEndpoint` instances in a web.config file.</span></span>  
  
    ```  
    public class CreationEndpointCollection : StandardEndpointCollectionElement<CreationEndpoint, CreationEndpointElement>  
    {  
    }  
    ```  
  
7.  <span data-ttu-id="e21a0-158">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="e21a0-158">Build the solution.</span></span>  
  
### <a name="host-the-workflow-in-iis"></a><span data-ttu-id="e21a0-159">Hosta przepływu pracy w programie IIS</span><span class="sxs-lookup"><span data-stu-id="e21a0-159">Host the workflow in IIS</span></span>  
  
1.  <span data-ttu-id="e21a0-160">Utwórz nową aplikację o nazwie `MyCreationEndpoint` w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="e21a0-160">Create a new application called `MyCreationEndpoint` in IIS.</span></span>  
  
2.  <span data-ttu-id="e21a0-161">Skopiuj plik workflow1.xaml generowany przez projektanta przepływów pracy do katalogu aplikacji i zmień jego nazwę na workflow1.xamlx.</span><span class="sxs-lookup"><span data-stu-id="e21a0-161">Copy the workflow1.xaml file generated by the workflow designer to the application directory and rename it to workflow1.xamlx.</span></span>  
  
3.  <span data-ttu-id="e21a0-162">Skopiuj shared.dll i CreationEndpoint.dll pliki do katalogu bin aplikacji (Utwórz katalog bin, jeśli nie jest zainstalowany).</span><span class="sxs-lookup"><span data-stu-id="e21a0-162">Copy the shared.dll and CreationEndpoint.dll files to the application’s bin directory (create the bin directory if it is not present).</span></span>  
  
4.  <span data-ttu-id="e21a0-163">Zastąp zawartość pliku Web.config w `CreationEndpoint` projektu z następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="e21a0-163">Replace the contents of the Web.config file in the `CreationEndpoint` project with the following code.</span></span>  
  
    ```xaml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.web>  
        <compilation debug="true" targetFramework="4.0" />  
      </system.web>   
    </configuration>  
    ```  
  
5.  <span data-ttu-id="e21a0-164">Po `<system.web>` elementu rejestru `CreationEndpoint` przez dodanie poniższego kodu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e21a0-164">After the `<system.web>` element, register `CreationEndpoint` by adding the following configuration code.</span></span>  
  
    ```xml  
    <system.serviceModel>  
        <!--register CreationEndpoint-->  
        <serviceHostingEnvironment multipleSiteBindingsEnabled="true" />  
        <extensions>  
          <endpointExtensions>  
            <add name="creationEndpoint" type="CreationEndpointTest.CreationEndpointCollection, CreationEndpoint, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
          </endpointExtensions>  
        </extensions>  
    </system.serviceModel>  
    ```  
  
     <span data-ttu-id="e21a0-165">Rejestruje to `CreationEndpointCollection` klasy, dlatego można skonfigurować `CreationEndpoint` w pliku web.config.</span><span class="sxs-lookup"><span data-stu-id="e21a0-165">This registers the `CreationEndpointCollection` class so you can configure a `CreationEndpoint` in a web.config file.</span></span>  
  
6.  <span data-ttu-id="e21a0-166">Dodaj `<service>` elementu (po \</extensions > tagu) z `CreationEndpoint` którego będzie nasłuchiwać komunikatów przychodzących.</span><span class="sxs-lookup"><span data-stu-id="e21a0-166">Add a `<service>` element (after the \</extensions> tag) with a `CreationEndpoint` which will listen for incoming messages.</span></span>  
  
    ```xml  
    <services>  
          <!-- add endpoint to service-->  
          <service name="Workflow1" behaviorConfiguration="basicConfig" >  
            <endpoint kind="creationEndpoint" binding="basicHttpBinding" address=""/>  
          </service>  
        </services>  
    ```  
  
7.  <span data-ttu-id="e21a0-167">Dodaj \<zachowania > elementu (po  \< /usług > tagów) Aby włączyć metadane usługi.</span><span class="sxs-lookup"><span data-stu-id="e21a0-167">Add a \<behaviors> element (after the \</services> tag) to enable service metadata.</span></span>  
  
    ```xml  
    <behaviors>  
          <serviceBehaviors>  
            <behavior name="basicConfig">  
              <serviceMetadata httpGetEnabled="true" />  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
    ```  
  
8.  <span data-ttu-id="e21a0-168">Kopiowanie pliku web.config w katalogu aplikacji usług IIS.</span><span class="sxs-lookup"><span data-stu-id="e21a0-168">Copy the web.config to your IIS application directory.</span></span>  
  
9. <span data-ttu-id="e21a0-169">Sprawdzenie, czy punkt końcowy tworzenia działa przez uruchomienie programu Internet Explorer i przejdź do http://localhost/MyCreationEndpoint/Workflow1.xamlx.</span><span class="sxs-lookup"><span data-stu-id="e21a0-169">Test to see if the creation endpoint is working by starting Internet Explorer and browsing to http://localhost/MyCreationEndpoint/Workflow1.xamlx.</span></span> <span data-ttu-id="e21a0-170">Program Internet Explorer powinien być wyświetlany następujący ekran:</span><span class="sxs-lookup"><span data-stu-id="e21a0-170">Internet Explorer should display the following screen:</span></span>  
  
     <span data-ttu-id="e21a0-171">![Testowanie usługi](../../../../docs/framework/wcf/feature-details/media/testservice.gif "TestService")</span><span class="sxs-lookup"><span data-stu-id="e21a0-171">![Testing the service](../../../../docs/framework/wcf/feature-details/media/testservice.gif "TestService")</span></span>  
  
### <a name="create-a-client-that-will-call-the-creationendpoint"></a><span data-ttu-id="e21a0-172">Tworzenie klienta, który wywoła CreationEndpoint.</span><span class="sxs-lookup"><span data-stu-id="e21a0-172">Create a client that will call the CreationEndpoint.</span></span>  
  
1.  <span data-ttu-id="e21a0-173">Dodaj nową aplikację konsoli do `CreationEndpointTest` rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="e21a0-173">Add a new Console application to the `CreationEndpointTest` solution.</span></span>  
  
2.  <span data-ttu-id="e21a0-174">Dodaj odwołania do System.ServiceModel.dll, System.ServiceModel.Activities i `Shared` projektu.</span><span class="sxs-lookup"><span data-stu-id="e21a0-174">Add references to System.ServiceModel.dll, System.ServiceModel.Activities, and the `Shared` project.</span></span>  
  
3.  <span data-ttu-id="e21a0-175">W `Main` metody tworzenia <xref:System.ServiceModel.ChannelFactory%601> typu `IWorkflowCreation` i Wywołaj <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A>.</span><span class="sxs-lookup"><span data-stu-id="e21a0-175">In the `Main` method create a <xref:System.ServiceModel.ChannelFactory%601> of type `IWorkflowCreation` and call <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A>.</span></span> <span data-ttu-id="e21a0-176">Spowoduje to przywrócenie serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="e21a0-176">This will return a proxy.</span></span> <span data-ttu-id="e21a0-177">Następnie można wywołać `Create` na tym serwerze proxy można utworzyć wystąpienia przepływu pracy hostowanej przez usługi IIS:</span><span class="sxs-lookup"><span data-stu-id="e21a0-177">You can then call `Create` on that proxy to create the workflow instance hosted under IIS:</span></span>  
  
    ```  
    using System.Text;  
    using Shared;  
    using System.ServiceModel;  
  
    namespace CreationEndpointClient  
    {  
        class Program  
        {  
            static void Main(string[] args)  
            {  
                try  
                {  
                    //client using BasicHttpBinding  
                    IWorkflowCreation client = new ChannelFactory<IWorkflowCreation>(new BasicHttpBinding(), new EndpointAddress("http://localhost/CreationEndpoint/Workflow1.xamlx")).CreateChannel();  
  
                    Console.WriteLine("Workflow Instance created using CreationEndpoint added in config. Instance Id: {0}", client.Create(null));  
                    Console.WriteLine("Press return to exit ...");  
                    Console.ReadLine();  
                }  
                catch (Exception ex)  
                {  
                    Console.WriteLine(ex);  
                    Console.ReadLine();  
                }  
            }  
        }  
    }  
    ```  
  
4.  <span data-ttu-id="e21a0-178">Uruchom CreationEndpointClient.</span><span class="sxs-lookup"><span data-stu-id="e21a0-178">Run the CreationEndpointClient.</span></span> <span data-ttu-id="e21a0-179">Dane wyjściowe powinny wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="e21a0-179">The output should look like the following:</span></span>  
  
    ```Output  
    Workflow Instance created using CreationEndpoint added in config. Instance Id: 0875dac0-2b8b-473e-b3cc-abcb235e9693Press return to exit ...  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="e21a0-180">Nie będą widzieć danych wyjściowych przepływu pracy, ponieważ jest on uruchomiony w środowisku usług IIS, którego żadnych danych wyjściowych konsoli.</span><span class="sxs-lookup"><span data-stu-id="e21a0-180">You will not see the output of the workflow because it is running under IIS which has no console output.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e21a0-181">Przykład</span><span class="sxs-lookup"><span data-stu-id="e21a0-181">Example</span></span>  
 <span data-ttu-id="e21a0-182">Oto kompletny kod dla tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="e21a0-182">The following is the complete code for this sample.</span></span>  
  
```xaml  
<!-— workflow1.xamlx -->  
<WorkflowService mc:Ignorable="sap"   
                 ConfigurationName="Workflow1"   
                 sap:VirtualizedContainerService.HintSize="263,230"   
                 Name="Workflow1"   
                 mva:VisualBasic.Settings="Assembly references and imported namespaces serialized as XML namespaces"   
                 xmlns="http://schemas.microsoft.com/netfx/2009/xaml/servicemodel"   
                 xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"   
                 xmlns:mv="clr-namespace:Microsoft.VisualBasic;assembly=System"   
                 xmlns:mva="clr-namespace:Microsoft.VisualBasic.Activities;assembly=System.Activities"   
                 xmlns:p="http://schemas.microsoft.com/netfx/2009/xaml/activities"   
                 xmlns:s="clr-namespace:System;assembly=mscorlib"   
                 xmlns:s1="clr-namespace:System;assembly=System"   
                 xmlns:s2="clr-namespace:System;assembly=System.Xml"   
                 xmlns:s3="clr-namespace:System;assembly=System.Core"   
                 xmlns:sad="clr-namespace:System.Activities.Debugger;assembly=System.Activities"   
                 xmlns:sap="http://schemas.microsoft.com/netfx/2009/xaml/activities/presentation"   
                 xmlns:scg="clr-namespace:System.Collections.Generic;assembly=System"   
                 xmlns:scg1="clr-namespace:System.Collections.Generic;assembly=System.ServiceModel"   
                 xmlns:scg2="clr-namespace:System.Collections.Generic;assembly=System.Core"   
                 xmlns:scg3="clr-namespace:System.Collections.Generic;assembly=mscorlib"   
                 xmlns:sd="clr-namespace:System.Data;assembly=System.Data"   
                 xmlns:sl="clr-namespace:System.Linq;assembly=System.Core"   
                 xmlns:st="clr-namespace:System.Text;assembly=mscorlib"   
                 xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <p:Sequence DisplayName="Sequential Service"   
              sad:XamlDebuggerXmlReader.FileName="c:\projects\CreationEndpointTest\CreationEndpoint\Service1.xamlx"   
              sap:VirtualizedContainerService.HintSize="233,200"   
              mva:VisualBasic.Settings="Assembly references and imported namespaces serialized as XML namespaces">  
    <p:Sequence.Variables>  
      <p:Variable x:TypeArguments="CorrelationHandle" Name="handle" />  
      <p:Variable x:TypeArguments="x:Int32" Name="data" />  
    </p:Sequence.Variables>  
    <sap:WorkflowViewStateService.ViewState>  
      <scg3:Dictionary x:TypeArguments="x:String, x:Object">  
        <x:Boolean x:Key="IsExpanded">True</x:Boolean>  
      </scg3:Dictionary>  
    </sap:WorkflowViewStateService.ViewState>  
    <p:WriteLine sap:VirtualizedContainerService.HintSize="211,61" Text="Hello, world" />  
  </p:Sequence>  
</WorkflowService>  
```  
  
```csharp  
// CreationEndpointElement.cs  
using System;  
using System.Configuration;  
using System.ServiceModel.Activities;  
using System.ServiceModel.Configuration;  
using System.ServiceModel.Description;  
using Shared;  
  
namespace CreationEndpointTest  
{  
    //config element for CreationEndpoint  
    public class CreationEndpointElement : StandardEndpointElement  
    {  
        protected override Type EndpointType  
        {  
            get { return typeof(CreationEndpoint); }  
        }  
  
        protected override ConfigurationPropertyCollection Properties  
        {  
            get  
            {  
                ConfigurationPropertyCollection properties = base.Properties;  
                properties.Add(new ConfigurationProperty("name", typeof(String), null, ConfigurationPropertyOptions.IsRequired));  
                return properties;  
            }  
        }  
  
        protected override ServiceEndpoint CreateServiceEndpoint(ContractDescription contractDescription)  
        {  
            return new CreationEndpoint();  
        }  
  
        protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ChannelEndpointElement channelEndpointElement)  
        {  
        }  
  
        protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ServiceEndpointElement serviceEndpointElement)  
        {  
        }  
  
        protected override void OnInitializeAndValidate(ChannelEndpointElement channelEndpointElement)  
        {  
        }  
  
        protected override void OnInitializeAndValidate(ServiceEndpointElement serviceEndpointElement)  
        {  
        }  
    }  
  
    public class CreationEndpointCollection : StandardEndpointCollectionElement<CreationEndpoint, CreationEndpointElement>  
    {  
    }  
}  
```  
  
```xml  
<!-- web.config -->  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.web>  
    <compilation debug="true" targetFramework="4.0" />  
  </system.web>  
  <system.serviceModel>  
    <!--register CreationEndpoint-->  
    <serviceHostingEnvironment multipleSiteBindingsEnabled="true" />  
    <extensions>  
      <endpointExtensions>  
        <add name="creationEndpoint" type="CreationEndpointTest.CreationEndpointCollection, Shared, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
      </endpointExtensions>  
    </extensions>  
    <services>  
      <!-- add endpoint to service-->  
      <service name="Workflow1" behaviorConfiguration="basicConfig" >  
        <endpoint kind="creationEndpoint" binding="basicHttpBinding" address=""/>  
      </service>  
    </services>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="basicConfig">  
          <serviceMetadata httpGetEnabled="true" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
```csharp  
// IWorkflowCreation.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.ServiceModel;  
  
namespace Shared  
{  
    //service contract exposed from the endpoint  
    [ServiceContract(Name = "IWorkflowCreation")]  
    public interface IWorkflowCreation  
    {  
        [OperationContract(Name = "Create")]  
        Guid Create(IDictionary<string, object> inputs);  
  
        [OperationContract(Name = "CreateWithInstanceId", IsOneWay = true)]  
        void CreateWithInstanceId(IDictionary<string, object> inputs, Guid instanceId);  
    }  
}  
```  
  
```csharp  
// CreationEndpoint.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.ServiceModel.Activities;  
using System.ServiceModel.Channels;  
using System.ServiceModel;  
using System.Globalization;  
using System.Diagnostics;  
  
namespace Shared  
{  
    public class CreationEndpoint : WorkflowHostingEndpoint  
    {  
        static Uri defaultBaseUri;  
  
        public CreationEndpoint(Binding binding, EndpointAddress address)  
            : base(typeof(IWorkflowCreation), binding, address) { }  
  
        public CreationEndpoint()  
            : this(GetDefaultBinding(),  
                new EndpointAddress(new Uri(DefaultBaseUri, new Uri(Guid.NewGuid().ToString(), UriKind.Relative)))) { }  
  
        static Uri DefaultBaseUri  
        {  
            get  
            {  
                if (defaultBaseUri == null)  
                {  
                    defaultBaseUri = new Uri(string.Format(CultureInfo.InvariantCulture, "net.pipe://localhost/workflowCreationEndpoint/{0}/{1}",  
                        Process.GetCurrentProcess().Id,  
                        AppDomain.CurrentDomain.Id));  
                }  
                return defaultBaseUri;  
            }  
        }  
  
        //defaults to NetNamedPipeBinding  
        public static Binding GetDefaultBinding()  
        {  
            return new NetNamedPipeBinding(NetNamedPipeSecurityMode.None) { TransactionFlow = true };  
        }  
  
        protected override Guid OnGetInstanceId(object[] inputs, OperationContext operationContext)  
        {  
            //Create was called by client  
            if (operationContext.IncomingMessageHeaders.Action.EndsWith("Create"))  
            {  
                return Guid.Empty;  
            }  
  
            //CreateWithInstanceId was called by client  
            else if (operationContext.IncomingMessageHeaders.Action.EndsWith("CreateWithInstanceId"))  
            {  
                return (Guid)inputs[1];  
            }  
            else  
            {  
                throw new InvalidOperationException("Invalid Action: " + operationContext.IncomingMessageHeaders.Action);  
            }  
        }  
  
        protected override WorkflowCreationContext OnGetCreationContext(object[] inputs, OperationContext operationContext, Guid instanceId, WorkflowHostingResponseContext responseContext)  
        {  
            WorkflowCreationContext creationContext = new WorkflowCreationContext();  
            if (operationContext.IncomingMessageHeaders.Action.EndsWith("Create"))  
            {  
                Dictionary<string, object> arguments = (Dictionary<string, object>)inputs[0];  
                if (arguments != null && arguments.Count > 0)  
                {  
                    foreach (KeyValuePair<string, object> pair in arguments)  
                    {  
                        //arguments to pass to the workflow  
                        creationContext.WorkflowArguments.Add(pair.Key, pair.Value);  
                    }  
                }  
                //reply to client with instanceId  
                responseContext.SendResponse(instanceId, null);  
            }  
            else if (operationContext.IncomingMessageHeaders.Action.EndsWith("CreateWithInstanceId"))  
            {  
                Dictionary<string, object> arguments = (Dictionary<string, object>)inputs[0];  
                if (arguments != null && arguments.Count > 0)  
                {  
                    foreach (KeyValuePair<string, object> pair in arguments)  
                    {  
                        //arguments to pass to workflow  
                        creationContext.WorkflowArguments.Add(pair.Key, pair.Value);  
                    }  
                }  
            }  
            else  
            {  
                throw new InvalidOperationException("Invalid Action: " + operationContext.IncomingMessageHeaders.Action);  
            }  
            return creationContext;  
        }  
    }  
}  
```  
  
```csharp  
// CreationEndpointClient.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using Shared;  
using System.ServiceModel;  
  
namespace CreationClient  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            try  
            {  
                //client using BasicHttpBinding  
                IWorkflowCreation client = new ChannelFactory<IWorkflowCreation>(new BasicHttpBinding(), new EndpointAddress("http://localhost/MyCreationEndpoint/Workflow1.xamlx")).CreateChannel();  
  
                Console.WriteLine("Workflow Instance created using CreationEndpoint added in config. Instance Id: {0}", client.Create(null));  
                Console.WriteLine("Press return to exit ...");  
                Console.ReadLine();  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine(ex);  
                Console.ReadLine();  
            }  
  
        }  
    }  
  
}  
```  
  
 <span data-ttu-id="e21a0-183">W tym przykładzie mogą być mylące, ponieważ nie implementuje usługi, który implementuje `IWorkflowCreation`.</span><span class="sxs-lookup"><span data-stu-id="e21a0-183">This example may seem confusing because you never implement a service that implements `IWorkflowCreation`.</span></span> <span data-ttu-id="e21a0-184">Jest to spowodowane `CreationEndpoint` robi to za Ciebie.</span><span class="sxs-lookup"><span data-stu-id="e21a0-184">This is because the `CreationEndpoint` does this for you.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e21a0-185">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e21a0-185">See Also</span></span>  
 [<span data-ttu-id="e21a0-186">Usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="e21a0-186">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [<span data-ttu-id="e21a0-187">Hostowanie przez Internetowe usługi informacyjne</span><span class="sxs-lookup"><span data-stu-id="e21a0-187">Hosting in Internet Information Services</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)  
 [<span data-ttu-id="e21a0-188">Najlepsze rozwiązania dotyczące hostowania Internetowych usług informacyjnych</span><span class="sxs-lookup"><span data-stu-id="e21a0-188">Internet Information Services Hosting Best Practices</span></span>](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)  
 [<span data-ttu-id="e21a0-189">Instrukcje dotyczące hostowania internetowej usługi informacyjnej</span><span class="sxs-lookup"><span data-stu-id="e21a0-189">Internet Information Service Hosting Instructions</span></span>](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)  
 [<span data-ttu-id="e21a0-190">Architektura programu Windows Workflow</span><span class="sxs-lookup"><span data-stu-id="e21a0-190">Windows Workflow Architecture</span></span>](../../../../docs/framework/windows-workflow-foundation/architecture.md)  
 [<span data-ttu-id="e21a0-191">Wznowienie zakładki WorkflowHostingEndpoint</span><span class="sxs-lookup"><span data-stu-id="e21a0-191">WorkflowHostingEndpoint Resume Bookmark</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/workflowhostingendpoint-resume-bookmark.md)  
 [<span data-ttu-id="e21a0-192">Rehostowanie projektanta przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="e21a0-192">Rehosting the Workflow Designer</span></span>](../../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)  
 [<span data-ttu-id="e21a0-193">Omówienie programu Windows Workflow</span><span class="sxs-lookup"><span data-stu-id="e21a0-193">Windows Workflow Overview</span></span>](../../../../docs/framework/windows-workflow-foundation/overview.md)
