---
title: Inspektorzy komunikatów
ms.date: 03/30/2017
ms.assetid: 9bd1f305-ad03-4dd7-971f-fa1014b97c9b
ms.openlocfilehash: 1a5519e815a6714e087a77c69e943a3a8c65db68
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84585081"
---
# <a name="message-inspectors"></a><span data-ttu-id="1d69d-102">Inspektorzy komunikatów</span><span class="sxs-lookup"><span data-stu-id="1d69d-102">Message Inspectors</span></span>
<span data-ttu-id="1d69d-103">W tym przykładzie przedstawiono sposób wdrażania i konfigurowania inspektorów komunikatów klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="1d69d-103">This sample demonstrates how to implement and configure client and service message inspectors.</span></span>  
  
 <span data-ttu-id="1d69d-104">Inspektor komunikatów jest obiektem rozszerzalności, który może być używany w środowisku uruchomieniowym klienta i w środowisku uruchomieniowym w ramach usługi lub przez konfigurację oraz który może sprawdzać i modyfikować komunikaty po ich otrzymaniu lub przed wysłaniem.</span><span class="sxs-lookup"><span data-stu-id="1d69d-104">A message inspector is an extensibility object that can be used in the service model's client runtime and dispatch runtime programmatically or through configuration and that can inspect and alter messages after they are received or before they are sent.</span></span>  
  
 <span data-ttu-id="1d69d-105">Ten przykład służy do implementowania podstawowego mechanizmu sprawdzania poprawności komunikatów klienta i usługi, który weryfikuje komunikaty przychodzące względem zestawu konfigurowalnych dokumentów schematu XML.</span><span class="sxs-lookup"><span data-stu-id="1d69d-105">This sample implements a basic client and service message validation mechanism that validates incoming messages against a set of configurable XML Schema documents.</span></span> <span data-ttu-id="1d69d-106">Należy zauważyć, że ten przykład nie sprawdza poprawności komunikatów dla każdej operacji.</span><span class="sxs-lookup"><span data-stu-id="1d69d-106">Note that this sample does not validate messages for each operation.</span></span> <span data-ttu-id="1d69d-107">Jest to celowe uproszczenie.</span><span class="sxs-lookup"><span data-stu-id="1d69d-107">This is an intentional simplification.</span></span>  
  
