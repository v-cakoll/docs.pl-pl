---
title: Element formatujący operacji i selektor operacji
ms.date: 03/30/2017
ms.assetid: 1c27e9fe-11f8-4377-8140-828207b98a0e
ms.openlocfilehash: a814de7433f2d06491245dc1d6e6e637b514118a
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44189939"
---
# <a name="operation-formatter-and-operation-selector"></a><span data-ttu-id="9f659-102">Element formatujący operacji i selektor operacji</span><span class="sxs-lookup"><span data-stu-id="9f659-102">Operation Formatter and Operation Selector</span></span>
<span data-ttu-id="9f659-103">Niniejszy przykład pokazuje, jak punkty rozszerzeń usługi Windows Communication Foundation (WCF) można umożliwić danych komunikatu w innym formacie z WCF oczekuje.</span><span class="sxs-lookup"><span data-stu-id="9f659-103">This sample demonstrates how Windows Communication Foundation (WCF) extensibility points can be used to allow message data in a different format from what WCF expects.</span></span> <span data-ttu-id="9f659-104">Domyślnie elementy formatujące WCF oczekiwane parametry metody, które mają zostać uwzględnione w ramach `soap:body` elementu.</span><span class="sxs-lookup"><span data-stu-id="9f659-104">By default, WCF formatters expect method parameters to be included under the `soap:body` element.</span></span> <span data-ttu-id="9f659-105">Przykład pokazuje, jak implementować niestandardowe działania programu formatującego, zamiast tego analizuje dane parametru ciągu zapytania HTTP GET, która wywołuje metody przy użyciu tych danych.</span><span class="sxs-lookup"><span data-stu-id="9f659-105">The sample shows how to implement a custom operation formatter that parses parameter data from an HTTP GET query string instead and invokes methods using that data.</span></span>  
  
 <span data-ttu-id="9f659-106">Przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), który implementuje `ICalculator` kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="9f659-106">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="9f659-107">Jego pokazuje jak dodawanie, odejmowanie, mnożenie, dzielenie wiadomości, można ją zmienić na użyć żądania HTTP GET dla żądań klienta do serwera i HTTP POST z POX komunikatów dla odpowiedzi z serwera do klienta.</span><span class="sxs-lookup"><span data-stu-id="9f659-107">It shows how Add, Subtract, Multiply, and Divide messages can be changed to use HTTP GET for client-to-server requests and HTTP POST with POX messages for server-to-client responses.</span></span>  
  
 <span data-ttu-id="9f659-108">Aby to zrobić, przykład zapewnia następujące korzyści:</span><span class="sxs-lookup"><span data-stu-id="9f659-108">To do so, the sample provides the following:</span></span>  
  
-   <span data-ttu-id="9f659-109">`QueryStringFormatter`, która implementuje <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> i <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> dla klienta i serwera, odpowiednio i przetwarza dane w ciągu zapytania.</span><span class="sxs-lookup"><span data-stu-id="9f659-109">`QueryStringFormatter`, which implements <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> and <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> for the client and server, respectively, and processes the data in the query string.</span></span>  
  
-   <span data-ttu-id="9f659-110">`UriOperationSelector`, która implementuje <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> na serwerze w celu wykonania wysyłki operacji na podstawie nazwy operacji żądania GET.</span><span class="sxs-lookup"><span data-stu-id="9f659-110">`UriOperationSelector`, which implements <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> on the server to perform operation dispatch based on the operation name in the GET request.</span></span>  
  
-   <span data-ttu-id="9f659-111">`EnableHttpGetRequestsBehavior` punkt końcowy zachowanie i odpowiedniej konfiguracji, która dodaje do środowiska uruchomieniowego selektor niezbędnych operacji.</span><span class="sxs-lookup"><span data-stu-id="9f659-111">`EnableHttpGetRequestsBehavior` endpoint behavior (and corresponding configuration), which adds the necessary operation selector to the runtime.</span></span>  
  
