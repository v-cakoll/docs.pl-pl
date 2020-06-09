---
title: Element formatujący operacji i selektor operacji
ms.date: 03/30/2017
ms.assetid: 1c27e9fe-11f8-4377-8140-828207b98a0e
ms.openlocfilehash: 344d3122d03e89a7f20e391db49005d0e085dfa6
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84575160"
---
# <a name="operation-formatter-and-operation-selector"></a><span data-ttu-id="62473-102">Element formatujący operacji i selektor operacji</span><span class="sxs-lookup"><span data-stu-id="62473-102">Operation Formatter and Operation Selector</span></span>
<span data-ttu-id="62473-103">Ten przykład pokazuje, w jaki sposób punkty rozszerzalności Windows Communication Foundation (WCF) mogą być używane do zezwalania na dane komunikatów w innym formacie niż oczekiwany przez WCF.</span><span class="sxs-lookup"><span data-stu-id="62473-103">This sample demonstrates how Windows Communication Foundation (WCF) extensibility points can be used to allow message data in a different format from what WCF expects.</span></span> <span data-ttu-id="62473-104">Domyślnie elementy formatujące WCF oczekują parametrów metody, które mają być zawarte w `soap:body` elemencie.</span><span class="sxs-lookup"><span data-stu-id="62473-104">By default, WCF formatters expect method parameters to be included under the `soap:body` element.</span></span> <span data-ttu-id="62473-105">W przykładzie przedstawiono sposób implementacji niestandardowego programu formatującego operacji, który analizuje dane parametrów z ciągu zapytania HTTP GET, a następnie wywołuje metody przy użyciu tych danych.</span><span class="sxs-lookup"><span data-stu-id="62473-105">The sample shows how to implement a custom operation formatter that parses parameter data from an HTTP GET query string instead and invokes methods using that data.</span></span>  
  
 <span data-ttu-id="62473-106">Przykład jest oparty na [wprowadzenie](getting-started-sample.md), który implementuje `ICalculator` kontrakt usługi.</span><span class="sxs-lookup"><span data-stu-id="62473-106">The sample is based on the [Getting Started](getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="62473-107">Pokazano, jak można zmienić komunikaty dodawania, odejmowania, mnożenia i dzielenia, aby używać protokołu HTTP GET dla żądań klient-serwer i HTTP POST z komunikatami POX dla odpowiedzi między serwerami i klientami.</span><span class="sxs-lookup"><span data-stu-id="62473-107">It shows how Add, Subtract, Multiply, and Divide messages can be changed to use HTTP GET for client-to-server requests and HTTP POST with POX messages for server-to-client responses.</span></span>  
  
 <span data-ttu-id="62473-108">W tym celu przykład zawiera następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="62473-108">To do so, the sample provides the following:</span></span>  
  
- <span data-ttu-id="62473-109">`QueryStringFormatter`, który implementuje <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> odpowiednio i dla klienta i serwera, i przetwarza dane w ciągu zapytania.</span><span class="sxs-lookup"><span data-stu-id="62473-109">`QueryStringFormatter`, which implements <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> and <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> for the client and server, respectively, and processes the data in the query string.</span></span>  
  
- <span data-ttu-id="62473-110">`UriOperationSelector`, który implementuje <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> na serwerze wykonywanie operacji wysyłania na podstawie nazwy operacji w ŻĄDANIU get.</span><span class="sxs-lookup"><span data-stu-id="62473-110">`UriOperationSelector`, which implements <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> on the server to perform operation dispatch based on the operation name in the GET request.</span></span>  
  
- <span data-ttu-id="62473-111">`EnableHttpGetRequestsBehavior`zachowanie punktu końcowego (i odpowiednia konfiguracja), które dodaje do środowiska uruchomieniowego niezbędny selektor operacji.</span><span class="sxs-lookup"><span data-stu-id="62473-111">`EnableHttpGetRequestsBehavior` endpoint behavior (and corresponding configuration), which adds the necessary operation selector to the runtime.</span></span>  
  
- <span data-ttu-id="62473-112">Pokazuje, w jaki sposób wstawić nowy program formatujący operacji do środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="62473-112">Shows how to insert a new operation formatter into the runtime.</span></span>  
  
- <span data-ttu-id="62473-113">W tym przykładzie zarówno klient, jak i usługa są aplikacjami konsolowymi (. exe).</span><span class="sxs-lookup"><span data-stu-id="62473-113">In this sample, both the client and the service are console applications (.exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="62473-114">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="62473-114">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="key-concepts"></a><span data-ttu-id="62473-115">Kluczowe pojęcia</span><span class="sxs-lookup"><span data-stu-id="62473-115">Key Concepts</span></span>  
 <span data-ttu-id="62473-116">`QueryStringFormatter`— Program formatujący operacji jest składnikiem programu WCF, który jest odpowiedzialny za konwertowanie komunikatu na tablicę obiektów parametrów i tablicę obiektów parametrów w wiadomości.</span><span class="sxs-lookup"><span data-stu-id="62473-116">`QueryStringFormatter` - The operation formatter is the component in WCF that is responsible for converting a message into an array of parameter objects and an array of parameter objects into a message.</span></span> <span data-ttu-id="62473-117">Jest to wykonywane na kliencie przy użyciu <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> interfejsu i na serwerze z <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interfejsem.</span><span class="sxs-lookup"><span data-stu-id="62473-117">This is done on the client using the <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> interface and on the server with the <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interface.</span></span> <span data-ttu-id="62473-118">Te interfejsy umożliwiają użytkownikom uzyskiwanie żądań i komunikatów odpowiedzi z `Serialize` `Deserialize` metod i.</span><span class="sxs-lookup"><span data-stu-id="62473-118">These interfaces enable users to get the request and response messages from the `Serialize` and `Deserialize` methods.</span></span>  
  
 <span data-ttu-id="62473-119">W tym przykładzie `QueryStringFormatter` implementuje obydwa te interfejsy i jest zaimplementowany na kliencie i serwerze.</span><span class="sxs-lookup"><span data-stu-id="62473-119">In this sample, `QueryStringFormatter` implements both of these interfaces and is implemented on the client and server.</span></span>  
  
 <span data-ttu-id="62473-120">Żądanie:</span><span class="sxs-lookup"><span data-stu-id="62473-120">Request:</span></span>  
  
- <span data-ttu-id="62473-121">Przykład używa <xref:System.ComponentModel.TypeConverter> klasy do konwersji danych parametrów w komunikacie żądania do i z ciągów znaków.</span><span class="sxs-lookup"><span data-stu-id="62473-121">The sample uses the <xref:System.ComponentModel.TypeConverter> class to convert parameter data in the request message to and from strings.</span></span> <span data-ttu-id="62473-122">Jeśli element <xref:System.ComponentModel.TypeConverter> nie jest dostępny dla określonego typu, przykładowy program formatujący zgłosi wyjątek.</span><span class="sxs-lookup"><span data-stu-id="62473-122">If a <xref:System.ComponentModel.TypeConverter> is not available for a specific type, the sample formatter throws an exception.</span></span>  
  
- <span data-ttu-id="62473-123">W `IClientMessageFormatter.SerializeRequest` metodzie klienta program formatujący tworzy identyfikator URI z odpowiednim adresem i dołącza nazwę operacji jako sufiks.</span><span class="sxs-lookup"><span data-stu-id="62473-123">In the `IClientMessageFormatter.SerializeRequest` method on the client, the formatter creates a URI with the appropriate To address and appends the operation name as a suffix.</span></span> <span data-ttu-id="62473-124">Ta nazwa jest używana do wysyłania do odpowiedniej operacji na serwerze.</span><span class="sxs-lookup"><span data-stu-id="62473-124">This name is used to dispatch to the appropriate operation on the server.</span></span> <span data-ttu-id="62473-125">Następnie pobiera tablicę obiektów parametrów i serializować dane parametrów do ciągu zapytania identyfikatora URI przy użyciu nazw parametrów i wartości przekonwertowanych przez <xref:System.ComponentModel.TypeConverter> klasę.</span><span class="sxs-lookup"><span data-stu-id="62473-125">It then takes the array of parameter objects and serializes the parameter data to the URI query string using parameter names and the values converted by the <xref:System.ComponentModel.TypeConverter> class.</span></span> <span data-ttu-id="62473-126"><xref:System.ServiceModel.Channels.MessageHeaders.To%2A>A <xref:System.ServiceModel.Channels.MessageProperties.Via%2A> następnie właściwości i są ustawiane na ten identyfikator URI.</span><span class="sxs-lookup"><span data-stu-id="62473-126">The <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> and <xref:System.ServiceModel.Channels.MessageProperties.Via%2A> properties are then set to this URI.</span></span> <span data-ttu-id="62473-127"><xref:System.ServiceModel.Channels.MessageProperties>jest dostępny za pomocą <xref:System.ServiceModel.Channels.Message.Properties%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="62473-127"><xref:System.ServiceModel.Channels.MessageProperties> is accessed through the <xref:System.ServiceModel.Channels.Message.Properties%2A> property.</span></span>  
  
- <span data-ttu-id="62473-128">W `IDispatchMessageFormatter.DeserializeRequest` metodzie na serwerze program formatujący pobiera `Via` Identyfikator URI we właściwościach komunikatu o żądaniu przychodzącym.</span><span class="sxs-lookup"><span data-stu-id="62473-128">In the `IDispatchMessageFormatter.DeserializeRequest` method on the server, the formatter retrieves the `Via` URI in the incoming request message properties.</span></span> <span data-ttu-id="62473-129">Analizuje pary nazwa-wartość w ciągu zapytania identyfikatora URI do nazw i wartości parametrów, a następnie używa nazw i wartości parametrów do wypełnienia tablicy parametrów przekazaną do metody.</span><span class="sxs-lookup"><span data-stu-id="62473-129">It parses the name-value pairs in the URI query string into parameter names and values and uses the parameter names and values to populate the array of parameters passed into the method.</span></span> <span data-ttu-id="62473-130">Należy zauważyć, że wysyłka operacji już się zakończyła, więc sufiks nazwy operacji jest ignorowany w tej metodzie.</span><span class="sxs-lookup"><span data-stu-id="62473-130">Note that operation dispatch has already occurred, so the operation name suffix is ignored in this method.</span></span>  
  
 <span data-ttu-id="62473-131">Odpowiedź:</span><span class="sxs-lookup"><span data-stu-id="62473-131">Response:</span></span>  
  
- <span data-ttu-id="62473-132">W tym przykładzie HTTP GET jest używany tylko dla żądania.</span><span class="sxs-lookup"><span data-stu-id="62473-132">In this sample, HTTP GET is used only for the request.</span></span> <span data-ttu-id="62473-133">Program formatujący deleguje wysyłanie odpowiedzi do oryginalnego programu formatującego, który mógłby zostać użyty do wygenerowania wiadomości XML.</span><span class="sxs-lookup"><span data-stu-id="62473-133">The formatter delegates the sending of the response to the original formatter that would have been used to generate an XML message.</span></span> <span data-ttu-id="62473-134">Jednym z celów tego przykładu jest przedstawienie sposobu, w jaki można zaimplementować ten program formatujący delegowanie.</span><span class="sxs-lookup"><span data-stu-id="62473-134">One of the goals of this sample is to show how such a delegating formatter can be implemented.</span></span>  
  
### <a name="uripathsuffixoperationselector-class"></a><span data-ttu-id="62473-135">Klasa UriPathSuffixOperationSelector</span><span class="sxs-lookup"><span data-stu-id="62473-135">UriPathSuffixOperationSelector Class</span></span>  
 <span data-ttu-id="62473-136"><xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector>Interfejs umożliwia użytkownikom implementację własnej logiki, dla której należy wysłać konkretną wiadomość.</span><span class="sxs-lookup"><span data-stu-id="62473-136">The <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> interface enables users to implement their own logic for which operation a particular message should be dispatched.</span></span>  
  
 <span data-ttu-id="62473-137">W tym przykładzie `UriPathSuffixOperationSelector` należy wdrożyć na serwerze, aby wybrać odpowiednią operację, ponieważ nazwa operacji jest uwzględniona w identyfikatorze URI http Get, a nie w nagłówku akcji w komunikacie.</span><span class="sxs-lookup"><span data-stu-id="62473-137">In this sample, `UriPathSuffixOperationSelector` must be implemented on the server to select the appropriate operation because the operation name is included in the HTTP GET URI rather than an action header in the message.</span></span> <span data-ttu-id="62473-138">Przykład jest skonfigurowany tak, aby zezwalał tylko na nazwy operacji bez uwzględniania wielkości liter.</span><span class="sxs-lookup"><span data-stu-id="62473-138">The sample is set up to allow only case-insensitive operation names.</span></span>  
  
 <span data-ttu-id="62473-139">`SelectOperation`Metoda przyjmuje komunikat przychodzący i wyszukuje `Via` Identyfikator URI we właściwościach komunikatu.</span><span class="sxs-lookup"><span data-stu-id="62473-139">The `SelectOperation` method takes the incoming message and looks up the `Via` URI in its message properties.</span></span> <span data-ttu-id="62473-140">Wyodrębnia sufiks nazwy operacji z identyfikatora URI, wyszukuje wewnętrzną tabelę, aby uzyskać nazwę operacji, do której wiadomość powinna zostać wysłana, i zwraca tę nazwę operacji.</span><span class="sxs-lookup"><span data-stu-id="62473-140">It extracts the operation name suffix from the URI, looks up an internal table to get the operation name that the message should be dispatched to, and returns that operation name.</span></span>  
  
### <a name="enablehttpgetrequestsbehavior-class"></a><span data-ttu-id="62473-141">Klasa EnableHttpGetRequestsBehavior</span><span class="sxs-lookup"><span data-stu-id="62473-141">EnableHttpGetRequestsBehavior Class</span></span>  
 <span data-ttu-id="62473-142">`UriPathSuffixOperationSelector`Składnik można skonfigurować programowo lub za pomocą zachowania punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="62473-142">The `UriPathSuffixOperationSelector` component can be set up programmatically or through an endpoint behavior.</span></span> <span data-ttu-id="62473-143">Przykład implementuje `EnableHttpGetRequestsBehavior` zachowanie, które jest określone w pliku konfiguracyjnym aplikacji usługi.</span><span class="sxs-lookup"><span data-stu-id="62473-143">The sample implements the `EnableHttpGetRequestsBehavior` behavior, which is specified in service’s application configuration file.</span></span>  
  
 <span data-ttu-id="62473-144">Na serwerze programu:</span><span class="sxs-lookup"><span data-stu-id="62473-144">On the server:</span></span>  
  
 <span data-ttu-id="62473-145"><xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A>Ustawiono <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementację.</span><span class="sxs-lookup"><span data-stu-id="62473-145">The <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A> is set to the <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementation.</span></span>  
  
 <span data-ttu-id="62473-146">Domyślnie WCF używa filtru adresów dokładnie dopasowane.</span><span class="sxs-lookup"><span data-stu-id="62473-146">By default, WCF uses an exact-match address filter.</span></span> <span data-ttu-id="62473-147">Identyfikator URI komunikatu przychodzącego zawiera sufiks nazwy operacji, po którym następuje ciąg zapytania, który zawiera dane parametrów, więc zachowanie punktu końcowego zmienia również filtr adresów na filtr dopasowania prefiksu.</span><span class="sxs-lookup"><span data-stu-id="62473-147">The URI on the incoming message contains an operation name suffix followed by a query string that contains parameter data, so the endpoint behavior also changes the address filter to be a prefix match filter.</span></span> <span data-ttu-id="62473-148">W tym celu używa programu WCF <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> .</span><span class="sxs-lookup"><span data-stu-id="62473-148">It uses the WCF<xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> for this purpose.</span></span>  
  
### <a name="installing-operation-formatters"></a><span data-ttu-id="62473-149">Instalowanie programów formatujących operacje</span><span class="sxs-lookup"><span data-stu-id="62473-149">Installing operation formatters</span></span>  
 <span data-ttu-id="62473-150">Zachowania operacji określające elementy formatujące są unikatowe.</span><span class="sxs-lookup"><span data-stu-id="62473-150">Operation behaviors that specify formatters are unique.</span></span> <span data-ttu-id="62473-151">Takie zachowanie jest zawsze zaimplementowane domyślnie dla każdej operacji w celu utworzenia wymaganego programu formatującego operacji.</span><span class="sxs-lookup"><span data-stu-id="62473-151">One such behavior is always implemented by default for every operation to create the necessary operation formatter.</span></span> <span data-ttu-id="62473-152">Jednak te zachowania wyglądają jak tylko inne zachowanie operacji; nie są one identyfikowane przez żaden inny atrybut.</span><span class="sxs-lookup"><span data-stu-id="62473-152">However, these behaviors look like just another operation behavior; they are not identifiable by any other attribute.</span></span> <span data-ttu-id="62473-153">Aby można było zainstalować zachowanie zamiany, implementacja musi szukać określonych zachowań programu formatującego, które są instalowane domyślnie przez program ładujący typ WCF, i zastąpić je lub dodać zgodne zachowanie, które zostanie uruchomione po domyślnym zachowaniu.</span><span class="sxs-lookup"><span data-stu-id="62473-153">To install a replacement behavior, the implementation must look for specific formatter behaviors that are installed by the WCF type loader by default and either replace it or add a compatible behavior to run after the default behavior.</span></span>  
  
 <span data-ttu-id="62473-154">Te zachowania programu formatującego operacji można skonfigurować programowo przed wywołaniem <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> lub przez określenie zachowania operacji, które jest wykonywane po wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="62473-154">These operation formatters behaviors can be set up programmatically prior to calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> or by specifying an operation behavior that is executed after the default one.</span></span> <span data-ttu-id="62473-155">Nie można go jednak łatwo konfigurować przy użyciu zachowania punktu końcowego (w związku z czym konfiguracja), ponieważ model zachowania nie zezwala na zachowanie innych zachowań lub modyfikowanie drzewa opisów.</span><span class="sxs-lookup"><span data-stu-id="62473-155">However, it cannot easily be set up by an endpoint behavior (and therefore by configuration) because the behavior model does not allow a behavior to replace other behaviors or otherwise modify the description tree.</span></span>  
  
 <span data-ttu-id="62473-156">Na kliencie:</span><span class="sxs-lookup"><span data-stu-id="62473-156">On the client:</span></span>  
  
 <span data-ttu-id="62473-157"><xref:System.ServiceModel.Dispatcher.IClientMessageFormatter>Implementacja musi być zaimplementowana, aby można było skonwertować żądania na żądania HTTP GET i delegować do oryginalnego programu formatującego dla odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="62473-157">The <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> implementation must be implemented so that it can convert the requests into HTTP GET requests and delegate to the original formatter for responses.</span></span> <span data-ttu-id="62473-158">W tym celu należy wywołać `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` metodę pomocnika.</span><span class="sxs-lookup"><span data-stu-id="62473-158">This is done by calling the `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` helper method.</span></span>  
  
 <span data-ttu-id="62473-159">Należy to zrobić przed wywołaniem metody `CreateChannel` .</span><span class="sxs-lookup"><span data-stu-id="62473-159">This must be done before calling `CreateChannel`.</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="62473-160">Na serwerze programu:</span><span class="sxs-lookup"><span data-stu-id="62473-160">On the server:</span></span>  
  
- <span data-ttu-id="62473-161"><xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter>Interfejs musi być zaimplementowany, aby mógł odczytywać żądania HTTP GET i delegować do oryginalnego programu formatującego w celu zapisywania odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="62473-161">The <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interface must be implemented so that it can read HTTP GET requests and delegate to the original formatter for writing responses.</span></span> <span data-ttu-id="62473-162">Jest to realizowane przez wywołanie tej samej `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` metody pomocnika co klient (zobacz poprzedni przykład kodu).</span><span class="sxs-lookup"><span data-stu-id="62473-162">This is done by calling the same `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` helper method as the client (see the previous code sample).</span></span>  
  
- <span data-ttu-id="62473-163">Należy to zrobić przed <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> wywołaniem metody.</span><span class="sxs-lookup"><span data-stu-id="62473-163">This must be done before <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> is called.</span></span> <span data-ttu-id="62473-164">W tym przykładzie pokazano, jak program formatujący został ręcznie zmodyfikowany przed wywołaniem <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> .</span><span class="sxs-lookup"><span data-stu-id="62473-164">In this sample, we show how the formatter is manually modified before calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span> <span data-ttu-id="62473-165">Innym sposobem osiągnięcia tego samego celu jest wyprowadzenie klasy z <xref:System.ServiceModel.ServiceHost> tego, że wywołania `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` przed otwarciem (patrz dokumentacja hostingu i przykłady).</span><span class="sxs-lookup"><span data-stu-id="62473-165">Another way to achieve the same thing is to derive a class from <xref:System.ServiceModel.ServiceHost> that makes the calls to `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` before opening (please see hosting documentation and samples for examples).</span></span>  
  
### <a name="user-experience"></a><span data-ttu-id="62473-166">Środowisko użytkownika</span><span class="sxs-lookup"><span data-stu-id="62473-166">User experience</span></span>  
 <span data-ttu-id="62473-167">Na serwerze programu:</span><span class="sxs-lookup"><span data-stu-id="62473-167">On the server:</span></span>  
  
- <span data-ttu-id="62473-168">Implementacja serwera nie `ICalculator` musi się zmieniać.</span><span class="sxs-lookup"><span data-stu-id="62473-168">The server `ICalculator` implementation does not need to change.</span></span>  
  
- <span data-ttu-id="62473-169">Plik App. config usługi musi używać niestandardowego powiązania POX, które ustawia `messageVersion` atrybut `textMessageEncoding` elementu na `None` .</span><span class="sxs-lookup"><span data-stu-id="62473-169">The App.config for the service must use a custom POX binding that sets the `messageVersion` attribute of the `textMessageEncoding` element to `None`.</span></span>  
  
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
  
- <span data-ttu-id="62473-170">Plik App. config usługi musi również określać niestandardowe `EnableHttpGetRequestsBehavior` przez dodanie go do sekcji rozszerzenia zachowań i używanie go.</span><span class="sxs-lookup"><span data-stu-id="62473-170">The App.config for the service also must specify the custom `EnableHttpGetRequestsBehavior` by adding it to the behavior extensions section and using it.</span></span>  
  
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
  
- <span data-ttu-id="62473-171">Dodaj elementy formatujące operacji przed wywołaniem metody <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> .</span><span class="sxs-lookup"><span data-stu-id="62473-171">Add operation formatters before calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span>  
  
 <span data-ttu-id="62473-172">Na kliencie:</span><span class="sxs-lookup"><span data-stu-id="62473-172">On the client:</span></span>  
  
- <span data-ttu-id="62473-173">Implementacja klienta nie musi być zmieniana.</span><span class="sxs-lookup"><span data-stu-id="62473-173">The client implementation does not need to change.</span></span>  
  
- <span data-ttu-id="62473-174">Plik App. config klienta musi używać niestandardowego powiązania POX, które ustawia `messageVersion` atrybut `textMessageEncoding` elementu na `None` .</span><span class="sxs-lookup"><span data-stu-id="62473-174">The App.config for the client must use a custom POX binding that sets the `messageVersion` attribute of the `textMessageEncoding` element to `None`.</span></span> <span data-ttu-id="62473-175">Jedną z różnic polega na tym, że klient musi włączyć ręczne adresowanie, aby można było zmodyfikować adres wychodzący.</span><span class="sxs-lookup"><span data-stu-id="62473-175">One difference from the service is that the client must enable manual addressing so that the outgoing To address can be modified.</span></span>  
  
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
  
- <span data-ttu-id="62473-176">Plik App. config klienta musi określać ten sam niestandardowy `EnableHttpGetRequestsBehavior` serwer.</span><span class="sxs-lookup"><span data-stu-id="62473-176">The App.config for the client must specify the same custom `EnableHttpGetRequestsBehavior` as the server.</span></span>  
  
- <span data-ttu-id="62473-177">Dodaj elementy formatujące operacji przed wywołaniem metody <xref:System.ServiceModel.ChannelFactory%601.CreateChannel> .</span><span class="sxs-lookup"><span data-stu-id="62473-177">Add operation formatters before calling <xref:System.ServiceModel.ChannelFactory%601.CreateChannel>.</span></span>  
  
 <span data-ttu-id="62473-178">Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="62473-178">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="62473-179">Wszystkie cztery operacje (Dodawanie, odejmowanie, mnożenie i dzielenie) muszą się zakończyć pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="62473-179">All four operations (Add, Subtract, Multiply, and Divide) must succeed.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="62473-180">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="62473-180">The samples may already be installed on your machine.</span></span> <span data-ttu-id="62473-181">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="62473-181">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="62473-182">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="62473-182">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="62473-183">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="62473-183">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Formatters\QueryStringFormatter`  
  
##### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="62473-184">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="62473-184">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="62473-185">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="62473-185">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="62473-186">Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="62473-186">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="62473-187">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="62473-187">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
