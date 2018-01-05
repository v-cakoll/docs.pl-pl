---
title: "Inspektorzy komunikatów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9bd1f305-ad03-4dd7-971f-fa1014b97c9b
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7ed4f31e004ddeb69a29568b3892ab7379715457
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="message-inspectors"></a>Inspektorzy komunikatów
W tym przykładzie pokazano, jak wdrożyć i skonfigurować klienta i usługi inspektorzy komunikatów.  
  
 Inspektor wiadomości jest obiektem rozszerzalności, który może być używana w modelu usługi klienta w czasie wykonywania i środowiska uruchomieniowego wysyłania programowo lub za pomocą konfiguracji i które można sprawdzić i zmienić wiadomości po otrzymaniu ich lub przed ich wysłaniem.  
  
 W tym przykładzie implementuje podstawowe klienta i usługi komunikatu sprawdzania poprawności mechanizmu sprawdzania wiadomości przychodzących z zestawem dokumentach schematów XML można skonfigurować. Należy pamiętać, że w tym przykładzie nie można zweryfikować wiadomości dla każdej operacji. Jest to zamierzone uproszczenia.  
  
## <a name="message-inspector"></a>Inspektor wiadomości  
 Implementowanie inspektorzy komunikatów klienta <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> interfejsu i usługa implementuje inspektorzy komunikatów <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> interfejsu. Implementacje mogą być połączone w jedną klasę do utworzenia inspektora komunikat, który działa w przypadku obu stron. W tym przykładzie implementuje inspektora Scalonej wiadomości. Inspektor jest tworzony przekazywanie w zestawie schematów, które są weryfikowane wiadomości przychodzących i wychodzących i umożliwia deweloperowi określić, czy są weryfikowane wiadomości przychodzących lub wychodzących i czy kontroler jest w trybie klienta lub wysyłania, która Obsługa błędów dotyczy, zgodnie z opisem w dalszej części tego tematu.  
  
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
  
 Wszelkie inspektora wiadomości usługi (dyspozytora) musi implementować dwa <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> metody <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> i <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>.  
  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>jest wywoływany przez Dyspozytor wiadomość została otrzymał, przetwarzane przez stos kanału i przypisane do usługi, ale przed deserializacji i wysyłane do operacji. Jeśli komunikat przychodzący został zaszyfrowany, komunikat już jest odszyfrowywany po osiągnięciu inspektora wiadomości. Pobiera metodę `request` komunikat przekazany jako parametr odwołania, dzięki czemu komunikat, aby sprawdził, manipulować lub zastąpione zgodnie z potrzebami. Zwracana wartość może być dowolnym obiektem i jest używany jako obiekt stanu korelacji, który jest przekazywany do <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> gdy usługa zwraca odpowiedź do bieżącej wiadomości. W tym przykładzie <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> deleguje inspekcji (Walidacja) wiadomości prywatne i lokalne metodę `ValidateMessageBody` i zwraca obiekt stanu nie korelacji. Ta metoda gwarantuje, że żadne komunikaty nieprawidłowy przekazać do usługi.  
  
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
  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>jest wywoływane zawsze, gdy odpowiedź jest gotowa do wysłania do klienta lub w przypadku jednokierunkowe komunikaty, po przetworzeniu komunikatu przychodzącego. Dzięki temu count wywoływana symetrycznie, niezależnie od MEP rozszerzeń. Jak <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, wiadomość jest przekazywana jako parametr odwołania i może sprawdzenia, zmodyfikowane lub zastąpione. Sprawdzanie poprawności wiadomości, które jest przeprowadzane w tym przykładzie jest ponownie delegowana do `ValidMessageBody` metody, ale obsługa błędów sprawdzania poprawności różni się nieco w takim przypadku.  
  
 Jeśli wystąpi błąd sprawdzania poprawności w usłudze `ValidateMessageBody` metoda zgłasza <xref:System.ServiceModel.FaultException>-pochodnych wyjątków. W <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, wyjątki te mogą być przełączane do modelu usługi infrastruktury, gdzie są one automatycznie przekształcone w błędach SOAP, a przekazany do klienta. W <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A>, <xref:System.ServiceModel.FaultException> wyjątki nie mogą być umieszczone w infrastrukturę, ponieważ transformacja wyjątków błędów zgłaszanych przez usługę występuje przed wywołaniem inspektora wiadomości. W związku z tym implementacji następujących przechwytuje znane `ReplyValidationFault` wyjątku i zamienia komunikat odpowiedzi z komunikat o błędzie jawna. Ta metoda gwarantuje, że żadne komunikaty nieprawidłowy są zwracane przez implementacji usługi.  
  
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
  
 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>wywoływane, gdy wiadomość została składane, przez aplikację klienta lub przez program formatujący operacji. Zgodnie z dyspozytora inspektorzy komunikatów, może po prostu komunikat sprawdzenia lub całkowicie zastąpiona. W tym przykładzie Inspektor deleguje do tej samej lokalnej `ValidateMessageBody` metody pomocniczej, która służy do wysyłania inspektorzy komunikatów.  
  
 Behawioralnej różnica między klientem a usługą sprawdzania poprawności (jak określono w konstruktorze) jest, że sprawdzanie poprawności klienta zgłasza wyjątki lokalne, które są umieszczane w kodzie użytkownika, ponieważ występują lokalnie, a nie z powodu błędu usługi. Ogólnie rzecz biorąc jest zasada, czy usługa dyspozytora inspektorzy zgłoszenie błędów i że inspektorzy klienta zgłaszają wyjątki.  
  
 To <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> implementacja zapewnia, że nie nieprawidłowy komunikaty są wysyłane do usługi.  
  
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
  
 `AfterReceiveReply` Implementacja zapewnia, że nie komunikaty nieprawidłowy otrzymał z usługi są przekazywane do kodu użytkownika klienta.  
  