-   <span data-ttu-id="9f659-112">Pokazuje, jak można wstawić nowy element formatujący operacji w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="9f659-112">Shows how to insert a new operation formatter into the runtime.</span></span>  
  
-   <span data-ttu-id="9f659-113">W tym przykładzie zarówno klient, jak i usługi są aplikacje konsoli (.exe).</span><span class="sxs-lookup"><span data-stu-id="9f659-113">In this sample, both the client and the service are console applications (.exe).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9f659-114">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="9f659-114">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="key-concepts"></a><span data-ttu-id="9f659-115">Kluczowe pojęcia</span><span class="sxs-lookup"><span data-stu-id="9f659-115">Key Concepts</span></span>  
 <span data-ttu-id="9f659-116">`QueryStringFormatter` Element formatujący operacji jest składnikiem programu WCF, odpowiedzialną za konwersji wiadomość do tablicy obiektów parametru i tablicę obiektów parametr do wiadomości.</span><span class="sxs-lookup"><span data-stu-id="9f659-116">`QueryStringFormatter` - The operation formatter is the component in WCF that is responsible for converting a message into an array of parameter objects and an array of parameter objects into a message.</span></span> <span data-ttu-id="9f659-117">Odbywa się na komputerze klienckim, za pomocą <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> interfejsu i na serwerze z <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="9f659-117">This is done on the client using the <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> interface and on the server with the <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interface.</span></span> <span data-ttu-id="9f659-118">Te interfejsy umożliwiają użytkownikom pobieranie komunikatów żądań i odpowiedzi z `Serialize` i `Deserialize` metody.</span><span class="sxs-lookup"><span data-stu-id="9f659-118">These interfaces enable users to get the request and response messages from the `Serialize` and `Deserialize` methods.</span></span>  
  
 <span data-ttu-id="9f659-119">W tym przykładzie `QueryStringFormatter` implementuje obu tych interfejsów i jest zaimplementowana na kliencie i serwerze.</span><span class="sxs-lookup"><span data-stu-id="9f659-119">In this sample, `QueryStringFormatter` implements both of these interfaces and is implemented on the client and server.</span></span>  
  
 <span data-ttu-id="9f659-120">Żądanie:</span><span class="sxs-lookup"><span data-stu-id="9f659-120">Request:</span></span>  
  
-   <span data-ttu-id="9f659-121">W przykładzie użyto <xref:System.ComponentModel.TypeConverter> klasy w celu przekonwertowania danych parametru w komunikacie żądania do i z ciągów.</span><span class="sxs-lookup"><span data-stu-id="9f659-121">The sample uses the <xref:System.ComponentModel.TypeConverter> class to convert parameter data in the request message to and from strings.</span></span> <span data-ttu-id="9f659-122">Jeśli <xref:System.ComponentModel.TypeConverter> nie jest dostępna dla określonego typu, zgłasza program formatujący przykładowy wyjątek, który.</span><span class="sxs-lookup"><span data-stu-id="9f659-122">If a <xref:System.ComponentModel.TypeConverter> is not available for a specific type, the sample formatter throws an exception.</span></span>  
  
