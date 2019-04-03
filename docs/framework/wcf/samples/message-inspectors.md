---
title: Inspektorzy komunikatów
ms.date: 03/30/2017
ms.assetid: 9bd1f305-ad03-4dd7-971f-fa1014b97c9b
ms.openlocfilehash: 248e74e039c0ebb0b1580ec2cb4f19d713d95c51
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58830152"
---
# <a name="message-inspectors"></a>Inspektorzy komunikatów
W tym przykładzie pokazano, jak zaimplementować i skonfigurować klienta i usługi inspektorzy komunikatów.  
  
 Inspektor wiadomość znajduje się obiekt rozszerzalności, który może służyć w modelu usług klienta w środowisku uruchomieniowym i wysyłania środowiska uruchomieniowego programowo lub za pośrednictwem konfiguracją oraz że można sprawdzić i zmienić wiadomości po odebraniu, lub przed ich wysłaniem.  
  
 W tym przykładzie implementuje podstawowe klienta i mechanizmu sprawdzania poprawności wiadomości usługi, która weryfikuje komunikaty przychodzące z zestawem dokumentów schematu XML można skonfigurować. Należy pamiętać, że w tym przykładzie nie można zweryfikować wiadomości dla każdej operacji. Jest to zamierzone uproszczenia.  
  
## <a name="message-inspector"></a>Inspektor wiadomości  
 Implementowanie inspektorzy komunikatów klienta <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> interfejsu i usługa Implementowanie inspektorzy komunikatów <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> interfejsu. Implementacje mogą być połączone w jedną klasę w celu utworzenia Inspektor komunikat, który działa w przypadku obu stronach. W tym przykładzie implementuje Inspektor połączone wiadomości. Inspektor jest konstruowany, przekazując w zestawie schematów, wobec których wiadomości przychodzące i wychodzące są weryfikowane i umożliwia deweloperom określić, czy komunikaty przychodzące lub wychodzące są prawidłowe i czy inspektor znajduje się w trybie klienta lub wysyłanie który wpływa na obsługi błędów, zgodnie z opisem w dalszej części tego tematu.  
  
```  
public class SchemaValidationMessageInspector : IClientMessageInspector, IDispatchMessageInspector  
{  
    XmlSchemaSet schemaSet;  
    bool validateRequest;  
    bool validateReply;  
    bool isClientSide;  
    [ThreadStatic]  
    bool isRequest;  
  
    public SchemaValidationMessageInspector(XmlSchemaSet schemaSet,  
         bool validateRequest, bool validateReply, bool isClientSide)  
    {  
        this.schemaSet = schemaSet;  
        this.validateReply = validateReply;  
        this.validateRequest = validateRequest;  
        this.isClientSide = isClientSide;  
    }  
```  
  
 Wszelkie Inspektor wiadomości usługi (dyspozytora) musi implementować dwa <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> metody <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> i <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>.  
  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> jest wywoływane przez Dyspozytor wiadomości odebrane, przetworzeniu przez stos kanału i przypisane do usługi, ale przed deserializacji i wysyłane do operacji. Jeśli przychodzący komunikat został zaszyfrowany, komunikat już są odszyfrowywane, po osiągnięciu Inspektor wiadomości. Metoda pobiera `request` komunikat przekazany jako parametr przekazany przez odwołanie, co pozwala komunikat, aby sprawdził, modyfikować lub zastąpić zgodnie z potrzebami. Zwracana wartość może być dowolny obiekt i jest używany jako obiekt stanu korelacji, który jest przekazywany do <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> kiedy usługa zwraca odpowiedź do bieżącej wiadomości. W tym przykładzie <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> deleguje inspekcji (zatwierdzenie) komunikatu do metody prywatnej, lokalny `ValidateMessageBody` i zwraca obiekt stanu nie korelacji. Ta metoda zapewnia, że żadne komunikaty nieprawidłowy przekazywać do usługi.  
  