## <a name="message-inspector"></a><span data-ttu-id="1d69d-108">Inspektor komunikatów</span><span class="sxs-lookup"><span data-stu-id="1d69d-108">Message Inspector</span></span>  
 <span data-ttu-id="1d69d-109">Inspektorzy komunikatów klienta implementują interfejs <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> i inspektorzy komunikatów usługi implementujący <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> interfejs.</span><span class="sxs-lookup"><span data-stu-id="1d69d-109">Client message inspectors implement the <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> interface and service message inspectors implement the <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> interface.</span></span> <span data-ttu-id="1d69d-110">Implementacje mogą być połączone w jedną klasę, aby utworzyć inspektora komunikatów, który działa po obu stronach.</span><span class="sxs-lookup"><span data-stu-id="1d69d-110">The implementations can be combined into a single class to form a message inspector that works for both sides.</span></span> <span data-ttu-id="1d69d-111">Ten przykład implementuje ten połączony Inspektor komunikatów.</span><span class="sxs-lookup"><span data-stu-id="1d69d-111">This sample implements such a combined message inspector.</span></span> <span data-ttu-id="1d69d-112">Inspektor jest zbudowany w zestawie schematów, do których są sprawdzane komunikaty przychodzące i wychodzące, i umożliwia deweloperom określenie, czy wiadomości przychodzące lub wychodzące są weryfikowane oraz czy inspektor znajduje się w trybie wysyłania lub klienta, co ma wpływ na obsługę błędów, jak opisano w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="1d69d-112">The inspector is constructed passing in a set of schemas against which incoming and outgoing messages are validated and allows the developer to specify whether incoming or outgoing messages are validated and whether the inspector is in dispatch or client mode, which affects the error handling as discussed later in this topic.</span></span>  
  
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
  
 <span data-ttu-id="1d69d-113">Każdy inspektor komunikatów usługi (dyspozytora) musi zaimplementować dwie <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> metody <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> i <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29> .</span><span class="sxs-lookup"><span data-stu-id="1d69d-113">Any service (dispatcher) message inspector must implement the two <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> methods <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> and <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>.</span></span>  
  
 <span data-ttu-id="1d69d-114"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>jest wywoływany przez dyspozytora, gdy otrzyma komunikat, przetworzony przez stos kanału i przypisany do usługi, ale zanim zostanie on rozszeregowany i wysłany do operacji.</span><span class="sxs-lookup"><span data-stu-id="1d69d-114"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> is invoked by the dispatcher when a message has been received, processed by the channel stack and assigned to a service, but before it is deserialized and dispatched to an operation.</span></span> <span data-ttu-id="1d69d-115">Jeśli komunikat przychodzący został zaszyfrowany, komunikat jest już odszyfrowany, gdy dociera do Inspektora komunikatów.</span><span class="sxs-lookup"><span data-stu-id="1d69d-115">If the incoming message was encrypted, the message is already decrypted when it reaches the message inspector.</span></span> <span data-ttu-id="1d69d-116">Metoda pobiera `request` komunikat przekazaną jako parametr odwołania, który umożliwia kontrolowanie, manipulowanie lub zamienienie komunikatu jako wymagane.</span><span class="sxs-lookup"><span data-stu-id="1d69d-116">The method gets the `request` message passed as a reference parameter, which allows the message to be inspected, manipulated or replaced as required.</span></span> <span data-ttu-id="1d69d-117">Wartością zwracaną może być dowolny obiekt i jest używany jako obiekt stanu korelacji, który jest przesyłany do <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> momentu, gdy usługa zwróci odpowiedź na bieżącą wiadomość.</span><span class="sxs-lookup"><span data-stu-id="1d69d-117">The return value can be any object and is used as a correlation state object that is passed to <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> when the service returns a reply to the current message.</span></span> <span data-ttu-id="1d69d-118">W tym przykładzie <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> deleguje inspekcję (walidację) wiadomości do prywatnej, lokalnej metody `ValidateMessageBody` i nie zwraca obiektu stanu korelacji.</span><span class="sxs-lookup"><span data-stu-id="1d69d-118">In this sample, <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> delegates the inspection (validation) of the message to the private, local method `ValidateMessageBody` and returns no correlation state object.</span></span> <span data-ttu-id="1d69d-119">Ta metoda zapewnia, że żadne nieprawidłowe komunikaty nie są przekazywane do usługi.</span><span class="sxs-lookup"><span data-stu-id="1d69d-119">This method ensures that no invalid messages pass into the service.</span></span>  
  
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
  
 <span data-ttu-id="1d69d-120"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>jest wywoływana za każdym razem, gdy odpowiedź jest gotowa do wysłania do klienta lub w przypadku komunikatów jednokierunkowych, gdy komunikat przychodzący został przetworzony.</span><span class="sxs-lookup"><span data-stu-id="1d69d-120"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29> is invoked whenever a reply is ready to be sent back to a client, or in the case of one-way messages, when the incoming message has been processed.</span></span> <span data-ttu-id="1d69d-121">Pozwala to na stosowanie rozszerzeń w sposób symetryczny, niezależnie od unikatowy MEP.</span><span class="sxs-lookup"><span data-stu-id="1d69d-121">This allows extensions to count on being called symmetrically, regardless of MEP.</span></span> <span data-ttu-id="1d69d-122">Podobnie jak w przypadku <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> , komunikat jest przenoszona jako parametr odwołania i może być sprawdzany, modyfikowany lub zastępowany.</span><span class="sxs-lookup"><span data-stu-id="1d69d-122">As with <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, the message is passed as a reference parameter and can be inspected, modified or replaced.</span></span> <span data-ttu-id="1d69d-123">Sprawdzanie poprawności komunikatu, który jest wykonywany w tym przykładzie, jest ponownie delegowane do `ValidMessageBody` metody, ale obsługa błędów walidacji jest nieco inna w tym przypadku.</span><span class="sxs-lookup"><span data-stu-id="1d69d-123">The validation of the message that is performed in this sample is again delegated to the `ValidMessageBody` method, but the handling of validation errors is slightly different in this case.</span></span>  
  
 <span data-ttu-id="1d69d-124">Jeśli w usłudze wystąpi błąd walidacji, `ValidateMessageBody` Metoda zgłasza <xref:System.ServiceModel.FaultException> wyjątek pochodne.</span><span class="sxs-lookup"><span data-stu-id="1d69d-124">If a validation error occurs on the service, the `ValidateMessageBody` method throws <xref:System.ServiceModel.FaultException>-derived exceptions.</span></span> <span data-ttu-id="1d69d-125">W programie <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> te wyjątki można umieścić w infrastrukturze modelu usług, gdzie są one automatycznie przekształcane w błędy protokołu SOAP i przekazywane do klienta.</span><span class="sxs-lookup"><span data-stu-id="1d69d-125">In <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, these exceptions can be put into the service model infrastructure where they are automatically transformed into SOAP faults and relayed to the client.</span></span> <span data-ttu-id="1d69d-126">W <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> programie <xref:System.ServiceModel.FaultException> wyjątki nie mogą być umieszczane w infrastrukturze, ponieważ przekształcenie wyjątków błędów zgłaszanych przez usługę występuje przed wywołaniem inspektora komunikatów.</span><span class="sxs-lookup"><span data-stu-id="1d69d-126">In <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A>, <xref:System.ServiceModel.FaultException> exceptions must not be put into the infrastructure, because the transformation of fault exceptions thrown by the service occurs before the message inspector is called.</span></span> <span data-ttu-id="1d69d-127">W związku z tym Następująca implementacja przechwytuje znany `ReplyValidationFault` wyjątek i zastępuje komunikat odpowiedzi z jawnym komunikatem o błędzie.</span><span class="sxs-lookup"><span data-stu-id="1d69d-127">Therefore the following implementation catches the known `ReplyValidationFault` exception and replaces the reply message with an explicit fault message.</span></span> <span data-ttu-id="1d69d-128">Dzięki tej metodzie implementacja usługi nie zwraca żadnych nieprawidłowych komunikatów.</span><span class="sxs-lookup"><span data-stu-id="1d69d-128">This method ensures that no invalid messages are returned by the service implementation.</span></span>  
  
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
  
 <span data-ttu-id="1d69d-129">Inspektor komunikatów klienta jest bardzo podobny.</span><span class="sxs-lookup"><span data-stu-id="1d69d-129">The client message inspector is very similar.</span></span> <span data-ttu-id="1d69d-130">Dwie metody, które muszą być zaimplementowane z <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> programu <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.AfterReceiveReply%2A> , to i <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> .</span><span class="sxs-lookup"><span data-stu-id="1d69d-130">The two methods that must be implemented from <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> are <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.AfterReceiveReply%2A> and <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>.</span></span>  
  
 <span data-ttu-id="1d69d-131"><xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>jest wywoływany, gdy wiadomość została złożona przez aplikację kliencką lub przez program formatujący operacji.</span><span class="sxs-lookup"><span data-stu-id="1d69d-131"><xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> is invoked when the message has been composed either by the client application or by the operation formatter.</span></span> <span data-ttu-id="1d69d-132">Podobnie jak w przypadku inspektorów komunikatów dyspozytora, komunikat można tylko sprawdzić lub całkowicie zastąpić.</span><span class="sxs-lookup"><span data-stu-id="1d69d-132">As with the dispatcher message inspectors, the message can just be inspected or entirely replaced.</span></span> <span data-ttu-id="1d69d-133">W tym przykładzie Inspektor delegowany do tej samej lokalnej `ValidateMessageBody` metody pomocnika, która również jest używana dla inspektorów komunikatów wysyłania.</span><span class="sxs-lookup"><span data-stu-id="1d69d-133">In this sample, the inspector delegates to the same local `ValidateMessageBody` helper method that is also used for the dispatch message inspectors.</span></span>  
  
 <span data-ttu-id="1d69d-134">Różnica w zachowaniu między walidacją klienta i usługi (zgodnie z definicją w konstruktorze) polega na tym, że Walidacja klienta zgłasza wyjątki lokalne, które są umieszczane w kodzie użytkownika, ponieważ są one wykonywane lokalnie, a nie z powodu błędu usługi.</span><span class="sxs-lookup"><span data-stu-id="1d69d-134">The behavioral difference between the client and service validation (as specified in the constructor) is that the client validation throws local exceptions that are put into the user code because they occur locally and not because of a service failure.</span></span> <span data-ttu-id="1d69d-135">Ogólnie rzecz biorąc, reguła jest taka, że inspektorzy dyspozytorów usługi zgłaszają błędy i inspektorzy klienta zgłaszają wyjątki.</span><span class="sxs-lookup"><span data-stu-id="1d69d-135">Generally, the rule is that service dispatcher inspectors throw faults and that client inspectors throw exceptions.</span></span>  
  
 <span data-ttu-id="1d69d-136">Ta <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> implementacja zapewnia, że do usługi nie są wysyłane żadne nieprawidłowe komunikaty.</span><span class="sxs-lookup"><span data-stu-id="1d69d-136">This <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> implementation ensures that no invalid messages are sent to the service.</span></span>  
  
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
  
 <span data-ttu-id="1d69d-137">`AfterReceiveReply`Implementacja gwarantuje, że żadne nieprawidłowe komunikaty odebrane z usługi nie są przekazywane do kodu użytkownika klienta.</span><span class="sxs-lookup"><span data-stu-id="1d69d-137">The `AfterReceiveReply` implementation ensures that no invalid messages received from the service are relayed to the client user code.</span></span>  
  
