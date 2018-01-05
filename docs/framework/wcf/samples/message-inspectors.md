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
# <a name="message-inspectors"></a><span data-ttu-id="28629-102">Inspektorzy komunikatów</span><span class="sxs-lookup"><span data-stu-id="28629-102">Message Inspectors</span></span>
<span data-ttu-id="28629-103">W tym przykładzie pokazano, jak wdrożyć i skonfigurować klienta i usługi inspektorzy komunikatów.</span><span class="sxs-lookup"><span data-stu-id="28629-103">This sample demonstrates how to implement and configure client and service message inspectors.</span></span>  
  
 <span data-ttu-id="28629-104">Inspektor wiadomości jest obiektem rozszerzalności, który może być używana w modelu usługi klienta w czasie wykonywania i środowiska uruchomieniowego wysyłania programowo lub za pomocą konfiguracji i które można sprawdzić i zmienić wiadomości po otrzymaniu ich lub przed ich wysłaniem.</span><span class="sxs-lookup"><span data-stu-id="28629-104">A message inspector is an extensibility object that can be used in the service model's client runtime and dispatch runtime programmatically or through configuration and that can inspect and alter messages after they are received or before they are sent.</span></span>  
  
 <span data-ttu-id="28629-105">W tym przykładzie implementuje podstawowe klienta i usługi komunikatu sprawdzania poprawności mechanizmu sprawdzania wiadomości przychodzących z zestawem dokumentach schematów XML można skonfigurować.</span><span class="sxs-lookup"><span data-stu-id="28629-105">This sample implements a basic client and service message validation mechanism that validates incoming messages against a set of configurable XML Schema documents.</span></span> <span data-ttu-id="28629-106">Należy pamiętać, że w tym przykładzie nie można zweryfikować wiadomości dla każdej operacji.</span><span class="sxs-lookup"><span data-stu-id="28629-106">Note that this sample does not validate messages for each operation.</span></span> <span data-ttu-id="28629-107">Jest to zamierzone uproszczenia.</span><span class="sxs-lookup"><span data-stu-id="28629-107">This is an intentional simplification.</span></span>  
  
