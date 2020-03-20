---
title: Wysyłanie według elementu treści
ms.date: 03/30/2017
ms.assetid: f64a3c04-62b4-47b2-91d9-747a3af1659f
ms.openlocfilehash: 754151f856dfe09b8fd12912ab06d1d8720be016
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183713"
---
# <a name="dispatch-by-body-element"></a><span data-ttu-id="6804f-102">Wysyłanie według elementu treści</span><span class="sxs-lookup"><span data-stu-id="6804f-102">Dispatch by Body Element</span></span>
<span data-ttu-id="6804f-103">W tym przykładzie pokazano, jak zaimplementować alternatywny algorytm przypisywania wiadomości przychodzących do operacji.</span><span class="sxs-lookup"><span data-stu-id="6804f-103">This sample demonstrates how to implement an alternate algorithm for assigning incoming messages to operations.</span></span>  
  
 <span data-ttu-id="6804f-104">Domyślnie dyspozytor modelu usługi wybiera odpowiednią metodę obsługi wiadomości przychodzącej na podstawie nagłówka "Akcja" adresowania WS wiadomości lub równoważnych informacji w żądaniu PROTOKOŁU HTTP SOAP.</span><span class="sxs-lookup"><span data-stu-id="6804f-104">By default, the service model dispatcher selects the appropriate handling method for an incoming message based on the message's WS-Addressing "Action" header or the equivalent information in the HTTP SOAP request.</span></span>  
  
 <span data-ttu-id="6804f-105">Niektóre stosy usług sieci Web protokołu SOAP 1.1, które nie są zgodne z wytycznymi WS-I Basic Profile 1.1, nie wysyłają komunikatów opartych na identyfikatorze URI akcji, ale raczej na podstawie kwalifikowanej nazwy XML pierwszego elementu wewnątrz treści PROTOKOŁU SOAP.</span><span class="sxs-lookup"><span data-stu-id="6804f-105">Some SOAP 1.1 Web services stacks that do not follow the WS-I Basic Profile 1.1 guidelines do not dispatch messages based on the Action URI, but rather based on the XML qualified name of the first element inside the SOAP body.</span></span> <span data-ttu-id="6804f-106">Podobnie po stronie klienta tych stosów może wysyłać wiadomości z pustym lub dowolnego nagłówka HTTP SoapAction, co było dozwolone przez protokół SOAP 1.1 specyfikacji.</span><span class="sxs-lookup"><span data-stu-id="6804f-106">Likewise, the client side of these stacks might send messages with an empty or arbitrary HTTP SoapAction header, which was permitted by the SOAP 1.1 specification.</span></span>  
  
 <span data-ttu-id="6804f-107">Aby zmienić sposób wysyłania wiadomości do metod, <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> w przykładzie `DispatchByBodyElementOperationSelector`implementuje interfejs rozszerzalności w programie .</span><span class="sxs-lookup"><span data-stu-id="6804f-107">To change the way messages are dispatched to methods, the sample implements the <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> extensibility interface on the `DispatchByBodyElementOperationSelector`.</span></span> <span data-ttu-id="6804f-108">Ta klasa wybiera operacje na podstawie pierwszego elementu treści wiadomości.</span><span class="sxs-lookup"><span data-stu-id="6804f-108">This class selects operations based on the first element of the message body.</span></span>  
  
 <span data-ttu-id="6804f-109">Konstruktor klasy oczekuje słownika wypełnione `XmlQualifiedName` parami i ciągami, przy czym nazwy kwalifikowane wskazują nazwę pierwszego rodu podrzędnego treści SOAP, a ciągi wskazują pasującą nazwę operacji.</span><span class="sxs-lookup"><span data-stu-id="6804f-109">The class constructor expects a dictionary populated with pairs of `XmlQualifiedName` and strings, whereby the qualified names indicate the name of the first child of the SOAP body and the strings indicate the matching operation name.</span></span> <span data-ttu-id="6804f-110">Jest `defaultOperationName` to nazwa operacji, która odbiera wszystkie komunikaty, które nie mogą być dopasowane do tego słownika:</span><span class="sxs-lookup"><span data-stu-id="6804f-110">The `defaultOperationName` is the name of the operation that receives all messages that cannot be matched against this dictionary:</span></span>  
  