```  
void IClientMessageInspector.AfterReceiveReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
{  
    if (validateReply)  
    {  
        ValidateMessageBody(ref reply, false);  
    }  
}  
```  
  
 Ten inspektor danego komunikatu to `ValidateMessageBody` metody. Aby wykonać swoją pracę, jest zawijany, sprawdzanie poprawności <xref:System.Xml.XmlReader> wokół zawartości drzewa podrzędnego treści komunikatu przekazany. Czytnik jest wypełniane przy użyciu zestawu schematów, które przechowuje inspektora wiadomości i wywołanie zwrotne weryfikacji ma ustawioną wartość delegata odwołujących się do `InspectionValidationHandler` zdefiniowanego równolegle z tej metody. Przeprowadzenie weryfikacji wiadomość jest następnie odczytu i buforowane w pamięci kopia strumienia <xref:System.Xml.XmlDictionaryWriter>. Jeśli wystąpi błąd sprawdzania poprawności lub ostrzeżenie w procesie, wywoływana jest metoda wywołania zwrotnego.  
  
 Jeśli nie występują błędy, nowy komunikat jest tworzony kopiuje właściwości i nagłówków z oryginalnej wiadomości, który używa typu infoset zweryfikowane teraz w strumieniu pamięci, która opakowane w usłudze <xref:System.Xml.XmlDictionaryReader> i dodane do wymiany wiadomości.  
  
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
  
 `InspectionValidationHandler` Metoda jest wywoływana przez sprawdzanie poprawności <xref:System.Xml.XmlReader> zawsze, gdy wystąpi błąd sprawdzania poprawności schematu lub ostrzeżenie. Następująca implementacja działa tylko z błędami i ignoruje wszystkie ostrzeżenia.  
  
 Na pierwszym zagadnieniem może wydawać się możliwe do dodania, sprawdzanie poprawności <xref:System.Xml.XmlReader> do wiadomości z Inspektora wiadomości i umożliwiają sprawdzanie poprawności stanie komunikat jest przetwarzany i bez buforowania wiadomości. Jednak oznacza, że to wywołanie zwrotne zgłasza wyjątki poprawności gdzieś w usłudze modelu infrastruktury lub kod użytkownika jak wykryto nieprawidłowy węzłów XML, spowodować nieprzewidywalne zachowanie. Podejście buforowania całkowicie chroni kod użytkownika z nieprawidłową wiadomości.  
  
 Jak już wspomniano wyjątki generowane przez program obsługi różnią się między klientem a usługą. W usłudze, wyjątki są uzyskiwane z <xref:System.ServiceModel.FaultException>, na kliencie wyjątki są regularnie niestandardowymi wyjątkami.  
  
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
 Inspektorzy komunikatów są rozszerzenia do środowiska uruchomieniowego klienta lub środowisko wykonawcze wysyłce. Takie rozszerzenia są skonfigurowane przy użyciu *zachowania*. Zachowanie jest klasa, która zmienia zachowanie środowiska uruchomieniowego modelu usługi przez zmianę konfiguracji domyślnej lub dodanie rozszerzenia (na przykład inspektorzy komunikatów).  
  
 Następujące `SchemaValidationBehavior` klasy jest zachowanie umożliwia Dodaj ten przykład inspektora wiadomości do klienta lub wysyłania środowiska wykonawczego. Implementacja jest raczej podstawowe w obu przypadkach. W <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyClientBehavior%2A> i <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyDispatchBehavior%2A>, inspektora wiadomości jest tworzony i dodawany do <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> kolekcji odpowiednich środowiska uruchomieniowego.  
  
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
>  To zachowanie określonego nie dwukrotnie jako atrybut i dlatego nie można dodać deklaratywnie na typ kontraktu usługi typu. Jest to wykonana, ponieważ nie można załadować kolekcji schematów w deklaracji atrybutu i odwołujące się do lokalizacji dodatkowej konfiguracji (na przykład w celu ustawienia aplikacji), w tym atrybucie oznacza tworzenia elementu konfiguracji, który decyzji projektowych nie jest zgodne z pozostałą częścią konfiguracji modelu usług. W związku z tym to zachowanie można dodać tylko imperatively za pośrednictwem kodu oraz rozszerzenie konfiguracji modelu usług.  
  