## <a name="message-inspector"></a><span data-ttu-id="28629-108">Inspektor wiadomości</span><span class="sxs-lookup"><span data-stu-id="28629-108">Message Inspector</span></span>  
 <span data-ttu-id="28629-109">Implementowanie inspektorzy komunikatów klienta <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> interfejsu i usługa implementuje inspektorzy komunikatów <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="28629-109">Client message inspectors implement the <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> interface and service message inspectors implement the <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> interface.</span></span> <span data-ttu-id="28629-110">Implementacje mogą być połączone w jedną klasę do utworzenia inspektora komunikat, który działa w przypadku obu stron.</span><span class="sxs-lookup"><span data-stu-id="28629-110">The implementations can be combined into a single class to form a message inspector that works for both sides.</span></span> <span data-ttu-id="28629-111">W tym przykładzie implementuje inspektora Scalonej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="28629-111">This sample implements such a combined message inspector.</span></span> <span data-ttu-id="28629-112">Inspektor jest tworzony przekazywanie w zestawie schematów, które są weryfikowane wiadomości przychodzących i wychodzących i umożliwia deweloperowi określić, czy są weryfikowane wiadomości przychodzących lub wychodzących i czy kontroler jest w trybie klienta lub wysyłania, która Obsługa błędów dotyczy, zgodnie z opisem w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="28629-112">The inspector is constructed passing in a set of schemas against which incoming and outgoing messages are validated and allows the developer to specify whether incoming or outgoing messages are validated and whether the inspector is in dispatch or client mode, which affects the error handling as discussed later in this topic.</span></span>  
  
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
  
 <span data-ttu-id="28629-113">Wszelkie inspektora wiadomości usługi (dyspozytora) musi implementować dwa <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> metody <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> i <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>.</span><span class="sxs-lookup"><span data-stu-id="28629-113">Any service (dispatcher) message inspector must implement the two <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> methods <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> and <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>.</span></span>  
  
 <span data-ttu-id="28629-114"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>jest wywoływany przez Dyspozytor wiadomość została otrzymał, przetwarzane przez stos kanału i przypisane do usługi, ale przed deserializacji i wysyłane do operacji.</span><span class="sxs-lookup"><span data-stu-id="28629-114"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> is invoked by the dispatcher when a message has been received, processed by the channel stack and assigned to a service, but before it is deserialized and dispatched to an operation.</span></span> <span data-ttu-id="28629-115">Jeśli komunikat przychodzący został zaszyfrowany, komunikat już jest odszyfrowywany po osiągnięciu inspektora wiadomości.</span><span class="sxs-lookup"><span data-stu-id="28629-115">If the incoming message was encrypted, the message is already decrypted when it reaches the message inspector.</span></span> <span data-ttu-id="28629-116">Pobiera metodę `request` komunikat przekazany jako parametr odwołania, dzięki czemu komunikat, aby sprawdził, manipulować lub zastąpione zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="28629-116">The method gets the `request` message passed as a reference parameter, which allows the message to be inspected, manipulated or replaced as required.</span></span> <span data-ttu-id="28629-117">Zwracana wartość może być dowolnym obiektem i jest używany jako obiekt stanu korelacji, który jest przekazywany do <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> gdy usługa zwraca odpowiedź do bieżącej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="28629-117">The return value can be any object and is used as a correlation state object that is passed to <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> when the service returns a reply to the current message.</span></span> <span data-ttu-id="28629-118">W tym przykładzie <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> deleguje inspekcji (Walidacja) wiadomości prywatne i lokalne metodę `ValidateMessageBody` i zwraca obiekt stanu nie korelacji.</span><span class="sxs-lookup"><span data-stu-id="28629-118">In this sample, <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> delegates the inspection (validation) of the message to the private, local method `ValidateMessageBody` and returns no correlation state object.</span></span> <span data-ttu-id="28629-119">Ta metoda gwarantuje, że żadne komunikaty nieprawidłowy przekazać do usługi.</span><span class="sxs-lookup"><span data-stu-id="28629-119">This method ensures that no invalid messages pass into the service.</span></span>  
  
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
  
 <span data-ttu-id="28629-120"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>jest wywoływane zawsze, gdy odpowiedź jest gotowa do wysłania do klienta lub w przypadku jednokierunkowe komunikaty, po przetworzeniu komunikatu przychodzącego.</span><span class="sxs-lookup"><span data-stu-id="28629-120"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29> is invoked whenever a reply is ready to be sent back to a client, or in the case of one-way messages, when the incoming message has been processed.</span></span> <span data-ttu-id="28629-121">Dzięki temu count wywoływana symetrycznie, niezależnie od MEP rozszerzeń.</span><span class="sxs-lookup"><span data-stu-id="28629-121">This allows extensions to count on being called symmetrically, regardless of MEP.</span></span> <span data-ttu-id="28629-122">Jak <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, wiadomość jest przekazywana jako parametr odwołania i może sprawdzenia, zmodyfikowane lub zastąpione.</span><span class="sxs-lookup"><span data-stu-id="28629-122">As with <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, the message is passed as a reference parameter and can be inspected, modified or replaced.</span></span> <span data-ttu-id="28629-123">Sprawdzanie poprawności wiadomości, które jest przeprowadzane w tym przykładzie jest ponownie delegowana do `ValidMessageBody` metody, ale obsługa błędów sprawdzania poprawności różni się nieco w takim przypadku.</span><span class="sxs-lookup"><span data-stu-id="28629-123">The validation of the message that is performed in this sample is again delegated to the `ValidMessageBody` method, but the handling of validation errors is slightly different in this case.</span></span>  
  
 <span data-ttu-id="28629-124">Jeśli wystąpi błąd sprawdzania poprawności w usłudze `ValidateMessageBody` metoda zgłasza <xref:System.ServiceModel.FaultException>-pochodnych wyjątków.</span><span class="sxs-lookup"><span data-stu-id="28629-124">If a validation error occurs on the service, the `ValidateMessageBody` method throws <xref:System.ServiceModel.FaultException>-derived exceptions.</span></span> <span data-ttu-id="28629-125">W <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, wyjątki te mogą być przełączane do modelu usługi infrastruktury, gdzie są one automatycznie przekształcone w błędach SOAP, a przekazany do klienta.</span><span class="sxs-lookup"><span data-stu-id="28629-125">In <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, these exceptions can be put into the service model infrastructure where they are automatically transformed into SOAP faults and relayed to the client.</span></span> <span data-ttu-id="28629-126">W <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A>, <xref:System.ServiceModel.FaultException> wyjątki nie mogą być umieszczone w infrastrukturę, ponieważ transformacja wyjątków błędów zgłaszanych przez usługę występuje przed wywołaniem inspektora wiadomości.</span><span class="sxs-lookup"><span data-stu-id="28629-126">In <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A>, <xref:System.ServiceModel.FaultException> exceptions must not be put into the infrastructure, because the transformation of fault exceptions thrown by the service occurs before the message inspector is called.</span></span> <span data-ttu-id="28629-127">W związku z tym implementacji następujących przechwytuje znane `ReplyValidationFault` wyjątku i zamienia komunikat odpowiedzi z komunikat o błędzie jawna.</span><span class="sxs-lookup"><span data-stu-id="28629-127">Therefore the following implementation catches the known `ReplyValidationFault` exception and replaces the reply message with an explicit fault message.</span></span> <span data-ttu-id="28629-128">Ta metoda gwarantuje, że żadne komunikaty nieprawidłowy są zwracane przez implementacji usługi.</span><span class="sxs-lookup"><span data-stu-id="28629-128">This method ensures that no invalid messages are returned by the service implementation.</span></span>  
  
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
  
 <span data-ttu-id="28629-129">Inspektor komunikat klienta jest bardzo podobne.</span><span class="sxs-lookup"><span data-stu-id="28629-129">The client message inspector is very similar.</span></span> <span data-ttu-id="28629-130">Te dwie metody, które muszą zostać zaimplementowane z <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> są <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.AfterReceiveReply%2A> i <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>.</span><span class="sxs-lookup"><span data-stu-id="28629-130">The two methods that must be implemented from <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> are <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.AfterReceiveReply%2A> and <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>.</span></span>  
  
 <span data-ttu-id="28629-131"><xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>wywoływane, gdy wiadomość została składane, przez aplikację klienta lub przez program formatujący operacji.</span><span class="sxs-lookup"><span data-stu-id="28629-131"><xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> is invoked when the message has been composed either by the client application or by the operation formatter.</span></span> <span data-ttu-id="28629-132">Zgodnie z dyspozytora inspektorzy komunikatów, może po prostu komunikat sprawdzenia lub całkowicie zastąpiona.</span><span class="sxs-lookup"><span data-stu-id="28629-132">As with the dispatcher message inspectors, the message can just be inspected or entirely replaced.</span></span> <span data-ttu-id="28629-133">W tym przykładzie Inspektor deleguje do tej samej lokalnej `ValidateMessageBody` metody pomocniczej, która służy do wysyłania inspektorzy komunikatów.</span><span class="sxs-lookup"><span data-stu-id="28629-133">In this sample, the inspector delegates to the same local `ValidateMessageBody` helper method that is also used for the dispatch message inspectors.</span></span>  
  
 <span data-ttu-id="28629-134">Behawioralnej różnica między klientem a usługą sprawdzania poprawności (jak określono w konstruktorze) jest, że sprawdzanie poprawności klienta zgłasza wyjątki lokalne, które są umieszczane w kodzie użytkownika, ponieważ występują lokalnie, a nie z powodu błędu usługi.</span><span class="sxs-lookup"><span data-stu-id="28629-134">The behavioral difference between the client and service validation (as specified in the constructor) is that the client validation throws local exceptions that are put into the user code because they occur locally and not because of a service failure.</span></span> <span data-ttu-id="28629-135">Ogólnie rzecz biorąc jest zasada, czy usługa dyspozytora inspektorzy zgłoszenie błędów i że inspektorzy klienta zgłaszają wyjątki.</span><span class="sxs-lookup"><span data-stu-id="28629-135">Generally, the rule is that service dispatcher inspectors throw faults and that client inspectors throw exceptions.</span></span>  
  
 <span data-ttu-id="28629-136">To <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> implementacja zapewnia, że nie nieprawidłowy komunikaty są wysyłane do usługi.</span><span class="sxs-lookup"><span data-stu-id="28629-136">This <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> implementation ensures that no invalid messages are sent to the service.</span></span>  
  
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
  
 <span data-ttu-id="28629-137">`AfterReceiveReply` Implementacja zapewnia, że nie komunikaty nieprawidłowy otrzymał z usługi są przekazywane do kodu użytkownika klienta.</span><span class="sxs-lookup"><span data-stu-id="28629-137">The `AfterReceiveReply` implementation ensures that no invalid messages received from the service are relayed to the client user code.</span></span>  
  
