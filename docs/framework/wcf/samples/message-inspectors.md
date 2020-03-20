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
# <a name="message-inspectors"></a><span data-ttu-id="ce7fa-102">Inspektorzy komunikatów</span><span class="sxs-lookup"><span data-stu-id="ce7fa-102">Message Inspectors</span></span>
<span data-ttu-id="ce7fa-103">W tym przykładzie pokazano, jak zaimplementować i skonfigurować inspektorów komunikatów klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-103">This sample demonstrates how to implement and configure client and service message inspectors.</span></span>  
  
 <span data-ttu-id="ce7fa-104">Inspektor komunikatów jest obiektem rozszerzalności, który może być używany w czasie wykonywania klienta modelu usługi i wysyłać środowisko uruchomieniowe programowo lub za pośrednictwem konfiguracji i który może sprawdzać i zmieniać komunikaty po ich odebraniu lub przed wysłaniem.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-104">A message inspector is an extensibility object that can be used in the service model's client runtime and dispatch runtime programmatically or through configuration and that can inspect and alter messages after they are received or before they are sent.</span></span>  
  
 <span data-ttu-id="ce7fa-105">W tym przykładzie implementuje podstawowy mechanizm sprawdzania poprawności komunikatów klienta i usługi, który sprawdza poprawność wiadomości przychodzących względem zestawu konfigurowalnych dokumentów schematu XML.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-105">This sample implements a basic client and service message validation mechanism that validates incoming messages against a set of configurable XML Schema documents.</span></span> <span data-ttu-id="ce7fa-106">Należy zauważyć, że ten przykład nie sprawdza poprawności komunikatów dla każdej operacji.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-106">Note that this sample does not validate messages for each operation.</span></span> <span data-ttu-id="ce7fa-107">Jest to celowe uproszczenie.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-107">This is an intentional simplification.</span></span>  
  