```csharp  
void IClientMessageInspector.AfterReceiveReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
{  
    if (validateReply)  
    {  
        ValidateMessageBody(ref reply, false);  
    }  
}  
```  
  
 <span data-ttu-id="1d69d-138">Tym konkretnym inspektorem komunikatów jest ta `ValidateMessageBody` Metoda.</span><span class="sxs-lookup"><span data-stu-id="1d69d-138">The heart of this particular message inspector is the `ValidateMessageBody` method.</span></span> <span data-ttu-id="1d69d-139">Aby można było wykonać swoją prace, zawija ona walidację <xref:System.Xml.XmlReader> wokół poddrzewa zawartości komunikatu o przekazaniu.</span><span class="sxs-lookup"><span data-stu-id="1d69d-139">To perform its work, it wraps a validating <xref:System.Xml.XmlReader> around the body content sub-tree of the passed message.</span></span> <span data-ttu-id="1d69d-140">Czytnik jest wypełniany zestawem schematów, które znajdują się w Inspektorze komunikatów, a wywołanie zwrotne walidacji jest ustawiane jako delegat odwołujący się do elementu `InspectionValidationHandler` , który jest zdefiniowany obok tej metody.</span><span class="sxs-lookup"><span data-stu-id="1d69d-140">The reader is populated with the set of schemas that the message inspector holds and the validation callback is set to a delegate referring to the `InspectionValidationHandler` that is defined alongside this method.</span></span> <span data-ttu-id="1d69d-141">W celu przeprowadzenia walidacji wiadomość jest odczytywana i buforowana w strumieniu pamięci <xref:System.Xml.XmlDictionaryWriter> .</span><span class="sxs-lookup"><span data-stu-id="1d69d-141">To perform the validation, the message is then read and spooled into a memory stream-backed <xref:System.Xml.XmlDictionaryWriter>.</span></span> <span data-ttu-id="1d69d-142">Jeśli w procesie wystąpi błąd lub ostrzeżenie z walidacją, wywoływana jest metoda wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="1d69d-142">If a validation error or warning occurs in the process, the callback method is invoked.</span></span>  
  
 <span data-ttu-id="1d69d-143">Jeśli wystąpi błąd, tworzony jest nowy komunikat, który kopiuje właściwości i nagłówki z oryginalnej wiadomości i używa teraz zweryfikowanych sprawdzonych w strumieniu pamięci, które są opakowane przez <xref:System.Xml.XmlDictionaryReader> i dodawane do komunikatu zastępczego.</span><span class="sxs-lookup"><span data-stu-id="1d69d-143">If no error occurs, a new message is constructed that copies the properties and headers from the original message and uses the now-validated infoset in the memory stream, which is wrapped by an <xref:System.Xml.XmlDictionaryReader> and added to the replacement message.</span></span>  
  
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
  
 <span data-ttu-id="1d69d-144">`InspectionValidationHandler`Metoda jest wywoływana przez walidację za <xref:System.Xml.XmlReader> każdym razem, gdy wystąpi błąd walidacji schematu lub ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="1d69d-144">The `InspectionValidationHandler` method is called by the validating <xref:System.Xml.XmlReader> whenever a schema validation error or warning occurs.</span></span> <span data-ttu-id="1d69d-145">Następująca implementacja działa tylko z błędami i ignoruje wszystkie ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="1d69d-145">The following implementation only works with errors and ignores all warnings.</span></span>  
  
 <span data-ttu-id="1d69d-146">Przy pierwszym rozważaniu może być możliwe wstrzyknięcie walidacji <xref:System.Xml.XmlReader> komunikatu za pomocą Inspektora komunikatów i przeprowadzenie walidacji, gdy komunikat jest przetwarzany i bez buforowania komunikatu.</span><span class="sxs-lookup"><span data-stu-id="1d69d-146">On first consideration, it might seem possible to inject a validating <xref:System.Xml.XmlReader> into the message with the message inspector and let the validation happen as the message is processed and without buffering the message.</span></span> <span data-ttu-id="1d69d-147">Oznacza to jednak, że to wywołanie zwrotne zgłasza wyjątki walidacji w infrastrukturze modelu usług lub w kodzie użytkownika, ponieważ wykryto nieprawidłowe węzły XML, co skutkuje nieprzewidywalnym zachowaniem.</span><span class="sxs-lookup"><span data-stu-id="1d69d-147">That, however, means that this callback throws the validation exceptions somewhere into the service model infrastructure or the user code as invalid XML nodes are detected, resulting in unpredictable behavior.</span></span> <span data-ttu-id="1d69d-148">Metoda buforowania umożliwia ochronę kodu użytkownika przed nieprawidłowymi komunikatami.</span><span class="sxs-lookup"><span data-stu-id="1d69d-148">The buffering approach shields the user code from invalid messages, entirely.</span></span>  
  
 <span data-ttu-id="1d69d-149">Jak wspomniano wcześniej, wyjątki zgłoszone przez program obsługi różnią się między klientem a usługą.</span><span class="sxs-lookup"><span data-stu-id="1d69d-149">As previously discussed, the exceptions thrown by the handler differ between the client and the service.</span></span> <span data-ttu-id="1d69d-150">W usłudze wyjątki są wyprowadzane z programu <xref:System.ServiceModel.FaultException> , na kliencie są to regularne wyjątki niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="1d69d-150">On the service, the exceptions are derived from <xref:System.ServiceModel.FaultException>, on the client the exceptions are regular custom exceptions.</span></span>  
  
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
  