```  
void IClientMessageInspector.AfterReceiveReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
{  
    if (validateReply)  
    {  
        ValidateMessageBody(ref reply, false);  
    }  
}  
```  
  
 <span data-ttu-id="28629-138">Ten inspektor danego komunikatu to `ValidateMessageBody` metody.</span><span class="sxs-lookup"><span data-stu-id="28629-138">The heart of this particular message inspector is the `ValidateMessageBody` method.</span></span> <span data-ttu-id="28629-139">Aby wykonać swoją pracę, jest zawijany, sprawdzanie poprawności <xref:System.Xml.XmlReader> wokół zawartości drzewa podrzędnego treści komunikatu przekazany.</span><span class="sxs-lookup"><span data-stu-id="28629-139">To perform its work, it wraps a validating <xref:System.Xml.XmlReader> around the body content sub-tree of the passed message.</span></span> <span data-ttu-id="28629-140">Czytnik jest wypełniane przy użyciu zestawu schematów, które przechowuje inspektora wiadomości i wywołanie zwrotne weryfikacji ma ustawioną wartość delegata odwołujących się do `InspectionValidationHandler` zdefiniowanego równolegle z tej metody.</span><span class="sxs-lookup"><span data-stu-id="28629-140">The reader is populated with the set of schemas that the message inspector holds and the validation callback is set to a delegate referring to the `InspectionValidationHandler` that is defined alongside this method.</span></span> <span data-ttu-id="28629-141">Przeprowadzenie weryfikacji wiadomość jest następnie odczytu i buforowane w pamięci kopia strumienia <xref:System.Xml.XmlDictionaryWriter>.</span><span class="sxs-lookup"><span data-stu-id="28629-141">To perform the validation, the message is then read and spooled into a memory stream-backed <xref:System.Xml.XmlDictionaryWriter>.</span></span> <span data-ttu-id="28629-142">Jeśli wystąpi błąd sprawdzania poprawności lub ostrzeżenie w procesie, wywoływana jest metoda wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="28629-142">If a validation error or warning occurs in the process, the callback method is invoked.</span></span>  
  
 <span data-ttu-id="28629-143">Jeśli nie występują błędy, nowy komunikat jest tworzony kopiuje właściwości i nagłówków z oryginalnej wiadomości, który używa typu infoset zweryfikowane teraz w strumieniu pamięci, która opakowane w usłudze <xref:System.Xml.XmlDictionaryReader> i dodane do wymiany wiadomości.</span><span class="sxs-lookup"><span data-stu-id="28629-143">If no error occurs, a new message is constructed that copies the properties and headers from the original message and uses the now-validated infoset in the memory stream, which is wrapped by an <xref:System.Xml.XmlDictionaryReader> and added to the replacement message.</span></span>  
  
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
  
 <span data-ttu-id="28629-144">`InspectionValidationHandler` Metoda jest wywoływana przez sprawdzanie poprawności <xref:System.Xml.XmlReader> zawsze, gdy wystąpi błąd sprawdzania poprawności schematu lub ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="28629-144">The `InspectionValidationHandler` method is called by the validating <xref:System.Xml.XmlReader> whenever a schema validation error or warning occurs.</span></span> <span data-ttu-id="28629-145">Następująca implementacja działa tylko z błędami i ignoruje wszystkie ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="28629-145">The following implementation only works with errors and ignores all warnings.</span></span>  
  
 <span data-ttu-id="28629-146">Na pierwszym zagadnieniem może wydawać się możliwe do dodania, sprawdzanie poprawności <xref:System.Xml.XmlReader> do wiadomości z Inspektora wiadomości i umożliwiają sprawdzanie poprawności stanie komunikat jest przetwarzany i bez buforowania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="28629-146">On first consideration, it might seem possible to inject a validating <xref:System.Xml.XmlReader> into the message with the message inspector and let the validation happen as the message is processed and without buffering the message.</span></span> <span data-ttu-id="28629-147">Jednak oznacza, że to wywołanie zwrotne zgłasza wyjątki poprawności gdzieś w usłudze modelu infrastruktury lub kod użytkownika jak wykryto nieprawidłowy węzłów XML, spowodować nieprzewidywalne zachowanie.</span><span class="sxs-lookup"><span data-stu-id="28629-147">That, however, means that this callback throws the validation exceptions somewhere into the service model infrastructure or the user code as invalid XML nodes are detected, resulting in unpredictable behavior.</span></span> <span data-ttu-id="28629-148">Podejście buforowania całkowicie chroni kod użytkownika z nieprawidłową wiadomości.</span><span class="sxs-lookup"><span data-stu-id="28629-148">The buffering approach shields the user code from invalid messages, entirely.</span></span>  
  
 <span data-ttu-id="28629-149">Jak już wspomniano wyjątki generowane przez program obsługi różnią się między klientem a usługą.</span><span class="sxs-lookup"><span data-stu-id="28629-149">As previously discussed, the exceptions thrown by the handler differ between the client and the service.</span></span> <span data-ttu-id="28629-150">W usłudze, wyjątki są uzyskiwane z <xref:System.ServiceModel.FaultException>, na kliencie wyjątki są regularnie niestandardowymi wyjątkami.</span><span class="sxs-lookup"><span data-stu-id="28629-150">On the service, the exceptions are derived from <xref:System.ServiceModel.FaultException>, on the client the exceptions are regular custom exceptions.</span></span>  
  
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
  