```csharp
class DispatchByBodyElementOperationSelector : IDispatchOperationSelector  
{  
    Dictionary<XmlQualifiedName, string> dispatchDictionary;  
    string defaultOperationName;  
  
    public DispatchByBodyElementOperationSelector(Dictionary<XmlQualifiedName,string> dispatchDictionary, string defaultOperationName)  
    {  
        this.dispatchDictionary = dispatchDictionary;  
        this.defaultOperationName = defaultOperationName;  
    }  
}
```  
  
 <span data-ttu-id="6804f-111"><xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector>implementacje są bardzo proste do zbudowania, ponieważ <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A>istnieje tylko jedna metoda na interfejsie: .</span><span class="sxs-lookup"><span data-stu-id="6804f-111"><xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementations are very straightforward to build as there is only one method on the interface: <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A>.</span></span> <span data-ttu-id="6804f-112">Zadaniem tej metody jest sprawdzenie wiadomości przychodzącej i zwrócenie ciągu, który jest równy nazwie metody w umowie serwisowej dla bieżącego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="6804f-112">The job of this method is to inspect an incoming message and to return a string that equals the name of a method on the service contract for the current endpoint.</span></span>  
  
 <span data-ttu-id="6804f-113">W tym przykładzie selektor operacji <xref:System.Xml.XmlDictionaryReader> uzyskuje dla treści wiadomości <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>przychodzącej przy użyciu .</span><span class="sxs-lookup"><span data-stu-id="6804f-113">In this sample, the operation selector acquires an <xref:System.Xml.XmlDictionaryReader> for the incoming message's body using <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>.</span></span> <span data-ttu-id="6804f-114">Ta metoda już umieszcza czytnik na pierwszym elemencie treści wiadomości, dzięki czemu jest wystarczająca, aby uzyskać nazwę `XmlQualifiedName` bieżącego elementu i identyfikator URI obszaru nazw i połączyć je w, który jest następnie używany do wyszukania odpowiedniej operacji ze słownika przechowywanego przez selektor operacji.</span><span class="sxs-lookup"><span data-stu-id="6804f-114">This method already positions the reader on the first child of the message's body so that it is sufficient to get the current element's name and namespace URI and combine them into an `XmlQualifiedName` that is then used for looking up the corresponding operation from the dictionary held by the operation selector.</span></span>  
  
```csharp
public string SelectOperation(ref System.ServiceModel.Channels.Message message)  
{  
    XmlDictionaryReader bodyReader = message.GetReaderAtBodyContents();  
    XmlQualifiedName lookupQName = new  
       XmlQualifiedName(bodyReader.LocalName, bodyReader.NamespaceURI);  
    message = CreateMessageCopy(message,bodyReader);  
    if (dispatchDictionary.ContainsKey(lookupQName))  
    {  
         return dispatchDictionary[lookupQName];  
    }  
    else  
    {  
        return defaultOperationName;  
    }  
}  
```  
  
 <span data-ttu-id="6804f-115">Uzyskiwanie dostępu do <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> treści wiadomości za pomocą lub dowolnej innej metody, które zapewniają dostęp do zawartości treści wiadomości powoduje, że wiadomość jest oznaczona jako "odczyt", co oznacza, że wiadomość jest nieprawidłowa do dalszego przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="6804f-115">Accessing the message body with <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> or any of the other methods that provide access to the message's body content causes the message to be marked as "read", which means that the message is invalid for any further processing.</span></span> <span data-ttu-id="6804f-116">W związku z tym selektor operacji tworzy kopię wiadomości przychodzącej z metodą pokazaną w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="6804f-116">Therefore, the operation selector creates a copy of the incoming message with the method shown in the following code.</span></span> <span data-ttu-id="6804f-117">Ponieważ pozycja czytelnika nie została zmieniona podczas inspekcji, może się do niego odwoływać nowo utworzona wiadomość, do której są również kopiowane właściwości wiadomości i nagłówki wiadomości, co skutkuje dokładnym klonem oryginalnej wiadomości:</span><span class="sxs-lookup"><span data-stu-id="6804f-117">Because the reader's position has not been changed during the inspection, it can be referenced by the newly created message to which the message properties and the message headers are also copied, which results in an exact clone of the original message:</span></span>  
  
