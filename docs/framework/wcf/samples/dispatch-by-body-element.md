---
title: "Wysyłanie według elementu treści"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f64a3c04-62b4-47b2-91d9-747a3af1659f
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4ab8ddccafa8dbf1ecde8afbb07f0a61faa62be5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="dispatch-by-body-element"></a><span data-ttu-id="e5690-102">Wysyłanie według elementu treści</span><span class="sxs-lookup"><span data-stu-id="e5690-102">Dispatch by Body Element</span></span>
<span data-ttu-id="e5690-103">W tym przykładzie pokazano, jak wdrożyć alternatywny algorytm przypisywanie komunikatów przychodzących do operacji.</span><span class="sxs-lookup"><span data-stu-id="e5690-103">This sample demonstrates how to implement an alternate algorithm for assigning incoming messages to operations.</span></span>  
  
 <span data-ttu-id="e5690-104">Domyślnie dyspozytora modelu usługi wybiera metodę odpowiednią obsługę wiadomości przychodzących, oparte na wiadomości WS-Addressing "Akcja" nagłówek lub równoważnych informacji w żądaniu SOAP protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="e5690-104">By default, the service model dispatcher selects the appropriate handling method for an incoming message based on the message's WS-Addressing "Action" header or the equivalent information in the HTTP SOAP request.</span></span>  
  
 <span data-ttu-id="e5690-105">Niektóre SOAP 1.1 w sieci Web usług stosy nie wykonuj WS-I Basic Profile 1.1 wytyczne, nie wysyła komunikaty oparte na identyfikator URI akcji, ale raczej opartego na nazwie kwalifikowanej XML pierwszego elementu wewnątrz treści protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="e5690-105">Some SOAP 1.1 Web services stacks that do not follow the WS-I Basic Profile 1.1 guidelines do not dispatch messages based on the Action URI, but rather based on the XML qualified name of the first element inside the SOAP body.</span></span> <span data-ttu-id="e5690-106">Podobnie te stosy po stronie klienta może wysyłać wiadomości z pustą lub dowolnego HTTP SoapAction nagłówka, który został dozwolone przez specyfikację SOAP 1.1.</span><span class="sxs-lookup"><span data-stu-id="e5690-106">Likewise, the client side of these stacks might send messages with an empty or arbitrary HTTP SoapAction header, which was permitted by the SOAP 1.1 specification.</span></span>  
  
 <span data-ttu-id="e5690-107">Aby zmienić sposób komunikaty są wysyłane do metod, implementuje próbki <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> interfejsu rozszerzalności na `DispatchByBodyElementOperationSelector`.</span><span class="sxs-lookup"><span data-stu-id="e5690-107">To change the way messages are dispatched to methods, the sample implements the <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> extensibility interface on the `DispatchByBodyElementOperationSelector`.</span></span> <span data-ttu-id="e5690-108">Ta klasa wybiera operacje oparte na pierwszym elementem w treści wiadomości.</span><span class="sxs-lookup"><span data-stu-id="e5690-108">This class selects operations based on the first element of the message body.</span></span>  
  
 <span data-ttu-id="e5690-109">Konstruktor klasy oczekuje słownik wypełniane przy użyciu pary `XmlQualifiedName` i ciągi, zgodnie z którymi nazwy kwalifikowane wskazują nazwę pierwszego elementu podrzędnego treści protokołu SOAP i ciągi wskazują pasujące nazwy operacji.</span><span class="sxs-lookup"><span data-stu-id="e5690-109">The class constructor expects a dictionary populated with pairs of `XmlQualifiedName` and strings, whereby the qualified names indicate the name of the first child of the SOAP body and the strings indicate the matching operation name.</span></span> <span data-ttu-id="e5690-110">`defaultOperationName` To nazwa operacji, która odbiera wszystkie komunikaty, które nie mogą być dopasowywane do tego słownika:</span><span class="sxs-lookup"><span data-stu-id="e5690-110">The `defaultOperationName` is the name of the operation that receives all messages that cannot be matched against this dictionary:</span></span>  
  