-   <span data-ttu-id="9f659-123">W `IClientMessageFormatter.SerializeRequest` metody na kliencie, program formatujący tworzy identyfikator URI przy użyciu odpowiedniego adresu i dołącza nazwy operacji jako sufiks.</span><span class="sxs-lookup"><span data-stu-id="9f659-123">In the `IClientMessageFormatter.SerializeRequest` method on the client, the formatter creates a URI with the appropriate To address and appends the operation name as a suffix.</span></span> <span data-ttu-id="9f659-124">Ta nazwa jest używana do wysłania do odpowiednich operacji na serwerze.</span><span class="sxs-lookup"><span data-stu-id="9f659-124">This name is used to dispatch to the appropriate operation on the server.</span></span> <span data-ttu-id="9f659-125">Następnie pobiera tablicę obiektów parametru i serializuje dane parametru ciągu zapytania identyfikatora URI za pomocą nazwy i wartości przekonwertowane przez <xref:System.ComponentModel.TypeConverter> klasy.</span><span class="sxs-lookup"><span data-stu-id="9f659-125">It then takes the array of parameter objects and serializes the parameter data to the URI query string using parameter names and the values converted by the <xref:System.ComponentModel.TypeConverter> class.</span></span> <span data-ttu-id="9f659-126"><xref:System.ServiceModel.Channels.MessageHeaders.To%2A> i <xref:System.ServiceModel.Channels.MessageProperties.Via%2A> właściwości są następnie ustawione do tego identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="9f659-126">The <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> and <xref:System.ServiceModel.Channels.MessageProperties.Via%2A> properties are then set to this URI.</span></span> <span data-ttu-id="9f659-127"><xref:System.ServiceModel.Channels.MessageProperties> jest dostępny za pośrednictwem <xref:System.ServiceModel.Channels.Message.Properties%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="9f659-127"><xref:System.ServiceModel.Channels.MessageProperties> is accessed through the <xref:System.ServiceModel.Channels.Message.Properties%2A> property.</span></span>  
  
-   <span data-ttu-id="9f659-128">W `IDispatchMessageFormatter.DeserializeRequest` pobiera element formatujący metody na serwerze, `Via` URI we właściwościach komunikatu żądania przychodzące.</span><span class="sxs-lookup"><span data-stu-id="9f659-128">In the `IDispatchMessageFormatter.DeserializeRequest` method on the server, the formatter retrieves the `Via` URI in the incoming request message properties.</span></span> <span data-ttu-id="9f659-129">On analizuje pary nazwa wartość w ciągu zapytania identyfikatora URI do nazwy parametrów i wartości i użyje nazwy parametrów i wartości, aby wypełnić Tablica parametrów przekazana do metody.</span><span class="sxs-lookup"><span data-stu-id="9f659-129">It parses the name-value pairs in the URI query string into parameter names and values and uses the parameter names and values to populate the array of parameters passed into the method.</span></span> <span data-ttu-id="9f659-130">Należy pamiętać, że operacja wysyłania już wystąpił, więc sufiks nazwy operacji jest ignorowany w przypadku tej metody.</span><span class="sxs-lookup"><span data-stu-id="9f659-130">Note that operation dispatch has already occurred, so the operation name suffix is ignored in this method.</span></span>  
  
 <span data-ttu-id="9f659-131">Odpowiedź:</span><span class="sxs-lookup"><span data-stu-id="9f659-131">Response:</span></span>  
  
-   <span data-ttu-id="9f659-132">W tym przykładzie HTTP GET jest używana tylko dla żądania.</span><span class="sxs-lookup"><span data-stu-id="9f659-132">In this sample, HTTP GET is used only for the request.</span></span> <span data-ttu-id="9f659-133">Element formatujący deleguje, wysyła odpowiedź do oryginalnego elementu formatującego, który będzie używany do generowania wiadomości XML.</span><span class="sxs-lookup"><span data-stu-id="9f659-133">The formatter delegates the sending of the response to the original formatter that would have been used to generate an XML message.</span></span> <span data-ttu-id="9f659-134">Jednym z celów tego przykładu jest pokazanie implementacji delegowania formatującego.</span><span class="sxs-lookup"><span data-stu-id="9f659-134">One of the goals of this sample is to show how such a delegating formatter can be implemented.</span></span>  
  