## <a name="behavior"></a><span data-ttu-id="28629-151">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="28629-151">Behavior</span></span>  
 <span data-ttu-id="28629-152">Inspektorzy komunikatów są rozszerzenia do środowiska uruchomieniowego klienta lub środowisko wykonawcze wysyłce.</span><span class="sxs-lookup"><span data-stu-id="28629-152">Message inspectors are extensions to the client runtime or the dispatch runtime.</span></span> <span data-ttu-id="28629-153">Takie rozszerzenia są skonfigurowane przy użyciu *zachowania*.</span><span class="sxs-lookup"><span data-stu-id="28629-153">Such extensions are configured using *behaviors*.</span></span> <span data-ttu-id="28629-154">Zachowanie jest klasa, która zmienia zachowanie środowiska uruchomieniowego modelu usługi przez zmianę konfiguracji domyślnej lub dodanie rozszerzenia (na przykład inspektorzy komunikatów).</span><span class="sxs-lookup"><span data-stu-id="28629-154">A behavior is a class that changes the behavior of the service model runtime by changing the default configuration or adding extensions (such as message inspectors) to it.</span></span>  
  
 <span data-ttu-id="28629-155">Następujące `SchemaValidationBehavior` klasy jest zachowanie umożliwia Dodaj ten przykład inspektora wiadomości do klienta lub wysyłania środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="28629-155">The following `SchemaValidationBehavior` class is the behavior used to add this sample's message inspector to the client or dispatch runtime.</span></span> <span data-ttu-id="28629-156">Implementacja jest raczej podstawowe w obu przypadkach.</span><span class="sxs-lookup"><span data-stu-id="28629-156">The implementation is rather basic in both cases.</span></span> <span data-ttu-id="28629-157">W <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyClientBehavior%2A> i <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyDispatchBehavior%2A>, inspektora wiadomości jest tworzony i dodawany do <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> kolekcji odpowiednich środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="28629-157">In <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyClientBehavior%2A> and <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyDispatchBehavior%2A>, the message inspector is created and added to the <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> collection of the respective runtime.</span></span>  
  
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
>  <span data-ttu-id="28629-158">To zachowanie określonego nie dwukrotnie jako atrybut i dlatego nie można dodać deklaratywnie na typ kontraktu usługi typu.</span><span class="sxs-lookup"><span data-stu-id="28629-158">This particular behavior does not double as an attribute and therefore cannot be added declaratively onto a contract type of a service type.</span></span> <span data-ttu-id="28629-159">Jest to wykonana, ponieważ nie można załadować kolekcji schematów w deklaracji atrybutu i odwołujące się do lokalizacji dodatkowej konfiguracji (na przykład w celu ustawienia aplikacji), w tym atrybucie oznacza tworzenia elementu konfiguracji, który decyzji projektowych nie jest zgodne z pozostałą częścią konfiguracji modelu usług.</span><span class="sxs-lookup"><span data-stu-id="28629-159">This is a by-design decision made because the schema collection cannot be loaded in an attribute declaration and referring to an extra configuration location (for instance to the application settings) in this attribute means creating a configuration element that is not consistent with the rest of the service model configuration.</span></span> <span data-ttu-id="28629-160">W związku z tym to zachowanie można dodać tylko imperatively za pośrednictwem kodu oraz rozszerzenie konfiguracji modelu usług.</span><span class="sxs-lookup"><span data-stu-id="28629-160">Therefore, this behavior can only be added imperatively through code and through a service model configuration extension.</span></span>  
  
