---
title: Inspektorzy komunikatów
ms.date: 03/30/2017
ms.assetid: 9bd1f305-ad03-4dd7-971f-fa1014b97c9b
ms.openlocfilehash: 705401a182d5d816bc2682f5f21ff09ca95f21c7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144451"
---
# <a name="message-inspectors"></a>Inspektorzy komunikatów
W tym przykładzie pokazano, jak zaimplementować i skonfigurować inspektorów komunikatów klienta i usługi.  
  
 Inspektor komunikatów jest obiektem rozszerzalności, który może być używany w czasie wykonywania klienta modelu usługi i wysyłać środowisko uruchomieniowe programowo lub za pośrednictwem konfiguracji i który może sprawdzać i zmieniać komunikaty po ich odebraniu lub przed wysłaniem.  
  
 W tym przykładzie implementuje podstawowy mechanizm sprawdzania poprawności komunikatów klienta i usługi, który sprawdza poprawność wiadomości przychodzących względem zestawu konfigurowalnych dokumentów schematu XML. Należy zauważyć, że ten przykład nie sprawdza poprawności komunikatów dla każdej operacji. Jest to celowe uproszczenie.  
  
## <a name="message-inspector"></a>Inspektor wiadomości  
 Inspektorzy komunikatów <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> klienta implementują interfejs i <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> inspektorzy komunikatów usługi implementują interfejs. Implementacje można połączyć w jedną klasę, aby utworzyć inspektora wiadomości, który działa dla obu stron. W tym przykładzie implementuje taki inspektor wiadomości połączone. Inspektor jest skonstruowany przekazywania w zestawie schematów, względem których są sprawdzane wiadomości przychodzące i wychodzące i pozwala deweloperowi określić, czy przychodzące lub wychodzące wiadomości są sprawdzane i czy inspektor jest w trybie wysyłki lub klienta, który wpływa na obsługę błędów, jak omówiono w dalszej części tego tematu.  
  
```csharp
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
  
 Każdy inspektor komunikatów usługi (dyspozytora) musi zaimplementować dwie <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> metody <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> i <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>.  
  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>jest wywoływana przez dyspozytora po odebraniu wiadomości, przetwarzane przez stos kanału i przypisane do usługi, ale przed jej deserializacji i wysyłki do operacji. Jeśli wiadomość przychodząca została zaszyfrowana, wiadomość jest już odszyfrowana, gdy dotrze do inspektora wiadomości. Metoda pobiera `request` komunikat przekazany jako parametr odwołania, który umożliwia wiadomości, które mają być kontrolowane, manipulować lub zastępowane w razie potrzeby. Zwracana wartość może być dowolny obiekt i jest używany jako <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> obiekt stanu korelacji, który jest przekazywany, gdy usługa zwraca odpowiedź na bieżącą wiadomość. W tym <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> przykładzie deleguje inspekcję (sprawdzanie poprawności) `ValidateMessageBody` wiadomości do prywatnej, lokalnej metody i zwraca obiekt stanu korelacji bez. Ta metoda gwarantuje, że żadne nieprawidłowe wiadomości przechodzą do usługi.  
  
```csharp  
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
  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>jest wywoływana za każdym razem, gdy odpowiedź jest gotowa do odesłania do klienta lub w przypadku wiadomości jednokierunkowych, gdy wiadomość przychodząca została przetworzona. Dzięki temu rozszerzenia mogą liczyć na to, że będą nazywane symetrycznie, niezależnie od posła do PE. Podobnie <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>jak w , wiadomość jest przekazywana jako parametr odniesienia i może być kontrolowana, modyfikowana lub wymieniana. Sprawdzanie poprawności wiadomości, który jest wykonywany w tym `ValidMessageBody` przykładzie jest ponownie delegowane do metody, ale obsługa błędów sprawdzania poprawności jest nieco inna w tym przypadku.  
  
 Jeśli błąd sprawdzania poprawności występuje `ValidateMessageBody` w usłudze, metoda zgłasza wyjątki <xref:System.ServiceModel.FaultException>pochodne. W <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>programach wyjątki te można umieścić w infrastrukturze modelu usługi, gdzie są automatycznie przekształcane w błędy protokołu SOAP i przekazywane do klienta. W <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> <xref:System.ServiceModel.FaultException> , wyjątki nie mogą być wprowadzane do infrastruktury, ponieważ przekształcenie wyjątków błędów zgłaszanych przez usługę występuje przed inspektorem wiadomości jest wywoływana. W związku z tym następująca implementacja przechwytuje znany `ReplyValidationFault` wyjątek i zastępuje komunikat odpowiedzi z jawnym komunikatem o błędzie. Ta metoda zapewnia, że nie nieprawidłowe komunikaty są zwracane przez implementację usługi.  
  