### <a name="uripathsuffixoperationselector-class"></a><span data-ttu-id="9f659-135">Klasa UriPathSuffixOperationSelector</span><span class="sxs-lookup"><span data-stu-id="9f659-135">UriPathSuffixOperationSelector Class</span></span>  
 <span data-ttu-id="9f659-136"><xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> Interfejs umożliwia użytkownikom do zaimplementowania własnej logiki dla operacji, który można wysłać określonej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="9f659-136">The <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> interface enables users to implement their own logic for which operation a particular message should be dispatched.</span></span>  
  
 <span data-ttu-id="9f659-137">W tym przykładzie `UriPathSuffixOperationSelector` musi zostać wdrożone na serwerze, aby wybrać odpowiednią operację, ponieważ nazwa operacji jest uwzględniony w identyfikator URI Pobierz protokołu HTTP, a nie nagłówek akcji w wiadomości.</span><span class="sxs-lookup"><span data-stu-id="9f659-137">In this sample, `UriPathSuffixOperationSelector` must be implemented on the server to select the appropriate operation because the operation name is included in the HTTP GET URI rather than an action header in the message.</span></span> <span data-ttu-id="9f659-138">Aby zezwolić na działanie tylko bez uwzględniania wielkości liter nazwy skonfigurowano próbki.</span><span class="sxs-lookup"><span data-stu-id="9f659-138">The sample is set up to allow only case-insensitive operation names.</span></span>  
  
 <span data-ttu-id="9f659-139">`SelectOperation` Metoda przyjmuje wiadomości przychodzącej i wyszukuje `Via` identyfikatora URI w jego właściwościach wiadomości.</span><span class="sxs-lookup"><span data-stu-id="9f659-139">The `SelectOperation` method takes the incoming message and looks up the `Via` URI in its message properties.</span></span> <span data-ttu-id="9f659-140">Jego wyodrębnia sufiks nazwy operacji z identyfikatora URI odwołuje się do wewnętrznej tabeli można uzyskać nazwy operacji, który komunikat powinien być wysyłane do i zwraca nazwę tej operacji.</span><span class="sxs-lookup"><span data-stu-id="9f659-140">It extracts the operation name suffix from the URI, looks up an internal table to get the operation name that the message should be dispatched to, and returns that operation name.</span></span>  
  
### <a name="enablehttpgetrequestsbehavior-class"></a><span data-ttu-id="9f659-141">Klasa EnableHttpGetRequestsBehavior</span><span class="sxs-lookup"><span data-stu-id="9f659-141">EnableHttpGetRequestsBehavior Class</span></span>  
 <span data-ttu-id="9f659-142">`UriPathSuffixOperationSelector` Składnika można skonfigurować pod kątem programowo lub za pomocą zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="9f659-142">The `UriPathSuffixOperationSelector` component can be set up programmatically or through an endpoint behavior.</span></span> <span data-ttu-id="9f659-143">Implementuje próbki `EnableHttpGetRequestsBehavior` zachowanie, które określono w pliku konfiguracji aplikacji usługi.</span><span class="sxs-lookup"><span data-stu-id="9f659-143">The sample implements the `EnableHttpGetRequestsBehavior` behavior, which is specified in service’s application configuration file.</span></span>  
  
 <span data-ttu-id="9f659-144">Na serwerze:</span><span class="sxs-lookup"><span data-stu-id="9f659-144">On the server:</span></span>  
  
 <span data-ttu-id="9f659-145"><xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A> Ustawiono <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementacji.</span><span class="sxs-lookup"><span data-stu-id="9f659-145">The <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A> is set to the <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementation.</span></span>  
  
 <span data-ttu-id="9f659-146">Domyślnie program WCF używa filtra dokładnie dopasowanego adresu.</span><span class="sxs-lookup"><span data-stu-id="9f659-146">By default, WCF uses an exact-match address filter.</span></span> <span data-ttu-id="9f659-147">Identyfikator URI na przychodząca wiadomość zawiera sufiks nazwy operacji następuje ciąg zapytania, który zawiera dane parametru, więc zachowanie punktu końcowego zmienia także filtr adresów jako prefiks, który pasuje do filtru.</span><span class="sxs-lookup"><span data-stu-id="9f659-147">The URI on the incoming message contains an operation name suffix followed by a query string that contains parameter data, so the endpoint behavior also changes the address filter to be a prefix match filter.</span></span> <span data-ttu-id="9f659-148">Używa ona WCF<xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> do tego celu.</span><span class="sxs-lookup"><span data-stu-id="9f659-148">It uses the WCF<xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> for this purpose.</span></span>  
  