## <a name="adding-the-message-inspector-through-configuration"></a><span data-ttu-id="28629-161">Dodawanie inspektora wiadomości przy użyciu konfiguracji</span><span class="sxs-lookup"><span data-stu-id="28629-161">Adding the Message Inspector through Configuration</span></span>  
 <span data-ttu-id="28629-162">W przypadku konfigurowania niestandardowych zachowania punktu końcowego w pliku konfiguracyjnym aplikacji, modelu usługi wymaga implementacji utworzyć konfigurację *elementu rozszerzenia* reprezentowany przez klasę pochodną <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>.</span><span class="sxs-lookup"><span data-stu-id="28629-162">For configuring a custom behavior on an endpoint in the application configuration file, the service model requires implementers to create a configuration *extension element* represented by a class derived from <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>.</span></span> <span data-ttu-id="28629-163">To rozszerzenie należy następnie dodać do sekcji konfiguracji modelu usług dla rozszerzeń, jak pokazano na następujące rozszerzenie omówione w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="28629-163">This extension must then be added to the service model's configuration section for extensions as shown for the following extension discussed in this section.</span></span>  
  
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
  
 <span data-ttu-id="28629-164">Rozszerzenia mogą być dodawane w aplikacji lub plik konfiguracyjny programu ASP.NET, który jest najbardziej typowych wybór, lub w pliku konfiguracji komputera.</span><span class="sxs-lookup"><span data-stu-id="28629-164">Extensions can be added in the application or ASP.NET configuration file, which is the most common choice, or in the machine configuration file.</span></span>  
  
 <span data-ttu-id="28629-165">Rozszerzenie zostanie dodany do zakresu konfiguracji, to zachowanie można dodać do konfiguracji zachowania pokazany w następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="28629-165">When the extension is added to a configuration scope, the behavior can be added to a behavior configuration as it is shown in the following code.</span></span> <span data-ttu-id="28629-166">Zachowanie konfiguracje są elementy wielokrotnego użytku, które można zastosować do wielu punktów końcowych zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="28629-166">Behavior configurations are reusable elements that can be applied to multiple endpoints as required.</span></span> <span data-ttu-id="28629-167">Ponieważ określone zachowanie być skonfigurowana tutaj implementuje <xref:System.ServiceModel.Description.IEndpointBehavior>, jest on prawidłowy tylko w sekcji odpowiednich konfiguracji w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="28629-167">Because the particular behavior to be configured here implements <xref:System.ServiceModel.Description.IEndpointBehavior>, it is only valid in the respective configuration section in the configuration file.</span></span>  
  
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
  
 <span data-ttu-id="28629-168">`<schemaValidator>` Element, który konfiguruje inspektora wiadomości nie jest obsługiwana przez `SchemaValidationBehaviorExtensionElement` klasy.</span><span class="sxs-lookup"><span data-stu-id="28629-168">The `<schemaValidator>` element that configures the message inspector is backed by the `SchemaValidationBehaviorExtensionElement` class.</span></span> <span data-ttu-id="28629-169">Klasa udostępnia dwa logiczną właściwości publicznej o nazwie `ValidateRequest` i `ValidateReply`.</span><span class="sxs-lookup"><span data-stu-id="28629-169">The class exposes two Boolean public properties named `ValidateRequest` and `ValidateReply`.</span></span> <span data-ttu-id="28629-170">Oba te są oznaczone ikoną z <xref:System.Configuration.ConfigurationPropertyAttribute>.</span><span class="sxs-lookup"><span data-stu-id="28629-170">Both of these are marked with a <xref:System.Configuration.ConfigurationPropertyAttribute>.</span></span> <span data-ttu-id="28629-171">Ten atrybut stanowi połączenie między właściwości kodu i atrybutów XML, które będą widoczne na poprzedni element XML w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="28629-171">This attribute constitutes the link between the code properties and the XML attributes that can be seen on the preceding XML configuration element.</span></span> <span data-ttu-id="28629-172">Klasa ma także właściwością `Schemas` który również jest oznaczony atrybutem <xref:System.Configuration.ConfigurationCollectionAttribute> i jest typu `SchemaCollection`, która jest również częścią tego przykładu, ale został pominięty z tego dokumentu do skrócenia.</span><span class="sxs-lookup"><span data-stu-id="28629-172">The class also has a property `Schemas` that is additionally marked with the <xref:System.Configuration.ConfigurationCollectionAttribute> and is of the type `SchemaCollection`, which is also part of this sample but omitted from this document for brevity.</span></span> <span data-ttu-id="28629-173">Tej właściwości wraz z kolekcji i klasa elementu kolekcji `SchemaConfigElement` kopie `<schemas>` elementu w poprzednim fragment konfiguracji i umożliwia dodawanie kolekcji schematów w zestawie sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="28629-173">This property along with the collection and the collection element class `SchemaConfigElement` backs the `<schemas>` element in the preceding configuration snippet and allows adding a collection of schemas to the validation set.</span></span>  
  
 <span data-ttu-id="28629-174">Zastąpione `CreateBehavior` — metoda powoduje dane konfiguracyjne do obiektu zachowania podczas środowiska uruchomieniowego ocenia dane konfiguracji, jak zbudował klienta lub punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="28629-174">The overridden `CreateBehavior` method turns the configuration data into a behavior object when the runtime evaluates the configuration data as it builds a client or an endpoint.</span></span>  
  
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
  