```csharp
private Message CreateMessageCopy(Message message,
                                     XmlDictionaryReader body)  
{  
    Message copy = Message.CreateMessage(message.Version,message.Headers.Action,body);  
    copy.Headers.CopyHeaderFrom(message,0);  
    copy.Properties.CopyProperties(message.Properties);  
    return copy;  
}  
```  
  
## <a name="adding-an-operation-selector-to-a-service"></a><span data-ttu-id="6804f-118">Dodawanie selektora operacji do usługi</span><span class="sxs-lookup"><span data-stu-id="6804f-118">Adding an Operation Selector to a Service</span></span>  
 <span data-ttu-id="6804f-119">Selektory operacji wysyłki usługi są rozszerzeniami dyspozytora Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="6804f-119">Service dispatch operation selectors are extensions to the Windows Communication Foundation (WCF) dispatcher.</span></span> <span data-ttu-id="6804f-120">W celu wybrania metod w kanale wywołania zwrotnego kontraktów dupleksu istnieją również selektory operacji klienta, które działają bardzo podobnie do selektorów operacji wysyłki opisanych w tym miejscu, ale które nie są wyraźnie uwzględnione w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="6804f-120">For selecting methods on the callback channel of duplex contracts, there are also client operation selectors, which work very much like the dispatch operation selectors described here, but which are not explicitly covered in this sample.</span></span>  
  
 <span data-ttu-id="6804f-121">Podobnie jak większość rozszerzeń modelu usługi, selektory operacji wysyłki są dodawane do dyspozytora przy użyciu zachowań.</span><span class="sxs-lookup"><span data-stu-id="6804f-121">Like most service model extensions, dispatch operation selectors are added to the dispatcher using behaviors.</span></span> <span data-ttu-id="6804f-122">*Zachowanie* jest obiekt konfiguracji, który dodaje jedno lub więcej rozszerzeń do środowiska wykonawczego wysyłki (lub do środowiska wykonawczego klienta) lub w inny sposób zmienia jego ustawienia.</span><span class="sxs-lookup"><span data-stu-id="6804f-122">A *behavior* is a configuration object, which either adds one or more extensions to the dispatch runtime (or to the client runtime) or otherwise changes its settings.</span></span>  
  
 <span data-ttu-id="6804f-123">Ponieważ selektory operacji mają zakres kontraktu, odpowiednie <xref:System.ServiceModel.Description.IContractBehavior>zachowanie do zaimplementowania w tym miejscu jest .</span><span class="sxs-lookup"><span data-stu-id="6804f-123">Because operation selectors have contract scope, the appropriate behavior to implement here is the <xref:System.ServiceModel.Description.IContractBehavior>.</span></span> <span data-ttu-id="6804f-124">Ponieważ interfejs jest implementowany <xref:System.Attribute> w klasie pochodnej, jak pokazano w poniższym kodzie, zachowanie może być deklaratywnie dodane do każdej umowy serwisowej.</span><span class="sxs-lookup"><span data-stu-id="6804f-124">Because the interface is implemented on a <xref:System.Attribute> derived class as shown in the following code, the behavior can be declaratively added to any service contract.</span></span> <span data-ttu-id="6804f-125">Za każdym <xref:System.ServiceModel.ServiceHost> razem, gdy a jest otwarty i środowisko uruchomieniowe wysyłki jest zbudowany, wszystkie zachowania znalezione jako atrybuty w kontraktach, operacji i implementacji usługi lub jako element w konfiguracji usługi są automatycznie dodawane, a następnie proszone o współtworzenie rozszerzeń lub zmodyfikować domyślną konfigurację.</span><span class="sxs-lookup"><span data-stu-id="6804f-125">Whenever a <xref:System.ServiceModel.ServiceHost> is opened and the dispatch runtime is built, all behaviors found either as attributes on contracts, operations, and service implementations or as element in the service configuration are automatically added and subsequently asked to contribute extensions or modify the default configuration.</span></span>  
  
 <span data-ttu-id="6804f-126">Dla zwięzłości poniższy fragment kodu <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A>pokazuje tylko implementację metody , która wpływa na zmiany konfiguracji dla dyspozytora w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="6804f-126">For brevity, the following code excerpt only shows the implementation of the method <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A>, which effects the configuration changes for the dispatcher in this sample.</span></span> <span data-ttu-id="6804f-127">Inne metody nie są wyświetlane, ponieważ powrót do obiektu wywołującego bez wykonywania jakiejkolwiek pracy.</span><span class="sxs-lookup"><span data-stu-id="6804f-127">The other methods are not shown because they return to the caller without doing any work.</span></span>  
  
