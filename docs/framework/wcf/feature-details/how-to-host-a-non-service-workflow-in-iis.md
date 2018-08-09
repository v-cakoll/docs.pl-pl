---
title: 'Porady: hosta z systemem innym niż usługi przepływu pracy w programie IIS'
ms.date: 03/30/2017
ms.assetid: f362562c-767d-401b-8257-916616568fd4
ms.openlocfilehash: 70fd6aca94f2addd7ee568e897171ae1da86db67
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33496764"
---
# <a name="how-to-host-a-non-service-workflow-in-iis"></a>Porady: hosta z systemem innym niż usługi przepływu pracy w programie IIS
Przepływy pracy, które nie są usługi przepływu pracy może być obsługiwany w środowisku usług IIS / WAS. Jest to przydatne, gdy trzeba hosta przepływu pracy napisane przez innej osoby. Na przykład, jeśli rehost projektanta przepływów pracy, a użytkownicy mogą tworzyć własne przepływy pracy.  Hosting przepływy pracy-service w usługach IIS zapewnia obsługę funkcji, takich jak proces zamykania odtwarzania, bezczynności, monitorowanie kondycji procesu i aktywacji opartej na komunikat. Przepływ pracy usług hostowanych w usługach IIS zawiera <xref:System.ServiceModel.Activities.Receive> działań i są aktywowany, gdy wiadomość zostanie odebrana przez usługi IIS. Non-service przepływy pracy nie zawierają działania obsługi wiadomości i domyślnie nie można aktywować, wysyłając wiadomość.  Musi pochodzić z klasy <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> i zdefiniowanie kontraktu usługi, który zawiera operacje można utworzyć wystąpienia przepływu pracy. Ten temat przeprowadzi Cię przez proces tworzenia prostych przepływu pracy, definiowanie kontraktu usługi, klient może używać do aktywowania przepływu pracy i wyprowadzanie klasy z <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> który używa kontraktu usługi do nasłuchiwania przepływu pracy tworzenia żądań.  
  
### <a name="create-a-simple-workflow"></a>Tworzenie prostego przepływu pracy  
  
1.  Utwórz nową [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] puste rozwiązanie o nazwie `CreationEndpointTest`.  
  
2.  Dodaj nowy projekt aplikacji usługi przepływu pracy WCF o nazwie `SimpleWorkflow` do rozwiązania. Zostanie otwarty w Projektancie przepływów pracy.  
  
3.  Usunięcie ReceiveRequest i SendResponse działań. Te działania są, co sprawia, że przepływ pracy usługi przepływu pracy. Ponieważ firma Microsoft nie działają z usługą przepływu pracy, firma Microsoft nie jest już potrzebne.  
  
4.  Ustaw wartość DisplayName dla działania sequence "Sekwencyjnego przepływu pracy".  
  
5.  Zmień nazwę Service1.xamlx na Workflow1.xamlx.  
  
6.  Kliknij projektanta poza działania sequence, a następnie ustawić właściwości nazwy i ConfigurationName "Workflow1"  
  
7.  Przeciągnij <xref:System.Activities.Statements.WriteLine> działania do <xref:System.Activities.Statements.Sequence>. <xref:System.Activities.Statements.WriteLine> Działania można znaleźć w **podstawowych** sekcji przybornika. Ustaw <xref:System.Activities.Statements.WriteLine.Text%2A> właściwość <xref:System.Activities.Statements.WriteLine> do działania "Hello, world".  
  
     Przepływ pracy powinna wyglądać podobnie jak na poniższym diagramie.  
  
     ![Proste przepływu pracy](../../../../docs/framework/wcf/feature-details/media/simpleworkflow.png "SimpleWorkflow")  
  
### <a name="create-the-workflow-creation-service-contract"></a>Tworzenie kontraktu usługi tworzenia przepływu pracy  
  
1.  Dodawanie nowego projektu biblioteki klas o nazwie `Shared` do `CreationEndpointTest` rozwiązania.  
  
2.  Dodaj odwołanie do System.ServiceModel.dll, System.Configuration i System.ServiceModel.Activities do `Shared` projektu.  
  
3.  Zmień nazwę pliku Class1.cs IWorkflowCreation.cs i następujący kod do pliku.  
  
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
  
     Ten kontrakt definiuje dwie operacje zarówno Tworzenie nowego wystąpienia przepływu pracy z systemem innym niż usługi utworzony. Jeden tworzy nowe wystąpienie z Identyfikatorem wystąpienia wygenerowany i innych pozwala na określenie Identyfikatora wystąpienia dla nowego wystąpienia przepływu pracy.  Obie metody umożliwiają przekazania parametrów do nowego wystąpienia przepływu pracy. Ten kontrakt będzie udostępniany przez <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> umożliwiają klientom tworzenie nowego wystąpienia przepływu pracy z systemem innym niż usługa.  
  