```  
object IDispatchMessageInspector.AfterReceiveRequest(ref System.ServiceModel.Channels.Message request, System.ServiceModel.IClientChannel channel, System.ServiceModel.InstanceContext instanceContext)  
{  
    if (validateRequest)  
    {  
        // inspect the message. If a validation error occurs,  
        // the thrown fault exception bubbles up.  
        ValidateMessageBody(ref request, true);  
    }  
    return null;  
}  
```  
  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29> jest wywoływane zawsze wtedy, gdy odpowiedź jest gotowe do wysłania do klienta lub w przypadku jednokierunkowe komunikaty, po przetworzeniu komunikatu przychodzącego. Dzięki temu możesz liczyć na są nazywane symetrycznie, niezależnie od tego, MEP rozszerzeń. Podobnie jak w przypadku <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, komunikat jest przekazywany jako parametr przekazany przez odwołanie i można sprawdził, zmodyfikowane lub zastąpione. Sprawdzanie poprawności wiadomości, która jest wykonywana w tym przykładzie jest ponownie delegowane do `ValidMessageBody` metody, ale obsługi błędów sprawdzania poprawności różni się nieco w tym przypadku.  
  
 Jeśli wystąpi błąd sprawdzania poprawności w usłudze `ValidateMessageBody` metoda zgłasza wyjątek <xref:System.ServiceModel.FaultException>-pochodnych wyjątków. W <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, tych wyjątków można umieścić w modelu usługi infrastruktury, gdzie one są przekształcone w błędach SOAP i automatycznie przekazywane do klienta. W <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A>, <xref:System.ServiceModel.FaultException> wyjątki nie mogą być umieszczone w infrastrukturę, ponieważ przekształcenie wyjątków błędów zgłaszanych przez usługę odbywa się przed wywołaniem Inspektor wiadomości. W związku z tym następującą implementacją przechwytuje znane `ReplyValidationFault` wyjątków i zastępuje odpowiedź komunikatu o komunikat o błędzie jawnego. Ta metoda zapewnia, że żadne komunikaty nieprawidłowy są zwracane przez implementacji usługi.  
  
```  
void IDispatchMessageInspector.BeforeSendReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
{  
    if (validateReply)  
    {  
        // Inspect the reply, catch a possible validation error   
        try  
        {  
            ValidateMessageBody(ref reply, false);  
        }  
        catch (ReplyValidationFault fault)  
        {  
            // if a validation error occurred, the message is replaced  
            // with the validation fault.  
            reply = Message.CreateMessage(reply.Version,   
                    fault.CreateMessageFault(), reply.Headers.Action);  
        }  
    }  
```  
  
 Inspektor komunikat klienta jest bardzo podobne. Te dwie metody, które muszą zostać zaimplementowane z <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> są <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.AfterReceiveReply%2A> i <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>.  
  
 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> jest wywoływane, gdy komunikat został złożony, przez aplikację klienta lub przez element formatujący operacji. Zgodnie ze wysyłający inspektorzy komunikatów, po prostu komunikat sprawdzenia lub całkowicie zastąpiony. W tym przykładzie Inspektor deleguje odpowiednie uprawnienia do tej samej lokalnej `ValidateMessageBody` metody pomocnika, która jest również używany do wysyłania inspektorzy komunikatów.  
  
 Zachowania różnica między klientem a usługą sprawdzania poprawności (jak określono w konstruktorze) polega na tym, czy sprawdzanie poprawności klienta zgłasza wyjątki lokalne, które są umieszczane w kodzie użytkownika, ponieważ występują one lokalnie, a nie z powodu błędu usługi. Ogólnie rzecz biorąc jest zasada, że usługa dyspozytora inspektorzy zgłasza błędy i zgłaszają wyjątki, że inspektorzy klienta.  
  
 To <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> implementacji gwarantuje, że nie nieprawidłowy komunikaty są wysyłane do usługi.  
  
```  
object IClientMessageInspector.BeforeSendRequest(ref System.ServiceModel.Channels.Message request, System.ServiceModel.IClientChannel channel)  
{  
    if (validateRequest)  
    {  
        ValidateMessageBody(ref request, true);  
    }  
    return null;  
}  
```  
  
 `AfterReceiveReply` Implementacji gwarantuje, że brak nieprawidłowy komunikatów odebranych z usługi są przekazywane do kodu użytkownika klienta.  
  
