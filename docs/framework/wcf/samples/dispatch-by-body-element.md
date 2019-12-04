---
title: Wysyłanie według elementu treści
ms.date: 03/30/2017
ms.assetid: f64a3c04-62b4-47b2-91d9-747a3af1659f
ms.openlocfilehash: 307d6bbbab118392ef079942eae367a4c6792c22
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74712030"
---
# <a name="dispatch-by-body-element"></a><span data-ttu-id="1bbfe-102">Wysyłanie według elementu treści</span><span class="sxs-lookup"><span data-stu-id="1bbfe-102">Dispatch by Body Element</span></span>
<span data-ttu-id="1bbfe-103">Ten przykład pokazuje, jak zaimplementować alternatywny algorytm przypisywania komunikatów przychodzących do operacji.</span><span class="sxs-lookup"><span data-stu-id="1bbfe-103">This sample demonstrates how to implement an alternate algorithm for assigning incoming messages to operations.</span></span>  
  
 <span data-ttu-id="1bbfe-104">Domyślnie Dyspozytor modelu usług wybiera odpowiednią metodę obsługi dla komunikatu przychodzącego na podstawie nagłówka "Akcja" WS-Addressing "lub równoważne informacje w żądaniu protokołu HTTP SOAP.</span><span class="sxs-lookup"><span data-stu-id="1bbfe-104">By default, the service model dispatcher selects the appropriate handling method for an incoming message based on the message's WS-Addressing "Action" header or the equivalent information in the HTTP SOAP request.</span></span>  
  
 <span data-ttu-id="1bbfe-105">Niektóre stosy usług sieci Web SOAP 1,1, które nie są zgodne z wytycznymi dotyczącymi profilu WS-I Basic 1,1 nie wysyłają komunikatów na podstawie identyfikatora URI akcji, ale raczej na podstawie kwalifikowanej nazwy XML pierwszego elementu wewnątrz treści protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="1bbfe-105">Some SOAP 1.1 Web services stacks that do not follow the WS-I Basic Profile 1.1 guidelines do not dispatch messages based on the Action URI, but rather based on the XML qualified name of the first element inside the SOAP body.</span></span> <span data-ttu-id="1bbfe-106">Podobnie po stronie klienta te stosy mogą wysyłać komunikaty z pustym lub dowolnym nagłówkiem HTTP SoapAction, który był dozwolony przez specyfikację protokołu SOAP 1,1.</span><span class="sxs-lookup"><span data-stu-id="1bbfe-106">Likewise, the client side of these stacks might send messages with an empty or arbitrary HTTP SoapAction header, which was permitted by the SOAP 1.1 specification.</span></span>  
  
 <span data-ttu-id="1bbfe-107">Aby zmienić sposób wysyłania komunikatów do metod, przykład implementuje interfejs rozszerzalności <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> na `DispatchByBodyElementOperationSelector`.</span><span class="sxs-lookup"><span data-stu-id="1bbfe-107">To change the way messages are dispatched to methods, the sample implements the <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> extensibility interface on the `DispatchByBodyElementOperationSelector`.</span></span> <span data-ttu-id="1bbfe-108">Ta klasa wybiera operacje na podstawie pierwszego elementu treści komunikatu.</span><span class="sxs-lookup"><span data-stu-id="1bbfe-108">This class selects operations based on the first element of the message body.</span></span>  
  
 <span data-ttu-id="1bbfe-109">Konstruktor klasy oczekuje słownika wypełnionego parami `XmlQualifiedName` i ciągów, według których kwalifikowane nazwy wskazują nazwę pierwszego elementu podrzędnego treści protokołu SOAP, a ciągi wskazują pasującą nazwę operacji.</span><span class="sxs-lookup"><span data-stu-id="1bbfe-109">The class constructor expects a dictionary populated with pairs of `XmlQualifiedName` and strings, whereby the qualified names indicate the name of the first child of the SOAP body and the strings indicate the matching operation name.</span></span> <span data-ttu-id="1bbfe-110">`defaultOperationName` to nazwa operacji, która odbiera wszystkie komunikaty, które nie mogą być dopasowane do tego słownika:</span><span class="sxs-lookup"><span data-stu-id="1bbfe-110">The `defaultOperationName` is the name of the operation that receives all messages that cannot be matched against this dictionary:</span></span>  
  
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
  
 <span data-ttu-id="1bbfe-111">implementacje <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> są bardzo proste dla kompilacji, ponieważ istnieje tylko jedna metoda w interfejsie: <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A>.</span><span class="sxs-lookup"><span data-stu-id="1bbfe-111"><xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementations are very straightforward to build as there is only one method on the interface: <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A>.</span></span> <span data-ttu-id="1bbfe-112">Zadaniem tej metody jest zbadanie komunikatu przychodzącego i zwrócenie ciągu, który jest równy nazwie metody w kontrakcie usługi dla bieżącego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="1bbfe-112">The job of this method is to inspect an incoming message and to return a string that equals the name of a method on the service contract for the current endpoint.</span></span>  
  
 <span data-ttu-id="1bbfe-113">W tym przykładzie selektor operacji uzyskuje <xref:System.Xml.XmlDictionaryReader> treści wiadomości przychodzącej przy użyciu <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>.</span><span class="sxs-lookup"><span data-stu-id="1bbfe-113">In this sample, the operation selector acquires an <xref:System.Xml.XmlDictionaryReader> for the incoming message's body using <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>.</span></span> <span data-ttu-id="1bbfe-114">Ta metoda już umieszcza czytnik w pierwszym elemencie podrzędnym treści wiadomości, dzięki czemu można uzyskać nazwę bieżącego elementu i identyfikator URI przestrzeni nazw, a następnie połączyć je w `XmlQualifiedName`, które są następnie używane do wyszukiwania odpowiedniej operacji ze słownika przechowywanego przez selektor operacji.</span><span class="sxs-lookup"><span data-stu-id="1bbfe-114">This method already positions the reader on the first child of the message's body so that it is sufficient to get the current element's name and namespace URI and combine them into an `XmlQualifiedName` that is then used for looking up the corresponding operation from the dictionary held by the operation selector.</span></span>  
  
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
  
 <span data-ttu-id="1bbfe-115">Uzyskiwanie dostępu do treści wiadomości za pomocą <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> lub dowolnej z innych metod zapewniających dostęp do zawartości treści wiadomości powoduje, że komunikat zostanie oznaczony jako "read" (odczyt), co oznacza, że komunikat jest nieprawidłowy do dalszej obróbki.</span><span class="sxs-lookup"><span data-stu-id="1bbfe-115">Accessing the message body with <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> or any of the other methods that provide access to the message's body content causes the message to be marked as "read", which means that the message is invalid for any further processing.</span></span> <span data-ttu-id="1bbfe-116">W związku z tym selektor operacji tworzy kopię komunikatu przychodzącego za pomocą metody pokazanej w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="1bbfe-116">Therefore, the operation selector creates a copy of the incoming message with the method shown in the following code.</span></span> <span data-ttu-id="1bbfe-117">Ponieważ pozycja czytnika nie została zmieniona podczas inspekcji, może odwoływać się do nowo utworzonego komunikatu, do którego są również kopiowane właściwości wiadomości i nagłówki wiadomości, co powoduje dokładne klonowanie oryginalnej wiadomości:</span><span class="sxs-lookup"><span data-stu-id="1bbfe-117">Because the reader's position has not been changed during the inspection, it can be referenced by the newly created message to which the message properties and the message headers are also copied, which results in an exact clone of the original message:</span></span>  
  
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
  