```csharp
[AttributeUsage(AttributeTargets.Class|AttributeTargets.Interface)]  
class DispatchByBodyElementBehaviorAttribute : Attribute, IContractBehavior  
{  
    // public void AddBindingParameters(...)
    // public void ApplyClientBehavior(...)  
    // public void Validate(...)  
```  
  
 <span data-ttu-id="6804f-128">Po pierwsze <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> implementacja konfiguruje słownik wyszukiwania dla selektora operacji <xref:System.ServiceModel.Description.OperationDescription> przez iterację nad <xref:System.ServiceModel.Description.ContractDescription>elementami w punkcie końcowym usługi .</span><span class="sxs-lookup"><span data-stu-id="6804f-128">First, the <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> implementation sets up the lookup dictionary for the operation selector by iterating over the <xref:System.ServiceModel.Description.OperationDescription> elements in the service endpoint's <xref:System.ServiceModel.Description.ContractDescription>.</span></span> <span data-ttu-id="6804f-129">Następnie każdy opis operacji jest sprawdzany `DispatchBodyElementAttribute` pod kątem obecności <xref:System.ServiceModel.Description.IOperationBehavior> zachowania, implementacja, która jest również zdefiniowana w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="6804f-129">Then, each operation description is inspected for the presence of the `DispatchBodyElementAttribute` behavior, an implementation of <xref:System.ServiceModel.Description.IOperationBehavior> that is also defined in this sample.</span></span> <span data-ttu-id="6804f-130">Chociaż ta klasa jest również zachowanie, jest pasywny i nie aktywnie przyczyniają się do żadnych zmian konfiguracji do środowiska wykonawczego wysyłki.</span><span class="sxs-lookup"><span data-stu-id="6804f-130">While this class is also a behavior, it is passive and does not actively contribute any configuration changes to the dispatch runtime.</span></span> <span data-ttu-id="6804f-131">Wszystkie jego metody powrócić do wywołującego bez podejmowania żadnych działań.</span><span class="sxs-lookup"><span data-stu-id="6804f-131">All of its methods return to the caller without taking any actions.</span></span> <span data-ttu-id="6804f-132">Zachowanie operacji istnieje tylko tak, że metadane wymagane dla nowego mechanizmu wysyłki, a mianowicie kwalifikowana nazwa elementu treści, na którego wystąpienie jest zaznaczona operacja, mogą być skojarzone z odpowiednich operacji.</span><span class="sxs-lookup"><span data-stu-id="6804f-132">The operation behavior only exists so that the metadata required for the new dispatch mechanism, namely the qualified name of the body element on whose occurrence an operation is selected, can be associated with the respective operations.</span></span>  
  
 <span data-ttu-id="6804f-133">Jeśli takie zachowanie zostanie znalezione, do słownika zostanie`QName` dodana para wartości`Name` utworzona na podstawie kwalifikowanej nazwy XML (właściwości) i nazwy operacji ( właściwości).</span><span class="sxs-lookup"><span data-stu-id="6804f-133">If such a behavior is found, a value pair created from the XML qualified name (`QName` property) and the operation name (`Name` property) is added to the dictionary.</span></span>  
  
 <span data-ttu-id="6804f-134">Po wypełnieniu słownika, `DispatchByBodyElementOperationSelector` nowy jest konstruowany z tymi informacjami i ustawiony jako selektor operacji środowiska wykonawczego wysyłki:</span><span class="sxs-lookup"><span data-stu-id="6804f-134">Once the dictionary is populated, a new `DispatchByBodyElementOperationSelector` is constructed with this information and set as the operation selector of the dispatch runtime:</span></span>  
  