```  
class DispatchByBodyElementOperationSelector : IDispatchOperationSelector  
{  
    Dictionary<XmlQualifiedName, string> dispatchDictionary;  
    string defaultOperationName;  
  
    public DispatchByBodyElementOperationSelector(Dictionary<XmlQualifiedName,string> dispatchDictionary, string defaultOperationName)  
    {  
        this.dispatchDictionary = dispatchDictionary;  
        this.defaultOperationName = defaultOperationName;  
    }  
```  
  
 <span data-ttu-id="e5690-111"><xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector>implementacje są bardzo proste do kompilacji, ponieważ istnieje tylko jedna metoda w interfejsie: <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A>.</span><span class="sxs-lookup"><span data-stu-id="e5690-111"><xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementations are very straightforward to build as there is only one method on the interface: <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A>.</span></span> <span data-ttu-id="e5690-112">Zadania tej metody jest do zbadania wiadomości przychodzącej i zwraca ciąg, który jest równe Nazwa metody na kontrakt usługi dla bieżącego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="e5690-112">The job of this method is to inspect an incoming message and to return a string that equals the name of a method on the service contract for the current endpoint.</span></span>  
  
 <span data-ttu-id="e5690-113">W tym przykładzie uzyskuje selektor operacji <xref:System.Xml.XmlDictionaryReader> komunikatu przychodzącego elementu body przy użyciu <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>.</span><span class="sxs-lookup"><span data-stu-id="e5690-113">In this sample, the operation selector acquires an <xref:System.Xml.XmlDictionaryReader> for the incoming message's body using <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>.</span></span> <span data-ttu-id="e5690-114">Ta metoda już umieszcza czytnik na pierwszy element podrzędny elementu treści wiadomości, aby jest wystarczająca do bieżącego elementu nazwa i identyfikator URI przestrzeni nazw i połączyć je w `XmlQualifiedName` następnie używany do wyszukiwania odpowiadająca mu operacja z Słownik posiadanych przez selektor operacji.</span><span class="sxs-lookup"><span data-stu-id="e5690-114">This method already positions the reader on the first child of the message's body so that it is sufficient to get the current element's name and namespace URI and combine them into an `XmlQualifiedName` that is then used for looking up the corresponding operation from the dictionary held by the operation selector.</span></span>  
  