## <a name="adding-an-operation-selector-to-a-service"></a><span data-ttu-id="1bbfe-118">Dodawanie selektora operacji do usługi</span><span class="sxs-lookup"><span data-stu-id="1bbfe-118">Adding an Operation Selector to a Service</span></span>  
 <span data-ttu-id="1bbfe-119">Selektory operacji wysyłania usług są rozszerzeniami do dyspozytora Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="1bbfe-119">Service dispatch operation selectors are extensions to the Windows Communication Foundation (WCF) dispatcher.</span></span> <span data-ttu-id="1bbfe-120">W przypadku wybierania metod w kanale wywołania zwrotnego w ramach kontraktów dupleksowych istnieją również selektory operacji klienta, które działają bardzo podobnie do selektorów operacji wysyłania opisanych tutaj, ale które nie zostały jawnie omówione w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="1bbfe-120">For selecting methods on the callback channel of duplex contracts, there are also client operation selectors, which work very much like the dispatch operation selectors described here, but which are not explicitly covered in this sample.</span></span>  
  
 <span data-ttu-id="1bbfe-121">Takie jak większość rozszerzeń modelu usług, selektory operacji wysyłania są dodawane do dyspozytora przy użyciu zachowań.</span><span class="sxs-lookup"><span data-stu-id="1bbfe-121">Like most service model extensions, dispatch operation selectors are added to the dispatcher using behaviors.</span></span> <span data-ttu-id="1bbfe-122">*Zachowanie* jest obiektem konfiguracji, który dodaje jeden lub więcej rozszerzeń do środowiska uruchomieniowego wysyłania (lub do środowiska uruchomieniowego klienta) lub w inny sposób zmienia jego ustawienia.</span><span class="sxs-lookup"><span data-stu-id="1bbfe-122">A *behavior* is a configuration object, which either adds one or more extensions to the dispatch runtime (or to the client runtime) or otherwise changes its settings.</span></span>  
  
 <span data-ttu-id="1bbfe-123">Ponieważ selektory operacji mają zakres kontraktu, odpowiednie zachowanie w celu zaimplementowania jest <xref:System.ServiceModel.Description.IContractBehavior>.</span><span class="sxs-lookup"><span data-stu-id="1bbfe-123">Because operation selectors have contract scope, the appropriate behavior to implement here is the <xref:System.ServiceModel.Description.IContractBehavior>.</span></span> <span data-ttu-id="1bbfe-124">Ponieważ interfejs jest zaimplementowany na <xref:System.Attribute> klasie pochodnej, jak pokazano w poniższym kodzie, zachowanie można deklaratywnie dodać do dowolnego kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="1bbfe-124">Because the interface is implemented on a <xref:System.Attribute> derived class as shown in the following code, the behavior can be declaratively added to any service contract.</span></span> <span data-ttu-id="1bbfe-125">Za każdym razem, gdy <xref:System.ServiceModel.ServiceHost> jest otwarty, a środowisko uruchomieniowe wysyłania zostało skompilowane, wszystkie zachowania, które znajdują się w ramach kontraktów, operacji i implementacji usług lub jako element w konfiguracji usługi są automatycznie dodawane, a następnie proszeni do współtworzenia rozszerzeń lub modyfikowania konfiguracji domyślnej.</span><span class="sxs-lookup"><span data-stu-id="1bbfe-125">Whenever a <xref:System.ServiceModel.ServiceHost> is opened and the dispatch runtime is built, all behaviors found either as attributes on contracts, operations, and service implementations or as element in the service configuration are automatically added and subsequently asked to contribute extensions or modify the default configuration.</span></span>  
  
 <span data-ttu-id="1bbfe-126">W przypadku zwięzłości Poniższy fragment kodu zawiera tylko implementację metody <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A>, co wpływa na zmiany konfiguracji dyspozytora w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="1bbfe-126">For brevity, the following code excerpt only shows the implementation of the method <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A>, which effects the configuration changes for the dispatcher in this sample.</span></span> <span data-ttu-id="1bbfe-127">Inne metody nie są wyświetlane, ponieważ zwracają do obiektu wywołującego bez wykonywania żadnej pracy.</span><span class="sxs-lookup"><span data-stu-id="1bbfe-127">The other methods are not shown because they return to the caller without doing any work.</span></span>  
  