```csharp  
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
  
 Inspektor komunikatów klienta jest bardzo podobny. Dwie metody, które muszą <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> być <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.AfterReceiveReply%2A> <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>zaimplementowane z są i .  
  
 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>jest wywoływana, gdy wiadomość została złożona przez aplikację kliencką lub przez program formatera operacji. Podobnie jak w inspektorów wiadomości dyspozytora, wiadomość może być po prostu kontrolowane lub całkowicie zastąpione. W tym przykładzie inspektor deleguje `ValidateMessageBody` do tej samej lokalnej metody pomocnika, która jest również używana dla inspektorów komunikatów wysyłki.  
  
 Różnica behawioralna między weryfikacji klienta i usługi (jak określono w konstruktorze) jest, że sprawdzanie poprawności klienta zgłasza wyjątki lokalne, które są wprowadzane do kodu użytkownika, ponieważ występują lokalnie, a nie z powodu błędu usługi. Ogólnie rzecz biorąc, regułą jest to, że inspektorzy dyspozytora usługi zgłaszają błędy i że inspektorzy klienta zgłaszają wyjątki.  
  
 Ta <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> implementacja zapewnia, że żadne nieprawidłowe komunikaty nie są wysyłane do usługi.  
  
```csharp  
object IClientMessageInspector.BeforeSendRequest(ref System.ServiceModel.Channels.Message request, System.ServiceModel.IClientChannel channel)  
{  
    if (validateRequest)  
    {  
        ValidateMessageBody(ref request, true);  
    }  
    return null;  
}  
```  
  
 Implementacja `AfterReceiveReply` zapewnia, że żadne nieprawidłowe komunikaty odebrane z usługi są przekazywane do kodu użytkownika klienta.  
  
```csharp  
void IClientMessageInspector.AfterReceiveReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
{  
    if (validateReply)  
    {  
        ValidateMessageBody(ref reply, false);  
    }  
}  
```  
  
 Sercem tego inspektora poszczególnych `ValidateMessageBody` komunikatów jest metoda. Aby wykonać swoją pracę, zawija sprawdzanie poprawności <xref:System.Xml.XmlReader> wokół poddrzewa zawartości treści treści przekazywanych wiadomości. Czytnik jest wypełniany zestaw schematów, które inspektor wiadomości posiada i wywołania zwrotnego `InspectionValidationHandler` sprawdzania poprawności jest ustawiona na delegata odnoszące się do tego, który jest zdefiniowany obok tej metody. Aby wykonać sprawdzanie poprawności, wiadomość jest następnie odczytywana i <xref:System.Xml.XmlDictionaryWriter>buforowana w kopii strumieniowej pamięci . Jeśli błąd sprawdzania poprawności lub ostrzeżenie występuje w procesie, wywoływana jest metoda wywołania zwrotnego.  
  
 Jeśli nie wystąpi żaden błąd, zostanie skonstruowany nowy komunikat, który kopiuje właściwości i nagłówki z oryginalnej wiadomości i używa <xref:System.Xml.XmlDictionaryReader> teraz zweryfikowanego zestawu informacyjnego w strumieniu pamięci, który jest zawijany przez komunikat zastępczy i dodany do wiadomości zastępczej.  
  
```csharp  
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
  
 Metoda `InspectionValidationHandler` jest wywoływana przez <xref:System.Xml.XmlReader> sprawdzanie poprawności, gdy wystąpi błąd sprawdzania poprawności schematu lub ostrzeżenie. Poniższa implementacja działa tylko z błędami i ignoruje wszystkie ostrzeżenia.  
  
 W pierwszej sprawie może się wydawać, <xref:System.Xml.XmlReader> że możliwe jest wstrzyknięcie sprawdzania poprawności do wiadomości za pomocą inspektora wiadomości i umożliwienie sprawdzania poprawności podczas przetwarzania wiadomości i bez buforowania wiadomości. Oznacza to jednak, że to wywołanie zwrotne zgłasza wyjątki sprawdzania poprawności gdzieś w infrastrukturze modelu usługi lub kod użytkownika, jak nieprawidłowe węzły XML są wykrywane, co powoduje nieprzewidywalne zachowanie. Podejście buforowania chroni kod użytkownika przed nieprawidłowymi wiadomościami, całkowicie.  
  
 Jak wcześniej wspomniano, wyjątki generowane przez program obsługi różnią się między klientem a usługą. W usłudze wyjątki są uzyskiwane z <xref:System.ServiceModel.FaultException>, na kliencie wyjątki są regularne wyjątki niestandardowe.  
  
