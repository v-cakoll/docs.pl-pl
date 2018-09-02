---
title: Inspektorzy komunikatów
ms.date: 03/30/2017
ms.assetid: 9bd1f305-ad03-4dd7-971f-fa1014b97c9b
ms.openlocfilehash: 253be4d13649d4f6394aad1bb002f5cd555d8af2
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43385847"
---
# <a name="message-inspectors"></a><span data-ttu-id="5f17d-102">Inspektorzy komunikatów</span><span class="sxs-lookup"><span data-stu-id="5f17d-102">Message Inspectors</span></span>
<span data-ttu-id="5f17d-103">W tym przykładzie pokazano, jak zaimplementować i skonfigurować klienta i usługi inspektorzy komunikatów.</span><span class="sxs-lookup"><span data-stu-id="5f17d-103">This sample demonstrates how to implement and configure client and service message inspectors.</span></span>  
  
 <span data-ttu-id="5f17d-104">Inspektor wiadomość znajduje się obiekt rozszerzalności, który może służyć w modelu usług klienta w środowisku uruchomieniowym i wysyłania środowiska uruchomieniowego programowo lub za pośrednictwem konfiguracją oraz że można sprawdzić i zmienić wiadomości po odebraniu, lub przed ich wysłaniem.</span><span class="sxs-lookup"><span data-stu-id="5f17d-104">A message inspector is an extensibility object that can be used in the service model's client runtime and dispatch runtime programmatically or through configuration and that can inspect and alter messages after they are received or before they are sent.</span></span>  
  
 <span data-ttu-id="5f17d-105">W tym przykładzie implementuje podstawowe klienta i mechanizmu sprawdzania poprawności wiadomości usługi, która weryfikuje komunikaty przychodzące z zestawem dokumentów schematu XML można skonfigurować.</span><span class="sxs-lookup"><span data-stu-id="5f17d-105">This sample implements a basic client and service message validation mechanism that validates incoming messages against a set of configurable XML Schema documents.</span></span> <span data-ttu-id="5f17d-106">Należy pamiętać, że w tym przykładzie nie można zweryfikować wiadomości dla każdej operacji.</span><span class="sxs-lookup"><span data-stu-id="5f17d-106">Note that this sample does not validate messages for each operation.</span></span> <span data-ttu-id="5f17d-107">Jest to zamierzone uproszczenia.</span><span class="sxs-lookup"><span data-stu-id="5f17d-107">This is an intentional simplification.</span></span>  
  