```csharp
[AttributeUsage(AttributeTargets.Class|AttributeTargets.Interface)]  
class DispatchByBodyElementBehaviorAttribute : Attribute, IContractBehavior  
{  
    // public void AddBindingParameters(...)   
    // public void ApplyClientBehavior(...)  
    // public void Validate(...)  
```  
  
 <span data-ttu-id="1bbfe-128">Najpierw implementacja <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> ustawia słownik wyszukiwania dla selektora operacji poprzez iterację elementów <xref:System.ServiceModel.Description.OperationDescription> w <xref:System.ServiceModel.Description.ContractDescription>punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="1bbfe-128">First, the <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> implementation sets up the lookup dictionary for the operation selector by iterating over the <xref:System.ServiceModel.Description.OperationDescription> elements in the service endpoint's <xref:System.ServiceModel.Description.ContractDescription>.</span></span> <span data-ttu-id="1bbfe-129">Następnie każdy opis operacji jest sprawdzany pod kątem obecności `DispatchBodyElementAttribute`, implementacja <xref:System.ServiceModel.Description.IOperationBehavior>, która jest również zdefiniowana w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="1bbfe-129">Then, each operation description is inspected for the presence of the `DispatchBodyElementAttribute` behavior, an implementation of <xref:System.ServiceModel.Description.IOperationBehavior> that is also defined in this sample.</span></span> <span data-ttu-id="1bbfe-130">Chociaż ta klasa jest również zachowaniem, jest pasywna i nie wprowadza żadnych zmian w konfiguracji w czasie wykonywania wysyłania.</span><span class="sxs-lookup"><span data-stu-id="1bbfe-130">While this class is also a behavior, it is passive and does not actively contribute any configuration changes to the dispatch runtime.</span></span> <span data-ttu-id="1bbfe-131">Wszystkie jego metody zwracają do obiektu wywołującego bez podejmowania żadnych działań.</span><span class="sxs-lookup"><span data-stu-id="1bbfe-131">All of its methods return to the caller without taking any actions.</span></span> <span data-ttu-id="1bbfe-132">Zachowanie tej operacji istnieje tylko wtedy, gdy metadane wymagane dla nowego mechanizmu wysyłania, czyli kwalifikowana nazwa elementu treści, dla którego wystąpienie operacji jest zaznaczone, mogą być skojarzone z odpowiednimi operacjami.</span><span class="sxs-lookup"><span data-stu-id="1bbfe-132">The operation behavior only exists so that the metadata required for the new dispatch mechanism, namely the qualified name of the body element on whose occurrence an operation is selected, can be associated with the respective operations.</span></span>  
  
 <span data-ttu-id="1bbfe-133">Jeśli takie zachowanie zostanie znalezione, para wartości utworzona na podstawie kwalifikowanej nazwy XML (Właściwość`QName`) i nazwy operacji (Właściwość`Name`) zostanie dodana do słownika.</span><span class="sxs-lookup"><span data-stu-id="1bbfe-133">If such a behavior is found, a value pair created from the XML qualified name (`QName` property) and the operation name (`Name` property) is added to the dictionary.</span></span>  
  
 <span data-ttu-id="1bbfe-134">Po wypełnieniu słownika zostanie utworzony nowy `DispatchByBodyElementOperationSelector` z tymi informacjami i ustawiony jako selektor operacji dla środowiska uruchomieniowego wysyłania:</span><span class="sxs-lookup"><span data-stu-id="1bbfe-134">Once the dictionary is populated, a new `DispatchByBodyElementOperationSelector` is constructed with this information and set as the operation selector of the dispatch runtime:</span></span>  
  
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
  