## <a name="behavior"></a><span data-ttu-id="1d69d-151">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="1d69d-151">Behavior</span></span>  
 <span data-ttu-id="1d69d-152">Inspektorzy komunikatów są rozszerzeniami środowiska uruchomieniowego klienta lub środowiska uruchomieniowego wysyłania.</span><span class="sxs-lookup"><span data-stu-id="1d69d-152">Message inspectors are extensions to the client runtime or the dispatch runtime.</span></span> <span data-ttu-id="1d69d-153">Takie rozszerzenia są konfigurowane przy użyciu *zachowań*.</span><span class="sxs-lookup"><span data-stu-id="1d69d-153">Such extensions are configured using *behaviors*.</span></span> <span data-ttu-id="1d69d-154">Zachowanie jest klasą, która zmienia zachowanie środowiska uruchomieniowego modelu usług, zmieniając domyślną konfigurację lub dodając do niej rozszerzenia (na przykład inspektorów komunikatów).</span><span class="sxs-lookup"><span data-stu-id="1d69d-154">A behavior is a class that changes the behavior of the service model runtime by changing the default configuration or adding extensions (such as message inspectors) to it.</span></span>  
  
 <span data-ttu-id="1d69d-155">Następująca `SchemaValidationBehavior` Klasa jest zachowaniem używanym do dodawania tego przykładowego inspektora komunikatów do klienta lub środowiska uruchomieniowego wysyłania.</span><span class="sxs-lookup"><span data-stu-id="1d69d-155">The following `SchemaValidationBehavior` class is the behavior used to add this sample's message inspector to the client or dispatch runtime.</span></span> <span data-ttu-id="1d69d-156">Implementacja jest raczej podstawowa w obu przypadkach.</span><span class="sxs-lookup"><span data-stu-id="1d69d-156">The implementation is rather basic in both cases.</span></span> <span data-ttu-id="1d69d-157">W programie <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyClientBehavior%2A> i <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyDispatchBehavior%2A> , inspektor komunikatów jest tworzony i dodawany do <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> kolekcji odpowiedniego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="1d69d-157">In <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyClientBehavior%2A> and <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyDispatchBehavior%2A>, the message inspector is created and added to the <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> collection of the respective runtime.</span></span>  
  
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
> <span data-ttu-id="1d69d-158">To konkretne zachowanie nie jest podwójne jako atrybut i dlatego nie można go dodać deklaratywnie do typu kontraktu typu usługi.</span><span class="sxs-lookup"><span data-stu-id="1d69d-158">This particular behavior does not double as an attribute and therefore cannot be added declaratively onto a contract type of a service type.</span></span> <span data-ttu-id="1d69d-159">Jest to podjęcie decyzji o projekcie, ponieważ kolekcja schematów nie może zostać załadowana w deklaracji atrybutu i odwołująca się do dodatkowej lokalizacji konfiguracji (na przykład ustawienia aplikacji) w tym atrybucie oznacza tworzenie elementu konfiguracji, który nie jest spójny z resztą konfiguracji modelu usług.</span><span class="sxs-lookup"><span data-stu-id="1d69d-159">This is a by-design decision made because the schema collection cannot be loaded in an attribute declaration and referring to an extra configuration location (for instance to the application settings) in this attribute means creating a configuration element that is not consistent with the rest of the service model configuration.</span></span> <span data-ttu-id="1d69d-160">W związku z tym takie zachowanie można dodać wyłącznie za pomocą kodu i rozszerzenia konfiguracji modelu usług.</span><span class="sxs-lookup"><span data-stu-id="1d69d-160">Therefore, this behavior can only be added imperatively through code and through a service model configuration extension.</span></span>  
  