## <a name="message-inspector"></a><span data-ttu-id="5f17d-108">Inspektor wiadomości</span><span class="sxs-lookup"><span data-stu-id="5f17d-108">Message Inspector</span></span>  
 <span data-ttu-id="5f17d-109">Implementowanie inspektorzy komunikatów klienta <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> interfejsu i usługa Implementowanie inspektorzy komunikatów <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="5f17d-109">Client message inspectors implement the <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> interface and service message inspectors implement the <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> interface.</span></span> <span data-ttu-id="5f17d-110">Implementacje mogą być połączone w jedną klasę w celu utworzenia Inspektor komunikat, który działa w przypadku obu stronach.</span><span class="sxs-lookup"><span data-stu-id="5f17d-110">The implementations can be combined into a single class to form a message inspector that works for both sides.</span></span> <span data-ttu-id="5f17d-111">W tym przykładzie implementuje Inspektor połączone wiadomości.</span><span class="sxs-lookup"><span data-stu-id="5f17d-111">This sample implements such a combined message inspector.</span></span> <span data-ttu-id="5f17d-112">Inspektor jest konstruowany, przekazując w zestawie schematów, wobec których wiadomości przychodzące i wychodzące są weryfikowane i umożliwia deweloperom określić, czy komunikaty przychodzące lub wychodzące są prawidłowe i czy inspektor znajduje się w trybie klienta lub wysyłanie który wpływa na obsługi błędów, zgodnie z opisem w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="5f17d-112">The inspector is constructed passing in a set of schemas against which incoming and outgoing messages are validated and allows the developer to specify whether incoming or outgoing messages are validated and whether the inspector is in dispatch or client mode, which affects the error handling as discussed later in this topic.</span></span>  
  
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
  
 <span data-ttu-id="5f17d-113">Wszelkie Inspektor wiadomości usługi (dyspozytora) musi implementować dwa <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> metody <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> i <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>.</span><span class="sxs-lookup"><span data-stu-id="5f17d-113">Any service (dispatcher) message inspector must implement the two <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> methods <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> and <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>.</span></span>  
  
 <span data-ttu-id="5f17d-114"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> jest wywoływane przez Dyspozytor wiadomości odebrane, przetworzeniu przez stos kanału i przypisane do usługi, ale przed deserializacji i wysyłane do operacji.</span><span class="sxs-lookup"><span data-stu-id="5f17d-114"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> is invoked by the dispatcher when a message has been received, processed by the channel stack and assigned to a service, but before it is deserialized and dispatched to an operation.</span></span> <span data-ttu-id="5f17d-115">Jeśli przychodzący komunikat został zaszyfrowany, komunikat już są odszyfrowywane, po osiągnięciu Inspektor wiadomości.</span><span class="sxs-lookup"><span data-stu-id="5f17d-115">If the incoming message was encrypted, the message is already decrypted when it reaches the message inspector.</span></span> <span data-ttu-id="5f17d-116">Metoda pobiera `request` komunikat przekazany jako parametr przekazany przez odwołanie, co pozwala komunikat, aby sprawdził, modyfikować lub zastąpić zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="5f17d-116">The method gets the `request` message passed as a reference parameter, which allows the message to be inspected, manipulated or replaced as required.</span></span> <span data-ttu-id="5f17d-117">Zwracana wartość może być dowolny obiekt i jest używany jako obiekt stanu korelacji, który jest przekazywany do <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> kiedy usługa zwraca odpowiedź do bieżącej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="5f17d-117">The return value can be any object and is used as a correlation state object that is passed to <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> when the service returns a reply to the current message.</span></span> <span data-ttu-id="5f17d-118">W tym przykładzie <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> deleguje inspekcji (zatwierdzenie) komunikatu do metody prywatnej, lokalny `ValidateMessageBody` i zwraca obiekt stanu nie korelacji.</span><span class="sxs-lookup"><span data-stu-id="5f17d-118">In this sample, <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> delegates the inspection (validation) of the message to the private, local method `ValidateMessageBody` and returns no correlation state object.</span></span> <span data-ttu-id="5f17d-119">Ta metoda zapewnia, że żadne komunikaty nieprawidłowy przekazywać do usługi.</span><span class="sxs-lookup"><span data-stu-id="5f17d-119">This method ensures that no invalid messages pass into the service.</span></span>  
  
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
  
 <span data-ttu-id="5f17d-120"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29> jest wywoływane zawsze wtedy, gdy odpowiedź jest gotowe do wysłania do klienta lub w przypadku jednokierunkowe komunikaty, po przetworzeniu komunikatu przychodzącego.</span><span class="sxs-lookup"><span data-stu-id="5f17d-120"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29> is invoked whenever a reply is ready to be sent back to a client, or in the case of one-way messages, when the incoming message has been processed.</span></span> <span data-ttu-id="5f17d-121">Dzięki temu możesz liczyć na są nazywane symetrycznie, niezależnie od tego, MEP rozszerzeń.</span><span class="sxs-lookup"><span data-stu-id="5f17d-121">This allows extensions to count on being called symmetrically, regardless of MEP.</span></span> <span data-ttu-id="5f17d-122">Podobnie jak w przypadku <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, komunikat jest przekazywany jako parametr przekazany przez odwołanie i można sprawdził, zmodyfikowane lub zastąpione.</span><span class="sxs-lookup"><span data-stu-id="5f17d-122">As with <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, the message is passed as a reference parameter and can be inspected, modified or replaced.</span></span> <span data-ttu-id="5f17d-123">Sprawdzanie poprawności wiadomości, która jest wykonywana w tym przykładzie jest ponownie delegowane do `ValidMessageBody` metody, ale obsługi błędów sprawdzania poprawności różni się nieco w tym przypadku.</span><span class="sxs-lookup"><span data-stu-id="5f17d-123">The validation of the message that is performed in this sample is again delegated to the `ValidMessageBody` method, but the handling of validation errors is slightly different in this case.</span></span>  
  
 <span data-ttu-id="5f17d-124">Jeśli wystąpi błąd sprawdzania poprawności w usłudze `ValidateMessageBody` metoda zgłasza wyjątek <xref:System.ServiceModel.FaultException>-pochodnych wyjątków.</span><span class="sxs-lookup"><span data-stu-id="5f17d-124">If a validation error occurs on the service, the `ValidateMessageBody` method throws <xref:System.ServiceModel.FaultException>-derived exceptions.</span></span> <span data-ttu-id="5f17d-125">W <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, tych wyjątków można umieścić w modelu usługi infrastruktury, gdzie one są przekształcone w błędach SOAP i automatycznie przekazywane do klienta.</span><span class="sxs-lookup"><span data-stu-id="5f17d-125">In <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, these exceptions can be put into the service model infrastructure where they are automatically transformed into SOAP faults and relayed to the client.</span></span> <span data-ttu-id="5f17d-126">W <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A>, <xref:System.ServiceModel.FaultException> wyjątki nie mogą być umieszczone w infrastrukturę, ponieważ przekształcenie wyjątków błędów zgłaszanych przez usługę odbywa się przed wywołaniem Inspektor wiadomości.</span><span class="sxs-lookup"><span data-stu-id="5f17d-126">In <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A>, <xref:System.ServiceModel.FaultException> exceptions must not be put into the infrastructure, because the transformation of fault exceptions thrown by the service occurs before the message inspector is called.</span></span> <span data-ttu-id="5f17d-127">W związku z tym następującą implementacją przechwytuje znane `ReplyValidationFault` wyjątków i zastępuje odpowiedź komunikatu o komunikat o błędzie jawnego.</span><span class="sxs-lookup"><span data-stu-id="5f17d-127">Therefore the following implementation catches the known `ReplyValidationFault` exception and replaces the reply message with an explicit fault message.</span></span> <span data-ttu-id="5f17d-128">Ta metoda zapewnia, że żadne komunikaty nieprawidłowy są zwracane przez implementacji usługi.</span><span class="sxs-lookup"><span data-stu-id="5f17d-128">This method ensures that no invalid messages are returned by the service implementation.</span></span>  
  
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
  
 <span data-ttu-id="5f17d-129">Inspektor komunikat klienta jest bardzo podobne.</span><span class="sxs-lookup"><span data-stu-id="5f17d-129">The client message inspector is very similar.</span></span> <span data-ttu-id="5f17d-130">Te dwie metody, które muszą zostać zaimplementowane z <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> są <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.AfterReceiveReply%2A> i <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>.</span><span class="sxs-lookup"><span data-stu-id="5f17d-130">The two methods that must be implemented from <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> are <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.AfterReceiveReply%2A> and <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>.</span></span>  
  
 <span data-ttu-id="5f17d-131"><xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> jest wywoływane, gdy komunikat został złożony, przez aplikację klienta lub przez element formatujący operacji.</span><span class="sxs-lookup"><span data-stu-id="5f17d-131"><xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> is invoked when the message has been composed either by the client application or by the operation formatter.</span></span> <span data-ttu-id="5f17d-132">Zgodnie ze wysyłający inspektorzy komunikatów, po prostu komunikat sprawdzenia lub całkowicie zastąpiony.</span><span class="sxs-lookup"><span data-stu-id="5f17d-132">As with the dispatcher message inspectors, the message can just be inspected or entirely replaced.</span></span> <span data-ttu-id="5f17d-133">W tym przykładzie Inspektor deleguje odpowiednie uprawnienia do tej samej lokalnej `ValidateMessageBody` metody pomocnika, która jest również używany do wysyłania inspektorzy komunikatów.</span><span class="sxs-lookup"><span data-stu-id="5f17d-133">In this sample, the inspector delegates to the same local `ValidateMessageBody` helper method that is also used for the dispatch message inspectors.</span></span>  
  
 <span data-ttu-id="5f17d-134">Zachowania różnica między klientem a usługą sprawdzania poprawności (jak określono w konstruktorze) polega na tym, czy sprawdzanie poprawności klienta zgłasza wyjątki lokalne, które są umieszczane w kodzie użytkownika, ponieważ występują one lokalnie, a nie z powodu błędu usługi.</span><span class="sxs-lookup"><span data-stu-id="5f17d-134">The behavioral difference between the client and service validation (as specified in the constructor) is that the client validation throws local exceptions that are put into the user code because they occur locally and not because of a service failure.</span></span> <span data-ttu-id="5f17d-135">Ogólnie rzecz biorąc jest zasada, że usługa dyspozytora inspektorzy zgłasza błędy i zgłaszają wyjątki, że inspektorzy klienta.</span><span class="sxs-lookup"><span data-stu-id="5f17d-135">Generally, the rule is that service dispatcher inspectors throw faults and that client inspectors throw exceptions.</span></span>  
  
 <span data-ttu-id="5f17d-136">To <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> implementacji gwarantuje, że nie nieprawidłowy komunikaty są wysyłane do usługi.</span><span class="sxs-lookup"><span data-stu-id="5f17d-136">This <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> implementation ensures that no invalid messages are sent to the service.</span></span>  
  
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
  
 <span data-ttu-id="5f17d-137">`AfterReceiveReply` Implementacji gwarantuje, że brak nieprawidłowy komunikatów odebranych z usługi są przekazywane do kodu użytkownika klienta.</span><span class="sxs-lookup"><span data-stu-id="5f17d-137">The `AfterReceiveReply` implementation ensures that no invalid messages received from the service are relayed to the client user code.</span></span>  
  