## <a name="implementing-the-service"></a><span data-ttu-id="1bbfe-135">Implementowanie usługi</span><span class="sxs-lookup"><span data-stu-id="1bbfe-135">Implementing the Service</span></span>  
 <span data-ttu-id="1bbfe-136">Zachowanie zaimplementowane w tym przykładzie bezpośrednio wpływa na sposób interpretowania i wysyłania komunikatów z sieci, która jest funkcją kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="1bbfe-136">The behavior implemented in this sample directly affects how messages from the wire are interpreted and dispatched, which is a function of the service contract.</span></span> <span data-ttu-id="1bbfe-137">W związku z tym zachowanie powinno być zadeklarowane na poziomie kontraktu usługi w każdej implementacji usługi, która wybierze jej użycie.</span><span class="sxs-lookup"><span data-stu-id="1bbfe-137">Consequently, the behavior should be declared on the service contract level in any service implementation that chooses to use it.</span></span>  
  
 <span data-ttu-id="1bbfe-138">Przykładowa usługa projektu stosuje zachowanie `DispatchByBodyElementBehaviorAttribute` umowy do kontraktu usługi `IDispatchedByBody` i etykiety każdej z dwóch operacji `OperationForBodyA()` i `OperationForBodyB()` z zachowaniem `DispatchBodyElementAttribute` operacji.</span><span class="sxs-lookup"><span data-stu-id="1bbfe-138">The sample project service applies the `DispatchByBodyElementBehaviorAttribute` contract behavior to the `IDispatchedByBody` service contract and labels each of the two operations `OperationForBodyA()` and `OperationForBodyB()` with a `DispatchBodyElementAttribute` operation behavior.</span></span> <span data-ttu-id="1bbfe-139">W przypadku otwarcia hosta usługi dla usługi implementującej ten kontrakt te metadane są pobierane przez konstruktora dyspozytora zgodnie z wcześniejszym opisem.</span><span class="sxs-lookup"><span data-stu-id="1bbfe-139">When a service host for a service that implements this contract is opened, this metadata is picked up by the dispatcher builder as previously described.</span></span>  
  
 <span data-ttu-id="1bbfe-140">Ponieważ selektor operacji jest wysyłany wyłącznie na podstawie treści wiadomości i ignoruje "działanie", jest wymagane, aby poinformować środowisko uruchomieniowe, aby nie sprawdzać nagłówka "Action" na zwracanych odpowiedzi, przypisując symbol wieloznaczny "\*" do właściwości `ReplyAction` <xref:System.ServiceModel.OperationContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="1bbfe-140">Because the operation selector dispatches solely based on the message body element and ignores the "Action", it is required to tell the runtime not to check the "Action" header on the returned replies by assigning the wildcard "\*" to the `ReplyAction` property of <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="1bbfe-141">Ponadto wymagane jest posiadanie domyślnej operacji, która ma właściwość "Action" ustawioną na symbol wieloznaczny "\*".</span><span class="sxs-lookup"><span data-stu-id="1bbfe-141">Furthermore, it is required to have a default operation that has the "Action" property set to the wildcard "\*".</span></span> <span data-ttu-id="1bbfe-142">Operacja domyślna odbiera wszystkie komunikaty, których nie można wysłać, i nie ma `DispatchBodyElementAttribute`:</span><span class="sxs-lookup"><span data-stu-id="1bbfe-142">The default operation receives all messages which cannot be dispatched and does not have a `DispatchBodyElementAttribute`:</span></span>  
  
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
  
 <span data-ttu-id="1bbfe-143">Przykładowa implementacja usługi jest prosta.</span><span class="sxs-lookup"><span data-stu-id="1bbfe-143">The sample service implementation is straightforward.</span></span> <span data-ttu-id="1bbfe-144">Każda metoda zawija odebrany komunikat do komunikatu odpowiedzi i odsyła go z powrotem do klienta.</span><span class="sxs-lookup"><span data-stu-id="1bbfe-144">Every method wraps the received message into a reply message and echoes it back to the client.</span></span>  
  