```csharp
public void ApplyDispatchBehavior(ContractDescription contractDescription, ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.DispatchRuntime dispatchRuntime)  
{  
    Dictionary<XmlQualifiedName,string> dispatchDictionary =
                     new Dictionary<XmlQualifiedName,string>();  
    foreach( OperationDescription operationDescription in
                              contractDescription.Operations )  
    {  
        DispatchBodyElementAttribute dispatchBodyElement =
   operationDescription.Behaviors.Find<DispatchBodyElementAttribute>();  
        if ( dispatchBodyElement != null )  
        {  
             dispatchDictionary.Add(dispatchBodyElement.QName,
                              operationDescription.Name);  
        }  
    }  
    dispatchRuntime.OperationSelector =
            new DispatchByBodyElementOperationSelector(  
               dispatchDictionary,
               dispatchRuntime.UnhandledDispatchOperation.Name);  
    }  
}  
```  
  
## <a name="implementing-the-service"></a><span data-ttu-id="6804f-135">Wdrażanie usługi</span><span class="sxs-lookup"><span data-stu-id="6804f-135">Implementing the Service</span></span>  
 <span data-ttu-id="6804f-136">Zachowanie zaimplementowane w tym przykładzie bezpośrednio wpływa na sposób interpretowania i wysyłania wiadomości z przewodu, co jest funkcją umowy serwisowej.</span><span class="sxs-lookup"><span data-stu-id="6804f-136">The behavior implemented in this sample directly affects how messages from the wire are interpreted and dispatched, which is a function of the service contract.</span></span> <span data-ttu-id="6804f-137">W związku z tym zachowanie powinno być zadeklarowane na poziomie umowy serwisowej w dowolnej implementacji usługi, która zdecyduje się go używać.</span><span class="sxs-lookup"><span data-stu-id="6804f-137">Consequently, the behavior should be declared on the service contract level in any service implementation that chooses to use it.</span></span>  
  
 <span data-ttu-id="6804f-138">Przykładowa usługa projektu `DispatchByBodyElementBehaviorAttribute` stosuje zachowanie `IDispatchedByBody` kontraktu do umowy serwisowej `OperationForBodyA()` `OperationForBodyB()` i `DispatchBodyElementAttribute` etykietuje każdą z dwóch operacji i z zachowaniem operacji.</span><span class="sxs-lookup"><span data-stu-id="6804f-138">The sample project service applies the `DispatchByBodyElementBehaviorAttribute` contract behavior to the `IDispatchedByBody` service contract and labels each of the two operations `OperationForBodyA()` and `OperationForBodyB()` with a `DispatchBodyElementAttribute` operation behavior.</span></span> <span data-ttu-id="6804f-139">Po otwarciu hosta usługi dla usługi implementacji tej umowy, metadane są pobierane przez konstruktora dyspozytora, jak opisano wcześniej.</span><span class="sxs-lookup"><span data-stu-id="6804f-139">When a service host for a service that implements this contract is opened, this metadata is picked up by the dispatcher builder as previously described.</span></span>  
  
 <span data-ttu-id="6804f-140">Ponieważ selektor operacji wywołuje wyłącznie na podstawie elementu treści wiadomości i ignoruje "Akcję", należy poinformować środowisko wykonawcze, aby nie sprawdzał nagłówka "Akcja" w `ReplyAction` zwróconych odpowiedziach, przypisując symbol wieloznaczny "\*" do właściwości <xref:System.ServiceModel.OperationContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="6804f-140">Because the operation selector dispatches solely based on the message body element and ignores the "Action", it is required to tell the runtime not to check the "Action" header on the returned replies by assigning the wildcard "\*" to the `ReplyAction` property of <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="6804f-141">Ponadto wymagane jest, aby mieć domyślną operację, która ma "Action"\*właściwość ustawiona na symbol wieloznaczny " ".</span><span class="sxs-lookup"><span data-stu-id="6804f-141">Furthermore, it is required to have a default operation that has the "Action" property set to the wildcard "\*".</span></span> <span data-ttu-id="6804f-142">Domyślna operacja odbiera wszystkie komunikaty, których nie `DispatchBodyElementAttribute`można wysłać i nie ma:</span><span class="sxs-lookup"><span data-stu-id="6804f-142">The default operation receives all messages which cannot be dispatched and does not have a `DispatchBodyElementAttribute`:</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples"),  
                            DispatchByBodyElementBehavior]  