## <a name="message-inspector"></a><span data-ttu-id="ce7fa-108">Inspektor wiadomości</span><span class="sxs-lookup"><span data-stu-id="ce7fa-108">Message Inspector</span></span>  
 <span data-ttu-id="ce7fa-109">Inspektorzy komunikatów <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> klienta implementują interfejs i <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> inspektorzy komunikatów usługi implementują interfejs.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-109">Client message inspectors implement the <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> interface and service message inspectors implement the <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> interface.</span></span> <span data-ttu-id="ce7fa-110">Implementacje można połączyć w jedną klasę, aby utworzyć inspektora wiadomości, który działa dla obu stron.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-110">The implementations can be combined into a single class to form a message inspector that works for both sides.</span></span> <span data-ttu-id="ce7fa-111">W tym przykładzie implementuje taki inspektor wiadomości połączone.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-111">This sample implements such a combined message inspector.</span></span> <span data-ttu-id="ce7fa-112">Inspektor jest skonstruowany przekazywania w zestawie schematów, względem których są sprawdzane wiadomości przychodzące i wychodzące i pozwala deweloperowi określić, czy przychodzące lub wychodzące wiadomości są sprawdzane i czy inspektor jest w trybie wysyłki lub klienta, który wpływa na obsługę błędów, jak omówiono w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-112">The inspector is constructed passing in a set of schemas against which incoming and outgoing messages are validated and allows the developer to specify whether incoming or outgoing messages are validated and whether the inspector is in dispatch or client mode, which affects the error handling as discussed later in this topic.</span></span>  
  
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
  
 <span data-ttu-id="ce7fa-113">Każdy inspektor komunikatów usługi (dyspozytora) musi zaimplementować dwie <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> metody <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> i <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-113">Any service (dispatcher) message inspector must implement the two <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> methods <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> and <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>.</span></span>  
  
 <span data-ttu-id="ce7fa-114"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>jest wywoływana przez dyspozytora po odebraniu wiadomości, przetwarzane przez stos kanału i przypisane do usługi, ale przed jej deserializacji i wysyłki do operacji.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-114"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> is invoked by the dispatcher when a message has been received, processed by the channel stack and assigned to a service, but before it is deserialized and dispatched to an operation.</span></span> <span data-ttu-id="ce7fa-115">Jeśli wiadomość przychodząca została zaszyfrowana, wiadomość jest już odszyfrowana, gdy dotrze do inspektora wiadomości.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-115">If the incoming message was encrypted, the message is already decrypted when it reaches the message inspector.</span></span> <span data-ttu-id="ce7fa-116">Metoda pobiera `request` komunikat przekazany jako parametr odwołania, który umożliwia wiadomości, które mają być kontrolowane, manipulować lub zastępowane w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-116">The method gets the `request` message passed as a reference parameter, which allows the message to be inspected, manipulated or replaced as required.</span></span> <span data-ttu-id="ce7fa-117">Zwracana wartość może być dowolny obiekt i jest używany jako <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> obiekt stanu korelacji, który jest przekazywany, gdy usługa zwraca odpowiedź na bieżącą wiadomość.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-117">The return value can be any object and is used as a correlation state object that is passed to <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> when the service returns a reply to the current message.</span></span> <span data-ttu-id="ce7fa-118">W tym <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> przykładzie deleguje inspekcję (sprawdzanie poprawności) `ValidateMessageBody` wiadomości do prywatnej, lokalnej metody i zwraca obiekt stanu korelacji bez.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-118">In this sample, <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> delegates the inspection (validation) of the message to the private, local method `ValidateMessageBody` and returns no correlation state object.</span></span> <span data-ttu-id="ce7fa-119">Ta metoda gwarantuje, że żadne nieprawidłowe wiadomości przechodzą do usługi.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-119">This method ensures that no invalid messages pass into the service.</span></span>  
  
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
  
 <span data-ttu-id="ce7fa-120"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>jest wywoływana za każdym razem, gdy odpowiedź jest gotowa do odesłania do klienta lub w przypadku wiadomości jednokierunkowych, gdy wiadomość przychodząca została przetworzona.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-120"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29> is invoked whenever a reply is ready to be sent back to a client, or in the case of one-way messages, when the incoming message has been processed.</span></span> <span data-ttu-id="ce7fa-121">Dzięki temu rozszerzenia mogą liczyć na to, że będą nazywane symetrycznie, niezależnie od posła do PE.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-121">This allows extensions to count on being called symmetrically, regardless of MEP.</span></span> <span data-ttu-id="ce7fa-122">Podobnie <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>jak w , wiadomość jest przekazywana jako parametr odniesienia i może być kontrolowana, modyfikowana lub wymieniana.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-122">As with <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, the message is passed as a reference parameter and can be inspected, modified or replaced.</span></span> <span data-ttu-id="ce7fa-123">Sprawdzanie poprawności wiadomości, który jest wykonywany w tym `ValidMessageBody` przykładzie jest ponownie delegowane do metody, ale obsługa błędów sprawdzania poprawności jest nieco inna w tym przypadku.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-123">The validation of the message that is performed in this sample is again delegated to the `ValidMessageBody` method, but the handling of validation errors is slightly different in this case.</span></span>  
  
 <span data-ttu-id="ce7fa-124">Jeśli błąd sprawdzania poprawności występuje `ValidateMessageBody` w usłudze, metoda zgłasza wyjątki <xref:System.ServiceModel.FaultException>pochodne.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-124">If a validation error occurs on the service, the `ValidateMessageBody` method throws <xref:System.ServiceModel.FaultException>-derived exceptions.</span></span> <span data-ttu-id="ce7fa-125">W <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>programach wyjątki te można umieścić w infrastrukturze modelu usługi, gdzie są automatycznie przekształcane w błędy protokołu SOAP i przekazywane do klienta.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-125">In <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, these exceptions can be put into the service model infrastructure where they are automatically transformed into SOAP faults and relayed to the client.</span></span> <span data-ttu-id="ce7fa-126">W <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> <xref:System.ServiceModel.FaultException> , wyjątki nie mogą być wprowadzane do infrastruktury, ponieważ przekształcenie wyjątków błędów zgłaszanych przez usługę występuje przed inspektorem wiadomości jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-126">In <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A>, <xref:System.ServiceModel.FaultException> exceptions must not be put into the infrastructure, because the transformation of fault exceptions thrown by the service occurs before the message inspector is called.</span></span> <span data-ttu-id="ce7fa-127">W związku z tym następująca implementacja przechwytuje znany `ReplyValidationFault` wyjątek i zastępuje komunikat odpowiedzi z jawnym komunikatem o błędzie.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-127">Therefore the following implementation catches the known `ReplyValidationFault` exception and replaces the reply message with an explicit fault message.</span></span> <span data-ttu-id="ce7fa-128">Ta metoda zapewnia, że nie nieprawidłowe komunikaty są zwracane przez implementację usługi.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-128">This method ensures that no invalid messages are returned by the service implementation.</span></span>  
  
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
  
 <span data-ttu-id="ce7fa-129">Inspektor komunikatów klienta jest bardzo podobny.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-129">The client message inspector is very similar.</span></span> <span data-ttu-id="ce7fa-130">Dwie metody, które muszą <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> być <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.AfterReceiveReply%2A> <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>zaimplementowane z są i .</span><span class="sxs-lookup"><span data-stu-id="ce7fa-130">The two methods that must be implemented from <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> are <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.AfterReceiveReply%2A> and <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>.</span></span>  
  
 <span data-ttu-id="ce7fa-131"><xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>jest wywoływana, gdy wiadomość została złożona przez aplikację kliencką lub przez program formatera operacji.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-131"><xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> is invoked when the message has been composed either by the client application or by the operation formatter.</span></span> <span data-ttu-id="ce7fa-132">Podobnie jak w inspektorów wiadomości dyspozytora, wiadomość może być po prostu kontrolowane lub całkowicie zastąpione.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-132">As with the dispatcher message inspectors, the message can just be inspected or entirely replaced.</span></span> <span data-ttu-id="ce7fa-133">W tym przykładzie inspektor deleguje `ValidateMessageBody` do tej samej lokalnej metody pomocnika, która jest również używana dla inspektorów komunikatów wysyłki.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-133">In this sample, the inspector delegates to the same local `ValidateMessageBody` helper method that is also used for the dispatch message inspectors.</span></span>  
  
 <span data-ttu-id="ce7fa-134">Różnica behawioralna między weryfikacji klienta i usługi (jak określono w konstruktorze) jest, że sprawdzanie poprawności klienta zgłasza wyjątki lokalne, które są wprowadzane do kodu użytkownika, ponieważ występują lokalnie, a nie z powodu błędu usługi.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-134">The behavioral difference between the client and service validation (as specified in the constructor) is that the client validation throws local exceptions that are put into the user code because they occur locally and not because of a service failure.</span></span> <span data-ttu-id="ce7fa-135">Ogólnie rzecz biorąc, regułą jest to, że inspektorzy dyspozytora usługi zgłaszają błędy i że inspektorzy klienta zgłaszają wyjątki.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-135">Generally, the rule is that service dispatcher inspectors throw faults and that client inspectors throw exceptions.</span></span>  
  
 <span data-ttu-id="ce7fa-136">Ta <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> implementacja zapewnia, że żadne nieprawidłowe komunikaty nie są wysyłane do usługi.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-136">This <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> implementation ensures that no invalid messages are sent to the service.</span></span>  
  
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
  
 <span data-ttu-id="ce7fa-137">Implementacja `AfterReceiveReply` zapewnia, że żadne nieprawidłowe komunikaty odebrane z usługi są przekazywane do kodu użytkownika klienta.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-137">The `AfterReceiveReply` implementation ensures that no invalid messages received from the service are relayed to the client user code.</span></span>  
  