```  
void IClientMessageInspector.AfterReceiveReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
{  
    if (validateReply)  
    {  
        ValidateMessageBody(ref reply, false);  
    }  
}  
```  
  
 To serce Inspektor tego konkretnego komunikatu `ValidateMessageBody` metody. Aby wykonać swoją pracę, jest zawijany, sprawdzanie poprawności <xref:System.Xml.XmlReader> wokół zawartości drzewo podrzędne treści przekazanych komunikatów. Czytnik jest wypełniana przy użyciu zestawu schematów, które przechowuje Inspektor wiadomości i wywołanie zwrotne weryfikacji jest ustawiona na obiekt delegowany odwołujące się do `InspectionValidationHandler` zdefiniowanego wraz z tej metody. Aby wykonać sprawdzanie poprawności, komunikat jest następnie odczytu i buforowane w pamięci z kopią zapasową w usłudze stream <xref:System.Xml.XmlDictionaryWriter>. Jeśli wystąpi błąd sprawdzania poprawności lub ostrzeżenie w procesie, wywoływana jest metoda wywołania zwrotnego.  
  
 Jeśli żaden błąd nie wystąpi, tworzony jest nowy komunikat kopiuje właściwości i nagłówki z oryginalną wiadomość, która używa zestaw informacji zweryfikowane teraz w strumień pamięci, który jest otoczony przez <xref:System.Xml.XmlDictionaryReader> i dodane do wymiany wiadomości.  
  
```  
void ValidateMessageBody(ref System.ServiceModel.Channels.Message message, bool isRequest)  
{  
    if (!message.IsFault)  
    {  
        XmlDictionaryReaderQuotas quotas =   
                new XmlDictionaryReaderQuotas();  
        XmlReader bodyReader =   
            message.GetReaderAtBodyContents().ReadSubtree();  
        XmlReaderSettings wrapperSettings =   
                              new XmlReaderSettings();  
        wrapperSettings.CloseInput = true;  
        wrapperSettings.Schemas = schemaSet;  
        wrapperSettings.ValidationFlags =   
                                XmlSchemaValidationFlags.None;  
        wrapperSettings.ValidationType = ValidationType.Schema;  
        wrapperSettings.ValidationEventHandler += new   
           ValidationEventHandler(InspectionValidationHandler);  
        XmlReader wrappedReader = XmlReader.Create(bodyReader,   
                                            wrapperSettings);  
  
        // pull body into a memory backed writer to validate  
        this.isRequest = isRequest;  
        MemoryStream memStream = new MemoryStream();  
        XmlDictionaryWriter xdw =  
              XmlDictionaryWriter.CreateBinaryWriter(memStream);  
        xdw.WriteNode(wrappedReader, false);  
        xdw.Flush(); memStream.Position = 0;  
        XmlDictionaryReader xdr =   
        XmlDictionaryReader.CreateBinaryReader(memStream, quotas);  
  
        // reconstruct the message with the validated body  
        Message replacedMessage =   
            Message.CreateMessage(message.Version, null, xdr);  
        replacedMessage.Headers.CopyHeadersFrom(message.Headers);  
        replacedMessage.Properties.CopyProperties(message.Properties);  
        message = replacedMessage;  
    }  
}  
```  
  
 `InspectionValidationHandler` Metoda jest wywoływana przez weryfikowanie <xref:System.Xml.XmlReader> zawsze, gdy występuje błąd walidacji schematu lub ostrzeżenie. Następującą implementacją działa tylko z błędami i ignoruje wszystkie ostrzeżenia.  
  
 Na pierwszym zagadnieniem mogą wydawać się możliwe do dodania, sprawdzanie poprawności <xref:System.Xml.XmlReader> do wiadomości przy użyciu Inspektora wiadomości, dzięki czemu Weryfikacja się zdarzyć, komunikat jest przetwarzany i bez buforowania wiadomości. Jednak oznacza, że to wywołanie zwrotne zgłasza wyjątki sprawdzania poprawności, gdzieś w usłudze modelu infrastruktury lub kod użytkownika, ponieważ wykryto nieprawidłowy węzłów XML, powodując nieprzewidywalne zachowanie. Buforowanie podejście ochronnym kod użytkownika z nieprawidłową wiadomości całkowicie.  
  
 Jak już wspomniano wyjątki generowane przez program obsługi różnią się między klientem a usługą. W usłudze wyjątki są uzyskiwane z <xref:System.ServiceModel.FaultException>, na komputerze klienckim wyjątki są regularnie niestandardowymi wyjątkami.  
  