### <a name="installing-operation-formatters"></a><span data-ttu-id="9f659-149">Instalowanie elementów formatujących operacji</span><span class="sxs-lookup"><span data-stu-id="9f659-149">Installing operation formatters</span></span>  
 <span data-ttu-id="9f659-150">Zachowania operacji, które określają elementy formatujące są unikatowe.</span><span class="sxs-lookup"><span data-stu-id="9f659-150">Operation behaviors that specify formatters are unique.</span></span> <span data-ttu-id="9f659-151">Jednego takiego zachowania zawsze jest implementowany przez domyślne dla każdej operacji utworzyć element formatujący niezbędnych operacji.</span><span class="sxs-lookup"><span data-stu-id="9f659-151">One such behavior is always implemented by default for every operation to create the necessary operation formatter.</span></span> <span data-ttu-id="9f659-152">Jednak te zachowania wyglądać kolejna operacja zachowań. nie są identyfikowane przez inne atrybuty.</span><span class="sxs-lookup"><span data-stu-id="9f659-152">However, these behaviors look like just another operation behavior; they are not identifiable by any other attribute.</span></span> <span data-ttu-id="9f659-153">Aby zainstalować zachowanie zastępczy, implementacja musi poszukaj go zastąpić określonego programu formatującego zachowań, które są instalowane przez moduł ładujący typu WCF domyślnie i za pomocą lub dodać zachowanie zgodne do uruchomienia po zachowanie domyślne.</span><span class="sxs-lookup"><span data-stu-id="9f659-153">To install a replacement behavior, the implementation must look for specific formatter behaviors that are installed by the WCF type loader by default and either replace it or add a compatible behavior to run after the default behavior.</span></span>  
  
 <span data-ttu-id="9f659-154">Zachowania elementy formatujące tych operacji można skonfigurować pod kątem programowo przed wywołaniem <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> lub określając zachowanie operacji, który jest wykonywany po domyślny.</span><span class="sxs-lookup"><span data-stu-id="9f659-154">These operation formatters behaviors can be set up programmatically prior to calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> or by specifying an operation behavior that is executed after the default one.</span></span> <span data-ttu-id="9f659-155">Jednak go nie można łatwo można skonfigurować przez zachowanie punktu końcowego (i w związku z tym przez konfigurację), ponieważ model zachowanie nie zezwala na to zachowanie zastąpić innych zachowań lub inny sposób modyfikować drzewa opis.</span><span class="sxs-lookup"><span data-stu-id="9f659-155">However, it cannot easily be set up by an endpoint behavior (and therefore by configuration) because the behavior model does not allow a behavior to replace other behaviors or otherwise modify the description tree.</span></span>  
  
 <span data-ttu-id="9f659-156">Na komputerze klienckim:</span><span class="sxs-lookup"><span data-stu-id="9f659-156">On the client:</span></span>  
  
 <span data-ttu-id="9f659-157"><xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> Implementacji należy zaimplementować tak, aby ją przekonwertować żądania na żądania HTTP GET i delegować do oryginalnego program formatujący dla odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="9f659-157">The <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> implementation must be implemented so that it can convert the requests into HTTP GET requests and delegate to the original formatter for responses.</span></span> <span data-ttu-id="9f659-158">Jest to realizowane przez wywołanie `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` metody pomocnika.</span><span class="sxs-lookup"><span data-stu-id="9f659-158">This is done by calling the `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` helper method.</span></span>  
  
 <span data-ttu-id="9f659-159">To musi odbywać się przed wywołaniem `CreateChannel`.</span><span class="sxs-lookup"><span data-stu-id="9f659-159">This must be done before calling `CreateChannel`.</span></span>  
  
