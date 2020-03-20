---
title: Element formatujący operacji i selektor operacji
ms.date: 03/30/2017
ms.assetid: 1c27e9fe-11f8-4377-8140-828207b98a0e
ms.openlocfilehash: 9d1bc0afa54f89e064eab3f3e45da60c8d10de38
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144282"
---
# <a name="operation-formatter-and-operation-selector"></a><span data-ttu-id="dbff4-102">Element formatujący operacji i selektor operacji</span><span class="sxs-lookup"><span data-stu-id="dbff4-102">Operation Formatter and Operation Selector</span></span>
<span data-ttu-id="dbff4-103">W tym przykładzie pokazano, jak Windows Communication Foundation (WCF) punkty rozszerzalności może służyć do zezwalania na dane wiadomości w innym formacie, niż oczekuje WCF.</span><span class="sxs-lookup"><span data-stu-id="dbff4-103">This sample demonstrates how Windows Communication Foundation (WCF) extensibility points can be used to allow message data in a different format from what WCF expects.</span></span> <span data-ttu-id="dbff4-104">Domyślnie formaterów WCF oczekiwać parametry metody `soap:body` mają być zawarte w elemencie.</span><span class="sxs-lookup"><span data-stu-id="dbff4-104">By default, WCF formatters expect method parameters to be included under the `soap:body` element.</span></span> <span data-ttu-id="dbff4-105">W przykładzie pokazano, jak zaimplementować niestandardowy formater operacji, który analizuje dane parametrów z ciągu zapytania HTTP GET zamiast i wywołuje metody przy użyciu tych danych.</span><span class="sxs-lookup"><span data-stu-id="dbff4-105">The sample shows how to implement a custom operation formatter that parses parameter data from an HTTP GET query string instead and invokes methods using that data.</span></span>  
  
 <span data-ttu-id="dbff4-106">Próbka jest oparta na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), `ICalculator` który implementuje umowy serwisowej.</span><span class="sxs-lookup"><span data-stu-id="dbff4-106">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="dbff4-107">Pokazuje, jak można zmienić komunikaty Dodaj, Odejmować, Mnożenie i Podziel, aby używać protokołu HTTP GET dla żądań klient-serwer i HTTP POST z komunikatami POX dla odpowiedzi między serwerami.</span><span class="sxs-lookup"><span data-stu-id="dbff4-107">It shows how Add, Subtract, Multiply, and Divide messages can be changed to use HTTP GET for client-to-server requests and HTTP POST with POX messages for server-to-client responses.</span></span>  
  
 <span data-ttu-id="dbff4-108">W tym celu próbka zawiera następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="dbff4-108">To do so, the sample provides the following:</span></span>  
  
- <span data-ttu-id="dbff4-109">`QueryStringFormatter`, który <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> implementuje i <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> dla klienta i serwera, odpowiednio, i przetwarza dane w ciągu zapytania.</span><span class="sxs-lookup"><span data-stu-id="dbff4-109">`QueryStringFormatter`, which implements <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> and <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> for the client and server, respectively, and processes the data in the query string.</span></span>  
  
- <span data-ttu-id="dbff4-110">`UriOperationSelector`, który <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementuje na serwerze do wykonywania operacji wysyłki na podstawie nazwy operacji w żądaniu GET.</span><span class="sxs-lookup"><span data-stu-id="dbff4-110">`UriOperationSelector`, which implements <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> on the server to perform operation dispatch based on the operation name in the GET request.</span></span>  
  
- <span data-ttu-id="dbff4-111">`EnableHttpGetRequestsBehavior`zachowanie punktu końcowego (i odpowiednia konfiguracja), który dodaje selektor operacji niezbędne do środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="dbff4-111">`EnableHttpGetRequestsBehavior` endpoint behavior (and corresponding configuration), which adds the necessary operation selector to the runtime.</span></span>  
  
- <span data-ttu-id="dbff4-112">Pokazuje, jak wstawić nowy program formatowania operacji do środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="dbff4-112">Shows how to insert a new operation formatter into the runtime.</span></span>  
  