```csharp  
void IClientMessageInspector.AfterReceiveReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
{  
    if (validateReply)  
    {  
        ValidateMessageBody(ref reply, false);  
    }  
}  
```  
  
 <span data-ttu-id="ce7fa-138">Sercem tego inspektora poszczególnych `ValidateMessageBody` komunikatów jest metoda.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-138">The heart of this particular message inspector is the `ValidateMessageBody` method.</span></span> <span data-ttu-id="ce7fa-139">Aby wykonać swoją pracę, zawija sprawdzanie poprawności <xref:System.Xml.XmlReader> wokół poddrzewa zawartości treści treści przekazywanych wiadomości.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-139">To perform its work, it wraps a validating <xref:System.Xml.XmlReader> around the body content sub-tree of the passed message.</span></span> <span data-ttu-id="ce7fa-140">Czytnik jest wypełniany zestaw schematów, które inspektor wiadomości posiada i wywołania zwrotnego `InspectionValidationHandler` sprawdzania poprawności jest ustawiona na delegata odnoszące się do tego, który jest zdefiniowany obok tej metody.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-140">The reader is populated with the set of schemas that the message inspector holds and the validation callback is set to a delegate referring to the `InspectionValidationHandler` that is defined alongside this method.</span></span> <span data-ttu-id="ce7fa-141">Aby wykonać sprawdzanie poprawności, wiadomość jest następnie odczytywana i <xref:System.Xml.XmlDictionaryWriter>buforowana w kopii strumieniowej pamięci .</span><span class="sxs-lookup"><span data-stu-id="ce7fa-141">To perform the validation, the message is then read and spooled into a memory stream-backed <xref:System.Xml.XmlDictionaryWriter>.</span></span> <span data-ttu-id="ce7fa-142">Jeśli błąd sprawdzania poprawności lub ostrzeżenie występuje w procesie, wywoływana jest metoda wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-142">If a validation error or warning occurs in the process, the callback method is invoked.</span></span>  
  
 <span data-ttu-id="ce7fa-143">Jeśli nie wystąpi żaden błąd, zostanie skonstruowany nowy komunikat, który kopiuje właściwości i nagłówki z oryginalnej wiadomości i używa <xref:System.Xml.XmlDictionaryReader> teraz zweryfikowanego zestawu informacyjnego w strumieniu pamięci, który jest zawijany przez komunikat zastępczy i dodany do wiadomości zastępczej.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-143">If no error occurs, a new message is constructed that copies the properties and headers from the original message and uses the now-validated infoset in the memory stream, which is wrapped by an <xref:System.Xml.XmlDictionaryReader> and added to the replacement message.</span></span>  
  
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
  
 <span data-ttu-id="ce7fa-144">Metoda `InspectionValidationHandler` jest wywoływana przez <xref:System.Xml.XmlReader> sprawdzanie poprawności, gdy wystąpi błąd sprawdzania poprawności schematu lub ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-144">The `InspectionValidationHandler` method is called by the validating <xref:System.Xml.XmlReader> whenever a schema validation error or warning occurs.</span></span> <span data-ttu-id="ce7fa-145">Poniższa implementacja działa tylko z błędami i ignoruje wszystkie ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-145">The following implementation only works with errors and ignores all warnings.</span></span>  
  
 <span data-ttu-id="ce7fa-146">W pierwszej sprawie może się wydawać, <xref:System.Xml.XmlReader> że możliwe jest wstrzyknięcie sprawdzania poprawności do wiadomości za pomocą inspektora wiadomości i umożliwienie sprawdzania poprawności podczas przetwarzania wiadomości i bez buforowania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-146">On first consideration, it might seem possible to inject a validating <xref:System.Xml.XmlReader> into the message with the message inspector and let the validation happen as the message is processed and without buffering the message.</span></span> <span data-ttu-id="ce7fa-147">Oznacza to jednak, że to wywołanie zwrotne zgłasza wyjątki sprawdzania poprawności gdzieś w infrastrukturze modelu usługi lub kod użytkownika, jak nieprawidłowe węzły XML są wykrywane, co powoduje nieprzewidywalne zachowanie.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-147">That, however, means that this callback throws the validation exceptions somewhere into the service model infrastructure or the user code as invalid XML nodes are detected, resulting in unpredictable behavior.</span></span> <span data-ttu-id="ce7fa-148">Podejście buforowania chroni kod użytkownika przed nieprawidłowymi wiadomościami, całkowicie.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-148">The buffering approach shields the user code from invalid messages, entirely.</span></span>  
  
 <span data-ttu-id="ce7fa-149">Jak wcześniej wspomniano, wyjątki generowane przez program obsługi różnią się między klientem a usługą.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-149">As previously discussed, the exceptions thrown by the handler differ between the client and the service.</span></span> <span data-ttu-id="ce7fa-150">W usłudze wyjątki są uzyskiwane z <xref:System.ServiceModel.FaultException>, na kliencie wyjątki są regularne wyjątki niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-150">On the service, the exceptions are derived from <xref:System.ServiceModel.FaultException>, on the client the exceptions are regular custom exceptions.</span></span>  
  
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
  