## <a name="adding-message-inspectors-imperatively"></a><span data-ttu-id="28629-175">Dodawanie Imperatively inspektorzy komunikatów</span><span class="sxs-lookup"><span data-stu-id="28629-175">Adding Message Inspectors Imperatively</span></span>  
 <span data-ttu-id="28629-176">Z wyjątkiem za pomocą atrybutów (które z powodu odnosiło się do wcześniej nie jest obsługiwana w tym przykładzie) i konfigurację, można dodać do obsługi klienta i usługi, przy użyciu kodu imperatywnych dość łatwe zachowania.</span><span class="sxs-lookup"><span data-stu-id="28629-176">Except through attributes (which is not supported in this sample for the reason cited previously) and configuration, behaviors can quite easily be added to a client and service runtime using imperative code.</span></span> <span data-ttu-id="28629-177">W tym przykładzie jest to realizowane w aplikacji klienckiej, aby przetestować inspektora komunikat klienta.</span><span class="sxs-lookup"><span data-stu-id="28629-177">In this sample, this is done in the client application to test the client message inspector.</span></span> <span data-ttu-id="28629-178">`GenericClient` Jest pochodną klasy <xref:System.ServiceModel.ClientBase%601>, który udostępnia konfigurację punktu końcowego do kodu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="28629-178">The `GenericClient` class is derived from <xref:System.ServiceModel.ClientBase%601>, which exposes the endpoint configuration to the user code.</span></span> <span data-ttu-id="28629-179">Przed otwarciem niejawnie klienta konfiguracji punktu końcowego można zmienić, na przykład przez dodanie zachowania, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="28629-179">Before the client is implicitly opened the endpoint configuration can be changed, for instance by adding behaviors as shown in the following code.</span></span> <span data-ttu-id="28629-180">Dodanie zachowania usługi jest odpowiednikiem przede wszystkim technika klienta pokazane i musi zostać wykonana przed otwarciem hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="28629-180">Adding the behavior on the service is largely equivalent to the client technique shown here and must be performed before the service host is opened.</span></span>  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="28629-181">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="28629-181">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="28629-182">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="28629-182">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="28629-183">Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="28629-183">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="28629-184">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="28629-184">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="28629-185">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="28629-185">The samples may already be installed on your machine.</span></span> <span data-ttu-id="28629-186">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="28629-186">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="28629-187">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="28629-187">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="28629-188">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="28629-188">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageInspectors`  
  
## <a name="see-also"></a><span data-ttu-id="28629-189">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="28629-189">See Also</span></span>