```  
        void InspectionValidationHandler(object sender, ValidationEventArgs e)  
{  
    if (e.Severity == XmlSeverityType.Error)  
    {  
        // We are treating client and service side validation errors  
        // differently here. Client side errors cause exceptions  
        // and are thrown straight up to the user code. Service side  
        // validations cause faults.  
        if (isClientSide)  
        {  
            if (isRequest)  
            {  
                throw new RequestClientValidationException(e.Message);  
            }  
            else  
            {  
                throw new ReplyClientValidationException(e.Message);  
            }  
        }  
        else  
        {  
            if (isRequest)  
            {  
                // this fault is caught by the ServiceModel   
                // infrastructure and turned into a fault reply.  
                throw new RequestValidationFault(e.Message);  
             }  
             else  
             {  
                // this fault is caught and turned into a fault message  
                // in BeforeSendReply in this class  
                throw new ReplyValidationFault(e.Message);  
              }  
          }  
      }  
    }  
```  
  
## <a name="behavior"></a>Zachowanie  
 Inspektorzy komunikatów są rozszerzeniami środowiska uruchomieniowego klienta lub w środowisku uruchomieniowym wysyłania. Takie rozszerzenia są konfigurowane przy użyciu *zachowania*. To zachowanie jest klasa, która zmienia zachowanie środowiska uruchomieniowego modelu usługi zmieniania konfiguracji domyślnej lub dodając rozszerzenia (na przykład inspektorzy komunikatów).  
  
 Następujące `SchemaValidationBehavior` klasa to zachowanie umożliwia dodawanie inspektora komunikat ten przykład do klienta lub wysyłanie środowiska uruchomieniowego. Implementacja jest raczej podstawowe w obu przypadkach. W <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyClientBehavior%2A> i <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyDispatchBehavior%2A>, inspektor wiadomość zostanie utworzony i dodany do <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> zbiór odpowiedniego środowiska uruchomieniowego.  
  
```  
public class SchemaValidationBehavior : IEndpointBehavior  
{  
    XmlSchemaSet schemaSet;   
    bool validateRequest;   
    bool validateReply;  
  
    public SchemaValidationBehavior(XmlSchemaSet schemaSet, bool   
                           inspectRequest, bool inspectReply)  
    {  
        this.schemaSet = schemaSet;  
        this.validateReply = inspectReply;  
        this.validateRequest = inspectRequest;  
    }  
    #region IEndpointBehavior Members  
  
    public void AddBindingParameters(ServiceEndpoint endpoint,   
       System.ServiceModel.Channels.BindingParameterCollection   
                                            bindingParameters)  
    {  
    }  
  
    public void ApplyClientBehavior(ServiceEndpoint endpoint,   
            System.ServiceModel.Dispatcher.ClientRuntime clientRuntime)  
    {  
        SchemaValidationMessageInspector inspector =   
           new SchemaValidationMessageInspector(schemaSet,   
                      validateRequest, validateReply, true);  
            clientRuntime.MessageInspectors.Add(inspector);  
    }  
  
    public void ApplyDispatchBehavior(ServiceEndpoint endpoint,   
         System.ServiceModel.Dispatcher.EndpointDispatcher   
                                          endpointDispatcher)  
    {  
        SchemaValidationMessageInspector inspector =   
           new SchemaValidationMessageInspector(schemaSet,   
                        validateRequest, validateReply, false);  
   endpointDispatcher.DispatchRuntime.MessageInspectors.Add(inspector);  
    }  
  
   public void Validate(ServiceEndpoint endpoint)  
   {  
   }  
  
    #endregion  
}  
```  
  