```  
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
  
 <span data-ttu-id="e5690-115">Dostęp do treści wiadomości z <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> lub dowolnej z metod, które zapewniają dostęp do zawartości w treści wiadomości powoduje, że komunikat, który ma być oznaczona jako "do odczytu", co oznacza, że wiadomość jest nieprawidłowa dla dalszego przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="e5690-115">Accessing the message body with <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> or any of the other methods that provide access to the message's body content causes the message to be marked as "read", which means that the message is invalid for any further processing.</span></span> <span data-ttu-id="e5690-116">W związku z tym selektor operacji tworzy kopię komunikat przychodzący z metodą poniższym kodem.</span><span class="sxs-lookup"><span data-stu-id="e5690-116">Therefore, the operation selector creates a copy of the incoming message with the method shown in the following code.</span></span> <span data-ttu-id="e5690-117">Ponieważ proces czytający pozycji nie została zmieniona podczas kontroli, mogą się odwoływać linie nowo utworzony komunikat do którego właściwości wiadomości i nagłówki komunikatów są również kopiowane, co powoduje dokładne klonowania oryginalnej wiadomości:</span><span class="sxs-lookup"><span data-stu-id="e5690-117">Because the reader's position has not been changed during the inspection, it can be referenced by the newly created message to which the message properties and the message headers are also copied, which results in an exact clone of the original message:</span></span>  
  
```  
private Message CreateMessageCopy(Message message,   
                                     XmlDictionaryReader body)  
{  
    Message copy = Message.CreateMessage(message.Version,message.Headers.Action,body);  
    copy.Headers.CopyHeaderFrom(message,0);  
    copy.Properties.CopyProperties(message.Properties);  
    return copy;  
}  
```  
  
## <a name="adding-an-operation-selector-to-a-service"></a><span data-ttu-id="e5690-118">Dodawanie selektor operacji do usługi</span><span class="sxs-lookup"><span data-stu-id="e5690-118">Adding an Operation Selector to a Service</span></span>  
 <span data-ttu-id="e5690-119">Selektory operacji wysyłania usługi są rozszerzenia [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] dyspozytora.</span><span class="sxs-lookup"><span data-stu-id="e5690-119">Service dispatch operation selectors are extensions to the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] dispatcher.</span></span> <span data-ttu-id="e5690-120">Wybierania metody w kanale wywołania zwrotnego kontraktów dupleksowych, są również selektorów operacji klienta, które znacznie działa jak selektorów operacji wysyłania opisane w tym miejscu, ale które nie są jawnie wymienione w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="e5690-120">For selecting methods on the callback channel of duplex contracts, there are also client operation selectors, which work very much like the dispatch operation selectors described here, but which are not explicitly covered in this sample.</span></span>  
  
 <span data-ttu-id="e5690-121">Podobnie jak większość rozszerzenia modelu usługi selektorów operacji wysyłania są dodawane do dyspozytora za pomocą zachowań.</span><span class="sxs-lookup"><span data-stu-id="e5690-121">Like most service model extensions, dispatch operation selectors are added to the dispatcher using behaviors.</span></span> <span data-ttu-id="e5690-122">A *zachowanie* jest obiekt konfiguracji, który dodaje jedno lub więcej rozszerzeń do wysyłania środowiska wykonawczego (lub środowiska uruchomieniowego klienta) albo w przeciwnym razie zmienia jego ustawienia.</span><span class="sxs-lookup"><span data-stu-id="e5690-122">A *behavior* is a configuration object, which either adds one or more extensions to the dispatch runtime (or to the client runtime) or otherwise changes its settings.</span></span>  
  
 <span data-ttu-id="e5690-123">Ponieważ selektory operacji zakresu kontraktu, działanie odpowiednie do zaimplementowania w tym miejscu jest <xref:System.ServiceModel.Description.IContractBehavior>.</span><span class="sxs-lookup"><span data-stu-id="e5690-123">Because operation selectors have contract scope, the appropriate behavior to implement here is the <xref:System.ServiceModel.Description.IContractBehavior>.</span></span> <span data-ttu-id="e5690-124">Ponieważ interfejs jest wdrażany na <xref:System.Attribute> klasy jak pokazano w poniższym kodzie, zachowanie można deklaratywnie dodać do dowolnego kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="e5690-124">Because the interface is implemented on a <xref:System.Attribute> derived class as shown in the following code, the behavior can be declaratively added to any service contract.</span></span> <span data-ttu-id="e5690-125">Zawsze, gdy <xref:System.ServiceModel.ServiceHost> jest otwarty i środowisko wykonawcze wysyłce jest wbudowana, wszystkie zachowania znaleziono jako atrybuty kontrakty, operacje i implementacji usługi lub jako element w konfiguracji usługi są automatycznie dodawane i później monit współtworzenia rozszerzenia lub zmodyfikować domyślną konfigurację.</span><span class="sxs-lookup"><span data-stu-id="e5690-125">Whenever a <xref:System.ServiceModel.ServiceHost> is opened and the dispatch runtime is built, all behaviors found either as attributes on contracts, operations, and service implementations or as element in the service configuration are automatically added and subsequently asked to contribute extensions or modify the default configuration.</span></span>  
  
 <span data-ttu-id="e5690-126">Jednak poniższy fragment kodu przedstawia tylko implementacja metody <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A>, który ma wpływ zmian konfiguracji dla dyspozytora w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="e5690-126">For brevity, the following code excerpt only shows the implementation of the method <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A>, which effects the configuration changes for the dispatcher in this sample.</span></span> <span data-ttu-id="e5690-127">Inne metody są niewidoczne, ponieważ zwracany do obiektu wywołującego w bez działał.</span><span class="sxs-lookup"><span data-stu-id="e5690-127">The other methods are not shown because they return to the caller without doing any work.</span></span>  
  
```  
[AttributeUsage(AttributeTargets.Class|AttributeTargets.Interface)]  
class DispatchByBodyElementBehaviorAttribute : Attribute, IContractBehavior  
{  
    // public void AddBindingParameters(...)   
    // public void ApplyClientBehavior(...)  
    // public void Validate(...)  
```  
  
 <span data-ttu-id="e5690-128">Najpierw <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> implementacja ustawia słownik selektor operacji wyszukiwania przez Iterowanie po <xref:System.ServiceModel.Description.OperationDescription> elementów w punkcie końcowym usługi <xref:System.ServiceModel.Description.ContractDescription>.</span><span class="sxs-lookup"><span data-stu-id="e5690-128">First, the <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> implementation sets up the lookup dictionary for the operation selector by iterating over the <xref:System.ServiceModel.Description.OperationDescription> elements in the service endpoint's <xref:System.ServiceModel.Description.ContractDescription>.</span></span> <span data-ttu-id="e5690-129">Następnie, każdy opis operacji jest sprawdzane pod kątem obecności `DispatchBodyElementAttribute` zachowanie, implementacja <xref:System.ServiceModel.Description.IOperationBehavior> jest też definiowany w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="e5690-129">Then, each operation description is inspected for the presence of the `DispatchBodyElementAttribute` behavior, an implementation of <xref:System.ServiceModel.Description.IOperationBehavior> that is also defined in this sample.</span></span> <span data-ttu-id="e5690-130">Ta klasa jest również zachowanie, jest w stanie pasywnym i nie wpływa aktywnie jakiekolwiek zmiany konfiguracji do środowiska wykonawczego wysyłania.</span><span class="sxs-lookup"><span data-stu-id="e5690-130">While this class is also a behavior, it is passive and does not actively contribute any configuration changes to the dispatch runtime.</span></span> <span data-ttu-id="e5690-131">Zwróć wszystkie jego metody do obiektu wywołującego bez konieczności przełączania żadnych akcji.</span><span class="sxs-lookup"><span data-stu-id="e5690-131">All of its methods return to the caller without taking any actions.</span></span> <span data-ttu-id="e5690-132">Zachowanie operacji istnieje tylko tak, aby metadane wymagane dla nowego wysyłania mechanizmu, czyli kwalifikowaną nazwę elementu body na wystąpienie, którego operacji jest zaznaczone, może być skojarzony z odpowiednich działań.</span><span class="sxs-lookup"><span data-stu-id="e5690-132">The operation behavior only exists so that the metadata required for the new dispatch mechanism, namely the qualified name of the body element on whose occurrence an operation is selected, can be associated with the respective operations.</span></span>  
  
 <span data-ttu-id="e5690-133">Jeśli takie zachowanie zostanie znaleziony, parę wartości utworzone na podstawie nazwy kwalifikowanej XML (`QName` właściwości) i nazwa operacji (`Name` właściwości) zostanie dodany do słownika.</span><span class="sxs-lookup"><span data-stu-id="e5690-133">If such a behavior is found, a value pair created from the XML qualified name (`QName` property) and the operation name (`Name` property) is added to the dictionary.</span></span>  
  
 <span data-ttu-id="e5690-134">Po słowniku zostanie wypełnione, nowy `DispatchByBodyElementOperationSelector` jest utworzone z tymi informacjami i Ustaw jako selektor operacji wysyłania środowiska uruchomieniowego:</span><span class="sxs-lookup"><span data-stu-id="e5690-134">Once the dictionary is populated, a new `DispatchByBodyElementOperationSelector` is constructed with this information and set as the operation selector of the dispatch runtime:</span></span>  
  
```  
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
  
## <a name="implementing-the-service"></a><span data-ttu-id="e5690-135">Wdrażanie usługi</span><span class="sxs-lookup"><span data-stu-id="e5690-135">Implementing the Service</span></span>  
 <span data-ttu-id="e5690-136">Zachowanie zaimplementowana w tym przykładzie bezpośrednio wpływa na sposób komunikaty z sieci są interpretowane i wysyłane, która jest funkcją kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="e5690-136">The behavior implemented in this sample directly affects how messages from the wire are interpreted and dispatched, which is a function of the service contract.</span></span> <span data-ttu-id="e5690-137">W rezultacie zachowanie powinny zostać zadeklarowane na poziomie kontraktu usługi w implementacji usługi wybierający z niego korzystać.</span><span class="sxs-lookup"><span data-stu-id="e5690-137">Consequently, the behavior should be declared on the service contract level in any service implementation that chooses to use it.</span></span>  
  