## <a name="behavior"></a><span data-ttu-id="ce7fa-151">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="ce7fa-151">Behavior</span></span>  
 <span data-ttu-id="ce7fa-152">Inspektorzy komunikatów są rozszerzenia do środowiska wykonawczego klienta lub środowiska wykonawczego wysyłki.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-152">Message inspectors are extensions to the client runtime or the dispatch runtime.</span></span> <span data-ttu-id="ce7fa-153">Takie rozszerzenia są konfigurowane przy użyciu *zachowań*.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-153">Such extensions are configured using *behaviors*.</span></span> <span data-ttu-id="ce7fa-154">Zachowanie jest klasą, która zmienia zachowanie środowiska wykonawczego modelu usługi, zmieniając domyślną konfigurację lub dodając do niego rozszerzenia (takie jak inspektorzy wiadomości).</span><span class="sxs-lookup"><span data-stu-id="ce7fa-154">A behavior is a class that changes the behavior of the service model runtime by changing the default configuration or adding extensions (such as message inspectors) to it.</span></span>  
  
 <span data-ttu-id="ce7fa-155">Następująca `SchemaValidationBehavior` klasa jest zachowanie używane do dodawania inspektora wiadomości tego przykładu do środowiska uruchomieniowego klienta lub wysyłki.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-155">The following `SchemaValidationBehavior` class is the behavior used to add this sample's message inspector to the client or dispatch runtime.</span></span> <span data-ttu-id="ce7fa-156">Wdrożenie jest raczej podstawowe w obu przypadkach.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-156">The implementation is rather basic in both cases.</span></span> <span data-ttu-id="ce7fa-157">W <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyClientBehavior%2A> <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyDispatchBehavior%2A>i , Inspektor wiadomości jest <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> tworzony i dodawany do kolekcji odpowiedniego środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-157">In <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyClientBehavior%2A> and <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyDispatchBehavior%2A>, the message inspector is created and added to the <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> collection of the respective runtime.</span></span>  
  
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
> <span data-ttu-id="ce7fa-158">To określone zachowanie nie jest dwukrotnie jako atrybut i dlatego nie można dodać deklaratywnie do typu umowy typu usługi.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-158">This particular behavior does not double as an attribute and therefore cannot be added declaratively onto a contract type of a service type.</span></span> <span data-ttu-id="ce7fa-159">Jest to decyzja w projekcie, ponieważ kolekcji schematu nie można załadować w deklaracji atrybutu i odwoływanie się do dodatkowej lokalizacji konfiguracji (na przykład do ustawień aplikacji) w tym atrybucie oznacza utworzenie elementu konfiguracji, który nie jest zgodna z pozostałą częścią konfiguracji modelu usługi.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-159">This is a by-design decision made because the schema collection cannot be loaded in an attribute declaration and referring to an extra configuration location (for instance to the application settings) in this attribute means creating a configuration element that is not consistent with the rest of the service model configuration.</span></span> <span data-ttu-id="ce7fa-160">W związku z tym to zachowanie można dodać tylko za pomocą kodu i za pośrednictwem rozszerzenia konfiguracji modelu usługi.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-160">Therefore, this behavior can only be added imperatively through code and through a service model configuration extension.</span></span>  
  