```  
void ReplaceFormatterBehavior(OperationDescription operationDescription, EndpointAddress address)  
{  
    // Remove the DataContract behavior if it is present.  
    IOperationBehavior formatterBehavior = operationDescription.Behaviors.Remove<DataContractSerializerOperationBehavior>();  
    if (formatterBehavior == null)  
    {  
        // Remove the XmlSerializer behavior if it is present.  
        formatterBehavior = operationDescription.Behaviors.Remove<XmlSerializerOperationBehavior>();  
        ...  
    }  
  
    // Remember what the innerFormatterBehavior was.  
    DelegatingFormatterBehavior delegatingFormatterBehavior = new DelegatingFormatterBehavior(address);  
    delegatingFormatterBehavior.InnerFormatterBehavior = formatterBehavior;  
   operationDescription.Behaviors.Add(delegatingFormatterBehavior);  
}  
```  
  
 <span data-ttu-id="9f659-160">Na serwerze:</span><span class="sxs-lookup"><span data-stu-id="9f659-160">On the server:</span></span>  
  
-   <span data-ttu-id="9f659-161"><xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> Można zaimplementować interfejsu, czemu może odczytywać żądania HTTP GET i delegować do oryginalnego elementu formatującego do pisania odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="9f659-161">The <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interface must be implemented so that it can read HTTP GET requests and delegate to the original formatter for writing responses.</span></span> <span data-ttu-id="9f659-162">Odbywa się przez wywołanie metody takie same `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` metody pomocnika jako klient (zobacz poprzedni przykład kodu).</span><span class="sxs-lookup"><span data-stu-id="9f659-162">This is done by calling the same `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` helper method as the client (see the previous code sample).</span></span>  
  
-   <span data-ttu-id="9f659-163">To musi odbywać się przed <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="9f659-163">This must be done before <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> is called.</span></span> <span data-ttu-id="9f659-164">W tym przykładzie pokazano, jak program formatujący jest modyfikowany ręcznie przed wywołaniem <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span><span class="sxs-lookup"><span data-stu-id="9f659-164">In this sample, we show how the formatter is manually modified before calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span> <span data-ttu-id="9f659-165">Innym sposobem, aby osiągnąć ten sam efekt jest wyprowadzić klasę z <xref:System.ServiceModel.ServiceHost> sprawia to, że wywołania `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` przed otwarciem (zobacz hostingu, dokumentację i przykłady dotyczące przykładów).</span><span class="sxs-lookup"><span data-stu-id="9f659-165">Another way to achieve the same thing is to derive a class from <xref:System.ServiceModel.ServiceHost> that makes the calls to `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` before opening (please see hosting documentation and samples for examples).</span></span>  
  
### <a name="user-experience"></a><span data-ttu-id="9f659-166">Środowisko użytkownika</span><span class="sxs-lookup"><span data-stu-id="9f659-166">User experience</span></span>  
 <span data-ttu-id="9f659-167">Na serwerze:</span><span class="sxs-lookup"><span data-stu-id="9f659-167">On the server:</span></span>  
  
-   <span data-ttu-id="9f659-168">Serwer `ICalculator` wdrożenia nie trzeba zmieniać.</span><span class="sxs-lookup"><span data-stu-id="9f659-168">The server `ICalculator` implementation does not need to change.</span></span>  
  
-   <span data-ttu-id="9f659-169">App.config dla usługi, należy użyć niestandardowego powiązania POX, która ustawia `messageVersion` atrybutu `textMessageEncoding` elementu `None`.</span><span class="sxs-lookup"><span data-stu-id="9f659-169">The App.config for the service must use a custom POX binding that sets the `messageVersion` attribute of the `textMessageEncoding` element to `None`.</span></span>  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="poxBinding">  
          <textMessageEncoding messageVersion="None" />  
          <httpTransport />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