public interface IDispatchedByBody  
{  
    [OperationContract(ReplyAction="*"),
     DispatchBodyElement("bodyA","http://tempuri.org")]  
    Message OperationForBodyA(Message msg);  
    [OperationContract(ReplyAction = "*"),
     DispatchBodyElement("bodyB", "http://tempuri.org")]  
    Message OperationForBodyB(Message msg);  
    [OperationContract(Action="*", ReplyAction="*")]  
    Message DefaultOperation(Message msg);  
}  
```  
  
 <span data-ttu-id="6804f-143">Implementacja przykładowej usługi jest prosta.</span><span class="sxs-lookup"><span data-stu-id="6804f-143">The sample service implementation is straightforward.</span></span> <span data-ttu-id="6804f-144">Każda metoda zawija odebraną wiadomość do wiadomości odpowiedzi i powtarza ją z powrotem do klienta.</span><span class="sxs-lookup"><span data-stu-id="6804f-144">Every method wraps the received message into a reply message and echoes it back to the client.</span></span>  
  
## <a name="running-and-building-the-sample"></a><span data-ttu-id="6804f-145">Uruchamianie i tworzenie próbki</span><span class="sxs-lookup"><span data-stu-id="6804f-145">Running and Building the Sample</span></span>  
 <span data-ttu-id="6804f-146">Po uruchomieniu próbki zawartość treści odpowiedzi operacji są wyświetlane w oknie konsoli klienta podobne do następujących (sformatowany) dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="6804f-146">When you run the sample, the body content of the operation responses are displayed in the client console window similar to the following (formatted) output.</span></span>  
  
 <span data-ttu-id="6804f-147">Klient wysyła trzy komunikaty do usługi, `bodyA`której `bodyB`element `bodyX`zawartości treści jest nazwany , i , odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="6804f-147">The client sends three messages to the service whose body content element is named `bodyA`, `bodyB`, and `bodyX`, respectively.</span></span> <span data-ttu-id="6804f-148">Jak można odroczyć z poprzedniego opisu i umowy serwisowej pokazano, przychodzące wiadomości z elementem `bodyA` jest wywoływana do `OperationForBodyA()` metody.</span><span class="sxs-lookup"><span data-stu-id="6804f-148">As can be deferred from the previous description and the service contract shown, the incoming message with the `bodyA` element is dispatched to the `OperationForBodyA()` method.</span></span> <span data-ttu-id="6804f-149">Ponieważ nie ma jawnego obiektu docelowego wysyłki dla wiadomości z `bodyX` `DefaultOperation()`elementem treści, wiadomość jest wysyłana do .</span><span class="sxs-lookup"><span data-stu-id="6804f-149">Because there is no explicit dispatch target for the message with the `bodyX` body element, the message is dispatched to the `DefaultOperation()`.</span></span> <span data-ttu-id="6804f-150">Każda z operacji usługi zawija treść odebranej wiadomości do elementu specyficznego dla metody i zwraca go, co odbywa się w celu wyraźnego skorelowania komunikatów wejściowych i wyjściowych dla tego przykładu:</span><span class="sxs-lookup"><span data-stu-id="6804f-150">Each of the service operations wraps the received message body into an element specific to the method and returns it, which is done to correlate input and output messages clearly for this sample:</span></span>  
  
```xml  
<?xml version="1.0" encoding="IBM437"?>  
<replyBodyA xmlns="http://tempuri.org">  
   <q:bodyA xmlns:q="http://tempuri.org">test</q:bodyA>  
</replyBodyA>  
<?xml version="1.0" encoding="IBM437"?>  
<replyBodyB xmlns="http://tempuri.org">  
  <q:bodyB xmlns:q="http://tempuri.org">test</q:bodyB>  
</replyBodyB>  
<?xml version="1.0" encoding="IBM437"?>  
<replyDefault xmlns="http://tempuri.org">  
   <q:bodyX xmlns:q="http://tempuri.org">test</q:bodyX>  
</replyDefault>  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6804f-151">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="6804f-151">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="6804f-152">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6804f-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="6804f-153">Aby utworzyć rozwiązanie, postępuj zgodnie z instrukcjami w [tworzeniu przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6804f-153">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="6804f-154">Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6804f-154">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="6804f-155">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="6804f-155">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6804f-156">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="6804f-156">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="6804f-157">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="6804f-157">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6804f-158">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="6804f-158">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\AdvancedDispatchByBody`  