### <a name="derive-a-class-from-workflowhostingendpoint"></a>Wyprowadzenia klasy z WorkflowHostingEndpoint  
  
1.  Dodaj nową klasę o nazwie `CreationEndpoint` pochodną <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> do `Shared` projektu.  
  
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
  
2.  Dodaj lokalne statycznego <xref:System.Uri> zmiennej o nazwie `defaultBaseUri` do `CreationEndpoint` klasy.  
  
    ```  
    public class CreationEndpoint : WorkflowHostingEndpoint  
    {  
        static Uri defaultBaseUri;  
    }  
    ```  
  
3.  Dodaj następujący Konstruktor do `CreationEndpoint` klasy. Zwróć uwagę, określono `IWorkflowCreation` kontraktu usługi w wywołaniu konstruktora podstawowego.  
  
    ```  
    public CreationEndpoint(Binding binding, EndpointAddress address)  
       : base(typeof(IWorkflowCreation), binding, address)  
       {  
       }  
    ```  
  
4.  Dodaj następujący Konstruktor domyślny do `CreationEndpoint` klasy.  
  
    ```  
    public CreationEndpoint()  
       : this(GetDefaultBinding(),  
       new EndpointAddress(new Uri(DefaultBaseUri, new Uri(Guid.NewGuid().ToString(), UriKind.Relative))))  
       {  
       }  
    ```  
  
5.  Dodawanie statycznego `DefaultBaseUri` właściwości `CreationEndpoint` klasy. Ta właściwość będzie służyć do przechowywania domyślny podstawowy identyfikator URI, jeśli nie jest dostępne.  
  
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
  
6.  Utwórz następującą metodę można uzyskać domyślnego powiązania do użycia podczas tworzenia punktu końcowego.  
  
    ```  
    //defaults to NetNamedPipeBinding  
    public static Binding GetDefaultBinding()  
    {  
       return new NetNamedPipeBinding(NetNamedPipeSecurityMode.None) { TransactionFlow = true };  
    }  
    ```  
  
7.  Zastąpienie <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetInstanceId%2A> metodę, aby zwracać identyfikator wystąpienia przepływu pracy. Jeśli `Action` kończy się nagłówka "Utwórz" zwraca pusty identyfikator GUID, jeśli `Action` nagłówka kończy się wyrazem "CreateWithInstanceId" return identyfikator GUID przekazany do metody. W przeciwnym razie throw <xref:System.InvalidOperationException>. Te `Action` nagłówki odpowiadają tych dwóch operacji zdefiniowanej w `IWorkflowCreation` kontraktu usługi.  
  
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
  
8.  Zastąpienie <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetCreationContext%2A> metodę w celu utworzenia <xref:System.ServiceModel.Activities.WorkflowCreationContext> i dodać żadnych argumentów dla przepływu pracy, wysyła do klienta, identyfikator wystąpienia, a następnie wróć <xref:System.ServiceModel.Activities.WorkflowCreationContext>.  
  
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
  
### <a name="create-a-standard-endpoint-element-to-allow-you-to-configure-the-workflowcreationendpoint"></a>Utwórz element standardowy punkt końcowy pozwala skonfigurować WorkflowCreationEndpoint  
  
1.  Dodaj odwołanie do Shared w `CreationEndpoint` projektu  
  
2.  Dodaj nową klasę o nazwie `CreationEndpointElement`, pochodną <xref:System.ServiceModel.Configuration.StandardEndpointElement> do `CreationEndpoint` projektu. Ta klasa reprezentuje `CreationEndpoint` w pliku web.config.  
  
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
  
3.  Dodaj właściwość o nazwie `EndpointType` jak zwracany typ punktu końcowego.  
  
    ```  
    protected override Type EndpointType  
    {  
       get { return typeof(CreationEndpoint); }  
    }  
    ```  
  
4.  Zastąpienie <xref:System.ServiceModel.Configuration.StandardEndpointElement.CreateServiceEndpoint%2A> — metoda i zwracają nowe `CreationEndpoint`.  
  
    ```  
    protected override ServiceEndpoint CreateServiceEndpoint(ContractDescription contractDescription)  
    {  
       return new CreationEndpoint();  
    }  
    ```  
  
5.  Przeciążenia <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnApplyConfiguration%2A>, <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnApplyConfiguration%2A>, <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnInitializeAndValidate%2A>, i <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnInitializeAndValidate%2A> metody. Te metody wystarczy, że ma zostać zdefiniowana, nie trzeba dodać kod do nich.  
  
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
  
6.  Dodaj klasę kolekcji dla `CreationEndpoint` do pliku CreationEndpointElement.cs w `CreationEndpoint` projektu. Ta klasa jest używana przez konfigurację, aby pomieścić szereg `CreationEndpoint` wystąpień w pliku web.config.  
  
    ```  
    public class CreationEndpointCollection : StandardEndpointCollectionElement<CreationEndpoint, CreationEndpointElement>  
    {  
    }  
    ```  
  