- <span data-ttu-id="dbff4-113">W tym przykładzie zarówno klient, jak i usługa są aplikacjami konsoli (.exe).</span><span class="sxs-lookup"><span data-stu-id="dbff4-113">In this sample, both the client and the service are console applications (.exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dbff4-114">Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="dbff4-114">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="key-concepts"></a><span data-ttu-id="dbff4-115">Kluczowe pojęcia</span><span class="sxs-lookup"><span data-stu-id="dbff4-115">Key Concepts</span></span>  
 <span data-ttu-id="dbff4-116">`QueryStringFormatter`- Formater operacji jest składnikiem w WCF, który jest odpowiedzialny za konwersję wiadomości do tablicy obiektów parametrów i tablicy obiektów parametrów w wiadomości.</span><span class="sxs-lookup"><span data-stu-id="dbff4-116">`QueryStringFormatter` - The operation formatter is the component in WCF that is responsible for converting a message into an array of parameter objects and an array of parameter objects into a message.</span></span> <span data-ttu-id="dbff4-117">Odbywa się to na <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> kliencie za pomocą <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interfejsu i na serwerze z interfejsem.</span><span class="sxs-lookup"><span data-stu-id="dbff4-117">This is done on the client using the <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> interface and on the server with the <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interface.</span></span> <span data-ttu-id="dbff4-118">Interfejsy te umożliwiają użytkownikom uzyskanie komunikatów `Serialize` żądania `Deserialize` i odpowiedzi z i metod.</span><span class="sxs-lookup"><span data-stu-id="dbff4-118">These interfaces enable users to get the request and response messages from the `Serialize` and `Deserialize` methods.</span></span>  
  
 <span data-ttu-id="dbff4-119">W tym `QueryStringFormatter` przykładzie implementuje oba te interfejsy i jest zaimplementowany na kliencie i serwerze.</span><span class="sxs-lookup"><span data-stu-id="dbff4-119">In this sample, `QueryStringFormatter` implements both of these interfaces and is implemented on the client and server.</span></span>  
  
 <span data-ttu-id="dbff4-120">Żądanie:</span><span class="sxs-lookup"><span data-stu-id="dbff4-120">Request:</span></span>  
  
- <span data-ttu-id="dbff4-121">Przykład używa <xref:System.ComponentModel.TypeConverter> klasy do konwersji danych parametrów w wiadomości żądania do i z ciągów.</span><span class="sxs-lookup"><span data-stu-id="dbff4-121">The sample uses the <xref:System.ComponentModel.TypeConverter> class to convert parameter data in the request message to and from strings.</span></span> <span data-ttu-id="dbff4-122">Jeśli <xref:System.ComponentModel.TypeConverter> a nie jest dostępna dla określonego typu, przykładowy formater zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="dbff4-122">If a <xref:System.ComponentModel.TypeConverter> is not available for a specific type, the sample formatter throws an exception.</span></span>  
  
- <span data-ttu-id="dbff4-123">W `IClientMessageFormatter.SerializeRequest` metodzie na kliencie formater tworzy identyfikator URI z odpowiednim Adresem i dołącza nazwę operacji jako sufiks.</span><span class="sxs-lookup"><span data-stu-id="dbff4-123">In the `IClientMessageFormatter.SerializeRequest` method on the client, the formatter creates a URI with the appropriate To address and appends the operation name as a suffix.</span></span> <span data-ttu-id="dbff4-124">Ta nazwa jest używana do wysyłania do odpowiedniej operacji na serwerze.</span><span class="sxs-lookup"><span data-stu-id="dbff4-124">This name is used to dispatch to the appropriate operation on the server.</span></span> <span data-ttu-id="dbff4-125">Następnie pobiera tablicę obiektów parametrów i serializuje dane parametrów do ciągu kwerendy URI <xref:System.ComponentModel.TypeConverter> przy użyciu nazw parametrów i wartości przekonwertowanych przez klasę.</span><span class="sxs-lookup"><span data-stu-id="dbff4-125">It then takes the array of parameter objects and serializes the parameter data to the URI query string using parameter names and the values converted by the <xref:System.ComponentModel.TypeConverter> class.</span></span> <span data-ttu-id="dbff4-126">Właściwości <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> <xref:System.ServiceModel.Channels.MessageProperties.Via%2A> i są następnie ustawione na ten identyfikator URI.</span><span class="sxs-lookup"><span data-stu-id="dbff4-126">The <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> and <xref:System.ServiceModel.Channels.MessageProperties.Via%2A> properties are then set to this URI.</span></span> <span data-ttu-id="dbff4-127"><xref:System.ServiceModel.Channels.MessageProperties>dostęp do <xref:System.ServiceModel.Channels.Message.Properties%2A> obiektu.</span><span class="sxs-lookup"><span data-stu-id="dbff4-127"><xref:System.ServiceModel.Channels.MessageProperties> is accessed through the <xref:System.ServiceModel.Channels.Message.Properties%2A> property.</span></span>  
  
- <span data-ttu-id="dbff4-128">W `IDispatchMessageFormatter.DeserializeRequest` metodzie na serwerze program formatujący pobiera identyfikator `Via` URI we właściwościach komunikatu żądania przychodzącego.</span><span class="sxs-lookup"><span data-stu-id="dbff4-128">In the `IDispatchMessageFormatter.DeserializeRequest` method on the server, the formatter retrieves the `Via` URI in the incoming request message properties.</span></span> <span data-ttu-id="dbff4-129">Analizuje pary nazwa-wartość w ciągu kwerendy URI na nazwy i wartości parametrów i używa nazw parametrów i wartości do wypełniania tablicy parametrów przekazanych do metody.</span><span class="sxs-lookup"><span data-stu-id="dbff4-129">It parses the name-value pairs in the URI query string into parameter names and values and uses the parameter names and values to populate the array of parameters passed into the method.</span></span> <span data-ttu-id="dbff4-130">Należy zauważyć, że wysyłka operacji już wystąpiła, więc sufiks nazwy operacji jest ignorowany w tej metodzie.</span><span class="sxs-lookup"><span data-stu-id="dbff4-130">Note that operation dispatch has already occurred, so the operation name suffix is ignored in this method.</span></span>  
  
 <span data-ttu-id="dbff4-131">Odpowiedź:</span><span class="sxs-lookup"><span data-stu-id="dbff4-131">Response:</span></span>  
  
- <span data-ttu-id="dbff4-132">W tym przykładzie HTTP GET jest używany tylko dla żądania.</span><span class="sxs-lookup"><span data-stu-id="dbff4-132">In this sample, HTTP GET is used only for the request.</span></span> <span data-ttu-id="dbff4-133">Formater deleguje wysyłanie odpowiedzi do oryginalnego formatera, który zostałby użyty do wygenerowania wiadomości XML.</span><span class="sxs-lookup"><span data-stu-id="dbff4-133">The formatter delegates the sending of the response to the original formatter that would have been used to generate an XML message.</span></span> <span data-ttu-id="dbff4-134">Jednym z celów tego przykładu jest pokazanie, jak można zaimplementować takiego formatera delegującego.</span><span class="sxs-lookup"><span data-stu-id="dbff4-134">One of the goals of this sample is to show how such a delegating formatter can be implemented.</span></span>  
  
### <a name="uripathsuffixoperationselector-class"></a><span data-ttu-id="dbff4-135">UriPathSuffixOperationSelector Klasa</span><span class="sxs-lookup"><span data-stu-id="dbff4-135">UriPathSuffixOperationSelector Class</span></span>  
 <span data-ttu-id="dbff4-136">Interfejs <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> umożliwia użytkownikom zaimplementowanie własnej logiki, dla której należy wysłać określoną wiadomość.</span><span class="sxs-lookup"><span data-stu-id="dbff4-136">The <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> interface enables users to implement their own logic for which operation a particular message should be dispatched.</span></span>  
  
 <span data-ttu-id="dbff4-137">W tym `UriPathSuffixOperationSelector` przykładzie muszą być zaimplementowane na serwerze, aby wybrać odpowiednią operację, ponieważ nazwa operacji znajduje się w identyfikatorze URI HTTP GET, a nie nagłówek akcji w komunikacie.</span><span class="sxs-lookup"><span data-stu-id="dbff4-137">In this sample, `UriPathSuffixOperationSelector` must be implemented on the server to select the appropriate operation because the operation name is included in the HTTP GET URI rather than an action header in the message.</span></span> <span data-ttu-id="dbff4-138">Próbka jest skonfigurowana tak, aby zezwalać tylko na nazwy operacji bez uwzględniania wielkości liter.</span><span class="sxs-lookup"><span data-stu-id="dbff4-138">The sample is set up to allow only case-insensitive operation names.</span></span>  
  
 <span data-ttu-id="dbff4-139">Metoda `SelectOperation` przyjmuje przychodzące wiadomości i `Via` wyszukuje identyfikator URI we właściwościach wiadomości.</span><span class="sxs-lookup"><span data-stu-id="dbff4-139">The `SelectOperation` method takes the incoming message and looks up the `Via` URI in its message properties.</span></span> <span data-ttu-id="dbff4-140">Wyodrębnia sufiks nazwy operacji z identyfikatora URI, wyszukuje tabelę wewnętrzną, aby uzyskać nazwę operacji, do których powinien być wywoływany komunikat, i zwraca tę nazwę operacji.</span><span class="sxs-lookup"><span data-stu-id="dbff4-140">It extracts the operation name suffix from the URI, looks up an internal table to get the operation name that the message should be dispatched to, and returns that operation name.</span></span>  
  
### <a name="enablehttpgetrequestsbehavior-class"></a><span data-ttu-id="dbff4-141">Włącz klasę HttpGetRequestsBehavior</span><span class="sxs-lookup"><span data-stu-id="dbff4-141">EnableHttpGetRequestsBehavior Class</span></span>  
 <span data-ttu-id="dbff4-142">Składnik `UriPathSuffixOperationSelector` można skonfigurować programowo lub za pomocą zachowania punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="dbff4-142">The `UriPathSuffixOperationSelector` component can be set up programmatically or through an endpoint behavior.</span></span> <span data-ttu-id="dbff4-143">Przykład implementuje `EnableHttpGetRequestsBehavior` zachowanie, które jest określone w pliku konfiguracji aplikacji usługi.</span><span class="sxs-lookup"><span data-stu-id="dbff4-143">The sample implements the `EnableHttpGetRequestsBehavior` behavior, which is specified in service’s application configuration file.</span></span>  
  
 <span data-ttu-id="dbff4-144">Na serwerze:</span><span class="sxs-lookup"><span data-stu-id="dbff4-144">On the server:</span></span>  
  
 <span data-ttu-id="dbff4-145">Jest <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A> ustawiona <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> na implementację.</span><span class="sxs-lookup"><span data-stu-id="dbff4-145">The <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A> is set to the <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementation.</span></span>  
  
 <span data-ttu-id="dbff4-146">Domyślnie WCF używa filtru adresów dopasowania ścisłego.</span><span class="sxs-lookup"><span data-stu-id="dbff4-146">By default, WCF uses an exact-match address filter.</span></span> <span data-ttu-id="dbff4-147">Identyfikator URI w wiadomości przychodzącej zawiera sufiks nazwy operacji, po którym następuje ciąg zapytania zawierający dane parametrów, więc zachowanie punktu końcowego zmienia również filtr adresów jako filtr dopasowania prefiksu.</span><span class="sxs-lookup"><span data-stu-id="dbff4-147">The URI on the incoming message contains an operation name suffix followed by a query string that contains parameter data, so the endpoint behavior also changes the address filter to be a prefix match filter.</span></span> <span data-ttu-id="dbff4-148">Używa WCF<xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> do tego celu.</span><span class="sxs-lookup"><span data-stu-id="dbff4-148">It uses the WCF<xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> for this purpose.</span></span>  
  
### <a name="installing-operation-formatters"></a><span data-ttu-id="dbff4-149">Instalowanie programów formatujących operacji</span><span class="sxs-lookup"><span data-stu-id="dbff4-149">Installing operation formatters</span></span>  
 <span data-ttu-id="dbff4-150">Zachowania operacji, które określają formaterów są unikatowe.</span><span class="sxs-lookup"><span data-stu-id="dbff4-150">Operation behaviors that specify formatters are unique.</span></span> <span data-ttu-id="dbff4-151">Jedno takie zachowanie jest zawsze implementowane domyślnie dla każdej operacji, aby utworzyć formater operacji niezbędne.</span><span class="sxs-lookup"><span data-stu-id="dbff4-151">One such behavior is always implemented by default for every operation to create the necessary operation formatter.</span></span> <span data-ttu-id="dbff4-152">Jednak te zachowania wyglądają jak tylko inne zachowanie operacji; nie można ich zidentyfikować za pomocą żadnego innego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="dbff4-152">However, these behaviors look like just another operation behavior; they are not identifiable by any other attribute.</span></span> <span data-ttu-id="dbff4-153">Aby zainstalować zachowanie zastępcze, implementacja musi wyszukać określone zachowania formatera, które są domyślnie instalowane przez program ładujący typu WCF i zastąpić go lub dodać zgodne zachowanie do uruchomienia po domyślnym zachowaniu.</span><span class="sxs-lookup"><span data-stu-id="dbff4-153">To install a replacement behavior, the implementation must look for specific formatter behaviors that are installed by the WCF type loader by default and either replace it or add a compatible behavior to run after the default behavior.</span></span>  
  
 <span data-ttu-id="dbff4-154">Te zachowania programowe formaterów operacji można skonfigurować <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> programowo przed wywołaniem lub określając zachowanie operacji wykonywane po domyślnym.</span><span class="sxs-lookup"><span data-stu-id="dbff4-154">These operation formatters behaviors can be set up programmatically prior to calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> or by specifying an operation behavior that is executed after the default one.</span></span> <span data-ttu-id="dbff4-155">Jednak nie można łatwo skonfigurować przez zachowanie punktu końcowego (i w związku z tym przez konfigurację), ponieważ model zachowania nie zezwala na zachowanie, aby zastąpić inne zachowania lub w inny sposób zmodyfikować drzewo opisu.</span><span class="sxs-lookup"><span data-stu-id="dbff4-155">However, it cannot easily be set up by an endpoint behavior (and therefore by configuration) because the behavior model does not allow a behavior to replace other behaviors or otherwise modify the description tree.</span></span>  
  
 <span data-ttu-id="dbff4-156">Na kliencie:</span><span class="sxs-lookup"><span data-stu-id="dbff4-156">On the client:</span></span>  
  
 <span data-ttu-id="dbff4-157">Implementacja <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> musi zostać zaimplementowana, aby mogła konwertować żądania na żądania HTTP GET i delegować do oryginalnego formatera odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="dbff4-157">The <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> implementation must be implemented so that it can convert the requests into HTTP GET requests and delegate to the original formatter for responses.</span></span> <span data-ttu-id="dbff4-158">Odbywa się to `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` przez wywołanie metody pomocnika.</span><span class="sxs-lookup"><span data-stu-id="dbff4-158">This is done by calling the `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` helper method.</span></span>  
  
 <span data-ttu-id="dbff4-159">Należy to zrobić `CreateChannel`przed wywołaniem .</span><span class="sxs-lookup"><span data-stu-id="dbff4-159">This must be done before calling `CreateChannel`.</span></span>  
  
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
  
 <span data-ttu-id="dbff4-160">Na serwerze:</span><span class="sxs-lookup"><span data-stu-id="dbff4-160">On the server:</span></span>  
  
- <span data-ttu-id="dbff4-161">Interfejs <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> musi być zaimplementowany tak, aby mógł odczytywać żądania HTTP GET i delegować do oryginalnego formatera do pisania odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="dbff4-161">The <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interface must be implemented so that it can read HTTP GET requests and delegate to the original formatter for writing responses.</span></span> <span data-ttu-id="dbff4-162">Odbywa się to przez `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` wywołanie tej samej metody pomocnika jako klienta (zobacz poprzedni przykład kodu).</span><span class="sxs-lookup"><span data-stu-id="dbff4-162">This is done by calling the same `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` helper method as the client (see the previous code sample).</span></span>  
  
- <span data-ttu-id="dbff4-163">Należy to zrobić, zanim <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> zostanie wywołana.</span><span class="sxs-lookup"><span data-stu-id="dbff4-163">This must be done before <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> is called.</span></span> <span data-ttu-id="dbff4-164">W tym przykładzie pokazujemy, jak formater jest <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>ręcznie modyfikowany przed wywołaniem .</span><span class="sxs-lookup"><span data-stu-id="dbff4-164">In this sample, we show how the formatter is manually modified before calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span> <span data-ttu-id="dbff4-165">Innym sposobem osiągnięcia tego samego jest wyprowadzenie klasy <xref:System.ServiceModel.ServiceHost> `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` z tego sprawia, że wywołania przed otwarciem (zobacz dokumentację hostingu i przykłady przykładów).</span><span class="sxs-lookup"><span data-stu-id="dbff4-165">Another way to achieve the same thing is to derive a class from <xref:System.ServiceModel.ServiceHost> that makes the calls to `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` before opening (please see hosting documentation and samples for examples).</span></span>  
  
### <a name="user-experience"></a><span data-ttu-id="dbff4-166">Środowisko użytkownika</span><span class="sxs-lookup"><span data-stu-id="dbff4-166">User experience</span></span>  
 <span data-ttu-id="dbff4-167">Na serwerze:</span><span class="sxs-lookup"><span data-stu-id="dbff4-167">On the server:</span></span>  
  
- <span data-ttu-id="dbff4-168">Implementacja `ICalculator` serwera nie musi się zmieniać.</span><span class="sxs-lookup"><span data-stu-id="dbff4-168">The server `ICalculator` implementation does not need to change.</span></span>  
  
- <span data-ttu-id="dbff4-169">App.config dla usługi musi używać niestandardowego powiązania `messageVersion` POX, `textMessageEncoding` które `None`ustawia atrybut elementu do .</span><span class="sxs-lookup"><span data-stu-id="dbff4-169">The App.config for the service must use a custom POX binding that sets the `messageVersion` attribute of the `textMessageEncoding` element to `None`.</span></span>  
  
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
  
- <span data-ttu-id="dbff4-170">App.config dla usługi również należy `EnableHttpGetRequestsBehavior` określić niestandardowe, dodając go do rozszerzenia zachowania sekcji i używając go.</span><span class="sxs-lookup"><span data-stu-id="dbff4-170">The App.config for the service also must specify the custom `EnableHttpGetRequestsBehavior` by adding it to the behavior extensions section and using it.</span></span>  
  
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
  
- <span data-ttu-id="dbff4-171">Dodaj programy formaterów <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>operacji przed wywołaniem .</span><span class="sxs-lookup"><span data-stu-id="dbff4-171">Add operation formatters before calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span>  
  
 <span data-ttu-id="dbff4-172">Na kliencie:</span><span class="sxs-lookup"><span data-stu-id="dbff4-172">On the client:</span></span>  
  
- <span data-ttu-id="dbff4-173">Implementacja klienta nie musi się zmieniać.</span><span class="sxs-lookup"><span data-stu-id="dbff4-173">The client implementation does not need to change.</span></span>  
  
- <span data-ttu-id="dbff4-174">App.config dla klienta musi używać niestandardowego powiązania `messageVersion` POX, `textMessageEncoding` które `None`ustawia atrybut elementu na .</span><span class="sxs-lookup"><span data-stu-id="dbff4-174">The App.config for the client must use a custom POX binding that sets the `messageVersion` attribute of the `textMessageEncoding` element to `None`.</span></span> <span data-ttu-id="dbff4-175">Jedną z różnic w stosunku do usługi jest to, że klient musi włączyć adres ręczny, tak aby adres wychodzący do może być modyfikowany.</span><span class="sxs-lookup"><span data-stu-id="dbff4-175">One difference from the service is that the client must enable manual addressing so that the outgoing To address can be modified.</span></span>  
  
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
  
- <span data-ttu-id="dbff4-176">App.config dla klienta musi określić `EnableHttpGetRequestsBehavior` ten sam niestandardowy jako serwer.</span><span class="sxs-lookup"><span data-stu-id="dbff4-176">The App.config for the client must specify the same custom `EnableHttpGetRequestsBehavior` as the server.</span></span>  
  
- <span data-ttu-id="dbff4-177">Dodaj programy formaterów <xref:System.ServiceModel.ChannelFactory%601.CreateChannel>operacji przed wywołaniem .</span><span class="sxs-lookup"><span data-stu-id="dbff4-177">Add operation formatters before calling <xref:System.ServiceModel.ChannelFactory%601.CreateChannel>.</span></span>  
  
 <span data-ttu-id="dbff4-178">Po uruchomieniu próbki żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="dbff4-178">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="dbff4-179">Wszystkie cztery operacje (Dodaj, Odejmij, Mnożenie i Podziel) muszą zakończyć się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="dbff4-179">All four operations (Add, Subtract, Multiply, and Divide) must succeed.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="dbff4-180">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="dbff4-180">The samples may already be installed on your machine.</span></span> <span data-ttu-id="dbff4-181">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="dbff4-181">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="dbff4-182">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="dbff4-182">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="dbff4-183">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="dbff4-183">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Formatters\QueryStringFormatter`  
  
##### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="dbff4-184">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="dbff4-184">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="dbff4-185">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="dbff4-185">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="dbff4-186">Aby utworzyć rozwiązanie, postępuj zgodnie z instrukcjami w [tworzeniu przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="dbff4-186">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="dbff4-187">Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="dbff4-187">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