-   <span data-ttu-id="9f659-170">App.config dla usługi również podać niestandardową `EnableHttpGetRequestsBehavior` , dodając go do sekcji rozszerzenia zachowania i korzystania z niego.</span><span class="sxs-lookup"><span data-stu-id="9f659-170">The App.config for the service also must specify the custom `EnableHttpGetRequestsBehavior` by adding it to the behavior extensions section and using it.</span></span>  
  
    ```xml  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="enableHttpGetRequestsBehavior">  
          <enableHttpGetRequests />  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
  
    <extensions>  
      <behaviorExtensions>  
        <!-- Enabling HTTP GET requests: Behavior Extension -->  
        <add   
          name="enableHttpGetRequests"           type="Microsoft.ServiceModel.Samples.EnableHttpGetRequestsBehaviorElement, QueryStringFormatter, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
      </behaviorExtensions>  
    </extensions>  
    ```  
  
-   <span data-ttu-id="9f659-171">Dodaj elementy formatujące operacji, przed wywołaniem <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span><span class="sxs-lookup"><span data-stu-id="9f659-171">Add operation formatters before calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span>  
  
 <span data-ttu-id="9f659-172">Na komputerze klienckim:</span><span class="sxs-lookup"><span data-stu-id="9f659-172">On the client:</span></span>  
  
-   <span data-ttu-id="9f659-173">Implementacja klienta nie trzeba zmieniać.</span><span class="sxs-lookup"><span data-stu-id="9f659-173">The client implementation does not need to change.</span></span>  
  
-   <span data-ttu-id="9f659-174">App.config dla klienta, należy użyć niestandardowego powiązania POX, która ustawia `messageVersion` atrybutu `textMessageEncoding` elementu `None`.</span><span class="sxs-lookup"><span data-stu-id="9f659-174">The App.config for the client must use a custom POX binding that sets the `messageVersion` attribute of the `textMessageEncoding` element to `None`.</span></span> <span data-ttu-id="9f659-175">Jedną różnicaą z usługi jest to klienta należy włączyć, ręcznego adresowania, tak aby wychodzących na adres może być modyfikowany.</span><span class="sxs-lookup"><span data-stu-id="9f659-175">One difference from the service is that the client must enable manual addressing so that the outgoing To address can be modified.</span></span>  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="poxBinding">  
          <textMessageEncoding messageVersion="None" />  
          <httpTransport manualAddressing="True" />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
-   <span data-ttu-id="9f659-176">App.config dla klienta należy określić ten sam niestandardowy `EnableHttpGetRequestsBehavior` co serwer.</span><span class="sxs-lookup"><span data-stu-id="9f659-176">The App.config for the client must specify the same custom `EnableHttpGetRequestsBehavior` as the server.</span></span>  
  
-   <span data-ttu-id="9f659-177">Dodaj elementy formatujące operacji, przed wywołaniem <xref:System.ServiceModel.ChannelFactory%601.CreateChannel>.</span><span class="sxs-lookup"><span data-stu-id="9f659-177">Add operation formatters before calling <xref:System.ServiceModel.ChannelFactory%601.CreateChannel>.</span></span>  
  
 <span data-ttu-id="9f659-178">Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="9f659-178">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="9f659-179">Wszystkie cztery operacje (dodawania, odejmowania, mnożenia i dzielenia) musi zakończyć się sukcesem.</span><span class="sxs-lookup"><span data-stu-id="9f659-179">All four operations (Add, Subtract, Multiply, and Divide) must succeed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9f659-180">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="9f659-180">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9f659-181">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="9f659-181">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9f659-182">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="9f659-182">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9f659-183">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="9f659-183">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Formatters\QuieryStringFormatter`  
  
##### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9f659-184">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="9f659-184">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="9f659-185">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9f659-185">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="9f659-186">Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9f659-186">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="9f659-187">Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9f659-187">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f659-188">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9f659-188">See Also</span></span>