 <span data-ttu-id="e5690-138">Dotyczy usługi projektu próbki `DispatchByBodyElementBehaviorAttribute` kontraktu zachowania do `IDispatchedByBody` usługi umowy oraz etykiety z tych dwóch operacji `OperationForBodyA()` i `OperationForBodyB()` z `DispatchBodyElementAttribute` zachowanie operacji.</span><span class="sxs-lookup"><span data-stu-id="e5690-138">The sample project service applies the `DispatchByBodyElementBehaviorAttribute` contract behavior to the `IDispatchedByBody` service contract and labels each of the two operations `OperationForBodyA()` and `OperationForBodyB()` with a `DispatchBodyElementAttribute` operation behavior.</span></span> <span data-ttu-id="e5690-139">Po otwarciu usługi hosta dla usługi, który implementuje ten kontrakt metadanych zostaje pobrana przez konstruktora dyspozytora w sposób opisany wcześniej.</span><span class="sxs-lookup"><span data-stu-id="e5690-139">When a service host for a service that implements this contract is opened, this metadata is picked up by the dispatcher builder as previously described.</span></span>  
  
 <span data-ttu-id="e5690-140">Selektor operacji wywołuje wyłącznie na podstawie elementu treści wiadomości i ignoruje "Akcja", dlatego jest wymagany w celu Poinformuj środowiska uruchomieniowego nie, aby sprawdzić nagłówka "Action" zwrócony odpowiedzi na przypisując symbol wieloznaczny "*" do `ReplyAction` właściwości <xref:System.ServiceModel.OperationContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="e5690-140">Because the operation selector dispatches solely based on the message body element and ignores the "Action", it is required to tell the runtime not to check the "Action" header on the returned replies by assigning the wildcard "*" to the `ReplyAction` property of <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="e5690-141">Ponadto jest wymagany do operacji domyślny, który ma właściwość "Akcja" symbol wieloznaczny "\*".</span><span class="sxs-lookup"><span data-stu-id="e5690-141">Furthermore, it is required to have a default operation that has the "Action" property set to the wildcard "\*".</span></span> <span data-ttu-id="e5690-142">Operacja domyślna odbiera wszystkie komunikaty, które nie mogą być wysyłane i nie ma `DispatchBodyElementAttribute`:</span><span class="sxs-lookup"><span data-stu-id="e5690-142">The default operation receives all messages which cannot be dispatched and does not have a `DispatchBodyElementAttribute`:</span></span>  
  
```  
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
  
 <span data-ttu-id="e5690-143">Przykładowe zastosowanie usługi jest prosta.</span><span class="sxs-lookup"><span data-stu-id="e5690-143">The sample service implementation is straightforward.</span></span> <span data-ttu-id="e5690-144">Każda metoda opakowuje odebranego komunikatu do komunikatu odpowiedzi i zwraca go do klienta.</span><span class="sxs-lookup"><span data-stu-id="e5690-144">Every method wraps the received message into a reply message and echoes it back to the client.</span></span>  
  
## <a name="running-and-building-the-sample"></a><span data-ttu-id="e5690-145">Uruchomiona i tworzenia próbki</span><span class="sxs-lookup"><span data-stu-id="e5690-145">Running and Building the Sample</span></span>  
 <span data-ttu-id="e5690-146">Po uruchomieniu przykładowej zawartości w treści odpowiedzi operacji są wyświetlane w oknie konsoli klienta podobne do następujących danych wyjściowych (sformatowanych).</span><span class="sxs-lookup"><span data-stu-id="e5690-146">When you run the sample, the body content of the operation responses are displayed in the client console window similar to the following (formatted) output.</span></span>  
  
 <span data-ttu-id="e5690-147">Klient wysyła wiadomości do usługi którego zawartości, nosi nazwę elementu treści `bodyA`, `bodyB`, i `bodyX`odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="e5690-147">The client sends three messages to the service whose body content element is named `bodyA`, `bodyB`, and `bodyX`, respectively.</span></span> <span data-ttu-id="e5690-148">Jak można odroczyć z poprzednich opis i kontraktu usługi pokazano, przychodzących komunikatów z `bodyA` element jest wysyłane do `OperationForBodyA()` metody.</span><span class="sxs-lookup"><span data-stu-id="e5690-148">As can be deferred from the previous description and the service contract shown, the incoming message with the `bodyA` element is dispatched to the `OperationForBodyA()` method.</span></span> <span data-ttu-id="e5690-149">Ponieważ nie istnieje bez obiektu docelowego jawne wysyłania wiadomości z `bodyX` elementu treści wiadomości jest wysyłane do `DefaultOperation()`.</span><span class="sxs-lookup"><span data-stu-id="e5690-149">Because there is no explicit dispatch target for the message with the `bodyX` body element, the message is dispatched to the `DefaultOperation()`.</span></span> <span data-ttu-id="e5690-150">Każdej operacji usługi do określonej metody elementu jest zawijana treści odebranego komunikatu i zwraca go, które skonfigurowano w celu skorelowania danych wejściowych i wyjściowych wiadomości wyraźnie dla tego przykładu:</span><span class="sxs-lookup"><span data-stu-id="e5690-150">Each of the service operations wraps the received message body into an element specific to the method and returns it, which is done to correlate input and output messages clearly for this sample:</span></span>  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e5690-151">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="e5690-151">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="e5690-152">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e5690-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="e5690-153">Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e5690-153">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="e5690-154">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e5690-154">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e5690-155">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="e5690-155">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e5690-156">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="e5690-156">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e5690-157">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="e5690-157">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e5690-158">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="e5690-158">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\AdvancedDispatchByBody`  
  
## <a name="see-also"></a><span data-ttu-id="e5690-159">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e5690-159">See Also</span></span>