## <a name="adding-the-message-inspector-through-configuration"></a>Dodawanie inspektora wiadomości przy użyciu konfiguracji  
 W przypadku konfigurowania niestandardowych zachowania punktu końcowego w pliku konfiguracyjnym aplikacji, modelu usługi wymaga implementacji utworzyć konfigurację *elementu rozszerzenia* reprezentowany przez klasę pochodną <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>. To rozszerzenie należy następnie dodać do sekcji konfiguracji modelu usług dla rozszerzeń, jak pokazano na następujące rozszerzenie omówione w tej sekcji.  
  
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
  
 Rozszerzenia mogą być dodawane w aplikacji lub plik konfiguracyjny programu ASP.NET, który jest najbardziej typowych wybór, lub w pliku konfiguracji komputera.  
  
 Rozszerzenie zostanie dodany do zakresu konfiguracji, to zachowanie można dodać do konfiguracji zachowania pokazany w następującym kodem. Zachowanie konfiguracje są elementy wielokrotnego użytku, które można zastosować do wielu punktów końcowych zgodnie z potrzebami. Ponieważ określone zachowanie być skonfigurowana tutaj implementuje <xref:System.ServiceModel.Description.IEndpointBehavior>, jest on prawidłowy tylko w sekcji odpowiednich konfiguracji w pliku konfiguracji.  
  
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
  
 `<schemaValidator>` Element, który konfiguruje inspektora wiadomości nie jest obsługiwana przez `SchemaValidationBehaviorExtensionElement` klasy. Klasa udostępnia dwa logiczną właściwości publicznej o nazwie `ValidateRequest` i `ValidateReply`. Oba te są oznaczone ikoną z <xref:System.Configuration.ConfigurationPropertyAttribute>. Ten atrybut stanowi połączenie między właściwości kodu i atrybutów XML, które będą widoczne na poprzedni element XML w konfiguracji. Klasa ma także właściwością `Schemas` który również jest oznaczony atrybutem <xref:System.Configuration.ConfigurationCollectionAttribute> i jest typu `SchemaCollection`, która jest również częścią tego przykładu, ale został pominięty z tego dokumentu do skrócenia. Tej właściwości wraz z kolekcji i klasa elementu kolekcji `SchemaConfigElement` kopie `<schemas>` elementu w poprzednim fragment konfiguracji i umożliwia dodawanie kolekcji schematów w zestawie sprawdzania poprawności.  
  
 Zastąpione `CreateBehavior` — metoda powoduje dane konfiguracyjne do obiektu zachowania podczas środowiska uruchomieniowego ocenia dane konfiguracji, jak zbudował klienta lub punktu końcowego.  
  
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
  
## <a name="adding-message-inspectors-imperatively"></a>Dodawanie Imperatively inspektorzy komunikatów  
 Z wyjątkiem za pomocą atrybutów (które z powodu odnosiło się do wcześniej nie jest obsługiwana w tym przykładzie) i konfigurację, można dodać do obsługi klienta i usługi, przy użyciu kodu imperatywnych dość łatwe zachowania. W tym przykładzie jest to realizowane w aplikacji klienckiej, aby przetestować inspektora komunikat klienta. `GenericClient` Jest pochodną klasy <xref:System.ServiceModel.ClientBase%601>, który udostępnia konfigurację punktu końcowego do kodu użytkownika. Przed otwarciem niejawnie klienta konfiguracji punktu końcowego można zmienić, na przykład przez dodanie zachowania, jak pokazano w poniższym kodzie. Dodanie zachowania usługi jest odpowiednikiem przede wszystkim technika klienta pokazane i musi zostać wykonana przed otwarciem hosta usługi.  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageInspectors`  
  
## <a name="see-also"></a>Zobacz też