## <a name="adding-the-message-inspector-through-configuration"></a><span data-ttu-id="1d69d-161">Dodawanie inspektora komunikatów za pomocą konfiguracji</span><span class="sxs-lookup"><span data-stu-id="1d69d-161">Adding the Message Inspector through Configuration</span></span>  
 <span data-ttu-id="1d69d-162">W przypadku konfigurowania zachowania niestandardowego w punkcie końcowym w pliku konfiguracji aplikacji model usługi wymaga realizatorów do utworzenia *elementu rozszerzenia* konfiguracji reprezentowanego przez klasę pochodną <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> .</span><span class="sxs-lookup"><span data-stu-id="1d69d-162">For configuring a custom behavior on an endpoint in the application configuration file, the service model requires implementers to create a configuration *extension element* represented by a class derived from <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>.</span></span> <span data-ttu-id="1d69d-163">To rozszerzenie należy dodać do sekcji konfiguracyjnej modelu usługi dla rozszerzeń, jak pokazano na poniższym rozszerzeniu opisanym w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="1d69d-163">This extension must then be added to the service model's configuration section for extensions as shown for the following extension discussed in this section.</span></span>  
  
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
  
 <span data-ttu-id="1d69d-164">Rozszerzenia można dodać w pliku konfiguracji aplikacji lub ASP.NET, który jest najbardziej typowym wyborem lub w pliku konfiguracyjnym komputera.</span><span class="sxs-lookup"><span data-stu-id="1d69d-164">Extensions can be added in the application or ASP.NET configuration file, which is the most common choice, or in the machine configuration file.</span></span>  
  
 <span data-ttu-id="1d69d-165">Po dodaniu rozszerzenia do zakresu konfiguracji zachowanie można dodać do konfiguracji zachowania, tak jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="1d69d-165">When the extension is added to a configuration scope, the behavior can be added to a behavior configuration as it is shown in the following code.</span></span> <span data-ttu-id="1d69d-166">Konfiguracje zachowań są elementami wielokrotnego użytku, które można zastosować do wielu punktów końcowych zgodnie z wymaganiami.</span><span class="sxs-lookup"><span data-stu-id="1d69d-166">Behavior configurations are reusable elements that can be applied to multiple endpoints as required.</span></span> <span data-ttu-id="1d69d-167">Ponieważ określone zachowanie należy skonfigurować w tym miejscu <xref:System.ServiceModel.Description.IEndpointBehavior> , jest ono prawidłowe tylko w odpowiedniej sekcji konfiguracji w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="1d69d-167">Because the particular behavior to be configured here implements <xref:System.ServiceModel.Description.IEndpointBehavior>, it is only valid in the respective configuration section in the configuration file.</span></span>  
  
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
  
 <span data-ttu-id="1d69d-168">`<schemaValidator>`Element, który konfiguruje inspektora komunikatów, jest obsługiwany przez `SchemaValidationBehaviorExtensionElement` klasę.</span><span class="sxs-lookup"><span data-stu-id="1d69d-168">The `<schemaValidator>` element that configures the message inspector is backed by the `SchemaValidationBehaviorExtensionElement` class.</span></span> <span data-ttu-id="1d69d-169">Klasa uwidacznia dwie właściwości publiczne Boolean o nazwie `ValidateRequest` i `ValidateReply` .</span><span class="sxs-lookup"><span data-stu-id="1d69d-169">The class exposes two Boolean public properties named `ValidateRequest` and `ValidateReply`.</span></span> <span data-ttu-id="1d69d-170">Oba te elementy są oznaczone symbolem <xref:System.Configuration.ConfigurationPropertyAttribute> .</span><span class="sxs-lookup"><span data-stu-id="1d69d-170">Both of these are marked with a <xref:System.Configuration.ConfigurationPropertyAttribute>.</span></span> <span data-ttu-id="1d69d-171">Ten atrybut stanowi połączenie między właściwościami kodu i atrybutami XML, które mogą być widoczne w poprzednim elemencie konfiguracji XML.</span><span class="sxs-lookup"><span data-stu-id="1d69d-171">This attribute constitutes the link between the code properties and the XML attributes that can be seen on the preceding XML configuration element.</span></span> <span data-ttu-id="1d69d-172">Klasa ma również właściwość `Schemas` , która jest dodatkowo oznaczona przy użyciu <xref:System.Configuration.ConfigurationCollectionAttribute> i jest typu `SchemaCollection` , który jest również częścią tego przykładu, ale został pominięty w tym dokumencie dla zwięzłości.</span><span class="sxs-lookup"><span data-stu-id="1d69d-172">The class also has a property `Schemas` that is additionally marked with the <xref:System.Configuration.ConfigurationCollectionAttribute> and is of the type `SchemaCollection`, which is also part of this sample but omitted from this document for brevity.</span></span> <span data-ttu-id="1d69d-173">Ta właściwość wraz z kolekcją i klasą elementów kolekcji `SchemaConfigElement` wykonuje kopię zapasową `<schemas>` elementu w poprzednim fragmencie konfiguracji i umożliwia dodanie kolekcji schematów do zestawu walidacji.</span><span class="sxs-lookup"><span data-stu-id="1d69d-173">This property along with the collection and the collection element class `SchemaConfigElement` backs the `<schemas>` element in the preceding configuration snippet and allows adding a collection of schemas to the validation set.</span></span>  
  
 <span data-ttu-id="1d69d-174">Zastąpiona `CreateBehavior` Metoda przekształca dane konfiguracji w obiekt zachowań, gdy środowisko uruchomieniowe szacuje dane konfiguracyjne w miarę kompilowania klienta lub punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="1d69d-174">The overridden `CreateBehavior` method turns the configuration data into a behavior object when the runtime evaluates the configuration data as it builds a client or an endpoint.</span></span>  
  
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
  