```  
void IClientMessageInspector.AfterReceiveReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
{  
    if (validateReply)  
    {  
        ValidateMessageBody(ref reply, false);  
    }  
}  
```  
  
 <span data-ttu-id="5f17d-138">To serce Inspektor tego konkretnego komunikatu `ValidateMessageBody` metody.</span><span class="sxs-lookup"><span data-stu-id="5f17d-138">The heart of this particular message inspector is the `ValidateMessageBody` method.</span></span> <span data-ttu-id="5f17d-139">Aby wykonać swoją pracę, jest zawijany, sprawdzanie poprawności <xref:System.Xml.XmlReader> wokół zawartości drzewo podrzędne treści przekazanych komunikatów.</span><span class="sxs-lookup"><span data-stu-id="5f17d-139">To perform its work, it wraps a validating <xref:System.Xml.XmlReader> around the body content sub-tree of the passed message.</span></span> <span data-ttu-id="5f17d-140">Czytnik jest wypełniana przy użyciu zestawu schematów, które przechowuje Inspektor wiadomości i wywołanie zwrotne weryfikacji jest ustawiona na obiekt delegowany odwołujące się do `InspectionValidationHandler` zdefiniowanego wraz z tej metody.</span><span class="sxs-lookup"><span data-stu-id="5f17d-140">The reader is populated with the set of schemas that the message inspector holds and the validation callback is set to a delegate referring to the `InspectionValidationHandler` that is defined alongside this method.</span></span> <span data-ttu-id="5f17d-141">Aby wykonać sprawdzanie poprawności, komunikat jest następnie odczytu i buforowane w pamięci z kopią zapasową w usłudze stream <xref:System.Xml.XmlDictionaryWriter>.</span><span class="sxs-lookup"><span data-stu-id="5f17d-141">To perform the validation, the message is then read and spooled into a memory stream-backed <xref:System.Xml.XmlDictionaryWriter>.</span></span> <span data-ttu-id="5f17d-142">Jeśli wystąpi błąd sprawdzania poprawności lub ostrzeżenie w procesie, wywoływana jest metoda wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="5f17d-142">If a validation error or warning occurs in the process, the callback method is invoked.</span></span>  
  
 <span data-ttu-id="5f17d-143">Jeśli żaden błąd nie wystąpi, tworzony jest nowy komunikat kopiuje właściwości i nagłówki z oryginalną wiadomość, która używa zestaw informacji zweryfikowane teraz w strumień pamięci, który jest otoczony przez <xref:System.Xml.XmlDictionaryReader> i dodane do wymiany wiadomości.</span><span class="sxs-lookup"><span data-stu-id="5f17d-143">If no error occurs, a new message is constructed that copies the properties and headers from the original message and uses the now-validated infoset in the memory stream, which is wrapped by an <xref:System.Xml.XmlDictionaryReader> and added to the replacement message.</span></span>  
  
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
  
 <span data-ttu-id="5f17d-144">`InspectionValidationHandler` Metoda jest wywoływana przez weryfikowanie <xref:System.Xml.XmlReader> zawsze, gdy występuje błąd walidacji schematu lub ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="5f17d-144">The `InspectionValidationHandler` method is called by the validating <xref:System.Xml.XmlReader> whenever a schema validation error or warning occurs.</span></span> <span data-ttu-id="5f17d-145">Następującą implementacją działa tylko z błędami i ignoruje wszystkie ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="5f17d-145">The following implementation only works with errors and ignores all warnings.</span></span>  
  
 <span data-ttu-id="5f17d-146">Na pierwszym zagadnieniem mogą wydawać się możliwe do dodania, sprawdzanie poprawności <xref:System.Xml.XmlReader> do wiadomości przy użyciu Inspektora wiadomości, dzięki czemu Weryfikacja się zdarzyć, komunikat jest przetwarzany i bez buforowania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="5f17d-146">On first consideration, it might seem possible to inject a validating <xref:System.Xml.XmlReader> into the message with the message inspector and let the validation happen as the message is processed and without buffering the message.</span></span> <span data-ttu-id="5f17d-147">Jednak oznacza, że to wywołanie zwrotne zgłasza wyjątki sprawdzania poprawności, gdzieś w usłudze modelu infrastruktury lub kod użytkownika, ponieważ wykryto nieprawidłowy węzłów XML, powodując nieprzewidywalne zachowanie.</span><span class="sxs-lookup"><span data-stu-id="5f17d-147">That, however, means that this callback throws the validation exceptions somewhere into the service model infrastructure or the user code as invalid XML nodes are detected, resulting in unpredictable behavior.</span></span> <span data-ttu-id="5f17d-148">Buforowanie podejście ochronnym kod użytkownika z nieprawidłową wiadomości całkowicie.</span><span class="sxs-lookup"><span data-stu-id="5f17d-148">The buffering approach shields the user code from invalid messages, entirely.</span></span>  
  
 <span data-ttu-id="5f17d-149">Jak już wspomniano wyjątki generowane przez program obsługi różnią się między klientem a usługą.</span><span class="sxs-lookup"><span data-stu-id="5f17d-149">As previously discussed, the exceptions thrown by the handler differ between the client and the service.</span></span> <span data-ttu-id="5f17d-150">W usłudze wyjątki są uzyskiwane z <xref:System.ServiceModel.FaultException>, na komputerze klienckim wyjątki są regularnie niestandardowymi wyjątkami.</span><span class="sxs-lookup"><span data-stu-id="5f17d-150">On the service, the exceptions are derived from <xref:System.ServiceModel.FaultException>, on the client the exceptions are regular custom exceptions.</span></span>  
  
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
  