> [!NOTE]
>  To zachowanie określonego nie dwukrotnie jako atrybut i dlatego nie można dodać deklaratywne na typ kontraktu typu usługi. Jest to wykonana, ponieważ kolekcja schematów nie może zostać załadowany w deklaracji atrybutu i odwołujące się do lokalizacji dodatkowej konfiguracji (na przykład w celu ustawienia aplikacji) w tym atrybucie oznacza, że tworzenie elementu konfiguracji, który decyzji projektowych nie jest zgodne z pozostałą częścią konfiguracji modelu usług. Dlatego to zachowanie można dodać tylko obowiązkowo przez kod i za pośrednictwem rozszerzenia konfiguracji modelu usług.  
  
## <a name="adding-the-message-inspector-through-configuration"></a>Dodawanie inspektora komunikat za pośrednictwem konfiguracji  
 Do konfigurowania niestandardowe zachowanie punktu końcowego w pliku konfiguracyjnym aplikacji, model usług wymaga implementacji utworzyć konfigurację *elementu rozszerzenia* reprezentowane przez klasę pochodną <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>. To rozszerzenie następnie należy dodać do sekcji konfiguracji modelu usług dla rozszerzenia, jak pokazano na następujące rozszerzenie omówione w tej sekcji.  
  
```xml  
<system.serviceModel>  
…  
   <extensions>  
      <behaviorExtensions>  
        <add name="schemaValidator" type="Microsoft.ServiceModel.Samples.SchemaValidationBehaviorExtensionElement, MessageInspectors, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null"/>  
      </behaviorExtensions>  
    </extensions>  
…  
</system.serviceModel>  
```  
  
 Rozszerzenia można dodać w aplikacji lub pliku konfiguracji platformy ASP.NET, który jest najbardziej typowe wybór, lub w pliku konfiguracji komputera.  
  
 Po dodaniu rozszerzenia zakres konfiguracji zachowanie można dodać do konfiguracji zachowania pokazany w poniższym kodzie. Zachowanie konfiguracje są elementy wielokrotnego użytku, które można zastosować do wielu punktów końcowych, zgodnie z potrzebami. Ponieważ określone zachowanie być skonfigurowane w tym miejscu implementuje <xref:System.ServiceModel.Description.IEndpointBehavior>, jest on prawidłowy tylko w sekcji odpowiedniej konfiguracji w pliku konfiguracji.  
  
```xml  
<system.serviceModel>  
   <behaviors>  
      …  
     <endpointBehaviors>  
        <behavior name="HelloServiceEndpointBehavior">  
          <schemaValidator validateRequest="True" validateReply="True">  
            <schemas>  
              <add location="messages.xsd" />    
            </schemas>  
          </schemaValidator>  
        </behavior>  
      </endpointBehaviors>  
      …  
    </behaviors>  
</system.serviceModel>  
```  
  
 `<schemaValidator>` Element, który konfiguruje Inspektor wiadomości jest wspierana przez `SchemaValidationBehaviorExtensionElement` klasy. Klasa udostępnia dwie właściwości publiczne logiczną o nazwie `ValidateRequest` i `ValidateReply`. Oba te są oznaczone <xref:System.Configuration.ConfigurationPropertyAttribute>. Ten atrybut stanowi link między właściwościami kodu i atrybutów XML, które będą widoczne na poprzedni element XML w konfiguracji. Klasa ma również właściwość `Schemas` dodatkowo oznaczona za pomocą <xref:System.Configuration.ConfigurationCollectionAttribute> i jest typu `SchemaCollection`, który wchodzi w skład tego przykładu, ale został pominięty z tego dokumentu w celu skrócenia programu. Tej właściwości wraz z kolekcji i klasa elementu kolekcji `SchemaConfigElement` kopię `<schemas>` elementu w poprzednim fragmencie kodu konfiguracji i zezwala na dodawanie kolekcji schematów w zestawie sprawdzania poprawności.  
  
 Zastąpione `CreateBehavior` metody jest przekształcany dane konfiguracyjne obiektu zachowanie po środowisko uruchomieniowe ocenia dane konfiguracji, ponieważ tworzy on klienta lub punktu końcowego.  
  