```csharp  
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
 Inspektorzy komunikatów są rozszerzenia do środowiska wykonawczego klienta lub środowiska wykonawczego wysyłki. Takie rozszerzenia są konfigurowane przy użyciu *zachowań*. Zachowanie jest klasą, która zmienia zachowanie środowiska wykonawczego modelu usługi, zmieniając domyślną konfigurację lub dodając do niego rozszerzenia (takie jak inspektorzy wiadomości).  
  
 Następująca `SchemaValidationBehavior` klasa jest zachowanie używane do dodawania inspektora wiadomości tego przykładu do środowiska uruchomieniowego klienta lub wysyłki. Wdrożenie jest raczej podstawowe w obu przypadkach. W <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyClientBehavior%2A> <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyDispatchBehavior%2A>i , Inspektor wiadomości jest <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> tworzony i dodawany do kolekcji odpowiedniego środowiska wykonawczego.  
  
```csharp
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
> To określone zachowanie nie jest dwukrotnie jako atrybut i dlatego nie można dodać deklaratywnie do typu umowy typu usługi. Jest to decyzja w projekcie, ponieważ kolekcji schematu nie można załadować w deklaracji atrybutu i odwoływanie się do dodatkowej lokalizacji konfiguracji (na przykład do ustawień aplikacji) w tym atrybucie oznacza utworzenie elementu konfiguracji, który nie jest zgodna z pozostałą częścią konfiguracji modelu usługi. W związku z tym to zachowanie można dodać tylko za pomocą kodu i za pośrednictwem rozszerzenia konfiguracji modelu usługi.  
  
## <a name="adding-the-message-inspector-through-configuration"></a>Dodawanie Inspektora wiadomości za pomocą konfiguracji  
 Aby skonfigurować zachowanie niestandardowe w punkcie końcowym w pliku konfiguracji aplikacji, model usługi wymaga implementerów do <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>utworzenia elementu *rozszerzenia* konfiguracji reprezentowanego przez klasę pochodzącą z programu . To rozszerzenie należy następnie dodać do sekcji konfiguracji modelu usługi dla rozszerzeń, jak pokazano dla następującego rozszerzenia omówione w tej sekcji.  
  
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
  
 Rozszerzenia można dodać w pliku konfiguracyjnym aplikacji lub ASP.NET, który jest najczęstszym wyborem lub w pliku konfiguracji komputera.  
  
 Po dodaniu rozszerzenia do zakresu konfiguracji, zachowanie można dodać do konfiguracji zachowania, jak pokazano w poniższym kodzie. Zachowania konfiguracje są elementy wielokrotnegoużytnia, które mogą być stosowane do wielu punktów końcowych zgodnie z wymaganiami. Ponieważ określone zachowanie, które ma <xref:System.ServiceModel.Description.IEndpointBehavior>być skonfigurowane w tym miejscu implementuje, jest prawidłowe tylko w odpowiedniej sekcji konfiguracji w pliku konfiguracyjnym.  
  
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
  
 Element, `<schemaValidator>` który konfiguruje inspektora `SchemaValidationBehaviorExtensionElement` wiadomości jest wspierany przez klasę. Klasa udostępnia dwie logiczne właściwości `ValidateRequest` publiczne `ValidateReply`o nazwie i . Oba te są oznaczone <xref:System.Configuration.ConfigurationPropertyAttribute>symbolem . Ten atrybut stanowi łącze między właściwościami kodu a atrybutami XML, które można zobaczyć w poprzednim elemencie konfiguracji XML. Klasa ma również `Schemas` właściwość, która jest <xref:System.Configuration.ConfigurationCollectionAttribute> dodatkowo oznaczona `SchemaCollection`i jest typu , który jest również częścią tego przykładu, ale pominięte w tym dokumencie dla zwięzłości. Ta właściwość wraz z kolekcji `SchemaConfigElement` i `<schemas>` klasy elementu kolekcji wspiera element w poprzednim fragmentze konfiguracji i umożliwia dodawanie kolekcji schematów do zestawu sprawdzania poprawności.  
  
 Zastąpiona `CreateBehavior` metoda zamienia dane konfiguracji w obiekt zachowania, gdy środowisko wykonawcze ocenia dane konfiguracji podczas tworzenia klienta lub punktu końcowego.  
  
```csharp
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
  
## <a name="adding-message-inspectors-imperatively"></a>Trwa dodawania inspektorów wiadomości  
 Z wyjątkiem za pomocą atrybutów (który nie jest obsługiwany w tym przykładzie z powodu cytowane wcześniej) i konfiguracji, zachowania można dość łatwo dodać do środowiska uruchomieniowego klienta i usługi przy użyciu kodu imperatywu. W tym przykładzie jest to wykonywane w aplikacji klienckiej, aby przetestować inspektora komunikatów klienta. Klasa `GenericClient` jest pochodną <xref:System.ServiceModel.ClientBase%601>, który udostępnia konfiguracji punktu końcowego do kodu użytkownika. Przed otwarciem klienta niejawnie można zmienić konfigurację punktu końcowego, na przykład dodając zachowania, jak pokazano w poniższym kodzie. Dodawanie zachowania w usłudze jest w dużej mierze równoważne techniki klienta pokazano w tym miejscu i muszą być wykonywane przed otwarciem hosta usługi.  
  
```csharp  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby utworzyć rozwiązanie, postępuj zgodnie z instrukcjami w [tworzeniu przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageInspectors`  