## <a name="behavior"></a><span data-ttu-id="5f17d-151">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="5f17d-151">Behavior</span></span>  
 <span data-ttu-id="5f17d-152">Inspektorzy komunikatów są rozszerzeniami środowiska uruchomieniowego klienta lub w środowisku uruchomieniowym wysyłania.</span><span class="sxs-lookup"><span data-stu-id="5f17d-152">Message inspectors are extensions to the client runtime or the dispatch runtime.</span></span> <span data-ttu-id="5f17d-153">Takie rozszerzenia są konfigurowane przy użyciu *zachowania*.</span><span class="sxs-lookup"><span data-stu-id="5f17d-153">Such extensions are configured using *behaviors*.</span></span> <span data-ttu-id="5f17d-154">To zachowanie jest klasa, która zmienia zachowanie środowiska uruchomieniowego modelu usługi zmieniania konfiguracji domyślnej lub dodając rozszerzenia (na przykład inspektorzy komunikatów).</span><span class="sxs-lookup"><span data-stu-id="5f17d-154">A behavior is a class that changes the behavior of the service model runtime by changing the default configuration or adding extensions (such as message inspectors) to it.</span></span>  
  
 <span data-ttu-id="5f17d-155">Następujące `SchemaValidationBehavior` klasa to zachowanie umożliwia dodawanie inspektora komunikat ten przykład do klienta lub wysyłanie środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="5f17d-155">The following `SchemaValidationBehavior` class is the behavior used to add this sample's message inspector to the client or dispatch runtime.</span></span> <span data-ttu-id="5f17d-156">Implementacja jest raczej podstawowe w obu przypadkach.</span><span class="sxs-lookup"><span data-stu-id="5f17d-156">The implementation is rather basic in both cases.</span></span> <span data-ttu-id="5f17d-157">W <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyClientBehavior%2A> i <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyDispatchBehavior%2A>, inspektor wiadomość zostanie utworzony i dodany do <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> zbiór odpowiedniego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="5f17d-157">In <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyClientBehavior%2A> and <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyDispatchBehavior%2A>, the message inspector is created and added to the <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> collection of the respective runtime.</span></span>  
  
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
>  <span data-ttu-id="5f17d-158">To zachowanie określonego nie dwukrotnie jako atrybut i dlatego nie można dodać deklaratywne na typ kontraktu typu usługi.</span><span class="sxs-lookup"><span data-stu-id="5f17d-158">This particular behavior does not double as an attribute and therefore cannot be added declaratively onto a contract type of a service type.</span></span> <span data-ttu-id="5f17d-159">Jest to wykonana, ponieważ kolekcja schematów nie może zostać załadowany w deklaracji atrybutu i odwołujące się do lokalizacji dodatkowej konfiguracji (na przykład w celu ustawienia aplikacji) w tym atrybucie oznacza, że tworzenie elementu konfiguracji, który decyzji projektowych nie jest zgodne z pozostałą częścią konfiguracji modelu usług.</span><span class="sxs-lookup"><span data-stu-id="5f17d-159">This is a by-design decision made because the schema collection cannot be loaded in an attribute declaration and referring to an extra configuration location (for instance to the application settings) in this attribute means creating a configuration element that is not consistent with the rest of the service model configuration.</span></span> <span data-ttu-id="5f17d-160">Dlatego to zachowanie można dodać tylko obowiązkowo przez kod i za pośrednictwem rozszerzenia konfiguracji modelu usług.</span><span class="sxs-lookup"><span data-stu-id="5f17d-160">Therefore, this behavior can only be added imperatively through code and through a service model configuration extension.</span></span>  
  