```  
public class SchemaValidationBehaviorExtensionElement : BehaviorExtensionElement  
{  
    public SchemaValidationBehaviorExtensionElement()  
    {  
    }  
  
    public override Type BehaviorType   
    {   
        get  
        {  
            return typeof(SchemaValidationBehavior);  
        }   
    }  
  
    protected override object CreateBehavior()  
    {  
        XmlSchemaSet schemaSet = new XmlSchemaSet();  
        foreach (SchemaConfigElement schemaCfg in this.Schemas)  
        {  
            Uri baseSchema = new   
                Uri(AppDomain.CurrentDomain.BaseDirectory);  
            string location = new   
                Uri(baseSchema,schemaCfg.Location).ToString();  
            XmlSchema schema =   
                XmlSchema.Read(new XmlTextReader(location), null);  
            schemaSet.Add(schema);  
        }  
     return new   
     SchemaValidationBehavior(schemaSet,ValidateRequest,ValidateReply);  
    }  
  
[ConfigurationProperty("validateRequest",DefaultValue=false,IsRequired=false)]  
public bool ValidateRequest  
{  
    get { return (bool)base["validateRequest"]; }  
    set { base["validateRequest"] = value; }  
}  
  
[ConfigurationProperty("validateReply", DefaultValue = false, IsRequired = false)]  
        public bool ValidateReply  
        {  
            get { return (bool)base["validateReply"]; }  
            set { base["validateReply"] = value; }  
        }  
  
     //Declare the Schema collection property.  
     //Note: the "IsDefaultCollection = false" instructs   
     //.NET Framework to build a nested section of   
     //the kind <Schema> ...</Schema>.  
    [ConfigurationProperty("schemas", IsDefaultCollection = true)]  
    [ConfigurationCollection(typeof(SchemasCollection),  
        AddItemName = "add",  
        ClearItemsName = "clear",  
        RemoveItemName = "remove")]  
    public SchemasCollection Schemas  
    {  
        get  
        {  
            SchemasCollection SchemasCollection =  
            (SchemasCollection)base["schemas"];  
            return SchemasCollection;  
        }  
    }  
}  
```  
  
## <a name="adding-message-inspectors-imperatively"></a>Dodawanie obowiązkowo inspektorzy komunikatów  
 Z wyjątkiem przez atrybuty (które z powodu wymienionych wcześniej nie jest obsługiwany w tym przykładzie) i konfigurację zachowania dość łatwo można dodać do środowiska uruchomieniowego klienta i usługi przy użyciu kodu imperatywnego. W tym przykładzie jest to realizowane w aplikacji klienckiej do testowania Inspektor komunikat klienta. `GenericClient` Klasa pochodzi od <xref:System.ServiceModel.ClientBase%601>, który udostępnia konfigurację punktu końcowego w kodzie użytkownika. Zanim klient jest niejawnie otwarty konfiguracji punktu końcowego można zmienić, na przykład poprzez dodanie zachowania, jak pokazano w poniższym kodzie. Dodawanie zachowania w usłudze odpowiada stopniu technika klienta pokazane tutaj i muszą być wykonywane przed otwarciem hosta usługi.  
  
```  
try  
{  
    Console.WriteLine("*** Call 'Hello' with generic client, with client behavior");  
    GenericClient client = new GenericClient();  
  
    // Configure client programmatically, adding behavior  
    XmlSchema schema = XmlSchema.Read(new StreamReader("messages.xsd"),   
                                                          null);  
    XmlSchemaSet schemaSet = new XmlSchemaSet();  
    schemaSet.Add(schema);  
    client.Endpoint.Behaviors.Add(new   
                SchemaValidationBehavior(schemaSet, true, true));  
  
    Console.WriteLine("--- Sending valid client request:");  
    GenericCallValid(client, helloAction);  
    Console.WriteLine("--- Sending invalid client request:");  
    GenericCallInvalid(client, helloAction);  
  
    client.Close();  
}  
catch (Exception e)  
{  
    DumpException(e);  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageInspectors`  
  