## <a name="adding-the-message-inspector-through-configuration"></a><span data-ttu-id="ce7fa-161">Dodawanie Inspektora wiadomości za pomocą konfiguracji</span><span class="sxs-lookup"><span data-stu-id="ce7fa-161">Adding the Message Inspector through Configuration</span></span>  
 <span data-ttu-id="ce7fa-162">Aby skonfigurować zachowanie niestandardowe w punkcie końcowym w pliku konfiguracji aplikacji, model usługi wymaga implementerów do <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>utworzenia elementu *rozszerzenia* konfiguracji reprezentowanego przez klasę pochodzącą z programu .</span><span class="sxs-lookup"><span data-stu-id="ce7fa-162">For configuring a custom behavior on an endpoint in the application configuration file, the service model requires implementers to create a configuration *extension element* represented by a class derived from <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>.</span></span> <span data-ttu-id="ce7fa-163">To rozszerzenie należy następnie dodać do sekcji konfiguracji modelu usługi dla rozszerzeń, jak pokazano dla następującego rozszerzenia omówione w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-163">This extension must then be added to the service model's configuration section for extensions as shown for the following extension discussed in this section.</span></span>  
  
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
  
 <span data-ttu-id="ce7fa-164">Rozszerzenia można dodać w pliku konfiguracyjnym aplikacji lub ASP.NET, który jest najczęstszym wyborem lub w pliku konfiguracji komputera.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-164">Extensions can be added in the application or ASP.NET configuration file, which is the most common choice, or in the machine configuration file.</span></span>  
  
 <span data-ttu-id="ce7fa-165">Po dodaniu rozszerzenia do zakresu konfiguracji, zachowanie można dodać do konfiguracji zachowania, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-165">When the extension is added to a configuration scope, the behavior can be added to a behavior configuration as it is shown in the following code.</span></span> <span data-ttu-id="ce7fa-166">Zachowania konfiguracje są elementy wielokrotnegoużytnia, które mogą być stosowane do wielu punktów końcowych zgodnie z wymaganiami.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-166">Behavior configurations are reusable elements that can be applied to multiple endpoints as required.</span></span> <span data-ttu-id="ce7fa-167">Ponieważ określone zachowanie, które ma <xref:System.ServiceModel.Description.IEndpointBehavior>być skonfigurowane w tym miejscu implementuje, jest prawidłowe tylko w odpowiedniej sekcji konfiguracji w pliku konfiguracyjnym.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-167">Because the particular behavior to be configured here implements <xref:System.ServiceModel.Description.IEndpointBehavior>, it is only valid in the respective configuration section in the configuration file.</span></span>  
  
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
  
 <span data-ttu-id="ce7fa-168">Element, `<schemaValidator>` który konfiguruje inspektora `SchemaValidationBehaviorExtensionElement` wiadomości jest wspierany przez klasę.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-168">The `<schemaValidator>` element that configures the message inspector is backed by the `SchemaValidationBehaviorExtensionElement` class.</span></span> <span data-ttu-id="ce7fa-169">Klasa udostępnia dwie logiczne właściwości `ValidateRequest` publiczne `ValidateReply`o nazwie i .</span><span class="sxs-lookup"><span data-stu-id="ce7fa-169">The class exposes two Boolean public properties named `ValidateRequest` and `ValidateReply`.</span></span> <span data-ttu-id="ce7fa-170">Oba te są oznaczone <xref:System.Configuration.ConfigurationPropertyAttribute>symbolem .</span><span class="sxs-lookup"><span data-stu-id="ce7fa-170">Both of these are marked with a <xref:System.Configuration.ConfigurationPropertyAttribute>.</span></span> <span data-ttu-id="ce7fa-171">Ten atrybut stanowi łącze między właściwościami kodu a atrybutami XML, które można zobaczyć w poprzednim elemencie konfiguracji XML.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-171">This attribute constitutes the link between the code properties and the XML attributes that can be seen on the preceding XML configuration element.</span></span> <span data-ttu-id="ce7fa-172">Klasa ma również `Schemas` właściwość, która jest <xref:System.Configuration.ConfigurationCollectionAttribute> dodatkowo oznaczona `SchemaCollection`i jest typu , który jest również częścią tego przykładu, ale pominięte w tym dokumencie dla zwięzłości.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-172">The class also has a property `Schemas` that is additionally marked with the <xref:System.Configuration.ConfigurationCollectionAttribute> and is of the type `SchemaCollection`, which is also part of this sample but omitted from this document for brevity.</span></span> <span data-ttu-id="ce7fa-173">Ta właściwość wraz z kolekcji `SchemaConfigElement` i `<schemas>` klasy elementu kolekcji wspiera element w poprzednim fragmentze konfiguracji i umożliwia dodawanie kolekcji schematów do zestawu sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-173">This property along with the collection and the collection element class `SchemaConfigElement` backs the `<schemas>` element in the preceding configuration snippet and allows adding a collection of schemas to the validation set.</span></span>  
  
 <span data-ttu-id="ce7fa-174">Zastąpiona `CreateBehavior` metoda zamienia dane konfiguracji w obiekt zachowania, gdy środowisko wykonawcze ocenia dane konfiguracji podczas tworzenia klienta lub punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-174">The overridden `CreateBehavior` method turns the configuration data into a behavior object when the runtime evaluates the configuration data as it builds a client or an endpoint.</span></span>  
  
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
  