## <a name="adding-the-message-inspector-through-configuration"></a><span data-ttu-id="5f17d-161">Dodawanie inspektora komunikat za pośrednictwem konfiguracji</span><span class="sxs-lookup"><span data-stu-id="5f17d-161">Adding the Message Inspector through Configuration</span></span>  
 <span data-ttu-id="5f17d-162">Do konfigurowania niestandardowe zachowanie punktu końcowego w pliku konfiguracyjnym aplikacji, model usług wymaga implementacji utworzyć konfigurację *elementu rozszerzenia* reprezentowane przez klasę pochodną <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>.</span><span class="sxs-lookup"><span data-stu-id="5f17d-162">For configuring a custom behavior on an endpoint in the application configuration file, the service model requires implementers to create a configuration *extension element* represented by a class derived from <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>.</span></span> <span data-ttu-id="5f17d-163">To rozszerzenie następnie należy dodać do sekcji konfiguracji modelu usług dla rozszerzenia, jak pokazano na następujące rozszerzenie omówione w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="5f17d-163">This extension must then be added to the service model's configuration section for extensions as shown for the following extension discussed in this section.</span></span>  
  
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
  
 <span data-ttu-id="5f17d-164">Rozszerzenia można dodać w aplikacji lub pliku konfiguracji platformy ASP.NET, który jest najbardziej typowe wybór, lub w pliku konfiguracji komputera.</span><span class="sxs-lookup"><span data-stu-id="5f17d-164">Extensions can be added in the application or ASP.NET configuration file, which is the most common choice, or in the machine configuration file.</span></span>  
  
 <span data-ttu-id="5f17d-165">Po dodaniu rozszerzenia zakres konfiguracji zachowanie można dodać do konfiguracji zachowania pokazany w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="5f17d-165">When the extension is added to a configuration scope, the behavior can be added to a behavior configuration as it is shown in the following code.</span></span> <span data-ttu-id="5f17d-166">Zachowanie konfiguracje są elementy wielokrotnego użytku, które można zastosować do wielu punktów końcowych, zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="5f17d-166">Behavior configurations are reusable elements that can be applied to multiple endpoints as required.</span></span> <span data-ttu-id="5f17d-167">Ponieważ określone zachowanie być skonfigurowane w tym miejscu implementuje <xref:System.ServiceModel.Description.IEndpointBehavior>, jest on prawidłowy tylko w sekcji odpowiedniej konfiguracji w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="5f17d-167">Because the particular behavior to be configured here implements <xref:System.ServiceModel.Description.IEndpointBehavior>, it is only valid in the respective configuration section in the configuration file.</span></span>  
  
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
  
 <span data-ttu-id="5f17d-168">`<schemaValidator>` Element, który konfiguruje Inspektor wiadomości jest wspierana przez `SchemaValidationBehaviorExtensionElement` klasy.</span><span class="sxs-lookup"><span data-stu-id="5f17d-168">The `<schemaValidator>` element that configures the message inspector is backed by the `SchemaValidationBehaviorExtensionElement` class.</span></span> <span data-ttu-id="5f17d-169">Klasa udostępnia dwie właściwości publiczne logiczną o nazwie `ValidateRequest` i `ValidateReply`.</span><span class="sxs-lookup"><span data-stu-id="5f17d-169">The class exposes two Boolean public properties named `ValidateRequest` and `ValidateReply`.</span></span> <span data-ttu-id="5f17d-170">Oba te są oznaczone <xref:System.Configuration.ConfigurationPropertyAttribute>.</span><span class="sxs-lookup"><span data-stu-id="5f17d-170">Both of these are marked with a <xref:System.Configuration.ConfigurationPropertyAttribute>.</span></span> <span data-ttu-id="5f17d-171">Ten atrybut stanowi link między właściwościami kodu i atrybutów XML, które będą widoczne na poprzedni element XML w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="5f17d-171">This attribute constitutes the link between the code properties and the XML attributes that can be seen on the preceding XML configuration element.</span></span> <span data-ttu-id="5f17d-172">Klasa ma również właściwość `Schemas` dodatkowo oznaczona za pomocą <xref:System.Configuration.ConfigurationCollectionAttribute> i jest typu `SchemaCollection`, który wchodzi w skład tego przykładu, ale został pominięty z tego dokumentu w celu skrócenia programu.</span><span class="sxs-lookup"><span data-stu-id="5f17d-172">The class also has a property `Schemas` that is additionally marked with the <xref:System.Configuration.ConfigurationCollectionAttribute> and is of the type `SchemaCollection`, which is also part of this sample but omitted from this document for brevity.</span></span> <span data-ttu-id="5f17d-173">Tej właściwości wraz z kolekcji i klasa elementu kolekcji `SchemaConfigElement` kopię `<schemas>` elementu w poprzednim fragmencie kodu konfiguracji i zezwala na dodawanie kolekcji schematów w zestawie sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="5f17d-173">This property along with the collection and the collection element class `SchemaConfigElement` backs the `<schemas>` element in the preceding configuration snippet and allows adding a collection of schemas to the validation set.</span></span>  
  
 <span data-ttu-id="5f17d-174">Zastąpione `CreateBehavior` metody jest przekształcany dane konfiguracyjne obiektu zachowanie po środowisko uruchomieniowe ocenia dane konfiguracji, ponieważ tworzy on klienta lub punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="5f17d-174">The overridden `CreateBehavior` method turns the configuration data into a behavior object when the runtime evaluates the configuration data as it builds a client or an endpoint.</span></span>  
  
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
  