7.  Skompiluj rozwiązanie.  
  
### <a name="host-the-workflow-in-iis"></a>Hosta przepływu pracy w programie IIS  
  
1.  Utwórz nową aplikację o nazwie `MyCreationEndpoint` w usługach IIS.  
  
2.  Skopiuj plik workflow1.xaml generowany przez projektanta przepływów pracy do katalogu aplikacji i zmień jego nazwę na workflow1.xamlx.  
  
3.  Skopiuj shared.dll i CreationEndpoint.dll pliki do katalogu bin aplikacji (Utwórz katalog bin, jeśli nie jest zainstalowany).  
  
4.  Zastąp zawartość pliku Web.config w `CreationEndpoint` projektu z następującym kodem.  
  
    ```xaml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.web>  
        <compilation debug="true" targetFramework="4.0" />  
      </system.web>   
    </configuration>  
    ```  
  
5.  Po `<system.web>` elementu rejestru `CreationEndpoint` przez dodanie poniższego kodu konfiguracji.  
  
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
  
     Rejestruje to `CreationEndpointCollection` klasy, dlatego można skonfigurować `CreationEndpoint` w pliku web.config.  
  
6.  Dodaj `<service>` elementu (po \</extensions > tagu) z `CreationEndpoint` którego będzie nasłuchiwać komunikatów przychodzących.  
  
    ```xml  
    <services>  
          <!-- add endpoint to service-->  
          <service name="Workflow1" behaviorConfiguration="basicConfig" >  
            <endpoint kind="creationEndpoint" binding="basicHttpBinding" address=""/>  
          </service>  
        </services>  
    ```  
  
7.  Dodaj \<zachowania > elementu (po  \< /usług > tagów) Aby włączyć metadane usługi.  
  
    ```xml  
    <behaviors>  
          <serviceBehaviors>  
            <behavior name="basicConfig">  
              <serviceMetadata httpGetEnabled="true" />  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
    ```  
  
8.  Kopiowanie pliku web.config w katalogu aplikacji usług IIS.  
  
9. Sprawdzenie, czy punkt końcowy tworzenia działa przez uruchomienie programu Internet Explorer i przejdź do http://localhost/MyCreationEndpoint/Workflow1.xamlx. Program Internet Explorer powinien być wyświetlany następujący ekran:  
  
     ![Testowanie usługi](../../../../docs/framework/wcf/feature-details/media/testservice.gif "TestService")  
  
### <a name="create-a-client-that-will-call-the-creationendpoint"></a>Tworzenie klienta, który wywoła CreationEndpoint.  
  
1.  Dodaj nową aplikację konsoli do `CreationEndpointTest` rozwiązania.  
  
2.  Dodaj odwołania do System.ServiceModel.dll, System.ServiceModel.Activities i `Shared` projektu.  
  
3.  W `Main` metody tworzenia <xref:System.ServiceModel.ChannelFactory%601> typu `IWorkflowCreation` i Wywołaj <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A>. Spowoduje to przywrócenie serwera proxy. Następnie można wywołać `Create` na tym serwerze proxy można utworzyć wystąpienia przepływu pracy hostowanej przez usługi IIS:  
  
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
  
4.  Uruchom CreationEndpointClient. Dane wyjściowe powinny wyglądać następująco:  
  
    ```Output  
    Workflow Instance created using CreationEndpoint added in config. Instance Id: 0875dac0-2b8b-473e-b3cc-abcb235e9693Press return to exit ...  
    ```  
  
    > [!NOTE]
    >  Nie będą widzieć danych wyjściowych przepływu pracy, ponieważ jest on uruchomiony w środowisku usług IIS, którego żadnych danych wyjściowych konsoli.  
  
## <a name="example"></a>Przykład  
 Oto kompletny kod dla tego przykładu.  
  
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
  
 W tym przykładzie mogą być mylące, ponieważ nie implementuje usługi, który implementuje `IWorkflowCreation`. Jest to spowodowane `CreationEndpoint` robi to za Ciebie.  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Hostowanie przez Internetowe usługi informacyjne](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)  
 [Najlepsze rozwiązania dotyczące hostowania Internetowych usług informacyjnych](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)  
 [Instrukcje dotyczące hostowania internetowej usługi informacyjnej](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)  
 [Architektura programu Windows Workflow](../../../../docs/framework/windows-workflow-foundation/architecture.md)  
 [Wznowienie zakładki WorkflowHostingEndpoint](../../../../docs/framework/windows-workflow-foundation/samples/workflowhostingendpoint-resume-bookmark.md)  
 [Rehostowanie projektanta przepływu pracy](../../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)  
 [Omówienie programu Windows Workflow](../../../../docs/framework/windows-workflow-foundation/overview.md)