## <a name="adding-message-inspectors-imperatively"></a><span data-ttu-id="ce7fa-175">Trwa dodawania inspektorów wiadomości</span><span class="sxs-lookup"><span data-stu-id="ce7fa-175">Adding Message Inspectors Imperatively</span></span>  
 <span data-ttu-id="ce7fa-176">Z wyjątkiem za pomocą atrybutów (który nie jest obsługiwany w tym przykładzie z powodu cytowane wcześniej) i konfiguracji, zachowania można dość łatwo dodać do środowiska uruchomieniowego klienta i usługi przy użyciu kodu imperatywu.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-176">Except through attributes (which is not supported in this sample for the reason cited previously) and configuration, behaviors can quite easily be added to a client and service runtime using imperative code.</span></span> <span data-ttu-id="ce7fa-177">W tym przykładzie jest to wykonywane w aplikacji klienckiej, aby przetestować inspektora komunikatów klienta.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-177">In this sample, this is done in the client application to test the client message inspector.</span></span> <span data-ttu-id="ce7fa-178">Klasa `GenericClient` jest pochodną <xref:System.ServiceModel.ClientBase%601>, który udostępnia konfiguracji punktu końcowego do kodu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-178">The `GenericClient` class is derived from <xref:System.ServiceModel.ClientBase%601>, which exposes the endpoint configuration to the user code.</span></span> <span data-ttu-id="ce7fa-179">Przed otwarciem klienta niejawnie można zmienić konfigurację punktu końcowego, na przykład dodając zachowania, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-179">Before the client is implicitly opened the endpoint configuration can be changed, for instance by adding behaviors as shown in the following code.</span></span> <span data-ttu-id="ce7fa-180">Dodawanie zachowania w usłudze jest w dużej mierze równoważne techniki klienta pokazano w tym miejscu i muszą być wykonywane przed otwarciem hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-180">Adding the behavior on the service is largely equivalent to the client technique shown here and must be performed before the service host is opened.</span></span>  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ce7fa-181">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="ce7fa-181">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="ce7fa-182">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ce7fa-182">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="ce7fa-183">Aby utworzyć rozwiązanie, postępuj zgodnie z instrukcjami w [tworzeniu przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ce7fa-183">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="ce7fa-184">Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ce7fa-184">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ce7fa-185">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-185">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ce7fa-186">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-186">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="ce7fa-187">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-187">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ce7fa-188">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="ce7fa-188">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageInspectors`  