## <a name="adding-message-inspectors-imperatively"></a><span data-ttu-id="5f17d-175">Dodawanie obowiązkowo inspektorzy komunikatów</span><span class="sxs-lookup"><span data-stu-id="5f17d-175">Adding Message Inspectors Imperatively</span></span>  
 <span data-ttu-id="5f17d-176">Z wyjątkiem przez atrybuty (które z powodu wymienionych wcześniej nie jest obsługiwany w tym przykładzie) i konfigurację zachowania dość łatwo można dodać do środowiska uruchomieniowego klienta i usługi przy użyciu kodu imperatywnego.</span><span class="sxs-lookup"><span data-stu-id="5f17d-176">Except through attributes (which is not supported in this sample for the reason cited previously) and configuration, behaviors can quite easily be added to a client and service runtime using imperative code.</span></span> <span data-ttu-id="5f17d-177">W tym przykładzie jest to realizowane w aplikacji klienckiej do testowania Inspektor komunikat klienta.</span><span class="sxs-lookup"><span data-stu-id="5f17d-177">In this sample, this is done in the client application to test the client message inspector.</span></span> <span data-ttu-id="5f17d-178">`GenericClient` Klasa pochodzi od <xref:System.ServiceModel.ClientBase%601>, który udostępnia konfigurację punktu końcowego w kodzie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5f17d-178">The `GenericClient` class is derived from <xref:System.ServiceModel.ClientBase%601>, which exposes the endpoint configuration to the user code.</span></span> <span data-ttu-id="5f17d-179">Zanim klient jest niejawnie otwarty konfiguracji punktu końcowego można zmienić, na przykład poprzez dodanie zachowania, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="5f17d-179">Before the client is implicitly opened the endpoint configuration can be changed, for instance by adding behaviors as shown in the following code.</span></span> <span data-ttu-id="5f17d-180">Dodawanie zachowania w usłudze odpowiada stopniu technika klienta pokazane tutaj i muszą być wykonywane przed otwarciem hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="5f17d-180">Adding the behavior on the service is largely equivalent to the client technique shown here and must be performed before the service host is opened.</span></span>  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5f17d-181">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="5f17d-181">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="5f17d-182">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5f17d-182">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="5f17d-183">Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5f17d-183">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="5f17d-184">Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5f17d-184">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5f17d-185">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="5f17d-185">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5f17d-186">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="5f17d-186">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5f17d-187">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="5f17d-187">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5f17d-188">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="5f17d-188">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageInspectors`  
  
## <a name="see-also"></a><span data-ttu-id="5f17d-189">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5f17d-189">See Also</span></span>