## <a name="running-and-building-the-sample"></a><span data-ttu-id="1bbfe-145">Uruchamianie i Tworzenie przykładu</span><span class="sxs-lookup"><span data-stu-id="1bbfe-145">Running and Building the Sample</span></span>  
 <span data-ttu-id="1bbfe-146">Po uruchomieniu przykładu zawartość treści odpowiedzi operacji zostanie wyświetlona w oknie konsoli klienta podobne do następujących (sformatowane) danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="1bbfe-146">When you run the sample, the body content of the operation responses are displayed in the client console window similar to the following (formatted) output.</span></span>  
  
 <span data-ttu-id="1bbfe-147">Klient wysyła trzy komunikaty do usługi, której treść składa się o nazwie `bodyA`, odpowiednio `bodyB`i `bodyX`.</span><span class="sxs-lookup"><span data-stu-id="1bbfe-147">The client sends three messages to the service whose body content element is named `bodyA`, `bodyB`, and `bodyX`, respectively.</span></span> <span data-ttu-id="1bbfe-148">Jak można wywnioskować na podstawie poprzedniego opisu i podanej umowy dotyczącej usługi, komunikat przychodzący z elementem `bodyA` jest wysyłany do metody `OperationForBodyA()`.</span><span class="sxs-lookup"><span data-stu-id="1bbfe-148">As can be deferred from the previous description and the service contract shown, the incoming message with the `bodyA` element is dispatched to the `OperationForBodyA()` method.</span></span> <span data-ttu-id="1bbfe-149">Ze względu na to, że dla komunikatu z `bodyX` treści nie istnieje jawny cel wysyłania wiadomości, komunikat jest wysyłany do `DefaultOperation()`.</span><span class="sxs-lookup"><span data-stu-id="1bbfe-149">Because there is no explicit dispatch target for the message with the `bodyX` body element, the message is dispatched to the `DefaultOperation()`.</span></span> <span data-ttu-id="1bbfe-150">Każda operacja usługi zawija treść otrzymanego komunikatu do elementu specyficznego dla metody i zwraca go, co jest gotowe do skorelowania komunikatów wejściowych i wyjściowych w tym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="1bbfe-150">Each of the service operations wraps the received message body into an element specific to the method and returns it, which is done to correlate input and output messages clearly for this sample:</span></span>  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1bbfe-151">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="1bbfe-151">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="1bbfe-152">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1bbfe-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="1bbfe-153">Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1bbfe-153">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="1bbfe-154">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1bbfe-154">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1bbfe-155">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="1bbfe-155">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1bbfe-156">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="1bbfe-156">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="1bbfe-157">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1bbfe-157">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1bbfe-158">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="1bbfe-158">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\AdvancedDispatchByBody`  