## <a name="adding-message-inspectors-imperatively"></a><span data-ttu-id="1d69d-175">Bezwzględne Dodawanie inspektorów komunikatów</span><span class="sxs-lookup"><span data-stu-id="1d69d-175">Adding Message Inspectors Imperatively</span></span>  
 <span data-ttu-id="1d69d-176">Oprócz atrybutów, które nie są obsługiwane w tym przykładzie z powodu podanej wcześniej przyczyny) i konfiguracji, zachowania można łatwo dodać do środowiska uruchomieniowego klienta i usługi przy użyciu własnego kodu.</span><span class="sxs-lookup"><span data-stu-id="1d69d-176">Except through attributes (which is not supported in this sample for the reason cited previously) and configuration, behaviors can quite easily be added to a client and service runtime using imperative code.</span></span> <span data-ttu-id="1d69d-177">W tym przykładzie jest to wykonywane w aplikacji klienckiej w celu przetestowania inspektora komunikatów klienta.</span><span class="sxs-lookup"><span data-stu-id="1d69d-177">In this sample, this is done in the client application to test the client message inspector.</span></span> <span data-ttu-id="1d69d-178">`GenericClient`Klasa pochodzi od <xref:System.ServiceModel.ClientBase%601> , która uwidacznia konfigurację punktu końcowego w kodzie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="1d69d-178">The `GenericClient` class is derived from <xref:System.ServiceModel.ClientBase%601>, which exposes the endpoint configuration to the user code.</span></span> <span data-ttu-id="1d69d-179">Przed niejawnie otwartym klientem można zmienić konfigurację punktu końcowego, na przykład przez dodanie zachowań, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="1d69d-179">Before the client is implicitly opened the endpoint configuration can be changed, for instance by adding behaviors as shown in the following code.</span></span> <span data-ttu-id="1d69d-180">Dodanie zachowania usługi jest w dużym stopniu odpowiednikiem techniki klienta pokazanej w tym miejscu i musi zostać wykonane przed otwarciem hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="1d69d-180">Adding the behavior on the service is largely equivalent to the client technique shown here and must be performed before the service host is opened.</span></span>  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1d69d-181">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="1d69d-181">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="1d69d-182">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1d69d-182">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="1d69d-183">Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1d69d-183">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="1d69d-184">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1d69d-184">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1d69d-185">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="1d69d-185">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1d69d-186">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="1d69d-186">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="1d69d-187">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="1d69d-187">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1d69d-188">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="1d69d-188">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageInspectors`  
